---
title: "Étape 2 : Créer un fichier de définition d’application pour les artefacts d’Oracle E-Business Suite | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2665afde-0337-4795-ab4c-6223d39fdf9c
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4ed4340893d351d8406212b585e6216de19c634c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-2-create-an-application-definition-file-for-the-oracle-e-business-suite-artifacts"></a><span data-ttu-id="6aa32-102">Étape 2 : Créer un fichier de définition d’application pour les artefacts d’Oracle E-Business Suite</span><span class="sxs-lookup"><span data-stu-id="6aa32-102">Step 2: Create an application definition file for the Oracle E-Business Suite artifacts</span></span>
<span data-ttu-id="6aa32-103">![Étape 2 sur 4](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-2of4.gif "Step_2of4")</span><span class="sxs-lookup"><span data-stu-id="6aa32-103">![Step 2 of 4](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-2of4.gif "Step_2of4")</span></span>  
  
 <span data-ttu-id="6aa32-104">**Durée :** 15 minutes</span><span class="sxs-lookup"><span data-stu-id="6aa32-104">**Time to complete:** 15 minutes</span></span>  
  
 <span data-ttu-id="6aa32-105">**Objectif :** la fonctionnalité de catalogue de données métiers dans Microsoft SharePoint Server expose et incorpore des données à partir d’applications de métier (LOB) dans des portails.</span><span class="sxs-lookup"><span data-stu-id="6aa32-105">**Objective:** The Business Data Catalog feature in Microsoft SharePoint Server exposes and incorporates data from line-of-business (LOB) applications into portals.</span></span> <span data-ttu-id="6aa32-106">Pour intégrer ces données dans votre site portail, vous devez générer un fichier de définition d’application Microsoft Office SharePoint Server peut consommer.</span><span class="sxs-lookup"><span data-stu-id="6aa32-106">To incorporate this data into your portal site, you must build an application definition file that Microsoft Office SharePoint Server can consume.</span></span>  
  
 <span data-ttu-id="6aa32-107">L’outil Business Data Catalog Definition Editor, disponible avec le SDK Microsoft Office SharePoint Server 2007, vous permet de créer un fichier de définition d’application pour le catalogue de données métiers.</span><span class="sxs-lookup"><span data-stu-id="6aa32-107">The Business Data Catalog Definition Editor tool, available with Microsoft Office SharePoint Server 2007 SDK, enables you to create an application definition file for the Business Data Catalog.</span></span> <span data-ttu-id="6aa32-108">Cet outil génère automatiquement un fichier XML pour le fichier de définition, vous n’avez pas besoin de créer manuellement le fichier dans un document XML éditeur.</span><span class="sxs-lookup"><span data-stu-id="6aa32-108">This tool automatically generates an XML file for the definition file, so you do not need to manually create the file in an XML editor.</span></span>  
  
 <span data-ttu-id="6aa32-109">L’objectif de l’application Microsoft Office SharePoint Server que vous créez est de :</span><span class="sxs-lookup"><span data-stu-id="6aa32-109">The purpose of the Microsoft Office SharePoint Server application that you are creating is to:</span></span>  
  
-   <span data-ttu-id="6aa32-110">Requête pour un employé dans la table d’interface MS_SAMPLE_EMPLOYEE à l’aide d’un composant WebPart de liste de données Business basée sur un nom d’employé.</span><span class="sxs-lookup"><span data-stu-id="6aa32-110">Query for an employee in the MS_SAMPLE_EMPLOYEE interface table using a Business Data List Web Part based on an employee name.</span></span>  
  
-   <span data-ttu-id="6aa32-111">Effectuer une recherche en texte intégral à partir de Microsoft Office SharePoint Server sur la table d’interface MS_SAMPLE_EMPLOYEE.</span><span class="sxs-lookup"><span data-stu-id="6aa32-111">Perform a full-text search from Microsoft Office SharePoint Server on the MS_SAMPLE_EMPLOYEE interface table.</span></span>  
  
 <span data-ttu-id="6aa32-112">Pour chacune de ces exigences, vous devez effectuer un ensemble de tâches dans l’outil Éditeur de définition de catalogue de données métier.</span><span class="sxs-lookup"><span data-stu-id="6aa32-112">For each of these requirements, you must complete a set of tasks in the Business Data Catalog Definition Editor tool.</span></span> <span data-ttu-id="6aa32-113">Cette rubrique fournit des instructions sur la façon d’effectuer ces tâches.</span><span class="sxs-lookup"><span data-stu-id="6aa32-113">This topic provides instructions on how to perform these tasks.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="6aa32-114">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="6aa32-114">Prerequisites</span></span>  
  
-   <span data-ttu-id="6aa32-115">Assurez-vous que vous disposez de l’éditeur de définition de catalogue de données métier installé avec le SDK de Microsoft Office SharePoint Server 2007.</span><span class="sxs-lookup"><span data-stu-id="6aa32-115">Be sure that you have the Business Data Catalog Definition Editor installed as part of the Microsoft Office SharePoint Server 2007 SDK.</span></span> <span data-ttu-id="6aa32-116">Vous pouvez télécharger le Kit de développement logiciel à partir de [http://go.microsoft.com/fwlink/?LinkId=104130](http://go.microsoft.com/fwlink/?LinkId=104130).</span><span class="sxs-lookup"><span data-stu-id="6aa32-116">You can download the SDK from [http://go.microsoft.com/fwlink/?LinkId=104130](http://go.microsoft.com/fwlink/?LinkId=104130).</span></span>  
  
-   <span data-ttu-id="6aa32-117">Publier le service WCF, comme décrit dans [étape 1 : utiliser l’adaptateur Oracle E-Business pour créer et publier un Service WCF](../../adapters-and-accelerators/adapter-oracle-ebs/step-1-use-the-oracle-e-business-adapter-to-create-and-publish-a-wcf-service.md).</span><span class="sxs-lookup"><span data-stu-id="6aa32-117">Publish the WCF service as described in [Step 1: Use the Oracle E-Business Adapter to Create and Publish a WCF Service](../../adapters-and-accelerators/adapter-oracle-ebs/step-1-use-the-oracle-e-business-adapter-to-create-and-publish-a-wcf-service.md).</span></span>  
  

  
##  <a name="Connect"></a><span data-ttu-id="6aa32-118">Se connecter au Service WCF LOB et créer une entité</span><span class="sxs-lookup"><span data-stu-id="6aa32-118">Connect to the WCF LOB Service and Create Entity</span></span>  
 <span data-ttu-id="6aa32-119">Vous devez vous connecter au service WCF pour extraire la Description langage WSDL (Web Services) pour le service.</span><span class="sxs-lookup"><span data-stu-id="6aa32-119">You must connect to the WCF service to extract the Web Services Description Language (WSDL) for the service.</span></span> <span data-ttu-id="6aa32-120">À partir de WSDL, l’éditeur de définition de catalogue de données métier extrait les méthodes.</span><span class="sxs-lookup"><span data-stu-id="6aa32-120">From the WSDL, the Business Data Catalog Definition Editor extracts the methods.</span></span> <span data-ttu-id="6aa32-121">Ces méthodes peuvent être utilisées pour créer des entités.</span><span class="sxs-lookup"><span data-stu-id="6aa32-121">These methods can be used to create entities.</span></span> <span data-ttu-id="6aa32-122">Pour ce didacticiel, une entité est créée.</span><span class="sxs-lookup"><span data-stu-id="6aa32-122">For this tutorial, an entity is created.</span></span>  
  
#### <a name="to-connect-to-the-wcf-service-and-create-entities"></a><span data-ttu-id="6aa32-123">Pour vous connecter au service WCF et de créer des entités</span><span class="sxs-lookup"><span data-stu-id="6aa32-123">To connect to the WCF service and create entities</span></span>  
  
1.  <span data-ttu-id="6aa32-124">Démarrez l’éditeur de définition de catalogue de données métier.</span><span class="sxs-lookup"><span data-stu-id="6aa32-124">Start the Business Data Catalog Definition Editor.</span></span> <span data-ttu-id="6aa32-125">Sur le **Démarrer** menu, cliquez sur **Microsoft Business Data Catalog Definition Editor**.</span><span class="sxs-lookup"><span data-stu-id="6aa32-125">On the **Start** menu, click **Microsoft Business Data Catalog Definition Editor**.</span></span>  
  
2.  <span data-ttu-id="6aa32-126">Dans la barre d’outils, cliquez sur **ajouter un système LOB**.</span><span class="sxs-lookup"><span data-stu-id="6aa32-126">On the toolbar, click **Add LOB System**.</span></span>  
  
3.  <span data-ttu-id="6aa32-127">Dans la fenêtre Ajouter un système LOB, cliquez sur **se connecter au service Web**.</span><span class="sxs-lookup"><span data-stu-id="6aa32-127">In the Add LOB System window, click **Connect to Webservice**.</span></span>  
  
4.  <span data-ttu-id="6aa32-128">Dans le **URL** zone, tapez l’URL pour le service WCF.</span><span class="sxs-lookup"><span data-stu-id="6aa32-128">In the **URL** box, type the URL for the WCF service.</span></span> <span data-ttu-id="6aa32-129">Pour ce didacticiel, l’URL sera :</span><span class="sxs-lookup"><span data-stu-id="6aa32-129">For this tutorial, the URL will be:</span></span>  
  
    ```  
    https://<COMPUTER_NAME>:<PORT_NUMBER>/MS_SAMPLE_EMPLOYEE/InterfaceTables_FND_APPS_MS_SAMPLE_EMPLOYEE.svc  
    ```  
  
     <span data-ttu-id="6aa32-130">L’URL est disponible lorsque vous testez si le service WCF est publié avec succès, comme décrit dans [étape 1 : utiliser l’adaptateur Oracle E-Business pour créer et publier un Service WCF](../../adapters-and-accelerators/adapter-oracle-ebs/step-1-use-the-oracle-e-business-adapter-to-create-and-publish-a-wcf-service.md).</span><span class="sxs-lookup"><span data-stu-id="6aa32-130">The URL is available when you test whether the WCF service is published successfully, as described in [Step 1: Use the Oracle E-Business Adapter to Create and Publish a WCF Service](../../adapters-and-accelerators/adapter-oracle-ebs/step-1-use-the-oracle-e-business-adapter-to-create-and-publish-a-wcf-service.md).</span></span>  
  
5.  <span data-ttu-id="6aa32-131">Cliquez sur **Se connecter**.</span><span class="sxs-lookup"><span data-stu-id="6aa32-131">Click **Connect**.</span></span>  
  
6.  <span data-ttu-id="6aa32-132">Pour afficher les opérations que vous avez sélectionné dans l’Assistant développement d’adaptateurs WCF, cliquez sur le **ajouter une méthode Web** onglet. Vous verrez la méthode suivante : **sélectionnez**.</span><span class="sxs-lookup"><span data-stu-id="6aa32-132">To see the operations you selected in the WCF Adapter Service Development Wizard, click the **Add Web Method** tab. You will see the following method: **Select**.</span></span>  
  
7.  <span data-ttu-id="6aa32-133">Faites glisser le **sélectionnez** méthodes à l’aire de conception.</span><span class="sxs-lookup"><span data-stu-id="6aa32-133">Drag the **Select** methods to the Design Surface.</span></span> <span data-ttu-id="6aa32-134">Lorsque vous faites glisser la méthode à l’aire de conception, une entité est créée, et la méthode devient partie intégrante de cette entité.</span><span class="sxs-lookup"><span data-stu-id="6aa32-134">As you drag the method to the Design Surface, an entity is created, and the method becomes part of that entity.</span></span>  
  
     <span data-ttu-id="6aa32-135">![Ajouter la méthode Select à l’aire de conception](../../adapters-and-accelerators/adapter-oracle-ebs/media/05-add-lob-system.gif "05_Add_LOB_System")</span><span class="sxs-lookup"><span data-stu-id="6aa32-135">![Add Select method to the Design Surface](../../adapters-and-accelerators/adapter-oracle-ebs/media/05-add-lob-system.gif "05_Add_LOB_System")</span></span>  
  
8.  <span data-ttu-id="6aa32-136">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="6aa32-136">Click **OK**.</span></span>  
  
9. <span data-ttu-id="6aa32-137">Dans le **Entrez un nom pour le système LOB** boîte de dialogue, tapez un nom dans la **nom du système LOB** boîte.</span><span class="sxs-lookup"><span data-stu-id="6aa32-137">In the **Enter the name for the LOB System** dialog box, type a name in the **LOB System Name** box.</span></span> <span data-ttu-id="6aa32-138">Pour cet exemple, appeler **MS_SAMPLE_EMPLOYEE**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="6aa32-138">For this example, call it **MS_SAMPLE_EMPLOYEE**, and then click **OK**.</span></span>  
  
10. <span data-ttu-id="6aa32-139">Dans l’entreprise Data Catalog Definition Editor, l’entité nouvellement créée est répertoriée en tant que **Entity0**.</span><span class="sxs-lookup"><span data-stu-id="6aa32-139">In the Business Data Catalog Definition Editor, the newly created entity is listed as **Entity0**.</span></span> <span data-ttu-id="6aa32-140">Renommez l’entité **employé**.</span><span class="sxs-lookup"><span data-stu-id="6aa32-140">Rename the entity to **Employee**.</span></span> <span data-ttu-id="6aa32-141">Procédez comme suit pour renommer l’entité :</span><span class="sxs-lookup"><span data-stu-id="6aa32-141">Perform the following steps to rename the entity:</span></span>  
  
    1.  <span data-ttu-id="6aa32-142">Développez le **MS_SAMPLE_EMPLOYEE** nœud, puis développez le **entités** nœud.</span><span class="sxs-lookup"><span data-stu-id="6aa32-142">Expand the **MS_SAMPLE_EMPLOYEE** node, and then expand the **Entities** node.</span></span>  
  
    2.  <span data-ttu-id="6aa32-143">Sélectionnez le **Entity0** nœud.</span><span class="sxs-lookup"><span data-stu-id="6aa32-143">Select the **Entity0** node.</span></span>  
  
    3.  <span data-ttu-id="6aa32-144">Dans le volet Propriétés, tapez **employé** dans les **nom** boîte.</span><span class="sxs-lookup"><span data-stu-id="6aa32-144">In the Properties pane, type **Employee** in the **Name** box.</span></span>  
  
         <span data-ttu-id="6aa32-145">![Renommer l’entité](../../adapters-and-accelerators/adapter-oracle-ebs/media/06-entity-name.gif "06_Entity_Name")</span><span class="sxs-lookup"><span data-stu-id="6aa32-145">![Rename the entity](../../adapters-and-accelerators/adapter-oracle-ebs/media/06-entity-name.gif "06_Entity_Name")</span></span>  
  
##  <a name="Headers"></a><span data-ttu-id="6aa32-146">Spécifiez le nom d’utilisateur et les en-têtes de mot de passe pour les méthodes</span><span class="sxs-lookup"><span data-stu-id="6aa32-146">Specify User Name and Password Headers for the Methods</span></span>  
 <span data-ttu-id="6aa32-147">Lorsque vous créez un service WCF pour l’opération Select sur la table d’interface MS_SAMPLE_EMPLOYEE dans Oracle E-Business Suite, vous avez spécifié des en-têtes nom et mot de passe d’utilisateur dans le cadre de la configuration de comportement de point de terminaison dans [étape 1 : utiliser le Oracle Adaptateur de E-Business pour créer et publier un Service WCF](../../adapters-and-accelerators/adapter-oracle-ebs/step-1-use-the-oracle-e-business-adapter-to-create-and-publish-a-wcf-service.md).</span><span class="sxs-lookup"><span data-stu-id="6aa32-147">When creating a WCF service for the Select operation on the MS_SAMPLE_EMPLOYEE interface table in Oracle E-Business Suite, you specified user name and password headers as part of the endpoint behavior configuration in [Step 1: Use the Oracle E-Business Adapter to Create and Publish a WCF Service](../../adapters-and-accelerators/adapter-oracle-ebs/step-1-use-the-oracle-e-business-adapter-to-create-and-publish-a-wcf-service.md).</span></span> <span data-ttu-id="6aa32-148">Vous devez spécifier les mêmes valeurs pour la propriété de la méthode Select.</span><span class="sxs-lookup"><span data-stu-id="6aa32-148">You must specify the same values for the Select method property.</span></span>  
  
#### <a name="to-specify-user-name-and-password-headers-for-the-select-method"></a><span data-ttu-id="6aa32-149">Pour spécifier les en-têtes de nom et mot de passe utilisateur pour la méthode Select</span><span class="sxs-lookup"><span data-stu-id="6aa32-149">To specify user name and password headers for the Select method</span></span>  
  
1.  <span data-ttu-id="6aa32-150">Dans le volet objets de métadonnées, développez le **employé** nœud, puis développez le **méthodes** nœud.</span><span class="sxs-lookup"><span data-stu-id="6aa32-150">In the Metadata Objects pane, expand the **Employee** node, and then expand the **Methods** node.</span></span>  
  
2.  <span data-ttu-id="6aa32-151">Cliquez sur le **sélectionnez** nœud, dans le volet Propriétés, cliquez sur le bouton de sélection (...) par rapport à la **propriétés** boîte.</span><span class="sxs-lookup"><span data-stu-id="6aa32-151">Click the **Select** node, and in the Properties pane click the ellipsis (…) button against the **Properties** box.</span></span>  
  
3.  <span data-ttu-id="6aa32-152">Dans la fenêtre Éditeur de collections PropertyView, cliquez sur **ajouter**et dans le volet Propriétés, tapez **HttpHeaderUserName** pour le **nom** boîte.</span><span class="sxs-lookup"><span data-stu-id="6aa32-152">In the PropertyView Collection Editor window, click **Add**, and in the Property pane, type **HttpHeaderUserName** for the **Name** box.</span></span> <span data-ttu-id="6aa32-153">Type **MyUserHeader** pour le **PropertyValue** boîte.</span><span class="sxs-lookup"><span data-stu-id="6aa32-153">Type **MyUserHeader** for the **PropertyValue** box.</span></span> <span data-ttu-id="6aa32-154">Sélectionnez **System.String** pour le **Type** boîte.</span><span class="sxs-lookup"><span data-stu-id="6aa32-154">Select **System.String** for the **Type** box.</span></span>  
  
4.  <span data-ttu-id="6aa32-155">Dans la fenêtre Éditeur de collections PropertyView, cliquez sur **ajouter**et dans le volet Propriétés, tapez **HttpHeaderPassword** pour le **nom** boîte.</span><span class="sxs-lookup"><span data-stu-id="6aa32-155">In the PropertyView Collection Editor window, click **Add**, and in the Property pane, type **HttpHeaderPassword** for the **Name** box.</span></span> <span data-ttu-id="6aa32-156">De même, tapez **MyPasswordHeader** pour le **PropertyValue** boîte.</span><span class="sxs-lookup"><span data-stu-id="6aa32-156">Similarly, type **MyPasswordHeader** for the **PropertyValue** box.</span></span> <span data-ttu-id="6aa32-157">Sélectionnez **System.String** pour le **Type** boîte.</span><span class="sxs-lookup"><span data-stu-id="6aa32-157">Select **System.String** for the **Type** box.</span></span>  
  
     <span data-ttu-id="6aa32-158">![Ajouter une propriété](../../adapters-and-accelerators/adapter-oracle-ebs/media/07-propertviewcollection-editor.gif "07_PropertViewCollection_Editor")</span><span class="sxs-lookup"><span data-stu-id="6aa32-158">![Add a property](../../adapters-and-accelerators/adapter-oracle-ebs/media/07-propertviewcollection-editor.gif "07_PropertViewCollection_Editor")</span></span>  
  
5.  <span data-ttu-id="6aa32-159">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="6aa32-159">Click **OK**.</span></span>  
  
##  <a name="Scenario1"></a><span data-ttu-id="6aa32-160">Scénario 1 : Les requêtes pour les employés à l’aide d’un composant WebPart de liste de données métier</span><span class="sxs-lookup"><span data-stu-id="6aa32-160">Scenario 1: Query for Employees using a Business Data List Web Part</span></span>  
 <span data-ttu-id="6aa32-161">Pour créer un fichier de définition d’application qui peut être utilisé pour rechercher des employés à partir d’un composant WebPart de liste de données métier et basé sur le nom de l’employé, vous devez effectuer l’ensemble suivant de tâches.</span><span class="sxs-lookup"><span data-stu-id="6aa32-161">To create an application definition file that can be used to search for employees from a Business Data List Web Part and based on employee name, you must perform the following set of tasks.</span></span>  
  
1.  <span data-ttu-id="6aa32-162">Dans le **sélectionnez** (méthode), créer un filtre et mappez-le à le **filtre** paramètre.</span><span class="sxs-lookup"><span data-stu-id="6aa32-162">In the **Select** method, create a filter and map it to the **FILTER** parameter.</span></span>  
  
2.  <span data-ttu-id="6aa32-163">Créer un **recherche** instance de méthode pour le **sélectionnez** (méthode).</span><span class="sxs-lookup"><span data-stu-id="6aa32-163">Create a **Finder** method instance for the **Select** method.</span></span> <span data-ttu-id="6aa32-164">A **recherche** méthode récupère une liste d’enregistrements en fonction d’un filtre.</span><span class="sxs-lookup"><span data-stu-id="6aa32-164">A **Finder** method retrieves a list of records based on a filter.</span></span>  
  
#### <a name="to-create-a-filter-and-map-it-to-the-filter-parameter"></a><span data-ttu-id="6aa32-165">Pour créer un filtre et la mapper au paramètre de filtre</span><span class="sxs-lookup"><span data-stu-id="6aa32-165">To create a filter, and map it to the FILTER parameter</span></span>  
  
1.  <span data-ttu-id="6aa32-166">Créer un filtre.</span><span class="sxs-lookup"><span data-stu-id="6aa32-166">Create a filter.</span></span>  
  
    1.  <span data-ttu-id="6aa32-167">Dans le volet objets de métadonnées, développez le **employé** nœud, puis développez le **méthodes** nœud.</span><span class="sxs-lookup"><span data-stu-id="6aa32-167">In the Metadata Objects pane, expand the **Employee** node, and then expand the **Methods** node.</span></span>  
  
    2.  <span data-ttu-id="6aa32-168">Développez le **sélectionnez** (méthode), avec le bouton droit **filtres**, puis cliquez sur **ajouter un filtre**.</span><span class="sxs-lookup"><span data-stu-id="6aa32-168">Expand the **Select** method, right-click **Filters**, and then click **Add Filter**.</span></span>  
  
         <span data-ttu-id="6aa32-169">![Ajouter un filtre à la méthode SELECT](../../adapters-and-accelerators/adapter-oracle-ebs/media/08-add-filter.gif "08_Add_Filter")</span><span class="sxs-lookup"><span data-stu-id="6aa32-169">![Add a filter to the SELECT method](../../adapters-and-accelerators/adapter-oracle-ebs/media/08-add-filter.gif "08_Add_Filter")</span></span>  
  
    3.  <span data-ttu-id="6aa32-170">Dans le volet Propriétés, pour le **FilterType** propriété, sélectionnez **est égal à**.</span><span class="sxs-lookup"><span data-stu-id="6aa32-170">In the Properties pane, for the **FilterType** property, select **Equals**.</span></span>  
  
    4.  <span data-ttu-id="6aa32-171">Dans le volet Propriétés, tapez **EmployeeName** dans les **nom** boîte.</span><span class="sxs-lookup"><span data-stu-id="6aa32-171">In the Properties pane, type **EmployeeName** in the **Name** box.</span></span>  
  
         <span data-ttu-id="6aa32-172">![Spécifiez les propriétés de filtre](../../adapters-and-accelerators/adapter-oracle-ebs/media/09-filter-properties.gif "09_Filter_Properties")</span><span class="sxs-lookup"><span data-stu-id="6aa32-172">![Specify filter properties](../../adapters-and-accelerators/adapter-oracle-ebs/media/09-filter-properties.gif "09_Filter_Properties")</span></span>  
  
2.  <span data-ttu-id="6aa32-173">Mapper le filtre à la **filtre** paramètre dans le **sélectionnez** (méthode).</span><span class="sxs-lookup"><span data-stu-id="6aa32-173">Map the filter to the **FILTER** parameter in the **Select** method.</span></span>  
  
    1.  <span data-ttu-id="6aa32-174">Dans le volet objets de métadonnées, développez le **employé** nœud, puis développez le **méthodes** nœud.</span><span class="sxs-lookup"><span data-stu-id="6aa32-174">In the Metadata Objects pane, expand the **Employee** node, and then expand the **Methods** node.</span></span>  
  
    2.  <span data-ttu-id="6aa32-175">Développez le **sélectionnez** (méthode), puis développez le **paramètres** nœud.</span><span class="sxs-lookup"><span data-stu-id="6aa32-175">Expand the **Select** method, and then expand the **Parameters** node.</span></span>  
  
    3.  <span data-ttu-id="6aa32-176">Développez le **filtre** nœud, puis cliquez sur le deuxième **filtre** nœud.</span><span class="sxs-lookup"><span data-stu-id="6aa32-176">Expand the **FILTER** node, and click the second **FILTER** node.</span></span>  
  
    4.  <span data-ttu-id="6aa32-177">Dans le volet Propriétés, sélectionnez **EmployeeName** à partir de la **FilterDescriptor** liste.</span><span class="sxs-lookup"><span data-stu-id="6aa32-177">In the Properties pane, select **EmployeeName** from the **FilterDescriptor** list.</span></span>  
  
         <span data-ttu-id="6aa32-178">![Mapper le filtre au paramètre de méthode Select](../../adapters-and-accelerators/adapter-oracle-ebs/media/10-map-filter.gif "10_Map_Filter")</span><span class="sxs-lookup"><span data-stu-id="6aa32-178">![Map the filter to the Select method parameter](../../adapters-and-accelerators/adapter-oracle-ebs/media/10-map-filter.gif "10_Map_Filter")</span></span>  
  
#### <a name="to-create-a-finder-method-instance-for-the-select-method"></a><span data-ttu-id="6aa32-179">Pour créer une instance de méthode Finder pour la méthode Select</span><span class="sxs-lookup"><span data-stu-id="6aa32-179">To create a Finder method instance for the Select method</span></span>  
  
1.  <span data-ttu-id="6aa32-180">Dans le volet objets de métadonnées, développez le **employé** nœud, puis développez le **méthodes** nœud.</span><span class="sxs-lookup"><span data-stu-id="6aa32-180">In the Metadata Objects pane, expand the **Employee** node, and then expand the **Methods** node.</span></span>  
  
2.  <span data-ttu-id="6aa32-181">Développez le **sélectionnez** nœud, avec le bouton droit **Instances**, puis cliquez sur **ajouter une Instance de méthode**.</span><span class="sxs-lookup"><span data-stu-id="6aa32-181">Expand the **Select** node, right-click **Instances**, and then click **Add Method Instance**.</span></span>  
  
     <span data-ttu-id="6aa32-182">![Ajouter une instance de méthode](../../adapters-and-accelerators/adapter-oracle-ebs/media/11-add-method-instance.gif "11_Add_Method_Instance")</span><span class="sxs-lookup"><span data-stu-id="6aa32-182">![Add a method instance](../../adapters-and-accelerators/adapter-oracle-ebs/media/11-add-method-instance.gif "11_Add_Method_Instance")</span></span>  
  
3.  <span data-ttu-id="6aa32-183">Dans la fenêtre Créer une Instance de méthode, cliquez sur **recherche** pour **Type d’Instance de méthode**.</span><span class="sxs-lookup"><span data-stu-id="6aa32-183">In the Create Method Instance window, click **Finder** for **Method Instance Type**.</span></span> <span data-ttu-id="6aa32-184">Sélectionnez **retourner** pour **TypeDescriptor de retour**.</span><span class="sxs-lookup"><span data-stu-id="6aa32-184">Select **Return** for **Return TypeDescriptor**.</span></span>  
  
     <span data-ttu-id="6aa32-185">![Créer une instance de méthode Finder](../../adapters-and-accelerators/adapter-oracle-ebs/media/12-create-method-instance.gif "12_Create_Method_Instance")</span><span class="sxs-lookup"><span data-stu-id="6aa32-185">![Create a Finder method instance](../../adapters-and-accelerators/adapter-oracle-ebs/media/12-create-method-instance.gif "12_Create_Method_Instance")</span></span>  
  
4.  <span data-ttu-id="6aa32-186">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="6aa32-186">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="6aa32-187">Dans le volet Propriétés, tapez **Finder_Instance** dans les **nom** boîte.</span><span class="sxs-lookup"><span data-stu-id="6aa32-187">In the Properties pane, type **Finder_Instance** in the **Name** box.</span></span>  
  
     <span data-ttu-id="6aa32-188">![Spécifiez un nom pour l’instance de méthode Finder](../../adapters-and-accelerators/adapter-oracle-ebs/media/13-instance-property.gif "13_Instance_Property")</span><span class="sxs-lookup"><span data-stu-id="6aa32-188">![Specify a name for the Finder method instance](../../adapters-and-accelerators/adapter-oracle-ebs/media/13-instance-property.gif "13_Instance_Property")</span></span>  
  
##  <a name="Scenario2"></a><span data-ttu-id="6aa32-189">Scénario 2 : Recherche de texte intégral sur la Table d’Interface MS_SAMPLE_EMPLOYEE à partir de Microsoft Office SharePoint Server</span><span class="sxs-lookup"><span data-stu-id="6aa32-189">Scenario 2: Full-Text Search on MS_SAMPLE_EMPLOYEE Interface Table from Microsoft Office SharePoint Server</span></span>  
 <span data-ttu-id="6aa32-190">Pour créer un fichier de définition d’application qui peut être utilisé pour effectuer une recherche en texte intégral sur la table d’interface MS_SAMPLE_EMPLOYEE à partir de Microsoft Office SharePoint Server, vous devez effectuer l’ensemble suivant de tâches.</span><span class="sxs-lookup"><span data-stu-id="6aa32-190">To create an application definition file that can be used to perform a full-text search on MS_SAMPLE_EMPLOYEE interface table from Microsoft Office SharePoint Server, you must perform the following set of tasks.</span></span>  
  
-   <span data-ttu-id="6aa32-191">Dans le **sélectionnez** (méthode), créer un identificateur et le mapper au paramètre filtre et la valeur de retour qui stocke le nom de l’employé.</span><span class="sxs-lookup"><span data-stu-id="6aa32-191">In the **Select** method, create an identifier, and map it to the FILTER parameter and the return value that stores the employee name.</span></span>  
  
-   <span data-ttu-id="6aa32-192">Créer un **recherche spécifique** instance de méthode pour le **sélectionnez**.</span><span class="sxs-lookup"><span data-stu-id="6aa32-192">Create a **Specific Finder** method instance for the **Select**.</span></span> <span data-ttu-id="6aa32-193">Le **recherche spécifique** méthode trouve un enregistrement spécifique en fonction de l’identificateur, autrement dit, un nom d’employé.</span><span class="sxs-lookup"><span data-stu-id="6aa32-193">The **Specific Finder** method will find a specific record based on the identifier, that is, an employee name.</span></span>  
  
-   <span data-ttu-id="6aa32-194">Créer une instance de méthode énumérateur d’ID.</span><span class="sxs-lookup"><span data-stu-id="6aa32-194">Create an ID Enumerator method instance.</span></span>  
  
#### <a name="to-create-an-identifier-and-map-it-to-the-filter-parameter-and-employee-name-return-value"></a><span data-ttu-id="6aa32-195">Pour créer un identificateur et mapper pour le nom du paramètre et employé filtre valeur de retour</span><span class="sxs-lookup"><span data-stu-id="6aa32-195">To create an identifier, and map it to the FILTER parameter and employee name return value</span></span>  
  
1.  <span data-ttu-id="6aa32-196">Créer un identificateur pour le **employé** entité.</span><span class="sxs-lookup"><span data-stu-id="6aa32-196">Create an identifier for the **Employee** entity.</span></span>  
  
    1.  <span data-ttu-id="6aa32-197">Dans le volet objets de métadonnées, développez le **employé** nœud.</span><span class="sxs-lookup"><span data-stu-id="6aa32-197">In the Metadata Objects pane, expand the **Employee** node.</span></span>  
  
    2.  <span data-ttu-id="6aa32-198">Cliquez sur le **identificateurs** nœud et sélectionnez **ajouter un identificateur**.</span><span class="sxs-lookup"><span data-stu-id="6aa32-198">Right-click the **Identifiers** node, and then select **Add Identifier**.</span></span>  
  
         <span data-ttu-id="6aa32-199">![Créer un identificateur](../../adapters-and-accelerators/adapter-oracle-ebs/media/14-create-identifier.gif "14_Create_Identifier")</span><span class="sxs-lookup"><span data-stu-id="6aa32-199">![Create an Identifier](../../adapters-and-accelerators/adapter-oracle-ebs/media/14-create-identifier.gif "14_Create_Identifier")</span></span>  
  
    3.  <span data-ttu-id="6aa32-200">Dans le volet Propriétés, tapez **EmployeeName** dans les **nom** boîte.</span><span class="sxs-lookup"><span data-stu-id="6aa32-200">In the Properties pane, type **EmployeeName** in the **Name** box.</span></span>  
  
    4.  <span data-ttu-id="6aa32-201">Sélectionnez **System.String** pour le **Type** boîte.</span><span class="sxs-lookup"><span data-stu-id="6aa32-201">Select **System.String** for the **Type** box.</span></span>  
  
         <span data-ttu-id="6aa32-202">![Spécifiez les propriétés de l’identificateur](../../adapters-and-accelerators/adapter-oracle-ebs/media/15-identifier-properties.gif "15_Identifier_Properties")</span><span class="sxs-lookup"><span data-stu-id="6aa32-202">![Specify identifier properties](../../adapters-and-accelerators/adapter-oracle-ebs/media/15-identifier-properties.gif "15_Identifier_Properties")</span></span>  
  
2.  <span data-ttu-id="6aa32-203">Mapper l’identificateur pour le paramètre de filtre pour le **sélectionnez** (méthode).</span><span class="sxs-lookup"><span data-stu-id="6aa32-203">Map the identifier to the FILTER parameter for the **Select** method.</span></span>  
  
    1.  <span data-ttu-id="6aa32-204">Dans le volet objets de métadonnées, développez le **employé** nœud, puis développez le **méthodes** nœud.</span><span class="sxs-lookup"><span data-stu-id="6aa32-204">In the Metadata Objects pane, expand the **Employee** node, and then expand the **Methods** node.</span></span>  
  
    2.  <span data-ttu-id="6aa32-205">Développez le **sélectionnez** (méthode), puis développez le **paramètres** nœud.</span><span class="sxs-lookup"><span data-stu-id="6aa32-205">Expand the **Select** method, and then expand the **Parameters** node.</span></span>  
  
    3.  <span data-ttu-id="6aa32-206">Développez le **filtre** paramètre, puis cliquez sur le deuxième **filtre** nœud.</span><span class="sxs-lookup"><span data-stu-id="6aa32-206">Expand the **FILTER** parameter, and then click the second **FILTER** node.</span></span>  
  
    4.  <span data-ttu-id="6aa32-207">Dans le volet Propriétés, sélectionnez **EmployeeName [Employee]** à partir de la **identificateur** liste.</span><span class="sxs-lookup"><span data-stu-id="6aa32-207">In the Properties pane, select **EmployeeName[Employee]** from the **Identifier** list.</span></span>  
  
         <span data-ttu-id="6aa32-208">![Définition d’identificateur pour le paramètre FILTER](../../adapters-and-accelerators/adapter-oracle-ebs/media/16-set-identifier.gif "16_Set_Identifier")</span><span class="sxs-lookup"><span data-stu-id="6aa32-208">![Setting identifier for the FILTER parameter](../../adapters-and-accelerators/adapter-oracle-ebs/media/16-set-identifier.gif "16_Set_Identifier")</span></span>  
  
3.  <span data-ttu-id="6aa32-209">Mapper l’identificateur à la valeur de retour du nom employé.</span><span class="sxs-lookup"><span data-stu-id="6aa32-209">Map the identifier to the employee name return value.</span></span>  
  
    1.  <span data-ttu-id="6aa32-210">Dans le volet objets de métadonnées, développez le **employé** nœud, puis développez le **méthodes** nœud.</span><span class="sxs-lookup"><span data-stu-id="6aa32-210">In the Metadata Objects pane, expand the **Employee** node, and then expand the **Methods** node.</span></span>  
  
    2.  <span data-ttu-id="6aa32-211">Développez le **sélectionnez** (méthode), puis développez le **paramètres** nœud.</span><span class="sxs-lookup"><span data-stu-id="6aa32-211">Expand the **Select** method, and then expand the **Parameters** node.</span></span>  
  
    3.  <span data-ttu-id="6aa32-212">Développez le **retourner** nœud, puis le deuxième **retourner** nœud, puis le **élément** nœud, puis cliquez sur le **nom** nœud.</span><span class="sxs-lookup"><span data-stu-id="6aa32-212">Expand the **Return** node, then the second **Return** node, then the **Item** node, and then click the **Name** node.</span></span>  
  
    4.  <span data-ttu-id="6aa32-213">Dans le volet Propriétés, sélectionnez **EmployeeName [Employee]** à partir de la **identificateur** liste.</span><span class="sxs-lookup"><span data-stu-id="6aa32-213">In the Properties pane, select **EmployeeName[Employee]** from the **Identifier** list.</span></span>  
  
#### <a name="to-create-a-specific-finder-method-instance-for-the-select-method"></a><span data-ttu-id="6aa32-214">Pour créer une instance de méthode Finder spécifique pour la méthode Select</span><span class="sxs-lookup"><span data-stu-id="6aa32-214">To create a Specific Finder method instance for the Select method</span></span>  
  
1.  <span data-ttu-id="6aa32-215">Dans le volet objets de métadonnées, développez le **employé** nœud, puis le **méthodes** nœud.</span><span class="sxs-lookup"><span data-stu-id="6aa32-215">In the Metadata Objects pane, expand the **Employee** node, and then the **Methods** node.</span></span>  
  
2.  <span data-ttu-id="6aa32-216">Développez le **sélectionnez** nœud, avec le bouton droit **Instances**, puis sélectionnez **ajouter une Instance de méthode** pour ouvrir la fenêtre Créer une Instance de méthode.</span><span class="sxs-lookup"><span data-stu-id="6aa32-216">Expand the **Select** node, right-click **Instances**, and then select **Add Method Instance** to open the Create Method Instance window.</span></span>  
  
     <span data-ttu-id="6aa32-217">![Ajouter une instance de méthode](../../adapters-and-accelerators/adapter-oracle-ebs/media/11-add-method-instance.gif "11_Add_Method_Instance")</span><span class="sxs-lookup"><span data-stu-id="6aa32-217">![Add a method instance](../../adapters-and-accelerators/adapter-oracle-ebs/media/11-add-method-instance.gif "11_Add_Method_Instance")</span></span>  
  
3.  <span data-ttu-id="6aa32-218">Dans la fenêtre Créer une Instance de méthode, sélectionnez **recherche spécifique** pour **Type d’Instance de méthode**.</span><span class="sxs-lookup"><span data-stu-id="6aa32-218">In the Create Method Instance window, select **Specific Finder** for **Method Instance Type**.</span></span> <span data-ttu-id="6aa32-219">Sélectionnez **retourner** pour **TypeDescriptor de retour**.</span><span class="sxs-lookup"><span data-stu-id="6aa32-219">Select **Return** for **Return TypeDescriptor**.</span></span>  
  
     <span data-ttu-id="6aa32-220">![Ajouter une instance de méthode Finder spécifique](../../adapters-and-accelerators/adapter-oracle-ebs/media/17-specific-finder.gif "17_Specific_Finder")</span><span class="sxs-lookup"><span data-stu-id="6aa32-220">![Add a Specific Finder method instance](../../adapters-and-accelerators/adapter-oracle-ebs/media/17-specific-finder.gif "17_Specific_Finder")</span></span>  
  
4.  <span data-ttu-id="6aa32-221">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="6aa32-221">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="6aa32-222">Dans le volet Propriétés, tapez **SpeciFinder_Instance** pour le **nom** boîte.</span><span class="sxs-lookup"><span data-stu-id="6aa32-222">In the Properties pane, type **SpeciFinder_Instance** for the **Name** box.</span></span>  
  
#### <a name="to-create-an-id-enumerator-method-instance-for-the-select-method"></a><span data-ttu-id="6aa32-223">Pour créer une instance de méthode énumérateur d’Id pour la méthode Select</span><span class="sxs-lookup"><span data-stu-id="6aa32-223">To create an Id Enumerator method instance for the Select method</span></span>  
  
1.  <span data-ttu-id="6aa32-224">Dans le volet objets de métadonnées, développez le **employé** nœud, puis le **méthodes** nœud.</span><span class="sxs-lookup"><span data-stu-id="6aa32-224">In the Metadata Objects pane, expand the **Employee** node, and then the **Methods** node.</span></span>  
  
2.  <span data-ttu-id="6aa32-225">Développez le **sélectionnez** nœud, avec le bouton droit **Instances**, puis sélectionnez **ajouter une Instance de méthode** pour ouvrir la fenêtre Créer une Instance de méthode.</span><span class="sxs-lookup"><span data-stu-id="6aa32-225">Expand the **Select** node, right-click **Instances**, and then select **Add Method Instance** to open the Create Method Instance window.</span></span>  
  
     <span data-ttu-id="6aa32-226">![Ajouter une instance de méthode](../../adapters-and-accelerators/adapter-oracle-ebs/media/11-add-method-instance.gif "11_Add_Method_Instance")</span><span class="sxs-lookup"><span data-stu-id="6aa32-226">![Add a method instance](../../adapters-and-accelerators/adapter-oracle-ebs/media/11-add-method-instance.gif "11_Add_Method_Instance")</span></span>  
  
3.  <span data-ttu-id="6aa32-227">Dans la fenêtre Créer une Instance de méthode, sélectionnez **énumérateur d’Id** pour **Type d’Instance de méthode**.</span><span class="sxs-lookup"><span data-stu-id="6aa32-227">In the Create Method Instance window, select **Id Enumerator** for **Method Instance Type**.</span></span> <span data-ttu-id="6aa32-228">Sélectionnez **retourner** pour **TypeDescriptor de retour**.</span><span class="sxs-lookup"><span data-stu-id="6aa32-228">Select **Return** for **Return TypeDescriptor**.</span></span>  
  
     <span data-ttu-id="6aa32-229">![Créer une instance de méthode énumérateur d’Id](../../adapters-and-accelerators/adapter-oracle-ebs/media/18-id-enumerator.gif "18_ID_Enumerator")</span><span class="sxs-lookup"><span data-stu-id="6aa32-229">![Create an Id Enumerator method instance](../../adapters-and-accelerators/adapter-oracle-ebs/media/18-id-enumerator.gif "18_ID_Enumerator")</span></span>  
  
4.  <span data-ttu-id="6aa32-230">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="6aa32-230">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="6aa32-231">Dans le volet Propriétés, tapez **IDEnumerator_Instance** pour le **nom** boîte.</span><span class="sxs-lookup"><span data-stu-id="6aa32-231">In the Properties pane, type **IDEnumerator_Instance** for the **Name** box.</span></span>  
  
##  <a name="Defaults"></a><span data-ttu-id="6aa32-232">Définir les paramètres par défaut pour les Instances (méthode)</span><span class="sxs-lookup"><span data-stu-id="6aa32-232">Set Default Parameters for the Method Instances</span></span>  
 <span data-ttu-id="6aa32-233">La méthode Select vous oblige à spécifier les noms de colonnes.</span><span class="sxs-lookup"><span data-stu-id="6aa32-233">The Select method requires you to specify the column names.</span></span> <span data-ttu-id="6aa32-234">Par conséquent, vous devez spécifier une valeur par défaut pour le **les noms de colonne** paramètre pour les instances de méthode Finder, recherche spécifique et que l’énumérateur d’Id a été créé précédemment.</span><span class="sxs-lookup"><span data-stu-id="6aa32-234">Therefore, you need to specify a default value for the **COLUMN_NAMES** parameter for the Finder, Specific Finder, and Id Enumerator method instances created earlier.</span></span> <span data-ttu-id="6aa32-235">En outre, vous devez également spécifier une valeur par défaut pour le **filtre** paramètre pour l’instance de méthode énumérateur d’Id.</span><span class="sxs-lookup"><span data-stu-id="6aa32-235">Additionally, you should also specify a default value for the **FILTER** parameter for the Id Enumerator method instance.</span></span>  
  
#### <a name="to-set-the-default-parameters-for-the-method-instances"></a><span data-ttu-id="6aa32-236">Pour définir les paramètres par défaut pour les instances (méthode)</span><span class="sxs-lookup"><span data-stu-id="6aa32-236">To set the default parameters for the method instances</span></span>  
  
1.  <span data-ttu-id="6aa32-237">Dans le volet objets de métadonnées, développez le **employé** nœud, puis développez le **méthodes** nœud.</span><span class="sxs-lookup"><span data-stu-id="6aa32-237">In the Metadata Objects pane, expand the **Employee** node, and then expand the **Methods** node.</span></span>  
  
2.  <span data-ttu-id="6aa32-238">Développez le **sélectionnez** nœud, puis développez le **paramètres** nœud.</span><span class="sxs-lookup"><span data-stu-id="6aa32-238">Expand the **Select** node, and then expand the **Parameters** node.</span></span>  
  
3.  <span data-ttu-id="6aa32-239">Développez le **les noms de colonne** nœud, puis sélectionnez le **les noms de colonne** paramètre.</span><span class="sxs-lookup"><span data-stu-id="6aa32-239">Expand the **COLUMN_NAMES** node, and then select the **COLUMN_NAMES** parameter.</span></span>  
  
4.  <span data-ttu-id="6aa32-240">Dans le volet Propriétés, cliquez sur le bouton de sélection (...) contre le **DefaultValues** boîte.</span><span class="sxs-lookup"><span data-stu-id="6aa32-240">In the Properties pane, click the ellipsis button (…) against the **DefaultValues** box.</span></span>  
  
5.  <span data-ttu-id="6aa32-241">Dans le **l’éditeur de collections DefaultValueView** boîte de dialogue, cliquez sur **ajouter**, dans le volet des propriétés, cliquez sur **Finder_Instance** dans le  **SelectMethodInstance** liste.</span><span class="sxs-lookup"><span data-stu-id="6aa32-241">In the **DefaultValueView Collection Editor** dialog box, click **Add**, and in the property pane, click **Finder_Instance** in the **SelectMethodInstance** list.</span></span>  
  
     <span data-ttu-id="6aa32-242">![En spécifiant la valeur par défaut pour l’instance Finder](../../adapters-and-accelerators/adapter-oracle-ebs/media/19-finderinstance-defaults.gif "19_FinderInstance_Defaults")</span><span class="sxs-lookup"><span data-stu-id="6aa32-242">![Specifying default value for the Finder instance](../../adapters-and-accelerators/adapter-oracle-ebs/media/19-finderinstance-defaults.gif "19_FinderInstance_Defaults")</span></span>  
  
6.  <span data-ttu-id="6aa32-243">Type `*` dans les **valeur** boîte.</span><span class="sxs-lookup"><span data-stu-id="6aa32-243">Type `*` in the **Value** box.</span></span>  
  
7.  <span data-ttu-id="6aa32-244">De même, répétez les étapes 5 et 6 pour ajouter des valeurs par défaut pour le **SpecificFinder_Instance** et **IDEnumerator_Instance** instances de méthode.</span><span class="sxs-lookup"><span data-stu-id="6aa32-244">Similarly, repeat steps 5 and 6 to add default values for the **SpecificFinder_Instance** and **IDEnumerator_Instance** method instances.</span></span>  
  
8.  <span data-ttu-id="6aa32-245">Dans le **l’éditeur de collections DefaultValueView** boîte de dialogue, cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="6aa32-245">In the **DefaultValueView Collection Editor** dialog box, click **OK**.</span></span>  
  
9. <span data-ttu-id="6aa32-246">Ensuite, ajoutez une valeur par défaut pour le **filtre** paramètre pour le **IDEnumerator_Instance** instance de méthode.</span><span class="sxs-lookup"><span data-stu-id="6aa32-246">Next, add a default value for the **FILTER** parameter for the **IDEnumerator_Instance** method instance.</span></span> <span data-ttu-id="6aa32-247">Développez le **filtre** nœud, puis sélectionnez le **filtre** paramètre.</span><span class="sxs-lookup"><span data-stu-id="6aa32-247">Expand the **FILTER** node, and then select the **FILTER** parameter.</span></span>  
  
10. <span data-ttu-id="6aa32-248">Dans le volet Propriétés, cliquez sur le bouton de sélection (...) contre le **DefaultValues** boîte.</span><span class="sxs-lookup"><span data-stu-id="6aa32-248">In the Properties pane, click the ellipsis button (…) against the **DefaultValues** box.</span></span>  
  
11. <span data-ttu-id="6aa32-249">Dans le **l’éditeur de collections DefaultValueView** boîte de dialogue, cliquez sur **ajouter**, dans le volet des propriétés, cliquez sur **IDEnumerator_Instance** dans le  **SelectMethodInstance** liste.</span><span class="sxs-lookup"><span data-stu-id="6aa32-249">In the **DefaultValueView Collection Editor** dialog box, click **Add**, and in the property pane, click **IDEnumerator_Instance** in the **SelectMethodInstance** list.</span></span>  
  
12. <span data-ttu-id="6aa32-250">Type `%` dans les **valeur** boîte.</span><span class="sxs-lookup"><span data-stu-id="6aa32-250">Type `%` in the **Value** box.</span></span>  
  
     <span data-ttu-id="6aa32-251">![Valeurs par défaut pour l’instance de l’énumérateur d’Id](../../adapters-and-accelerators/adapter-oracle-ebs/media/20-idenumeratorinstance-defaults.gif "20_IDEnumeratorInstance_Defaults")</span><span class="sxs-lookup"><span data-stu-id="6aa32-251">![Default values for the Id Enumerator instance](../../adapters-and-accelerators/adapter-oracle-ebs/media/20-idenumeratorinstance-defaults.gif "20_IDEnumeratorInstance_Defaults")</span></span>  
  
13. <span data-ttu-id="6aa32-252">Dans le **l’éditeur de collections DefaultValueView** boîte de dialogue, cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="6aa32-252">In the **DefaultValueView Collection Editor** dialog box, click **OK**.</span></span>  
  
##  <a name="SSO"></a><span data-ttu-id="6aa32-253">Valeur de l’authentification unique pour la connexion à Oracle E-Business Suite</span><span class="sxs-lookup"><span data-stu-id="6aa32-253">Set up Single Sign-On for Connecting to Oracle E-Business Suite</span></span>  
 <span data-ttu-id="6aa32-254">Une fois que vous avez terminé d’exécuter toutes les procédures dans cette rubrique, vous avez créé un fichier de définition d’application qui peut être importé dans une application SharePoint.</span><span class="sxs-lookup"><span data-stu-id="6aa32-254">After you have finished performing all the procedures in this topic, you will have created an application definition file that can be imported into a SharePoint application.</span></span> <span data-ttu-id="6aa32-255">À partir de l’application, vous appelez les méthodes pour récupérer les données pertinentes à partir d’Oracle E-Business Suite.</span><span class="sxs-lookup"><span data-stu-id="6aa32-255">From the application, you invoke the methods to retrieve relevant data from Oracle E-Business Suite.</span></span> <span data-ttu-id="6aa32-256">Pour ce faire, vous devez créer un mappage entre un utilisateur dans Oracle E-Business Suite et de l’utilisateur dans l’application SharePoint.</span><span class="sxs-lookup"><span data-stu-id="6aa32-256">To enable this, you must create a mapping between a user in the Oracle E-Business Suite and the user in the SharePoint application.</span></span> <span data-ttu-id="6aa32-257">Vous créez ce mappage dans la console d’Administration centrale de SharePoint après avoir importé le fichier de définition d’application.</span><span class="sxs-lookup"><span data-stu-id="6aa32-257">You create this mapping in SharePoint Central Administration console after you have imported the application definition file.</span></span>  
  
 <span data-ttu-id="6aa32-258">Toutefois, pour créer le mappage, vous devez définir une propriété **SecondarySsoApplicationId** dans Business Data Catalog Definition Editor.</span><span class="sxs-lookup"><span data-stu-id="6aa32-258">However, to create the mapping you must set a property **SecondarySsoApplicationId** in the Business Data Catalog Definition Editor.</span></span>  
  
#### <a name="to-set-the-secondaryssoapplicationid-property"></a><span data-ttu-id="6aa32-259">Pour définir la propriété SecondarySsoApplicationId</span><span class="sxs-lookup"><span data-stu-id="6aa32-259">To set the SecondarySsoApplicationId property</span></span>  
  
1.  <span data-ttu-id="6aa32-260">Dans le volet objets de métadonnées, développez le **MS_SAMPLE_EMPLOYEE** nœud, puis développez le **Instances** nœud.</span><span class="sxs-lookup"><span data-stu-id="6aa32-260">In the Metadata Objects pane, expand the **MS_SAMPLE_EMPLOYEE** node, and then expand the **Instances** node.</span></span>  
  
2.  <span data-ttu-id="6aa32-261">Cliquez sur **MS_SAMPLE_EMPLOYEE_Instance**, dans le volet Propriétés, cliquez sur le bouton de sélection (...) par rapport à la **propriétés** boîte.</span><span class="sxs-lookup"><span data-stu-id="6aa32-261">Click **MS_SAMPLE_EMPLOYEE_Instance**, and in the Properties pane, click the ellipsis (…) button against the **Properties** box.</span></span>  
  
3.  <span data-ttu-id="6aa32-262">Dans le **l’éditeur de collections PropertyView** boîte de dialogue, cliquez sur **ajouter**et dans le volet Propriétés, tapez **SecondarySsoApplicationId** pour le **nom** boîte.</span><span class="sxs-lookup"><span data-stu-id="6aa32-262">In the **PropertyView Collection Editor** dialog box, click **Add**, and in the Property pane, type **SecondarySsoApplicationId** for the **Name** box.</span></span> <span data-ttu-id="6aa32-263">De même, tapez **OracleSSO** pour le **PropertyValue** boîte.</span><span class="sxs-lookup"><span data-stu-id="6aa32-263">Similarly, type **OracleSSO** for the **PropertyValue** box.</span></span> <span data-ttu-id="6aa32-264">Sélectionnez **System.String** pour le **Type** boîte.</span><span class="sxs-lookup"><span data-stu-id="6aa32-264">Select **System.String** for the **Type** box.</span></span>  
  
     <span data-ttu-id="6aa32-265">![Ajouter la propriété SSO](../../adapters-and-accelerators/adapter-oracle-ebs/media/21-sso.gif "21_SSO")</span><span class="sxs-lookup"><span data-stu-id="6aa32-265">![Add the SSO Property](../../adapters-and-accelerators/adapter-oracle-ebs/media/21-sso.gif "21_SSO")</span></span>  
  
4.  <span data-ttu-id="6aa32-266">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="6aa32-266">Click **OK**.</span></span>  
  
##  <a name="Export"></a><span data-ttu-id="6aa32-267">Exporter la définition d’Application dans un fichier</span><span class="sxs-lookup"><span data-stu-id="6aa32-267">Export the Application Definition to a File</span></span>  
 <span data-ttu-id="6aa32-268">Vous venez de créer une définition d’application qui contient les métadonnées de l’instance Oracle E-Business Suite.</span><span class="sxs-lookup"><span data-stu-id="6aa32-268">You have now created an application definition that contains Oracle E-Business Suite instance metadata.</span></span> <span data-ttu-id="6aa32-269">Vous devez exporter cette définition dans un fichier XML, qui peut être importé dans Microsoft Office SharePoint Server.</span><span class="sxs-lookup"><span data-stu-id="6aa32-269">You must export this definition to an XML file, which can be imported into Microsoft Office SharePoint Server.</span></span>  
  
#### <a name="to-export-the-application-definition-to-a-file"></a><span data-ttu-id="6aa32-270">Pour exporter la définition d’application dans un fichier</span><span class="sxs-lookup"><span data-stu-id="6aa32-270">To export the application definition to a file</span></span>  
  
1.  <span data-ttu-id="6aa32-271">Dans le volet objets de métadonnées, cliquez sur le **MS_SAMPLE_EMPLOYEE** nœud, puis cliquez sur **exporter**.</span><span class="sxs-lookup"><span data-stu-id="6aa32-271">In the Metadata Objects pane, right-click the **MS_SAMPLE_EMPLOYEE** node, and then click **Export**.</span></span>  
  
2.  <span data-ttu-id="6aa32-272">Enregistrez le fichier sous Employee.xml.</span><span class="sxs-lookup"><span data-stu-id="6aa32-272">Save the file as Employee.xml.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="6aa32-273">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="6aa32-273">Next Steps</span></span>  
 <span data-ttu-id="6aa32-274">Vous devez maintenant créer une application SharePoint pour récupérer des données à partir d’Oracle E-Business Suite.</span><span class="sxs-lookup"><span data-stu-id="6aa32-274">You must now create a SharePoint application to retrieve data from Oracle E-Business Suite.</span></span> <span data-ttu-id="6aa32-275">Pour obtenir des instructions, consultez [étape 3 : créer une Application SharePoint pour récupérer des données à partir d’Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/step-3-create-a-sharepoint-application-to-retrieve-data-from-oracle-ebs.md).</span><span class="sxs-lookup"><span data-stu-id="6aa32-275">For instructions, see [Step 3: Create a SharePoint Application to Retrieve Data from Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/step-3-create-a-sharepoint-application-to-retrieve-data-from-oracle-ebs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6aa32-276">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6aa32-276">See Also</span></span>  
 [<span data-ttu-id="6aa32-277">Didacticiel : Présenter les données à partir d’Oracle E-Business Suite sur un Site SharePoint</span><span class="sxs-lookup"><span data-stu-id="6aa32-277">Tutorial: Present Data from Oracle E-Business Suite on a SharePoint Site</span></span>](Tutorial:%20Present%20data%20from%20Oracle%20E-Business%20Suite%20on%20a%20SharePoint%20Site.md)