---
title: 'Procédure pas à pas : Désassemblage de fichier plat à l’aide d’un en-tête et un code de fin | Documents Microsoft'
description: Utilisez l’Assistant schéma de fichier plat pour créer un schéma d’en-tête, le schéma de code de fin et le schéma de corps, puis désassembler un fichier plat dans BizTalk Server
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 715af9cc-d718-483d-b593-64462aa5a58b
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b7c1406367f047794c6d8931352104bb59e6ca5b
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="walkthrough-flat-file-disassembly-using-a-header-and-trailer"></a><span data-ttu-id="0bed5-103">Procédure pas à pas : Désassemblage de fichier plat à l’aide d’un en-tête et un code de fin</span><span class="sxs-lookup"><span data-stu-id="0bed5-103">Walkthrough: Flat File Disassembly Using a Header and Trailer</span></span>

## <a name="overview"></a><span data-ttu-id="0bed5-104">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="0bed5-104">Overview</span></span>
<span data-ttu-id="0bed5-105">Cette procédure pas à pas illustre l'utilisation de schémas créés par l'Assistant Schéma de fichier plat pour effectuer le désassemblage de fichier plat d'un fichier contenant un en-tête, un code de fin et un corps de message répété.</span><span class="sxs-lookup"><span data-stu-id="0bed5-105">This walkthrough demonstrates the use of schemas created by the Flat File Schema Wizard to perform flat file disassembly of a file containing a header, a trailer, and a repeating message body.</span></span> <span data-ttu-id="0bed5-106">Lors de cette procédure pas à pas, vous développez en partie un système de suivi des erreurs fictif répondant aux conditions suivantes :</span><span class="sxs-lookup"><span data-stu-id="0bed5-106">In this walkthrough, you develop part of a fictitious error-tracking system that meets the following requirements:</span></span>  
  
-   <span data-ttu-id="0bed5-107">les messages d'erreur sont consignés dans divers sites physiques de l'entreprise, puis envoyés vers un emplacement central pour être traités par différents systèmes principaux ;</span><span class="sxs-lookup"><span data-stu-id="0bed5-107">Error messages are logged at various physical sites within the company and sent to a central location for processing into various back-end systems.</span></span>  
  
-   <span data-ttu-id="0bed5-108">les messages d'erreur sont écrits dans un format de fichier plat qui comprend un en-tête indiquant l'emplacement, un corps contenant un ou plusieurs messages d'erreur et un code de fin indiquant le numéro du lot ;</span><span class="sxs-lookup"><span data-stu-id="0bed5-108">Error messages are written into a flat file format that contains a header indicating location, a body containing one or more error messages, and a trailer indicating the batch number.</span></span>  
  
-   <span data-ttu-id="0bed5-109">les messages sont considérés comme non valides s'ils ne comportent ni en-tête, ni corps, ni code de fin.</span><span class="sxs-lookup"><span data-stu-id="0bed5-109">Messages are considered invalid if they do not have a header, body, and trailer.</span></span>  
  
 <span data-ttu-id="0bed5-110">Au terme de la procédure pas à pas, vous disposez d'une application BizTalk Server qui traite les fichiers plats et les convertit au format XML en vue de leur traitement par un système principal.</span><span class="sxs-lookup"><span data-stu-id="0bed5-110">When the walkthrough is completed you will have a BizTalk Server application that processes flat files and writes them out as XML for processing by a back-end system.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="0bed5-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="0bed5-111">Prerequisites</span></span>  
 <span data-ttu-id="0bed5-112">Cet exemple nécessite que vous soyez familiarisé avec la création de projets BizTalk, la signature d'un assembly et l'utilisation de la console Administration de BizTalk Server pour afficher les applications et les ports.</span><span class="sxs-lookup"><span data-stu-id="0bed5-112">For this example you need to be comfortable with creating BizTalk Server projects, signing an assembly, and using the BizTalk Server Administration console to view applications and ports.</span></span> <span data-ttu-id="0bed5-113">Vous devez également être familiarisé avec les concepts présentés dans [procédure pas à pas : déploiement d’une Application BizTalk base](../core/walkthrough-deploying-a-basic-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="0bed5-113">You should also be comfortable with the ideas presented in [Walkthrough: Deploying a Basic BizTalk Application](../core/walkthrough-deploying-a-basic-biztalk-application.md).</span></span> <span data-ttu-id="0bed5-114">Les notions de base de l'Assistant Schéma de fichier plat sont également utiles mais pas nécessaires.</span><span class="sxs-lookup"><span data-stu-id="0bed5-114">Basic familiarity with the Flat File Schema Wizard is also helpful but not required.</span></span>  
  
## <a name="what-this-example-does"></a><span data-ttu-id="0bed5-115">Ce que fait cet exemple</span><span class="sxs-lookup"><span data-stu-id="0bed5-115">What This Example Does</span></span>  
 <span data-ttu-id="0bed5-116">Cet exemple traite des messages de fichier plat entrants à l'aide d'un pipeline personnalisé et du composant Désassembleur de fichier plat.</span><span class="sxs-lookup"><span data-stu-id="0bed5-116">This example processes inbound flat file messages using a custom pipeline and the Flat File Disassembler component.</span></span> <span data-ttu-id="0bed5-117">Les messages sont analysés à l'aide de schémas d'en-tête, de code de fin et de corps, puis écrits dans un emplacement d'envoi en vue du traitement principal.</span><span class="sxs-lookup"><span data-stu-id="0bed5-117">Messages are parsed using header, trailer, and body schemas and then written out to a send location for back-end processing.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0bed5-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="0bed5-118">Example</span></span>  
 <span data-ttu-id="0bed5-119">Pour créer l'exemple, suivez les étapes présentées dans les sections ci-après.</span><span class="sxs-lookup"><span data-stu-id="0bed5-119">To create the example, follow the steps outlined in the following sections.</span></span>  
  
### <a name="create-a-new-biztalk-project"></a><span data-ttu-id="0bed5-120">Créez un projet BizTalk</span><span class="sxs-lookup"><span data-stu-id="0bed5-120">Create a New BizTalk Project</span></span>  
 <span data-ttu-id="0bed5-121">Avant de concevoir une solution, vous devez créer un projet BizTalk, vous assurer qu'il porte un nom fort, puis lui attribuer un nom d'application.</span><span class="sxs-lookup"><span data-stu-id="0bed5-121">Before building a solution you need to create a BizTalk project, ensure that it is strongly named, and assign it an application name.</span></span> <span data-ttu-id="0bed5-122">Attribuer un nom d'application empêche BizTalk Server de déployer la solution dans l'application BizTalk par défaut.</span><span class="sxs-lookup"><span data-stu-id="0bed5-122">Assigning an application name prevents BizTalk Server from deploying the solution into the default BizTalk application.</span></span>  
  
1.  <span data-ttu-id="0bed5-123">Créez un projet BizTalk dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0bed5-123">Use [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] to create a new BizTalk project.</span></span> <span data-ttu-id="0bed5-124">Appelez le projet **FFDisassemblerWalkthrough**.</span><span class="sxs-lookup"><span data-stu-id="0bed5-124">Call the project **FFDisassemblerWalkthrough**.</span></span>  
  
2.  <span data-ttu-id="0bed5-125">Générez un fichier de clé et attribuez-le au projet.</span><span class="sxs-lookup"><span data-stu-id="0bed5-125">Generate a key file and assign it to the project.</span></span> <span data-ttu-id="0bed5-126">Pour plus d’informations, consultez [Page signature, Concepteur de projets](http://go.microsoft.com/fwlink/?LinkId=125876).</span><span class="sxs-lookup"><span data-stu-id="0bed5-126">For more information about this task, see [Signing Page, Project Designer](http://go.microsoft.com/fwlink/?LinkId=125876).</span></span>  
  
3.  <span data-ttu-id="0bed5-127">Dans les propriétés de déploiement pour le projet, définissez **nom de l’Application** à « FlatFileExample » et affectez **redémarrer les Instances d’hôte** à `True`.</span><span class="sxs-lookup"><span data-stu-id="0bed5-127">In the deployment properties for the project, set **Application Name** to “FlatFileExample” and set **Restart Host Instances** to `True`.</span></span> <span data-ttu-id="0bed5-128">La définition de cet indicateur indique à l'hôte d'effacer toutes les instances mises en cache de l'assembly.</span><span class="sxs-lookup"><span data-stu-id="0bed5-128">Setting this flag tells the host to clear any cached instances of the assembly.</span></span>  
  
### <a name="create-the-sample-data-file"></a><span data-ttu-id="0bed5-129">Création du fichier de données exemple</span><span class="sxs-lookup"><span data-stu-id="0bed5-129">Create the Sample Data File</span></span>  
<span data-ttu-id="0bed5-130">Avant de générer des schémas, vous devez créer un fichier de test.</span><span class="sxs-lookup"><span data-stu-id="0bed5-130">Before generating schemas, you need to create a test file.</span></span>   
  
1.  <span data-ttu-id="0bed5-131">Lancez le Bloc-notes ou un autre éditeur de texte.</span><span class="sxs-lookup"><span data-stu-id="0bed5-131">Start Notepad or another text editor.</span></span>  
  
2.  <span data-ttu-id="0bed5-132">Créer un exemple de fichier de test.</span><span class="sxs-lookup"><span data-stu-id="0bed5-132">Create a sample test file.</span></span> <span data-ttu-id="0bed5-133">Ce fichier est composé d'un en-tête indiquant l'emplacement qui signale les erreurs, d'un code de fin accompagné de l'ID de ce lot et d'un corps consistant en un ou plusieurs enregistrements Error.</span><span class="sxs-lookup"><span data-stu-id="0bed5-133">The file consists of a header indicating the location reporting the error(s), a trailer with a batch ID for this batch, and a body consisting of one or more error records.</span></span> <span data-ttu-id="0bed5-134">Le format du fichier est le suivant :</span><span class="sxs-lookup"><span data-stu-id="0bed5-134">The format of the file is as follows:</span></span>  
  
    ```  
    Location  
    ERRORid|type|priority|description|errorDateTime  
    …additional error records   
    BatchID  
    ```  
  
    <span data-ttu-id="0bed5-135">L’enregistrement ERROR est marqué avec le texte « Erreur » et délimité avec le «&#124;» caractères (et non pas positionnel).</span><span class="sxs-lookup"><span data-stu-id="0bed5-135">The ERROR record is tagged with the text “ERROR” and delimited with the “&#124;” character (versus positional).</span></span> <span data-ttu-id="0bed5-136">Les données qu'il contient sont décrites dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="0bed5-136">The data elements of the ERROR record are described in the following table.</span></span>  
  
    |<span data-ttu-id="0bed5-137">Élément</span><span class="sxs-lookup"><span data-stu-id="0bed5-137">Element</span></span>|<span data-ttu-id="0bed5-138">Type de données</span><span class="sxs-lookup"><span data-stu-id="0bed5-138">Data type</span></span>|<span data-ttu-id="0bed5-139"> Description</span><span class="sxs-lookup"><span data-stu-id="0bed5-139">Description</span></span>|  
    |---|---|---|  
    |<span data-ttu-id="0bed5-140">ID</span><span class="sxs-lookup"><span data-stu-id="0bed5-140">ID</span></span>|<span data-ttu-id="0bed5-141">entier</span><span class="sxs-lookup"><span data-stu-id="0bed5-141">integer</span></span>|<span data-ttu-id="0bed5-142">ID de l'erreur</span><span class="sxs-lookup"><span data-stu-id="0bed5-142">ID for this error.</span></span>|  
    |<span data-ttu-id="0bed5-143">Type</span><span class="sxs-lookup"><span data-stu-id="0bed5-143">Type</span></span>|<span data-ttu-id="0bed5-144">entier</span><span class="sxs-lookup"><span data-stu-id="0bed5-144">integer</span></span>|<span data-ttu-id="0bed5-145">Type d'erreur</span><span class="sxs-lookup"><span data-stu-id="0bed5-145">Type of error.</span></span>|  
    |<span data-ttu-id="0bed5-146">Priorité</span><span class="sxs-lookup"><span data-stu-id="0bed5-146">Priority</span></span>|<span data-ttu-id="0bed5-147">chaîne</span><span class="sxs-lookup"><span data-stu-id="0bed5-147">string</span></span>|<span data-ttu-id="0bed5-148">Indicateur de priorité : haute, moyenne ou faible.</span><span class="sxs-lookup"><span data-stu-id="0bed5-148">Priority indicator: Low, Medium, or High.</span></span>|  
    |<span data-ttu-id="0bed5-149"> Description</span><span class="sxs-lookup"><span data-stu-id="0bed5-149">Description</span></span>|<span data-ttu-id="0bed5-150">chaîne</span><span class="sxs-lookup"><span data-stu-id="0bed5-150">string</span></span>|<span data-ttu-id="0bed5-151">Description de l’erreur.</span><span class="sxs-lookup"><span data-stu-id="0bed5-151">Description of the error.</span></span>|  
    |<span data-ttu-id="0bed5-152">ErrorDateTime</span><span class="sxs-lookup"><span data-stu-id="0bed5-152">ErrorDateTime</span></span>|<span data-ttu-id="0bed5-153">DateTime</span><span class="sxs-lookup"><span data-stu-id="0bed5-153">DateTime</span></span>|<span data-ttu-id="0bed5-154">Date et heure auxquelles l'erreur s'est produite.</span><span class="sxs-lookup"><span data-stu-id="0bed5-154">Date and time that the error occurred.</span></span>|  
  
    <span data-ttu-id="0bed5-155">Le fichier peut comporter un ou plusieurs enregistrements ERROR.</span><span class="sxs-lookup"><span data-stu-id="0bed5-155">The file can have one or more ERROR records.</span></span>  
  
     <span data-ttu-id="0bed5-156">**--OU--**</span><span class="sxs-lookup"><span data-stu-id="0bed5-156">**-- OR --  **</span></span>
  
     <span data-ttu-id="0bed5-157">Copiez les données suivantes dans le nouveau fichier.</span><span class="sxs-lookup"><span data-stu-id="0bed5-157">Copy the following sample data into the new file.</span></span> <span data-ttu-id="0bed5-158">La dernière ligne contient un saut de ligne de fin :</span><span class="sxs-lookup"><span data-stu-id="0bed5-158">The last line contains a trailing linefeed:</span></span>
  
    ```  
    East Coast Facility  
    ERROR102|0|High|Sprocket query fails.|1999-05-31T13:20:00.000-05:00  
    ERROR16502|2|Low|Time threshold exceeded.|1999-05-31T13:20:00.000-05:00  
    8675309  
  
    ```  
  
3.  <span data-ttu-id="0bed5-159">Enregistrez le nouveau fichier exemple dans le répertoire du projet.</span><span class="sxs-lookup"><span data-stu-id="0bed5-159">Save the new sample file in the project directory.</span></span> <span data-ttu-id="0bed5-160">Nommez-le par exemple « ErrorFile.txt. ».</span><span class="sxs-lookup"><span data-stu-id="0bed5-160">Use a descriptive name like "ErrorFile.txt" so it can be located easily.</span></span>  
  
### <a name="create-and-test-the-header-trailer-and-body-schemas"></a><span data-ttu-id="0bed5-161">Création et test des schémas d'en-tête, de code de fin et de corps</span><span class="sxs-lookup"><span data-stu-id="0bed5-161">Create and Test the Header, Trailer, and Body Schemas</span></span>  
 <span data-ttu-id="0bed5-162">Une fois le fichier de données exemple créé, l'étape suivante consiste à créer les schémas d'en-tête, de code de fin et de corps.</span><span class="sxs-lookup"><span data-stu-id="0bed5-162">After the sample data file is created, the next step is to create the header, trailer, and body schemas.</span></span> <span data-ttu-id="0bed5-163">Ces schémas sont utilisés avec le composant de pipeline Désassembleur de fichier plat pour traiter les messages reçus.</span><span class="sxs-lookup"><span data-stu-id="0bed5-163">These schemas are used with the Flat File Disassembler receive pipeline component to process received messages.</span></span>  
  
##### <a name="use-the-flat-file-schema-wizard-to-create-the-header-schema"></a><span data-ttu-id="0bed5-164">Utilisez l’Assistant schéma de fichier plat pour créer le schéma d’en-tête</span><span class="sxs-lookup"><span data-stu-id="0bed5-164">Use the Flat File Schema Wizard to create the header schema</span></span>  
  
1.  <span data-ttu-id="0bed5-165">Ajoutez un nouveau schéma au projet.</span><span class="sxs-lookup"><span data-stu-id="0bed5-165">Add a new schema to the project.</span></span> <span data-ttu-id="0bed5-166">Dans l’Explorateur de solutions, cliquez sur **FFDisassemblerWalkthrough**, pointez sur **ajouter**, puis cliquez sur **un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="0bed5-166">In Solution Explorer, right-click **FFDisassemblerWalkthrough**, point to **Add**, and then click **New Item**.</span></span>  
  
2.  <span data-ttu-id="0bed5-167">Dans le **ajouter un nouvel élément** boîte de dialogue, cliquez sur **les fichiers de schéma** et sélectionnez **Assistant schéma de fichier plat**.</span><span class="sxs-lookup"><span data-stu-id="0bed5-167">In the **Add New Item** dialog box, click **Schema Files** and select **Flat File Schema Wizard**.</span></span> <span data-ttu-id="0bed5-168">Nommez le nouveau schéma « Header.xsd », puis **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="0bed5-168">Name the new schema "Header.xsd" and then click **Add**.</span></span>  
  
3.  <span data-ttu-id="0bed5-169">Sur le **Bienvenue dans l’Assistant schéma de fichier plat BizTalk** , cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="0bed5-169">On the **Welcome to the BizTalk Flat File Schema Wizard** page, click **Next**.</span></span>  
  
4.  <span data-ttu-id="0bed5-170">Sur le **informations de schéma de fichier plat** , cliquez sur **Parcourir** et recherchez le fichier de données exemple créé précédemment.</span><span class="sxs-lookup"><span data-stu-id="0bed5-170">On the **Flat File Schema Information** page, click **Browse** and locate the sample data file created earlier.</span></span> <span data-ttu-id="0bed5-171">Modifier la **nom de l’enregistrement** à « En-tête », vérifiez que la page de codes, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="0bed5-171">Change the **Record Name** to "Header", verify the code page, and then click **Next**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0bed5-172">Si vous avez enregistré l'exemple de fichier au format Unicode, le format de la page de code est Little-Endian-UTF16 (1200).</span><span class="sxs-lookup"><span data-stu-id="0bed5-172">If you saved the sample file in Unicode format the code page will be Little-Endian-UTF16 (1200).</span></span> <span data-ttu-id="0bed5-173">Ceci n'affecte pas l'exemple.</span><span class="sxs-lookup"><span data-stu-id="0bed5-173">This will not adversely affect the example.</span></span>  
  
5.  <span data-ttu-id="0bed5-174">Sélectionnez ensuite les données du document.</span><span class="sxs-lookup"><span data-stu-id="0bed5-174">Next select the document data.</span></span> <span data-ttu-id="0bed5-175">Sur le **sélectionner des données du Document** page, mettez en surbrillance la première ligne de données, notamment les caractères de nouvelle ligne {CR} et {LF} comme suit :</span><span class="sxs-lookup"><span data-stu-id="0bed5-175">On the **Select Document Data** page, highlight the first line of data including the new-line characters {CR} and {LF} as shown:</span></span>  
  
     <span data-ttu-id="0bed5-176">![Données sélectionnées pour le schéma d’en-tête](../core/media/ffwiz-header-select-document-data.gif "ffwiz_header_select_document_data")</span><span class="sxs-lookup"><span data-stu-id="0bed5-176">![Data selected for header schema](../core/media/ffwiz-header-select-document-data.gif "ffwiz_header_select_document_data")</span></span>  
  
     <span data-ttu-id="0bed5-177">Cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="0bed5-177">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="0bed5-178">Sur le **sélectionner le Format d’enregistrement** , cliquez sur **suivant** pour accepter la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="0bed5-178">On the **Select Record Format** page, click **Next** to accept the default.</span></span> <span data-ttu-id="0bed5-179">Vous pouvez accepter l'option « par symbole délimiteur » par défaut, car le fichier de données n'utilise pas de position relative.</span><span class="sxs-lookup"><span data-stu-id="0bed5-179">You can accept the default "by delimiter symbol" because the data file does not use relative position.</span></span>  
  
7.  <span data-ttu-id="0bed5-180">Sur le **enregistrement délimité** , cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="0bed5-180">On the **Delimited Record** page, click **Next**.</span></span>  
  
8.  <span data-ttu-id="0bed5-181">À présent, spécifiez les éléments enfants.</span><span class="sxs-lookup"><span data-stu-id="0bed5-181">Now you specify child elements.</span></span> <span data-ttu-id="0bed5-182">L'en-tête contient un élément nommé « Location » :</span><span class="sxs-lookup"><span data-stu-id="0bed5-182">The header contains one element named "Location":</span></span>  
  
     <span data-ttu-id="0bed5-183">![Nœud d’emplacement défini pour l’en-tête](../core/media/ffwiz-header-child-elements.gif "ffwiz_header_child_elements")</span><span class="sxs-lookup"><span data-stu-id="0bed5-183">![Location node defined for header](../core/media/ffwiz-header-child-elements.gif "ffwiz_header_child_elements")</span></span>  
  
     <span data-ttu-id="0bed5-184">Cliquez sur **Suivant** pour continuer.</span><span class="sxs-lookup"><span data-stu-id="0bed5-184">Click **Next** to continue.</span></span>  
  
9. <span data-ttu-id="0bed5-185">Sur le **vue schéma** , vérifiez le schéma.</span><span class="sxs-lookup"><span data-stu-id="0bed5-185">On the **Schema View** page, verify the schema.</span></span>  
  
     <span data-ttu-id="0bed5-186">![Schéma d’en-tête de vue de schéma illustrant terminée](../core/media/ffwiz-header-schema-view.gif "ffwiz_header_schema_view")</span><span class="sxs-lookup"><span data-stu-id="0bed5-186">![Schema view showing completed Header schema](../core/media/ffwiz-header-schema-view.gif "ffwiz_header_schema_view")</span></span>  
  
     <span data-ttu-id="0bed5-187">Lorsque vous êtes satisfait, cliquez sur **Terminer** pour terminer l’Assistant.</span><span class="sxs-lookup"><span data-stu-id="0bed5-187">When you are satisfied, click **Finish** to complete the wizard.</span></span>  
  
10. <span data-ttu-id="0bed5-188">Cliquez sur le **\<schéma\>** nœud dans le volet Schéma d’en-tête.</span><span class="sxs-lookup"><span data-stu-id="0bed5-188">Click the **\<Schema\>** node in the Header schema pane.</span></span> <span data-ttu-id="0bed5-189">Dans le volet Propriétés, modifiez **Element FormDefault** à **Qualified**.</span><span class="sxs-lookup"><span data-stu-id="0bed5-189">In the Properties pane, change **Element FormDefault** to **Qualified**.</span></span> <span data-ttu-id="0bed5-190">Vous indiquez ainsi que les éléments déclarés localement doivent être qualifiés par l'espace de noms cible dans un document d'instance.</span><span class="sxs-lookup"><span data-stu-id="0bed5-190">This indicates that locally declared elements must be qualified by the target namespace in an instance document.</span></span>  
  
##### <a name="use-the-flat-file-schema-wizard-to-create-the-trailer-schema"></a><span data-ttu-id="0bed5-191">Utilisez l’Assistant schéma de fichier plat pour créer le schéma de code de fin</span><span class="sxs-lookup"><span data-stu-id="0bed5-191">Use the Flat File Schema Wizard to create the trailer schema</span></span>  
  
1.  <span data-ttu-id="0bed5-192">Ajoutez un nouveau schéma au projet.</span><span class="sxs-lookup"><span data-stu-id="0bed5-192">Add a new schema to the project.</span></span> <span data-ttu-id="0bed5-193">Dans l’Explorateur de solutions, cliquez sur **FFDisassemblerWalkthrough**, pointez sur **ajouter** , puis cliquez sur **un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="0bed5-193">In Solution Explorer, right-click **FFDisassemblerWalkthrough**, point to **Add** , and then click **New Item**.</span></span>  
  
2.  <span data-ttu-id="0bed5-194">Dans le **ajouter un nouvel élément** boîte de dialogue, cliquez sur **les fichiers de schéma** et sélectionnez **Assistant schéma de fichier plat**.</span><span class="sxs-lookup"><span data-stu-id="0bed5-194">In the **Add New Item** dialog box, click **Schema Files** and select **Flat File Schema Wizard**.</span></span> <span data-ttu-id="0bed5-195">Nommez le nouveau schéma « Trailer.xsd », puis **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="0bed5-195">Name the new schema "Trailer.xsd" and then click **Add**.</span></span>  
  
3.  <span data-ttu-id="0bed5-196">Sur le **Bienvenue dans l’Assistant schéma de fichier plat BizTalk** , cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="0bed5-196">On the **Welcome to the BizTalk Flat File Schema Wizard** page, click **Next**.</span></span>  
  
4.  <span data-ttu-id="0bed5-197">Sur le **informations de schéma de fichier plat** , cliquez sur **Parcourir** et recherchez le fichier de données exemple créé précédemment.</span><span class="sxs-lookup"><span data-stu-id="0bed5-197">On the **Flat File Schema Information** page, click **Browse** and locate the sample data file created earlier.</span></span> <span data-ttu-id="0bed5-198">Modifier la **nom de l’enregistrement** par « Trailer », vérifiez que la page de codes, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="0bed5-198">Change the **Record Name** to "Trailer", verify the code page, and then click **Next**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0bed5-199">Si vous avez enregistré l'exemple de fichier au format Unicode, le format de la page de code est Little-Endian-UTF16 (1200).</span><span class="sxs-lookup"><span data-stu-id="0bed5-199">If you saved the sample file in Unicode format the code page will be Little-Endian-UTF16 (1200).</span></span> <span data-ttu-id="0bed5-200">Ceci n'affecte pas l'exemple.</span><span class="sxs-lookup"><span data-stu-id="0bed5-200">This will not adversely affect the example.</span></span>  
  
5.  <span data-ttu-id="0bed5-201">Sélectionnez ensuite les données du document.</span><span class="sxs-lookup"><span data-stu-id="0bed5-201">Next select the document data.</span></span> <span data-ttu-id="0bed5-202">Sur le **sélectionner des données du Document** page, sélectionnez la dernière ligne de données, notamment les caractères de nouvelle ligne {CR} et {LF} comme suit :</span><span class="sxs-lookup"><span data-stu-id="0bed5-202">On the **Select Document Data** page, highlight the last line of data including the new-line characters {CR} and {LF} as shown:</span></span>  
  
     <span data-ttu-id="0bed5-203">![Les données sélectionnées pour le schéma de code de fin](../core/media/ffwiz-trailer-select-document-data.gif "ffwiz_trailer_select_document_data")</span><span class="sxs-lookup"><span data-stu-id="0bed5-203">![Data selected for trailer schema](../core/media/ffwiz-trailer-select-document-data.gif "ffwiz_trailer_select_document_data")</span></span>  
  
     <span data-ttu-id="0bed5-204">Cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="0bed5-204">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="0bed5-205">Sur le **sélectionner le Format d’enregistrement** , cliquez sur **suivant** pour accepter la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="0bed5-205">On the **Select Record Format** page, click **Next** to accept the default.</span></span> <span data-ttu-id="0bed5-206">Vous pouvez accepter l'option « par symbole délimiteur » par défaut, car le fichier de données n'utilise pas de position relative.</span><span class="sxs-lookup"><span data-stu-id="0bed5-206">You can accept the default "by delimiter symbol" because the data file does not use relative position.</span></span>  
  
7.  <span data-ttu-id="0bed5-207">Sur le **enregistrement délimité** , cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="0bed5-207">On the **Delimited Record** page, click **Next**.</span></span>  
  
8.  <span data-ttu-id="0bed5-208">À présent, spécifiez les éléments enfants.</span><span class="sxs-lookup"><span data-stu-id="0bed5-208">Now you specify child elements.</span></span> <span data-ttu-id="0bed5-209">L'en-tête contient un élément nommé « BatchID » :</span><span class="sxs-lookup"><span data-stu-id="0bed5-209">The header contains one element named "BatchID":</span></span>  
  
     <span data-ttu-id="0bed5-210">![Nœud d’emplacement défini pour le code de fin](../core/media/ffwiz-trailer-child-elements.gif "ffwiz_trailer_child_elements")</span><span class="sxs-lookup"><span data-stu-id="0bed5-210">![Location node defined for trailer](../core/media/ffwiz-trailer-child-elements.gif "ffwiz_trailer_child_elements")</span></span>  
  
     <span data-ttu-id="0bed5-211">Cliquez sur **Suivant** pour continuer.</span><span class="sxs-lookup"><span data-stu-id="0bed5-211">Click **Next** to continue.</span></span>  
  
9. <span data-ttu-id="0bed5-212">Sur le **vue schéma** , vérifiez le schéma.</span><span class="sxs-lookup"><span data-stu-id="0bed5-212">On the **Schema View** page, verify the schema.</span></span>  
  
     <span data-ttu-id="0bed5-213">![Schéma de code de fin terminée affichant](../core/media/ffwiz-trailer-schema-view.gif "ffwiz_trailer_schema_view")</span><span class="sxs-lookup"><span data-stu-id="0bed5-213">![Schema view showing completed Trailer schema](../core/media/ffwiz-trailer-schema-view.gif "ffwiz_trailer_schema_view")</span></span>  
  
     <span data-ttu-id="0bed5-214">Lorsque vous êtes satisfait, cliquez sur **Terminer** pour terminer l’Assistant.</span><span class="sxs-lookup"><span data-stu-id="0bed5-214">When you are satisfied, click **Finish** to complete the wizard.</span></span>  
  
10. <span data-ttu-id="0bed5-215">Cliquez sur le **\<schéma\>** nœud dans le volet Schéma de code de fin.</span><span class="sxs-lookup"><span data-stu-id="0bed5-215">Click the **\<Schema\>** node in the Trailer schema pane.</span></span> <span data-ttu-id="0bed5-216">Dans le volet Propriétés, modifiez **elementFormDefault** à **Qualified**.</span><span class="sxs-lookup"><span data-stu-id="0bed5-216">In the Properties pane, change **elementFormDefault** to **Qualified**.</span></span> <span data-ttu-id="0bed5-217">Vous indiquez ainsi que les éléments déclarés localement doivent être qualifiés par l'espace de noms cible dans un document d'instance.</span><span class="sxs-lookup"><span data-stu-id="0bed5-217">This indicates that locally declared elements must be qualified by the target namespace in an instance document.</span></span>  
  
##### <a name="use-the-flat-file-schema-wizard-to-create-the-body-schema"></a><span data-ttu-id="0bed5-218">Utilisez l’Assistant schéma de fichier plat pour créer le schéma de corps</span><span class="sxs-lookup"><span data-stu-id="0bed5-218">Use the Flat File Schema Wizard to create the body schema</span></span>  
  
1.  <span data-ttu-id="0bed5-219">Ajoutez un nouveau schéma au projet.</span><span class="sxs-lookup"><span data-stu-id="0bed5-219">Add a new schema to the project.</span></span> <span data-ttu-id="0bed5-220">Dans l’Explorateur de solutions, cliquez sur **FFDisassemblerWalkthrough**, pointez sur **ajouter**, puis cliquez sur **un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="0bed5-220">In Solution Explorer, right-click **FFDisassemblerWalkthrough**, point to **Add**, and then click **New Item**.</span></span>  
  
2.  <span data-ttu-id="0bed5-221">Dans le **ajouter un nouvel élément** boîte de dialogue, cliquez sur **les fichiers de schéma** et sélectionnez **Assistant schéma de fichier plat**.</span><span class="sxs-lookup"><span data-stu-id="0bed5-221">In the **Add New Item** dialog box, click **Schema Files** and select **Flat File Schema Wizard**.</span></span> <span data-ttu-id="0bed5-222">Nommez le nouveau schéma « Body.xsd », puis **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="0bed5-222">Name the new schema "Body.xsd" and then click **Add**.</span></span>  
  
3.  <span data-ttu-id="0bed5-223">Sur le **Bienvenue dans l’Assistant schéma de fichier plat BizTalk** , cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="0bed5-223">On the **Welcome to the BizTalk Flat File Schema Wizard** page, click **Next**.</span></span>  
  
4.  <span data-ttu-id="0bed5-224">Sur le **informations de schéma de fichier plat** , cliquez sur **Parcourir** et recherchez le fichier de données exemple créé précédemment.</span><span class="sxs-lookup"><span data-stu-id="0bed5-224">On the **Flat File Schema Information** page, click **Browse** and locate the sample data file created earlier.</span></span> <span data-ttu-id="0bed5-225">Modifier la **nom de l’enregistrement** sur « Corps », vérifiez que la page de codes, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="0bed5-225">Change the **Record Name** to "Body", verify the code page, and then click **Next**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0bed5-226">Si vous avez enregistré l'exemple de fichier au format Unicode, le format de la page de code est Little-Endian-UTF16 (1200).</span><span class="sxs-lookup"><span data-stu-id="0bed5-226">If you saved the sample file in Unicode format the code page will be Little-Endian-UTF16 (1200).</span></span> <span data-ttu-id="0bed5-227">Ceci n'affecte pas l'exemple.</span><span class="sxs-lookup"><span data-stu-id="0bed5-227">This will not adversely affect the example.</span></span>  
  
5.  <span data-ttu-id="0bed5-228">Sélectionnez ensuite les données du document.</span><span class="sxs-lookup"><span data-stu-id="0bed5-228">Next select the document data.</span></span> <span data-ttu-id="0bed5-229">Sur le **sélectionner des données du Document** page, sélectionnez les lignes deux et trois des données, notamment les caractères de nouvelle ligne {CR} et {LF} comme suit :</span><span class="sxs-lookup"><span data-stu-id="0bed5-229">On the **Select Document Data** page, highlight lines two and three of data including the new-line characters {CR} and {LF} as shown:</span></span>  
  
     <span data-ttu-id="0bed5-230">![Les données sélectionnées pour le schéma de corps](../core/media/ffwiz-body-select-document-data.gif "ffwiz_body_select_document_data")</span><span class="sxs-lookup"><span data-stu-id="0bed5-230">![Data selected for body schema](../core/media/ffwiz-body-select-document-data.gif "ffwiz_body_select_document_data")</span></span>  
  
     <span data-ttu-id="0bed5-231">Cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="0bed5-231">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="0bed5-232">Sur le **sélectionner le Format d’enregistrement** , cliquez sur **suivant** pour accepter la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="0bed5-232">On the **Select Record Format** page, click **Next** to accept the default.</span></span> <span data-ttu-id="0bed5-233">Vous pouvez accepter l'option « par symbole délimiteur » par défaut, car le fichier de données n'utilise pas de position relative.</span><span class="sxs-lookup"><span data-stu-id="0bed5-233">You can accept the default "by delimiter symbol" because the data file does not use relative position.</span></span>  
  
7.  <span data-ttu-id="0bed5-234">Sur le **enregistrement délimité** page, sélectionnez **suivant**.</span><span class="sxs-lookup"><span data-stu-id="0bed5-234">On the **Delimited Record** page, select **Next**.</span></span>  
  
8.  <span data-ttu-id="0bed5-235">Définissez ensuite les éléments enfants.</span><span class="sxs-lookup"><span data-stu-id="0bed5-235">Next define the child elements.</span></span> <span data-ttu-id="0bed5-236">Modification **Body_Child1** à **erreur**et définissez son type d’élément **enregistrement répété**.</span><span class="sxs-lookup"><span data-stu-id="0bed5-236">Change **Body_Child1** to **Error**and set its element type to **Repeating record**.</span></span> <span data-ttu-id="0bed5-237">Définir le **Body_Child2** type d’enregistrement à élément **ignorer**.</span><span class="sxs-lookup"><span data-stu-id="0bed5-237">Set the **Body_Child2** element record type to **Ignore**.</span></span>  
  
9. <span data-ttu-id="0bed5-238">Sur le **vue schéma** , cliquez sur **suivant** pour définir les éléments enfants de l’enregistrement d’erreur.</span><span class="sxs-lookup"><span data-stu-id="0bed5-238">On the **Schema View** page, click **Next** to define the child elements of the Error record.</span></span>  
  
10. <span data-ttu-id="0bed5-239">Sur le **sélectionner des données du Document** , cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="0bed5-239">On the **Select Document Data** page, click **Next**.</span></span> <span data-ttu-id="0bed5-240">L'Assistant choisit les données de définition d'enregistrement correctement.</span><span class="sxs-lookup"><span data-stu-id="0bed5-240">The wizard chooses the record-defining data correctly.</span></span>  
  
11. <span data-ttu-id="0bed5-241">Sur le **sélectionner le Format d’enregistrement** , cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="0bed5-241">On the **Select Record Format** page, click **Next**.</span></span> <span data-ttu-id="0bed5-242">Les données sont formatées par symbole délimiteur.</span><span class="sxs-lookup"><span data-stu-id="0bed5-242">The data is formatted by delimiter symbol.</span></span>  
  
12. <span data-ttu-id="0bed5-243">Sur le **enregistrement délimité** page, sélectionnez **&#124;** pour le **délimiteur enfant**.</span><span class="sxs-lookup"><span data-stu-id="0bed5-243">On the **Delimited Record** page, select **&#124;** for the **Child delimiter**.</span></span> <span data-ttu-id="0bed5-244">Ensuite, sélectionnez le **enregistrement comporte un identificateur de balise** et tapez **erreur** pour la valeur de balise.</span><span class="sxs-lookup"><span data-stu-id="0bed5-244">Next, select the **Record has a tag identifier** check box and type **ERROR** for the tag value.</span></span>  
  
     <span data-ttu-id="0bed5-245">![Configuration délimitées enregistrement avec l’identificateur de balise](../core/media/ffwiz-bodyerror-delimited-record.gif "ffwiz_bodyerror_delimited_record")</span><span class="sxs-lookup"><span data-stu-id="0bed5-245">![Configuring delimited record with tag identifier](../core/media/ffwiz-bodyerror-delimited-record.gif "ffwiz_bodyerror_delimited_record")</span></span>  
  
     <span data-ttu-id="0bed5-246">Cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="0bed5-246">Click **Next**.</span></span>  
  
13. <span data-ttu-id="0bed5-247">Définissez à présent les éléments enfants de l'enregistrement Error.</span><span class="sxs-lookup"><span data-stu-id="0bed5-247">Now define the child elements of the Error record.</span></span>  
  
     <span data-ttu-id="0bed5-248">![Enregistrement d’erreur défini avec cinq éléments](../core/media/ffwiz-bodyerror-child-elements.gif "ffwiz_bodyerror_child_elements")</span><span class="sxs-lookup"><span data-stu-id="0bed5-248">![Error record defined with five elements](../core/media/ffwiz-bodyerror-child-elements.gif "ffwiz_bodyerror_child_elements")</span></span>  
  
     <span data-ttu-id="0bed5-249">Cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="0bed5-249">Click **Next**.</span></span>  
  
14. <span data-ttu-id="0bed5-250">Sur le **vue schéma** , vérifiez le schéma.</span><span class="sxs-lookup"><span data-stu-id="0bed5-250">On the **Schema View** page, verify the schema.</span></span>  
  
     <span data-ttu-id="0bed5-251">![Schéma de corps terminée affichant](../core/media/ffwiz-bodyerror-schema-view.gif "ffwiz_bodyerror_schema_view")</span><span class="sxs-lookup"><span data-stu-id="0bed5-251">![Schema view showing completed Body schema](../core/media/ffwiz-bodyerror-schema-view.gif "ffwiz_bodyerror_schema_view")</span></span>  
  
     <span data-ttu-id="0bed5-252">Si vous avez apporté des erreurs, cliquez sur **nouveau** et apporter les corrections nécessaires.</span><span class="sxs-lookup"><span data-stu-id="0bed5-252">If you have made any mistakes, click **Back** and make the necessary corrections.</span></span> <span data-ttu-id="0bed5-253">Lorsque vous êtes satisfait, cliquez sur **Terminer** pour terminer l’Assistant.</span><span class="sxs-lookup"><span data-stu-id="0bed5-253">When you are satisfied, click **Finish** to complete the wizard.</span></span>  
  
15. <span data-ttu-id="0bed5-254">Cliquez sur le **\<schéma\>** nœud dans le volet Schéma de corps.</span><span class="sxs-lookup"><span data-stu-id="0bed5-254">Click the **\<Schema\>** node in the Body schema pane.</span></span> <span data-ttu-id="0bed5-255">Dans le volet Propriétés, modifiez **Element FormDefault** à **Qualified**.</span><span class="sxs-lookup"><span data-stu-id="0bed5-255">In the Properties pane, change **Element FormDefault** to **Qualified**.</span></span> <span data-ttu-id="0bed5-256">Vous indiquez ainsi que les éléments déclarés localement doivent être qualifiés par l'espace de noms cible dans un document d'instance.</span><span class="sxs-lookup"><span data-stu-id="0bed5-256">This indicates that locally declared elements must be qualified by the target namespace in an instance document.</span></span>  
  
16. <span data-ttu-id="0bed5-257">Cliquez sur le **\<erreur\>** nœud dans le volet Schéma de corps.</span><span class="sxs-lookup"><span data-stu-id="0bed5-257">Click the **\<Error\>** node on the Body schema pane.</span></span> <span data-ttu-id="0bed5-258">Dans le volet Propriétés, modifiez **Max Occurs** à **1**.</span><span class="sxs-lookup"><span data-stu-id="0bed5-258">In the Properties pane, change **Max Occurs** to **1**.</span></span> <span data-ttu-id="0bed5-259">Le désassembleur de fichier plat fractionne alors chaque erreur dans son propre message.</span><span class="sxs-lookup"><span data-stu-id="0bed5-259">This causes the Flat File Disassembler to split each error into its own message.</span></span>  
  
##### <a name="test-the-schemas-using-ffdasm"></a><span data-ttu-id="0bed5-260">Tester les schémas à l’aide de FFDasm</span><span class="sxs-lookup"><span data-stu-id="0bed5-260">Test the schemas using FFDasm</span></span>  
  
1.  <span data-ttu-id="0bed5-261">Ouvrez une invite de commandes et remplacez le répertoire par celui de votre projet.</span><span class="sxs-lookup"><span data-stu-id="0bed5-261">Open a command prompt and change the directory to your project directory.</span></span>  
  
2.  <span data-ttu-id="0bed5-262">À l'invite de commandes, exécutez FFDasm.exe comme suit.</span><span class="sxs-lookup"><span data-stu-id="0bed5-262">From the command prompt, run FFDasm.exe as shown below.</span></span>  
  
    ```  
    <Samples Path>\SDK\Utilities\PipelineTools\FFDasm ErrorFile.txt  -hs header.xsd -bs body.xsd -ts Trailer.xsd  
    ```  
  
     <span data-ttu-id="0bed5-263">Pour plus d’informations sur l’emplacement de ce document et d’autres outils de pipeline, consultez [outils de Pipeline](../core/pipeline-tools.md).</span><span class="sxs-lookup"><span data-stu-id="0bed5-263">For information about the location of this and other pipeline tools, see [Pipeline Tools](../core/pipeline-tools.md).</span></span>  
  
3.  <span data-ttu-id="0bed5-264">FFDasm.exe génère normalement deux fichiers de sortie nommés {GUID}.xml, un pour chaque enregistrement ERROR du fichier de test.</span><span class="sxs-lookup"><span data-stu-id="0bed5-264">FFDasm.exe should produce two output files named {GUID}.xml, one for each ERROR record in the test file.</span></span> <span data-ttu-id="0bed5-265">L'enregistrement Error prioritaire se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="0bed5-265">The high-priority error record looks like the following:</span></span>  
  
    ```  
    <Body xmlns="http://FFDisassemblerWalkthrough.Body">  
      <Error>  
        <ID>102</ID>  
        <Type>0</Type>  
        <Priority>High</Priority>  
        <Description>Sprocket query fails.</Description>  
        <DateTime>1999-05-31T13:20:00.000-05:00</DateTime>  
      </Error>  
    </Body>  
    ```  
  
### <a name="create-a-custom-receive-pipeline"></a><span data-ttu-id="0bed5-266">Création d'un pipeline de réception personnalisé</span><span class="sxs-lookup"><span data-stu-id="0bed5-266">Create a Custom Receive Pipeline</span></span>  
 <span data-ttu-id="0bed5-267">À présent que les schémas de fichier plat sont définis, vous devez créer un pipeline de réception personnalisé qui utilise le composant Désassembleur de fichier plat.</span><span class="sxs-lookup"><span data-stu-id="0bed5-267">Now that the flat file schemas are defined, you need to create a custom pipeline that uses the Flat File Disassembler component.</span></span> <span data-ttu-id="0bed5-268">Le composant Désassembleur de fichier plat peut ensuite être configuré pour utiliser les schémas d'en-tête, de corps et de code de fin afin de scinder les messages.</span><span class="sxs-lookup"><span data-stu-id="0bed5-268">The Flat File Disassembler component can then be configured to use the header, body, and trailer schemas to break up messages.</span></span>    
 
1.  <span data-ttu-id="0bed5-269">Ajoutez un nouveau pipeline de réception au projet.</span><span class="sxs-lookup"><span data-stu-id="0bed5-269">Add a new receive pipeline to the project.</span></span> <span data-ttu-id="0bed5-270">Dans l’Explorateur de solutions, cliquez sur le **FFDisassemblerWalkthrough** de projet, pointez sur **ajouter**, puis cliquez sur **un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="0bed5-270">In Solution Explorer, right-click the **FFDisassemblerWalkthrough** project, point to **Add**, and then click **New Item**.</span></span>  
  
2.  <span data-ttu-id="0bed5-271">Dans le **ajouter un nouvel élément** boîte de dialogue, pointez sur **fichiers de Pipeline** puis cliquez sur **Pipeline de réception**.</span><span class="sxs-lookup"><span data-stu-id="0bed5-271">In the **Add New Item** dialog box, point to **Pipeline Files** and then click **Receive Pipeline**.</span></span> <span data-ttu-id="0bed5-272">Nommez le nouveau pipeline « FFReceivePipeline », puis **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="0bed5-272">Name the new pipeline "FFReceivePipeline" and then click **Add**.</span></span>  
  
3.  <span data-ttu-id="0bed5-273">Configurez le nouveau pipeline en faisant glisser le composant Désassembleur de fichier plat du volet Boîte à outils vers l'étape Désassembler.</span><span class="sxs-lookup"><span data-stu-id="0bed5-273">Configure the new pipeline by dragging the Flat File Disassembler component from the Toolbox pane to the Disassemble step.</span></span>  
  
4.  <span data-ttu-id="0bed5-274">Dans le volet Propriétés, définissez la **schéma de Document** à **FFDisassemblerWalkthrough.Body**, le **schéma d’en-tête** à  **FFDisassemblerWalkthrough.Header** et **schéma de code de fin** à **FFDisassemblerWalkthrough.Trailer**.</span><span class="sxs-lookup"><span data-stu-id="0bed5-274">In the Properties pane, set the **Document schema** to **FFDisassemblerWalkthrough.Body**, the **Header schema** to **FFDisassemblerWalkthrough.Header** and the **Trailer schema** to **FFDisassemblerWalkthrough.Trailer**.</span></span>  
  
### <a name="deploy-the-application-and-configure-the-send-and-receive-ports"></a><span data-ttu-id="0bed5-275">Déploiement de l'application et configuration des ports d'envoi et de réception</span><span class="sxs-lookup"><span data-stu-id="0bed5-275">Deploy the Application and Configure the Send and Receive Ports</span></span>  
 <span data-ttu-id="0bed5-276">Une fois les schémas et le pipeline de réception personnalisé créés, vous devez compiler et déployer le projet.</span><span class="sxs-lookup"><span data-stu-id="0bed5-276">With the schemas and custom receive pipeline created, you need to compile and deploy the project.</span></span> <span data-ttu-id="0bed5-277">Lorsque le projet est déployé, vous pouvez utiliser la console Administration de BizTalk Server pour configurer les ports d'envoi et de réception.</span><span class="sxs-lookup"><span data-stu-id="0bed5-277">After it is deployed, you can use the BizTalk Server Administration console to configure the send and receive ports.</span></span>  

##### <a name="deploy"></a><span data-ttu-id="0bed5-278">Déployer</span><span class="sxs-lookup"><span data-stu-id="0bed5-278">Deploy</span></span>  
1.  <span data-ttu-id="0bed5-279">Depuis [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], déployez la solution en cliquant sur le projet, puis cliquez sur **déployer**.</span><span class="sxs-lookup"><span data-stu-id="0bed5-279">From within [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], deploy the solution by right-clicking on the project and then clicking **Deploy**.</span></span>  
  
2.  <span data-ttu-id="0bed5-280">À l’aide de la console Administration de BizTalk Server, développez le **Applications** groupe pour vérifier que **FlatFileExample** est présent sous la forme d’une application personnalisée.</span><span class="sxs-lookup"><span data-stu-id="0bed5-280">Using the BizTalk Server Administration console, expand the **Applications** group to verify that **FlatFileExample** is present as a custom application.</span></span>  
  
##### <a name="configure-the-receive-port"></a><span data-ttu-id="0bed5-281">Configurer le port de réception</span><span class="sxs-lookup"><span data-stu-id="0bed5-281">Configure the receive port</span></span>  
  
1.  <span data-ttu-id="0bed5-282">Utilisez l’Explorateur Windows pour créer un répertoire nommé « Receive » sous le **FFDisassemblerWalkthrough** répertoire du projet.</span><span class="sxs-lookup"><span data-stu-id="0bed5-282">Use Windows Explorer to create a directory named "Receive" under the **FFDisassemblerWalkthrough** project directory.</span></span>  
  
2.  <span data-ttu-id="0bed5-283">Dans la console Administration de BizTalk Server, développez le **FlatFileExample** application, avec le bouton droit **Ports de réception**, pointez sur **nouveau**, puis cliquez sur **Unidirectionnel Port de réception**.</span><span class="sxs-lookup"><span data-stu-id="0bed5-283">In the BizTalk Server Administration console, expand the **FlatFileExample** application, right-click **Receive Ports**, point to **New**, and then click **One-way Receive Port**.</span></span>  
  
3.  <span data-ttu-id="0bed5-284">Dans le **propriétés du Port de réception** boîte de dialogue, définissez le nom du port sur « ReceiveError ».</span><span class="sxs-lookup"><span data-stu-id="0bed5-284">In the **Receive Port Properties** dialog box, set the name of the port to "ReceiveError".</span></span>  
  
4.  <span data-ttu-id="0bed5-285">Cliquez sur **emplacements de réception**, puis cliquez sur **nouveau** pour ajouter un emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="0bed5-285">Click **Receive Locations**, and then click **New** to add a receive location.</span></span> <span data-ttu-id="0bed5-286">Nommez le nouvel emplacement « ReceiveErrorLocation ».</span><span class="sxs-lookup"><span data-stu-id="0bed5-286">Name the new receive location "ReceiveErrorLocation".</span></span> <span data-ttu-id="0bed5-287">Définir le **Pipeline de réception** à **FFReceivePipeline**.</span><span class="sxs-lookup"><span data-stu-id="0bed5-287">Set the **Receive Pipeline** to **FFReceivePipeline**.</span></span> <span data-ttu-id="0bed5-288">Pour **Type de Transport**, sélectionnez **fichier**, puis cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="0bed5-288">For **Transport Type**, select **FILE**, and then click **Configure**.</span></span> <span data-ttu-id="0bed5-289">Sélectionnez le répertoire de réception que vous avez créé et puis définissez la **masque de fichier** \*.txt.</span><span class="sxs-lookup"><span data-stu-id="0bed5-289">Select the receive directory you created, and then set the **File mask** to \*.txt.</span></span>  
  
5.  <span data-ttu-id="0bed5-290">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="0bed5-290">Click **OK**.</span></span> <span data-ttu-id="0bed5-291">Votre port de réception devrait à présent être configuré.</span><span class="sxs-lookup"><span data-stu-id="0bed5-291">Your receive port should now be configured.</span></span> <span data-ttu-id="0bed5-292">Cliquez sur **OK** à fermer.</span><span class="sxs-lookup"><span data-stu-id="0bed5-292">Click **OK** to close.</span></span>  
  
##### <a name="configure-the-send-port"></a><span data-ttu-id="0bed5-293">Configurer le port d’envoi</span><span class="sxs-lookup"><span data-stu-id="0bed5-293">Configure the send port</span></span>  
  
1.  <span data-ttu-id="0bed5-294">Utilisez l’Explorateur Windows pour créer un répertoire nommé « Send » sous le **FFDisassemblerWalkthrough** répertoire du projet.</span><span class="sxs-lookup"><span data-stu-id="0bed5-294">Use Windows Explorer to create a directory named "Send" under the **FFDisassemblerWalkthrough** project directory.</span></span>  
  
2.  <span data-ttu-id="0bed5-295">Dans la console Administration de BizTalk Server, développez le **FlatFileExample** application, avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi unidirectionnel statique...**.</span><span class="sxs-lookup"><span data-stu-id="0bed5-295">In the BizTalk Server Administration console, expand the **FlatFileExample** application, right-click **Send Ports**, point to **New**, and then click **Static One-Way  Send Port…**.</span></span>  
  
3.  <span data-ttu-id="0bed5-296">Dans le **propriétés de Port d’envoi** boîte de dialogue, définissez le nom du port sur « Send ».</span><span class="sxs-lookup"><span data-stu-id="0bed5-296">In the **Send Port Properties** dialog box, set the name of the port to "Send".</span></span>  
  
4.  <span data-ttu-id="0bed5-297">Pour le type de transport, sélectionnez **fichier**, puis cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="0bed5-297">For transport type, select **FILE**, and then click **Configure**.</span></span> <span data-ttu-id="0bed5-298">Définissez le dossier de destination sur le répertoire d'envoi que vous avez créé auparavant.</span><span class="sxs-lookup"><span data-stu-id="0bed5-298">Set the destination folder to the send directory you created earlier.</span></span>  
  
5.  <span data-ttu-id="0bed5-299">Configurez à présent le filtre.</span><span class="sxs-lookup"><span data-stu-id="0bed5-299">Now configure the filter.</span></span> <span data-ttu-id="0bed5-300">Cliquez sur **filtres** et ajouter une expression :</span><span class="sxs-lookup"><span data-stu-id="0bed5-300">Click **Filters** and add one expression:</span></span>  
  
    -   <span data-ttu-id="0bed5-301">BTS.MessageType == **http://FFDisassemblerWalkthrough.Body#Body**</span><span class="sxs-lookup"><span data-stu-id="0bed5-301">BTS.MessageType == **http://FFDisassemblerWalkthrough.Body#Body**</span></span>  
  
6.  <span data-ttu-id="0bed5-302">Cliquez sur **OK** pour terminer la configuration de port d’envoi.</span><span class="sxs-lookup"><span data-stu-id="0bed5-302">Click **OK** to complete the send port configuration.</span></span> <span data-ttu-id="0bed5-303">Votre port d'envoi devrait à présent être configuré.</span><span class="sxs-lookup"><span data-stu-id="0bed5-303">Your send port should be configured.</span></span>  
  
### <a name="run-the-example"></a><span data-ttu-id="0bed5-304">Exécution de l'exemple</span><span class="sxs-lookup"><span data-stu-id="0bed5-304">Run the Example</span></span>  
 <span data-ttu-id="0bed5-305">Il est maintenant temps d'exécuter l'exemple.</span><span class="sxs-lookup"><span data-stu-id="0bed5-305">It is now time to run the example.</span></span> <span data-ttu-id="0bed5-306">Après avoir utilisé la console Administration de BizTalk Server pour démarrer l’application, copiez les fichiers de test à l’emplacement de réception et observez le résultat produit dans l’emplacement d’envoi.</span><span class="sxs-lookup"><span data-stu-id="0bed5-306">After using the BizTalk Server Management console to start the application, copy the test files to the receive location and observe what is produced in the send location.</span></span>  
  
1.  <span data-ttu-id="0bed5-307">Dans la console Administration de BizTalk Server, cliquez sur le **FlatFileExample** application, puis sur **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="0bed5-307">In the BizTalk Server Administration console, right-click the **FlatFileExample** application, and then click **Start**.</span></span> <span data-ttu-id="0bed5-308">Il inscrit et démarre l’envoi et ports de réception.</span><span class="sxs-lookup"><span data-stu-id="0bed5-308">This enlists and starts the send and receive ports.</span></span>  
  
2.  <span data-ttu-id="0bed5-309">Faites glisser la copie de l'exemple de fichier Errorfile.txt dans le répertoire de réception.</span><span class="sxs-lookup"><span data-stu-id="0bed5-309">Drop the copy of the sample Errorfile.txt into the receive directory.</span></span> <span data-ttu-id="0bed5-310">Deux fichiers de sortie sont normalement écrits dans le répertoire d'envoi.</span><span class="sxs-lookup"><span data-stu-id="0bed5-310">Two output files should be written to the send directory.</span></span>  
  
