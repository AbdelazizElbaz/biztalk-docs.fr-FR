---
title: "Dans le Concepteur d’Orchestration | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestrations, saving
- deleting, orchestrations
- projects, orchestrations
- orchestrations, properties
- orchestrations, creating
- creating, orchestrations
- naming conventions, orchestrations
- orchestrations, naming conventions
- orchestrations, deleting
ms.assetid: 13e72b41-d9b6-4508-9a44-b3c7c1804f36
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 512dc85fb1599bdaa77fe2550390ec2ce6954643
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="working-in-orchestration-designer"></a><span data-ttu-id="04801-102">Utilisation du Concepteur d'orchestration</span><span class="sxs-lookup"><span data-stu-id="04801-102">Working in Orchestration Designer</span></span>
<span data-ttu-id="04801-103">Après avoir ouvert un projet BizTalk, vous pouvez créer de nouvelles orchestrations et ajouter des orchestrations existantes au projet.</span><span class="sxs-lookup"><span data-stu-id="04801-103">After you have started a BizTalk project, you can create new orchestrations and add existing orchestrations to the project.</span></span> <span data-ttu-id="04801-104">Les procédures suivantes vous expliquent comment créer et enregistrer une orchestration, ajouter une orchestration existante à un projet ou en supprimer une, modifier le nom d'une orchestration et définir les propriétés d'une orchestration.</span><span class="sxs-lookup"><span data-stu-id="04801-104">See the following procedures to create and save an orchestration, to add an existing orchestration to a project or remove one from it, to change the name of an orchestration, and to set orchestration properties.</span></span>  
  
### <a name="to-create-an-orchestration"></a><span data-ttu-id="04801-105">Pour créer une orchestration</span><span class="sxs-lookup"><span data-stu-id="04801-105">To create an orchestration</span></span>  
  
1.  <span data-ttu-id="04801-106">Dans l’Explorateur de solutions, cliquez sur le nom du projet, sélectionnez **ajouter**, puis cliquez sur **un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="04801-106">In Solution Explorer, right-click the project name, select **Add**, and then click **New Item**.</span></span>  
  
2.  <span data-ttu-id="04801-107">Dans le **ajouter un nouvel élément** boîte de dialogue le **catégories** volet, cliquez sur **des éléments de projet BizTalk**, puis, dans le **modèles** volet, cliquez sur **Orchestration BizTalk**.</span><span class="sxs-lookup"><span data-stu-id="04801-107">In the **Add New Item** dialog box, in the **Categories** pane, click **BizTalk Project Items**, and then in the **Templates** pane, click **BizTalk Orchestration**.</span></span>  
  
3.  <span data-ttu-id="04801-108">Dans le **nom** zone située au bas de la boîte de dialogue, fournissez un nom pour l’orchestration, puis cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="04801-108">In the **Name** box at the bottom of the dialog box, supply a name for the orchestration, and then click **Add**.</span></span>  
  
     <span data-ttu-id="04801-109">La nouvelle orchestration est créée et s'affiche dans le Concepteur d'orchestration, et un fichier .odx correspondant est créé et affiché dans l'Explorateur de solutions.</span><span class="sxs-lookup"><span data-stu-id="04801-109">The new orchestration is created and displayed in Orchestration Designer, and a corresponding .odx file is created and displayed in Solution Explorer.</span></span>  
  
### <a name="to-add-an-existing-orchestration-to-a-project"></a><span data-ttu-id="04801-110">Pour ajouter une orchestration existante à un projet</span><span class="sxs-lookup"><span data-stu-id="04801-110">To add an existing orchestration to a project</span></span>  
  
1.  <span data-ttu-id="04801-111">Dans l’Explorateur de solutions, cliquez sur le nom du projet, cliquez sur **ajouter**, puis cliquez sur **élément existant**.</span><span class="sxs-lookup"><span data-stu-id="04801-111">In Solution Explorer, right-click the project name, click **Add**, and then click **Existing Item**.</span></span>  
  
2.  <span data-ttu-id="04801-112">Dans le **ajouter un élément existant** boîte de dialogue, accédez au répertoire contenant l’orchestration, sélectionnez l’orchestration, puis cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="04801-112">In the **Add Existing Item** dialog box, navigate to the directory containing the orchestration, select the orchestration, and then click **Add**.</span></span>  
  
     <span data-ttu-id="04801-113">L'orchestration est ajoutée au projet.</span><span class="sxs-lookup"><span data-stu-id="04801-113">The orchestration is added to the project.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="04801-114">Lorsque vous ajoutez un fichier existant, le fichier est copié vers votre projet</span><span class="sxs-lookup"><span data-stu-id="04801-114">When you add an existing file, the file is copied to your project.</span></span> <span data-ttu-id="04801-115">(il n'est pas simplement ajouté par référence). Si vous modifiez le fichier dans votre projet, le fichier original reste en l'état.</span><span class="sxs-lookup"><span data-stu-id="04801-115">(The file is not simply added by reference.) If you change the file in your project, the original file is left unchanged.</span></span>  
  
### <a name="to-change-the-name-of-an-orchestration"></a><span data-ttu-id="04801-116">Pour modifier le nom d'une orchestration</span><span class="sxs-lookup"><span data-stu-id="04801-116">To change the name of an orchestration</span></span>  
  
1.  <span data-ttu-id="04801-117">Dans l’Explorateur de solutions, cliquez sur le fichier .odx que vous souhaitez modifier, puis cliquez sur **renommer**.</span><span class="sxs-lookup"><span data-stu-id="04801-117">In Solution Explorer, right-click the .odx file you want to change, and then click **Rename**.</span></span>  
  
2.  <span data-ttu-id="04801-118">Tapez le nouveau nom de fichier de votre choix, puis appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="04801-118">Type the new file name you want, and then press ENTER.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="04801-119">Lorsque vous modifiez le nom d’un fichier .odx, vous pouvez également modifier le nom du type d’orchestration en cliquant sur l’aire de conception pour afficher la fenêtre Propriétés et modifiez la valeur de la **Typename** propriété de la orchestration.</span><span class="sxs-lookup"><span data-stu-id="04801-119">When you change the name of an .odx file, you might also want to change the name of the orchestration type by clicking on the design surface to bring up the Properties window and changing the value of the **Typename** property of the orchestration.</span></span>  
  
### <a name="to-save-an-orchestration"></a><span data-ttu-id="04801-120">Pour enregistrer une orchestration</span><span class="sxs-lookup"><span data-stu-id="04801-120">To save an orchestration</span></span>  
  
-   <span data-ttu-id="04801-121">Sur le **fichier** menu, cliquez sur **enregistrer \<nom de l’orchestration >**.</span><span class="sxs-lookup"><span data-stu-id="04801-121">On the **File** menu, click **Save \<orchestration name>**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="04801-122">Fichiers d’orchestration sont enregistrées au format UTF-8.</span><span class="sxs-lookup"><span data-stu-id="04801-122">Orchestration files are saved as UTF-8.</span></span>  <span data-ttu-id="04801-123">Schémas, mappages et pipelines sont enregistrés au format UTF-16.</span><span class="sxs-lookup"><span data-stu-id="04801-123">Schemas, maps, and pipelines are saved as UTF-16.</span></span>  
  
### <a name="to-remove-an-orchestration-from-a-project"></a><span data-ttu-id="04801-124">Pour supprimer une orchestration d'un projet</span><span class="sxs-lookup"><span data-stu-id="04801-124">To remove an orchestration from a project</span></span>  
  
-   <span data-ttu-id="04801-125">Dans l’Explorateur de solutions, cliquez sur le fichier que vous souhaitez supprimer, puis cliquez sur **exclure du projet**.</span><span class="sxs-lookup"><span data-stu-id="04801-125">In Solution Explorer, right-click the file you want to remove, and then click **Exclude From Project**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="04801-126">Pour supprimer l’orchestration d’un projet et supprimer définitivement le fichier, cliquez sur **supprimer** à la place.</span><span class="sxs-lookup"><span data-stu-id="04801-126">To remove the orchestration from a project and permanently delete the file, click **Delete** instead.</span></span>  
  
### <a name="to-include-an-excluded-orchestration-in-a-project"></a><span data-ttu-id="04801-127">Pour inclure une orchestration exclue dans un projet</span><span class="sxs-lookup"><span data-stu-id="04801-127">To include an excluded orchestration in a project</span></span>  
  
-   <span data-ttu-id="04801-128">Dans l’Explorateur de solutions, cliquez sur le **afficher tout** bouton de barre d’outils, le fichier .odx de clic droit et sélectionnez **inclure dans le projet**.</span><span class="sxs-lookup"><span data-stu-id="04801-128">In Solution Explorer, click the **Show All** toolbar button, right-click the .odx file you want, and select **Include in Project**.</span></span>  
  
### <a name="to-set-orchestration-properties"></a><span data-ttu-id="04801-129">Pour définir les propriétés de l'orchestration</span><span class="sxs-lookup"><span data-stu-id="04801-129">To set orchestration properties</span></span>  
  
1.  <span data-ttu-id="04801-130">Ouvrez l'orchestration en double-cliquant sur le fichier.odx du projet, ou en sélectionnant l'onglet contenant l'orchestration dans la zone de processus.</span><span class="sxs-lookup"><span data-stu-id="04801-130">Open the orchestration by double-clicking on the .odx file in the project, or by selecting the tab containing the orchestration in the Process Area.</span></span>  
  
2.  <span data-ttu-id="04801-131">Dans la fenêtre Vue Orchestration, sélectionnez **propriétés d’Orchestration**.</span><span class="sxs-lookup"><span data-stu-id="04801-131">In the Orchestration View window, select **Orchestration Properties**.</span></span>  
  
     <span data-ttu-id="04801-132">— Ou :</span><span class="sxs-lookup"><span data-stu-id="04801-132">—Or—</span></span>  
  
     <span data-ttu-id="04801-133">Cliquez sur le **zone de processus** en arrière-plan de l’aire de conception d’Orchestration.</span><span class="sxs-lookup"><span data-stu-id="04801-133">Click the **Process Area** background of the Orchestration Design Surface.</span></span>  
  
3.  <span data-ttu-id="04801-134">Dans la fenêtre Propriétés, définissez les propriétés suivantes.</span><span class="sxs-lookup"><span data-stu-id="04801-134">In the Properties window, specify the following properties.</span></span> <span data-ttu-id="04801-135">Notez que certaines propriétés n'apparaissent que dans certaines circonstances.</span><span class="sxs-lookup"><span data-stu-id="04801-135">Note that some properties appear only under certain circumstances.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="04801-136">Les noms des orchestrations, des types de ports et des types de messages à parties multiples doivent être uniques dans toute l'étendue d'un module.</span><span class="sxs-lookup"><span data-stu-id="04801-136">The names of orchestrations, port types and multi-part message types must be unique within the scope of a module.</span></span>  
  
    |<span data-ttu-id="04801-137">Propriété</span><span class="sxs-lookup"><span data-stu-id="04801-137">Property</span></span>|<span data-ttu-id="04801-138"> Description</span><span class="sxs-lookup"><span data-stu-id="04801-138">Description</span></span>|  
    |--------------|-----------------|  
    |<span data-ttu-id="04801-139">Traitement</span><span class="sxs-lookup"><span data-stu-id="04801-139">Batch</span></span>|<span data-ttu-id="04801-140">Détermine si une orchestration de transaction atomique peut être mise en lot avec d'autres instances.</span><span class="sxs-lookup"><span data-stu-id="04801-140">Determines whether an orchestration that is an atomic transaction can be batched with other instances.</span></span>|  
    |<span data-ttu-id="04801-141">Compensation</span><span class="sxs-lookup"><span data-stu-id="04801-141">Compensation</span></span>|<span data-ttu-id="04801-142">Indique le type de compensation à effectuer dans l'orchestration.</span><span class="sxs-lookup"><span data-stu-id="04801-142">Specifies what type of compensation to perform on the orchestration.</span></span>|  
    |<span data-ttu-id="04801-143">Niveau d'isolement</span><span class="sxs-lookup"><span data-stu-id="04801-143">Isolation Level</span></span>|<span data-ttu-id="04801-144">Pour les orchestrations transactionnelles, détermine le niveau auquel les données sont accessibles parmi les transactions simultanées.</span><span class="sxs-lookup"><span data-stu-id="04801-144">For transactional orchestrations, determines the degree to which data is accessible among concurrent transactions.</span></span>|  
    |<span data-ttu-id="04801-145">Module Exportable</span><span class="sxs-lookup"><span data-stu-id="04801-145">Module Exportable</span></span>|<span data-ttu-id="04801-146">Détermine si le module peut être exporté ou non vers BPEL4WS.</span><span class="sxs-lookup"><span data-stu-id="04801-146">Determines whether or not the module can be exported to BPEL4WS.</span></span>|  
    |<span data-ttu-id="04801-147">Espace de noms cible XML du module</span><span class="sxs-lookup"><span data-stu-id="04801-147">Module XML Target Namespace</span></span>|<span data-ttu-id="04801-148">Espace de noms cible XML utilisé pour l'exportation des types vers BPEL4WS.</span><span class="sxs-lookup"><span data-stu-id="04801-148">The XML target namespace used when exporting types to BPEL4WS.</span></span>|  
    |<span data-ttu-id="04801-149">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="04801-149">Namespace</span></span>|<span data-ttu-id="04801-150">Détermine le nom du module contenant qui inclut l'orchestration et les types d'orchestrations.</span><span class="sxs-lookup"><span data-stu-id="04801-150">Determines the name of the containing module that includes the orchestration and the orchestration types.</span></span>|  
    |<span data-ttu-id="04801-151">Orchestration exportable</span><span class="sxs-lookup"><span data-stu-id="04801-151">Orchestration Exportable</span></span>|<span data-ttu-id="04801-152">Indique si cette orchestration est censée être exportable ou non vers BPEL4WS.</span><span class="sxs-lookup"><span data-stu-id="04801-152">Indicates whether this orchestration is intended to be exportable to BPEL4WS.</span></span>|  
    |<span data-ttu-id="04801-153">Espace de noms cible de l'orchestration XML</span><span class="sxs-lookup"><span data-stu-id="04801-153">Orchestration XML Target Namespace</span></span>|<span data-ttu-id="04801-154">Espace de noms cible XML utilisé pour l'exportation de cette orchestration vers BPEL4WS.</span><span class="sxs-lookup"><span data-stu-id="04801-154">The XML target namespace used when exporting this orchestration to BPEL4WS.</span></span>|  
    |<span data-ttu-id="04801-155">Réessayer</span><span class="sxs-lookup"><span data-stu-id="04801-155">Retry</span></span>|<span data-ttu-id="04801-156">Indique s'il faut retenter une orchestration transactionnelle en cas d'échec.</span><span class="sxs-lookup"><span data-stu-id="04801-156">Specify whether to retry a transactional orchestration if it fails.</span></span>|  
    |<span data-ttu-id="04801-157">Délai d'expiration</span><span class="sxs-lookup"><span data-stu-id="04801-157">Timeout</span></span>|<span data-ttu-id="04801-158">Délai en secondes après lequel une orchestration transactionnelle est considérée comme ayant échoué pour cause d'inactivité.</span><span class="sxs-lookup"><span data-stu-id="04801-158">The time in seconds until a transactional orchestration fails due to inactivity.</span></span>|  
    |<span data-ttu-id="04801-159">Identificateur de la transaction</span><span class="sxs-lookup"><span data-stu-id="04801-159">Transaction Identifier</span></span>|<span data-ttu-id="04801-160">Identificateur unique d'une orchestration transactionnelle.</span><span class="sxs-lookup"><span data-stu-id="04801-160">Unique identifier for a transactional orchestration.</span></span>|  
    |<span data-ttu-id="04801-161">Type de transaction</span><span class="sxs-lookup"><span data-stu-id="04801-161">Transaction Type</span></span>|<span data-ttu-id="04801-162">Indique si l'orchestration est une transaction atomique, une transaction longue ou si elle n'est pas traitée.</span><span class="sxs-lookup"><span data-stu-id="04801-162">Determines whether the orchestration is an atomic transaction, a long-running transaction, or is not transacted.</span></span>|  
    |<span data-ttu-id="04801-163">Modificateur de type</span><span class="sxs-lookup"><span data-stu-id="04801-163">Type Modifier</span></span>|<span data-ttu-id="04801-164">Détermine l'étendue des variables au niveau de l'orchestration.</span><span class="sxs-lookup"><span data-stu-id="04801-164">Determines the scope of orchestration-level variables:</span></span><br /><br /> <span data-ttu-id="04801-165">Privé : l'accès à cette orchestration est limité au module contenant.</span><span class="sxs-lookup"><span data-stu-id="04801-165">Private—Access to this orchestration is limited to the containing module.</span></span><br /><br /> <span data-ttu-id="04801-166">Public : l'accès à cette orchestration n'est pas limité.</span><span class="sxs-lookup"><span data-stu-id="04801-166">Public—Access to this orchestration is not limited.</span></span><br /><br /> <span data-ttu-id="04801-167">Interne : l'accès à cette orchestration est limité aux modules d'un même projet.</span><span class="sxs-lookup"><span data-stu-id="04801-167">Internal—Access to this orchestration is limited to modules within the same project.</span></span>|  
    |<span data-ttu-id="04801-168">Nom du type</span><span class="sxs-lookup"><span data-stu-id="04801-168">Typename</span></span>|<span data-ttu-id="04801-169">Détermine le nom de cette orchestration dans le module contenant.</span><span class="sxs-lookup"><span data-stu-id="04801-169">Determines the name of this orchestration within the containing module.</span></span> <span data-ttu-id="04801-170">**Remarque :** si vous permet d’utiliser un nom de type qui est identique à un espace de noms racine, vous pouvez recevoir une erreur à partir du Concepteur d’Orchestration lorsque vous définissez des messages et affecter des variables basées sur le Typename et tentez d’effectuer des opérations sur les.</span><span class="sxs-lookup"><span data-stu-id="04801-170">**Note:**  If you to use a Typename that is the same as a root-level namespace, you may receive an error from Orchestration Designer when you define messages and variables based on the Typename and attempt to perform assign operations on them.</span></span> <span data-ttu-id="04801-171">Par exemple, si vous choisissez le nom de type System, puis définissez des messages et des variables en tant que System.String, une erreur risque de se produire.</span><span class="sxs-lookup"><span data-stu-id="04801-171">For example, if you specify a Typename of System, and then define messages and variables like System.String, you may receive an error.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="04801-172">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="04801-172">See Also</span></span>  
 <span data-ttu-id="04801-173">[Formes d’orchestration](../core/orchestration-shapes.md) </span><span class="sxs-lookup"><span data-stu-id="04801-173">[Orchestration Shapes](../core/orchestration-shapes.md) </span></span>  
 <span data-ttu-id="04801-174">[Comment ajouter des formes aux Orchestrations](../core/how-to-add-shapes-to-orchestrations.md) </span><span class="sxs-lookup"><span data-stu-id="04801-174">[How to Add Shapes to Orchestrations](../core/how-to-add-shapes-to-orchestrations.md) </span></span>  
 <span data-ttu-id="04801-175">[Comment ajouter des paramètres aux Orchestrations](../core/how-to-add-parameters-to-orchestrations.md) </span><span class="sxs-lookup"><span data-stu-id="04801-175">[How to Add Parameters to Orchestrations](../core/how-to-add-parameters-to-orchestrations.md) </span></span>  
 [<span data-ttu-id="04801-176">Comment utiliser le Type de boîte de dialogue Sélectionnez artefact</span><span class="sxs-lookup"><span data-stu-id="04801-176">How to Use the Select Artifact Type Dialog Box</span></span>](../core/how-to-use-the-select-artifact-type-dialog-box.md)