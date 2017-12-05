---
title: MQSCorrelationSetOrchestration (exemple BizTalk Server) | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- examples, MQSeries adapters
- orchestrations, examples
- examples, orchestrations
- examples, messages
- messages, examples
- MQSeries adapters, examples
ms.assetid: fcda65d0-e3ec-4ead-978d-3904903b8762
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 75ac63fe0fee593f927e854ce425ff7f631f9475
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="mqscorrelationsetorchestration-biztalk-server-sample"></a>MQSCorrelationSetOrchestration (exemple BizTalk Server)
L'exemple MQSCorrelationSetOrchestration illustre le mode d'utilisation de l'identificateur de corrélation MQSeries pour la corrélation de messages envoyés à une file d'attente MQSeries vers une orchestration en cours d'exécution. L’orchestration définit l’identificateur de corrélation MQSeries et le message à l’aide de valeurs d’identificateur de la **MQMD_CorrelId** et **MQMD_MsgID** propriétés. Le gestionnaire de file d'attente MQSeries copie la valeur MessageID dans la propriété CorrelationID du message.  
  
## <a name="prerequisites"></a>Conditions préalables  
 On suppose dans cet exemple que vous avez installé IBM WebSphere MQSeries sur le même serveur que celui sur lequel vous exécutez [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
## <a name="what-this-sample-does"></a>Fonctions de l'exemple  
 Cet exemple illustre la manière de définir un identificateur de message et un identificateur de corrélation dans un message envoyé à un serveur IBM WebSphere MQSeries Server. Il s'agit d'une méthode que vous pouvez utiliser pour mettre en corrélation un message avec une instance de l'orchestration en cours d'exécution. Lorsque le gestionnaire de file d'attente MQSeries reçoit le message, il copie la valeur MessageID dans la propriété CorrelationID du message. Cette propriété CorrelationID (**MQMD_CorrelId**) est ensuite utilisé dans l’orchestration pour associer le message de réponse sur MQSeries avec l’instance utilisée pour envoyer des messages à MQSeries.  
  
## <a name="how-this-sample-is-designed-and-why"></a>Cet exemple est conçu et pourquoi  
 Cet exemple illustre un scénario dans lequel un document en cours de traitement par une orchestration peut être envoyé à une file d'attente MQSeries (probablement en vue d'un traitement supplémentaire) et retourné à l'orchestration en cours d'exécution.  
  
## <a name="where-to-find-this-sample"></a>Accès à l'exemple  
 *\<Exemples de chemin d’accès\>*\AdaptersUsage\MQSeriesAdapter\MQSCorrelationSetOrchestration  
  
 Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.  
  
|**Fichier**|**Description**|  
|--------------|---------------------|  
|**MQSCorrelationSetOrchestration.btproj,**<br /><br /> **MQSCorrelationSetOrchestration.sln**|Fichiers de projet et de solution de l'application.|  
|**MQSCorrelationSetOrchestration.odx**|Orchestration de l'application.|  
|**MQSCorrelationSetOrchestration.snk**|Fichier de clé de nom fort.|  
|**Setup.bat**|Crée et initialise l'exemple.|  
  
## <a name="how-to-use-this-sample"></a>L’utilisation de cet exemple  
 Incorporez la logique de cet exemple si vous devez envoyer un message à MQSeries Server dans l'une des étapes du workflow général.  
  
### <a name="to-create-the-mqseries-queue-through-the-websphere-mq-explorer"></a>Pour créer la file d'attente MQSeries à l'aide de WebSphere MQ Explorer  
  
1.  Cliquez sur **Démarrer**, pointez sur **programmes**, pointez sur **IBM WebSphere MQ**, puis cliquez sur **WebSphere MQ Explorer**.  
  
2.  Double-cliquez sur **gestionnaires de file d’attente**, puis double-cliquez sur le Gestionnaire de file d’attente par défaut. Le Gestionnaire de file d’attente par défaut est généralement nommé **QM_ < nom_ordinateur >** où *Nom_Ordinateur* est le nom de votre ordinateur.  
  
3.  Avec le bouton droit **les files d’attente**, pointez sur **nouveau**, puis cliquez sur **file d’attente locale**.  
  
4.  Dans **créer une file d’attente locale** boîte de dialogue **nom de la file d’attente**, tapez « MQCorrelation », puis cliquez sur **OK**.  
  
### <a name="to-create-the-receive-location-and-the-mqseries-queue"></a>Pour créer l’emplacement de réception et de la file d’attente MQSeries  
  
1.  Ouvrez la console Administration de BizTalk Server.  
  
2.  Développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, puis développez l’application requise.  
  
3.  Avec le bouton droit **Ports de réception**, pointez sur **nouveau**, puis cliquez sur **Port de réception unidirectionnel**.  
  
4.  Dans le **propriétés du Port de réception unidirectionnel** boîte de dialogue le **nom** tapez « MQIn », puis cliquez sur **OK**.  
  
5.  Dans le volet gauche, cliquez sur **emplacements de réception** onglet, puis cliquez sur **nouveau**.  
  
6.  Dans le **propriétés de l’emplacement de réception** boîte de dialogue le **nom** , tapez « MQIn ».  
  
7.  Dans le **Type de Transport** boîte, sélectionnez **MQSeries**.  
  
8.  Dans le **Gestionnaire de réception** boîte, sélectionnez **BizTalkServerApplication**.  
  
9. Dans le **pipeline de réception** boîte, sélectionnez **Microsoft.BizTalk.DefaultPipelines.PassThruReceive**.  
  
10. Cliquez sur **configurer**.  
  
11. Dans le **propriétés du Transport MQSeries** boîte de dialogue le **fréquence d’interrogation** , tapez « 10 ».  
  
12. Dans le **définition file d’attente** , cliquez sur le bouton de sélection (...).  
  
13. Dans le **définition file d’attente** boîte de dialogue le **nom du serveur** , tapez le nom de votre ordinateur.  
  
14. Dans le **Gestionnaire de file d’attente** , sélectionnez le Gestionnaire de file d’attente par défaut.  
  
15. Dans le **file d’attente** zone, tapez « MQCorrelation », puis cliquez sur **exporter**.  
  
16. Dans le **exporter** boîte de dialogue, cliquez sur **créer une file d’attente**, puis cliquez sur**OK**ou **fait** jusqu'à ce que vous avez terminé toutes les boîtes de dialogue.  
  
### <a name="to-create-the-send-port-to-mqseries"></a>Pour créer le port d'envoi vers MQSeries  
  
1.  Avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi unidirectionnel statique**.  
  
2.  Dans le **propriétés de Port d’envoi** boîte de dialogue le **nom** , tapez « MQOut ».  
  
3.  Dans le **Type de Transport** boîte, sélectionnez **MQSeries**.  
  
4.  Dans le **pipeline d’envoi** boîte, sélectionnez **Microsoft.BizTalk.DefaultPipelines.PassThruTransmit**.  
  
5.  Cliquez sur **configurer**.  
  
6.  Dans le **propriétés du Transport MQSeries** boîte de dialogue le **définition file d’attente** , cliquez sur le bouton de sélection (...).  
  
7.  Dans le **définition file d’attente** boîte de dialogue le **nom du serveur** , tapez le nom de votre ordinateur.  
  
8.  Dans le **Gestionnaire de file d’attente** , sélectionnez le Gestionnaire de file d’attente par défaut.  
  
9. Dans le **file d’attente** zone, tapez « MQCorrelation », puis cliquez sur **OK**.  
  
10. Cliquez sur **OK** jusqu'à ce que vous avez terminé toutes les boîtes de dialogue.  
  
### <a name="to-enable-the-receive-location-and-start-the-send-port"></a>Activation de l'emplacement de réception et démarrage du port d'envoi  
  
1.  Dans la console Administration de BizTalk Server, cliquez sur **Ports de réception**.  
  
2.  Dans le volet détails, cliquez sur le **MQIn** emplacement de réception et cliquez sur **activer**.  
  
3.  Dans le volet détails, cliquez sur le **MQOut** port d’envoi, puis cliquez sur **Démarrer.**  
  
### <a name="to-create-the-folders-used-by-the-application"></a>Pour créer les dossiers utilisés par l'application  
  
1.  Sur votre **C:\\**  disque, créez un dossier nommé « temp » si elle n’existe pas déjà.  
  
2.  Sous le **C:\temp** active, créer des dossiers nommés « Pickup » et « Dropit ».  
  
### <a name="building-and-deploying-this-sample"></a>Création et déploiement de l'exemple  
  
1.  Dans une fenêtre de commande, accédez au dossier suivant :  
  
     `<Samples Path>\AdaptersUsage\MQSeriesAdapter\MQSCorrelationSetOrchestration`  
  
2.  Exécutez le fichier Setup.bat, qui effectue les actions suivantes :  
  
    1.  création d'une clé de nom fort pour le projet ;  
  
    2.  compilation et déploiement du projet d'orchestration.  
  
    3.  création d'un port d'envoi et d'un port de réception avec l'adaptateur FILE.  
  
### <a name="bind-and-start-the-orchestration"></a>Lier et démarrer l'orchestration  
  
1.  Dans la console Administration de BizTalk Server, développez le **Orchestrations** dossier.  
  
2.  Dans le volet détails, cliquez sur le **MQSCorrelationSetOrchestration** orchestration, puis cliquez sur **lier**.  
  
3.  Liez les ports d'orchestration aux ports d'envoi et aux emplacements de réception suivants :  
  
    |**Port d’orchestration**|**Port de messagerie / emplacement de réception**|  
    |----------------------------|--------------------------------------------|  
    |FileReceivePort|MQSCorrelationSetOrchestration.FileReceivePort|  
    |MQSeriesResponseReceivePort|MQIn|  
    |MQSeriesRequestSendPort|MQOut|  
    |FileSendPort|MQSCorrelationSetOrchestration.FileSendPort|  
  
4.  Cliquez sur **hôte**.  
  
5.  Dans le **hôte** boîte, sélectionnez **BizTalkServerApplication**, puis cliquez sur **OK**.  
  
6.  Dans **Ports d’envoi**, avec le bouton droit **MQSCorrelationSetOrchestration.FileSendPort**, puis sélectionnez **Démarrer**.  
  
7.  Dans **emplacements de réception**, avec le bouton droit **MQSCorrelationSetOrchestration.FileReceivePort** , puis sélectionnez **activer**.  
  
8.  Avec le bouton droit de l’orchestration, puis cliquez sur **Démarrer**.  
  
    > [!NOTE]
    >  Le démarrage de l'orchestration inscrit l'orchestration automatiquement.  
  
### <a name="to-test-the-application"></a>Pour tester l'application  
  
1.  Placez un fichier dans le **C:\Temp\Pickup** dossier.  
  
2.  Examinez le fichier dans le **C:\Temp\Dropit** dossier.  
  
    > [!NOTE]
    >  Si vous désactivez le **MQIn** emplacement de réception, vous pouvez examiner le message dans WebSphere MQ Explorer et vérifier que les identificateurs de message et de corrélation sont définis. Pour ce faire, lancez le **WebSphere MQ Explorer** et examinez le message placé dans le **MQCorrelation** file d’attente. Les identificateurs de message et de corrélation sont affichés sur la **identificateurs** onglet de la **propriétés du Message** boîte de dialogue.  
  
    > [!NOTE]
    >  Dans un scénario de production, vous souhaiterez probablement affecter un ID unique à chaque message envoyé vers la file d'attente MQSeries. Cela peut se faire en modifiant la forme Expression dans l'orchestration. Modifiez les lignes suivantes afin de définir ces propriétés avec un ID unique de 24 octets :  
    >   
    >  MQSeriesRequestSendMessageModified(MQSeries.MQMD_MsgId) = "111213141516171819202122232425262728293031323334";  
    >   
    >  MQSeriesRequestSendMessageModified(MQSeries.MQMD_CorrelId) = "111213141516171819202122232425262728293031323334";  
    >   
    >  Si vous souhaitez définir un ID unique de 24 octets pour ces propriétés, consultez la section **pour créer un ID unique de 24 octets pour les messages envoyés à MQSeries**.  
  
### <a name="to-create-a-unique-24-byte-id-for-messages-sent-to-mqseries"></a>Pour créer un ID unique de 24 octets pour les messages envoyés à MQSeries  
  
1.  Créez un nouveau projet de bibliothèque de classes C# dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].  
  
2.  Collez le code suivant dans le fichier .cs de la classe :  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.Text;  
    using System.Security.Cryptography;  
  
    namespace MQId  
    {[Serializable]  
        public class GetId  
        {  
            RNGCryptoServiceProvider randomCryptoString = new RNGCryptoServiceProvider();  
  
            public string getGuidstr()  
            {  
                byte[] newGuid = GetRandomData(24);  
                return ConvertToHex(newGuid);  
            }  
  
            private byte[] GetRandomData(int keySize)  
            {  
                byte[] randomData = new byte[keySize];  
                randomCryptoString.GetBytes(randomData);  
                return randomData;  
            }  
  
            private string ConvertToHex(byte[] key)  
            {  
                StringBuilder hexString = new StringBuilder();  
                for (int i = 0; i < key.Length; ++i)  
                {  
                    hexString.Append(String.Format("{0:X2}", key[i]));  
                }  
                return hexString.ToString();  
            }  
        }  
    }  
    ```  
  
3.  Spécifiez un **par défaut d’espace de noms** de **MQId** et un **nom de l’Assembly** de **GetId** sur les propriétés du projet **Application**  page.  
  
4.  Spécifiez un fichier de clé de nom fort pour signer l’assembly sur les propriétés du projet **signature** page et que vous générez le projet.  
  
5.  Utilisez l’outil global assembly cache (gacutil.exe) pour charger l’assembly compilé dans le Global Assembly Cache (gacutil /i \< *nom de fichier .dll compilé*\>).  
  
6.  Ajoutez une référence à l'assembly GetId dans le projet BizTalk pour cet exemple.  
  
7.  Ajoutez deux variables à l'orchestration utilisée dans cet exemple :  
  
    |Nom de la variable (identificateur)|Type|  
    |----------------------------------|----------|  
    |GetId|MQId.GetId|  
    |strGuid|System.String|  
  
8.  Collez le code suivant dans la forme Expression utilisée dans l'orchestration de cet exemple ; il doit remplacer le code existant :  
  
    ```  
    GetId = new MQId.GetId();  
    strGuid = GetId.getGuidstr();  
    MQSeriesRequestSendMessageModified = MQSeriesRequestSendMessage;  
    MQSeriesRequestSendMessageModified(MQSeries.MQMD_MsgId) = strGuid;  
    MQSeriesRequestSendMessageModified(MQSeries.MQMD_CorrelId) = strGuid;  
    ```  
  
9. Arrêtez et supprimez l'orchestration dans la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] si elle est déjà déployée. Puis suivez les étapes décrites dans les sections **génération et déploiement de l’exemple**, **lier et démarrer l’Orchestration** et **pour tester l’application**.  
  
    > [!NOTE]
    >  L'utilisation de cette méthode pour créer un ID unique de 24 octets pour les messages envoyés à MQSeries ne garantit pas à 100 % l'unicité des ID pour l'ensemble des messages, mais la probabilité d'ID de message en double est très faible. Si vos contraintes professionnelles nécessitent une garantie à 100 % de l'absence de doublons parmi les ID de message, vous devrez opter pour un code personnalisé différent pour atteindre cet objectif.  
  
## <a name="classes-or-methods-used-in-this-sample"></a>Classes ou méthodes utilisées dans l'exemple  
 Cet exemple ne fait pas un usage explicite des classes ou des méthodes.  
  
## <a name="see-also"></a>Voir aussi  
 [Mise en corrélation des Messages à l’aide de la demande-réponse](../core/correlating-messages-using-request-reply.md)   
 [Exemples d’adaptateurs MQSeries](../core/mqseries-adapter-samples.md)