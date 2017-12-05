---
title: "API BAM à partir d’une Expression d’Orchestration (exemple BizTalk Server) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestrations, examples
- examples, BAM
- examples, orchestrations
- BAM, examples
ms.assetid: 341bc333-9bfc-484c-b431-9a71f9188792
caps.latest.revision: "23"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e3f78297b57dc2c9bc61d5996c49f7543ac64163
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="bam-api-from-an-orchestration-expression-biztalk-server-sample"></a>API BAM à partir d'une expression d'orchestration (exemple BizTalk Server)
Cet exemple montre comment :  
  
-   utiliser l'API BAM à partir d'une expression d'orchestration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ;  
  
-   suivre des éléments répétés à l'intérieur d'un message comme des instances d'activité distinctes ;  
  
-   créer une relation entre les données BAM suivies à l'aide d'un modèle de suivi et les données BAM suivies à l'aide de l'API BAM.  
  
## <a name="where-to-find-this-sample"></a>Accès à l'exemple  
 Vous pouvez trouver cet exemple à  *\<exemples de chemin\>*\BAM\BamFromExpression.  
  
 Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.  
  
|Fichier| Description|  
|----------|-----------------|  
|BamDefinition.xls|Feuille de style définition BAM.|  
|BamDefinition.xml|Définition BAM.|  
|BamFromExpression.btproj|Projet de fichier de suivi [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].|  
|BamFromExpression.sln|Solution [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].|  
|Cleanup.bat|Fichiers de commandes pour annuler le déploiement de l'exemple.|  
|InputMessage.xml|Message d'entrée.|  
|Orchestration1.odx|Orchestration :|  
|PoSchema.xsd|Schéma de bon de commande.|  
|PropertySchema.xsd|Schéma de propriété.|  
|Setup.bat|Fichier de commandes pour compiler et déployer l'exemple.|  
|QueryBam.sql|Script SQL.|  
  
## <a name="how-to-use-this-sample"></a>L’utilisation de cet exemple  
 Les procédures suivantes permettent de créer le modèle de suivi, d'exécuter l'exemple et de consulter les résultats.  
  
#### <a name="to-create-the-tracking-profile"></a>Pour créer le modèle de suivi  
  
1.  Ouvrez une invite de commandes et exécutez  *\<exemples de chemin\>*\BAM\BAMFromExpression\Setup.bat. Si vous utilisez [!INCLUDE[btsWinVista](../includes/btswinvista-md.md)] ou [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)], ouvrez l'invite de commandes en tant qu'administrateur. Setup.bat initialise l'infrastructure BAM pour cet exemple et déploie l'activité BAM.  
  
2.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **éditeur**. Si vous utilisez [!INCLUDE[btsWinVista](../includes/btswinvista-md.md)] ou [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)], avec le bouton droit **éditeur** puis cliquez sur **exécuter en tant qu’administrateur**.  
  
3.  Dans le volet gauche de la **éditeur** fenêtre, cliquez sur **cliquez ici pour importer une définition d’activité BAM**.  
  
4.  Dans le **le nom de définition d’activité BAM** section de la **importer une définition d’activité BAM** boîte de dialogue, sélectionnez **FromExpressionPo**, puis cliquez sur **OK**.  
  
5.  Dans le volet droit de la **éditeur** fenêtre, cliquez sur **cliquez ici pour sélectionner une source d’événement**.  
  
6.  Dans le **nom de l’Assembly** section de la **sélectionner l’Assembly Parent Source événement** boîte de dialogue, sélectionnez **Microsoft.Samples.BizTalk.BamFromExpression**, puis cliquez sur  **Suivant**.  
  
7.  Dans le **nom de l’Orchestration** section de la **sélectionner une Orchestration** boîte de dialogue, sélectionnez **BamFromExpression.Orchestration1**, puis cliquez sur **OK**.  
  
8.  Cliquez sur le **Receive_1** mettre en forme, puis cliquez sur **schéma de charge utile de Message**.  
  
9. Développez  **\<schéma\>**, développez **PurchaseOrder**, développez **de**, puis faites glisser **PoID** à droite volet à **ActivityID** dans le volet gauche.  
  
10. Faites glisser les éléments suivants à partir du volet droit et déposez-les sur les nœuds nommés dans le volet gauche :  
  
    |De|Pour|  
    |----------|--------|  
    |Nom|De|  
    |État|État|  
    |Ville|Ville|  
    |Téléphone|Téléphone|  
    |Total|PoTotal|  
  
11. Cliquez sur l’icône de dossier avec la flèche (![bouton avec dossier et des &#45; flèche](../core/media/abccd08b-2b01-49c6-80ed-a032bbbd10d4.gif "abccd08b-2b01-49c6-80ed-a032bbbd10d4")) pour afficher l’orchestration.  
  
12. Faites glisser le **Receive_1** forme dans le volet droit pour **reçus** dans le volet gauche.  
  
13. Faites glisser le **Send_1** forme dans le volet droit pour **envoyer** dans le volet gauche.  
  
14. Enregistrer le modèle de suivi à  *\<exemples de chemin\>*\BAM\BamFromExpression\ BamFromExpression.btt.  
  
15. Sur le **outils** menu, cliquez sur **appliquer le modèle de suivi**.  
  
#### <a name="to-build-and-initialize-this-sample"></a>Pour créer et initialiser l'exemple  
  
-   Déployez le modèle de suivi BamFromExpression.btt. Pour plus d’informations, consultez [comment déployer des profils de suivi avec le suivi des profils de l’utilitaire de gestion](../core/how-to-deploy-tracking-profiles-with-the-tracking-profiles-management-utility.md).  
  
#### <a name="to-run-this-sample"></a>Pour exécuter l'exemple  
  
-   Copiez le fichier  *\<exemples de chemin\>*\BamFromExpression\InputMessage.xml à  *\<exemples de chemin\>*\BamFromExpression\Input.  
  
     Environ 10 secondes, le message de sortie s’affiche dans  *\<exemples de chemin\>*\BamFromExpression\Output.  
  
#### <a name="to-view-the-bam-data"></a>Pour afficher les données BAM  
  
1.  Ouvrez SQL Server Management Studio.  
  
2.  Dans SQL Server Management Studio, développez le serveur, **bases de données**, développez **BAMPrimaryImport**, puis développez **Tables**.  
  
3.  Avec le bouton droit **dbo.bam_FromExpressionPo_Completed**, puis cliquez sur **ouvrir la Table**. Si vous utilisez SQL Server, cliquez sur **sélectionner les 1000 lignes**.  
  
     Le contenu de la table bam_FromExpressionPo_Completed s'affiche dans le volet droit. La ligne dont l'ID d'activité est 123 représente le bon de commande d'une valeur de 345 $ que contenait le message entrant.  
  
4.  Avec le bouton droit **dbo.bam_FromExpressionPoItem_Completed**, puis cliquez sur **ouvrir la Table**. Si vous utilisez SQL Server, cliquez sur **sélectionner les 1000 lignes**.  
  
     Le contenu de la table bam_FromExpressionPoItem_Completed s'affiche dans le volet droit. Les deux lignes ayant activité ID 123_0 et 123_1 représentent les éléments dans l’ordre d’achat : articles Flash MC et décodeur infrarouge.  
  
5.  Avec le bouton droit **dbo.bam_FromExpressionPoItem_CompletedRelationships**, puis cliquez sur **ouvrir la Table**. Si vous utilisez SQL Server, cliquez sur **sélectionner les 1000 lignes**.  
  
     Le contenu de la table bam_FromExpressionPoItem_CompletedRelationships s'affiche dans le volet droit. Chaque ligne de la table représente une relation entre une activité FromExpressionPoItem et une activité FromExpressionPo. La valeur de la **ActivityID** colonne fait référence à l’ID d’activité de l’activité FromExpressionPoItem. La valeur de la **ReferenceData** colonne fait référence à l’ID d’activité de l’activité FromExpressionPo. Dans ce cas, les deux enregistrements indiquent que les articles Flash MC et décodeur infrarouge sont associés au bon de commande d'une valeur de 345 $.  
  
#### <a name="to-re-run-the-sample"></a>Pour réexécuter l'exemple  
  
1.  Ouvrez une invite de commandes et exécutez  *\<exemples de chemin\>*\BAM\BamFromExpression\Cleanup.bat pour supprimer le modèle de suivi et toute autre infrastructure BAM. Si vous utilisez [!INCLUDE[btsWinVista](../includes/btswinvista-md.md)] ou [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)], ouvrez l'invite de commandes en tant qu'administrateur.  
  
2.  Exécutez  *\<exemples de chemin\>*\BAM\BamFromExpression\Setup.bat pour compiler l’exemple et le déployer.  
  
## <a name="see-also"></a>Voir aussi  
 [Business Activity Monitoring (dossier d’exemples BizTalk Server)](../core/business-activity-monitoring-biztalk-server-samples-folder.md)   
 [Relations d’activité](../core/activity-relationships.md)