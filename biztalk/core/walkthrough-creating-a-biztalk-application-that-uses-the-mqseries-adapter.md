---
title: "Procédure pas à pas : Création d’une Application BizTalk qui utilise l’adaptateur MQSeries | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IBM WebSphere MQ queues
- MQSeries adapters, tutorial
- MQSeries adapters, testing
- tutorials, MQSeries adapters
- MQSeries adapters, IBM WebSphere MQ queues
- testing, MQSeries adapters
- MQSeries adapters, queues
- configuring [MQSeries adapters], tutorial
ms.assetid: e9e169e4-d41c-4e5d-b165-7bd36b481f24
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0132387b86e048c26c0dab61ca174f3e10c55012
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="walkthrough-creating-a-biztalk-application-that-uses-the-mqseries-adapter"></a>Procédure pas à pas : Création d’une Application BizTalk qui utilise l’adaptateur MQSeries
Cette section vous permet de créer une application Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] simple qui utilise l'adaptateur MQSeries.  
  
> [!NOTE]
>  Cette application part du principe que vous avez installé le composant serveur IBM WebSphere MQ pour les plateformes Windows sur le même ordinateur que BizTalk Server. Elle suppose également que vous n'avez encore créé aucun port d'envoi ni emplacement de réception. Si vous avez des ports d'envoi ou emplacements de réception existants, remplacez par les noms appropriés lorsque vous avancez dans la procédure.  
  
 Il s'agit d'une application de routage simple basé sur le contenu utilisant uniquement un emplacement de réception et un port d'envoi. L'emplacement de réception lit à partir d'une file d'attente IBM WebSphere MQ. Le port d'envoi prend le message à l'emplacement de réception et l'envoie à une file d'attente IBM WebSphere MQ différente.  
  
 Pour créer l'application, vous devez créer les files d'attente IBM WebSphere MQ, configurer l'emplacement de réception et le port d'envoi de BizTalk Server, démarrer le port d'envoi et activer l'emplacement de réception, puis placer un message de test dans la file d'attente.  
  
 Si vous disposez des autorisations nécessaires pour installer IBM WebSphere MQ, vous pouvez créer les files d'attente IBM WebSphere MQ à l'aide des boîtes de dialogue de l'adaptateur et ignorer la procédure suivante. Sinon, vous pouvez créer les files d'attente à l'aide des composants client IBM WebSphere MQ Explorer pour les plateformes Windows. Pour créer les files d'attente à l'aide du composant logiciel enfichable IBM WebSphere MQ Explorer, procédez comme suit :  
  
## <a name="to-create-the-ibm-websphere-mq-queues-through-the-ibm-websphere-mq-explorer"></a>Création des files d'attente IBM WebSphere MQ à l'aide d'IBM WebSphere MQ Explorer  
 Procédez comme suit pour créer les files d'attente IBM WebSphere MQ à l'aide d'IBM WebSphere MQ Explorer :  
  
1.  Cliquez sur **Démarrer**, pointez sur **programmes**, pointez sur **IBM WebSphere MQ**, puis cliquez sur **WebSphere MQ Explorer**.  
  
2.  Double-cliquez sur **gestionnaires de file d’attente**, puis double-cliquez sur le Gestionnaire de file d’attente par défaut. Le Gestionnaire de file d’attente par défaut est généralement nommé **QM_***< nom_ordinateur >* où *Nom_Ordinateur* est le nom de votre ordinateur.  
  
3.  Avec le bouton droit **les files d’attente**, pointez sur **nouveau**, puis cliquez sur **file d’attente locale**.  
  
4.  Dans **créer une file d’attente locale** boîte de dialogue **nom de la file d’attente**, type **BTStoMQS**, puis cliquez sur **OK**.  
  
5.  Avec le bouton droit **les files d’attente**, pointez sur **nouveau**, puis cliquez sur **file d’attente locale**.  
  
6.  Dans **créer une file d’attente locale** boîte de dialogue **nom de la file d’attente**, type **MQStoBTS**, puis cliquez sur **OK**.  
  
 Les étapes suivantes permettent de créer l'emplacement de réception et le port d'envoi, de démarrer le port d'envoi et d'activer l'emplacement de réception. Elles permettent également de créer les files d'attente IBM WebSphere MQ.  
  
## <a name="to-create-the-receive-location-and-the-mqseries-queue"></a>Pour créer l’emplacement de réception et de la file d’attente MQSeries  
 Procédez comme suit pour créer l'emplacement de réception et la file d'attente MQSeries :  
  
1.  Dans la console Administration de BizTalk Server, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, puis développez la valeur par défaut application (**BizTalk Application 1** par défaut).  
  
2.  Avec le bouton droit le **Ports de réception** nœud, cliquez sur **nouveau**, puis sélectionnez **Port unidirectionnel**.  
  
3.  Dans le **propriétés du Port de réception** boîte de dialogue le **nom** , tapez **MQStoBTS**.  
  
4.  Dans le volet gauche, cliquez sur **emplacements de réception**, dans le volet droit, cliquez sur **nouveau**.  
  
5.  Dans le **propriétés de l’emplacement de réception** boîte de dialogue le **nom** , tapez **MQStoBTS**.  
  
6.  Sélectionnez **MQSeries** à partir de la liste déroulante liste en regard du **Type** option.  
  
7.  Dans le **Transport** , cliquez sur **configurer**.  
  
8.  Dans le **propriétés du Transport MQSeries** boîte de dialogue le **fréquence d’interrogation** , tapez **1**.  
  
9. Dans le **définition file d’attente** , cliquez sur le bouton de sélection (**...** ) bouton.  
  
10. Dans le **définition file d’attente** boîte de dialogue le **nom du serveur** , tapez le nom de votre ordinateur.  
  
11. Dans le **Gestionnaire de file d’attente** , sélectionnez le Gestionnaire de file d’attente par défaut.  
  
12. Dans le **file d’attente** , tapez **MQStoBTS**, puis cliquez sur **exporter**.  
  
13. Dans le **exporter** boîte de dialogue, cliquez sur **créer une file d’attente**, puis cliquez sur **OK** et **OK** pour revenir à la **réception Propriétés de l’emplacement** boîte de dialogue.  
  
14. Dans le **Gestionnaire de réception** boîte, sélectionnez **BizTalkServerApplication**.  
  
15. Dans le **Pipeline de réception** boîte, sélectionnez **PassThruReceive**.  
  
16. Cliquez sur **OK** pour appliquer les modifications.  
  
## <a name="to-create-the-send-port-and-the-mqseries-queue"></a>Pour créer le port d’envoi et de la file d’attente MQSeries  
 Procédez comme suit pour créer le port d'envoi et la file d'attente MQSeries :  
  
1.  Avec le bouton droit **Ports d’envoi**, cliquez sur **nouveau**, puis sélectionnez **Port d’envoi unidirectionnel statique**.  
  
2.  Dans le **propriétés de Port d’envoi** boîte de dialogue le **nom** , tapez **BTStoMQS.**  
  
3.  Sélectionnez **MQSeries** à partir de la liste déroulante liste en regard du **Type** option.  
  
4.  Dans le **Transport** , cliquez sur **configurer**.  
  
5.  Dans le **propriétés du Transport MQSeries** boîte de dialogue le **définition file d’attente** , cliquez sur le bouton de sélection (**...** ) bouton.  
  
6.  Dans le **définition file d’attente** boîte de dialogue le **nom du serveur** , tapez le nom de votre ordinateur.  
  
7.  Dans le **Gestionnaire de file d’attente** , sélectionnez le Gestionnaire de file d’attente par défaut.  
  
8.  Dans le **file d’attente** , tapez **BTStoMQS**, puis cliquez sur **exporter**.  
  
9. Dans le **exporter** boîte de dialogue, cliquez sur **créer une file d’attente**, puis cliquez sur **OK** et **OK** pour revenir à la **Port d’envoi Propriétés** boîte de dialogue.  
  
10. Dans le **Pipeline d’envoi** boîte, sélectionnez **PassThruTransmit**.  
  
11. Cliquez pour sélectionner **filtres** dans le volet gauche, puis configurez les options de filtre dans le volet droit.  
  
12. Dans le **propriété** la liste déroulante, sélectionnez **BTS. ReceivePortName**.  
  
13. Dans le **valeur** , tapez **MQStoBTS**.  
  
14. Cliquez sur **OK** pour appliquer les modifications.  
  
## <a name="to-enable-the-receive-location-and-start-the-send-port"></a>Activation de l'emplacement de réception et démarrage du port d'envoi  
 Procédez comme suit pour activer l'emplacement de réception et démarrer le port d'envoi :  
  
1.  Cliquez sur le **MQStoBTS** emplacement de réception, puis cliquez sur **activer**.  
  
2.  Cliquez sur le **BTStoMQS** port d’envoi, puis cliquez sur **Démarrer**.  
  
 L'étape suivante permet de tester l'application en envoyant un message de test à la file d'attente de réception.  
  
## <a name="to-test-the-application"></a>Pour tester l'application  
 Procédez comme suit pour tester l'application :  
  
1.  Cliquez sur **Démarrer**, pointez sur **programmes**, pointez sur **IBM WebSphere MQ**, puis cliquez sur **WebSphere MQ Explorer**.  
  
2.  Avec le bouton droit **MQStoBTS**, puis cliquez sur **placer Message de Test**.  
  
3.  Dans le **les données de Message** , tapez un message de test. Cliquez sur **OK**.  
  
 Après avoir entré les données, le **profondeur actuelle** pour le **MQStoBTS** file d’attente est un (1). Lorsque l’application traite le message, le nombre renvoie zéro (0) et le **profondeur actuelle** pour **BTStoMQS** devient un (1). Vous pouvez également afficher le contenu du message.  
  
## <a name="to-view-the-message"></a>Pour afficher le message  
 Procédez comme suit pour afficher le message :  
  
1.  Double-cliquez sur le **BTStoMQS** file d’attente.  
  
2.  Double-cliquez sur le message, puis sélectionnez le **données** feuille. Vous pouvez afficher le texte du message dans le **les données de Message** boîte.  
  
3.  Cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Nouveautés de l’adaptateur MQSeries ?](../core/what-is-the-mqseries-adapter.md)   
 [Architecture de l’adaptateur MQSeries](../core/mqseries-adapter-architecture.md)