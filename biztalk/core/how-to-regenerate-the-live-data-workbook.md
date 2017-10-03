---
title: "Comment faire pour régénérer le classeur des données actives | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4bd3a3fa-a550-4363-bbc0-2153226509ad
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8fcabebb1429fae8531753a8a3aede5595bb148f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-regenerate-the-live-data-workbook"></a>Régénération du classeur des données actives
En cas de perte ou d'altération du classeur BAM de données actives, l'utilitaire de gestion de l'analyse BAM permet de regénérer ce classeur. Ceci est également utile lorsque vous voulez effectuer une mise à niveau de [!INCLUDE[btsBizTalkServer2004](../includes/btsbiztalkserver2004-md.md)] à [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)], car les classeurs de données actives [!INCLUDE[btsBizTalkServer2004](../includes/btsbiztalkserver2004-md.md)] ne sont pas compatibles avec [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)].  
  
 Les étapes générales sont les suivantes :  
  
-   Extraction de la définition d'analyse BAM à l'aide de l'utilitaire de gestion de l'analyse BAM  
  
-   Recréez les rapports de tableau croisé dynamique. Comme l'extraction XML effectuée avec la commande get-defxml ne contient que les activités et les vues actives, vous devez recréer les rapports de tableau croisé dynamique à l'aide du complément BAM pour Excel.  
  
-   Renommez les rapports de tableau croisé dynamique. Cette étape est nécessaire si vous effectuez une mise à niveau de [!INCLUDE[btsBizTalkServer2004](../includes/btsbiztalkserver2004-md.md)] vers [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]. Cela est nécessaire puisque dans [!INCLUDE[btsBizTalkServer2004](../includes/btsbiztalkserver2004-md.md)], BAM stocke deux ensembles de noms pour les classeurs BAM : un nom complet et un nom interne. Lorsque vous extrayez une définition d'analyse BAM, le conteneur XML contient le nom interne du classeur. Vous devez renommer les rapports de tableau croisé dynamique pour vous assurer que le classeur de données actives comporte la connexion qui convient à la base de données.  
  
-   Régénérez le classeur de données actives à l'aide de l'utilitaire de gestion de l'analyse BAM.  
  
### <a name="to-retrieve-the-bam-definition"></a>Pour extraire la définition d'analyse BAM  
  
1.  Cliquez sur **Démarrer**, puis sur **Exécuter**, tapez **cmd**, puis cliquez sur **OK**.  
  
2.  À l'invite de commandes, accédez au répertoire suivant : [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Suivi.  
  
3.  Type : **bm.exe get-defxml-FileName:abc.xml**  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
### <a name="to-re-create-the-pivottable-reports"></a>Pour recréer les rapports de tableau croisé dynamique  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft Office**, puis cliquez sur **Microsoft Office Excel**.  
  
2.  Cliquez sur le **compléments** onglet, puis sélectionnez **Importer XML** à partir de la **BAM** liste déroulante dans le **commandes de Menu** groupe.  
  
    > [!NOTE]
    >  Si le **compléments** onglet n’est pas présent, suivez les instructions de [étape 1 : ajouter le complément BAM pour Microsoft Office Excel](http://msdn.microsoft.com/library/3400969f-0c54-4a75-979d-ad2f7af86448) pour ajouter le complément BAM.  
  
3.  Accédez au dossier [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking, puis sélectionnez le fichier abc.xml.  
  
4.  Recréez les rapports de tableau croisé dynamique à partir de votre définition.  
  
5.  Enregistrez le classeur. Pour ce faire, cliquez sur le **fichier** menu, puis sur **enregistrer en tant que** et tapez monnouveauclasseur.xls lorsque vous y êtes invité pour un nom de fichier.  
  
### <a name="to-rename-the-pivottable-reports-optional"></a>Pour renommer les rapports de tableau croisé dynamique (facultatif)  
  
1.  Ouvrez le fichier abc.xml que vous avez créé lorsque vous avez extrait les définitions BAM à l’aide du bloc-notes en cliquant sur **Démarrer**, puis sur **exécuter**, tapez notepad [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]tracking\abc.XML, puis en cliquant sur  **OK**.  
  
2.  Recherchez le \<Caption > sous la balise \<BAMDefinition >\\< Extension\>\\< OWC\>\\< PivotTableView\>\\< Tableau croisé dynamique\>\\< PivotView\>\\< étiquette\>. Le contenu de cette balise est le nom interne de l'un des rapports de tableau croisé dynamique. Vous pouvez trouver le nom interne pour les autres rapports de tableau croisé dynamique en recherchant la prochaine \<légende > balise. Ouvrez **monnouveauclasseur.xls** et utilisez les noms que vous avez trouvés pour renommer vos rapports de tableau croisé dynamique.  
  
3.  Enregistrez le classeur mis à jour.  
  
    > [!NOTE]
    >  Effectuez la procédure suivante uniquement si vous procédez à une mise à niveau de [!INCLUDE[btsBizTalkServer2004](../includes/btsbiztalkserver2004-md.md)] vers [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)].  
  
### <a name="to-regenerate-the-bam-live-data-workbook"></a>Pour régénérer le classeur de données actives d'analyse BAM  
  
1.  Cliquez sur **Démarrer**, puis sur **Exécuter**, tapez **cmd**, puis cliquez sur **OK**.  
  
2.  À l'invite de commandes, accédez au répertoire suivant : [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Suivi.  
  
3.  Type : **bm.exe regenerate-livedataworkbook-workbookname : monnouveauclasseur.xls**  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
## <a name="see-also"></a>Voir aussi  
 [La gestion BAM](../core/managing-bam.md)   
 [Utilitaire de gestion BAM](../core/bam-management-utility.md)   
 [Configuration requise pour utiliser le complément BAM pour Excel](../core/requirements-for-using-the-bam-add-in-for-excel.md)   
 [Étape 1 : Ajouter le complément BAM à Microsoft Office Excel](http://msdn.microsoft.com/library/3400969f-0c54-4a75-979d-ad2f7af86448)