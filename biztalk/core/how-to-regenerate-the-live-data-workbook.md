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
# <a name="regenerate-the-live-data-workbook"></a><span data-ttu-id="45edf-102">Régénérer le classeur des données actives</span><span class="sxs-lookup"><span data-stu-id="45edf-102">Regenerate the Live Data Workbook</span></span>
<span data-ttu-id="45edf-103">En cas de perte ou d'altération du classeur BAM de données actives, l'utilitaire de gestion de l'analyse BAM permet de regénérer ce classeur.</span><span class="sxs-lookup"><span data-stu-id="45edf-103">In cases where the BAM live data workbook has been lost or corrupted, you can regenerate the workbook using the BAM Management utiprolity.</span></span> <span data-ttu-id="45edf-104">Ce processus est également utile lorsque vous mettez à niveau à partir de versions précédentes de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="45edf-104">This process is also useful when you are upgrading from from previous BizTalk Server versions.</span></span>
  
 <span data-ttu-id="45edf-105">Les étapes générales sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="45edf-105">The general steps are as follows:</span></span>  
  
-   <span data-ttu-id="45edf-106">Extraction de la définition d'analyse BAM à l'aide de l'utilitaire de gestion de l'analyse BAM</span><span class="sxs-lookup"><span data-stu-id="45edf-106">Retrieve the BAM definition from the BAM database using the BAM Management utility.</span></span>  
  
-   <span data-ttu-id="45edf-107">Recréez les rapports de tableau croisé dynamique.</span><span class="sxs-lookup"><span data-stu-id="45edf-107">Re-create the PivotTable reports.</span></span> <span data-ttu-id="45edf-108">Comme l'extraction XML effectuée avec la commande get-defxml ne contient que les activités et les vues actives, vous devez recréer les rapports de tableau croisé dynamique à l'aide du complément BAM pour Excel.</span><span class="sxs-lookup"><span data-stu-id="45edf-108">Since the XML retrieval by the get-defxml command contains only the activities and views, you must re-create the PivotTable reports using the BAM Add-in for Excel.</span></span>  
  
-   <span data-ttu-id="45edf-109">Renommez les rapports de tableau croisé dynamique.</span><span class="sxs-lookup"><span data-stu-id="45edf-109">Rename the PivotTable reports.</span></span> <span data-ttu-id="45edf-110">Cette étape peut être nécessaire si vous mettez à niveau à partir d’une version précédente de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="45edf-110">This step may be necessary if you are upgrading from a previous BizTalk Server version.</span></span> <span data-ttu-id="45edf-111">Avec certaines versions, BAM stocke deux ensembles de noms pour les classeurs BAM : un nom complet et un nom interne.</span><span class="sxs-lookup"><span data-stu-id="45edf-111">With some versions, BAM stores two sets of names for BAM workbooks: a display name and an internal name.</span></span> <span data-ttu-id="45edf-112">Lorsque vous extrayez une définition d'analyse BAM, le conteneur XML contient le nom interne du classeur.</span><span class="sxs-lookup"><span data-stu-id="45edf-112">When you retrieve the BAM definition, the XML contains the internal name for the workbook.</span></span> <span data-ttu-id="45edf-113">Vous devez renommer les rapports de tableau croisé dynamique pour vous assurer que le classeur de données actives comporte la connexion qui convient à la base de données.</span><span class="sxs-lookup"><span data-stu-id="45edf-113">You must rename the PivotTable reports to ensure that the live data workbook has the correct connection to the database.</span></span>  
  
-   <span data-ttu-id="45edf-114">Régénérez le classeur de données actives à l'aide de l'utilitaire de gestion de l'analyse BAM.</span><span class="sxs-lookup"><span data-stu-id="45edf-114">Regenerate the live data workbook using the BAM Management utility.</span></span>  
  
## <a name="retrieve-the-bam-definition"></a><span data-ttu-id="45edf-115">Récupérer la définition BAM</span><span class="sxs-lookup"><span data-stu-id="45edf-115">Retrieve the BAM definition</span></span>  
  
1.  <span data-ttu-id="45edf-116">Cliquez sur **Démarrer**, puis sur **Exécuter**, tapez **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="45edf-116">Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="45edf-117">À l’invite de commandes, accédez au répertoire suivant : [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]\Tracking.</span><span class="sxs-lookup"><span data-stu-id="45edf-117">At the command prompt, navigate to the following directory: [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]\Tracking.</span></span>  
  
3.  <span data-ttu-id="45edf-118">Type : **bm.exe get-defxml-FileName:abc.xml**</span><span class="sxs-lookup"><span data-stu-id="45edf-118">Type: **bm.exe get-defxml -FileName:abc.xml**</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="45edf-119">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="45edf-119">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="recreate-the-pivottable-reports"></a><span data-ttu-id="45edf-120">Recréez les rapports de tableau croisé dynamique</span><span class="sxs-lookup"><span data-stu-id="45edf-120">Recreate the PivotTable reports</span></span>  
  
1.  <span data-ttu-id="45edf-121">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft Office**, puis cliquez sur **Microsoft Office Excel**.</span><span class="sxs-lookup"><span data-stu-id="45edf-121">Click **Start**, point to **All Programs**, point to **Microsoft Office**, and then click **Microsoft Office Excel**.</span></span>  
  
2.  <span data-ttu-id="45edf-122">Cliquez sur le **compléments** onglet, puis sélectionnez **Importer XML** à partir de la **BAM** liste déroulante dans le **commandes de Menu** groupe.</span><span class="sxs-lookup"><span data-stu-id="45edf-122">Click the **Add-Ins** tab, and then select **Import XML** from the **BAM** drop-down list in the **Menu Commands** group.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="45edf-123">Si le **compléments** onglet n’est pas présent, suivez les instructions de [étape 1 : ajouter le complément BAM pour Microsoft Office Excel](http://msdn.microsoft.com/library/3400969f-0c54-4a75-979d-ad2f7af86448) pour ajouter le complément BAM.</span><span class="sxs-lookup"><span data-stu-id="45edf-123">If the **Add-Ins** tab is not present, follow the instructions in [Step 1: Add the BAM Add-In to Microsoft Office Excel](http://msdn.microsoft.com/library/3400969f-0c54-4a75-979d-ad2f7af86448) to add the BAM add-in.</span></span>  
  
3.  <span data-ttu-id="45edf-124">Accédez au dossier [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]\Tracking, puis sélectionnez le fichier abc.xml.</span><span class="sxs-lookup"><span data-stu-id="45edf-124">Navigate to the [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]\Tracking folder and select the abc.xml file.</span></span>  
  
4.  <span data-ttu-id="45edf-125">Recréez les rapports de tableau croisé dynamique à partir de votre définition.</span><span class="sxs-lookup"><span data-stu-id="45edf-125">Re-create your PivotTable reports based on your definition.</span></span>  
  
5.  <span data-ttu-id="45edf-126">Enregistrez le classeur.</span><span class="sxs-lookup"><span data-stu-id="45edf-126">Save the workbook.</span></span> <span data-ttu-id="45edf-127">Pour ce faire, cliquez sur le **fichier** menu, puis sur **enregistrer en tant que** et tapez monnouveauclasseur.xls lorsque vous y êtes invité pour un nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="45edf-127">To do this, click the **File** menu, and then click **Save As** and type mynewbook.xls when prompted for a file name.</span></span>  
  
## <a name="rename-the-pivottable-reports-optional"></a><span data-ttu-id="45edf-128">Renommez les rapports de tableau croisé dynamique (facultatifs)</span><span class="sxs-lookup"><span data-stu-id="45edf-128">Rename the PivotTable reports (optional)</span></span>  

> [!NOTE]
> <span data-ttu-id="45edf-129">Cette étape peut être nécessaire uniquement si vous mettez à niveau à partir d’une version antérieure de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="45edf-129">This step may only be required if you are upgrading from an older version of BizTalk Server.</span></span> 

1.  <span data-ttu-id="45edf-130">Ouvrez le fichier abc.xml que vous avez créé lorsque vous avez extrait les définitions BAM à l’aide du bloc-notes en cliquant sur **Démarrer**, puis sur **exécuter**, tapez notepad [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]\Tracking\abc.xml, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="45edf-130">Open the abc.xml file that you created when you retrieved the BAM definitions using Notepad by clicking **Start**, clicking **Run**, typing notepad [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]\Tracking\abc.xml, and then clicking **OK**.</span></span>  
  
2.  <span data-ttu-id="45edf-131">Recherchez le \<légende\> sous la balise \<BAMDefinition\>\\< Extension\>\\< OWC\>\\< PivotTableView\> \\< tableau croisé dynamique\>\\< PivotView\>\\< étiquette\>.</span><span class="sxs-lookup"><span data-stu-id="45edf-131">Locate the \<Caption\> tag under \<BAMDefinition\>\\<Extension\>\\<OWC\>\\<PivotTableView\>\\<PivotTable\>\\<PivotView\>\\<Label\>.</span></span> <span data-ttu-id="45edf-132">Le contenu de cette balise est le nom interne de l'un des rapports de tableau croisé dynamique.</span><span class="sxs-lookup"><span data-stu-id="45edf-132">The content of this tag is the internal name for one of your PivotTable reports.</span></span> <span data-ttu-id="45edf-133">Vous pouvez trouver le nom interne pour les autres rapports de tableau croisé dynamique en recherchant la prochaine \<légende\> balise.</span><span class="sxs-lookup"><span data-stu-id="45edf-133">You can find the internal name for the other PivotTable reports by locating the next \<Caption\> tag.</span></span> <span data-ttu-id="45edf-134">Ouvrez **monnouveauclasseur.xls** et utilisez les noms que vous avez trouvés pour renommer vos rapports de tableau croisé dynamique.</span><span class="sxs-lookup"><span data-stu-id="45edf-134">Open **mynewbook.xls** and use the names you located to rename your PivotTable reports.</span></span>  
  
3.  <span data-ttu-id="45edf-135">Enregistrez le classeur mis à jour.</span><span class="sxs-lookup"><span data-stu-id="45edf-135">Save the updated workbook.</span></span>    
 
  
## <a name="regenerate-the-bam-live-data-workbook"></a><span data-ttu-id="45edf-136">Régénérez le classeur de données actives BAM</span><span class="sxs-lookup"><span data-stu-id="45edf-136">Regenerate the BAM live data workbook</span></span>  

> [!NOTE]
>  <span data-ttu-id="45edf-137">Exécutez cet outil avec des privilèges d’administrateur.</span><span class="sxs-lookup"><span data-stu-id="45edf-137">Run this tool with Administrative privileges.</span></span>  


1.  <span data-ttu-id="45edf-138">Cliquez sur **Démarrer**, puis sur **Exécuter**, tapez **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="45edf-138">Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="45edf-139">À l’invite de commandes, accédez au répertoire suivant : [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]\Tracking.</span><span class="sxs-lookup"><span data-stu-id="45edf-139">At the command prompt, navigate to the following directory: [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]\Tracking.</span></span>  
  
3.  <span data-ttu-id="45edf-140">Type : **bm.exe regenerate-livedataworkbook-workbookname : monnouveauclasseur.xls**</span><span class="sxs-lookup"><span data-stu-id="45edf-140">Type: **bm.exe regenerate-livedataworkbook -WorkbookName:mynewbook.xls**</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45edf-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="45edf-141">See Also</span></span>  
 <span data-ttu-id="45edf-142">[La gestion BAM](../core/managing-bam.md) </span><span class="sxs-lookup"><span data-stu-id="45edf-142">[Managing BAM](../core/managing-bam.md) </span></span>  
 <span data-ttu-id="45edf-143">[Utilitaire de gestion BAM](../core/bam-management-utility.md) </span><span class="sxs-lookup"><span data-stu-id="45edf-143">[BAM Management Utility](../core/bam-management-utility.md) </span></span>  
 <span data-ttu-id="45edf-144">[Configuration requise pour utiliser le complément BAM pour Excel](../core/requirements-for-using-the-bam-add-in-for-excel.md) </span><span class="sxs-lookup"><span data-stu-id="45edf-144">[Requirements for Using the BAM Add-In for Excel](../core/requirements-for-using-the-bam-add-in-for-excel.md) </span></span>  
 [<span data-ttu-id="45edf-145">Étape 1 : Ajouter le complément BAM à Microsoft Office Excel</span><span class="sxs-lookup"><span data-stu-id="45edf-145">Step 1: Add the BAM Add-In to Microsoft Office Excel</span></span>](http://msdn.microsoft.com/library/3400969f-0c54-4a75-979d-ad2f7af86448)