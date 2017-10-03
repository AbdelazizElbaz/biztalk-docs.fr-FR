---
title: "Prise en charge pour la gestion de la file d’attente | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d60d06ba-8cf3-46d6-af59-626f12fc572a
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: faeb3f141e114cf1f86157084f50d0a0d490833a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="support-for-queue-management"></a>Prise en charge de la gestion des files d'attente
Grâce à l'adaptateur MQSeries [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], vous pouvez maintenant créer et supprimer des files d'attente à distance dans le gestionnaire de file d'attente MQSeries. Cette fonctionnalité est prise en charge car [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] utilise un objet MQSAgent COM+ distant qui communique directement avec le gestionnaire de file d'attente MQSeries. Généralement, cet objet MQSAgent est utilisé au moment de l'exécution pour lire et écrire des messages dans les files d'attente du serveur MQSeries distant. Plusieurs serveurs BizTalk peuvent être clients de ce service distant. En outre, les fonctionnalités de création et de suppression de files d'attente sont fournies par ce composant MQSAgent et peuvent être appelées directement à partir d'une orchestration ou d'un adaptateur. Cela rend possible des scénarios hautement dynamiques dans lesquels l'orchestration ou l'adaptateur peut créer une file d'attente temporaire, y envoyer un message, recevoir une réponse sur une autre file d'attente, puis supprimer la file d'attente temporaire.  
  
## <a name="createqueue-and-deletequeue-apis"></a>API CreateQueue et DeleteQueue  
 Les API CreateQueue et DeleteQueue sont définies comme suit :  
  
### <a name="structure-definition"></a>Définition de structure  
  
```  
typedef enum QueueUsage {  
      Normal       = 0,  
      Transmission = 1  
} QueueUsage;  
  
typedef enum ResultCode {  
      QueueAlreadyExists                     = 0, //  no bits set  
      QueueCreated                           = 1, //  QueueCreated  
      QueueCreatedAndRemoteDefinitionUpdated = 5, //  QueueCreated | RemoteDefinitionUpdated  
      QueueAndRemoteDefinitionCreated        = 7, //  QueueCreated | RemoteDefinitionCreated | RemoteDefinitionUpdated  
      QueueDoesNotExist                      = 8, //  QueueDoesNotExist  
      QueueDeleted                           = 16 //  QueueDeleted  
} ResultCode;  
```  
  
### <a name="interface-definition"></a>Définition d'interface  
  
```  
[  
            object,  
            uuid(E90AC1A6-657B-4680-AF6A-89F11113FB8B),  
            dual,  
            nonextensible,  
            helpstring("IMQSAdmin Interface"),  
            pointer_default(unique)  
]  
interface IMQSAdmin2 : IDispatch{  
  
HRESULT CreateQueue (  
[in]BSTR queueManager,  
[in]BSTR newQueueName,  
[in]QueueUsage usage,  
[in]BSTR remoteDefinition,  
[in]BSTR remoteQName,  
[in]BSTR remoteQMgrName,  
[in]BOOL updateExistingRemoteDefinition,  
[out, retval]ResultCode* resultCode);  
  
HRESULT DeleteQueue (  
[in]BSTR queueManager,  
[in]BSTR newQueueName,  
[out, retval]ResultCode* resultCode);  
};  
  
      [  
            uuid(412AF00D-7CA8-4d2a-AFF6-F61CE2E29A0D),  
            helpstring("MQSAdmin Class")  
      ]  
      coclass MQSAdmin  
      {  
            [default] interface IMQSAdmin2;  
      };  
  
```  
  
## <a name="examples"></a>Exemples  
 Effectuez les étapes de l'exemple 1 pour créer une application de console C# [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] permettant de créer ou de supprimer des files d'attente MQSeries.  
  
### <a name="example-1"></a>Exemple 1  
  
##### <a name="create-a-c-console-application-to-manage-mqseries-server-queues"></a>Pour créer une application de console C# permettant de gérer des files d'attente sur le serveur MQSeries  
  
1.  Créer une nouvelle Application Visual c# Console dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] portant le nom **MQSeriesQueues**.  
  
2.  Remplacez tout code existant dans le fichier Program.cs qui est généré par le code suivant :  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.Text;  
    using MQSAgentLib;  
  
    namespace MQSeriesQueues  
    {  
        class ManageQueues  
        {  
            public static void Main(string[] args)  
            {  
                // The first argument should be "c" (without quotes)  
                // to create a queue, anything else to delete a queue.  
                // The 2nd and 3rd arguments should be the name of   
                // the MQSeries Queue Manager and the name of   
                // the queue to be created or deleted for example  
                // the following usage will create the local   
                // queue testq for the Queue Manager QM_Test  
                // MQSeriesQueues c QM_Test testq  
                createordeleteQs(args[0], args[1], args[2]);  
            }  
  
            static void createordeleteQs(string Qswitch, string QMgr, string QName)  
            {   
            if ((Qswitch =="c" & (QMgr != null & QName != null)))  
                {  
                    CreateQueue(QMgr, QName);  
                }  
                else if(QMgr != null & QName != null)  
                {  
                    DeleteQueue(QMgr, QName);  
                }  
             }  
  
            static void CreateQueue(string Qmgr, string Qname)  
            {  
                MQSAdmin admin = new MQSAdmin();    
  
                ResultCode resultCode = admin.CreateQueue(Qmgr, Qname, 0, "", "", "", 0);  
  
                if ((resultCode & ResultCode.QueueCreated) == ResultCode.QueueCreated)  
                {  
                    Console.WriteLine("Queue Created.");  
                }  
                else if ((resultCode & ResultCode.QueueAlreadyExists) == ResultCode.QueueAlreadyExists)  
                {  
                    Console.WriteLine("Queue Already Exists.");  
                }  
            }  
  
            static void DeleteQueue(string Qmgr, string Qname)  
            {  
                MQSAdmin admin = new MQSAdmin();  
  
                ResultCode resultCode = admin.DeleteQueue(Qmgr, Qname);  
  
                if ((resultCode & ResultCode.QueueDeleted) == ResultCode.QueueDeleted)  
                {  
                    Console.WriteLine("Queue successfully deleted.");  
                }  
                if ((resultCode & ResultCode.QueueDoesNotExist) == ResultCode.QueueDoesNotExist)  
                {  
                    Console.WriteLine("Queue did not exist anyway!");  
                }  
            }  
  
        }  
    }  
    ```  
  
3.  Ajoutez une référence à ce projet dans le **bibliothèque de types MQSAgent 1.0**. Le **MQSAgent 1.0 Type Library** est disponible sur le **COM** onglet de la **ajouter une référence** boîte de dialogue.  
  
    > [!NOTE]
    >  Le composant MQSAgent COM+ doit être installé sur l'ordinateur à partir duquel vous exécutez cette application de console. Pour plus d’informations sur l’installation du composant MQSAgent COM + voir [à l’aide de l’Assistant de Configuration de MQSAgent COM +](../core/using-the-mqsagent-com-configuration-wizard.md).  
  
4.  Créez l'application de console.  
  
5.  Ouvrez une invite de commandes dans le même répertoire que celui de l'application de console compilée.  
  
6.  Tapez le nom de l'application de console compilée avec les arguments adéquats, puis appuyez sur ENTRÉE. Par exemple, pour supprimer la file d’attente **testq** pour le Gestionnaire de file d’attente **QM_Test** vous tapez le texte suivant à l’invite de commandes et appuyez sur ENTRÉE :  
  
    ```  
    MQSeriesQueues d QM_Test testq  
    ```  
  
7.  Pour créer la file d’attente **testq** pour le Gestionnaire de file d’attente **QM_Test** vous tapez le texte suivant à l’invite de commandes et appuyez sur ENTRÉE :  
  
    ```  
    MQSeriesQueues c QM_Test testq  
    ```