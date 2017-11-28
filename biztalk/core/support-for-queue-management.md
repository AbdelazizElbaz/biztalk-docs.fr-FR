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
# <a name="support-for-queue-management"></a><span data-ttu-id="afe83-102">Prise en charge de la gestion des files d'attente</span><span class="sxs-lookup"><span data-stu-id="afe83-102">Support for Queue Management</span></span>
<span data-ttu-id="afe83-103">Grâce à l'adaptateur MQSeries [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], vous pouvez maintenant créer et supprimer des files d'attente à distance dans le gestionnaire de file d'attente MQSeries.</span><span class="sxs-lookup"><span data-stu-id="afe83-103">With the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] MQSeries adapter you can now create and delete queues remotely on the MQSeries Queue Manager.</span></span> <span data-ttu-id="afe83-104">Cette fonctionnalité est prise en charge car [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] utilise un objet MQSAgent COM+ distant qui communique directement avec le gestionnaire de file d'attente MQSeries.</span><span class="sxs-lookup"><span data-stu-id="afe83-104">This is supported because [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] uses a remote MQSAgent COM+ object that communicates directly with the MQSeries Queue Manager.</span></span> <span data-ttu-id="afe83-105">Généralement, cet objet MQSAgent est utilisé au moment de l'exécution pour lire et écrire des messages dans les files d'attente du serveur MQSeries distant.</span><span class="sxs-lookup"><span data-stu-id="afe83-105">Typically this MQSAgent is used at run time to read and write messages to the remote MQSeries Server queues.</span></span> <span data-ttu-id="afe83-106">Plusieurs serveurs BizTalk peuvent être clients de ce service distant.</span><span class="sxs-lookup"><span data-stu-id="afe83-106">More than one BizTalk server can be a client of this remote service.</span></span> <span data-ttu-id="afe83-107">En outre, les fonctionnalités de création et de suppression de files d'attente sont fournies par ce composant MQSAgent et peuvent être appelées directement à partir d'une orchestration ou d'un adaptateur.</span><span class="sxs-lookup"><span data-stu-id="afe83-107">Additionally, queue creation and deletion functions are provided by this MQSAgent and can be called directly from within an orchestration or adapter.</span></span> <span data-ttu-id="afe83-108">Cela rend possible des scénarios hautement dynamiques dans lesquels l'orchestration ou l'adaptateur peut créer une file d'attente temporaire, y envoyer un message, recevoir une réponse sur une autre file d'attente, puis supprimer la file d'attente temporaire.</span><span class="sxs-lookup"><span data-stu-id="afe83-108">This allows for highly dynamic scenarios whereby the orchestration or adapter can create a temporary queue and then send a message on it, receive a reply on another queue, and finally delete the temporary queue.</span></span>  
  
## <a name="createqueue-and-deletequeue-apis"></a><span data-ttu-id="afe83-109">API CreateQueue et DeleteQueue</span><span class="sxs-lookup"><span data-stu-id="afe83-109">CreateQueue and DeleteQueue APIs</span></span>  
 <span data-ttu-id="afe83-110">Les API CreateQueue et DeleteQueue sont définies comme suit :</span><span class="sxs-lookup"><span data-stu-id="afe83-110">The CreateQueue and DeleteQueue APIs are defined as follows.</span></span>  
  
### <a name="structure-definition"></a><span data-ttu-id="afe83-111">Définition de structure</span><span class="sxs-lookup"><span data-stu-id="afe83-111">Structure Definition</span></span>  
  
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
  
### <a name="interface-definition"></a><span data-ttu-id="afe83-112">Définition d'interface</span><span class="sxs-lookup"><span data-stu-id="afe83-112">Interface Definition</span></span>  
  
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
  
## <a name="examples"></a><span data-ttu-id="afe83-113">Exemples</span><span class="sxs-lookup"><span data-stu-id="afe83-113">Examples</span></span>  
 <span data-ttu-id="afe83-114">Effectuez les étapes de l'exemple 1 pour créer une application de console C# [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] permettant de créer ou de supprimer des files d'attente MQSeries.</span><span class="sxs-lookup"><span data-stu-id="afe83-114">Complete the steps in Example 1 to create a [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] C# console application which can be used to create or delete MQSeries Server queues.</span></span>  
  
### <a name="example-1"></a><span data-ttu-id="afe83-115">Exemple 1</span><span class="sxs-lookup"><span data-stu-id="afe83-115">Example 1</span></span>  
  
##### <a name="create-a-c-console-application-to-manage-mqseries-server-queues"></a><span data-ttu-id="afe83-116">Pour créer une application de console C# permettant de gérer des files d'attente sur le serveur MQSeries</span><span class="sxs-lookup"><span data-stu-id="afe83-116">Create a C# console application to manage MQSeries Server queues</span></span>  
  
1.  <span data-ttu-id="afe83-117">Créer une nouvelle Application Visual c# Console dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] portant le nom **MQSeriesQueues**.</span><span class="sxs-lookup"><span data-stu-id="afe83-117">Create a new Visual C# Console Application in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] with the name **MQSeriesQueues**.</span></span>  
  
2.  <span data-ttu-id="afe83-118">Remplacez tout code existant dans le fichier Program.cs qui est généré par le code suivant :</span><span class="sxs-lookup"><span data-stu-id="afe83-118">Replace any existing code in the Program.cs file that is generated with the code below:</span></span>  
  
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
  
3.  <span data-ttu-id="afe83-119">Ajoutez une référence à ce projet dans le **bibliothèque de types MQSAgent 1.0**.</span><span class="sxs-lookup"><span data-stu-id="afe83-119">Add a reference to this project to the **MQSAgent 1.0 Type Library**.</span></span> <span data-ttu-id="afe83-120">Le **MQSAgent 1.0 Type Library** est disponible sur le **COM** onglet de la **ajouter une référence** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="afe83-120">The **MQSAgent 1.0 Type Library** is available on the **COM** tab of the **Add reference** dialog box.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="afe83-121">Le composant MQSAgent COM+ doit être installé sur l'ordinateur à partir duquel vous exécutez cette application de console.</span><span class="sxs-lookup"><span data-stu-id="afe83-121">The MQSAgent COM+ component must be installed on the computer that you are running this console application from.</span></span> <span data-ttu-id="afe83-122">Pour plus d’informations sur l’installation du composant MQSAgent COM + voir [à l’aide de l’Assistant de Configuration de MQSAgent COM +](../core/using-the-mqsagent-com-configuration-wizard.md).</span><span class="sxs-lookup"><span data-stu-id="afe83-122">For more information about installing the MQSAgent COM+ component see [Using the MQSAgent COM+ Configuration Wizard](../core/using-the-mqsagent-com-configuration-wizard.md).</span></span>  
  
4.  <span data-ttu-id="afe83-123">Créez l'application de console.</span><span class="sxs-lookup"><span data-stu-id="afe83-123">Build the console application.</span></span>  
  
5.  <span data-ttu-id="afe83-124">Ouvrez une invite de commandes dans le même répertoire que celui de l'application de console compilée.</span><span class="sxs-lookup"><span data-stu-id="afe83-124">Open a command prompt in the same directory as the compiled console application.</span></span>  
  
6.  <span data-ttu-id="afe83-125">Tapez le nom de l'application de console compilée avec les arguments adéquats, puis appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="afe83-125">Type the name of the compiled console application with the appropriate arguments and press ENTER.</span></span> <span data-ttu-id="afe83-126">Par exemple, pour supprimer la file d’attente **testq** pour le Gestionnaire de file d’attente **QM_Test** vous tapez le texte suivant à l’invite de commandes et appuyez sur ENTRÉE :</span><span class="sxs-lookup"><span data-stu-id="afe83-126">For example, to delete the queue **testq** for the Queue Manager **QM_Test** you would type the following text at the command prompt and press ENTER:</span></span>  
  
    ```  
    MQSeriesQueues d QM_Test testq  
    ```  
  
7.  <span data-ttu-id="afe83-127">Pour créer la file d’attente **testq** pour le Gestionnaire de file d’attente **QM_Test** vous tapez le texte suivant à l’invite de commandes et appuyez sur ENTRÉE :</span><span class="sxs-lookup"><span data-stu-id="afe83-127">To create the queue **testq** for the Queue Manager **QM_Test** you would type the following text at the command prompt and press ENTER:</span></span>  
  
    ```  
    MQSeriesQueues c QM_Test testq  
    ```