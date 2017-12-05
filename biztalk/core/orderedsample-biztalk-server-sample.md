---
title: OrderedSample (exemple BizTalk Server) | Documents Microsoft
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
- MQSeries adapters, examples
ms.assetid: 7e59ff43-d425-40cd-9725-af13084f83d9
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1b9e93c7bb9cb59088e465dc53dd992ffd5f1c11
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="orderedsample-biztalk-server-sample"></a>OrderedSample (exemple BizTalk Server)
L'exemple OrderedSample illustre l'utilisation d'une orchestration pour recevoir et envoyer une série classée de messages de manière cyclique.  
  
## <a name="what-this-sample-does"></a>Fonctions de l'exemple  
 Cet exemple part du principe qu'il existe des messages dans la file d'attente MQSeries à partir de laquelle il reçoit les messages. L'adaptateur lit les messages de la file d'attente MQSeries dans l'ordre chronologique, puis il les envoie à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
 Le port de réception dans l’orchestration, **mqreceive**, a ses **livraison chronologique des messages** propriété **True**.  
  
 Au niveau de l'envoi, l'orchestration envoie un message puis attend un accusé de réception avant d'expédier le suivant. Le port d’envoi, **mqsend** a son **accusé de réception** propriété **transmis**. Pour simplifier l'exemple, l'orchestration utilise une boucle infinie.  
  
 L'orchestration peut recevoir des lots de messages et des messages individuels.  
  
## <a name="where-to-find-this-sample"></a>Accès à l'exemple  
 *\<Exemples de chemin d’accès\>*\AdaptersUsage\MQSeriesAdapter\OrderedSample  
  
 Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.  
  
|Fichier| Description|  
|----------|-----------------|  
|OrderedReceiveSend.btproj,<br /><br /> OrderedReceiveSend.sln|Fichiers de projet et de solution de l'application.|  
|OrderedReceiveSendOrchestration.odx|Orchestration de l'application.|  
|OrderedSample.snk|Fichier de clé de nom fort.|  
|**Setup.bat**|Crée et initialise l'exemple.|  
  
## <a name="building-and-running-the-sample"></a>Création et exécution de l'exemple  
  
#### <a name="to-build-and-deploy-the-sample"></a>Pour créer et déployer l'exemple  
  
1.  Dans une fenêtre de commande, accédez au dossier suivant :  
  
     `<Samples Path>\AdaptersUsage\MQSeriesAdapter\OrderedSample`  
  
2.  Exécutez le fichier Setup.bat, qui effectue les actions suivantes :  
  
    1.  création d'une clé de nom fort pour le projet ;  
  
    2.  compilation et déploiement du projet d'orchestration.  
  
 Si vous disposez des autorisations nécessaires à l'installation du serveur MQSeries pour Windows, vous pouvez créer les files d'attente MQSeries à l'aide des boîtes de dialogue de l'adaptateur et ignorer la procédure suivante. Sinon, vous pouvez créer les files d'attente à l'aide d'IBM WebSphere MQ Explorer. Pour créer les files d’attente à le WebSphere MQ Explorer, procédez comme suit.  
  
## <a name="creating-the-mqseries-queues-through-the-websphere-mq-explorer"></a>Création des files d'attente MQSeries à l'aide de WebSphere MQ Explorer  
  
#### <a name="to-create-the-mqseries-queues-through-the-websphere-mq-explorer"></a>Pour créer les files d'attente MQSeries à l'aide de WebSphere MQ Explorer  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **IBM WebSphere MQ**, puis cliquez sur **WebSphere MQ Explorer**.  
  
2.  Double-cliquez sur **gestionnaires de file d’attente**, puis double-cliquez sur le **Gestionnaire de file d’attente par défaut**. Celui-ci est généralement nommé QM_<nom_ordinateur>, où nom_ordinateur correspond au nom de votre ordinateur.  
  
3.  Avec le bouton droit **les files d’attente**, pointez sur **nouveau**, puis cliquez sur **file d’attente locale**.  
  
4.  Dans **créer une file d’attente locale** boîte de dialogue **nom de la file d’attente**, type **« queue1 »**, puis cliquez sur **OK**.  
  
5.  Avec le bouton droit **les files d’attente**, cliquez sur **nouveau**, puis cliquez sur **file d’attente locale**.  
  
6.  Dans le **créer une file d’attente locale** boîte de dialogue **nom de la file d’attente**, type **« queue2 »**, puis cliquez sur **OK**.  
  
## <a name="creating-the-receive-location-and-the-mqseries-queue"></a>Création de l'emplacement de réception et de la file d'attente MQSeries  
 Cette procédure permet de créer le port d'envoi et l'emplacement de réception pour envoyer le message à MQSeries et recevoir le message de corrélation de MQSeries. Le cas échéant, la file d'attente MQSeries est également créée lorsque vous créez l'emplacement de réception.  
  
#### <a name="to-create-the-receive-location-and-the-mqseries-queue"></a>Pour créer l’emplacement de réception et de la file d’attente MQSeries  
  
1.  Ouvrez la console Administration de BizTalk Server.  
  
2.  Développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, puis développez l’application requise.  
  
3.  Avec le bouton droit **Ports de réception**, pointez sur **nouveau**, puis cliquez sur **Port de réception unidirectionnel**.  
  
4.  Dans le **propriétés du Port de réception unidirectionnel** boîte de dialogue type, dans le **nom** zone **OrderedSampleReceive** et cliquez sur **OK**.  
  
5.  Dans le volet gauche, cliquez sur **emplacements de réception** onglet, puis cliquez sur **nouveau**.  
  
6.  Dans le **propriétés de l’emplacement de réception** boîte de dialogue le **nom** zone «**OrderedSampleReceiveLocation**».  
  
7.  Dans le **Type de Transport** boîte, sélectionnez **MQSeries**.  
  
8.  Dans le **Gestionnaire de réception** boîte, sélectionnez **BizTalkServerApplication**.  
  
9. Dans le **pipeline de réception** boîte, sélectionnez **Microsoft.BizTalk.DefaultPipelines.PassThruReceive**.  
  
10. Cliquez sur **configurer**.  
  
11. Dans le **propriétés du Transport MQSeries** boîte de dialogue le **fréquence d’interrogation** , tapez **« 10 »**.  
  
12. Dans le **définition file d’attente** , cliquez sur le **points de suspension (...)**  bouton.  
  
13. Dans le **définition file d’attente** boîte de dialogue le **nom du serveur** , tapez le nom de votre ordinateur.  
  
14. Dans le **Gestionnaire de file d’attente** boîte, sélectionnez le **Gestionnaire de file d’attente par défaut**.  
  
15. Dans le **file d’attente** , tapez « **queue1**», puis cliquez sur **exporter**.  
  
16. Dans le **exporter** boîte de dialogue, cliquez sur **créer une file d’attente**, puis cliquez sur **OK** ou **fait** jusqu'à ce que vous avez terminé toutes les boîtes de dialogue.  
  
## <a name="creating-the-send-port-and-mqseries-queue"></a>Création du port d'envoi et de la file d'attente MQSeries  
  
#### <a name="to-create-the-send-port-and-mqseries-queue"></a>Pour créer le port d'envoi et la file d'attente MQSeries  
  
1.  Avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi unidirectionnel statique**.  
  
2.  Dans le **propriétés du Port statique** boîte de dialogue type, dans le **nom** , tapez «**OrderedSampleSend**».  
  
3.  Dans le **Type de Transport** boîte, sélectionnez **MQSeries**.  
  
4.  Dans le **pipeline d’envoi** boîte, sélectionnez **Microsoft.BizTalk.DefaultPipelines.PassThruTransmit**.  
  
5.  Cliquez sur **configurer**.  
  
6.  Dans le **propriétés du Transport MQSeries** boîte de dialogue le **définition file d’attente** , cliquez sur le **points de suspension (...)**  bouton.  
  
7.  Dans le **définition file d’attente** boîte de dialogue le **nom du serveur** , tapez le nom de votre ordinateur.  
  
8.  Dans le **Gestionnaire de file d’attente** boîte, sélectionnez le **Gestionnaire de file d’attente par défaut**.  
  
9. Dans le **file d’attente** , tapez « **queue2**», puis cliquez sur **exporter**.  
  
10. Dans le **exporter** boîte de dialogue, cliquez sur **créer une file d’attente**, puis cliquez sur **OK** ou **fait** jusqu'à ce que vous avez terminé toutes les boîtes de dialogue.  
  
#### <a name="to-enable-the-receive-location-and-start-the-send-port"></a>Activation de l'emplacement de réception et démarrage du port d'envoi  
  
1.  Dans la console Administration de BizTalk Server, cliquez sur **Ports de réception**.  
  
2.  Dans le volet détails, cliquez sur le **MQIn** emplacement de réception et cliquez sur **activer**.  
  
3.  Dans le volet détails, cliquez sur le **MQOut** port d’envoi, puis cliquez sur **Démarrer.**  
  
#### <a name="to-bind-and-start-the-orchestration"></a>Pour lier et démarrer l’Orchestration  
  
1.  Dans la console Administration de BizTalk Server, développez le **Orchestrations** dossier.  
  
2.  Double-cliquez sur le **OrderedSampleOrchestration** orchestration, puis cliquez sur **liaisons**.  
  
3.  Liez les ports d'orchestration aux ports d'envoi et aux emplacements de réception suivants :  
  
    |Port d'orchestration|Port de messagerie/Emplacement de réception|  
    |------------------------|----------------------------------------|  
    |mqreceive|OrderedSampleReceive|  
    |mqsend|OrderedSampleSend|  
  
4.  Cliquez sur **hôte**.  
  
5.  Dans le **hôte** boîte, sélectionnez **BizTalkServerApplication**, puis cliquez sur **OK**.  
  
6.  Bouton droit sur le **Orchestration** et cliquez sur **Démarrer**.  
  
#### <a name="to-run-the-sample"></a>Pour exécuter l’exemple  
  
1.  Démarrez l'orchestration.  
  
2.  Placez les messages dans la file d'attente MQSeries dans laquelle a été configurée la lecture des messages par l'emplacement de réception.  
  
3.  À l'aide de WebSphere MQ Explorer, affichez les messages de la file d'envoi à partir de laquelle vous avez configuré l'envoi de messages via le port d'envoi.  
  
## <a name="see-also"></a>Voir aussi  
 [Exemples d’adaptateurs MQSeries](../core/mqseries-adapter-samples.md)