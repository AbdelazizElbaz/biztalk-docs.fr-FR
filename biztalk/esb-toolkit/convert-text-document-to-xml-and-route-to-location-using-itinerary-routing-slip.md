---
title: "Comment : convertir un Document texte XML et d’itinéraire vers un emplacement de fichier à l’aide d’une feuille de route bordereau | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 01597a5f-5ca3-440e-ad97-70332233f319
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0ba308473568c222559ccc799faf3233478ee490
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-convert-a-text-document-to-xml-and-route-to-a-file-location-using-an-itinerary-routing-slip"></a><span data-ttu-id="f9ff0-102">Comment : convertir un Document texte XML et d’itinéraire vers un emplacement de fichier à l’aide d’un bon d’itinéraire de routage</span><span class="sxs-lookup"><span data-stu-id="f9ff0-102">How to: Convert a Text Document to XML and Route to a File Location Using an Itinerary Routing Slip</span></span>
## <a name="goal"></a><span data-ttu-id="f9ff0-103">Objectif</span><span class="sxs-lookup"><span data-stu-id="f9ff0-103">Goal</span></span>  
 <span data-ttu-id="f9ff0-104">La section explique comment créer un pipeline qui sera convertir un document texte XML puis sélectionnez la feuille de route appropriée et acheminer le message vers un emplacement de fichier.</span><span class="sxs-lookup"><span data-stu-id="f9ff0-104">The section demonstrates how to create a pipeline that will convert a text document to XML and then select the appropriate itinerary and route the message to a FILE location.</span></span>  
  
 <span data-ttu-id="f9ff0-105">Dans cette rubrique, vous effectuerez les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="f9ff0-105">In this How-to topic, you will complete the following steps:</span></span>  
  
-   <span data-ttu-id="f9ff0-106">Utilisez un pipeline pour recevoir un document de fichier plat et la convertir en XML.</span><span class="sxs-lookup"><span data-stu-id="f9ff0-106">Use a pipeline to receive a flat file document and convert it to XML.</span></span>  
  
-   <span data-ttu-id="f9ff0-107">Configurer le composant de pipeline de sélecteur de feuille de route pour résoudre le bordereau de routage approprié.</span><span class="sxs-lookup"><span data-stu-id="f9ff0-107">Configure the Itinerary Selector pipeline component to resolve the appropriate routing slip.</span></span>  
  
-   <span data-ttu-id="f9ff0-108">Créer une rampe d’entrée qui utilise le pipeline personnalisé.</span><span class="sxs-lookup"><span data-stu-id="f9ff0-108">Create an on-ramp that uses the custom pipeline.</span></span>  
  
-   <span data-ttu-id="f9ff0-109">Testez le routage basé sur l’itinéraire d’un message de fichier plat.</span><span class="sxs-lookup"><span data-stu-id="f9ff0-109">Test itinerary-based routing of a flat file message.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="f9ff0-110">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="f9ff0-110">Prerequisites</span></span>  
 <span data-ttu-id="f9ff0-111">Les procédures de cette rubrique requièrent l’achèvement de la [conditions préalables pour les activités de développement](../esb-toolkit/prerequisites-for-the-development-activities.md).</span><span class="sxs-lookup"><span data-stu-id="f9ff0-111">The procedures in this How-to topic require the completion of the [Prerequisites for the Development Activities](../esb-toolkit/prerequisites-for-the-development-activities.md).</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="f9ff0-112">Avant de commencer</span><span class="sxs-lookup"><span data-stu-id="f9ff0-112">Before You Begin</span></span>  
 <span data-ttu-id="f9ff0-113">Effectuez les tâches suivantes avant d’effectuer les étapes plus loin dans cette rubrique :</span><span class="sxs-lookup"><span data-stu-id="f9ff0-113">Complete the following tasks before you perform the steps later in this How-to topic:</span></span>  
  
-   <span data-ttu-id="f9ff0-114">Déployer le **DataFormatTransformation** itinéraire.</span><span class="sxs-lookup"><span data-stu-id="f9ff0-114">Deploy the **DataFormatTransformation** itinerary.</span></span>  
  
-   <span data-ttu-id="f9ff0-115">Créer le message de test.</span><span class="sxs-lookup"><span data-stu-id="f9ff0-115">Create the test message.</span></span>  
  
 <span data-ttu-id="f9ff0-116">Les procédures suivantes décrivent comment effectuer chacune d’elles.</span><span class="sxs-lookup"><span data-stu-id="f9ff0-116">The following procedures describe how to do each of these.</span></span>  
  
#### <a name="to-deploy-the-dataformattransformation-itinerary"></a><span data-ttu-id="f9ff0-117">Pour déployer l’itinéraire DataFormatTransformation</span><span class="sxs-lookup"><span data-stu-id="f9ff0-117">To deploy the DataFormatTransformation itinerary</span></span>  
  
1.  <span data-ttu-id="f9ff0-118">Dans [!INCLUDE[vs2010](../includes/vs2010-md.md)], ouvrez C:\Projects\Microsoft.Practices.ESB\Source\Samples\DataFormatTransformation\DataFormatTransformation.sln.</span><span class="sxs-lookup"><span data-stu-id="f9ff0-118">In [!INCLUDE[vs2010](../includes/vs2010-md.md)], open C:\Projects\Microsoft.Practices.ESB\Source\Samples\DataFormatTransformation\DataFormatTransformation.sln.</span></span>  
  
2.  <span data-ttu-id="f9ff0-119">Dans l’Explorateur de solutions, dans le **Itinerary.Library** de projet, double-cliquez sur **DataFormatTransformation.itinerary** pour l’ouvrir dans le Concepteur d’itinéraire.</span><span class="sxs-lookup"><span data-stu-id="f9ff0-119">In Solution Explorer, in the **Itinerary.Library** project, double-click **DataFormatTransformation.itinerary** to open it in the Itinerary Designer.</span></span>  
  
3.  <span data-ttu-id="f9ff0-120">Dans Visual Studio, cliquez sur l’aire de conception de **DataFormatTransformation.itinerary**.</span><span class="sxs-lookup"><span data-stu-id="f9ff0-120">In Visual Studio, click the design surface of **DataFormatTransformation.itinerary**.</span></span> <span data-ttu-id="f9ff0-121">Dans le **DataFormatTransformation.itinerary** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="f9ff0-121">In the **DataFormatTransformation.itinerary** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="f9ff0-122">Dans le **état de la feuille de route** la liste déroulante, cliquez sur **déployées**.</span><span class="sxs-lookup"><span data-stu-id="f9ff0-122">In the **Itinerary Status** drop-down list, click **Deployed**.</span></span>  
  
    2.  <span data-ttu-id="f9ff0-123">Dans le **modèle exportateur** la liste déroulante, cliquez sur **exportateur de feuille de route de base de données**.</span><span class="sxs-lookup"><span data-stu-id="f9ff0-123">In the **Model Exporter** drop-down list, click **Database Itinerary Exporter**.</span></span>  
  
    3.  <span data-ttu-id="f9ff0-124">Cliquez sur le bouton de sélection (...) à côté du **base de données de la feuille de route** propriété.</span><span class="sxs-lookup"><span data-stu-id="f9ff0-124">Click the ellipsis button (...) next to the **Itinerary Database** property.</span></span>  
  
    4.  <span data-ttu-id="f9ff0-125">Dans le **propriétés de connexion** boîte de dialogue, choisissez le serveur SQL qui héberge la base de données de référentiel d’itinéraire, puis spécifiez le nom de la base de données (le nom par défaut est **EsbItineraryDb**).</span><span class="sxs-lookup"><span data-stu-id="f9ff0-125">In the **Connection Properties** dialog box, choose the SQL Server that hosts the itinerary repository database, and then specify the name of the database (the default name is **EsbItineraryDb**).</span></span>  
  
4.  <span data-ttu-id="f9ff0-126">Enregistrez tous les artefacts de projet.</span><span class="sxs-lookup"><span data-stu-id="f9ff0-126">Save all project artifacts.</span></span>  
  
5.  <span data-ttu-id="f9ff0-127">Dans Visual Studio, cliquez sur l’aire de conception de la **DataModelTransformation** itinéraire, puis cliquez sur **exporter le modèle**.</span><span class="sxs-lookup"><span data-stu-id="f9ff0-127">In Visual Studio, right-click the design surface of the **DataModelTransformation** itinerary, and then click **Export Model**.</span></span>  
  
#### <a name="to-create-the-receive-pipeline"></a><span data-ttu-id="f9ff0-128">Pour créer le pipeline de réception</span><span class="sxs-lookup"><span data-stu-id="f9ff0-128">To create the receive pipeline</span></span>  
  
1.  <span data-ttu-id="f9ff0-129">Dans Visual Studio, cliquez sur **DataFormatTransformation.Schemas**, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="f9ff0-129">In Visual Studio, right-click **DataFormatTransformation.Schemas**, and then click **Properties**.</span></span> <span data-ttu-id="f9ff0-130">Cliquez sur **Application**, puis tapez **GlobalBank.ESB.DataFormatTransformation.Schemas** dans les **nom de l’Assembly** boîte.</span><span class="sxs-lookup"><span data-stu-id="f9ff0-130">Click **Application**, and then type **GlobalBank.ESB.DataFormatTransformation.Schemas** in the **Assembly name** box.</span></span>  
  
2.  <span data-ttu-id="f9ff0-131">Avec le bouton droit **DataFormatTransformation.Schemas**, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="f9ff0-131">Right-click **DataFormatTransformation.Schemas**, and then click **Properties**.</span></span> <span data-ttu-id="f9ff0-132">Cliquez sur **signature**, puis vérifiez que le **signer l’assembly** case à cocher est activée et que l’emplacement de l’assembly pointe vers **.\\... \\.. \\.. \\.. \\.. \keys\Microsoft.Practices.ESB.snk**.</span><span class="sxs-lookup"><span data-stu-id="f9ff0-132">Click **Signing**, and then verify that the **Sign the assembly** check box is selected and that the assembly location points to **.\\..\\..\\..\\..\\..\keys\Microsoft.Practices.ESB.snk**.</span></span>  
  
3.  <span data-ttu-id="f9ff0-133">Avec le bouton droit **DataFormatTransformation.Pipelines**, puis cliquez sur **supprimer**.</span><span class="sxs-lookup"><span data-stu-id="f9ff0-133">Right-click **DataFormatTransformation.Pipelines**, and then click **Remove**.</span></span>  
  
4.  <span data-ttu-id="f9ff0-134">Avec le bouton droit **DataFormatTransformation**, pointez sur **ajouter**, puis cliquez sur **nouveau projet**.</span><span class="sxs-lookup"><span data-stu-id="f9ff0-134">Right-click **DataFormatTransformation**, point to **Add**, and then click **New Project**.</span></span> <span data-ttu-id="f9ff0-135">Cliquez sur **projets Biztalk**, puis cliquez sur **projet Biztalk Server vide**.</span><span class="sxs-lookup"><span data-stu-id="f9ff0-135">Click **Biztalk Projects**, and then click **Empty Biztalk Server Project**.</span></span> <span data-ttu-id="f9ff0-136">Dans le **nom** , tapez **DataFormatTransformationReceive.Pipeline**.</span><span class="sxs-lookup"><span data-stu-id="f9ff0-136">In the **Name** box, type **DataFormatTransformationReceive.Pipeline**.</span></span>  
  
5.  <span data-ttu-id="f9ff0-137">Avec le bouton droit **DataFormatTransformationReceive.Pipeline**, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="f9ff0-137">Right-click **DataFormatTransformationReceive.Pipeline**, and then click **Properties**.</span></span> <span data-ttu-id="f9ff0-138">Cliquez sur **signature**, puis vérifiez que le **signer l’assembly** case à cocher est activée et que l’emplacement de l’assembly pointe vers **C:\projects\Microsoft.Practices.ESB\keys\ Microsoft.Practices.ESB.snk**.</span><span class="sxs-lookup"><span data-stu-id="f9ff0-138">Click **Signing**, and then verify that the **Sign the assembly** check box is selected and that the assembly location points to **C:\projects\Microsoft.Practices.ESB\keys\Microsoft.Practices.ESB.snk**.</span></span>  
  
6.  <span data-ttu-id="f9ff0-139">Avec le bouton droit **DataFormatTransformationReceive.Pipeline**, pointez sur **ajouter**, puis cliquez sur **un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="f9ff0-139">Right-click **DataFormatTransformationReceive.Pipeline**, point to **Add**, and then click **New Item**.</span></span>  
  
7.  <span data-ttu-id="f9ff0-140">Dans le **ajouter un nouvel élément** boîte de dialogue, cliquez sur **Pipeline de réception** dans le volet Modèles.</span><span class="sxs-lookup"><span data-stu-id="f9ff0-140">In the **Add New Item** dialog box, click **Receive Pipeline** in the Templates pane.</span></span> <span data-ttu-id="f9ff0-141">Dans le **nom** , tapez **ItinerarySelectReceiveFF**, puis cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="f9ff0-141">In the **Name** box, type **ItinerarySelectReceiveFF**, and then click **Add**.</span></span>  
  
8.  <span data-ttu-id="f9ff0-142">Avec le bouton droit **références** pour le projet de DataFormatTransformationReceive.Pipeline, puis cliquez sur **ajouter une référence**.</span><span class="sxs-lookup"><span data-stu-id="f9ff0-142">Right-click **References** for the DataFormatTransformationReceive.Pipeline project, and then click **Add Reference**.</span></span> <span data-ttu-id="f9ff0-143">Cliquez sur le **projets** onglet, puis cliquez sur **DataFormatTransformation.Schemas**.</span><span class="sxs-lookup"><span data-stu-id="f9ff0-143">Click the **Projects** tab, and then click **DataFormatTransformation.Schemas**.</span></span> <span data-ttu-id="f9ff0-144">Cliquez sur **OK** pour ajouter la référence.</span><span class="sxs-lookup"><span data-stu-id="f9ff0-144">Click **OK** to add the reference.</span></span>  
  
9. <span data-ttu-id="f9ff0-145">Dans la boîte à outils, faites glisser un **désassembleur de fichier plat** composant de pipeline pour le **désassembler** étape du pipeline.</span><span class="sxs-lookup"><span data-stu-id="f9ff0-145">From the Toolbox, drag a **Flat file disassembler** pipeline component to the **Disassemble** stage of the pipeline.</span></span>  
  
10. <span data-ttu-id="f9ff0-146">Dans la fenêtre Propriétés pour le fichier plat désassembler, cliquez sur **DataModelTransformation.Schemas.NAOrderDocFF** dans les **schéma de Document** liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="f9ff0-146">In the Properties window for the flat file disassemble, click **DataModelTransformation.Schemas.NAOrderDocFF** in the **Document schema** drop-down list.</span></span>  
  
11. <span data-ttu-id="f9ff0-147">Dans la boîte à outils, faites glisser un **ESB itinéraire sélecteur** composant de pipeline pour le **résoudre le tiers** étape du pipeline.</span><span class="sxs-lookup"><span data-stu-id="f9ff0-147">From the Toolbox, drag an **ESB Itinerary Selector** pipeline component to the **Resolve Party** stage of the pipeline.</span></span>  
  
12. <span data-ttu-id="f9ff0-148">À partir de la boîte à outils, faites glisser un **ESB répartiteur** composant de pipeline le **résoudre le tiers** étape du pipeline, puis placez-le sous le **ESB itinéraire sélecteur** pipeline composant.</span><span class="sxs-lookup"><span data-stu-id="f9ff0-148">From the Toolbox, drag an **ESB Dispatcher** pipeline component to the **Resolve Party** stage of the pipeline, and then place it under the **ESB Itinerary Selector** pipeline component.</span></span>  
  
13. <span data-ttu-id="f9ff0-149">Enregistrez tous les artefacts de projet.</span><span class="sxs-lookup"><span data-stu-id="f9ff0-149">Save all project artifacts.</span></span>  
  
## <a name="to-create-the-test-message"></a><span data-ttu-id="f9ff0-150">Pour créer le message de test</span><span class="sxs-lookup"><span data-stu-id="f9ff0-150">To create the test message</span></span>  
  
1.  <span data-ttu-id="f9ff0-151">Cliquez une fois dans le fichier de schéma NAOrderDocFF.xsd du projet DataFormatTransformation.Schemas.</span><span class="sxs-lookup"><span data-stu-id="f9ff0-151">Click once in the NAOrderDocFF.xsd schema file of the DataFormatTransformation.Schemas project.</span></span> <span data-ttu-id="f9ff0-152">Dans le volet Propriétés de Visual Studio, modifiez les deux propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="f9ff0-152">In the Properties pane of Visual Studio, change the following two properties:</span></span>  
  
    -   <span data-ttu-id="f9ff0-153">**Générer le Type d’Instance de sortie**.</span><span class="sxs-lookup"><span data-stu-id="f9ff0-153">**Generate Instance Output Type**.</span></span> <span data-ttu-id="f9ff0-154">Cliquez sur la liste déroulante de cette propriété pour la remplacer par **natif**.</span><span class="sxs-lookup"><span data-stu-id="f9ff0-154">Click the drop-down list for this property to change it to **Native**.</span></span>  
  
    -   <span data-ttu-id="f9ff0-155">**Nom du fichier de l’Instance de sortie**.</span><span class="sxs-lookup"><span data-stu-id="f9ff0-155">**Output Instance Filename**.</span></span> <span data-ttu-id="f9ff0-156">Cliquez sur le bouton de sélection (...) pour cette propriété et acceptez le chemin d’accès par défaut de C:\Projects\Microsoft.Practices.ESB\Source\Samples\DataFormatTransformation.</span><span class="sxs-lookup"><span data-stu-id="f9ff0-156">Click the ellipsis button (…) for this property and accept the default path of C:\Projects\Microsoft.Practices.ESB\Source\Samples\DataFormatTransformation.</span></span> <span data-ttu-id="f9ff0-157">Dans le **nom de fichier** , tapez **NAOrderDocFF**, puis cliquez sur **enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="f9ff0-157">In the **File name** box, type **NAOrderDocFF**, and then click **Save**.</span></span>  
  
2.  <span data-ttu-id="f9ff0-158">Avec le bouton droit **NAOrderDocFF.xsd** sous **DataFormatTransformation.Schemas**, puis cliquez sur **générer l’Instance**.</span><span class="sxs-lookup"><span data-stu-id="f9ff0-158">Right-click **NAOrderDocFF.xsd** under **DataFormatTransformation.Schemas**, and then click **Generate Instance**.</span></span> <span data-ttu-id="f9ff0-159">À ce stade, vous devez générer un nouveau fichier dans le répertoire C:\Projects\Microsoft.Practices.ESB\Source\Samples\DataFormatTransformation.</span><span class="sxs-lookup"><span data-stu-id="f9ff0-159">At this point, you should have a new file generated in the C:\Projects\Microsoft.Practices.ESB\Source\Samples\DataFormatTransformation directory.</span></span>  
  
3.  <span data-ttu-id="f9ff0-160">Copie (ne déplacez pas) le fichier NAOrderDocFF.txt à partir de C:\Projects\Microsoft.Practices.ESB\Source\Samples\DataFormatTransformation à C:\HowTos.</span><span class="sxs-lookup"><span data-stu-id="f9ff0-160">Copy (do not move) the file NAOrderDocFF.txt from C:\Projects\Microsoft.Practices.ESB\Source\Samples\DataFormatTransformation to C:\HowTos.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f9ff0-161">Voici le message sera reçu et convertir au format XML.</span><span class="sxs-lookup"><span data-stu-id="f9ff0-161">This is the message you will receive and convert to XML.</span></span> <span data-ttu-id="f9ff0-162">Ce document représente une version de fichier plat de la commande en Amérique du Nord.</span><span class="sxs-lookup"><span data-stu-id="f9ff0-162">This document represents a flat file version of North American Order document.</span></span>  
  
## <a name="steps"></a><span data-ttu-id="f9ff0-163">Étapes</span><span class="sxs-lookup"><span data-stu-id="f9ff0-163">Steps</span></span>  
  
#### <a name="to-deploy-the-receive-pipeline-and-the-schema"></a><span data-ttu-id="f9ff0-164">Pour déployer le pipeline de réception et le schéma</span><span class="sxs-lookup"><span data-stu-id="f9ff0-164">To deploy the receive pipeline and the schema</span></span>  
  
1.  <span data-ttu-id="f9ff0-165">Avec le bouton droit **DataFormatTransformationReceive.Pipeline**, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="f9ff0-165">Right-click **DataFormatTransformationReceive.Pipeline**, and then click **Properties**.</span></span> <span data-ttu-id="f9ff0-166">Cliquez sur **déploiement**, puis tapez **Microsoft.Practices.ESB** dans les **nom de l’Application** boîte.</span><span class="sxs-lookup"><span data-stu-id="f9ff0-166">Click **Deployment**, and then type **Microsoft.Practices.ESB** in the **Application Name** box.</span></span>  
  
2.  <span data-ttu-id="f9ff0-167">Cliquez sur le **DataFormatTransformation.Schemas** de projet, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="f9ff0-167">Right-click the **DataFormatTransformation.Schemas** project, and then click **Properties**.</span></span> <span data-ttu-id="f9ff0-168">Cliquez sur **déploiement**, puis tapez **Microsoft.Practices.ESB** dans les **nom de l’Application** boîte.</span><span class="sxs-lookup"><span data-stu-id="f9ff0-168">Click **Deployment**, and then type **Microsoft.Practices.ESB** in the **Application Name** box.</span></span>  
  
3.  <span data-ttu-id="f9ff0-169">Fermer les volets de propriétés pour les deux **DataFormatTransformationReceive.Pipeline** et **DataFormatTransformation.Schemas**.</span><span class="sxs-lookup"><span data-stu-id="f9ff0-169">Close the Properties panes for both **DataFormatTransformationReceive.Pipeline** and **DataFormatTransformation.Schemas**.</span></span>  
  
4.  <span data-ttu-id="f9ff0-170">Dans l’Explorateur de solutions, cliquez sur le **DataFormatTransformation** de projet, puis cliquez sur **déployer la Solution**.</span><span class="sxs-lookup"><span data-stu-id="f9ff0-170">In Solution Explorer, right-click the **DataFormatTransformation** project, and then click **Deploy Solution**.</span></span>  
  
#### <a name="to-create-and-configure-an-esb-on-ramp"></a><span data-ttu-id="f9ff0-171">Pour créer et configurer un ESB rampe d’entrée</span><span class="sxs-lookup"><span data-stu-id="f9ff0-171">To create and configure an ESB on-ramp</span></span>  
  
1.  <span data-ttu-id="f9ff0-172">Cliquez sur **Démarrer** dans la barre des tâches, pointez sur **tous les programmes**, pointez sur  **[!INCLUDE[prague](../includes/prague-md.md)]** , puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="f9ff0-172">Click **Start** on the taskbar, point to **All Programs**, point to **[!INCLUDE[prague](../includes/prague-md.md)]**, and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="f9ff0-173">Dans le [!INCLUDE[prague](../includes/prague-md.md)] Console d’Administration, développez **groupe BizTalk**, développez **Applications**, puis cliquez sur **Microsoft.Practices.ESB**.</span><span class="sxs-lookup"><span data-stu-id="f9ff0-173">In the [!INCLUDE[prague](../includes/prague-md.md)] Administration Console, expand **BizTalk Group**, expand **Applications**, and then click **Microsoft.Practices.ESB**.</span></span>  
  
3.  <span data-ttu-id="f9ff0-174">Avec le bouton droit **emplacements de réception**, pointez sur **nouveau**, puis cliquez sur **emplacement de réception unidirectionnel**.</span><span class="sxs-lookup"><span data-stu-id="f9ff0-174">Right-click **Receive Locations**, point to **New**, and then click **One-way Receive Location**.</span></span>  
  
4.  <span data-ttu-id="f9ff0-175">Dans le **sélectionner un Port de réception** boîte de dialogue, cliquez sur **OnRamp.Itinerary**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="f9ff0-175">In the **Select a Receive Port** dialog box, click **OnRamp.Itinerary**, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="f9ff0-176">Dans le **propriétés de l’emplacement de réception** boîte de dialogue le **nom** , tapez **OnRamp.Itinerary.FlatFile.FILE**.</span><span class="sxs-lookup"><span data-stu-id="f9ff0-176">In the **Receive Location Properties** dialog box, in the **Name** box, type **OnRamp.Itinerary.FlatFile.FILE**.</span></span>  
  
6.  <span data-ttu-id="f9ff0-177">Dans le **Type** la liste déroulante, cliquez sur **fichier**, puis cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="f9ff0-177">In the **Type** drop-down list, click **FILE**, and then click **Configure**.</span></span>  
  
7.  <span data-ttu-id="f9ff0-178">Dans le **propriétés du Transport FILE** boîte de dialogue le **dossier de réception** , tapez **C:\HowTos\DropFolder**.</span><span class="sxs-lookup"><span data-stu-id="f9ff0-178">In the **FILE Transport Properties** dialog box, in the **Receive Folder** box, type **C:\HowTos\DropFolder**.</span></span>  
  
8.  <span data-ttu-id="f9ff0-179">Dans le **propriétés du Transport FILE** boîte de dialogue le **masque de fichier** , tapez  **\*.txt**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="f9ff0-179">In the **FILE Transport Properties** dialog box, in the **File mask** box, type **\*.txt**, and then click **OK**.</span></span>  
  
#### <a name="to-configure-the-itinerary-selector-pipeline-component"></a><span data-ttu-id="f9ff0-180">Pour configurer le composant de pipeline du sélecteur de feuille de route</span><span class="sxs-lookup"><span data-stu-id="f9ff0-180">To configure the Itinerary Selector pipeline component</span></span>  
  
1.  <span data-ttu-id="f9ff0-181">Dans le **propriétés de l’emplacement de réception** boîte de dialogue, cliquez sur **ItinerarySelectReceiveFF** dans les **pipeline de réception** zone de liste déroulante, puis cliquez sur le bouton de sélection (...).</span><span class="sxs-lookup"><span data-stu-id="f9ff0-181">In the **Receive Location Properties** dialog box, click **ItinerarySelectReceiveFF** in the **Receive pipeline** drop down list, and then click the ellipsis button (...).</span></span>  
  
2.  <span data-ttu-id="f9ff0-182">Utilisez le **configurer le Pipeline** boîte de dialogue pour configurer les éléments suivants **itinéraire sélecteur** les propriétés du composant :</span><span class="sxs-lookup"><span data-stu-id="f9ff0-182">Use the **Configure Pipeline** dialog box to configure the following **Itinerary Selector** component properties:</span></span>  
  
    1.  <span data-ttu-id="f9ff0-183">Cliquez sur le **ItineraryFactKey** propriété, puis tapez **Resolver.Itinerary**.</span><span class="sxs-lookup"><span data-stu-id="f9ff0-183">Click the **ItineraryFactKey** property, and then type **Resolver.Itinerary**.</span></span>  
  
    2.  <span data-ttu-id="f9ff0-184">Cliquez sur le **ResolverConnectionString** , tapez **itinéraire :\\\name=DataFormatTransformation ;** puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="f9ff0-184">Click the **ResolverConnectionString** property, type **ITINERARY:\\\name=DataFormatTransformation;** and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="f9ff0-185">Cliquez sur **OK** pour fermer la **propriétés de l’emplacement de réception** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="f9ff0-185">Click **OK** to close the **Receive Location Properties** dialog box.</span></span>  
  
4.  <span data-ttu-id="f9ff0-186">Dans le [!INCLUDE[prague](../includes/prague-md.md)] Console d’Administration, avec le bouton droit le **OnRamp.Itinerary.FlatFile.FILE** emplacement de réception, puis cliquez sur **activer**.</span><span class="sxs-lookup"><span data-stu-id="f9ff0-186">In the [!INCLUDE[prague](../includes/prague-md.md)] Administration Console, right-click the **OnRamp.Itinerary.FlatFile.FILE** receive location, and then click **Enable**.</span></span>  
  
#### <a name="to-test-itinerary-based-routing-of-a-flat-file-message"></a><span data-ttu-id="f9ff0-187">Pour tester le routage basé sur l’itinéraire d’un message de fichier plat</span><span class="sxs-lookup"><span data-stu-id="f9ff0-187">To test itinerary-based routing of a flat file message</span></span>  
  
1.  <span data-ttu-id="f9ff0-188">Dans l’Explorateur Windows, accédez à C:\HowTos.</span><span class="sxs-lookup"><span data-stu-id="f9ff0-188">In Windows Explorer, browse to C:\HowTos.</span></span>  
  
2.  <span data-ttu-id="f9ff0-189">Copie (ne déplacez pas) NAOrderDocFF.txt à C:\HowTos\DropFolder.</span><span class="sxs-lookup"><span data-stu-id="f9ff0-189">Copy (do not move) NAOrderDocFF.txt to C:\HowTos\DropFolder.</span></span>  
  
3.  <span data-ttu-id="f9ff0-190">Accédez à C:\HowTos\Out. Vérifiez que le message DFT%MessageID%.xml a été écrit dans le répertoire.</span><span class="sxs-lookup"><span data-stu-id="f9ff0-190">Browse to C:\HowTos\Out. Verify that the DFT%MessageID%.xml message has been written to the directory.</span></span>  
  
4.  <span data-ttu-id="f9ff0-191">Dans le [!INCLUDE[prague](../includes/prague-md.md)] Console d’Administration, avec le bouton droit le **OnRamp.Itinerary.FlatFile.FILE** emplacement de réception, puis cliquez sur **désactiver**.</span><span class="sxs-lookup"><span data-stu-id="f9ff0-191">In the [!INCLUDE[prague](../includes/prague-md.md)] Administration Console, right-click the **OnRamp.Itinerary.FlatFile.FILE** receive location, and then click **Disable**.</span></span>  
  
5.  <span data-ttu-id="f9ff0-192">Après le **OnRamp.Itinerary.FlatFile.FILE** recevoir d’emplacement est désactivée, faites un clic droit, puis cliquez sur **supprimer**.</span><span class="sxs-lookup"><span data-stu-id="f9ff0-192">After the **OnRamp.Itinerary.FlatFile.FILE** receive location is disabled, right-click it, and then click **Delete**.</span></span> <span data-ttu-id="f9ff0-193">Dans le **emplacement de réception de confirmer la suppression** boîte de dialogue, cliquez sur **Oui**.</span><span class="sxs-lookup"><span data-stu-id="f9ff0-193">In the **Confirm delete receive location** dialog box, click **Yes**.</span></span>  
  
## <a name="additional-resources"></a><span data-ttu-id="f9ff0-194">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="f9ff0-194">Additional Resources</span></span>  
 <span data-ttu-id="f9ff0-195">Pour plus d'informations, consultez les rubriques connexes suivantes :</span><span class="sxs-lookup"><span data-stu-id="f9ff0-195">For more information, see the following related topics:</span></span>  
  
-   [<span data-ttu-id="f9ff0-196">Comment : transformer un Message et router le Message résultant à un emplacement de fichier à l’aide d’un bon d’itinéraire de routage</span><span class="sxs-lookup"><span data-stu-id="f9ff0-196">How to: Transform a Message and Route the Resulting Message to a File Location Using an Itinerary Routing Slip</span></span>](../esb-toolkit/transform-message-and-route-the-message-to-a-location-using-itinerary-routing.md)  
  
-   [<span data-ttu-id="f9ff0-197">Comment : router un Message unique à plusieurs destinataires à l’aide d’un bon d’itinéraire de routage</span><span class="sxs-lookup"><span data-stu-id="f9ff0-197">How to: Route a Single Message to Multiple Recipients Using an Itinerary Routing Slip</span></span>](../esb-toolkit/route-a-single-message-to-multiple-recipients-using-an-itinerary-routing-slip.md)  
  
-   [<span data-ttu-id="f9ff0-198">Activités de développement</span><span class="sxs-lookup"><span data-stu-id="f9ff0-198">Development Activities</span></span>](../esb-toolkit/development-activities.md)  
  
-   [<span data-ttu-id="f9ff0-199">Modèles de Transformation de messages</span><span class="sxs-lookup"><span data-stu-id="f9ff0-199">Message Transformation Patterns</span></span>](../esb-toolkit/message-transformation-patterns.md)