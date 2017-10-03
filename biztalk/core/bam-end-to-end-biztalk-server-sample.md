---
title: Exemple de bout en bout BAM dans BizTalk Server | Documents Microsoft
description: "Scénario sur la façon de mettre en corrélation les événements issus de plusieurs composants à l’aide de l’analyse BAM dans BizTalk Server"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 81406038-7f3f-499f-a003-12423d92c44b
caps.latest.revision: "35"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 21cf3bcfae53d3204a1b4de23c1476591be2b453
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="bam-end-to-end-biztalk-server-sample"></a>Analyse BAM de bout en bout (exemple BizTalk Server)
L'exemple de bout en bout décrit la corrélation des événements issus de plusieurs composants (dans ce cas, trois orchestrations et un pipeline) à l'aide de l'analyse BAM.  
  
 L'analyse BAM reconstitue l'activité d'entreprise qui couvre le composant de pipeline et les orchestrations. Niveau le plus bas, cela fonctionne par les appels à **EventStream.EnableContinuation** à partir de chaque composant de l’implémentation qui attend davantage d’événements pour l’activité. L’appel à **EnableContinuation** est explicite, tandis que les appels dans Orchestration1 et Orchestration2 sont effectués par l’ajout d’un dossier de Continuation au modèle de suivi dans une planification et un dossier ContinuationID à la planification suivante Il s’agit.  
  
 Le schéma ci-dessous illustre le flux de travail utilisé dans l'exemple.  
  
 ![](../core/media/ebiz-sdk-samples-bam-endtoendwkflw.gif "ebiz_sdk_samples_bam_endtoendwkflw")  

  
## <a name="what-this-sample-does"></a>Fonctions de l'exemple  
 L'exemple de bout en bout présente l'utilisation de l'analyse BAM pour rassembler des informations à partir d'un pipeline et de plusieurs orchestrations, et mettre à jour une activité spécifique.  
  
## <a name="how-this-sample-was-designed-and-why"></a>Conception et finalité de cet exemple  
 L'exemple d'analyse BAM de bout en bout a été conçu pour illustrer les activités suivantes :  
  
-   utilisation de l'analyse BAM au sein d'un pipeline ;  
  
-   utilisation de l'Éditeur de modèle de suivi pour mapper les éléments d'activité vers des formes dans une orchestration et les éléments d'un message ;  
  
-   utilisation des continuations pour conserver une activité active lorsque plusieurs éléments d'une solution contribuent à l'activité.  
  

L'exemple fonctionne comme suit :  
  
1.  Un message d’entrée est récupéré à partir de la  *\<exemples de chemin >*dossier \BamEndToEnd\Input.  
  
2.  Le composant de pipeline affecte un DocumentID unique au message, et utilise l'API BAM pour commencer une nouvelle activité BAM. Le DocumentID est joint en tant qu'élément distinct du message d'entrée afin qu'il devienne accessible aux orchestrations.  
  
3.  Le service Orchestration1 est activé à la réception du message d'entrée.  
  
4.  Orchestration1 modifie le message d'entrée et le transfère en tant que paramètre à Orchestration2.  
  
5.  Orchestration2 modifie le message d'entrée et l'envoie vers la base de données MessageBox, qui active Orchestration3.  
  
6.  Orchestration3 modifie le message et l’écrit dans le dossier  *\<exemples de chemin >*\BamEndToEnd\Output.  
  
7.  Chaque orchestration met à jour les éléments d'activité dans l'activité BAM.  
  
## <a name="where-to-find-this-sample"></a>Accès à l'exemple  
 Vous pouvez trouver cet exemple à  *\<exemples de chemin >*\BAM\BamEndToEnd.  
  
 Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.  
  
|Fichier(s)| Description|  
|----|---|  
|BamEndToEnd.sln|Exemple de solution d'analyse BAM de bout en bout|  
|BamEndToEnd.xls|Feuille de style de définition BAM.|  
|BamEndToEnd.xml|XML de définition BAM.|  
|BAMEndToEndBinding.xml|Liaison BAM.|  
|Cleanup.bat|Fichiers de commandes pour annuler le déploiement de l'exemple.|  
|InputMessage.xml|Message d'entrée.|  
|Setup.bat|Fichier de commandes pour compiler et déployer l'exemple.|  
|\Components\AssemblyInfo.cs|Code du composant du pipeline.|  
|\Components\BAMMessagePartPLComponent.cs|Code du composant du pipeline.|  
|\Components\Components.csproj|Projet du composant du pipeline.|  
|\Messages\InputMessage01.xml<br /><br /> ...<br /><br /> \Messages\InputMessage10.xml|Messages d'entrée de l'exemple.|  
|\Services\BAMInbound.btp|Fichier de pipeline entrant.|  
|\Services\BAMPartSchema.xsd|Schéma de la partie du message BAM.|  
|\Services\Orchestration1.odx|Orchestration :|  
|\Services\Orchestration2.odx|Orchestration :|  
|\Services\Orchestration3.odx|Orchestration :|  
|\Services\PropertySchema.xsd|Schéma de propriété.|  
|\Services\Schema1.xsd|Schéma du message.|  
|\Services\Schema2.xsd|Schéma du message.|  
Services\Schema3.xsd|Schéma du message.|  
|\Services\Services.btproj|Fichier de projet BizTalk [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].|  
|\Services\Transform_1.btm|Fichier de mappage.|  
|\Services\Transform_2.btm|Fichier de mappage.|  
|\Services\Transform_3.btm|Fichier de mappage.|  
  
## <a name="how-to-use-this-sample"></a>L’utilisation de cet exemple  
 Les procédures suivantes permettent de créer et d'exécuter l'exemple d'analyse BAM de bout en bout :  
  
-   [Pour créer et initialiser l’exemple](#To_Build_Sample)  
  
-   [Pour exécuter cet exemple](#To_Run_Sample)  
  
-   [Pour afficher les données BAM](#To_View_Data)  
  
##  <a name="To_Build_Sample"></a>Créer et initialiser l’exemple  
  
1.  Ouvrez une invite de commandes en tant qu’administrateur et exécutez  *\<exemples de chemin >*\BAM\BAMEndToEnd\Setup.bat. Setup.bat crée et initialise l'infrastructure BAM pour cet exemple. Maintenez l'invite de commandes ouverte.  
  
2.  Créez un modèle de suivi pour mapper Orchestration1, Orchestration2 et Orchestration3 vers l'activité BAM. (Étant donné que la création du profil de suivi est un processus complexe, les instructions détaillées sont dans une procédure séparée appelée **pour créer un modèle de suivi**. Cette procédure est traitée ultérieurement dans ce document.)  
  
3.  Déployez le modèle de suivi BamEndToEnd.btt que vous venez de créer au cours de l'étape précédente.  Dans l’invite de commandes, remplacez par le  *\<exemples de chemin >*répertoire \BAM\BamEndToEnd. Pour déployer le modèle de suivi, tapez la ligne suivante, puis appuyez sur **entrée**:  
  
    `“<BizTalkInstallationPath>\Tracking\bttdeploy” BamEndToEnd.btt`
  
     [Comment déployer des profils de suivi avec le suivi des profils de l’utilitaire de gestion](../core/how-to-deploy-tracking-profiles-with-the-tracking-profiles-management-utility.md) fournit plus d’informations.
  
    > [!IMPORTANT]
    >  Vous pouvez ignorer le message indiquant que ContinuationID Orch1_ ne possède pas de continuation correspondante. Ce message est attendu, car la continuation nommée Orch1_ est définie dans le composant de pipeline, mais pas dans le modèle de suivi.  
  
##  <a name="To_Run_Sample"></a>Exécuter cet exemple  
  
Copiez le fichier  *\<exemples de chemin >*\BamEndToEnd\InputMessage.xml dans le dossier  *\<exemples de chemin >*\BamEndToEnd\Input. Après quelques secondes, le message disparaît du dossier d’entrée et un message de sortie s’affiche dans le  *\<exemples de chemin >*dossier \BamEndToEnd\Output.  
  
##  <a name="To_View_Data"></a>Afficher les données BAM  
  
1.  Ouvrez SQL Server Management Studio.  
  
2.  Dans SQL Server Management Studio, développez le serveur, **bases de données**, développez **BAMPrimaryImport**, puis développez **Tables**.  
  
3.  Avec le bouton droit **dbo.bam_EndToEndActivity_Completed**, puis cliquez sur **ouvrir la Table**. Si vous utilisez [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)], cliquez sur **sélectionner les 1000 lignes**.  
  
     Le contenu de la table bam_EndToEndActivity_Completed s'affiche dans le volet droit. Chaque ligne de la table représente une activité EndToEndActivity terminée.  
  
#### <a name="rerun-this-sample"></a>Exécutez à nouveau cet exemple  
  
1.  Ouvrez une invite de commandes en tant qu’administrateur et remplacez le  *\<exemples de chemin >*répertoire \BAM\BamEndToEnd. Tapez la ligne suivante :  
  
    `“C:\Program Files\Microsoft BizTalk Server <version>\Tracking\bttdeploy” BamEndToEnd.btt /remove`  
  
    > [!NOTE]
    >  Si vous n’avez pas installé [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sur le lecteur C, remplacez « C » par la lettre de lecteur où vous avez installé [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
2.  Exécutez  *\<exemples de chemin d’accès >*\BAM\BAMEndToEnd\Cleanup.bat. Cleanup.bat supprime l'infrastructure BAM pour cet exemple.  
  
3.  Effectuez les étapes dans **pour créer et initialiser l’exemple** dans cette rubrique.  
  
##  <a name="TPE_procedure"></a>Créer un modèle de suivi  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]. Avec le bouton droit **éditeur**, et **exécuter en tant qu’administrateur**.  
  
2.  Dans le volet gauche de la **éditeur** fenêtre, cliquez sur **cliquez ici pour importer une définition d’activité BAM**.  
  
3.  Dans le **le nom de définition d’activité BAM** section de la **importer une définition d’activité BAM** boîte de dialogue, sélectionnez **EndToEndActivity**, puis cliquez sur **OK**.  
  
4.  Dans le volet droit de la **éditeur** fenêtre, cliquez sur **cliquez ici pour sélectionner une source d’événement**.  
  
5.  Dans le **nom de l’Assembly** section de la **sélectionner l’Assembly Parent Source événement** boîte de dialogue, sélectionnez **Microsoft.Samples.BizTalk.BamEndToEnd.Services**, puis cliquez sur **Suivant**.  
  
6.  Dans le **nom de l’Orchestration** section de la **sélectionner une Orchestration** boîte de dialogue, sélectionnez **BamEndToEnd.Services.Orchestration1**, puis cliquez sur **OK** .  
  
7.  Dans le volet gauche de la **éditeur** fenêtre, avec le bouton droit **EndToEndActivity**, puis cliquez sur **nouveau ContinuationID**. Nommez le nouveau Continuationid **Orch1_**. Répétez cette étape pour créer les deux autres ContinuationID nommés **Orch2_** et **Orch3_**.  
  
8.  Avec le bouton droit **EndToEndActivity**, puis cliquez sur **Nouvelle Continuation**. Nommez la nouvelle continuation **Orch2_**. Répétez cette étape pour créer une autre continuation nommée **Orch3_**.  
  
9. Avec le bouton droit le **Receive1** mettre en forme, puis cliquez sur **les schémas de propriété de contexte**.  
  
10. Faites défiler jusqu'à la fin de la **nom de propriété de contexte** liste, puis double-cliquez sur **BAMEndToEnd.Services.PropertySchema.DocumentID**.  
  
11. Développez  **\<schéma >**, puis faites glisser **DocumentID** dans le volet droit pour **Orch1_** dans le volet gauche.  
  
12. Cliquez sur l’icône de dossier avec la flèche (![bouton avec dossier et flèche haut](../core/media/abccd08b-2b01-49c6-80ed-a032bbbd10d4.gif "abccd08b-2b01-49c6-80ed-a032bbbd10d4")) à deux reprises pour afficher l’orchestration.  
  
13. Faites glisser le **Receive1** forme dans le volet droit pour **SBegin1** dans le volet gauche.  
  
14. Faites glisser le **StartOrchestration_1** forme dans le volet droit pour **SEnd1** dans le volet gauche.  
  
15. Avec le bouton droit le **StartOrchestration_1** mettre en forme, puis cliquez sur **schémas de charges de Message**.  
  
16. Double-cliquez sur la ligne qui contient la valeur « Message_2 » dans le **Message** colonne et la valeur « MessageBody » dans le **partie** colonne.  
  
     ![Schéma de charge utile du Message TPE montrant les message &#95; 2](../core/media/77fbc444-46cf-4d45-8e9c-c330da7ba7d1.gif "77fbc444-46cf-4d45-8e9c-c330da7ba7d1")  
  
17. Développez **Schema2**, puis faites glisser **Data2** dans le volet droit pour **Data1** dans le volet gauche.  
  
18. Cliquez sur **Source d’événement sélectionnez**, puis cliquez sur **sélectionner la propriété de contexte**.  
  
19. Faites défiler jusqu'à la fin de la **nom de propriété de contexte** liste, puis double-cliquez sur **BAMEndToEnd.Services.PropertySchema.DocumentID**.  
  
20. Développez  **\<schéma >**, puis faites glisser **DocumentID** à la **Orch2_** continuation dans le volet gauche.  
  
    > [!NOTE]
    >  Ne confondez pas la continuation Orch2_ et le continuationID Orch2_. L’icône représentant un Continuationid contient une clé (![icône d’un Continuationid](../core/media/2d04a714-ade9-4e96-b89e-00002da75bea.gif "2d04a714-ade9-4e96-b89e-00002da75bea")), alors que l’icône représentant une continuation ne contient-elle pas de clé () ![icône pour une continuation](../core/media/test.gif "test")).  
  
21. Cliquez sur **Source d’événement sélectionnez**, puis cliquez sur **sélectionner une planification d’Orchestration**.  
  
22. Dans le **nom de l’Assembly** section de la **sélectionner l’Assembly Parent Source événement** boîte de dialogue, sélectionnez **Microsoft.Samples.BizTalk.BamEndToEnd.Services**, puis cliquez sur **Suivant**.  
  
23. Dans le **nom de l’Orchestration** section de la **sélectionner une Orchestration** boîte de dialogue, sélectionnez **BamEndToEnd.Services.Orchestration2**, puis cliquez sur **OK** .  
  
24. Avec le bouton droit le **ConstructMessage_1** mettre en forme, puis cliquez sur **schémas de charges de Message**.  
  
25. Double-cliquez sur la ligne qui contient la valeur « Message_3 » dans le **Message** colonne et la valeur « BAMPart » dans le **partie** colonne.  
  
26. Développez **BAMPart**, puis faites glisser **DocumentID** dans le volet droit vers le **Orch2_** Continuationid dans le volet gauche.  
  
    > [!NOTE]
    >  Ne confondez pas la continuation Orch2_ et le continuationID Orch2_. L’icône représentant un Continuationid contient une clé (![icône d’un Continuationid](../core/media/2d04a714-ade9-4e96-b89e-00002da75bea.gif "2d04a714-ade9-4e96-b89e-00002da75bea")), alors que l’icône représentant une continuation ne contient-elle pas de clé () ![icône pour une continuation](../core/media/test.gif "test")).  
  
27. Cliquez sur l’icône de dossier avec la flèche (![bouton avec dossier et des &#45; flèche](../core/media/abccd08b-2b01-49c6-80ed-a032bbbd10d4.gif "abccd08b-2b01-49c6-80ed-a032bbbd10d4")) à deux reprises pour afficher l’orchestration.  
  
28. Faites glisser le **ConstructMessage_1** forme dans le volet droit pour **SBegin2** dans le volet gauche.  
  
29. Faites glisser le **Send_1** forme dans le volet droit pour **SEnd2** dans le volet gauche.  
  
30. Avec le bouton droit le **Send_1** mettre en forme, puis cliquez sur **schémas de charges de Message**.  
  
31. Double-cliquez sur la ligne qui contient la valeur « Message_3 » dans le **Message** colonne et la valeur « MessageBody » dans le **partie** colonne.  
  
32. Développez **Schema3**, puis faites glisser **Data3** dans le volet droit pour **Data2** dans le volet gauche.  
  
33. Dans la liste déroulante au-dessus du volet droit, sélectionnez **schémas de charges de Message**.  
  
34. Double-cliquez sur la ligne qui contient la valeur « Message_3 » dans le **Message** colonne et la valeur « BAMPart » dans le **partie** colonne.  
  
35. Développez **BAMPart**, puis faites glisser **DocumentID** dans le volet droit vers le **Orch3_** continuation dans le volet gauche.  
  
    > [!NOTE]
    >  Ne confondez pas la continuation Orch3_ et le continuationID Orch3_. L’icône représentant un Continuationid contient une clé (![icône d’un Continuationid](../core/media/2d04a714-ade9-4e96-b89e-00002da75bea.gif "2d04a714-ade9-4e96-b89e-00002da75bea")), alors que l’icône représentant une continuation ne contient-elle pas de clé () ![icône pour une continuation](../core/media/test.gif "test")).  
  
36. Cliquez sur **Source d’événement sélectionnez**, puis cliquez sur **sélectionner une planification d’Orchestration**.  
  
37. Dans le **nom de l’Assembly** section de la **sélectionner l’Assembly Parent Source événement** boîte de dialogue, sélectionnez **Microsoft.Samples.BizTalk.BamEndToEnd.Services**, puis cliquez sur **Suivant**.  
  
38. Dans le **nom de l’Orchestration** section de la **sélectionner une Orchestration** boîte de dialogue, sélectionnez **BamEndToEnd.Services.Orchestration3**, puis cliquez sur **OK** .  
  
39. Avec le bouton droit le **Receive1** mettre en forme, puis cliquez sur **schémas de charges de Message**.  
  
40. Double-cliquez sur la ligne qui contient la valeur « Message_3 » dans le **Message** colonne et la valeur « BAMPart » dans le **partie** colonne.  
  
41. Développez **BAMPart**, puis faites glisser **DocumentID** dans le volet droit vers le **Orch3_** Continuationid dans le volet gauche.  
  
    > [!NOTE]
    >  Ne confondez pas la continuation Orch3_ et le continuationID Orch3_. L’icône représentant un Continuationid contient une clé (![icône d’un Continuationid](../core/media/2d04a714-ade9-4e96-b89e-00002da75bea.gif "2d04a714-ade9-4e96-b89e-00002da75bea")), alors que l’icône représentant une continuation ne contient-elle pas de clé () ![icône pour une continuation](../core/media/test.gif "test")).  
  
42. Cliquez sur l’icône de dossier avec la flèche (![bouton avec dossier et flèche haut](../core/media/abccd08b-2b01-49c6-80ed-a032bbbd10d4.gif "abccd08b-2b01-49c6-80ed-a032bbbd10d4")) à deux reprises pour afficher l’orchestration.  
  
43. Faites glisser le **Receive1** forme dans le volet droit pour **SBegin3** dans le volet gauche.  
  
44. Faites glisser le **Send_1** forme dans le volet droit pour **SEnd3** dans le volet gauche.  
  
45. Cliquez sur le **Send_1** mettre en forme, puis cliquez sur **schéma de charge utile de Message**.  
  
46. Développez **Schema3**, puis faites glisser **Data3** dans le volet droit pour **Data3** dans le volet gauche.  
  
47. Avec le bouton droit **DocumentID** sous le **Orch2_** continuation, puis cliquez sur **définir les mappages de Port**.  
  
    > [!NOTE]
    >  Ne confondez pas la continuation Orch2_ et le continuationID Orch2_. L’icône représentant un Continuationid contient une clé (![icône d’un Continuationid](../core/media/2d04a714-ade9-4e96-b89e-00002da75bea.gif "2d04a714-ade9-4e96-b89e-00002da75bea")), alors que l’icône représentant une continuation ne contient-elle pas de clé () ![icône pour une continuation](../core/media/test.gif "test")).  
  
48. Dans le **sélectionner des Ports** section de la **sélectionner des Ports** boîte de dialogue, cliquez sur **BamEndToEnd_ReceivePort**, cliquez sur la plus grande-signe ( **>** ), puis cliquez sur **OK**.  
  
49. Enregistrer le modèle de suivi à  *\<exemples de chemin >*\BAM\BamEndToEnd\BamEndToEnd.btt.  
  
## <a name="important-details"></a>Obtenir des informations importantes  
 Les modèles de suivi ne sont pas pris en charge pour les pipelines. Toutefois, l’appel à **BeginActivity** dans le pipeline de composant est identique à l’aide d’ActivityID dans une orchestration. L’appel à **EnableContinuation** est identique à l’aide d’une continuation dans une orchestration.  
  
## <a name="see-also"></a>Voir aussi  
 [Business Activity Monitoring (dossier d’exemples BizTalk Server)](../core/business-activity-monitoring-biztalk-server-samples-folder.md)