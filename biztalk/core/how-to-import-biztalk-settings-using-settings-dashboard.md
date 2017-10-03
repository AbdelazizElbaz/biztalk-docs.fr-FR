---
title: "Importer ou exporter le panneau de configuration à l’aide de paramètres de BizTalk | Documents Microsoft"
description: "Administration de BizTalk Server permet d’importer ou exporter des paramètres entre les environnements BizTalk Server"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cc2f0b44-d79b-4f95-811a-0843e3d6d1c8
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5e33b8659701ab991f7b7467c8ab3edd8b79def4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="use-settings-dashboard-to-import-or-export-biztalk-settings"></a>Utilisez le panneau de configuration pour importer ou exporter les paramètres de BizTalk 

## <a name="overview"></a>Vue d'ensemble
Le Panneau de configuration BizTalk permet d'exporter les paramètres d'un environnement [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et d'importer ceux-ci dans un autre environnement [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], ce qui réduit le délai nécessaire à la mise en place de la solution. Ceci est particulièrement utile dans les scénarios où les administrateurs tentent d'ajuster les performances de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dans un environnement intermédiaire et, lorsque les résultats souhaités sont atteints, ils peuvent importer les paramètres dans un environnement de production. Cette rubrique contient une procédure pas à pas permettant d'importer les paramètres du groupe, de l'hôte et de l'instance d'hôte BizTalk à l'aide du panneau de configuration.  

> [!TIP]
> L’utilitaire de ligne de commande BTSTask peut également être utilisé pour importer ou exporter les paramètres de groupe, d’hôte et d’Instance de l’hôte. Consultez [importation ou exportation BizTalk paramètres à l’aide de BTSTask](how-to-import-biztalk-settings-using-btstask.md).

  
## <a name="prerequisites"></a>Conditions préalables  
 Pour effectuer cette opération, vous devez être connecté en tant que membre du groupe Administrateurs de BizTalk Server.  
  
## <a name="import-the-biztalk-group-host-and-host-instance-settings"></a>Importer le groupe BizTalk, hôte et paramètres de l’instance hôte  

> [!IMPORTANT]
>  Pour importer les paramètres de BizTalk Server à partir d’un environnement spécifique, doit avoir déjà enregistré et exporter ces paramètres dans un fichier XML. **Exportation des paramètres BizTalk** (dans cette rubrique) ou [importation ou exportation BizTalk paramètres à l’aide de BTSTask](how-to-import-biztalk-settings-using-btstask.md) peut aider.
  
 En important le fichier XML, vous pouvez répliquer les paramètres de BizTalk Server requis sur l'ordinateur cible. À l'aide du panneau de configuration, vous pouvez importer les paramètres du groupe, de l'hôte et de l'instance d'hôte, puis mapper les propriétés de ceux-ci. Ci-après sont présentées les hypothèses nécessaires pour importer les paramètres :  
  
-   La topologie de BizTalk Server est cohérente entre l'environnement source et l'environnement de destination.  
  
-   Les définitions d'hôte peuvent être mappées via ces environnements. Vous devez pouvoir mapper tous les hôtes de l'environnement source à ceux de l'environnement de destination.  
  
-   L'environnement de destination possède un matériel similaire (sinon identique) à l'environnement source. Ceci est essentiel car certains paramètres dépendent du matériel sous-jacent.  

### <a name="import-steps"></a>Étapes d’importation
  
1.  Dans le **Console d’Administration de BizTalk Server**, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], avec le bouton droit **groupe BizTalk**, puis cliquez sur **paramètres**.  
  
2.  Dans le **Panneau de configuration BizTalk** boîte de dialogue, cliquez sur **importation**. Le **Assistant Importation des paramètres** boîte de dialogue s’affiche.  
  
    > [!NOTE]
    >  Le **le groupe de Destination** affiche les informations de groupe de l’ordinateur cible sur lequel vous souhaitez importer les paramètres.  
  
     ![Spécifiez l’emplacement du fichier pour importer les paramètres](../core/media/importsettings-filelocation.jpg "ImportSettings_FileLocation")  
  
3.  Cliquez sur le **spécifier un emplacement de fichier** page, puis cliquez sur ![parcourir le fichier de paramètres](../core/media/importsettings-filelocationbrowse.gif "ImportSettings_FileLocationBrowse"). L'Explorateur de fichiers s'affiche.  
  
4.  Sélectionnez le fichier XML contenant les paramètres d’environnement source, puis cliquez sur **ouvrir**. Le **emplacement du fichier** affiche le chemin d’accès du fichier XML et le **groupe Source** est rempli avec les informations de groupe de l’ordinateur source. Cliquez sur **Suivant**.  
  
5.  Sur le **mappage de l’hôte** page, procédez comme suit :  
  
    1.  À partir de la **hôtes de Destination** , sélectionnez un hôte de destination pour lequel vous souhaitez spécifier l’hôte source, puis cliquez sur **ajouter**.  
  
         ![Héberger le mappage](../core/media/importsettings-hostmapping.gif "ImportSettings_HostMapping")  
  
    2.  Dans le **sélectionner l’entité Source** boîte de dialogue, sélectionnez l’hôte source, puis cliquez sur **OK**.  
  
        > [!NOTE]
        >  Pour mapper plusieurs hôtes de destination à un hôte source unique, répétez les étapes **5 a** et **5 b**.  
  
    3.  Dans le **mappage de l’hôte** , cliquez sur **suivant**.  
  
6.  Dans le **mappage des instances d’hôte** page, procédez comme suit :  
  
    1.  Dans la liste des instances d’hôte de destination, sélectionnez une instance d’hôte de destination pour lequel vous souhaitez spécifier l’instance d’hôte source, puis cliquez sur **ajouter**.  
  
        > [!NOTE]
        >  Les instances d'hôtes ne peuvent être mappées qu'à l'hôte correspondant qui a été créé dans le mappage de l'hôte. Par exemple, si vous spécifiez un mappage où **SourceHost1** est mappé à **DestinationHost1**, les instances de **DestinationHost1** ne peut être mappé vers les instances de **SourceHost1**.  
        >   
        >  L'assistant d'importation gère la contrainte ci-dessus. Si vous ne respectez pas cette contrainte, les tâches BizTalk généreront des erreurs.  
        >   
        >  Vous devez utiliser la convention **nomhôte : nommachine** pour spécifier une instance d’hôte dans un fichier de mappage. Par exemple, **host1 : server1** dans un mappage de fichier indique que l’instance de **Host1** est en cours d’exécution ou disponible sur **Serveur1**.  
  
         ![Héberger le mappage d’une Instance](../core/media/importsettings-hostinstancemapping.gif "ImportSettings_HostInstanceMapping")  
  
    2.  Dans le **sélectionner l’entité Source** boîte de dialogue, sélectionnez l’instance d’hôte source, puis cliquez sur **OK**.  
  
        > [!NOTE]
        >  Pour mapper plusieurs instances d’hôte de destination à une instance d’hôte source unique, répétez les étapes **6 a** à **6 b**.  
  
    3.  Dans le **mappage des instances d’hôte** , cliquez sur **suivant**.  
  
7.  Dans le **résumé d’importation** boîte de dialogue, vérifiez si tous les paramètres d’importation pour les environnements source et de destination, vous avez créé sont comme vous le souhaitez, puis cliquez sur **importer**. Le **progression** page affiche la progression de l’importation des paramètres.  
  
    > [!WARNING]
    >  Vous ne pouvez pas annuler l'importation des paramètres de BizTalk Server. Si vous cliquez sur **importation**, le processus d’importation des paramètres à partir de l’environnement source sur l’environnement de destination est lancé et **Annuler** est désactivé. Vérifiez à poursuivre l’importation avant de cliquer sur **importer**.  
  
8.  Dans le **importer les résultats** onglet, vérifiez l’état de l’importation des paramètres de groupe, hôte et une Instance d’hôte, puis cliquez sur **Terminer** pour terminer l’opération d’importation. Tous les paramètres de l'environnement source importés sont appliqués à l'environnement de destination.  
  
     ![Importer les résultats](../core/media/importsettings-importresults.gif "ImportSettings_ImportResults")  

## <a name="export-the-biztalk-group-host-and-host-instance-settings"></a>Exporter le groupe BizTalk, hôte et paramètres de l’instance hôte  

1.  Dans le **Console d’Administration de BizTalk Server**, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], avec le bouton droit **groupe BizTalk**, puis cliquez sur **paramètres**.  
  
2.  Dans le **Panneau de configuration BizTalk** boîte de dialogue, cliquez sur **exporter**. La boîte de dialogue **Enregistrer sous** s’affiche.  
  
3.  Accédez à l'emplacement dans lequel vous souhaitez enregistrer les paramètres BizTalk actuels. Entrez le nom de fichier, sélectionnez le type de format XML, puis cliquez sur **enregistrer**.  

> [!IMPORTANT]
>  N’est pas pas recommandée manuellement la mise à jour le fichier XML exporté. Lorsque vous importez un fichier XML mis à jour dans un environnement de production, le processus d’importation peut échouer en raison d’une incompatibilité de type de données ou d’autres erreurs introduites par une modification manuelle.  

## <a name="see-also"></a>Voir aussi  
 [À l’aide du Panneau de configuration de BizTalk Server réglage des performances](../core/using-settings-dashboard-for-biztalk-server-performance-tuning.md)