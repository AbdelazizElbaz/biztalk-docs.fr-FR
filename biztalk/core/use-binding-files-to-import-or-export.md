---
title: Utiliser des fichiers de liaison pour importer ou exporter | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f9a2a82a-f8d4-4ec2-b8c1-be6cda3f993a
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e3707726eb9e8e77e0536f36700fe098d83ad414
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="use-binding-files-to-import-or-export"></a><span data-ttu-id="25627-102">Utiliser des fichiers de liaison pour importer ou exporter</span><span class="sxs-lookup"><span data-stu-id="25627-102">Use binding files to import or export</span></span>

<span data-ttu-id="25627-103">En commençant par [!INCLUDE[bts2016_md](../includes/bts2016-md.md)], vous pouvez exporter et importer des fichiers de liaison à la **Parties** et **accord** niveaux.</span><span class="sxs-lookup"><span data-stu-id="25627-103">Starting with [!INCLUDE[bts2016_md](../includes/bts2016-md.md)], you can export and import binding files at the **Parties** and **Agreement** levels.</span></span> <span data-ttu-id="25627-104">Pour les versions précédentes de BizTalk, vous exportez au niveau de l’application, comme décrit dans :</span><span class="sxs-lookup"><span data-stu-id="25627-104">For previous BizTalk versions, you export at the application level, as described at:</span></span> 

* [<span data-ttu-id="25627-105">Comment exporter des liaisons pour une Solution EDI AS2</span><span class="sxs-lookup"><span data-stu-id="25627-105">How to Export Bindings for an EDI-AS2 Solution</span></span>](../core/how-to-export-bindings-for-an-edi-as2-solution.md)
* [<span data-ttu-id="25627-106">Comment importer des liaisons pour une Solution EDI-AS2</span><span class="sxs-lookup"><span data-stu-id="25627-106">How to Import Bindings for an EDI-AS2 Solution</span></span>](../core/how-to-import-bindings-for-an-edi-as2-solution.md)

<span data-ttu-id="25627-107">Cette rubrique vous montre comment importer et exporte les parties, leurs profils, accords, les paramètres de secours et à l’aide de plusieurs [!INCLUDE[btsBizTalkServerAdminConsoleui_md](../includes/btsbiztalkserveradminconsoleui-md.md)] et BTSTask.</span><span class="sxs-lookup"><span data-stu-id="25627-107">This topic shows you how to import and exports parties, their profiles, agreements, fallback settings, and more using [!INCLUDE[btsBizTalkServerAdminConsoleui_md](../includes/btsbiztalkserveradminconsoleui-md.md)] and BTSTask.</span></span> 

## <a name="overview"></a><span data-ttu-id="25627-108">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="25627-108">Overview</span></span>

<span data-ttu-id="25627-109">Voici quelques-unes des fonctionnalités d’importation et d’exportation :</span><span class="sxs-lookup"><span data-stu-id="25627-109">Some of the import and export features include:</span></span>

* <span data-ttu-id="25627-110">Importer des tiers, des profils d’entreprise et des accords à partir d’un fichier de liaison XML</span><span class="sxs-lookup"><span data-stu-id="25627-110">Import parties, business profiles, and agreements from an XML binding file</span></span>
* <span data-ttu-id="25627-111">Exporter les tiers, profils d’entreprise, des contrats et les paramètres de secours EDI dans un fichier de liaison XML</span><span class="sxs-lookup"><span data-stu-id="25627-111">Export parties, business profiles, agreements, and EDI fallback settings to an XML binding file</span></span>
* <span data-ttu-id="25627-112">Lorsque vous importez un fichier de liaison, vous pouvez choisir n’importe ne pas les parties ou les paramètres de secours</span><span class="sxs-lookup"><span data-stu-id="25627-112">When importing a binding file, you can chose to not import the parties, or the fallback settings</span></span>
* <span data-ttu-id="25627-113">Lors de l’importation au niveau du tiers, uniquement les parties et les accords dans le fichier de liaison sont importées.</span><span class="sxs-lookup"><span data-stu-id="25627-113">When importing at the Parties-level, only the parties and agreements within the binding file are imported</span></span>
* <span data-ttu-id="25627-114">Exporter des tiers spécifiques dans le même fichier de liaison, puis choisissez d’exporter également tous les accords associés à ces parties</span><span class="sxs-lookup"><span data-stu-id="25627-114">Export specific parties to the same binding file, and choose to also export all the agreements associated with those parties</span></span>
* <span data-ttu-id="25627-115">L’Assistant Liaison importer l’application vous permet de choisir d’importer les paramètres de suivi ou exclure les parties.</span><span class="sxs-lookup"><span data-stu-id="25627-115">The application import binding wizard lets you choose to import the tracking settings, or exclude the parties.</span></span>
* <span data-ttu-id="25627-116">BTSTask inclut la `ImportParties` et `ExportParties` commandes</span><span class="sxs-lookup"><span data-stu-id="25627-116">BTSTask includes the `ImportParties` and `ExportParties` commands</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="25627-117">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="25627-117">Prerequisites</span></span>

* <span data-ttu-id="25627-118">Vous devez être connecté avec un compte qui est membre de la ** groupe Administrateurs de BizTalk Server **.</span><span class="sxs-lookup"><span data-stu-id="25627-118">You must be logged on with an account that is a member of the** BizTalk Server Administrators** group.</span></span> <span data-ttu-id="25627-119">Consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="25627-119">See [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  

* <span data-ttu-id="25627-120">Vous devez avoir ajouté une référence à la **Application EDI BizTalk** à partir d’une application BizTalk qui sera utilisée comme une application EDI.</span><span class="sxs-lookup"><span data-stu-id="25627-120">You must have added a reference to the **BizTalk EDI Application** from a BizTalk application that will be used as an EDI application.</span></span> <span data-ttu-id="25627-121">Consultez [post-configuration étapes](../install-and-config-guides/post-configuration-steps-to-optimize-your-environment.md).</span><span class="sxs-lookup"><span data-stu-id="25627-121">See [Post-configuration steps](../install-and-config-guides/post-configuration-steps-to-optimize-your-environment.md).</span></span>

## <a name="import-or-export-all-the-trading-partners"></a><span data-ttu-id="25627-122">Importer ou exporter tous les partenaires commerciaux</span><span class="sxs-lookup"><span data-stu-id="25627-122">Import or export all the trading partners</span></span>
1. <span data-ttu-id="25627-123">Ouvrez  **[!INCLUDE[btsBizTalkServerAdminConsoleui_md](../includes/btsbiztalkserveradminconsoleui-md.md)]** , développez le groupe BizTalk.</span><span class="sxs-lookup"><span data-stu-id="25627-123">Open **[!INCLUDE[btsBizTalkServerAdminConsoleui_md](../includes/btsbiztalkserveradminconsoleui-md.md)]**, and expand the BizTalk group.</span></span>
2. <span data-ttu-id="25627-124">Avec le bouton droit **Parties**, puis sélectionnez **exporter**.</span><span class="sxs-lookup"><span data-stu-id="25627-124">Right-click **Parties**, and select **Export**.</span></span> 

    <span data-ttu-id="25627-125">Lorsque vous exportez à la **parties**-niveau, vous exportez tous les partenaires commerciaux.</span><span class="sxs-lookup"><span data-stu-id="25627-125">When you export at the **parties**-level, you are exporting all the trading partners.</span></span> <span data-ttu-id="25627-126">Cette opération exporte également tous les éléments utilisés par les partenaires commerciaux, y compris les profils d’entreprise et des accords dans un fichier XML.</span><span class="sxs-lookup"><span data-stu-id="25627-126">This also exports everything used by the trading partners, including business profiles, and agreements into an XML file.</span></span> 

3. <span data-ttu-id="25627-127">Avec le bouton droit **Parties**, sélectionnez **importation**, puis sélectionnez le fichier XML de liaison.</span><span class="sxs-lookup"><span data-stu-id="25627-127">Right-click **Parties**, select **Import**, and select the binding XML file.</span></span> 

      <span data-ttu-id="25627-128">Choisissez de **exclure les Parties**, ou **exclure des paramètres de secours EDI** afin qu’ils ne sont pas importés.</span><span class="sxs-lookup"><span data-stu-id="25627-128">Choose to **Exclude Parties**, or **Exclude EDI Fallback Settings** so they are not imported.</span></span> <span data-ttu-id="25627-129">Dans le cas contraire, tous les éléments dans le fichier de liaison sont importé, y compris les partenaires, profils d’entreprise et des accords commerciaux.</span><span class="sxs-lookup"><span data-stu-id="25627-129">Otherwise, everything in the binding file is imported, including the trading partners, business profiles, and agreements.</span></span>     

### <a name="btstask-example"></a><span data-ttu-id="25627-130">Exemple de BTSTask</span><span class="sxs-lookup"><span data-stu-id="25627-130">BTSTask example</span></span>

`BTSTask ImportParties  -Source:"C:\Temp\MyParties.Xml" -ExcludeEdiFallbackSettings`

<span data-ttu-id="25627-131">Consultez [ImportParties commande](../core/importparties-command.md).</span><span class="sxs-lookup"><span data-stu-id="25627-131">See [ImportParties command](../core/importparties-command.md).</span></span>

    
## <a name="export-individual-partners"></a><span data-ttu-id="25627-132">Exporter des partenaires</span><span class="sxs-lookup"><span data-stu-id="25627-132">Export individual partners</span></span>
1. <span data-ttu-id="25627-133">Dans  **[!INCLUDE[btsBizTalkServerAdminConsoleui_md](../includes/btsbiztalkserveradminconsoleui-md.md)]** , sélectionnez **Parties**.</span><span class="sxs-lookup"><span data-stu-id="25627-133">In **[!INCLUDE[btsBizTalkServerAdminConsoleui_md](../includes/btsbiztalkserveradminconsoleui-md.md)]**, select **Parties**.</span></span>
2. <span data-ttu-id="25627-134">Dans le **tiers et profils d’entreprise** volet, avec le bouton droit à un tiers, puis sélectionnez **exporter**.</span><span class="sxs-lookup"><span data-stu-id="25627-134">In the **Parties and business profiles** pane, right-click a party, and select **Export**.</span></span>

    <span data-ttu-id="25627-135">Lorsque vous exportez un tiers spécifique, vous êtes proposé pour exporter toutes les parties et tous les contrats utilisés par ce tiers.</span><span class="sxs-lookup"><span data-stu-id="25627-135">When you export a specific party, you are given the choice to export all the parties, and all the agreements used by that party.</span></span> <span data-ttu-id="25627-136">Vous pouvez désactiver **exporter tiers sélectionnés et tous les contrats dans les parties sélectionnées** pour exporter uniquement la partie que vous sélectionnez.</span><span class="sxs-lookup"><span data-stu-id="25627-136">You can uncheck **Export selected parties and all the agreements within the selected parties** to only export the party you select.</span></span>

3. <span data-ttu-id="25627-137">Sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="25627-137">Select **OK**.</span></span> 

> [!TIP]
> <span data-ttu-id="25627-138">Dans le **tiers et profils d’entreprise** volet, vous pouvez également utiliser le **CTRL** et **MAJ** enfoncée pour sélectionner plusieurs parties dans la liste.</span><span class="sxs-lookup"><span data-stu-id="25627-138">In the **Parties and business profiles** pane, you can also use the **CTRL** and **Shift** keys to select multiple parties in the list.</span></span> <span data-ttu-id="25627-139">Tous les tiers que vous sélectionnez Exporter dans le même fichier de liaison.</span><span class="sxs-lookup"><span data-stu-id="25627-139">All of the parties you select export into the same binding file.</span></span>

### <a name="btstask-example"></a><span data-ttu-id="25627-140">Exemple de BTSTask</span><span class="sxs-lookup"><span data-stu-id="25627-140">BTSTask example</span></span>

`BTSTask ExportParties -Destination:"C:\Temp\MyParties.Xml"`

<span data-ttu-id="25627-141">Consultez [ExportParties commande](../core/exportparties-command.md).</span><span class="sxs-lookup"><span data-stu-id="25627-141">See [ExportParties command](../core/exportparties-command.md).</span></span>


## <a name="import-application-binding-file"></a><span data-ttu-id="25627-142">Fichier de liaison d’application importation</span><span class="sxs-lookup"><span data-stu-id="25627-142">Import application binding file</span></span>

<span data-ttu-id="25627-143">Au niveau de l’application, vous pouvez importer un fichier de liaison avec des tiers EDI et AS2.</span><span class="sxs-lookup"><span data-stu-id="25627-143">At the application-level, you can import a binding file with EDI and AS2 parties.</span></span> 

1. <span data-ttu-id="25627-144">Dans  **[!INCLUDE[btsBizTalkServerAdminConsoleui_md](../includes/btsbiztalkserveradminconsoleui-md.md)]** , développez **Applications**</span><span class="sxs-lookup"><span data-stu-id="25627-144">In **[!INCLUDE[btsBizTalkServerAdminConsoleui_md](../includes/btsbiztalkserveradminconsoleui-md.md)]**, expand **Applications**</span></span>
2. <span data-ttu-id="25627-145">Avec le bouton droit de votre application, puis sélectionnez **importation**.</span><span class="sxs-lookup"><span data-stu-id="25627-145">Right-click your application, and select **Import**.</span></span>
3. <span data-ttu-id="25627-146">**Importer des paramètres de suivi** et **exclure les Parties** options sont disponibles.</span><span class="sxs-lookup"><span data-stu-id="25627-146">**Import Tracking Settings** and **Exclude Parties** options are available.</span></span> <span data-ttu-id="25627-147">À l’aide de ces options, vous pouvez choisir Importer les paramètres de suivi existants ou exclure des parties EDI/AS2 dans le fichier de liaison.</span><span class="sxs-lookup"><span data-stu-id="25627-147">Using these options, you can choose to import any existing tracking settings, or exclude any EDI/AS2 parties within the binding file.</span></span>

    | <span data-ttu-id="25627-148">Paramètre</span><span class="sxs-lookup"><span data-stu-id="25627-148">Setting</span></span> | <span data-ttu-id="25627-149">Détails</span><span class="sxs-lookup"><span data-stu-id="25627-149">Details</span></span> |
    |---|---|
    |<span data-ttu-id="25627-150">**Importer les paramètres de suivi**</span><span class="sxs-lookup"><span data-stu-id="25627-150">**Import Tracking Settings**</span></span> | <span data-ttu-id="25627-151">Importe les paramètres de suivi activés sur les différents artefacts dans l’application, telles que le corps de message de suivi et suivre les événements.</span><span class="sxs-lookup"><span data-stu-id="25627-151">Imports the tracking settings enabled on the different artifacts within the application, such as track message bodies, and track events.</span></span> <br/><br/><span data-ttu-id="25627-152">Activé par défaut pour garantir la compatibilité descendante.</span><span class="sxs-lookup"><span data-stu-id="25627-152">Enabled by default to ensure backwards-compatibility.</span></span> |
    | <span data-ttu-id="25627-153">**Exclure les Parties**</span><span class="sxs-lookup"><span data-stu-id="25627-153">**Exclude Parties**</span></span>|<span data-ttu-id="25627-154">Effectue pas les parties d’importation, les profils et accords existants dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="25627-154">Does not import parties, profiles, and agreements that existing within the file.</span></span> <br/><br/><span data-ttu-id="25627-155">Cette option est désactivée par défaut pour garantir la compatibilité descendante.</span><span class="sxs-lookup"><span data-stu-id="25627-155">Disabled by default to ensure backwards-compatibility.</span></span>|

     > [!IMPORTANT] 
     > <span data-ttu-id="25627-156">Les paramètres de suivi global remplacent **importer les paramètres de suivi**.</span><span class="sxs-lookup"><span data-stu-id="25627-156">The global tracking settings override **Import Tracking Settings**.</span></span> <span data-ttu-id="25627-157">Par conséquent, si vous avez désactivé le suivi au niveau global de niveau, tout le suivi de paramètres ne sont pas importés, même si **importer les paramètres de suivi** est activée.</span><span class="sxs-lookup"><span data-stu-id="25627-157">So if you've disabled tracking at the global level, any tracking settings are not imported, even if **Import Tracking Settings** is checked.</span></span>
     > 
     > <span data-ttu-id="25627-158">**Panneau de configuration de BizTalk, Page groupe** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)] explique le **autoriser l’importation des paramètres de suivi** paramètre global.</span><span class="sxs-lookup"><span data-stu-id="25627-158">**BizTalk Settings Dashboard, Group Page** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)] explains the **Allow import of tracking settings** global setting.</span></span>

### <a name="btstask-example"></a><span data-ttu-id="25627-159">Exemple de BTSTask</span><span class="sxs-lookup"><span data-stu-id="25627-159">BTSTask example</span></span>

`BTSTask ImportBindings -ApplicationName:MyApplication -Source:C:\Bindings\Binding1.xml -ImportTrackingSettings:true`

<span data-ttu-id="25627-160">Consultez [commande ImportBindings](../core/importbindings-command.md).</span><span class="sxs-lookup"><span data-stu-id="25627-160">See [ImportBindings command](../core/importbindings-command.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="25627-161">Contenu de cette section</span><span class="sxs-lookup"><span data-stu-id="25627-161">In this section</span></span>
<span data-ttu-id="25627-162">Pour importer ou exporter des fichiers de liaison EDI et AS2 sur les versions précédentes de BizTalk, consultez :</span><span class="sxs-lookup"><span data-stu-id="25627-162">To import or export EDI and AS2 binding files on previous BizTalk versions, see:</span></span> 

* [<span data-ttu-id="25627-163">Comment exporter des liaisons pour une Solution EDI AS2</span><span class="sxs-lookup"><span data-stu-id="25627-163">How to Export Bindings for an EDI-AS2 Solution</span></span>](../core/how-to-export-bindings-for-an-edi-as2-solution.md)
* [<span data-ttu-id="25627-164">Comment importer des liaisons pour une Solution EDI-AS2</span><span class="sxs-lookup"><span data-stu-id="25627-164">How to Import Bindings for an EDI-AS2 Solution</span></span>](../core/how-to-import-bindings-for-an-edi-as2-solution.md)
