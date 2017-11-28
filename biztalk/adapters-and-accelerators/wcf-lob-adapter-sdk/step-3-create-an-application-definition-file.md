---
title: "Étape 3 : Créer un fichier de définition d’Application | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 843fafdb-571e-4da4-ad04-7dc7f23e03ac
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ce22a63e8267c36c1306974caa0faa5f9aa6be4b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-3-create-an-application-definition-file"></a><span data-ttu-id="2f4ea-102">Étape 3 : Créer un fichier de définition d’Application</span><span class="sxs-lookup"><span data-stu-id="2f4ea-102">Step 3: Create an Application Definition File</span></span>
<span data-ttu-id="2f4ea-103">![Étape 3 sur 4](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-3of4.gif "Step_3of4")</span><span class="sxs-lookup"><span data-stu-id="2f4ea-103">![Step 3 of 4](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-3of4.gif "Step_3of4")</span></span>  
  
 <span data-ttu-id="2f4ea-104">**Durée :** 15 minutes</span><span class="sxs-lookup"><span data-stu-id="2f4ea-104">**Time to complete:** 15 minutes</span></span>  
  
 <span data-ttu-id="2f4ea-105">La fonctionnalité de catalogue de données métiers dans Microsoft Office SharePoint Server expose et incorpore des données dans les applications line-of-business (LOB) dans des portails.</span><span class="sxs-lookup"><span data-stu-id="2f4ea-105">The Business Data Catalog feature in Microsoft Office SharePoint Server exposes and incorporates data from line-of-business (LOB) applications into portals.</span></span> <span data-ttu-id="2f4ea-106">Pour intégrer ces données dans votre site portail, vous devez générer un fichier de définition d’application Microsoft Office SharePoint Server peut consommer.</span><span class="sxs-lookup"><span data-stu-id="2f4ea-106">To incorporate this data into your portal site, you must build an application definition file that Microsoft Office SharePoint Server can consume.</span></span>  
  
 <span data-ttu-id="2f4ea-107">Dans cette étape, vous utilisez l’outil Business Data Catalog Definition Editor, disponible avec le SDK Microsoft Office SharePoint Server 2007, pour créer un fichier de définition d’application pour le catalogue de données métiers.</span><span class="sxs-lookup"><span data-stu-id="2f4ea-107">In this step you use the Business Data Catalog Definition Editor tool, available with the Microsoft Office SharePoint Server 2007 SDK, to create an application definition file for the Business Data Catalog.</span></span> <span data-ttu-id="2f4ea-108">Ce fichier de définition décrit la méthode EchoGreetings de l’adaptateur d’écho et servira dans les étapes suivantes pour activer SharePoint pour communiquer avec la carte.</span><span class="sxs-lookup"><span data-stu-id="2f4ea-108">This definition file describes the EchoGreetings method of the Echo adapter, and will be used in later steps to enable SharePoint to communicate with the adapter.</span></span>  
  
 <span data-ttu-id="2f4ea-109">L’objectif de l’application Microsoft Office SharePoint Server que vous créez doit vous permettent d’appeler la méthode EchoGreetings de l’adaptateur d’écho et de retourner la réponse à l’aide d’un composant WebPart SharePoint.</span><span class="sxs-lookup"><span data-stu-id="2f4ea-109">The purpose of the Microsoft Office SharePoint Server application that you are creating is to allow you to invoke the EchoGreetings method of the Echo adapter and return the response using a SharePoint Web Part.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="2f4ea-110">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="2f4ea-110">Prerequisites</span></span>  
 <span data-ttu-id="2f4ea-111">Vous devez avoir terminé [étape 2 : déployer le projet Web](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-2-deploy-the-web-project.md).</span><span class="sxs-lookup"><span data-stu-id="2f4ea-111">You should have completed [Step 2: Deploy the Web Project](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-2-deploy-the-web-project.md).</span></span> <span data-ttu-id="2f4ea-112">Vous devez également avoir accès à la Business Data Catalog Definition Editor, qui est installé dans le cadre de la SDK Microsoft Office SharePoint Server 2007.</span><span class="sxs-lookup"><span data-stu-id="2f4ea-112">You must also have access to the Business Data Catalog Definition Editor, which is installed as part of the Microsoft Office SharePoint Server 2007 SDK.</span></span> <span data-ttu-id="2f4ea-113">Vous pouvez télécharger le Kit de développement logiciel à partir de [http://go.microsoft.com/fwlink/?LinkId=104130](http://go.microsoft.com/fwlink/?LinkId=104130).</span><span class="sxs-lookup"><span data-stu-id="2f4ea-113">You can download the SDK from [http://go.microsoft.com/fwlink/?LinkId=104130](http://go.microsoft.com/fwlink/?LinkId=104130).</span></span>  
  
## <a name="creating-an-application-definition-file"></a><span data-ttu-id="2f4ea-114">Création d’un fichier de définition d’Application</span><span class="sxs-lookup"><span data-stu-id="2f4ea-114">Creating an Application Definition File</span></span>  
 <span data-ttu-id="2f4ea-115">Cette rubrique fournit des instructions pas à pas pour créer un fichier de définition d’application pour la connexion du catalogue de données métiers SharePoint avec l’adaptateur WCF hébergé dans IIS.</span><span class="sxs-lookup"><span data-stu-id="2f4ea-115">This topic provides step-by-step instructions to create an application definition file for connecting the SharePoint Business Data Catalog with the WCF adapter hosted in IIS.</span></span>  
  
#### <a name="to-connect-to-the-wcf-adapter-service-and-create-entities"></a><span data-ttu-id="2f4ea-116">Pour vous connecter au service de l’adaptateur WCF et créer des entités</span><span class="sxs-lookup"><span data-stu-id="2f4ea-116">To connect to the WCF adapter service and create entities</span></span>  
  
1.  <span data-ttu-id="2f4ea-117">À partir de la **menu Démarrer**, pointez sur **tous les programmes**, puis cliquez sur **Microsoft Business Data Catalog Definition Editor**.</span><span class="sxs-lookup"><span data-stu-id="2f4ea-117">From the **Start menu**, point to **All Programs**, and then click **Microsoft Business Data Catalog Definition Editor**.</span></span>  
  
2.  <span data-ttu-id="2f4ea-118">Dans la barre d’outils, cliquez sur **ajouter un système LOB**.</span><span class="sxs-lookup"><span data-stu-id="2f4ea-118">On the toolbar, click **Add LOB System**.</span></span>  
  
3.  <span data-ttu-id="2f4ea-119">Dans la fenêtre Ajouter un système LOB, cliquez sur **se connecter au service Web**.</span><span class="sxs-lookup"><span data-stu-id="2f4ea-119">In the Add LOB System window, click **Connect to Webservice**.</span></span>  
  
4.  <span data-ttu-id="2f4ea-120">Dans le **URL** zone, tapez l’URL pour le service WCF.</span><span class="sxs-lookup"><span data-stu-id="2f4ea-120">In the **URL** box, type the URL for the WCF service.</span></span> <span data-ttu-id="2f4ea-121">L’URL doit être au format suivant :`https://machinename/EchoWeb/EchoOutboundContract.svc?wsdl`</span><span class="sxs-lookup"><span data-stu-id="2f4ea-121">The URL must be in the following format: `https://machinename/EchoWeb/EchoOutboundContract.svc?wsdl`</span></span>  
  
5.  <span data-ttu-id="2f4ea-122">Cliquez sur **Se connecter**.</span><span class="sxs-lookup"><span data-stu-id="2f4ea-122">Click **Connect**.</span></span>  
  
6.  <span data-ttu-id="2f4ea-123">Pour afficher les opérations disponibles, cliquez sur le **ajouter une méthode Web** onglet. Vous devez voir la méthode EchoGreetings.</span><span class="sxs-lookup"><span data-stu-id="2f4ea-123">To see the available operations, click the **Add Web Method** tab. You should see the EchoGreetings method.</span></span> <span data-ttu-id="2f4ea-124">Faites glisser la méthode à l’aire de conception.</span><span class="sxs-lookup"><span data-stu-id="2f4ea-124">Drag the method to the Design Surface.</span></span>  
  
7.  <span data-ttu-id="2f4ea-125">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="2f4ea-125">Click **OK**.</span></span>  
  
8.  <span data-ttu-id="2f4ea-126">Dans le **Entrez un nom pour le système LOB** boîte de dialogue, tapez un nom dans la **nom du système LOB** boîte.</span><span class="sxs-lookup"><span data-stu-id="2f4ea-126">In the **Enter the name for the LOB System** dialog box, type a name in the **LOB System Name** box.</span></span> <span data-ttu-id="2f4ea-127">Par exemple, entrez **EchoWSLOB**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="2f4ea-127">For this example, enter **EchoWSLOB**, and then click **OK**.</span></span>  
  
9. <span data-ttu-id="2f4ea-128">Développez le **EchoWSLob** nœud, puis développez le **entités** nœud.</span><span class="sxs-lookup"><span data-stu-id="2f4ea-128">Expand the **EchoWSLob** node, and then expand the **Entities** node.</span></span> <span data-ttu-id="2f4ea-129">Sélectionnez **Entity0** et dans le type du volet Propriétés **EchoGreetings** comme valeur pour le **nom** propriété.</span><span class="sxs-lookup"><span data-stu-id="2f4ea-129">Select **Entity0** and in the Properties pane type **EchoGreetings** as the value for the **Name** property.</span></span>  
  
     <span data-ttu-id="2f4ea-130">![Nom de l’entité](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/942e7853-451e-4cf5-8884-09fb7d8dc19d.gif "942e7853-451e-4cf5-8884-09fb7d8dc19d")</span><span class="sxs-lookup"><span data-stu-id="2f4ea-130">![Entity Name](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/942e7853-451e-4cf5-8884-09fb7d8dc19d.gif "942e7853-451e-4cf5-8884-09fb7d8dc19d")</span></span>  
  
## <a name="specify-user-name-and-password-headers-for-the-method"></a><span data-ttu-id="2f4ea-131">Spécifiez le nom d’utilisateur et mot de passe en-têtes pour la méthode</span><span class="sxs-lookup"><span data-stu-id="2f4ea-131">Specify User Name and Password Headers for the Method</span></span>  
 <span data-ttu-id="2f4ea-132">Lors de l’appel d’un adaptateur WCF, vous devrez fournir les informations d’identification d’utilisateur qui seront transmises au système métier.</span><span class="sxs-lookup"><span data-stu-id="2f4ea-132">When calling a WCF adapter, you may have to provide user credentials that will be passed to the LOB system.</span></span> <span data-ttu-id="2f4ea-133">Dans [étape 1 : utiliser l’Assistant développement d’adaptateurs pour créer le projet Web](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-1-use-the-adapter-service-development-wizard-to-create-the-web-project.md), vous avez configuré l’adaptateur Echo pour exiger que les informations de nom et mot de passe utilisateur fourni dans les champs MyUserHeader et MyPassHeader.</span><span class="sxs-lookup"><span data-stu-id="2f4ea-133">In [Step 1: Use the Adapter Service Development Wizard to Create the Web Project](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-1-use-the-adapter-service-development-wizard-to-create-the-web-project.md), you configured the Echo adapter to require that user name and password information be provided in the MyUserHeader and MyPassHeader fields.</span></span> <span data-ttu-id="2f4ea-134">Vous devez maintenant utiliser les mêmes noms de champ pour ce fichier de définition d’application.</span><span class="sxs-lookup"><span data-stu-id="2f4ea-134">You must now use the same field names for this application definition file.</span></span>  
  
#### <a name="to-specify-user-name-and-password-headers"></a><span data-ttu-id="2f4ea-135">Pour spécifier les en-têtes de nom et mot de passe utilisateur</span><span class="sxs-lookup"><span data-stu-id="2f4ea-135">To specify user name and password headers</span></span>  
  
1.  <span data-ttu-id="2f4ea-136">Dans le volet objets de métadonnées, développez le **EchoGreetings** nœud, puis développez le **méthodes** nœud.</span><span class="sxs-lookup"><span data-stu-id="2f4ea-136">In the Metadata Objects pane, expand the **EchoGreetings** node, and then expand the **Methods** node.</span></span>  
  
2.  <span data-ttu-id="2f4ea-137">Cliquez sur le **EchoGreetings** nœud et, dans le volet Propriétés, cliquez sur le bouton de sélection **(...)**  situé dans le **propriétés** champ.</span><span class="sxs-lookup"><span data-stu-id="2f4ea-137">Click the **EchoGreetings** node and, in the Properties pane, click the ellipsis **(…)** button in the **Properties** field.</span></span>  
  
3.  <span data-ttu-id="2f4ea-138">Dans la fenêtre Éditeur de collections PropertyView, cliquez sur **ajouter**et dans le **nom** champ du volet Propriétés, type **HttpHeaderUserName**.</span><span class="sxs-lookup"><span data-stu-id="2f4ea-138">In the PropertyView Collection Editor window, click **Add**, and in the **Name** field of the Property pane, type  **HttpHeaderUserName**.</span></span>  
  
     <span data-ttu-id="2f4ea-139">![Spécifiez les champs d’en-tête de nom d’utilisateur](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/8da4d1b7-0792-407a-ba93-ba749138dd14.gif "8da4d1b7-0792-407a-ba93-ba749138dd14")</span><span class="sxs-lookup"><span data-stu-id="2f4ea-139">![Specify Username Header Fields](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/8da4d1b7-0792-407a-ba93-ba749138dd14.gif "8da4d1b7-0792-407a-ba93-ba749138dd14")</span></span>  
  
4.  <span data-ttu-id="2f4ea-140">Dans le **PropertyValue**, tapez **MyUserHeader**.</span><span class="sxs-lookup"><span data-stu-id="2f4ea-140">In the **PropertyValue**field, type **MyUserHeader**.</span></span>  
  
5.  <span data-ttu-id="2f4ea-141">Cliquez sur **ajouter**et dans le type de volet propriété **HttpHeaderPassword** pour le champ nom, puis tapez **MyPassHeader** pour la **PropertyValue**champ.</span><span class="sxs-lookup"><span data-stu-id="2f4ea-141">Click **Add**, and in the Property pane type **HttpHeaderPassword** for the Name field, then type **MyPassHeader** for the **PropertyValue** field.</span></span>  
  
6.  <span data-ttu-id="2f4ea-142">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="2f4ea-142">Click **OK**.</span></span>  
  
## <a name="set-up-single-sign-on-for-connecting-to-the-echo-adapter"></a><span data-ttu-id="2f4ea-143">Définir des Single Sign-On pour la connexion à l’adaptateur d’écho</span><span class="sxs-lookup"><span data-stu-id="2f4ea-143">Set up Single Sign-On for Connecting to the Echo Adapter</span></span>  
 <span data-ttu-id="2f4ea-144">SharePoint utilise les informations à partir de l’authentification unique pour remplir le MyUserHeader et MyPassHeader avec des valeurs de l’authentification.</span><span class="sxs-lookup"><span data-stu-id="2f4ea-144">SharePoint uses information from Single Sign-On to populate the MyUserHeader and MyPassHeader with authentication values.</span></span> <span data-ttu-id="2f4ea-145">Pour lier ce fichier de définition d’application pour l’authentification unique, vous devez fournir un SecondarySsoApplicationId.</span><span class="sxs-lookup"><span data-stu-id="2f4ea-145">To link this application definition file to Single Sign-On, you must provide a SecondarySsoApplicationId.</span></span>  
  
#### <a name="to-set-the-secondaryssoapplicationid-property"></a><span data-ttu-id="2f4ea-146">Pour définir la propriété SecondarySsoApplicationId</span><span class="sxs-lookup"><span data-stu-id="2f4ea-146">To set the SecondarySsoApplicationId property</span></span>  
  
1.  <span data-ttu-id="2f4ea-147">Dans le volet objets de métadonnées, développez le **EchoWSLOB** nœud, puis développez le **Instances** nœud.</span><span class="sxs-lookup"><span data-stu-id="2f4ea-147">In the Metadata Objects pane, expand the **EchoWSLOB** node, and then expand the **Instances** node.</span></span>  
  
2.  <span data-ttu-id="2f4ea-148">Cliquez sur **EchoWSLOB_Instance**, dans le volet Propriétés, cliquez sur le bouton de sélection **(...)** situé dans le **propriétés** champ.</span><span class="sxs-lookup"><span data-stu-id="2f4ea-148">Click **EchoWSLOB_Instance**, and in the Properties pane, click the ellipsis **(…)**button in the **Properties** field.</span></span>  
  
3.  <span data-ttu-id="2f4ea-149">Dans la fenêtre Éditeur de collections PropertyView, cliquez sur **ajouter**et dans le volet Propriétés, tapez **SecondarySsoApplicationId** dans les **nom** champ.</span><span class="sxs-lookup"><span data-stu-id="2f4ea-149">In the PropertyView Collection Editor window, click **Add**, and in the Property pane, type **SecondarySsoApplicationId** in the **Name** field.</span></span>  
  
4.  <span data-ttu-id="2f4ea-150">Dans le **PropertyValue** , tapez **EchoSSO**.</span><span class="sxs-lookup"><span data-stu-id="2f4ea-150">In the **PropertyValue** field, type **EchoSSO**.</span></span>  
  
     <span data-ttu-id="2f4ea-151">![Définir SecondarySsoApplicationId](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/68e6be61-77af-46b1-8ff0-b8538c526228.gif "68e6be61-77af-46b1-8ff0-b8538c526228")</span><span class="sxs-lookup"><span data-stu-id="2f4ea-151">![Set the SecondarySsoApplicationId](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/68e6be61-77af-46b1-8ff0-b8538c526228.gif "68e6be61-77af-46b1-8ff0-b8538c526228")</span></span>  
  
5.  <span data-ttu-id="2f4ea-152">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="2f4ea-152">Click **OK**.</span></span>  
  
## <a name="create-input-filters-and-default-values"></a><span data-ttu-id="2f4ea-153">Créer des filtres d’entrée et les valeurs par défaut</span><span class="sxs-lookup"><span data-stu-id="2f4ea-153">Create Input Filters and Default Values</span></span>  
 <span data-ttu-id="2f4ea-154">Le fichier de définition d’application doit être en mesure d’accepter l’entrée d’utilisateur qui peut être passée à un service Web.</span><span class="sxs-lookup"><span data-stu-id="2f4ea-154">The application definition file must be able to  accept user input that can be passed to a Web service.</span></span> <span data-ttu-id="2f4ea-155">Pour ce faire, vous devez effectuer l’ensemble suivant de tâches :</span><span class="sxs-lookup"><span data-stu-id="2f4ea-155">To accomplish this, you must perform the following set of tasks:</span></span>  
  
#### <a name="to-create-a-filter-and-map-it-to-the-greeting-parameter"></a><span data-ttu-id="2f4ea-156">Pour créer un filtre et la mapper au paramètre de message d’accueil</span><span class="sxs-lookup"><span data-stu-id="2f4ea-156">To create a filter, and map it to the greeting parameter</span></span>  
  
1.  <span data-ttu-id="2f4ea-157">Dans le volet objets de métadonnées, développez le **EchoWSLOB** nœud, puis développez le **méthodes** nœud.</span><span class="sxs-lookup"><span data-stu-id="2f4ea-157">In the Metadata Objects pane, expand the **EchoWSLOB** node, and then expand the **Methods** node.</span></span>  
  
2.  <span data-ttu-id="2f4ea-158">Développez le **EchoGreetings** (méthode), avec le bouton droit **filtres**, puis cliquez sur **ajouter un filtre**.</span><span class="sxs-lookup"><span data-stu-id="2f4ea-158">Expand the **EchoGreetings** method, right-click **Filters**, and then click **Add Filter**.</span></span>  
  
3.  <span data-ttu-id="2f4ea-159">Dans le volet Propriétés, tapez **salutation** dans les **nom** champ.</span><span class="sxs-lookup"><span data-stu-id="2f4ea-159">In the Properties pane, type **Greeting** in the **Name** field.</span></span>  
  
     <span data-ttu-id="2f4ea-160">![Définir le nom du filtre](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/74036b9e-7eec-4156-b238-840e67a2f00c.gif "74036b9e-7eec-4156-b238-840e67a2f00c")</span><span class="sxs-lookup"><span data-stu-id="2f4ea-160">![Set the Filter Name](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/74036b9e-7eec-4156-b238-840e67a2f00c.gif "74036b9e-7eec-4156-b238-840e67a2f00c")</span></span>  
  
4.  <span data-ttu-id="2f4ea-161">Dans le volet objets de métadonnées, développez le **EchoWSLOB** nœud, puis développez le **méthodes** nœud</span><span class="sxs-lookup"><span data-stu-id="2f4ea-161">In the Metadata Objects pane, expand the **EchoWSLOB** node, and then expand the **Methods** node</span></span>  
  
5.  <span data-ttu-id="2f4ea-162">Développez le **EchoGreetings** (méthode), puis développez le **paramètres** nœud.</span><span class="sxs-lookup"><span data-stu-id="2f4ea-162">Expand the **EchoGreetings** method, and then expand the **Parameters** node.</span></span>  
  
6.  <span data-ttu-id="2f4ea-163">Développez le **salutation** nœud, puis développez la seconde **salutation** nœud.</span><span class="sxs-lookup"><span data-stu-id="2f4ea-163">Expand the **greeting** node, and then expand the second **greeting** node.</span></span>  
  
7.  <span data-ttu-id="2f4ea-164">Cliquez sur le **greetingText** nœud, puis dans le volet Propriétés, sélectionnez **salutation** à partir de la **FilterDescriptor** liste.</span><span class="sxs-lookup"><span data-stu-id="2f4ea-164">Click the **greetingText** node, and in the Properties pane, select **Greeting** from the **FilterDescriptor** list.</span></span>  
  
#### <a name="to-create-a-finder-method-instance-for-the-echogreetings-method"></a><span data-ttu-id="2f4ea-165">Pour créer une instance de méthode Finder pour la méthode EchoGreetings</span><span class="sxs-lookup"><span data-stu-id="2f4ea-165">To create a Finder method instance for the EchoGreetings method</span></span>  
  
1.  <span data-ttu-id="2f4ea-166">Dans le volet objets de métadonnées, développez le **EchoWSLOB** nœud, puis développez le **méthodes** nœud.</span><span class="sxs-lookup"><span data-stu-id="2f4ea-166">In the Metadata Objects pane, expand the **EchoWSLOB** node, and then expand the **Methods** node.</span></span>  
  
2.  <span data-ttu-id="2f4ea-167">Développez le **EchoGreetings** (méthode), avec le bouton droit **Instances**, puis cliquez sur **ajouter une Instance de méthode** pour ouvrir la fenêtre Créer une Instance de méthode.</span><span class="sxs-lookup"><span data-stu-id="2f4ea-167">Expand the **EchoGreetings** method, right-click **Instances**, and then click **Add Method Instance** to open the Create Method Instance window.</span></span>  
  
3.  <span data-ttu-id="2f4ea-168">Dans la fenêtre Créer une Instance de méthode, cliquez sur **recherche** pour **Type d’Instance de méthode**, puis sélectionnez **retourner** pour **TypeDescriptor de retour**.</span><span class="sxs-lookup"><span data-stu-id="2f4ea-168">In the Create Method Instance window, click **Finder** for **Method Instance Type**, and then select **Return** for **Return TypeDescriptor**.</span></span>  
  
     <span data-ttu-id="2f4ea-169">![Créer l’Instance de méthode](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/a932a7a0-c004-46bf-af5c-cc7392bafa43.gif "a932a7a0-c004-46bf-af5c-cc7392bafa43")</span><span class="sxs-lookup"><span data-stu-id="2f4ea-169">![Create the Method Instance](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/a932a7a0-c004-46bf-af5c-cc7392bafa43.gif "a932a7a0-c004-46bf-af5c-cc7392bafa43")</span></span>  
  
4.  <span data-ttu-id="2f4ea-170">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="2f4ea-170">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="2f4ea-171">Dans le volet Propriétés, tapez **EchoGreetings_Instance** dans les **nom** champ.</span><span class="sxs-lookup"><span data-stu-id="2f4ea-171">In the Properties pane, type **EchoGreetings_Instance** in the **Name** field.</span></span>  
  
#### <a name="to-set-default-parameters"></a><span data-ttu-id="2f4ea-172">Pour définir les paramètres par défaut</span><span class="sxs-lookup"><span data-stu-id="2f4ea-172">To set default parameters</span></span>  
  
1.  <span data-ttu-id="2f4ea-173">Dans le volet objets de métadonnées, développez le **EchoWSLOB** nœud, puis développez le **méthodes** nœud.</span><span class="sxs-lookup"><span data-stu-id="2f4ea-173">In the Metadata Objects pane, expand the **EchoWSLOB** node, and then expand the **Methods** node.</span></span>  
  
2.  <span data-ttu-id="2f4ea-174">Développez le **EchoGreetings** (méthode), puis développez le **Instances** nœud.</span><span class="sxs-lookup"><span data-stu-id="2f4ea-174">Expand the **EchoGreetings** method, and then expand the **Instances** node.</span></span>  
  
3.  <span data-ttu-id="2f4ea-175">Sélectionnez le **EchoGreetings_Instance** méthode d’instance et dans le volet Propriétés, cliquez sur le bouton de sélection (...) dans le **DefaultValues** champ.</span><span class="sxs-lookup"><span data-stu-id="2f4ea-175">Select the **EchoGreetings_Instance** method instance, and in the Properties pane, click the ellipsis button (…) in the **DefaultValues** field.</span></span>  
  
4.  <span data-ttu-id="2f4ea-176">Dans la fenêtre d’édition, développez le **salutation** nœud, puis développez la seconde **salutation** nœud.</span><span class="sxs-lookup"><span data-stu-id="2f4ea-176">In the Edit window, expand the **greeting** node, and then expand the second **greeting** node.</span></span> <span data-ttu-id="2f4ea-177">Développez le **nom** nœud, jusqu'à ce que l’arborescence est entièrement affiché.</span><span class="sxs-lookup"><span data-stu-id="2f4ea-177">Expand the **name** node, until the tree structure is fully displayed.</span></span>  
  
5.  <span data-ttu-id="2f4ea-178">Dans la fenêtre d’édition, définissez les valeurs de champ comme suit :</span><span class="sxs-lookup"><span data-stu-id="2f4ea-178">In the Edit window, set the field values as follows:</span></span>  
  
    |<span data-ttu-id="2f4ea-179">Définition de</span><span class="sxs-lookup"><span data-stu-id="2f4ea-179">Set this</span></span>|<span data-ttu-id="2f4ea-180">Sur</span><span class="sxs-lookup"><span data-stu-id="2f4ea-180">To this</span></span>|  
    |--------------|-------------|  
    |<span data-ttu-id="2f4ea-181">**id**</span><span class="sxs-lookup"><span data-stu-id="2f4ea-181">**id**</span></span>|<span data-ttu-id="2f4ea-182">Une valeur GUID, par exemple 27829ed4-583a - 40c 4-ad87-fb8cdd9dc98d.</span><span class="sxs-lookup"><span data-stu-id="2f4ea-182">A GUID value, for example 27829ed4-583a-40c4-ad87-fb8cdd9dc98d.</span></span>|  
    |<span data-ttu-id="2f4ea-183">**sentDateTime**</span><span class="sxs-lookup"><span data-stu-id="2f4ea-183">**sentDateTime**</span></span>|<span data-ttu-id="2f4ea-184">La date et l’heure, par exemple 15/05/08 9 h 12</span><span class="sxs-lookup"><span data-stu-id="2f4ea-184">The current date and time, for example 05/15/08 9:12 AM</span></span>|  
    |<span data-ttu-id="2f4ea-185">**Prénom**</span><span class="sxs-lookup"><span data-stu-id="2f4ea-185">**firstName**</span></span>|<span data-ttu-id="2f4ea-186">Première</span><span class="sxs-lookup"><span data-stu-id="2f4ea-186">First</span></span>|  
    |<span data-ttu-id="2f4ea-187">**middleName**</span><span class="sxs-lookup"><span data-stu-id="2f4ea-187">**middleName**</span></span>|<span data-ttu-id="2f4ea-188">Milieu</span><span class="sxs-lookup"><span data-stu-id="2f4ea-188">Middle</span></span>|  
    |<span data-ttu-id="2f4ea-189">**lastName**</span><span class="sxs-lookup"><span data-stu-id="2f4ea-189">**lastName**</span></span>|<span data-ttu-id="2f4ea-190">Dernière</span><span class="sxs-lookup"><span data-stu-id="2f4ea-190">Last</span></span>|  
  
     <span data-ttu-id="2f4ea-191">![Paramètres par défaut](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/70250957-9680-48ce-8bce-420ff18bb47a.gif "70250957-9680-48ce-8bce-420ff18bb47a")</span><span class="sxs-lookup"><span data-stu-id="2f4ea-191">![Default Parameters](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/70250957-9680-48ce-8bce-420ff18bb47a.gif "70250957-9680-48ce-8bce-420ff18bb47a")</span></span>  
  
6.  <span data-ttu-id="2f4ea-192">Cliquez sur **Fermer**.</span><span class="sxs-lookup"><span data-stu-id="2f4ea-192">Click **Close**.</span></span>  
  
### <a name="to-export-the-application-definition-file"></a><span data-ttu-id="2f4ea-193">Pour exporter le fichier de définition d’application</span><span class="sxs-lookup"><span data-stu-id="2f4ea-193">To export the application definition file</span></span>  
  
1.  <span data-ttu-id="2f4ea-194">Dans le volet objets de métadonnées, cliquez sur le **EchoWSLOB** nœud, puis cliquez sur **exporter**.</span><span class="sxs-lookup"><span data-stu-id="2f4ea-194">In the Metadata Objects pane, right-click the **EchoWSLOB** node, and then click **Export**.</span></span>  
  
2.  <span data-ttu-id="2f4ea-195">Enregistrez le fichier sous EchoWS.xml.</span><span class="sxs-lookup"><span data-stu-id="2f4ea-195">Save the file as EchoWS.xml.</span></span>  
  
## <a name="what-did-i-just-do"></a><span data-ttu-id="2f4ea-196">Actions effectuées</span><span class="sxs-lookup"><span data-stu-id="2f4ea-196">What did I just do?</span></span>  
 <span data-ttu-id="2f4ea-197">Vous avez utilisé l’outil Business Data Catalog Definition Editor pour créer un fichier de définition d’application qui peut être importé dans Microsoft Office SharePoint Server 2007 pour activer la connectivité avec votre adaptateur est hébergé dans IIS.</span><span class="sxs-lookup"><span data-stu-id="2f4ea-197">You have used the Business Data Catalog Definition Editor tool to create an application definition file that can be imported into Microsoft Office SharePoint Server 2007 to enable connectivity with your adapter that is hosted in IIS.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="2f4ea-198">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="2f4ea-198">Next Steps</span></span>  
 <span data-ttu-id="2f4ea-199">Vous devez maintenant créer une application SharePoint basée sur le fichier de définition d’application créé à cette étape.</span><span class="sxs-lookup"><span data-stu-id="2f4ea-199">You must now create a SharePoint application based on the application definition file created in this step.</span></span> <span data-ttu-id="2f4ea-200">Consultez [étape 4 : créer une Application Sharepoint pour accéder à la carte](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-4-create-a-sharepoint-application-to-access-the-adapter.md) pour obtenir des instructions.</span><span class="sxs-lookup"><span data-stu-id="2f4ea-200">See [Step 4: Create a Sharepoint Application to Access the Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-4-create-a-sharepoint-application-to-access-the-adapter.md) for instructions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f4ea-201">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2f4ea-201">See Also</span></span>  
 [<span data-ttu-id="2f4ea-202">Didacticiel 3 : Hébergeant l’adaptateur de l’écho dans IIS</span><span class="sxs-lookup"><span data-stu-id="2f4ea-202">Tutorial 3: Hosting the Echo Adapter in IIS</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-3-hosting-the-echo-adapter-in-iis.md)