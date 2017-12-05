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
ms.openlocfilehash: e3e98ac5f02363c02ff422f44397fbf1f0e3b4c0
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="how-to-regenerate-the-live-data-workbook"></a><span data-ttu-id="b7d11-102">Régénération du classeur des données actives</span><span class="sxs-lookup"><span data-stu-id="b7d11-102">How to Regenerate the Live Data Workbook</span></span>
<span data-ttu-id="b7d11-103">En cas de perte ou d'altération du classeur BAM de données actives, l'utilitaire de gestion de l'analyse BAM permet de regénérer ce classeur.</span><span class="sxs-lookup"><span data-stu-id="b7d11-103">In cases where the BAM live data workbook has been lost or corrupted, you can regenerate the workbook using the BAM Management utiprolity.</span></span> <span data-ttu-id="b7d11-104">Ce processus est également utile lorsque vous mettez à niveau à partir de [!INCLUDE[btsBizTalkServer2004](../includes/btsbiztalkserver2004-md.md)] à BizTalk Server, depuis les classeurs de données actives [!INCLUDE[btsBizTalkServer2004](../includes/btsbiztalkserver2004-md.md)] ne sont pas compatibles avec BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="b7d11-104">This process is also useful when you are upgrading from [!INCLUDE[btsBizTalkServer2004](../includes/btsbiztalkserver2004-md.md)] to BizTalk Server, since live data workbooks for [!INCLUDE[btsBizTalkServer2004](../includes/btsbiztalkserver2004-md.md)] are not compatible with BizTalk Server.</span></span>  
  
 <span data-ttu-id="b7d11-105">Les étapes générales sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="b7d11-105">The general steps are as follows:</span></span>  
  
-   <span data-ttu-id="b7d11-106">Extraction de la définition d'analyse BAM à l'aide de l'utilitaire de gestion de l'analyse BAM</span><span class="sxs-lookup"><span data-stu-id="b7d11-106">Retrieve the BAM definition from the BAM database using the BAM Management utility.</span></span>  
  
-   <span data-ttu-id="b7d11-107">Recréez les rapports de tableau croisé dynamique.</span><span class="sxs-lookup"><span data-stu-id="b7d11-107">Re-create the PivotTable reports.</span></span> <span data-ttu-id="b7d11-108">Comme l'extraction XML effectuée avec la commande get-defxml ne contient que les activités et les vues actives, vous devez recréer les rapports de tableau croisé dynamique à l'aide du complément BAM pour Excel.</span><span class="sxs-lookup"><span data-stu-id="b7d11-108">Since the XML retrieval by the get-defxml command contains only the activities and views, you must re-create the PivotTable reports using the BAM Add-in for Excel.</span></span>  
  
-   <span data-ttu-id="b7d11-109">Renommez les rapports de tableau croisé dynamique.</span><span class="sxs-lookup"><span data-stu-id="b7d11-109">Rename the PivotTable reports.</span></span> <span data-ttu-id="b7d11-110">Cette étape est nécessaire si vous mettez à niveau à partir de [!INCLUDE[btsBizTalkServer2004](../includes/btsbiztalkserver2004-md.md)] à BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="b7d11-110">This step is necessary if you are upgrading from [!INCLUDE[btsBizTalkServer2004](../includes/btsbiztalkserver2004-md.md)] to BizTalk Server.</span></span> <span data-ttu-id="b7d11-111">Cela est nécessaire puisque dans [!INCLUDE[btsBizTalkServer2004](../includes/btsbiztalkserver2004-md.md)], BAM stocke deux ensembles de noms pour les classeurs BAM : un nom complet et un nom interne.</span><span class="sxs-lookup"><span data-stu-id="b7d11-111">This is necessary since in [!INCLUDE[btsBizTalkServer2004](../includes/btsbiztalkserver2004-md.md)], BAM stores two sets of names for BAM workbooks: a display name and an internal name.</span></span> <span data-ttu-id="b7d11-112">Lorsque vous extrayez une définition d'analyse BAM, le conteneur XML contient le nom interne du classeur.</span><span class="sxs-lookup"><span data-stu-id="b7d11-112">When you retrieve the BAM definition, the XML contains the internal name for the workbook.</span></span> <span data-ttu-id="b7d11-113">Vous devez renommer les rapports de tableau croisé dynamique pour vous assurer que le classeur de données actives comporte la connexion qui convient à la base de données.</span><span class="sxs-lookup"><span data-stu-id="b7d11-113">You must rename the PivotTable reports to ensure that the live data workbook has the correct connection to the database.</span></span>  
  
-   <span data-ttu-id="b7d11-114">Régénérez le classeur de données actives à l'aide de l'utilitaire de gestion de l'analyse BAM.</span><span class="sxs-lookup"><span data-stu-id="b7d11-114">Regenerate the live data workbook using the BAM Management utility.</span></span>  
  
### <a name="to-retrieve-the-bam-definition"></a><span data-ttu-id="b7d11-115">Pour extraire la définition d'analyse BAM</span><span class="sxs-lookup"><span data-stu-id="b7d11-115">To retrieve the BAM definition</span></span>  
  
1.  <span data-ttu-id="b7d11-116">Cliquez sur **Démarrer**, puis sur **Exécuter**, tapez **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="b7d11-116">Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="b7d11-117">À l'invite de commandes, accédez au répertoire suivant : [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Suivi.</span><span class="sxs-lookup"><span data-stu-id="b7d11-117">At the command prompt, navigate to the following directory: [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.</span></span>  
  
3.  <span data-ttu-id="b7d11-118">Type : **bm.exe get-defxml-FileName:abc.xml**</span><span class="sxs-lookup"><span data-stu-id="b7d11-118">Type: **bm.exe get-defxml -FileName:abc.xml**</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b7d11-119">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="b7d11-119">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
### <a name="to-re-create-the-pivottable-reports"></a><span data-ttu-id="b7d11-120">Pour recréer les rapports de tableau croisé dynamique</span><span class="sxs-lookup"><span data-stu-id="b7d11-120">To re-create the PivotTable reports</span></span>  
  
1.  <span data-ttu-id="b7d11-121">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft Office**, puis cliquez sur **Microsoft Office Excel**.</span><span class="sxs-lookup"><span data-stu-id="b7d11-121">Click **Start**, point to **All Programs**, point to **Microsoft Office**, and then click **Microsoft Office Excel**.</span></span>  
  
2.  <span data-ttu-id="b7d11-122">Cliquez sur le **compléments** onglet, puis sélectionnez **Importer XML** à partir de la **BAM** liste déroulante dans le **commandes de Menu** groupe.</span><span class="sxs-lookup"><span data-stu-id="b7d11-122">Click the **Add-Ins** tab, and then select **Import XML** from the **BAM** drop-down list in the **Menu Commands** group.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b7d11-123">Si le **compléments** onglet n’est pas présent, suivez les instructions de [étape 1 : ajouter le complément BAM pour Microsoft Office Excel](http://msdn.microsoft.com/library/3400969f-0c54-4a75-979d-ad2f7af86448) pour ajouter le complément BAM.</span><span class="sxs-lookup"><span data-stu-id="b7d11-123">If the **Add-Ins** tab is not present, follow the instructions in [Step 1: Add the BAM Add-In to Microsoft Office Excel](http://msdn.microsoft.com/library/3400969f-0c54-4a75-979d-ad2f7af86448) to add the BAM add-in.</span></span>  
  
3.  <span data-ttu-id="b7d11-124">Accédez au dossier [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking, puis sélectionnez le fichier abc.xml.</span><span class="sxs-lookup"><span data-stu-id="b7d11-124">Navigate to the [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking folder and select the abc.xml file.</span></span>  
  
4.  <span data-ttu-id="b7d11-125">Recréez les rapports de tableau croisé dynamique à partir de votre définition.</span><span class="sxs-lookup"><span data-stu-id="b7d11-125">Re-create your PivotTable reports based on your definition.</span></span>  
  
5.  <span data-ttu-id="b7d11-126">Enregistrez le classeur.</span><span class="sxs-lookup"><span data-stu-id="b7d11-126">Save the workbook.</span></span> <span data-ttu-id="b7d11-127">Pour ce faire, cliquez sur le **fichier** menu, puis sur **enregistrer en tant que** et tapez monnouveauclasseur.xls lorsque vous y êtes invité pour un nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="b7d11-127">To do this, click the **File** menu, and then click **Save As** and type mynewbook.xls when prompted for a file name.</span></span>  
  
### <a name="to-rename-the-pivottable-reports-optional"></a><span data-ttu-id="b7d11-128">Pour renommer les rapports de tableau croisé dynamique (facultatif)</span><span class="sxs-lookup"><span data-stu-id="b7d11-128">To rename the PivotTable reports (optional)</span></span>  
  
1.  <span data-ttu-id="b7d11-129">Ouvrez le fichier abc.xml que vous avez créé lorsque vous avez extrait les définitions BAM à l’aide du bloc-notes en cliquant sur **Démarrer**, puis sur **exécuter**, tapez notepad [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]tracking\abc.XML, puis en cliquant sur  **OK**.</span><span class="sxs-lookup"><span data-stu-id="b7d11-129">Open the abc.xml file that you created when you retrieved the BAM definitions using Notepad by clicking **Start**, clicking **Run**, typing notepad [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking\abc.xml, and then clicking **OK**.</span></span>  
  
2.  <span data-ttu-id="b7d11-130">Recherchez le \<légende\> sous la balise \<BAMDefinition\>\\< Extension\>\\< OWC\>\\< PivotTableView\> \\< tableau croisé dynamique\>\\< PivotView\>\\< étiquette\>.</span><span class="sxs-lookup"><span data-stu-id="b7d11-130">Locate the \<Caption\> tag under \<BAMDefinition\>\\<Extension\>\\<OWC\>\\<PivotTableView\>\\<PivotTable\>\\<PivotView\>\\<Label\>.</span></span> <span data-ttu-id="b7d11-131">Le contenu de cette balise est le nom interne de l'un des rapports de tableau croisé dynamique.</span><span class="sxs-lookup"><span data-stu-id="b7d11-131">The content of this tag is the internal name for one of your PivotTable reports.</span></span> <span data-ttu-id="b7d11-132">Vous pouvez trouver le nom interne pour les autres rapports de tableau croisé dynamique en recherchant la prochaine \<légende\> balise.</span><span class="sxs-lookup"><span data-stu-id="b7d11-132">You can find the internal name for the other PivotTable reports by locating the next \<Caption\> tag.</span></span> <span data-ttu-id="b7d11-133">Ouvrez **monnouveauclasseur.xls** et utilisez les noms que vous avez trouvés pour renommer vos rapports de tableau croisé dynamique.</span><span class="sxs-lookup"><span data-stu-id="b7d11-133">Open **mynewbook.xls** and use the names you located to rename your PivotTable reports.</span></span>  
  
3.  <span data-ttu-id="b7d11-134">Enregistrez le classeur mis à jour.</span><span class="sxs-lookup"><span data-stu-id="b7d11-134">Save the updated workbook.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b7d11-135">Vous devez suivre cette procédure uniquement si vous mettez à niveau à partir de [!INCLUDE[btsBizTalkServer2004](../includes/btsbiztalkserver2004-md.md)] à BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="b7d11-135">You must follow this procedure only if you are upgrading from [!INCLUDE[btsBizTalkServer2004](../includes/btsbiztalkserver2004-md.md)] to BizTalk Server.</span></span>  
  
### <a name="to-regenerate-the-bam-live-data-workbook"></a><span data-ttu-id="b7d11-136">Pour régénérer le classeur de données actives d'analyse BAM</span><span class="sxs-lookup"><span data-stu-id="b7d11-136">To regenerate the BAM live data workbook</span></span>  
  
1.  <span data-ttu-id="b7d11-137">Cliquez sur **Démarrer**, puis sur **Exécuter**, tapez **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="b7d11-137">Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="b7d11-138">À l'invite de commandes, accédez au répertoire suivant : [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Suivi.</span><span class="sxs-lookup"><span data-stu-id="b7d11-138">At the command prompt, navigate to the following directory: [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.</span></span>  
  
3.  <span data-ttu-id="b7d11-139">Type : **bm.exe regenerate-livedataworkbook-workbookname : monnouveauclasseur.xls**</span><span class="sxs-lookup"><span data-stu-id="b7d11-139">Type: **bm.exe regenerate-livedataworkbook -WorkbookName:mynewbook.xls**</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b7d11-140">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="b7d11-140">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7d11-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b7d11-141">See Also</span></span>  
 <span data-ttu-id="b7d11-142">[La gestion BAM](../core/managing-bam.md) </span><span class="sxs-lookup"><span data-stu-id="b7d11-142">[Managing BAM](../core/managing-bam.md) </span></span>  
 <span data-ttu-id="b7d11-143">[Utilitaire de gestion BAM](../core/bam-management-utility.md) </span><span class="sxs-lookup"><span data-stu-id="b7d11-143">[BAM Management Utility](../core/bam-management-utility.md) </span></span>  
 <span data-ttu-id="b7d11-144">[Configuration requise pour utiliser le complément BAM pour Excel](../core/requirements-for-using-the-bam-add-in-for-excel.md) </span><span class="sxs-lookup"><span data-stu-id="b7d11-144">[Requirements for Using the BAM Add-In for Excel](../core/requirements-for-using-the-bam-add-in-for-excel.md) </span></span>  
 [<span data-ttu-id="b7d11-145">Étape 1 : Ajouter le complément BAM à Microsoft Office Excel</span><span class="sxs-lookup"><span data-stu-id="b7d11-145">Step 1: Add the BAM Add-In to Microsoft Office Excel</span></span>](http://msdn.microsoft.com/library/3400969f-0c54-4a75-979d-ad2f7af86448)