---
title: MQSSendPipelineComponent (exemple BizTalk Server) | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- examples, MQSeries adapters
- pipelines, examples
- MQSeries adapters, examples
- examples, pipelines
ms.assetid: ac709e45-524b-45ab-9673-060790ecbed2
caps.latest.revision: "27"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 256731dbb6194aa1962d62ec9fdbe58a0fd60e03
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="mqssendpipelinecomponent-biztalk-server-sample"></a>MQSSendPipelineComponent (exemple BizTalk Server)
Cet exemple montre comment écrire un composant de pipeline capable de lire un ensemble de valeurs de propriétés MQSeries à partir d'un fichier XML et de les appliquer à un message.  
  
## <a name="what-this-sample-does"></a>Fonctions de l'exemple  
 Cet exemple est constitué de deux projets [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] : un projet de composant de pipeline et un projet de pipeline utilisant le composant de pipeline.  
  
## <a name="where-to-find-this-sample"></a>Accès à l'exemple  
  
-   *\<Cheminaccèsexemples >*\AdaptersUsage\MQSeriesAdapter\MQSSendPipelineComponent\SetMQSeriesHeaderPropertyComponent  
  
-   *\<Cheminaccèsexemples >*\AdaptersUsage\MQSeriesAdapter\MQSSendPipelineComponent\SetMQSeriesHeaderPropertyPipeline  
  
 Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.  
  
|**Fichier**|**Description**|  
|--------------|---------------------|  
|SetMQSeriesHeaderPropertyComponent\SetMQSeriesHeaderPropertyComponent.sln,<br /><br /> SetMQSeriesHeaderPropertyComponent\SetMQSeriesHeaderPropertyComponent.csproj|Fichiers projet et solution du composant de pipeline.|  
|SetMQSeriesHeaderPropertyComponent\CSetMQSeriesHeaderPropertyComponent.cs|Fichier source Visual C#® du composant de pipeline.|  
|SetMQSeriesHeaderPropertyComponent\SetMQSMQMDHdrProps.xml|Propriétés MQSeries lues et utilisées par le composant de pipeline.|  
|SetMQSeriesHeaderPropertyPipeline\SetMQSeriesHeaderPropertyPipeline.btproj,<br /><br /> SetMQSeriesHeaderPropertyPipeline\SetMQSeriesHeaderPropertyPipeline.sln|Fichiers projet et solution du pipeline BizTalk.|  
|SetMQSeriesHeaderPropertyPipeline\SetMQSeriesHeaderPropertyPipeline.snk|Fichier de clé de nom fort du projet de pipeline BizTalk.|  
|SetMQSeriesHeaderPropertyPipeline\SetMQSeriesHeaderPropertyPipeline.btp|Pipeline [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].|  
  
## <a name="how-to-use-this-sample"></a>L’utilisation de cet exemple  
 Pour créer l'application, procédez comme suit :  
  
1.  Créez les dossiers pour l'application.  
  
2.  Modifiez et compilez le projet [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] pour le composant de pipeline.  
  
3.  Copiez l'assembly compilé et le fichier d'en-tête dans les dossiers appropriés.  
  
4.  Modifiez le projet [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] pour le pipeline [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
5.  Compilez et déployez le projet de pipeline [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
6.  Configurez un emplacement de réception [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
7.  Créez une file d'attente MQSeries.  
  
8.  Configurez un port d'envoi.  
  
9. Activez l'emplacement de réception et démarrez le port d'envoi.  
  
## <a name="creating-the-folders-for-the-application"></a>Création des dossiers pour l'application  
 Cette procédure permet de créer les dossiers appropriés pour l'application.  
  
#### <a name="to-create-the-folders-for-the-application"></a>Pour créer les dossiers pour l'application  
  
1.  Créez un dossier nommé **temp** sur votre lecteur C:\ si elle n’existe pas déjà.  
  
2.  Créez un dossier sous le **C:\temp** répertoire nommé **Pickup3**.  
  
## <a name="modifying-and-compiling-the-project-for-the-pipeline-component"></a>Modification et compilation du projet pour le composant de pipeline  
 Cette procédure permet de modifier et de compiler le projet [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] pour le composant de pipeline.  
  
#### <a name="to-modify-and-compile-the-project-for-the-pipeline-component"></a>Pour modifier et compiler le projet pour le composant de pipeline  
  
1.  Double-cliquez sur le fichier solution **setmqseriesheaderpropertycomponent\setmqseriesheaderpropertycomponent.sln** pour ouvrir la solution dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].  
  
2.  Double-cliquez sur le fichier de classe **CSetMQSeriesHeaderPropertyComponent.cs** pour ouvrir le fichier de classe dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].  
  
3.  Recherchez la variable **samplesDir**, vérifiez que cette variable est définie à l’emplacement **C:\temp**.  
  
4.  Avec le bouton droit de la solution dans l’Explorateur de solutions, puis cliquez sur **Build**. Cela sera compilé le projet dans une dll située dans le **SetMQSeriesHeaderPropertyComponent\SetMQSeriesHeaderPropertyComponent\bin\Debug\\**  active.  
  
## <a name="copying-the-assembly-and-header-file-to-appropriate-folders"></a>Copie de l'assembly et du fichier d'en-tête dans les dossiers appropriés  
 Cette procédure permet de copier l'assembly compilé et le fichier d'en-tête dans les dossiers appropriés.  
  
#### <a name="to-copy-the-compiled-assembly-and-header-file-to-the-appropriate-folders"></a>Pour copier l'assembly compilé et le fichier d'en-tête dans les dossiers appropriés  
  
1.  Copiez l’assembly compilé **SetMQSeriesHeaderPropertyComponent.dll** dans le dossier composants de pipeline BizTalk. Par défaut, le dossier des composants de pipeline BizTalk se trouve à l'emplacement suivant : [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Composants de pipeline.  
  
2.  Copiez le fichier de propriétés MQHeader **SetMQSMQMDHdrProps.xml** à la **C:\temp** active.  
  
## <a name="modifying-the-project-for-the-biztalk-server-pipeline"></a>Modification du projet pour le pipeline BizTalk Server  
 Cette procédure permet de modifier le projet [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] pour le pipeline [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
#### <a name="to-modify-the-project-for-the-biztalk-server-pipeline"></a>Pour modifier le projet pour le pipeline BizTalk Server  
  
1.  Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], ouvrez la solution en double-cliquant sur le fichier solution **setmqseriesheaderpropertypipeline\setmqseriesheaderpropertypipeline.sln**.  
  
2.  Créez un fichier de clé de nom fort pour le projet. Pour ce faire, procédez comme suit :  
  
    1.  Ouvrez une invite de commandes [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].  
  
    2.  Remplacez les répertoires par \<Cheminaccèsexemples > \AdaptersUsage\MQSeriesAdapter\MQSSendPipelineComponent.  
  
    3.  Tapez la commande suivante :  
  
         `sn -k MQSSendPipelineComponent.snk`  
  
    4.  Appuyez sur Entrée. Le fichier de clé sera ainsi créé.  
  
3.  Dans **l’Explorateur de solutions**, cliquez sur le projet, cliquez sur **propriétés** pour lancer le Concepteur de projet pour le projet (dans le centre de la fenêtre).  
  
    1.  Dans le Concepteur de projets, cliquez sur **signature** onglet.  
  
    2.  Dans le volet droit, sélectionnez le **signer l’assembly** option...  
  
    3.  Cliquez sur la liste déroulante pour le **choisir un fichier de clé de nom fort** option, puis cliquez sur **Parcourir**.  
  
    4.  Accédez à \<Cheminaccèsexemples > \AdaptersUsage\MQSeriesAdapter\MQSSendPipelineComponent\MQSSendPipelineComponent.snk, cliquez sur **ouvrir**.  
  
4.  Le composant de pipeline que vous avez créé précédemment est déjà ajouté à la **préassembler** stade de ce projet de pipeline. Si ce composant n'était pas déjà ajouté, vous devriez procéder comme suit :  
  
    1.  Dans le [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] IDE, cliquez sur le **boîte à outils** onglet sur le côté gauche.  
  
    2.  Cliquez sur le **boîte à outils**, puis cliquez sur **choisir des éléments de**.  
  
    3.  Dans le **choisir des éléments de boîte à outils** boîte de dialogue, cliquez sur le **composants de Pipeline BizTalk** onglet, sélectionnez le **Custom Component to Set MQseries propriétés d’en-tête**composant, et puis cliquez sur **OK**.  
  
    4.  Faites glisser le **Custom Component to Set MQseries propriétés d’en-tête**composant le **préassembler** stade de ce pipeline.  
  
## <a name="compiling-and-deploying-the-pipeline-project"></a>Compilation et déploiement du projet de pipeline  
 Cette procédure permet de compiler et de déployer le projet de pipeline [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
#### <a name="to-compile-and-deploy-the-pipeline-project"></a>Pour compiler et déployer le projet de pipeline  
  
1.  Dans la fenêtre Explorateur de solutions, cliquez sur la solution, puis cliquez sur **déployer la Solution**. La solution est alors générée et l'assembly est déployé dans la base de données de gestion BizTalk.  
  
2.  Vérifiez que l'assembly a été déployé dans la base de données de gestion BizTalk :  
  
    1.  Ouvrez la console Administration de BizTalk.  
  
    2.  Cliquez pour développer **groupe BizTalk [\<nom_serveur > :\<base de données de gestion >]**, puis cliquez pour développer le **assemblys** dossier.  
  
         L’assembly de pipeline déployé doit être visible sous le **assemblys** dossier.  
  
## <a name="creating-the-receive-location"></a>Création de l'emplacement de réception  
 Cette procédure permet de créer un emplacement de réception [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
#### <a name="to-create-the-receive-location"></a>Pour créer l'emplacement de réception  
  
1.  Dans la Console Administration de BizTalk Server, cliquez sur **Ports de réception**, pointez sur **nouveau**, puis cliquez sur **Port de réception unidirectionnel**.  
  
2.  Dans le **propriétés du Port de réception unidirectionnel** boîte de dialogue le **nom** tapez « MQReply », puis cliquez sur **OK**.  
  
3.  Dans le volet gauche, cliquez sur **emplacements de réception** onglet, puis cliquez sur **nouveau**.  
  
4.  Dans le **propriétés de l’emplacement de réception** boîte de dialogue le **nom** , tapez « ReceiveFile ».  
  
5.  Dans le **Type de Transport** boîte, sélectionnez **fichier**.  
  
6.  Dans le **Gestionnaire de réception** champ, sélectionnez **BizTalkServerApplication**.  
  
7.  Dans le **pipeline de réception** champ, sélectionnez **Microsoft.BizTalk.DefaultPipelines.PassThruReceive**.  
  
8.  Dans le **dossier de réception** , tapez « C:\temp\Pickup3 ».  
  
9. Dans le **masque de fichier** , tapez « *.\*».  
  
10. Cliquez sur **OK**, puis cliquez sur **OK** pour quitter le **propriétés de l’emplacement de réception** boîte de dialogue.  
  
## <a name="creating-a-mqseries-queue-through-the-mqseries-explorer"></a>Création d'une file d'attente MQSeries à l'aide de MQSeries Explorer  
 Si vous avez les autorisations requises pour le serveur MQSeries pour l’installation de Windows, vous pouvez créer la file d’attente MQSeries via les boîtes de dialogue de l’adaptateur et ignorez cette procédure suivante.  
  
 Sinon, vous pouvez utiliser la procédure suivante pour créer les files d'attente à l'aide d'IBM WebSphere MQ Explorer.  
  
#### <a name="to-create-a-mqseries-queue-through-the-mqseries-explorer"></a>Pour créer une file d'attente MQSeries à l'aide de MQSeries Explorer  
  
1.  Cliquez sur **Démarrer**, pointez sur **programmes**, pointez sur **IBM WebSphere MQ**, puis cliquez sur **WebSphere MQ Explorer**.  
  
2.  Double-cliquez sur **gestionnaires de file d’attente**, puis double-cliquez sur le Gestionnaire de file d’attente par défaut. Le Gestionnaire de file d’attente par défaut est généralement nommé **QM_**\<*Nom_Ordinateur*> où *Nom_Ordinateur* est le nom de votre ordinateur.  
  
3.  Avec le bouton droit **les files d’attente**, pointez sur **nouveau**, puis cliquez sur **file d’attente locale**.  
  
4.  Dans **créer une file d’attente locale** boîte de dialogue **nom de la file d’attente**, type **SETHEADER**, puis cliquez sur **OK**.  
  
## <a name="creating-the-send-port-and-mqseries-queue"></a>Création du port d'envoi et de la file d'attente MQSeries  
 Cette procédure permet de créer le port d'envoi pour le message sortant. Le cas échéant, la file d'attente MQSeries est également créée lorsque vous créez le port d'envoi.  
  
#### <a name="to-create-the-send-port-and-mqseries-queue"></a>Pour créer le port d'envoi et la file d'attente MQSeries  
  
1.  Avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi unidirectionnel statique**.  
  
2.  Dans le **propriétés de Port d’envoi** boîte de dialogue le **nom** , tapez « MQSolicitResponse ».  
  
3.  Dans le **Type de Transport** boîte, sélectionnez **MQSeries**.  
  
4.  Dans le **pipeline d’envoi** boîte, sélectionnez **SetMQSeriesHeaderPropertyPipeline.SetMQSeriesHeadersSendPipeline**.  
  
5.  Dans **filtres**, ajouter une nouvelle entrée avec les paires nom/valeur suivantes :  
  
    -   Définissez **propriété** à « BizTalk Server. ReceivePortName ».  
  
    -   Définissez **opérateur** à « == ».  
  
    -   Définissez **valeur** sur « ReceiveFile ».  
  
        > [!NOTE]
        >  Le port d'envoi sera ainsi configuré pour s'abonner aux messages qui arrivent sur le port de réception ReceiveFile.  
  
6.  Cliquez sur **Transport**.  
  
7.  Dans le **adresse (URI)** , cliquez sur le bouton de sélection (...).  
  
8.  Dans le **propriétés du Transport MQSeries** boîte de dialogue le **définition file d’attente** , cliquez sur le bouton de sélection (...).  
  
9. Dans le **définition file d’attente** boîte de dialogue le **nom du serveur** , tapez le nom de votre ordinateur.  
  
10. Dans le **Gestionnaire de file d’attente** , sélectionnez le Gestionnaire de file d’attente par défaut.  
  
11. Dans le champ de la file d’attente, tapez « SETHEADER », puis cliquez sur **exporter**.  
  
12. Dans le **exporter** boîte de dialogue, cliquez sur **créer une file d’attente**, puis cliquez sur **OK** ou **fait** jusqu'à ce que vous avez quitté la boîte de dialogue tous les.  
  
## <a name="enabling-the-receive-location-and-starting-the-send-port"></a>L’activation de l’emplacement de réception et démarrer le Port d’envoi  
 Cette procédure permet d'activer l'emplacement de réception et de démarrer le port d'envoi.  
  
#### <a name="to-enable-the-receive-location-and-start-the-send-port"></a>Activation de l'emplacement de réception et démarrage du port d'envoi  
  
1.  Dans la console Administration de BizTalk Server, cliquez sur **Ports de réception**.  
  
2.  Dans le volet détails, cliquez sur le **MQIn** emplacement de réception et cliquez sur **activer**.  
  
3.  Dans le volet détails, cliquez sur le **SetMQHeader** port d’envoi, puis cliquez sur **Démarrer**.  
  
## <a name="testing-the-application"></a>Test de l'application  
 Cette procédure permet de tester l'application.  
  
#### <a name="to-test-the-application"></a>Pour tester l'application  
  
1.  Placez un fichier dans le **C:\Temp\Pickup3** dossier.  
  
2.  Lancez WebSphere MQ Explorer et double-cliquez sur la file d'attente SETHEADER pour examiner le ou les messages dans la file d'attente SETHEADER.  
  
     Pour afficher toutes les propriétés de contexte des messages dans la file d'attente SETHEADER, procédez comme suit :  
  
    1.  Double-cliquez sur le **SETHEADER** file d’attente pour afficher les **Message Browser** boîte de dialogue.  
  
    2.  Dans le **Message Browser** boîte de dialogue, cliquez sur **colonnes** pour afficher les **afficher/masquer les colonnes de Messages** boîte de dialogue.  
  
    3.  Sous **colonnes disponibles**, double-cliquez sur chaque entrée pour le rendre visible dans le **Message Browser** boîte de dialogue, puis cliquez sur **OK**.  
  
3.  Les propriétés de contexte de message pour chaque message doivent être visibles dans le **Message Browser** boîte de dialogue.  
  
## <a name="see-also"></a>Voir aussi  
 [Exemples d’adaptateur MQSeries](../core/mqseries-adapter-samples.md)