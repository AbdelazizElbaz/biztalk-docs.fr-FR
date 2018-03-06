---
title: "Régénérer le classeur des données actives | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4bd3a3fa-a550-4363-bbc0-2153226509ad
caps.latest.revision: 
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fabecd70c39f7bae14765a35c510f5c62c3814a9
ms.sourcegitcommit: 32f380810b90b70e5df7be72a6a14988a747868e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2018
---
# <a name="regenerate-the-live-data-workbook"></a>Régénérer le classeur des données actives
En cas de perte ou d'altération du classeur BAM de données actives, l'utilitaire de gestion de l'analyse BAM permet de regénérer ce classeur. Ce processus est également utile lorsque vous mettez à niveau à partir de versions précédentes de BizTalk Server.
  
 Les étapes générales sont les suivantes :  
  
-   Extraction de la définition d'analyse BAM à l'aide de l'utilitaire de gestion de l'analyse BAM  
  
-   Recréez les rapports de tableau croisé dynamique. Comme l'extraction XML effectuée avec la commande get-defxml ne contient que les activités et les vues actives, vous devez recréer les rapports de tableau croisé dynamique à l'aide du complément BAM pour Excel.  
  
-   Renommez les rapports de tableau croisé dynamique. Cette étape peut être nécessaire si vous mettez à niveau à partir d’une version précédente de BizTalk Server. Avec certaines versions, BAM stocke deux ensembles de noms pour les classeurs BAM : un nom complet et un nom interne. Lorsque vous extrayez une définition d'analyse BAM, le conteneur XML contient le nom interne du classeur. Vous devez renommer les rapports de tableau croisé dynamique pour vous assurer que le classeur de données actives comporte la connexion qui convient à la base de données.  
  
-   Régénérez le classeur de données actives à l'aide de l'utilitaire de gestion de l'analyse BAM.  
  
## <a name="retrieve-the-bam-definition"></a>Récupérer la définition BAM  
  
1.  Cliquez sur **Démarrer**, puis sur **Exécuter**, tapez **cmd**, puis cliquez sur **OK**.  
  
2.  À l’invite de commandes, accédez au répertoire suivant : [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]\Tracking.  
  
3.  Type : **bm.exe get-defxml-FileName:abc.xml**  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
## <a name="recreate-the-pivottable-reports"></a>Recréez les rapports de tableau croisé dynamique  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft Office**, puis cliquez sur **Microsoft Office Excel**.  
  
2.  Cliquez sur le **compléments** onglet, puis sélectionnez **Importer XML** à partir de la **BAM** liste déroulante dans le **commandes de Menu** groupe.  
  
    > [!NOTE]
    >  Si le **compléments** onglet n’est pas présent, suivez les instructions de [étape 1 : ajouter le complément BAM pour Microsoft Office Excel](http://msdn.microsoft.com/library/3400969f-0c54-4a75-979d-ad2f7af86448) pour ajouter le complément BAM.  
  
3.  Accédez au dossier [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]\Tracking, puis sélectionnez le fichier abc.xml.  
  
4.  Recréez les rapports de tableau croisé dynamique à partir de votre définition.  
  
5.  Enregistrez le classeur. Pour ce faire, cliquez sur le **fichier** menu, puis sur **enregistrer en tant que** et tapez monnouveauclasseur.xls lorsque vous y êtes invité pour un nom de fichier.  
  
## <a name="rename-the-pivottable-reports-optional"></a>Renommez les rapports de tableau croisé dynamique (facultatifs)  

> [!NOTE]
> Cette étape peut être nécessaire uniquement si vous mettez à niveau à partir d’une version antérieure de BizTalk Server. 

1.  Ouvrez le fichier abc.xml que vous avez créé lorsque vous avez extrait les définitions BAM à l’aide du bloc-notes en cliquant sur **Démarrer**, puis sur **exécuter**, tapez notepad [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]\Tracking\abc.xml, puis cliquez sur **OK**.  
  
2.  Recherchez le \<légende\> sous la balise \<BAMDefinition\>\\< Extension\>\\< OWC\>\\< PivotTableView\> \\< tableau croisé dynamique\>\\< PivotView\>\\< étiquette\>. Le contenu de cette balise est le nom interne de l'un des rapports de tableau croisé dynamique. Vous pouvez trouver le nom interne pour les autres rapports de tableau croisé dynamique en recherchant la prochaine \<légende\> balise. Ouvrez **monnouveauclasseur.xls** et utilisez les noms que vous avez trouvés pour renommer vos rapports de tableau croisé dynamique.  
  
3.  Enregistrez le classeur mis à jour.    
 
  
## <a name="regenerate-the-bam-live-data-workbook"></a>Régénérez le classeur de données actives BAM  

> [!NOTE]
>  Exécutez cet outil avec des privilèges d’administrateur.  


1.  Cliquez sur **Démarrer**, puis sur **Exécuter**, tapez **cmd**, puis cliquez sur **OK**.  
  
2.  À l’invite de commandes, accédez au répertoire suivant : [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]\Tracking.  
  
3.  Type : **bm.exe regenerate-livedataworkbook-workbookname : monnouveauclasseur.xls**  
  
## <a name="see-also"></a>Voir aussi  
 [La gestion BAM](../core/managing-bam.md)   
 [Utilitaire de gestion BAM](../core/bam-management-utility.md)   
 [Configuration requise pour utiliser le complément BAM pour Excel](../core/requirements-for-using-the-bam-add-in-for-excel.md)   
 [Étape 1 : Ajouter le complément BAM à Microsoft Office Excel](http://msdn.microsoft.com/library/3400969f-0c54-4a75-979d-ad2f7af86448)