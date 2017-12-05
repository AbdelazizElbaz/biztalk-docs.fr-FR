---
title: MQSCorrelationSetOrchestrationWithSolicitResponse (exemple BizTalk Server) | Documents Microsoft
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
ms.assetid: 5127d743-bb79-4e97-a2f3-446892e1bfa0
caps.latest.revision: "29"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 79d92ca7a65262d18a08cab700710284accfbf78
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="mqscorrelationsetorchestrationwithsolicitresponse-biztalk-server-sample"></a>MQSCorrelationSetOrchestrationWithSolicitResponse (exemple BizTalk Server)
L'exemple MQSCorrelationSetOrchestrationWithSolicitResponse illustre l'utilisation d'un identificateur de corrélation produit par le serveur MQSeries au lieu de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
## <a name="what-this-sample-does"></a>Fonctions de l'exemple  
 L’orchestration envoie un message avec une valeur vide pour le **MQMD_MsgID** propriété dans l’en-tête du message. MQSeries génère le message et corrélation et renvoie un message avec une valeur attribuée à **MQMD_MsgID** et **MQMD_CorrelId** port de l’adaptateur d’envoi dans le cadre de la réponse de sollicitation-réponse . L’orchestration utilise l’identificateur de corrélation généré pour initialiser l’ensemble de corrélations et l’emplacement de réception suit cet ensemble dans une ultérieure en vérifiant la **MQMD_CorrelId** propriété du message. L’adaptateur affecte également l’identificateur de corrélation pour **BizTalk_CorrelationID**, que vous pouvez également utiliser dans une orchestration. Pour plus d’informations sur l’utilisation des identificateurs de corrélation avec l’adaptateur, consultez [mise en corrélation de demande-réponse d’à l’aide des Messages](../core/correlating-messages-using-request-reply.md).  
  
> [!IMPORTANT]
>  Les orchestrations utilisant cette technique peuvent rencontrer des problèmes si le message du serveur MQSeries arrive avant l'identificateur de corrélation. Veillez à définir vos orchestrations de façon à laisser un délai suffisant au serveur MQSeries pour le renvoi de l'identificateur de corrélation. L'exemple ne tient pas compte de cette condition d'engorgement possible.  
  
## <a name="where-to-find-this-sample"></a>Accès à l'exemple  
 *\<Exemples de chemin d’accès\>*\AdaptersUsage\MQSeriesAdapter\MQSCorrelationSetOrchestrationWithSolicitResponse  
  
 Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.  
  
|**Fichier**|**Description**|  
|--------------|---------------------|  
|**MQSCorrelationSolicitResponse.btproj,**<br /><br /> **MQSCorrelationSolicitResponse.sln**|Fichiers de projet et de solution de l'application.|  
|**MQSCorrelationSolicitResponse.odx**|Fichier d'orchestration BizTalk de l'application.|  
|**MQSCorrelationSolicitResponse.snk**|Fichier de clé de nom fort.|  
|Setup.bat|Crée et initialise l'exemple.|  
  
## <a name="how-to-use-this-sample"></a>L’utilisation de cet exemple  
 Pour créer l'application, procédez comme suit :  
  
-   Créez deux files d'attente MQSeries.  
  
-   Configurez un emplacement de réception et un port d'envoi [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
-   Activez l'emplacement de réception  
  
-   démarrez le port d'envoi.  
  
-   Créez les dossiers appropriés.  
  
-   Modifiez l'orchestration.  
  
-   Déployez, liez et démarrez l'orchestration.  
  
 Si vous disposez des autorisations nécessaires à l'installation du serveur MQSeries pour Windows, vous pouvez créer les files d'attente MQSeries à l'aide des boîtes de dialogue de l'adaptateur et ignorer la procédure suivante. Sinon, vous pouvez créer les files d'attente à l'aide d'IBM WebSphere MQ Explorer. Pour créer les files d’attente à le WebSphere MQ Explorer, procédez comme suit.  
  
## <a name="creating-the-mqseries-queues-through-the-websphere-mq-explorer"></a>Création des files d'attente MQSeries à l'aide de WebSphere MQ Explorer  
  
#### <a name="to-create-the-mqseries-queues-through-the-websphere-mq-explorer"></a>Pour créer les files d'attente MQSeries à l'aide de WebSphere MQ Explorer  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **IBM WebSphere MQ**, puis cliquez sur **WebSphere MQ Explorer**.  
  
2.  Double-cliquez sur **gestionnaires de file d’attente**, puis double-cliquez sur le Gestionnaire de file d’attente par défaut. Le Gestionnaire de file d’attente par défaut est généralement nommé **QM_***< nom_ordinateur >* où *Nom_Ordinateur* est le nom de votre ordinateur.  
  
3.  Avec le bouton droit **les files d’attente**, pointez sur **nouveau**, puis cliquez sur **file d’attente locale**.  
  
4.  Dans **créer une file d’attente locale** boîte de dialogue **nom de la file d’attente**, tapez « REPLYTOQ », puis cliquez sur **OK**.  
  
5.  Avec le bouton droit **les files d’attente**, cliquez sur **nouveau**, puis cliquez sur **file d’attente locale**.  
  
6.  Dans le **créer une file d’attente locale** boîte de dialogue **nom de la file d’attente**, tapez « SOLICITRESPONSEQ », puis cliquez sur **OK**.  
  
## <a name="creating-the-receive-location-and-the-mqseries-queue"></a>Création de l'emplacement de réception et de la file d'attente MQSeries  
 Cette procédure permet de créer le port d'envoi et l'emplacement de réception pour envoyer le message à MQSeries et recevoir le message de corrélation de MQSeries. Le cas échéant, la file d'attente MQSeries est également créée lorsque vous créez l'emplacement de réception.  
  
#### <a name="to-create-the-receive-location-and-the-mqseries-queue"></a>Pour créer l’emplacement de réception et de la file d’attente MQSeries  
  
1.  Ouvrez la console Administration de BizTalk Server.  
  
2.  Développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, puis développez l’application requise.  
  
3.  Avec le bouton droit **Ports de réception**, pointez sur **nouveau**, puis cliquez sur **Port de réception unidirectionnel**.  
  
4.  Dans le **propriétés du Port de réception unidirectionnel** boîte de dialogue le **nom** , tapez « MQReply » et cliquez sur **OK**.  
  
5.  Dans le volet gauche, cliquez sur **emplacements de réception** onglet, puis cliquez sur **nouveau**.  
  
6.  Dans le **propriétés de l’emplacement de réception** boîte de dialogue le **nom** , tapez « MQReply ».  
  
7.  Dans le **Type de Transport** boîte, sélectionnez **MQSeries**.  
  
8.  Dans le **Gestionnaire de réception** boîte, sélectionnez **BizTalkServerApplication**.  
  
9. Dans le **pipeline de réception** boîte, sélectionnez **Microsoft.BizTalk.DefaultPipelines.PassThruReceive**.  
  
10. Cliquez sur **configurer**.  
  
11. Dans le **propriétés du Transport MQSeries** boîte de dialogue le **fréquence d’interrogation** , tapez « 10 ».  
  
12. Dans le **définition file d’attente** , cliquez sur le bouton de sélection (...).  
  
13. Dans le **définition file d’attente** boîte de dialogue le **nom du serveur** , tapez le nom de votre ordinateur.  
  
14. Dans le **Gestionnaire de file d’attente** , sélectionnez le Gestionnaire de file d’attente par défaut.  
  
15. Dans le **file d’attente** zone, tapez « REPLYTOQ », puis cliquez sur **exporter**.  
  
16. Dans le **exporter** boîte de dialogue, cliquez sur **créer une file d’attente**, puis cliquez sur**OK**ou **fait** jusqu'à ce que vous avez terminé toutes les boîtes de dialogue.  
  
## <a name="creating-the-send-port-and-mqseries-queue"></a>Création du port d'envoi et de la file d'attente MQSeries  
  
#### <a name="to-create-the-send-port-and-mqseries-queue"></a>Pour créer le port d'envoi et la file d'attente MQSeries  
  
1.  Avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi unidirectionnel statique**.  
  
2.  Dans le **propriétés de Port d’envoi** boîte de dialogue le **nom** , tapez « MQSolicitResponse ».  
  
3.  Dans le **Type de Transport** boîte, sélectionnez **MQSeries**.  
  
4.  Dans le **pipeline d’envoi** boîte, sélectionnez **Microsoft.BizTalk.DefaultPipelines.PassThruTransmit**.  
  
5.  Dans le **pipeline de réception** boîte, sélectionnez **Microsoft.BizTalk.DefaultPipelines.PassThruReceive**.  
  
6.  Cliquez sur **configurer**.  
  
7.  Dans le **propriétés du Transport MQSeries** boîte de dialogue le **définition file d’attente** , cliquez sur le bouton de sélection (...).  
  
8.  Dans le **définition file d’attente** boîte de dialogue le **nom du serveur** , tapez le nom de votre ordinateur.  
  
9. Dans le **Gestionnaire de file d’attente** , sélectionnez le Gestionnaire de file d’attente par défaut.  
  
10. Dans le **file d’attente** zone, tapez « SOLICITRESPONSEQ », puis cliquez sur **exporter**.  
  
11. Dans la boîte de dialogue Exporter, cliquez sur **créer une file d’attente**, puis cliquez sur **OK** ou **fait** jusqu'à ce que vous avez terminé toutes les boîtes de dialogue.  
  
## <a name="enabling-the-receive-location-and-starting-the-send-port"></a>L’activation de l’emplacement de réception et démarrer le Port d’envoi  
 Cette procédure permet de créer les dossiers requis pour recevoir le fichier dans l'orchestration et envoyer le message corrélé et le message de réponse vers les dossiers de sortie.  
  
#### <a name="to-enable-the-receive-location-and-start-the-send-port"></a>Activation de l'emplacement de réception et démarrage du port d'envoi  
  
1.  Dans la console Administration de BizTalk Server, cliquez sur **Ports de réception**.  
  
2.  Dans le volet détails, cliquez sur le **MQIn** emplacement de réception et cliquez sur **activer**.  
  
3.  Dans le volet détails, cliquez sur le **MQOut** port d’envoi, puis cliquez sur **Démarrer.**  
  
## <a name="creating-the-folders-used-by-the-application"></a>Création des dossiers utilisés par l'application  
  
#### <a name="to-create-the-folders-used-by-the-application"></a>Pour créer les dossiers utilisés par l'application  
  
1.  Créez un dossier nommé « temp » sur votre disque C:\, le cas échéant.  
  
2.  Créer des dossiers sous le **C:\temp** répertoire nommé « Pickup2 », « Dropit2 » et « MoveIt ».  
  
## <a name="modifying-the-orchestration-used-by-the-application"></a>Modification de l'orchestration utilisée par l'application  
 Cette procédure permet de modifier l'orchestration utilisée par l'application.  
  
||  
|-|  
|Pour modifier l'orchestration utilisée par l'application|  
|-Dans Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], double-cliquez sur le fichier solution **MQSCorrelationSolicitResponse.sln**, pour ouvrir la solution.<br /><br /> -Dans le volet de l’Explorateur de solutions, double-cliquez sur l’orchestration **MQSCorrelationSolicitResponse.odx** pour afficher l’orchestration.<br /><br /> -Double-cliquez sur la forme assignation du message **MessageAssignment_1** pour lancer l’éditeur d’Expression BizTalk.<br /><br /> -Entrez le nom de gestionnaire de file d’attente MQSeries approprié pour l’expression suivante :<br /><br /> `MQSeriesRequestSendMessage(MQSeries.MQMD_ReplyToQMgr) = "QM_<machine_name>";`<br /><br /> -Si vous souhaitez que le message de réponse envoyé par BizTalk pour contenir la totalité du message d’origine à la place uniquement les 100 premiers octets, modifiez la ligne suivante dans l’éditeur d’Expression BizTalk.<br /><br /> -Ligne d’origine :<br /><br /> `MQSeriesRequestSendMessage(MQSeries.MQMD_Report) = 768;`<br /><br /> Ligne modifiée :<br /><br /> `MQSeriesRequestSendMessage(MQSeries.MQMD_Report) = 1792;`<br /><br /> -Dans l’éditeur d’Expression BizTalk, cliquez sur **OK** pour enregistrer l’expression modifiée.<br /><br /> -En [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], sélectionnez **fichier**, puis sélectionnez **Enregistrer tout**.|  
  
## <a name="building-and-deploying-the-sample"></a>Génération et déploiement de l’exemple  
 Cette procédure permet de créer et de déployer la solution contenant l'orchestration utilisée dans cette application.  
  
#### <a name="to-build-and-deploy-the-sample"></a>Pour créer et déployer l'exemple  
  
1.  Dans une fenêtre de commande, accédez au dossier suivant :  
  
     `<Samples Path>\AdaptersUsage\MQSeriesAdapter\MQSCorrelationSetOrchestrationWithSolicitResponse`  
  
2.  Exécutez le fichier Setup.bat, qui effectue les actions suivantes :  
  
    1.  création d'une clé de nom fort pour le projet ;  
  
    2.  compilation et déploiement du projet d'orchestration.  
  
    3.  création d'un port d'envoi et d'un port de réception avec l'adaptateur FILE.  
  
    > [!NOTE]
    >  Cette orchestration spécifie les liaisons pour l'envoi et la réception de fichiers avec l'adaptateur FILE. Aussi, lorsque vous déployez l'orchestration, les ports d'envoi, le port de réception et l'emplacement de réception requis sont créés pour la réception d'un fichier dans l'orchestration et la génération du message de corrélation et du message de réponse.  
  
## <a name="binding-and-starting-the-orchestration"></a>Liaison et démarrage de l'orchestration  
 Cette procédure permet de lier l'orchestration à l'hôte, ainsi qu'aux ports d'envoi et emplacements de réception appropriés.  
  
#### <a name="to-bind-and-start-the-orchestration"></a>Pour lier et démarrer l'orchestration  
  
1.  Dans la console Administration de BizTalk Server, développez le **Orchestrations** dossier.  
  
2.  Dans le volet détails, cliquez sur le **MQSCorrelationSolicitResponse** orchestration et cliquez sur **lier**.  
  
3.  Liez les ports d'orchestration aux ports d'envoi et aux emplacements de réception suivants :  
  
    |**Port d’orchestration**|**Port de messagerie / emplacement de réception**|  
    |----------------------------|--------------------------------------------|  
    |FileReceivePort|MQSCorrelationSolicitResponse.Orchestration.FileReceivePort|  
    |MQSeriesResponseReceivePort|MQReply|  
    |SolicitResponsePort|MQSolicitResponse|  
    |TempPort|MQSCorrelationSolicitResponse.Orchestration.TempPort|  
    |FileSendPort|MQSCorrelationSolicitResponse.Orchestration.FileSendPort|  
  
4.  Cliquez sur **hôte**.  
  
5.  Dans le **hôte** boîte, sélectionnez **BizTalkServerApplication** et cliquez sur **OK**.  
  
6.  Dans **Ports d’envoi**, avec le bouton droit **MQSCorrelationSolicitResponse.Orchestration.TempPort**, puis sélectionnez **Démarrer**.  
  
7.  Dans **Ports d’envoi**, avec le bouton droit **MQSCorrelationSolicitResponse.Orchestration.FileSendPort**, puis sélectionnez **Démarrer**.  
  
8.  Dans **emplacements de réception**, avec le bouton droit **MQSCorrelationSolicitResponse.Orchestration.FileReceivePort**, puis sélectionnez **activer**.  
  
9. Avec le bouton droit de l’orchestration, puis cliquez sur **Démarrer**.  
  
    > [!NOTE]
    >  Le démarrage de l'orchestration inscrit l'orchestration automatiquement.  
  
## <a name="testing-the-application"></a>Test de l'application  
 Cette procédure permet de tester l'application.  
  
#### <a name="to-test-the-application"></a>Pour tester l'application  
  
1.  Placez un fichier dans le **C:\Temp\Pickup2** dossier.  
  
2.  Examinez les fichiers dans le **C:\Temp\Dropit2** dossier et le **C:\Temp\Moveit**dossier.  
  
    -   Le **C:\Temp\Dropit2** dossier doit contenir une copie du message qui a été récupéré à l’origine par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
    -   Le **C:\Temp\Moveit**dossier doit contenir un document de réponse avec l’identificateur de message (MQMD_MsgId) et l’identificateur de corrélation (MQMD_CorrelId).  
  
    > [!NOTE]
    >  Si vous désactivez le **MQReply** emplacement de réception, vous pouvez examiner le message dans WebSphere MQ Explorer et vérifier que les identificateurs de message et de corrélation sont définis. Pour ce faire, lancez le **WebSphere MQ Explorer** et examinez le message placé dans le **REPLYTOQ** file d’attente. Les identificateurs de message et de corrélation sont affichés sur la **identificateurs** onglet de la **Messageproperties** boîte de dialogue.  
  
## <a name="see-also"></a>Voir aussi  
 [Mise en corrélation des Messages à l’aide de la demande-réponse](../core/correlating-messages-using-request-reply.md)   
 [Exemples d’adaptateurs MQSeries](../core/mqseries-adapter-samples.md)