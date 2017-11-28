---
title: "Procédure pas à pas : Module 2 - intégration d’Office avec Windows SharePoint Services adaptateur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows SharePoint Services adapters, InfoPath forms
- InfoPath forms, creating
- InfoPath forms, Windows SharePoint Services adapters
- tutorials, Windows SharePoint Services adapters
- Windows SharePoint Services adapter tutorials, integrating Microsoft Office
- Windows SharePoint Services, document libraries
ms.assetid: 2f81a712-bb20-4c32-bbac-fb438deded38
caps.latest.revision: "48"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 64e23cef8b362accba726c60945548a3345c9c45
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="walkthrough-module-2---integrating-office-with-the-windows-sharepoint-services-adapter"></a><span data-ttu-id="aa9a6-102">Procédure pas à pas : Module 2 - intégration d’Office avec l’adaptateur Windows SharePoint Services</span><span class="sxs-lookup"><span data-stu-id="aa9a6-102">Walkthrough: Module 2 - Integrating Office with the Windows SharePoint Services Adapter</span></span>
<span data-ttu-id="aa9a6-103">Cette procédure pas à pas est la suite de [procédure pas à pas : Module 1 - envoi et réception de Messages avec l’adaptateur Windows SharePoint Services](../core/walkthrough-module-1--send-and-receive-messages-with-the-sharepoint-adapter.md) et vous montre comment intégrer Microsoft Office à le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] en fonction du contenu application de routage (CBR) vous avez créé.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-103">This walkthrough is a continuation of [Walkthrough: Module 1 - Sending and Receiving Messages with the Windows SharePoint Services Adapter](../core/walkthrough-module-1--send-and-receive-messages-with-the-sharepoint-adapter.md) and shows you how to integrate Microsoft Office with the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] content-based routing (CBR) application you created.</span></span> <span data-ttu-id="aa9a6-104">Pour une présentation de l’adaptateur Windows SharePoint Services, consultez [quel est l’adaptateur Windows SharePoint Services ?](../core/what-is-the-windows-sharepoint-services-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="aa9a6-104">For an introduction to the Windows SharePoint Services adapter see [What Is the Windows SharePoint Services Adapter?](../core/what-is-the-windows-sharepoint-services-adapter.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="aa9a6-105">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="aa9a6-105">Prerequisites</span></span>  
 <span data-ttu-id="aa9a6-106">La configuration suivante est requise pour exécuter les procédures décrites dans cette rubrique :</span><span class="sxs-lookup"><span data-stu-id="aa9a6-106">The following are prerequisites for performing the procedures in this topic:</span></span>  
  
-   <span data-ttu-id="aa9a6-107">Vous devez avoir un déploiement sur un seul serveur avec une installation complète de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="aa9a6-107">You must have a single-server deployment with a complete installation of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="aa9a6-108">Vous devez effectuer la procédure suivante : [procédure pas à pas : Module 1 - envoi et réception de Messages avec l’adaptateur Windows SharePoint Services](../core/walkthrough-module-1--send-and-receive-messages-with-the-sharepoint-adapter.md)</span><span class="sxs-lookup"><span data-stu-id="aa9a6-108">You must complete the following walkthrough: [Walkthrough: Module 1 - Sending and Receiving Messages with the Windows SharePoint Services Adapter](../core/walkthrough-module-1--send-and-receive-messages-with-the-sharepoint-adapter.md)</span></span>  
  
 <span data-ttu-id="aa9a6-109">Pour plus d’informations sur l’utilisation de l’adaptateur Windows SharePoint Services dans un déploiement multiserveur, consultez [configuration et déploiement de l’adaptateur Windows SharePoint Services](../core/setting-up-and-deploying-the-windows-sharepoint-services-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="aa9a6-109">For information about using the Windows SharePoint Services Adapter in a multiserver deployment, see [Setting Up and Deploying the Windows SharePoint Services Adapter](../core/setting-up-and-deploying-the-windows-sharepoint-services-adapter.md).</span></span>  
  
## <a name="create-a-biztalk-project"></a><span data-ttu-id="aa9a6-110">Création d'un projet BizTalk</span><span class="sxs-lookup"><span data-stu-id="aa9a6-110">Create a BizTalk project</span></span>  
 <span data-ttu-id="aa9a6-111">Cette procédure permet de créer un projet BizTalk vide et un schéma à l'aide de l'Éditeur BizTalk.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-111">In this procedure you create an empty BizTalk project and a schema using the BizTalk Editor.</span></span> <span data-ttu-id="aa9a6-112">Elle est requise pour créer le schéma du formulaire InfoPath qui sera utilisé ultérieurement.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-112">This procedure is required to create the schema for the InfoPath form that is used later.</span></span>  
  
#### <a name="create-a-strong-name-key-file"></a><span data-ttu-id="aa9a6-113">Pour créer un fichier de clé de nom fort</span><span class="sxs-lookup"><span data-stu-id="aa9a6-113">Create a strong name key file</span></span>  
  
1.  <span data-ttu-id="aa9a6-114">Démarrer **invite de commandes Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-114">Start **Visual Studio Command Prompt**.</span></span>  
  
2.  <span data-ttu-id="aa9a6-115">Type `sn -k C:\WSSAdapterWalkthrough\OrderProcess.snk`, puis appuyez sur **entrée**.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-115">Type `sn -k C:\WSSAdapterWalkthrough\OrderProcess.snk`, and then press **Enter**.</span></span> <span data-ttu-id="aa9a6-116">La paire de clés est alors écrite.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-116">The key pair will be written.</span></span>  
  
3.  <span data-ttu-id="aa9a6-117">Fermez l'invite de commande.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-117">Close the command prompt.</span></span>  
  
#### <a name="create-an-empty-biztalk-project"></a><span data-ttu-id="aa9a6-118">Créer un projet BizTalk vide</span><span class="sxs-lookup"><span data-stu-id="aa9a6-118">Create an empty BizTalk project</span></span>  
  
1.  <span data-ttu-id="aa9a6-119">Démarrer **Microsoft Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-119">Start **Microsoft Visual Studio**.</span></span>  
  
2.  <span data-ttu-id="aa9a6-120">Cliquez sur **fichier**, **nouveau**, puis cliquez sur **projet**.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-120">Click **File**, **New**, and then click **Project**.</span></span>  
  
3.  <span data-ttu-id="aa9a6-121">Sous **types de projet**, sélectionnez **projets BizTalk**.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-121">Under **Project types**, select **BizTalk Projects**.</span></span>  
  
4.  <span data-ttu-id="aa9a6-122">Sous **modèles**, sélectionnez **projet BizTalk Server vide**.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-122">Under **Templates**, select **Empty BizTalk Server Project**.</span></span>  
  
5.  <span data-ttu-id="aa9a6-123">Type `OrderProcess` dans les **nom** champ.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-123">Type `OrderProcess` in the **Name** field.</span></span>  
  
6.  <span data-ttu-id="aa9a6-124">Tapez le chemin d’accès de fichier dans votre répertoire de travail dans le **emplacement** champ.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-124">Type the file path to your working directory in the **Location** field.</span></span> <span data-ttu-id="aa9a6-125">Par exemple, `C:\WSSAdapterWalkthrough\`.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-125">For example, `C:\WSSAdapterWalkthrough\`.</span></span>  
  
7.  <span data-ttu-id="aa9a6-126">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-126">Click **OK**.</span></span>  
  
#### <a name="associate-the-key-file-with-the-assembly"></a><span data-ttu-id="aa9a6-127">Pour associer le fichier de clé à l'assembly</span><span class="sxs-lookup"><span data-stu-id="aa9a6-127">Associate the key file with the assembly</span></span>  
  
1.  <span data-ttu-id="aa9a6-128">Dans l’Explorateur de solutions, cliquez sur le `OrderProcess` de projet, puis cliquez sur **propriétés** pour lancer le Concepteur de projet.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-128">In Solution Explorer, right-click the `OrderProcess` project, and then click **Properties** to launch the Project Designer.</span></span>  
  
2.  <span data-ttu-id="aa9a6-129">Cliquez sur l'onglet **Signature** .</span><span class="sxs-lookup"><span data-stu-id="aa9a6-129">Click the **Signing** tab.</span></span>  
  
3.  <span data-ttu-id="aa9a6-130">Sélectionnez l'option **Signer l'assembly** , cliquez sur l'option **Choisir un fichier de clé de nom fort** dans la liste déroulante, puis sur **Parcourir**.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-130">Select **Sign the assembly** option, click drop-down list for the **Choose a strong name key file** option, and then click **Browse**.</span></span>  
  
4.  <span data-ttu-id="aa9a6-131">Tapez `C:\WSSAdapterWalkthrough\OrderProcess.snk`.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-131">Type `C:\WSSAdapterWalkthrough\OrderProcess.snk`.</span></span>  
  
5.  <span data-ttu-id="aa9a6-132">Cliquez sur **Ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-132">Click **Open**.</span></span>  
  
#### <a name="create-an-xsd-schema-by-using-the-biztalk-editor"></a><span data-ttu-id="aa9a6-133">Pour créer un schéma XSD à l'aide de l'Éditeur BizTalk</span><span class="sxs-lookup"><span data-stu-id="aa9a6-133">Create an XSD schema by using the BizTalk Editor</span></span>  
  
1.  <span data-ttu-id="aa9a6-134">Dans l’Explorateur de solutions, cliquez sur le `OrderProcess` de projet, cliquez sur **ajouter**, puis cliquez sur **un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-134">In Solution Explorer, right-click the `OrderProcess` project, click **Add**, and then click **New Item**.</span></span>  
  
2.  <span data-ttu-id="aa9a6-135">Sous **catégories**, cliquez sur **les fichiers de schéma**.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-135">Under **Categories**, click **Schema Files**.</span></span>  
  
3.  <span data-ttu-id="aa9a6-136">Sous **modèles**, cliquez sur **schéma**.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-136">Under **Templates**, click **Schema**.</span></span>  
  
4.  <span data-ttu-id="aa9a6-137">Type `OrderProcessSchema` dans les **nom** champ, puis cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-137">Type `OrderProcessSchema` in the **Name** field, and then click **Add**.</span></span>  
  
5.  <span data-ttu-id="aa9a6-138">Dans la fenêtre Propriétés pour `OrderProcessSchema`, sélectionnez `Qualified` pour le **Element FormDefault** propriété.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-138">In the Properties Window for `OrderProcessSchema`, select `Qualified` for the **Element FormDefault** property.</span></span>  
  
6.  <span data-ttu-id="aa9a6-139">Dans la fenêtre Propriétés pour `OrderProcessSchema`, type `http://OrderProcess.PurchaseOrder` dans les **cible Namespace** champ.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-139">In the Properties Window for `OrderProcessSchema`, type `http://OrderProcess.PurchaseOrder` in the **Target Namespace** field.</span></span>  
  
7.  <span data-ttu-id="aa9a6-140">Dans le **l’Éditeur BizTalk**, avec le bouton droit `Root`, cliquez sur **renommer**, puis tapez `PurchaseOrder`.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-140">In the **BizTalk Editor**, right-click `Root`, click **Rename**, and then type `PurchaseOrder`.</span></span>  
  
8.  <span data-ttu-id="aa9a6-141">Cliquez sur le **PurchaseOrder** nœud, cliquez sur **insérer un nœud de schéma**, puis cliquez sur **élément de champ enfant**.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-141">Right-click the **PurchaseOrder** node, click **Insert Schema Node**, then click **Child Field Element**.</span></span>  
  
9. <span data-ttu-id="aa9a6-142">Nommez-le `PurchaseOrderID`.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-142">Name it `PurchaseOrderID`.</span></span>  
  
10. <span data-ttu-id="aa9a6-143">Créez un autre élément de champ enfant et nommez-le `BillTo`.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-143">Create another child field element and name it `BillTo`.</span></span>  
  
11. <span data-ttu-id="aa9a6-144">Créez un autre élément de champ enfant et nommez-le `Amount`.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-144">Create another child field element and name it `Amount`.</span></span>  
  
12. <span data-ttu-id="aa9a6-145">Dans la fenêtre Propriétés, définissez la **Type de données** propriété `Amount` à xs : unsignedInt.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-145">In the Properties Window, set the **Data Type** property for `Amount` to xs:unsignedInt.</span></span>  
  
13. <span data-ttu-id="aa9a6-146">Créez un autre élément de champ enfant et nommez-le `PurchaseOrderDate`.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-146">Create another child field element and name it `PurchaseOrderDate`.</span></span>  
  
14. <span data-ttu-id="aa9a6-147">Dans la fenêtre Propriétés, définissez la **Type de données** propriété `PurchaseOrderDate` à xs : DateTime.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-147">In the Properties Window, set the **Data Type** property for `PurchaseOrderDate` to xs:dateTime.</span></span>  
  
15. <span data-ttu-id="aa9a6-148">Cliquez sur **fichier**, puis cliquez sur **Enregistrer tout**.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-148">Click **File**, and then click **Save All**.</span></span>  
  
16. <span data-ttu-id="aa9a6-149">Fermez [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="aa9a6-149">Close [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span></span>  
  
## <a name="create-an-infopath-form"></a><span data-ttu-id="aa9a6-150">Création d'un formulaire InfoPath</span><span class="sxs-lookup"><span data-stu-id="aa9a6-150">Create an InfoPath form</span></span>  
 <span data-ttu-id="aa9a6-151">Cette procédure permet de créer une autre bibliothèque de documents et un formulaire InfoPath à partir du schéma créé dans la procédure précédente.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-151">In this procedure you create another document library and an InfoPath form based on the schema you created in the last procedure.</span></span> <span data-ttu-id="aa9a6-152">Ce formulaire InfoPath sera utilisé pour envoyer un document à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="aa9a6-152">This InfoPath form will be used to submit a document to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="aa9a6-153">Cette procédure pas à pas requiert Microsoft Office InfoPath 2007.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-153">This walkthrough requires Microsoft Office InfoPath 2007</span></span>  
  
#### <a name="create-a-new-document-library"></a><span data-ttu-id="aa9a6-154">Pour créer une bibliothèque de documents</span><span class="sxs-lookup"><span data-stu-id="aa9a6-154">Create a new document library</span></span>  
  
1.  <span data-ttu-id="aa9a6-155">Ouvrez un navigateur Web, puis accédez à l'URL du site que vous avez créé</span><span class="sxs-lookup"><span data-stu-id="aa9a6-155">Open a Web browser and navigate to the URL of the site you created.</span></span> <span data-ttu-id="aa9a6-156">Par exemple, `http://<server_name>/sites/WSSAdapterWalkthrough`.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-156">For example, `http://<server_name>/sites/WSSAdapterWalkthrough`.</span></span>  
  
2.  <span data-ttu-id="aa9a6-157">Dans la barre de navigation supérieure, cliquez sur **créer**.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-157">On the top navigation bar, click **Create**.</span></span>  
  
3.  <span data-ttu-id="aa9a6-158">Sous **bibliothèques de documents**, cliquez sur **bibliothèque de documents**.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-158">Under **Document Libraries**, click **Document Library**.</span></span>  
  
4.  <span data-ttu-id="aa9a6-159">Dans le **nom et Description** , tapez `InfoPathSolutions` dans les **champ nom**.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-159">In the **Name and Description** section, type `InfoPathSolutions` in the **Name field**.</span></span>  
  
5.  <span data-ttu-id="aa9a6-160">Dans le **Navigation** section, sélectionnez **Oui** pour afficher cette bibliothèque de formulaires dans la barre de lancement rapide.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-160">In the **Navigation** section, select **Yes** to display this form library on the Quick Launch bar.</span></span>  
  
6.  <span data-ttu-id="aa9a6-161">Dans le **modèle de Document** section, sélectionnez `None` pour le **modèle de Document**.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-161">In the **Document Template** section, select `None` for the **Document Template**.</span></span>  
  
7.  <span data-ttu-id="aa9a6-162">Cliquez sur **Créer**.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-162">Click **Create**.</span></span> <span data-ttu-id="aa9a6-163">Vous êtes alors redirigé vers la bibliothèque vide que vous venez de créer.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-163">You will be redirected to the empty library you just created.</span></span>  
  
8.  <span data-ttu-id="aa9a6-164">Sur le côté gauche, cliquez sur **modifier les paramètres et les colonnes**.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-164">On the left side, click **Modify Settings and Columns**.</span></span>  
  
9. <span data-ttu-id="aa9a6-165">Sous **colonnes**, cliquez sur **ajouter une nouvelle colonne**.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-165">Under **Columns**, click **Add a New Column**.</span></span>  
  
10. <span data-ttu-id="aa9a6-166">Sous **nom et le Type**, type `Namespace` dans les **nom** champ.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-166">Under **Name and Type**, type `Namespace` in the **Name** field.</span></span>  
  
11. <span data-ttu-id="aa9a6-167">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-167">Click **OK**.</span></span>  
  
12. <span data-ttu-id="aa9a6-168">Fermez le site Web `WSSAdapterWalkthrough`.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-168">Close the `WSSAdapterWalkthrough` Web site.</span></span>  
  
#### <a name="create-an-infopath-form-based-on-the-orderprocessschema-schema-file"></a><span data-ttu-id="aa9a6-169">Pour créer un formulaire InfoPath à partir du fichier de schéma OrderProcessSchema</span><span class="sxs-lookup"><span data-stu-id="aa9a6-169">Create an InfoPath form based on the OrderProcessSchema schema file</span></span>  
  
1.  <span data-ttu-id="aa9a6-170">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft Office**, puis cliquez sur **Microsoft Office InfoPath 2007**.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-170">Click **Start**, point to **All Programs**, point to **Microsoft Office**, and then click **Microsoft Office InfoPath 2007**.</span></span>  
  
2.  <span data-ttu-id="aa9a6-171">Dans le **remplir un formulaire** boîte de dialogue, sélectionnez **concevoir un formulaire.**</span><span class="sxs-lookup"><span data-stu-id="aa9a6-171">In the **Fill Out a Form** dialog box, select **Design a Form.**</span></span>  
  
3.  <span data-ttu-id="aa9a6-172">Dans le **concevoir un formulaire** volet des tâches, sélectionnez **nouveau à partir de Document ou schéma XML**.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-172">In the **Design a Form** task pane, select **New from XML Document or Schema**.</span></span>  
  
4.  <span data-ttu-id="aa9a6-173">Dans le **Assistant Source de données**, cliquez sur **Parcourir** et sélectionnez le fichier de schéma que vous avez créé dans la dernière procédure.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-173">In the **Data Source Wizard**, click **Browse** and select the schema file you created in the last procedure.</span></span> <span data-ttu-id="aa9a6-174">Par exemple, `C:\WSSAdapterWalkthrough\OrderProcess\OrderProcess\OrderProcessSchema.xsd`.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-174">For example, `C:\WSSAdapterWalkthrough\OrderProcess\OrderProcess\OrderProcessSchema.xsd`.</span></span>  
  
5.  <span data-ttu-id="aa9a6-175">Cliquez sur **Suivant**, puis sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-175">Click **Next**, and then click **Finish**.</span></span>  
  
6.  <span data-ttu-id="aa9a6-176">Dans le **Source de données** volet de tâches, cliquez sur le **PurchaseOrder** nœud, puis cliquez sur **Section avec contrôles**.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-176">In the **Data Source** task pane, right-click the **PurchaseOrder** node, and then click **Section with Controls**.</span></span> <span data-ttu-id="aa9a6-177">Cette opération crée le formulaire à partir du modèle.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-177">This will create the form on the template.</span></span>  
  
7.  <span data-ttu-id="aa9a6-178">Cliquez sur **fichier**, cliquez sur **enregistrer**, puis cliquez sur **enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-178">Click **File**, click **Save**, and then click **Save**.</span></span>  
  
8.  <span data-ttu-id="aa9a6-179">Dans le **enregistrer en tant que** boîte de dialogue, tapez `PurchaseOrder.xsn` dans les **nom de fichier** champ, puis cliquez sur **enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-179">In the **Save As** dialog box, type `PurchaseOrder.xsn` in the **File name** field, and then click **Save**.</span></span>  
  
9. <span data-ttu-id="aa9a6-180">Cliquez sur **fichier**, puis cliquez sur **publier**.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-180">Click **File**, and then click **Publish**.</span></span>  
  
10. <span data-ttu-id="aa9a6-181">Dans le **l’Assistant Publication de**, cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-181">In the **Publishing Wizard**, click **Next**.</span></span>  
  
11. <span data-ttu-id="aa9a6-182">Sélectionnez **vers un serveur Web**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-182">Select **To a Web Server**, and then click **Next**.</span></span>  
  
12. <span data-ttu-id="aa9a6-183">Tapez le chemin d’accès et le nom de fichier à votre `InfoPathSolutions` bibliothèque de documents, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-183">Type the path and filename to your `InfoPathSolutions` document library, and then click **Next**.</span></span> <span data-ttu-id="aa9a6-184">Par exemple, `http://<server_name>/sites/WSSAdapterWalkthrough/InfoPathSolutions/PurchaseOrder.xsn`.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-184">For example, `http://<server_name>/sites/WSSAdapterWalkthrough/InfoPathSolutions/PurchaseOrder.xsn`.</span></span>  
  
13. <span data-ttu-id="aa9a6-185">Cliquez sur **Terminer**, puis cliquez sur **fermer**.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-185">Click **Finish**, and then click **Close**.</span></span>  
  
14. <span data-ttu-id="aa9a6-186">Fermez Microsoft InfoPath.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-186">Close Microsoft InfoPath.</span></span>  
  
## <a name="modify-the-sharepoint-document-libraries"></a><span data-ttu-id="aa9a6-187">Modification des bibliothèques de documents SharePoint</span><span class="sxs-lookup"><span data-stu-id="aa9a6-187">Modify the SharePoint document libraries</span></span>  
 <span data-ttu-id="aa9a6-188">Cette procédure permet de mettre à jour la propriété d'espace de noms pour le fichier PurchaseOrder.xsn et de modifier la bibliothèque de documents de destination.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-188">In this procedure you will update the namespace property for the PurchaseOrder.xsn file and modify the Destination Document Library.</span></span> <span data-ttu-id="aa9a6-189">Cet espace de noms sert de variable lors de l'identification des abonnés aux documents publiés pour les scénarios de routage basé sur le contenu.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-189">This namespace is used as a variable when determining subscribers of published documents for content based routing scenarios.</span></span>  
  
#### <a name="update-the-namespace-for-purchaseorderxsn"></a><span data-ttu-id="aa9a6-190">Pour mettre à jour l'espace de noms pour PurchaseOrder.xsn</span><span class="sxs-lookup"><span data-stu-id="aa9a6-190">Update the namespace for PurchaseOrder.xsn</span></span>  
  
1.  <span data-ttu-id="aa9a6-191">Ouvrez un navigateur Web, puis accédez à l'URL du site que vous avez créé</span><span class="sxs-lookup"><span data-stu-id="aa9a6-191">Open a Web browser and navigate to the URL of the site you created.</span></span> <span data-ttu-id="aa9a6-192">Par exemple, `http://<server_name>/sites/WSSAdapterWalkthrough`.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-192">For example, `http://<server_name>/sites/WSSAdapterWalkthrough`.</span></span>  
  
2.  <span data-ttu-id="aa9a6-193">Sur le côté gauche, sous **Documents**, cliquez sur `InfoPathSolutions`.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-193">On the left side, under **Documents**, click `InfoPathSolutions`.</span></span>  
  
3.  <span data-ttu-id="aa9a6-194">Déplacez le pointeur sur `PurchaseOrder.xsn`, faites un clic droit, puis cliquez sur **modifier les propriétés de**.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-194">Move the pointer over `PurchaseOrder.xsn`, right-click it, and then click **Edit Properties**.</span></span>  
  
4.  <span data-ttu-id="aa9a6-195">Type `http://OrderProcess.PurchaseOrder` dans les **Namespace** champ, puis cliquez sur **enregistrer et fermer**.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-195">Type `http://OrderProcess.PurchaseOrder` in the **Namespace** field, and then click **Save and Close**.</span></span>  
  
#### <a name="modify-the-destination-document-library"></a><span data-ttu-id="aa9a6-196">Pour modifier la bibliothèque de documents de destination</span><span class="sxs-lookup"><span data-stu-id="aa9a6-196">Modify the Destination document library</span></span>  
  
1.  <span data-ttu-id="aa9a6-197">Dans la barre de navigation supérieure, cliquez sur **Documents et listes**.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-197">On the top navigation bar, click **Documents and Lists**.</span></span>  
  
2.  <span data-ttu-id="aa9a6-198">Sous **bibliothèques de documents**, cliquez sur **Destination**.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-198">Under **Document Libraries**, click **Destination**.</span></span>  
  
3.  <span data-ttu-id="aa9a6-199">Sur le côté gauche, cliquez sur **modifier les paramètres et les colonnes**.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-199">On the left side, click **Modify Settings and Columns**.</span></span>  
  
4.  <span data-ttu-id="aa9a6-200">Sous **colonnes**, cliquez sur **ajouter une nouvelle colonne**.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-200">Under **Columns**, click **Add New Column**.</span></span>  
  
5.  <span data-ttu-id="aa9a6-201">Sous **nom et le Type**, type `Partner Name` dans les **nom de la colonne** champ.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-201">Under **Name and Type**, type `Partner Name` in the **Column name** field.</span></span>  
  
6.  <span data-ttu-id="aa9a6-202">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-202">Click **OK**.</span></span>  
  
7.  <span data-ttu-id="aa9a6-203">Fermez le site Web `WSSAdapterWalkthrough`.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-203">Close the `WSSAdapterWalkthrough` Web site.</span></span>  
  
## <a name="modify-the-send-port-from-walkthrough-1"></a><span data-ttu-id="aa9a6-204">Modification du port d'envoi à partir de la procédure pas à pas 1</span><span class="sxs-lookup"><span data-stu-id="aa9a6-204">Modify the send port from walkthrough 1</span></span>  
 <span data-ttu-id="aa9a6-205">Cette procédure permet de modifier le port d'envoi à partir de la procédure pas à pas 1.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-205">In this procedure you modify the send port from walkthrough 1.</span></span> <span data-ttu-id="aa9a6-206">Elle est requise pour garantir l'acheminement correct vers le port d'envoi du document traité dans cette procédure pas à pas.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-206">This procedure is required to ensure that the document processed in this walkthrough is correctly routed to the send port.</span></span>  
  
#### <a name="modify-the-send-port"></a><span data-ttu-id="aa9a6-207">Modification du port d'envoi</span><span class="sxs-lookup"><span data-stu-id="aa9a6-207">Modify the send port</span></span>  
  
1.  <span data-ttu-id="aa9a6-208">Ouvrez **Administration de BizTalk Server.**</span><span class="sxs-lookup"><span data-stu-id="aa9a6-208">Open **BizTalk Server Administration.**</span></span>  
  
2.  <span data-ttu-id="aa9a6-209">Développez **Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration**, développez **groupe BizTalk**, développez **Applications**, développez **BizTalk Application 1**, puis cliquez sur le **Ports d’envoi** nœud.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-209">Expand **Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration**, expand **BizTalk Group**, expand **Applications**, expand **BizTalk Application 1**, and then click the **Send Ports** node.</span></span>  
  
3.  <span data-ttu-id="aa9a6-210">Avec le bouton droit `SendToDestination`, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-210">Right-click `SendToDestination`, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="aa9a6-211">Sous **Transport**, cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-211">Under **Transport**, click **Configure**.</span></span>  
  
5.  <span data-ttu-id="aa9a6-212">Dans le **nom de fichier** , tapez `PurchaseOrder2-%XPATH=//pons:PurchaseOrder/pons:PurchaseOrderID%.xml`.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-212">In the **Filename** field, type `PurchaseOrder2-%XPATH=//pons:PurchaseOrder/pons:PurchaseOrderID%.xml`.</span></span>  
  
6.  <span data-ttu-id="aa9a6-213">Dans le **Namespace alias** , tapez `pons="http://OrderProcess.PurchaseOrder"`.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-213">In the **Namespace Aliases** field, type `pons="http://OrderProcess.PurchaseOrder"`.</span></span>  
  
7.  <span data-ttu-id="aa9a6-214">Dans le **bibliothèque de documents modèles**, type `InfoPathSolutions`.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-214">In the **Templates Document Library**, type `InfoPathSolutions`.</span></span>  
  
8.  <span data-ttu-id="aa9a6-215">Dans le **modèles Namespace colonne**, type `Namespace`.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-215">In the **Templates Namespace Column**, type `Namespace`.</span></span>  
  
9. <span data-ttu-id="aa9a6-216">Sélectionnez `Yes` pour le **intégration de Microsoft Office** propriété.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-216">Select `Yes` for the **Microsoft Office Integration** property.</span></span>  
  
10. <span data-ttu-id="aa9a6-217">Sous **l’intégration de Windows SharePoint Services**, type `Partner Name` dans les **colonne 01** champ.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-217">Under **Windows SharePoint Services Integration**, type `Partner Name` in the **Column 01** field.</span></span>  
  
11. <span data-ttu-id="aa9a6-218">Type `%XPATH=//pons:PurchaseOrder/pons:BillTo%` dans les **valeur colonne 01** , cliquez sur **OK**, puis cliquez sur **OK** pour quitter le **propriétés de Port d’envoi** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-218">Type `%XPATH=//pons:PurchaseOrder/pons:BillTo%` in the **Column 01 Value** field, click **OK**, and then click **OK** again to exit the **Send Port Properties** dialog box.</span></span>  
  
#### <a name="restart-the-send-port"></a><span data-ttu-id="aa9a6-219">Pour redémarrer le port d'envoi</span><span class="sxs-lookup"><span data-stu-id="aa9a6-219">Restart the send port</span></span>  
  
1.  <span data-ttu-id="aa9a6-220">Dans le **Console Administration de BizTalk**, cliquez sur le **Ports d’envoi** nœud.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-220">In the **BizTalk Administration Console**, click the **Send Ports** node.</span></span>  
  
2.  <span data-ttu-id="aa9a6-221">Avec le bouton droit `SendToDestination`, puis cliquez sur **désinscrire**.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-221">Right-click `SendToDestination`, and then click **Unenlist**.</span></span>  
  
3.  <span data-ttu-id="aa9a6-222">Avec le bouton droit `SendToDestination`, puis cliquez sur **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-222">Right-click `SendToDestination`, and then click **Start**.</span></span>  
  
4.  <span data-ttu-id="aa9a6-223">Fermer le **Console Administration de BizTalk**.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-223">Close the **BizTalk Administration Console**.</span></span>  
  
## <a name="send-a-message-through-the-system"></a><span data-ttu-id="aa9a6-224">Envoi d'un message via le système</span><span class="sxs-lookup"><span data-stu-id="aa9a6-224">Send a message through the system</span></span>  
 <span data-ttu-id="aa9a6-225">Dans cette procédure, vous allez créer un formulaire InfoPath et le télécharger sur le site Web Windows SharePoint Services.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-225">In this procedure you create an InfoPath form and upload it to the Windows SharePoint Services Web site.</span></span> <span data-ttu-id="aa9a6-226">L'adaptateur Windows SharePoint Services prend ce message, l'archive dans la bibliothèque de documents d'archive, puis l'envoie dans la bibliothèque de documents de destination.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-226">The Windows SharePoint Services adapter will take that message, archive it in the Archive document library, and then send it to the Destination document library.</span></span> <span data-ttu-id="aa9a6-227">Cette procédure montre comment un document circule depuis un site Web SharePoint, via [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], vers un site Web SharePoint Services, à l'aide de l'adaptateur Windows SharePoint Services.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-227">This procedure demonstrates how a document flows from a Sharepoint web site, through [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], and to a Sharepoint Services Web site using the Windows Sharepoint Services adapter.</span></span>  
  
#### <a name="create-an-infopath-form-to-send-through-the-system"></a><span data-ttu-id="aa9a6-228">Création d'un formulaire InfoPath pour envoi via le système</span><span class="sxs-lookup"><span data-stu-id="aa9a6-228">Create an InfoPath form to send through the system</span></span>  
  
1.  <span data-ttu-id="aa9a6-229">Ouvrez un navigateur Web, puis accédez à l'URL du site que vous avez créé</span><span class="sxs-lookup"><span data-stu-id="aa9a6-229">Open a Web browser and navigate to the URL of the site you created.</span></span> <span data-ttu-id="aa9a6-230">Par exemple, `http://<server_name>/sites/WSSAdapterWalkthrough`.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-230">For example, `http://<server_name>/sites/WSSAdapterWalkthrough`.</span></span>  
  
2.  <span data-ttu-id="aa9a6-231">Sur le côté gauche, sous **Documents**, cliquez sur `InfoPathSolutions`.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-231">On the left side, under **Documents**, click `InfoPathSolutions`.</span></span>  
  
3.  <span data-ttu-id="aa9a6-232">Cliquez sur le `PurchaseOrder` fichier pour afficher la **télécharger le fichier** boîte de dialogue, puis cliquez sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-232">Click the `PurchaseOrder` file to display the **File Download** dialog box, and then click **Open**.</span></span> <span data-ttu-id="aa9a6-233">InfoPath va charger le formulaire.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-233">InfoPath will load the form.</span></span>  
  
4.  <span data-ttu-id="aa9a6-234">Dans le **Purchase Order ID** , tapez `1002`.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-234">In the **Purchase Order ID** field, type `1002`.</span></span>  
  
5.  <span data-ttu-id="aa9a6-235">Dans le **facturation** , tapez `John Doe`.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-235">In the **Bill To** field, type `John Doe`.</span></span>  
  
6.  <span data-ttu-id="aa9a6-236">Dans le **quantité** , tapez `750`.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-236">In the **Amount** field, type `750`.</span></span>  
  
7.  <span data-ttu-id="aa9a6-237">Dans le **Purchase Order Date** , tapez `1/2/2005`.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-237">In the **Purchase Order Date** field, type `1/2/2005`.</span></span>  
  
8.  <span data-ttu-id="aa9a6-238">Cliquez sur **Enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-238">Click **Save**.</span></span>  
  
9. <span data-ttu-id="aa9a6-239">Dans le **enregistrer en tant que** boîte de dialogue, tapez `http://<server_name>/sites/WSSAdapterWalkthrough/Source`dans les **nom de fichier** champ, puis appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-239">In the **Save As** dialog box, type `http://<server_name>/sites/WSSAdapterWalkthrough/Source`in the **file name** field, and then hit Enter.</span></span>  
  
10. <span data-ttu-id="aa9a6-240">Type `PurchaseOrder2.xml` dans les **nom de fichier** champ, puis cliquez sur **enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-240">Type `PurchaseOrder2.xml` in the **file name** field, and then click **Save**.</span></span>  
  
11. <span data-ttu-id="aa9a6-241">Fermez Microsoft Office InfoPath.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-241">Close Microsoft Office InfoPath.</span></span>  
  
12. <span data-ttu-id="aa9a6-242">Dans le navigateur Web, dans la barre de navigation supérieure, cliquez sur **Documents et listes**.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-242">In the Web browser, on the top navigation bar, click **Documents and Lists**.</span></span>  
  
13. <span data-ttu-id="aa9a6-243">Sous **bibliothèques de documents**, cliquez sur **Destination**.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-243">Under **Document Libraries**, click **Destination**.</span></span>  
  
14. <span data-ttu-id="aa9a6-244">Votre message est désormais répertorié dans la bibliothèque de documents de destination.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-244">In the Destination document library, you will now see your message listed.</span></span> <span data-ttu-id="aa9a6-245">Vous y trouverez également une copie archivée dans la bibliothèque de documents d’Archive.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-245">You will also find a copy archived in the Archive document library.</span></span>  
  
15. <span data-ttu-id="aa9a6-246">Dans la bibliothèque de documents de destination, cliquez sur `PurchaseOrder1.xml`.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-246">In the Destination document library, click `PurchaseOrder1.xml`.</span></span> <span data-ttu-id="aa9a6-247">Notez que ce fichier XML s'ouvre dans Microsoft Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-247">Note that this XML file is opened in Microsoft Internet Explorer.</span></span>  
  
16. <span data-ttu-id="aa9a6-248">Dans la bibliothèque de documents de destination, cliquez sur `PurchaseOrder2.xml`.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-248">In the Destination document library, click `PurchaseOrder2.xml`.</span></span> <span data-ttu-id="aa9a6-249">Notez que le fichier XML est ouvert dans Microsoft Office InfoPath.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-249">Note that this XML file is opened in Microsoft Office InfoPath.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="aa9a6-250">Dans la bibliothèque de documents de destination, les colonnes Nom de fichier et Nom du partenaire devraient contenir respectivement la valeur des champs Réf bon de commande et Facturer à.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-250">In the Destination document library, the file name column should contain the value of the PurchaseOrderID field and the Partner Name column should contain the value of the BillTo field.</span></span>  
  
## <a name="summary"></a><span data-ttu-id="aa9a6-251">Résumé</span><span class="sxs-lookup"><span data-stu-id="aa9a6-251">Summary</span></span>  
 <span data-ttu-id="aa9a6-252">Cette procédure pas à pas vous a permis d'ajouter une intégration étroite à Microsoft InfoPath, à l'aide de l'adaptateur Windows SharePoint Services et du routage basé sur le contenu.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-252">In this walkthrough you have seen how to add tighter integration with Microsoft InfoPath using the Windows SharePoint Services Adapter and content-based routing (CBR).</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="aa9a6-253">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="aa9a6-253">Next Steps</span></span>  
 <span data-ttu-id="aa9a6-254">Maintenant que vous avez terminé cette procédure pas à pas, effectuez la [procédure pas à pas : Module 3 - l’accès à des propriétés SharePoint à partir d’une Orchestration](../core/walkthrough-module-3-accessing-sharepoint-properties-from-an-orchestration.md) procédure pas à pas qui permet de compléter le travail que vous avez terminé cette procédure pas à pas, intègre un orchestration dans le projet et vous montre comment accéder aux propriétés de SharePoint à partir d’elle.</span><span class="sxs-lookup"><span data-stu-id="aa9a6-254">Now that you have completed this walkthrough, perform the [Walkthrough: Module 3 - Accessing SharePoint Properties from an Orchestration](../core/walkthrough-module-3-accessing-sharepoint-properties-from-an-orchestration.md) walkthrough which expands on the work you have done with this walkthrough, integrates an orchestration into the project, and shows you how to access SharePoint properties from within it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa9a6-255">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aa9a6-255">See Also</span></span>  
 <span data-ttu-id="aa9a6-256">[Nouveautés de l’adaptateur Windows SharePoint Services ?](../core/what-is-the-windows-sharepoint-services-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="aa9a6-256">[What Is the Windows SharePoint Services Adapter?](../core/what-is-the-windows-sharepoint-services-adapter.md) </span></span>  
 [<span data-ttu-id="aa9a6-257">Procédures pas à pas de carte de Windows SharePoint Services</span><span class="sxs-lookup"><span data-stu-id="aa9a6-257">Windows SharePoint Services Adapter Walkthroughs</span></span>](../core/windows-sharepoint-services-adapter-walkthroughs.md)