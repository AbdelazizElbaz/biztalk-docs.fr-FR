---
title: "Étape 2 : Créer un fichier de définition d’Application pour les artefacts SAP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application definition file, creating a
- Business Data Catalog Definition Editor
- Business Data Catalog
ms.assetid: d254b00e-dbeb-4167-ad57-6f0aa2e7a563
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0d334b885b1135fb429655200090671a2a750ec0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-2-create-an-application-definition-file-for-the-sap-artifacts"></a><span data-ttu-id="613db-102">Étape 2 : Créer un fichier de définition d’Application pour les artefacts SAP</span><span class="sxs-lookup"><span data-stu-id="613db-102">Step 2: Create an Application Definition File for the SAP Artifacts</span></span>
<span data-ttu-id="613db-103">![Étape 2 sur 4](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-2of4.gif "Step_2of4")</span><span class="sxs-lookup"><span data-stu-id="613db-103">![Step 2 of 4](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-2of4.gif "Step_2of4")</span></span>  
  
 <span data-ttu-id="613db-104">**Durée :** 15 minutes</span><span class="sxs-lookup"><span data-stu-id="613db-104">**Time to complete:** 15 minutes</span></span>  
  
 <span data-ttu-id="613db-105">**Objectif :** la fonctionnalité de catalogue de données métiers dans Microsoft SharePoint Server expose et incorpore des données à partir d’applications de métier (LOB) dans des portails.</span><span class="sxs-lookup"><span data-stu-id="613db-105">**Objective:** The Business Data Catalog feature in Microsoft SharePoint Server exposes and incorporates data from line-of-business (LOB) applications into portals.</span></span> <span data-ttu-id="613db-106">Pour intégrer ces données dans votre site portail, vous devez générer un fichier de définition d’application Microsoft Office SharePoint Server peut consommer.</span><span class="sxs-lookup"><span data-stu-id="613db-106">To incorporate this data into your portal site, you must build an application definition file that Microsoft Office SharePoint Server can consume.</span></span>  
  
 <span data-ttu-id="613db-107">L’outil Business Data Catalog Definition Editor, disponible avec le SDK Microsoft Office SharePoint Server 2007, vous permet de créer un fichier de définition d’application pour le catalogue de données métiers.</span><span class="sxs-lookup"><span data-stu-id="613db-107">The Business Data Catalog Definition Editor tool, available with Microsoft Office SharePoint Server 2007 SDK,enables you to create an application definition file for the Business Data Catalog.</span></span> <span data-ttu-id="613db-108">Cet outil génère automatiquement un fichier XML pour le fichier de définition, vous n’avez pas besoin de créer manuellement le fichier dans un document XML éditeur.</span><span class="sxs-lookup"><span data-stu-id="613db-108">This tool automatically generates an XML file for the definition file, so you do not need to manually create the file in an XML editor.</span></span>  
  
 <span data-ttu-id="613db-109">L’objectif de l’application Microsoft Office SharePoint Server que vous créez est de :</span><span class="sxs-lookup"><span data-stu-id="613db-109">The purpose of the Microsoft Office SharePoint Server application that you are creating is to:</span></span>  
  
-   <span data-ttu-id="613db-110">Rechercher un client dans le système SAP basé sur un nom de client.</span><span class="sxs-lookup"><span data-stu-id="613db-110">Search for a customer in the SAP system based on a customer name.</span></span>  
  
-   <span data-ttu-id="613db-111">Sélectionnez un client dans la liste des clients d’extraction et de récupérer les détails pour le client.</span><span class="sxs-lookup"><span data-stu-id="613db-111">Select a customer from the list of fetched customers and retrieve the details for the customer.</span></span>  
  
-   <span data-ttu-id="613db-112">Sélectionnez un client dans la liste des clients d’extraction et de récupérer les commandes client pour le client.</span><span class="sxs-lookup"><span data-stu-id="613db-112">Select a customer from the list of fetched customers and retrieve the sales orders for the customer.</span></span>  
  
 <span data-ttu-id="613db-113">Pour chacune de ces exigences, vous devez effectuer un ensemble de tâches dans l’outil Éditeur de définition de catalogue de données métier.</span><span class="sxs-lookup"><span data-stu-id="613db-113">For each of these requirements, you must complete a set of tasks in the Business Data Catalog Definition Editor tool.</span></span> <span data-ttu-id="613db-114">Cette rubrique fournit des instructions sur la façon d’effectuer ces tâches.</span><span class="sxs-lookup"><span data-stu-id="613db-114">This topic provides instructions on how to perform these tasks.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="613db-115">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="613db-115">Prerequisites</span></span>  
  
-   <span data-ttu-id="613db-116">Assurez-vous que vous disposez de l’éditeur de définition de catalogue de données métier installé avec le SDK de Microsoft Office SharePoint Server 2007.</span><span class="sxs-lookup"><span data-stu-id="613db-116">Be sure that you have the Business Data Catalog Definition Editor installed as part of the Microsoft Office SharePoint Server 2007 SDK.</span></span> <span data-ttu-id="613db-117">Vous pouvez télécharger le Kit de développement logiciel à partir de [http://go.microsoft.com/fwlink/?LinkId=104130](http://go.microsoft.com/fwlink/?LinkId=104130).</span><span class="sxs-lookup"><span data-stu-id="613db-117">You can download the SDK from [http://go.microsoft.com/fwlink/?LinkId=104130](http://go.microsoft.com/fwlink/?LinkId=104130).</span></span>  
  
-   <span data-ttu-id="613db-118">Publier le service WCF, comme décrit dans [étape 1 : publier les artefacts SAP comme un Service WCF](../../adapters-and-accelerators/adapter-sap/step-1-publish-the-sap-artifacts-as-a-wcf-service.md).</span><span class="sxs-lookup"><span data-stu-id="613db-118">Publish the WCF service as described in [Step 1: Publish the SAP Artifacts as a WCF Service](../../adapters-and-accelerators/adapter-sap/step-1-publish-the-sap-artifacts-as-a-wcf-service.md).</span></span>  
  
## <a name="creating-an-application-definition-file"></a><span data-ttu-id="613db-119">Création d’un fichier de définition d’Application</span><span class="sxs-lookup"><span data-stu-id="613db-119">Creating an Application Definition File</span></span>  
 <span data-ttu-id="613db-120">Cette rubrique fournit des instructions pas à pas pour créer un fichier de définition d’application pour le service WCF.</span><span class="sxs-lookup"><span data-stu-id="613db-120">This topic provides step-by-step instructions to create an application definition file for the WCF service.</span></span>  
  
### <a name="connect-to-the-wcf-lob-service-and-create-entities"></a><span data-ttu-id="613db-121">Se connecter au Service WCF LOB et créer des entités</span><span class="sxs-lookup"><span data-stu-id="613db-121">Connect to the WCF LOB Service, and Create Entities</span></span>  
 <span data-ttu-id="613db-122">Vous devez vous connecter au service WCF pour extraire la Description langage WSDL (Web Services) pour le service.</span><span class="sxs-lookup"><span data-stu-id="613db-122">You must connect to the WCF service to extract the Web Services Description Language (WSDL) for the service.</span></span> <span data-ttu-id="613db-123">À partir de WSDL, l’éditeur de définition de catalogue de données métier extrait les méthodes.</span><span class="sxs-lookup"><span data-stu-id="613db-123">From the WSDL, the Business Data Catalog Definition Editor extracts the methods.</span></span> <span data-ttu-id="613db-124">Ces méthodes peuvent être utilisées pour créer des entités.</span><span class="sxs-lookup"><span data-stu-id="613db-124">These methods can be used to create entities.</span></span> <span data-ttu-id="613db-125">Pour cet exemple, deux entités sont créées, chacune pour les client et les commandes client.</span><span class="sxs-lookup"><span data-stu-id="613db-125">For this example, two entities are created, one each for the customer and sales orders.</span></span>  
  
##### <a name="to-connect-to-the-wcf-service-and-create-entities"></a><span data-ttu-id="613db-126">Pour vous connecter au service WCF et de créer des entités</span><span class="sxs-lookup"><span data-stu-id="613db-126">To connect to the WCF service and create entities</span></span>  
  
1.  <span data-ttu-id="613db-127">Démarrez l’éditeur de définition de catalogue de données métier.</span><span class="sxs-lookup"><span data-stu-id="613db-127">Start the Business Data Catalog Definition Editor.</span></span> <span data-ttu-id="613db-128">Sur le **Démarrer** menu, cliquez sur **Microsoft Business Data Catalog Definition Editor**.</span><span class="sxs-lookup"><span data-stu-id="613db-128">On the **Start** menu, click **Microsoft Business Data Catalog Definition Editor**.</span></span>  
  
2.  <span data-ttu-id="613db-129">Dans la barre d’outils, cliquez sur **ajouter un système LOB**.</span><span class="sxs-lookup"><span data-stu-id="613db-129">On the toolbar, click **Add LOB System**.</span></span>  
  
3.  <span data-ttu-id="613db-130">Dans la fenêtre Ajouter un système LOB, cliquez sur **se connecter au service Web**.</span><span class="sxs-lookup"><span data-stu-id="613db-130">In the Add LOB System window, click **Connect to Webservice**.</span></span>  
  
4.  <span data-ttu-id="613db-131">Dans le **URL** zone, tapez l’URL pour le service WCF.</span><span class="sxs-lookup"><span data-stu-id="613db-131">In the **URL** box, type the URL for the WCF service.</span></span> <span data-ttu-id="613db-132">L’URL doit être au format suivant :</span><span class="sxs-lookup"><span data-stu-id="613db-132">The URL must be in the following format:</span></span>  
  
    ```  
    https://<computer_name>/Customer_Order/Rfc.svc?wsdl  
    ```  
  
     <span data-ttu-id="613db-133">où Rfc.svc est le fichier créé pour le contrat de Rfc.</span><span class="sxs-lookup"><span data-stu-id="613db-133">where Rfc.svc is the file created for the Rfc contract.</span></span>  
  
     <span data-ttu-id="613db-134">L’URL est disponible lorsque vous testez si le service WCF est publié avec succès, comme décrit dans la rubrique [étape 1 : publier les artefacts SAP comme un Service WCF](../../adapters-and-accelerators/adapter-sap/step-1-publish-the-sap-artifacts-as-a-wcf-service.md).</span><span class="sxs-lookup"><span data-stu-id="613db-134">The URL is available when you test whether the WCF service is published successfully, as described in the topic [Step 1: Publish the SAP Artifacts as a WCF Service](../../adapters-and-accelerators/adapter-sap/step-1-publish-the-sap-artifacts-as-a-wcf-service.md).</span></span>  
  
5.  <span data-ttu-id="613db-135">Cliquez sur **Se connecter**.</span><span class="sxs-lookup"><span data-stu-id="613db-135">Click **Connect**.</span></span>  
  
6.  <span data-ttu-id="613db-136">Pour afficher les opérations que vous avez sélectionné dans l’Assistant développement d’adaptateurs WCF, cliquez sur le **ajouter une méthode Web** onglet. Vous verrez les méthodes suivantes :</span><span class="sxs-lookup"><span data-stu-id="613db-136">To see the operations you selected in the WCF Adapter Service Development Wizard, click the **Add Web Method** tab. You will see the following methods:</span></span>  
  
    -   <span data-ttu-id="613db-137">SD_RFC_CUSTOMER_GET</span><span class="sxs-lookup"><span data-stu-id="613db-137">SD_RFC_CUSTOMER_GET</span></span>  
  
    -   <span data-ttu-id="613db-138">BAPI_SALESORDER_GETLIST</span><span class="sxs-lookup"><span data-stu-id="613db-138">BAPI_SALESORDER_GETLIST</span></span>  
  
         <span data-ttu-id="613db-139">![Ajouter des méthodes web à l’application BDC](../../adapters-and-accelerators/adapter-sap/media/ea411db2-5cf4-4486-83da-57d3fc332448.gif "ea411db2-5cf4-4486-83da-57d3fc332448")</span><span class="sxs-lookup"><span data-stu-id="613db-139">![Add web methods to the BDC application](../../adapters-and-accelerators/adapter-sap/media/ea411db2-5cf4-4486-83da-57d3fc332448.gif "ea411db2-5cf4-4486-83da-57d3fc332448")</span></span>  
  
     <span data-ttu-id="613db-140">Faites glisser les méthodes à l’aire de conception.</span><span class="sxs-lookup"><span data-stu-id="613db-140">Drag the methods to the Design Surface.</span></span> <span data-ttu-id="613db-141">Assurez-vous que vous faites glisser les deux opérations pour les différentes entités.</span><span class="sxs-lookup"><span data-stu-id="613db-141">Make sure you drag both operations to the different entities.</span></span>  
  
     <span data-ttu-id="613db-142">![Créer des entités pour les méthodes web](../../adapters-and-accelerators/adapter-sap/media/ce4e9bc3-1eae-43ae-8375-e44cf19aaffc.gif "ce4e9bc3-1eae-43ae-8375-e44cf19aaffc")</span><span class="sxs-lookup"><span data-stu-id="613db-142">![Create entities for the web methods](../../adapters-and-accelerators/adapter-sap/media/ce4e9bc3-1eae-43ae-8375-e44cf19aaffc.gif "ce4e9bc3-1eae-43ae-8375-e44cf19aaffc")</span></span>  
  
7.  <span data-ttu-id="613db-143">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="613db-143">Click **OK**.</span></span>  
  
8.  <span data-ttu-id="613db-144">Dans le **Entrez un nom pour le système LOB** boîte de dialogue, tapez un nom dans la **nom du système LOB** boîte.</span><span class="sxs-lookup"><span data-stu-id="613db-144">In the **Enter the name for the LOB System** dialog box, type a name in the **LOB System Name** box.</span></span> <span data-ttu-id="613db-145">Pour cet exemple, appeler **Customer_Order**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="613db-145">For this example, call it **Customer_Order**, and then click **OK**.</span></span>  
  
9. <span data-ttu-id="613db-146">Dans l’entreprise Data Catalog Definition Editor, les deux entités sont répertoriées comme **Entity0** et **Entity1**.</span><span class="sxs-lookup"><span data-stu-id="613db-146">In the Business Data Catalog Definition Editor, the two entities are listed as **Entity0** and **Entity1**.</span></span> <span data-ttu-id="613db-147">Donnez des noms conviviaux ces entités.</span><span class="sxs-lookup"><span data-stu-id="613db-147">Give these entities friendly names.</span></span> <span data-ttu-id="613db-148">Renommer l’entité pour SD_RFC_CUSTOMER_GET à **client**et renommer l’entité pour BAPI_SALESORDER_GETLIST à **SalesOrder**.</span><span class="sxs-lookup"><span data-stu-id="613db-148">Rename the entity for SD_RFC_CUSTOMER_GET to **Customer**, and rename the entity for BAPI_SALESORDER_GETLIST to **SalesOrder**.</span></span> <span data-ttu-id="613db-149">Procédez comme suit pour renommer les entités :</span><span class="sxs-lookup"><span data-stu-id="613db-149">Perform the following steps to rename the entities:</span></span>  
  
    1.  <span data-ttu-id="613db-150">Développez le **Customer_Order** nœud, puis développez le **entités** nœud.</span><span class="sxs-lookup"><span data-stu-id="613db-150">Expand the **Customer_Order** node, and then expand the **Entities** node.</span></span>  
  
    2.  <span data-ttu-id="613db-151">Sélectionnez le **Entity0** nœud.</span><span class="sxs-lookup"><span data-stu-id="613db-151">Select the **Entity0** node.</span></span>  
  
    3.  <span data-ttu-id="613db-152">Dans le volet Propriétés, tapez **client** dans les **nom** boîte.</span><span class="sxs-lookup"><span data-stu-id="613db-152">In the Properties pane, type **Customer** in the **Name** box.</span></span>  
  
         <span data-ttu-id="613db-153">![Renommer l’entité](../../adapters-and-accelerators/adapter-sap/media/4e83a036-3ab7-4f74-9f67-420574219d3d.gif "4e83a036-3ab7-4f74-9f67-420574219d3d")</span><span class="sxs-lookup"><span data-stu-id="613db-153">![Rename the entity](../../adapters-and-accelerators/adapter-sap/media/4e83a036-3ab7-4f74-9f67-420574219d3d.gif "4e83a036-3ab7-4f74-9f67-420574219d3d")</span></span>  
  
    4.  <span data-ttu-id="613db-154">Sélectionnez le **Entity1** nœud.</span><span class="sxs-lookup"><span data-stu-id="613db-154">Select the **Entity1** node.</span></span>  
  
    5.  <span data-ttu-id="613db-155">Dans le volet Propriétés, tapez **SalesOrder** dans les **nom** boîte.</span><span class="sxs-lookup"><span data-stu-id="613db-155">In the Properties pane, type **SalesOrder** in the **Name** box.</span></span>  
  
### <a name="specify-user-name-and-password-headers-for-the-methods"></a><span data-ttu-id="613db-156">Spécifiez le nom d’utilisateur et les en-têtes de mot de passe pour les méthodes</span><span class="sxs-lookup"><span data-stu-id="613db-156">Specify User Name and Password Headers for the Methods</span></span>  
 <span data-ttu-id="613db-157">Lorsque vous créez un service WCF pour les documents RFC sélectionnés dans le système SAP, vous avez spécifié les en-têtes nom et mot de passe utilisateur en tant que partie de la configuration de comportement de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="613db-157">When creating a WCF service for the selected RFCs in the SAP system, you specified user name and password headers as part of the endpoint behavior configuration.</span></span> <span data-ttu-id="613db-158">Consultez [étape 1 : publier les artefacts SAP sous la forme d’un Service WCF](../../adapters-and-accelerators/adapter-sap/step-1-publish-the-sap-artifacts-as-a-wcf-service.md).</span><span class="sxs-lookup"><span data-stu-id="613db-158">See [Step 1: Publish the SAP Artifacts as a WCF Service](../../adapters-and-accelerators/adapter-sap/step-1-publish-the-sap-artifacts-as-a-wcf-service.md).</span></span> <span data-ttu-id="613db-159">Vous devez spécifier les mêmes valeurs pour les propriétés de la méthode.</span><span class="sxs-lookup"><span data-stu-id="613db-159">You must specify the same values for the method properties.</span></span>  
  
##### <a name="to-specify-user-name-and-password-headers"></a><span data-ttu-id="613db-160">Pour spécifier les en-têtes de nom et mot de passe utilisateur</span><span class="sxs-lookup"><span data-stu-id="613db-160">To specify user name and password headers</span></span>  
  
1.  <span data-ttu-id="613db-161">Ajoutez les en-têtes de nom et mot de passe utilisateur pour la méthode SD_RFC_CUSTOMER_GET.</span><span class="sxs-lookup"><span data-stu-id="613db-161">Add the user name and password headers for the SD_RFC_CUSTOMER_GET method.</span></span>  
  
    1.  <span data-ttu-id="613db-162">Dans le volet objets de métadonnées, développez le **client** nœud, puis développez le **méthodes** nœud.</span><span class="sxs-lookup"><span data-stu-id="613db-162">In the Metadata Objects pane, expand the **Customer** node, and then expand the **Methods** node.</span></span>  
  
    2.  <span data-ttu-id="613db-163">Cliquez sur le nœud SD_RFC_CUSTOMER_GET et dans le volet Propriétés, cliquez sur le bouton de sélection (...) contre le **propriétés** boîte.</span><span class="sxs-lookup"><span data-stu-id="613db-163">Click the SD_RFC_CUSTOMER_GET node, and in the Properties pane click the ellipsis (…) button against the **Properties** box.</span></span>  
  
    3.  <span data-ttu-id="613db-164">Dans la fenêtre Éditeur de collections PropertyView, cliquez sur **ajouter**et dans le volet Propriétés, tapez **HttpHeaderUserName** pour le **nom** boîte.</span><span class="sxs-lookup"><span data-stu-id="613db-164">In the PropertyView Collection Editor window, click **Add**, and in the Property pane, type **HttpHeaderUserName** for the **Name** box.</span></span> <span data-ttu-id="613db-165">De même, tapez **MyUserHeader** pour le **PropertyValue** boîte.</span><span class="sxs-lookup"><span data-stu-id="613db-165">Similarly, type **MyUserHeader** for the **PropertyValue** box.</span></span> <span data-ttu-id="613db-166">Sélectionnez **System.String** pour le **Type** boîte.</span><span class="sxs-lookup"><span data-stu-id="613db-166">Select **System.String** for the **Type** box.</span></span>  
  
         <span data-ttu-id="613db-167">![Ajouter une propriété](../../adapters-and-accelerators/adapter-sap/media/9eef32ac-8a93-45dc-8d07-12b7dbf961ba.gif "9eef32ac-8a93-45dc-8d07-12b7dbf961ba")</span><span class="sxs-lookup"><span data-stu-id="613db-167">![Add a property](../../adapters-and-accelerators/adapter-sap/media/9eef32ac-8a93-45dc-8d07-12b7dbf961ba.gif "9eef32ac-8a93-45dc-8d07-12b7dbf961ba")</span></span>  
  
    4.  <span data-ttu-id="613db-168">Dans la fenêtre Éditeur de collections PropertyView, cliquez sur **ajouter**et dans le volet Propriétés, tapez **HttpHeaderPassword** pour le **nom** boîte.</span><span class="sxs-lookup"><span data-stu-id="613db-168">In the PropertyView Collection Editor window, click **Add**, and in the Property pane, type **HttpHeaderPassword** for the **Name** box.</span></span> <span data-ttu-id="613db-169">De même, tapez **MyPassHeader** pour le **PropertyValue** boîte.</span><span class="sxs-lookup"><span data-stu-id="613db-169">Similarly, type **MyPassHeader** for the **PropertyValue** box.</span></span> <span data-ttu-id="613db-170">Sélectionnez **System.String** pour le **Type** boîte.</span><span class="sxs-lookup"><span data-stu-id="613db-170">Select **System.String** for the **Type** box.</span></span>  
  
    5.  <span data-ttu-id="613db-171">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="613db-171">Click **OK**.</span></span>  
  
2.  <span data-ttu-id="613db-172">Ajoutez les en-têtes de nom et mot de passe utilisateur pour la méthode BAPI_SALESORDER_GETLIST.</span><span class="sxs-lookup"><span data-stu-id="613db-172">Add the user name and password headers for the BAPI_SALESORDER_GETLIST method.</span></span>  
  
    1.  <span data-ttu-id="613db-173">Dans le volet objets de métadonnées, développez le **SalesOrder** nœud, puis développez le **méthodes** nœud.</span><span class="sxs-lookup"><span data-stu-id="613db-173">In the Metadata Objects pane, expand the **SalesOrder** node, and then expand the **Methods** node.</span></span>  
  
    2.  <span data-ttu-id="613db-174">Cliquez sur le nœud BAPI_SALESORDER_GETLIST et dans le volet Propriétés, cliquez sur le bouton de sélection (...) contre le **propriétés** boîte.</span><span class="sxs-lookup"><span data-stu-id="613db-174">Click the BAPI_SALESORDER_GETLIST node, and in the Properties pane click the ellipsis (…) button against the **Properties** box.</span></span>  
  
    3.  <span data-ttu-id="613db-175">Dans la fenêtre Éditeur de collections PropertyView, cliquez sur **ajouter**et dans le volet Propriétés, tapez **HttpHeaderUserName** pour le **nom** boîte.</span><span class="sxs-lookup"><span data-stu-id="613db-175">In the PropertyView Collection Editor window, click **Add**, and in the Property pane, type **HttpHeaderUserName** for the **Name** box.</span></span> <span data-ttu-id="613db-176">De même, tapez **MyUserHeader** pour le **PropertyValue** boîte.</span><span class="sxs-lookup"><span data-stu-id="613db-176">Similarly, type **MyUserHeader** for the **PropertyValue** box.</span></span> <span data-ttu-id="613db-177">Sélectionnez **System.String** pour le **Type** boîte.</span><span class="sxs-lookup"><span data-stu-id="613db-177">Select **System.String** for the **Type** box.</span></span>  
  
    4.  <span data-ttu-id="613db-178">Dans la fenêtre Éditeur de collections PropertyView, cliquez sur **ajouter**et dans le volet Propriétés, tapez **HttpHeaderPassword** pour le **nom** boîte.</span><span class="sxs-lookup"><span data-stu-id="613db-178">In the PropertyView Collection Editor window, click **Add**, and in the Property pane, type **HttpHeaderPassword** for the **Name** box.</span></span> <span data-ttu-id="613db-179">De même, tapez **MyPassHeader** pour le **PropertyValue** boîte.</span><span class="sxs-lookup"><span data-stu-id="613db-179">Similarly, type **MyPassHeader** for the **PropertyValue** box.</span></span> <span data-ttu-id="613db-180">Sélectionnez **System.String** pour le **Type** boîte.</span><span class="sxs-lookup"><span data-stu-id="613db-180">Select **System.String** for the **Type** box.</span></span>  
  
    5.  <span data-ttu-id="613db-181">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="613db-181">Click **OK**.</span></span>  
  
### <a name="set-up-single-sign-on-for-connecting-to-the-sap-system"></a><span data-ttu-id="613db-182">Valeur de l’authentification unique pour la connexion au système SAP</span><span class="sxs-lookup"><span data-stu-id="613db-182">Set up Single Sign-On for Connecting to the SAP System</span></span>  
 <span data-ttu-id="613db-183">Une fois que vous avez terminé d’exécuter toutes les procédures dans cette rubrique, vous avez créé un fichier de définition d’application qui peut être importé dans une application SharePoint.</span><span class="sxs-lookup"><span data-stu-id="613db-183">After you have finished performing all the procedures in this topic, you will have created an application definition file that can be imported into a SharePoint application.</span></span> <span data-ttu-id="613db-184">À partir de l’application, vous appelez les méthodes SAP pour récupérer les données pertinentes à partir du système SAP.</span><span class="sxs-lookup"><span data-stu-id="613db-184">From the application, you invoke the SAP methods to retrieve relevant data from the SAP system.</span></span> <span data-ttu-id="613db-185">Pour ce faire, vous devez créer un mappage entre un utilisateur dans le système SAP et de l’utilisateur dans l’application SharePoint.</span><span class="sxs-lookup"><span data-stu-id="613db-185">To enable this, you must create a mapping between a user in the SAP system and the user in the SharePoint application.</span></span> <span data-ttu-id="613db-186">Vous créez ce mappage dans la console d’Administration centrale de SharePoint après avoir importé le fichier de définition d’application.</span><span class="sxs-lookup"><span data-stu-id="613db-186">You create this mapping in SharePoint Central Administration console after you have imported the application definition file.</span></span>  
  
 <span data-ttu-id="613db-187">Toutefois, pour créer le mappage, vous devez définir une propriété **SecondarySsoApplicationId** dans Business Data Catalog Definition Editor.</span><span class="sxs-lookup"><span data-stu-id="613db-187">However, to create the mapping you must set a property **SecondarySsoApplicationId** in the Business Data Catalog Definition Editor.</span></span>  
  
##### <a name="to-set-the-secondaryssoapplicationid-property"></a><span data-ttu-id="613db-188">Pour définir la propriété SecondarySsoApplicationId</span><span class="sxs-lookup"><span data-stu-id="613db-188">To set the SecondarySsoApplicationId property</span></span>  
  
1.  <span data-ttu-id="613db-189">Dans le volet objets de métadonnées, développez le **Customer_Order** nœud, puis développez le **Instances** nœud.</span><span class="sxs-lookup"><span data-stu-id="613db-189">In the Metadata Objects pane, expand the **Customer_Order** node, and then expand the **Instances** node.</span></span>  
  
2.  <span data-ttu-id="613db-190">Cliquez sur **Customer_Order_Instance**, dans le volet Propriétés, cliquez sur le bouton de sélection (...) par rapport à la **propriétés** boîte.</span><span class="sxs-lookup"><span data-stu-id="613db-190">Click **Customer_Order_Instance**, and in the Properties pane, click the ellipsis (…) button against the **Properties** box.</span></span>  
  
3.  <span data-ttu-id="613db-191">Dans la fenêtre Éditeur de collections PropertyView, cliquez sur **ajouter**et dans le volet Propriétés, tapez **SecondarySsoApplicationId** pour le **nom** boîte.</span><span class="sxs-lookup"><span data-stu-id="613db-191">In the PropertyView Collection Editor window, click **Add**, and in the Property pane, type **SecondarySsoApplicationId** for the **Name** box.</span></span> <span data-ttu-id="613db-192">De même, tapez **SAPSSO** pour le **PropertyValue** boîte.</span><span class="sxs-lookup"><span data-stu-id="613db-192">Similarly, type **SAPSSO** for the **PropertyValue** box.</span></span> <span data-ttu-id="613db-193">Sélectionnez **System.String** pour le **Type** boîte.</span><span class="sxs-lookup"><span data-stu-id="613db-193">Select **System.String** for the **Type** box.</span></span>  
  
     <span data-ttu-id="613db-194">![Ajouter la propriété SSO](../../adapters-and-accelerators/adapter-sap/media/1eb813e4-fed2-45c2-8902-9af5dd3369bf.gif "1eb813e4-fed2-45c2-8902-9af5dd3369bf")</span><span class="sxs-lookup"><span data-stu-id="613db-194">![Add the SSO property](../../adapters-and-accelerators/adapter-sap/media/1eb813e4-fed2-45c2-8902-9af5dd3369bf.gif "1eb813e4-fed2-45c2-8902-9af5dd3369bf")</span></span>  
  
4.  <span data-ttu-id="613db-195">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="613db-195">Click **OK**.</span></span>  
  
### <a name="requirement-1-search-for-customers-based-on-customer-name"></a><span data-ttu-id="613db-196">Condition 1 : Recherche pour les clients basés sur le nom du client</span><span class="sxs-lookup"><span data-stu-id="613db-196">Requirement 1: Search for Customers Based on Customer Name</span></span>  
 <span data-ttu-id="613db-197">Pour créer un fichier de définition d’application qui peut être utilisé pour rechercher des clients basés sur le nom du client, vous devez effectuer l’ensemble suivant de tâches.</span><span class="sxs-lookup"><span data-stu-id="613db-197">To create an application definition file that can be used to search for customers based on customer name, you must perform the following set of tasks.</span></span>  
  
-   <span data-ttu-id="613db-198">Dans la méthode SD_RFC_CUSTOMER_GET, créer un filtre et le mapper au paramètre qui stocke le nom du client.</span><span class="sxs-lookup"><span data-stu-id="613db-198">In the SD_RFC_CUSTOMER_GET method, create a filter and map it to the parameter that stores the customer name.</span></span>  
  
-   <span data-ttu-id="613db-199">Créer un **recherche** instance de méthode pour la méthode SD_RFC_CUSTOMER_GET.</span><span class="sxs-lookup"><span data-stu-id="613db-199">Create a **Finder** method instance for the SD_RFC_CUSTOMER_GET method.</span></span> <span data-ttu-id="613db-200">A **recherche** méthode récupère une liste d’enregistrements en fonction d’un filtre.</span><span class="sxs-lookup"><span data-stu-id="613db-200">A **Finder** method retrieves a list of records based on a filter.</span></span>  
  
##### <a name="to-create-a-filter-and-map-it-to-the-customer-name-parameter"></a><span data-ttu-id="613db-201">Pour créer un filtre et la mapper au paramètre de nom de client</span><span class="sxs-lookup"><span data-stu-id="613db-201">To create a filter, and map it to the customer name parameter</span></span>  
  
1.  <span data-ttu-id="613db-202">Créer un filtre.</span><span class="sxs-lookup"><span data-stu-id="613db-202">Create a filter.</span></span>  
  
    1.  <span data-ttu-id="613db-203">Dans le volet objets de métadonnées, développez le **client** nœud, puis développez le **méthodes** nœud.</span><span class="sxs-lookup"><span data-stu-id="613db-203">In the Metadata Objects pane, expand the **Customer** node, and then expand the **Methods** node.</span></span>  
  
    2.  <span data-ttu-id="613db-204">Développez la méthode SD_RFC_CUSTOMER_GET, avec le bouton droit **filtres**, puis cliquez sur **ajouter un filtre**.</span><span class="sxs-lookup"><span data-stu-id="613db-204">Expand the SD_RFC_CUSTOMER_GET method, right-click **Filters**, and then click **Add Filter**.</span></span>  
  
         <span data-ttu-id="613db-205">![Ajouter un filtre à une méthode](../../adapters-and-accelerators/adapter-sap/media/23eaab24-66e4-486f-8f99-02a5e0fef984.gif "23eaab24-66e4-486f-8f99-02a5e0fef984")</span><span class="sxs-lookup"><span data-stu-id="613db-205">![Add filter to a method](../../adapters-and-accelerators/adapter-sap/media/23eaab24-66e4-486f-8f99-02a5e0fef984.gif "23eaab24-66e4-486f-8f99-02a5e0fef984")</span></span>  
  
    3.  <span data-ttu-id="613db-206">Dans le volet Propriétés, tapez **CustomerName** dans les **nom** boîte.</span><span class="sxs-lookup"><span data-stu-id="613db-206">In the Properties pane, type **CustomerName** in the **Name** box.</span></span>  
  
         <span data-ttu-id="613db-207">![Spécifiez un nom pour le filtre](../../adapters-and-accelerators/adapter-sap/media/0a0d0f85-a16a-4969-a122-097355141c27.gif "0a0d0f85-a16a-4969-a122-097355141c27")</span><span class="sxs-lookup"><span data-stu-id="613db-207">![Specify a name for the filter](../../adapters-and-accelerators/adapter-sap/media/0a0d0f85-a16a-4969-a122-097355141c27.gif "0a0d0f85-a16a-4969-a122-097355141c27")</span></span>  
  
    4.  <span data-ttu-id="613db-208">Pour le **FilterType** propriété, sélectionnez **WildcardFilter**.</span><span class="sxs-lookup"><span data-stu-id="613db-208">For the **FilterType** property, select **WildcardFilter**.</span></span>  
  
2.  <span data-ttu-id="613db-209">Mapper le filtre à la **nom1** paramètre dans la méthode SD_RFC_CUSTOMER_GET.</span><span class="sxs-lookup"><span data-stu-id="613db-209">Map the filter to the **NAME1** parameter in the SD_RFC_CUSTOMER_GET method.</span></span>  
  
    1.  <span data-ttu-id="613db-210">Dans le volet objets de métadonnées, développez le **client** nœud, puis développez le **méthodes** nœud.</span><span class="sxs-lookup"><span data-stu-id="613db-210">In the Metadata Objects pane, expand the **Customer** node, and then expand the **Methods** node.</span></span>  
  
    2.  <span data-ttu-id="613db-211">La méthode SD_RFC_CUSTOMER_GET, puis le **paramètres** nœud.</span><span class="sxs-lookup"><span data-stu-id="613db-211">Expand the SD_RFC_CUSTOMER_GET method, and then expand the **Parameters** node.</span></span>  
  
    3.  <span data-ttu-id="613db-212">Développez le **nom1** nœud, puis cliquez sur le deuxième **nom1** nœud.</span><span class="sxs-lookup"><span data-stu-id="613db-212">Expand the **NAME1** node, and click the second **NAME1** node.</span></span> <span data-ttu-id="613db-213">Le **nom1** paramètre contient le nom du client.</span><span class="sxs-lookup"><span data-stu-id="613db-213">The **NAME1** parameter contains the name of the customer.</span></span>  
  
    4.  <span data-ttu-id="613db-214">Dans le volet Propriétés, sélectionnez **CustomerName** à partir de la **FilterDescriptor** liste.</span><span class="sxs-lookup"><span data-stu-id="613db-214">In the Properties pane, select **CustomerName** from the **FilterDescriptor** list.</span></span>  
  
         <span data-ttu-id="613db-215">![Mapper le filtre à un paramètre de méthode](../../adapters-and-accelerators/adapter-sap/media/6cc4ef85-503c-4847-95cb-633b902a715d.gif "6cc4ef85-503c-4847-95cb-633b902a715d")</span><span class="sxs-lookup"><span data-stu-id="613db-215">![Map the filter to a method parameter](../../adapters-and-accelerators/adapter-sap/media/6cc4ef85-503c-4847-95cb-633b902a715d.gif "6cc4ef85-503c-4847-95cb-633b902a715d")</span></span>  
  
##### <a name="to-create-a-finder-method-instance-for-the-sdrfccustomerget-method"></a><span data-ttu-id="613db-216">Pour créer une instance de méthode Finder pour la méthode SD_RFC_CUSTOMER_GET</span><span class="sxs-lookup"><span data-stu-id="613db-216">To create a Finder method instance for the SD_RFC_CUSTOMER_GET method</span></span>  
  
1.  <span data-ttu-id="613db-217">Dans le volet objets de métadonnées, développez le **client** nœud, puis développez le **méthodes** nœud.</span><span class="sxs-lookup"><span data-stu-id="613db-217">In the Metadata Objects pane, expand the **Customer** node, and then expand the **Methods** node.</span></span>  
  
2.  <span data-ttu-id="613db-218">Développez le **SD_RFC_CUSTOMER_GET** nœud, avec le bouton droit **Instances**, puis cliquez sur **ajouter une Instance de méthode** pour ouvrir la fenêtre Créer une Instance de méthode.</span><span class="sxs-lookup"><span data-stu-id="613db-218">Expand the **SD_RFC_CUSTOMER_GET** node, right-click **Instances**, and then click **Add Method Instance** to open the Create Method Instance window.</span></span>  
  
     <span data-ttu-id="613db-219">![Ajouter une instance de méthode](../../adapters-and-accelerators/adapter-sap/media/f583f8ef-e364-4665-8514-db033219ba0b.gif "f583f8ef-e364-4665-8514-db033219ba0b")</span><span class="sxs-lookup"><span data-stu-id="613db-219">![Add a method instance](../../adapters-and-accelerators/adapter-sap/media/f583f8ef-e364-4665-8514-db033219ba0b.gif "f583f8ef-e364-4665-8514-db033219ba0b")</span></span>  
  
3.  <span data-ttu-id="613db-220">Dans la fenêtre Créer une Instance de méthode, cliquez sur **recherche** pour **Type d’Instance de méthode**.</span><span class="sxs-lookup"><span data-stu-id="613db-220">In the Create Method Instance window, click **Finder** for **Method Instance Type**.</span></span> <span data-ttu-id="613db-221">Sélectionnez **CUSTOMER_T** pour **TypeDescriptor de retour**.</span><span class="sxs-lookup"><span data-stu-id="613db-221">Select **CUSTOMER_T** for **Return TypeDescriptor**.</span></span>  
  
     <span data-ttu-id="613db-222">![Ajouter une instance de méthode Finder](../../adapters-and-accelerators/adapter-sap/media/e9ae47f2-32f5-4586-8467-94e3713d2a06.gif "e9ae47f2-32f5-4586-8467-94e3713d2a06")</span><span class="sxs-lookup"><span data-stu-id="613db-222">![Add a Finder method instance](../../adapters-and-accelerators/adapter-sap/media/e9ae47f2-32f5-4586-8467-94e3713d2a06.gif "e9ae47f2-32f5-4586-8467-94e3713d2a06")</span></span>  
  
4.  <span data-ttu-id="613db-223">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="613db-223">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="613db-224">Dans le volet Propriétés, tapez **GetCustomerByName_Instance** dans les **nom** boîte.</span><span class="sxs-lookup"><span data-stu-id="613db-224">In the Properties pane, type **GetCustomerByName_Instance** in the **Name** box.</span></span>  
  
     <span data-ttu-id="613db-225">![Spécifiez un nom pour l’instance de méthode](../../adapters-and-accelerators/adapter-sap/media/e44e02e8-b9fb-40ca-a55d-8bdc7ace02b5.gif "e44e02e8-b9fb-40ca-a55d-8bdc7ace02b5")</span><span class="sxs-lookup"><span data-stu-id="613db-225">![Specify a name for the method instance](../../adapters-and-accelerators/adapter-sap/media/e44e02e8-b9fb-40ca-a55d-8bdc7ace02b5.gif "e44e02e8-b9fb-40ca-a55d-8bdc7ace02b5")</span></span>  
  
### <a name="requirement-2-retrieve-details-for-a-specific-customer-from-the-list-of-customers"></a><span data-ttu-id="613db-226">Condition 2 : Récupération des détails pour un client spécifique à partir de la liste des clients</span><span class="sxs-lookup"><span data-stu-id="613db-226">Requirement 2: Retrieve Details for a Specific Customer from the List of Customers</span></span>  
 <span data-ttu-id="613db-227">Pour créer un fichier de définition d’application qui peut être utilisé pour rechercher des clients basés sur le nom du client, vous devez effectuer l’ensemble suivant de tâches.</span><span class="sxs-lookup"><span data-stu-id="613db-227">To create an application definition file that can be used to search for customers based on customer name, you must perform the following set of tasks.</span></span>  
  
-   <span data-ttu-id="613db-228">Dans la méthode SD_RFC_CUSTOMER_GET, créer un identificateur et le mapper au paramètre qui stocke le numéro de client.</span><span class="sxs-lookup"><span data-stu-id="613db-228">In the SD_RFC_CUSTOMER_GET method, create an identifier, and map it to the parameter that stores the customer number.</span></span>  
  
-   <span data-ttu-id="613db-229">Créer un **recherche spécifique** instance de méthode pour la méthode SD_RFC_CUSTOMER_GET.</span><span class="sxs-lookup"><span data-stu-id="613db-229">Create a **Specific Finder** method instance for the SD_RFC_CUSTOMER_GET method.</span></span> <span data-ttu-id="613db-230">A **recherche spécifique** méthode trouve un enregistrement spécifique en fonction d’un identificateur.</span><span class="sxs-lookup"><span data-stu-id="613db-230">A **Specific Finder** method finds a specific record based on an identifier.</span></span>  
  
##### <a name="to-create-an-identifier-and-map-it-to-the-customer-number-parameter"></a><span data-ttu-id="613db-231">Pour créer un identificateur et la mapper vers le paramètre numéro de client</span><span class="sxs-lookup"><span data-stu-id="613db-231">To create an identifier, and map it to the customer number parameter</span></span>  
  
1.  <span data-ttu-id="613db-232">Créer un identificateur pour le **client** entité.</span><span class="sxs-lookup"><span data-stu-id="613db-232">Create an identifier for the **Customer** entity.</span></span>  
  
    1.  <span data-ttu-id="613db-233">Dans le volet objets de métadonnées, développez le **client** nœud.</span><span class="sxs-lookup"><span data-stu-id="613db-233">In the Metadata Objects pane, expand the **Customer** node.</span></span>  
  
    2.  <span data-ttu-id="613db-234">Cliquez sur le **identificateurs** nœud et sélectionnez **ajouter un identificateur**.</span><span class="sxs-lookup"><span data-stu-id="613db-234">Right-click the **Identifiers** node, and then select **Add Identifier**.</span></span>  
  
         <span data-ttu-id="613db-235">![Ajouter un identificateur à une méthode](../../adapters-and-accelerators/adapter-sap/media/3adeeda3-426c-41fe-8d5c-5ca5863fb430.gif "3adeeda3-426c-41fe-8d5c-5ca5863fb430")</span><span class="sxs-lookup"><span data-stu-id="613db-235">![Add an identifier to a method](../../adapters-and-accelerators/adapter-sap/media/3adeeda3-426c-41fe-8d5c-5ca5863fb430.gif "3adeeda3-426c-41fe-8d5c-5ca5863fb430")</span></span>  
  
    3.  <span data-ttu-id="613db-236">Dans le volet Propriétés, tapez **CustomerID** dans les **nom** boîte.</span><span class="sxs-lookup"><span data-stu-id="613db-236">In the Properties pane, type **CustomerID** in the **Name** box.</span></span>  
  
    4.  <span data-ttu-id="613db-237">Sélectionnez **System.String** pour le **Type** boîte.</span><span class="sxs-lookup"><span data-stu-id="613db-237">Select **System.String** for the **Type** box.</span></span>  
  
         <span data-ttu-id="613db-238">![Spécifiez un nom pour l’identificateur](../../adapters-and-accelerators/adapter-sap/media/a2304bca-9a54-4d2b-ba9f-461cfaafccb0.gif "a2304bca-9a54-4d2b-ba9f-461cfaafccb0")</span><span class="sxs-lookup"><span data-stu-id="613db-238">![Specify a name for the identifier](../../adapters-and-accelerators/adapter-sap/media/a2304bca-9a54-4d2b-ba9f-461cfaafccb0.gif "a2304bca-9a54-4d2b-ba9f-461cfaafccb0")</span></span>  
  
2.  <span data-ttu-id="613db-239">Mapper l’identificateur pour le paramètre de clé pour la méthode SD_RFC_CUSTOMER_GET.</span><span class="sxs-lookup"><span data-stu-id="613db-239">Map the identifier to the key parameter for the SD_RFC_CUSTOMER_GET method.</span></span>  
  
    1.  <span data-ttu-id="613db-240">Dans le volet objets de métadonnées, développez le **client** nœud, puis développez le **méthodes** nœud.</span><span class="sxs-lookup"><span data-stu-id="613db-240">In the Metadata Objects pane, expand the **Customer** node, and then expand the **Methods** node.</span></span>  
  
    2.  <span data-ttu-id="613db-241">La méthode SD_RFC_CUSTOMER_GET, puis le **paramètres** nœud.</span><span class="sxs-lookup"><span data-stu-id="613db-241">Expand the SD_RFC_CUSTOMER_GET method, and then expand the **Parameters** node.</span></span>  
  
    3.  <span data-ttu-id="613db-242">Développez le **KUNNR** paramètre, puis cliquez sur le deuxième **KUNNR** nœud.</span><span class="sxs-lookup"><span data-stu-id="613db-242">Expand the **KUNNR** parameter, and then click the second **KUNNR** node.</span></span>  
  
    4.  <span data-ttu-id="613db-243">Dans le volet Propriétés, sélectionnez **CustomerID [Customer]** à partir de la **identificateur** liste.</span><span class="sxs-lookup"><span data-stu-id="613db-243">In the Properties pane, select **CustomerID[Customer]** from the **Identifier** list.</span></span>  
  
         <span data-ttu-id="613db-244">![Mapper l’identificateur à un paramètre](../../adapters-and-accelerators/adapter-sap/media/04ff6496-34a7-421b-ae9e-f9263895c153.gif "04ff6496-34a7-421b-ae9e-f9263895c153")</span><span class="sxs-lookup"><span data-stu-id="613db-244">![Map the identifier to a parameter](../../adapters-and-accelerators/adapter-sap/media/04ff6496-34a7-421b-ae9e-f9263895c153.gif "04ff6496-34a7-421b-ae9e-f9263895c153")</span></span>  
  
3.  <span data-ttu-id="613db-245">Définir une association entre les paramètres d’entrée et de retournés.</span><span class="sxs-lookup"><span data-stu-id="613db-245">Set up an association between input and return parameters.</span></span>  
  
    1.  <span data-ttu-id="613db-246">Dans le volet objets de métadonnées, développez le **client** nœud, puis développez le **méthodes** nœud.</span><span class="sxs-lookup"><span data-stu-id="613db-246">In the Metadata Objects pane, expand the **Customer** node, and then expand the **Methods** node.</span></span>  
  
    2.  <span data-ttu-id="613db-247">La méthode SD_RFC_CUSTOMER_GET, puis le **paramètres** nœud.</span><span class="sxs-lookup"><span data-stu-id="613db-247">Expand the SD_RFC_CUSTOMER_GET method, and then expand the **Parameters** node.</span></span>  
  
    3.  <span data-ttu-id="613db-248">Développez le **CUSTOMER_T** nœud, puis le deuxième **CUSTOMER_T** nœud, puis le **élément** nœud, puis cliquez sur le **KUNNR** nœud.</span><span class="sxs-lookup"><span data-stu-id="613db-248">Expand the **CUSTOMER_T** node, then the second **CUSTOMER_T** node, then the **Item** node, and then click the **KUNNR** node.</span></span>  
  
    4.  <span data-ttu-id="613db-249">Dans le volet Propriétés, sélectionnez **CustomerID [Customer]** à partir de la **identificateur** liste.</span><span class="sxs-lookup"><span data-stu-id="613db-249">In the Properties pane, select **CustomerID[Customer]** from the **Identifier** list.</span></span>  
  
##### <a name="to-create-a-specific-finder-method-instance-for-the-sdrfccustomerget-method"></a><span data-ttu-id="613db-250">Pour créer une instance de méthode Finder spécifique pour la méthode SD_RFC_CUSTOMER_GET</span><span class="sxs-lookup"><span data-stu-id="613db-250">To create a Specific Finder method instance for the SD_RFC_CUSTOMER_GET method</span></span>  
  
1.  <span data-ttu-id="613db-251">Dans le volet objets de métadonnées, développez le **client** nœud, puis le **méthodes** nœud.</span><span class="sxs-lookup"><span data-stu-id="613db-251">In the Metadata Objects pane, expand the **Customer** node, and then the **Methods** node.</span></span>  
  
2.  <span data-ttu-id="613db-252">Développez le **SD_RFC_CUSTOMER_GET** nœud, avec le bouton droit **Instances**, puis sélectionnez **ajouter une Instance de méthode** pour ouvrir la fenêtre Créer une Instance de méthode.</span><span class="sxs-lookup"><span data-stu-id="613db-252">Expand the **SD_RFC_CUSTOMER_GET** node, right-click **Instances**, and then select **Add Method Instance** to open the Create Method Instance window.</span></span>  
  
     <span data-ttu-id="613db-253">![Ajouter une instance de méthode](../../adapters-and-accelerators/adapter-sap/media/f583f8ef-e364-4665-8514-db033219ba0b.gif "f583f8ef-e364-4665-8514-db033219ba0b")</span><span class="sxs-lookup"><span data-stu-id="613db-253">![Add a method instance](../../adapters-and-accelerators/adapter-sap/media/f583f8ef-e364-4665-8514-db033219ba0b.gif "f583f8ef-e364-4665-8514-db033219ba0b")</span></span>  
  
3.  <span data-ttu-id="613db-254">Dans la fenêtre Créer une Instance de méthode, sélectionnez **recherche spécifique** pour **Type d’Instance de méthode**.</span><span class="sxs-lookup"><span data-stu-id="613db-254">In the Create Method Instance window, select **Specific Finder** for **Method Instance Type**.</span></span> <span data-ttu-id="613db-255">De même, sélectionnez **CUSTOMER_T** pour **TypeDescriptor de retour**.</span><span class="sxs-lookup"><span data-stu-id="613db-255">Similarly, select **CUSTOMER_T** for **Return TypeDescriptor**.</span></span>  
  
     <span data-ttu-id="613db-256">![Ajouter une Instance de méthode Finder spécifique](../../adapters-and-accelerators/adapter-sap/media/838eb512-b967-46e7-a865-0bf3651b02a1.gif "838eb512-b967-46e7-a865-0bf3651b02a1")</span><span class="sxs-lookup"><span data-stu-id="613db-256">![Add a Specific Finder Method Instance](../../adapters-and-accelerators/adapter-sap/media/838eb512-b967-46e7-a865-0bf3651b02a1.gif "838eb512-b967-46e7-a865-0bf3651b02a1")</span></span>  
  
4.  <span data-ttu-id="613db-257">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="613db-257">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="613db-258">Dans le volet Propriétés, tapez **GetCustomerByNumber_Instance** pour le **nom** boîte.</span><span class="sxs-lookup"><span data-stu-id="613db-258">In the Properties pane, type **GetCustomerByNumber_Instance** for the **Name** box.</span></span>  
  
     <span data-ttu-id="613db-259">![Spécifiez un nom pour l’instance de méthode](../../adapters-and-accelerators/adapter-sap/media/970f543c-cd06-4921-86c9-c110abdc7994.gif "970f543c-cd06-4921-86c9-c110abdc7994")</span><span class="sxs-lookup"><span data-stu-id="613db-259">![Specify a name for the method instance](../../adapters-and-accelerators/adapter-sap/media/970f543c-cd06-4921-86c9-c110abdc7994.gif "970f543c-cd06-4921-86c9-c110abdc7994")</span></span>  
  
### <a name="requirement-3-retrieve-sales-order-details-for-a-specific-customer-from-the-list-of-customers"></a><span data-ttu-id="613db-260">Condition 3 : Récupérer les détails des commandes client pour un client spécifique à partir de la liste des clients</span><span class="sxs-lookup"><span data-stu-id="613db-260">Requirement 3: Retrieve Sales Order Details for a Specific Customer from the List of Customers</span></span>  
 <span data-ttu-id="613db-261">Pour créer un fichier de définition d’application qui peut être utilisé pour récupérer les détails des commandes client pour un client spécifique, vous devez effectuer l’ensemble suivant de tâches.</span><span class="sxs-lookup"><span data-stu-id="613db-261">To create an application definition file that can be used to retrieve sales order details for a specific customer, you must perform the following set of tasks.</span></span>  
  
-   <span data-ttu-id="613db-262">Configurer une association entre la **client** et **SalesOrder** entités.</span><span class="sxs-lookup"><span data-stu-id="613db-262">Set up an association between the **Customer** and **SalesOrder** entities.</span></span>  
  
-   <span data-ttu-id="613db-263">Créer un **Association** méthode pour la méthode BAPI_SALESORDER_GETLIST.</span><span class="sxs-lookup"><span data-stu-id="613db-263">Create an **Association** method for the BAPI_SALESORDER_GETLIST method.</span></span>  
  
##### <a name="to-create-an-association-between-the-customer-and-salesorder-entities"></a><span data-ttu-id="613db-264">Pour créer une association entre les entités Customer et SalesOrder</span><span class="sxs-lookup"><span data-stu-id="613db-264">To create an association between the Customer and SalesOrder entities</span></span>  
  
1.  <span data-ttu-id="613db-265">Dans le volet objets de métadonnées, développez le **SalesOrder** nœud, puis développez le **méthodes** nœud.</span><span class="sxs-lookup"><span data-stu-id="613db-265">In the Metadata Objects pane, expand the **SalesOrder** node, and then expand the **Methods** node.</span></span>  
  
2.  <span data-ttu-id="613db-266">La méthode BAPI_SALESORDER_GETLIST, puis le **paramètres** nœud.</span><span class="sxs-lookup"><span data-stu-id="613db-266">Expand the BAPI_SALESORDER_GETLIST method, and then expand the **Parameters** node.</span></span>  
  
3.  <span data-ttu-id="613db-267">Développez le **CUSTOMER_NUMBER** nœud, puis cliquez sur le deuxième **CUSTOMER_NUMBER** nœud.</span><span class="sxs-lookup"><span data-stu-id="613db-267">Expand the **CUSTOMER_NUMBER** node, and then click the second **CUSTOMER_NUMBER** node.</span></span>  
  
4.  <span data-ttu-id="613db-268">Dans le volet Propriétés, sélectionnez **CustomerID [Customer]** à partir de la **identificateur** liste.</span><span class="sxs-lookup"><span data-stu-id="613db-268">In the Properties pane, select **CustomerID[Customer]** from the **Identifier** list.</span></span>  
  
     <span data-ttu-id="613db-269">![Créer une association entre les deux entités](../../adapters-and-accelerators/adapter-sap/media/ae7e1e7a-a12b-4905-b002-2a04c7050848.gif "ae7e1e7a-a12b-4905-b002-2a04c7050848")</span><span class="sxs-lookup"><span data-stu-id="613db-269">![Create association between the two entities](../../adapters-and-accelerators/adapter-sap/media/ae7e1e7a-a12b-4905-b002-2a04c7050848.gif "ae7e1e7a-a12b-4905-b002-2a04c7050848")</span></span>  
  
##### <a name="to-create-an-association-method-instance-for-the-bapisalesordergetlist-method"></a><span data-ttu-id="613db-270">Pour créer une instance de méthode d’Association pour la méthode BAPI_SALESORDER_GETLIST</span><span class="sxs-lookup"><span data-stu-id="613db-270">To create an Association method instance for the BAPI_SALESORDER_GETLIST method</span></span>  
  
1.  <span data-ttu-id="613db-271">Dans le volet objets de métadonnées, développez le **SalesOrder** nœud, puis développez le **méthodes** nœud.</span><span class="sxs-lookup"><span data-stu-id="613db-271">In the Metadata Objects pane, expand the **SalesOrder** node, and then expand the **Methods** node.</span></span>  
  
2.  <span data-ttu-id="613db-272">Développez le **BAPI_SALESORDER_GETLIST** nœud, avec le bouton droit **Instances**, puis sélectionnez **ajouter une Instance de méthode** pour ouvrir la fenêtre Créer une Instance de méthode.</span><span class="sxs-lookup"><span data-stu-id="613db-272">Expand the **BAPI_SALESORDER_GETLIST** node, right-click **Instances**, and then select **Add Method Instance** to open the Create Method Instance window.</span></span>  
  
     <span data-ttu-id="613db-273">![Ajoutez une Instance de méthode Association](../../adapters-and-accelerators/adapter-sap/media/c62a0d01-d4f3-470e-92f1-8a5cf666f8da.gif "c62a0d01-d4f3-470e-92f1-8a5cf666f8da")</span><span class="sxs-lookup"><span data-stu-id="613db-273">![Add an Association Method Instance](../../adapters-and-accelerators/adapter-sap/media/c62a0d01-d4f3-470e-92f1-8a5cf666f8da.gif "c62a0d01-d4f3-470e-92f1-8a5cf666f8da")</span></span>  
  
3.  <span data-ttu-id="613db-274">Dans la fenêtre Créer une Instance de méthode, sélectionnez **Association** pour **Type d’Instance de méthode**.</span><span class="sxs-lookup"><span data-stu-id="613db-274">In the Create Method Instance window, select **Association** for **Method Instance Type**.</span></span>  
  
4.  <span data-ttu-id="613db-275">Dans le **entités sources** liste, sélectionnez **client**.</span><span class="sxs-lookup"><span data-stu-id="613db-275">In the **Source Entities** list, select **Customer**.</span></span>  
  
5.  <span data-ttu-id="613db-276">Dans le **TypeDescriptor de retour** liste, sélectionnez **SALES_ORDERS**...</span><span class="sxs-lookup"><span data-stu-id="613db-276">In the **Return TypeDescriptor** list, select **SALES_ORDERS**..</span></span>  
  
     <span data-ttu-id="613db-277">![Créer une Instance de méthode Association](../../adapters-and-accelerators/adapter-sap/media/15975b78-8932-41ce-8c10-41891fc1fb22.gif "15975b78-8932-41ce-8c10-41891fc1fb22")</span><span class="sxs-lookup"><span data-stu-id="613db-277">![Create an Association Method Instance](../../adapters-and-accelerators/adapter-sap/media/15975b78-8932-41ce-8c10-41891fc1fb22.gif "15975b78-8932-41ce-8c10-41891fc1fb22")</span></span>  
  
6.  <span data-ttu-id="613db-278">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="613db-278">Click **OK**.</span></span>  
  
7.  <span data-ttu-id="613db-279">Dans le volet Propriétés, tapez **SalesOrderForCustomer_Instance** pour le **nom** boîte.</span><span class="sxs-lookup"><span data-stu-id="613db-279">In the Properties pane, type **SalesOrderForCustomer_Instance** for the **Name** box.</span></span>  
  
     <span data-ttu-id="613db-280">![Spécifiez un nom pour la méthode d’Association](../../adapters-and-accelerators/adapter-sap/media/0f1d13e4-e5a3-49ec-92a7-6329c6db1eb0.gif "0f1d13e4-e5a3-49ec-92a7-6329c6db1eb0")</span><span class="sxs-lookup"><span data-stu-id="613db-280">![Specify a name for the Association Method](../../adapters-and-accelerators/adapter-sap/media/0f1d13e4-e5a3-49ec-92a7-6329c6db1eb0.gif "0f1d13e4-e5a3-49ec-92a7-6329c6db1eb0")</span></span>  
  
### <a name="remove-parameters-of-systemnullable-type"></a><span data-ttu-id="613db-281">Supprimer les paramètres de Type de System.Nullable</span><span class="sxs-lookup"><span data-stu-id="613db-281">Remove Parameters of System.Nullable Type</span></span>  
 <span data-ttu-id="613db-282">Lors de la création du **Association** instance de méthode pour la méthode BAPI_SALESORDER_GETLIST, vous avez sélectionné le type de retour en tant que SALES_ORDERS.</span><span class="sxs-lookup"><span data-stu-id="613db-282">While creating the **Association** method instance for the BAPI_SALESORDER_GETLIST method, you selected the return type as SALES_ORDERS.</span></span> <span data-ttu-id="613db-283">Si vous développez le paramètre SALES_ORDER, vous remarquerez que certains paramètres sont de type de System.Nullable.</span><span class="sxs-lookup"><span data-stu-id="613db-283">If you expand the SALES_ORDER parameter, you will notice some parameters are of System.Nullable type.</span></span> <span data-ttu-id="613db-284">Vous pouvez voir le paramètre de type en sélectionnant le paramètre dans Business Data Catalog Definition Editor et en examinant la valeur de la **TypeName** propriété.</span><span class="sxs-lookup"><span data-stu-id="613db-284">You can see the parameter type by selecting the parameter in the Business Data Catalog Definition Editor, and looking at the value for the **TypeName** property.</span></span>  
  
 <span data-ttu-id="613db-285">Pour ces paramètres, l’éditeur de définition de catalogue de données métier crée un autre paramètre portant le même nom mais avec un suffixe « Spécifié ».</span><span class="sxs-lookup"><span data-stu-id="613db-285">For such parameters, the Business Data Catalog Definition Editor creates another parameter with the same name but with a “Specified” suffix.</span></span> <span data-ttu-id="613db-286">Par exemple, examinez les paramètres *ITM_NUMBER* et *ITM_NUMBERSpecified*.</span><span class="sxs-lookup"><span data-stu-id="613db-286">For example, look at parameters *ITM_NUMBER* and *ITM_NUMBERSpecified*.</span></span> <span data-ttu-id="613db-287">Microsoft Office SharePoint Server ne prend pas en charge System.Nullable paramètres.</span><span class="sxs-lookup"><span data-stu-id="613db-287">Microsoft Office SharePoint Server does not support System.Nullable parameters.</span></span> <span data-ttu-id="613db-288">Par conséquent, lorsque vous essayez d’enregistrements qui contiennent le type de paramètre System.Nullable, elle lève une exception.</span><span class="sxs-lookup"><span data-stu-id="613db-288">So, when you try records that contain the System.Nullable parameter type, it throws an exception.</span></span> <span data-ttu-id="613db-289">Par conséquent, vous devez supprimer les paramètres (avec et sans le suffixe « Spécifié » et portant le même nom) à partir de Business Data Catalog Definition Editor</span><span class="sxs-lookup"><span data-stu-id="613db-289">Therefore, you must remove both the parameters (with and without the “Specified” suffix and having the same name) from the Business Data Catalog Definition Editor</span></span>  
  
##### <a name="to-remove-the-parameters-of-systemnullable-type"></a><span data-ttu-id="613db-290">Pour supprimer les paramètres du type de System.Nullable</span><span class="sxs-lookup"><span data-stu-id="613db-290">To remove the parameters of System.Nullable type</span></span>  
  
1.  <span data-ttu-id="613db-291">Dans le volet objets de métadonnées, développez le **SalesOrder** nœud, puis développez le **méthodes** nœud.</span><span class="sxs-lookup"><span data-stu-id="613db-291">In the Metadata Objects pane, expand the **SalesOrder** node, and then expand the **Methods** node.</span></span>  
  
2.  <span data-ttu-id="613db-292">Développez le **BAPI_SALESORDER_GETLIST** nœud, puis développez le **paramètres** nœud.</span><span class="sxs-lookup"><span data-stu-id="613db-292">Expand the **BAPI_SALESORDER_GETLIST** node, and then expand the **Parameters** node.</span></span>  
  
3.  <span data-ttu-id="613db-293">Développez **SALES_ORDERS**, développez la seconde **SALES_ORDERS**, puis développez **élément**.</span><span class="sxs-lookup"><span data-stu-id="613db-293">Expand **SALES_ORDERS**, expand the second **SALES_ORDERS**, and then expand **Item**.</span></span>  
  
4.  <span data-ttu-id="613db-294">Cliquez sur le paramètre qui contient le suffixe « Specified » dans le nom, puis sélectionnez **supprimer**.</span><span class="sxs-lookup"><span data-stu-id="613db-294">Right-click the parameter that contains the "Specified" suffix in the name, and then select **Delete**.</span></span>  
  
5.  <span data-ttu-id="613db-295">Le paramètre qui porte le même nom que le paramètre que vous avez supprimé, sans le suffixe d’avec le bouton droit, puis sélectionnez **supprimer**.</span><span class="sxs-lookup"><span data-stu-id="613db-295">Right-click the parameter that has the same name as the parameter you deleted, without the suffix, and then select **Delete**.</span></span> <span data-ttu-id="613db-296">En règle générale, ce paramètre est juste avant le paramètre qui a le suffixe « Spécifié ».</span><span class="sxs-lookup"><span data-stu-id="613db-296">Typically, this parameter is right before the parameter that has the "Specified" suffix.</span></span>  
  
### <a name="set-default-parameters"></a><span data-ttu-id="613db-297">Définir les paramètres par défaut</span><span class="sxs-lookup"><span data-stu-id="613db-297">Set Default Parameters</span></span>  
 <span data-ttu-id="613db-298">Le BAPI_SALESORDER_GETLIST accepte deux paramètres.</span><span class="sxs-lookup"><span data-stu-id="613db-298">The BAPI_SALESORDER_GETLIST takes two parameters.</span></span> <span data-ttu-id="613db-299">Un de ces paramètres, TRANSACTION_GROUP, est le paramètre par défaut.</span><span class="sxs-lookup"><span data-stu-id="613db-299">One of these parameters, TRANSACTION_GROUP, is the default parameter.</span></span> <span data-ttu-id="613db-300">Par conséquent, vous devez définir la valeur par défaut pour ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="613db-300">So, you must set the default value for this parameter.</span></span>  
  
##### <a name="to-set-the-default-value-for-transactiongroup"></a><span data-ttu-id="613db-301">Pour définir la valeur par défaut pour TRANSACTION_GROUP</span><span class="sxs-lookup"><span data-stu-id="613db-301">To set the default value for TRANSACTION_GROUP</span></span>  
  
1.  <span data-ttu-id="613db-302">Dans le volet objets de métadonnées, développez le **SalesOrder** nœud, puis développez le **méthodes** nœud.</span><span class="sxs-lookup"><span data-stu-id="613db-302">In the Metadata Objects pane, expand the **SalesOrder** node, and then expand the **Methods** node.</span></span>  
  
2.  <span data-ttu-id="613db-303">Développez le **BAPI_SALESORDER_GETLIST** nœud, puis développez le **Instances** nœud.</span><span class="sxs-lookup"><span data-stu-id="613db-303">Expand the **BAPI_SALESORDER_GETLIST** node, and then expand the **Instances** node.</span></span>  
  
3.  <span data-ttu-id="613db-304">Sélectionnez le **SalesOrderForCustomer_Instance** (méthode) de l’instance et dans le volet Propriétés, cliquez sur le bouton de sélection (...) par rapport à la **DefaultValues** boîte.</span><span class="sxs-lookup"><span data-stu-id="613db-304">Select the **SalesOrderForCustomer_Instance** method instance, and in the Properties pane, click the ellipsis button (…) against the **DefaultValues** box.</span></span>  
  
4.  <span data-ttu-id="613db-305">Dans la fenêtre d’édition, développez **TRANSACTION_GROUP** nœud et pour le **TRANSACTION_GROUP** , spécifiez la valeur par défaut 0.</span><span class="sxs-lookup"><span data-stu-id="613db-305">In the Edit window, expand **TRANSACTION_GROUP** node, and for the **TRANSACTION_GROUP** box, specify the default value 0.</span></span>  
  
     <span data-ttu-id="613db-306">![Spécifiez une valeur par défaut pour l’instance de méthode](../../adapters-and-accelerators/adapter-sap/media/86e0a42d-61c0-4d5d-ba3f-55b328f79576.gif "86e0a42d-61c0-4d5d-ba3f-55b328f79576")</span><span class="sxs-lookup"><span data-stu-id="613db-306">![Specify a default value for the method instance](../../adapters-and-accelerators/adapter-sap/media/86e0a42d-61c0-4d5d-ba3f-55b328f79576.gif "86e0a42d-61c0-4d5d-ba3f-55b328f79576")</span></span>  
  
5.  <span data-ttu-id="613db-307">Cliquez sur **Fermer**.</span><span class="sxs-lookup"><span data-stu-id="613db-307">Click **Close**.</span></span>  
  
### <a name="export-the-application-definition-to-a-file"></a><span data-ttu-id="613db-308">Exporter la définition d’Application dans un fichier</span><span class="sxs-lookup"><span data-stu-id="613db-308">Export the Application Definition to a File</span></span>  
 <span data-ttu-id="613db-309">Vous venez de créer une définition d’application qui contient les métadonnées de l’instance du système SAP.</span><span class="sxs-lookup"><span data-stu-id="613db-309">You have now created an application definition that contains the SAP system instance metadata.</span></span> <span data-ttu-id="613db-310">Vous devez exporter cette définition dans un fichier XML, qui peut être importé dans Microsoft Office SharePoint Server.</span><span class="sxs-lookup"><span data-stu-id="613db-310">You must export this definition to an XML file, which can be imported into Microsoft Office SharePoint Server.</span></span>  
  
##### <a name="to-export-the-application-definition-to-a-file"></a><span data-ttu-id="613db-311">Pour exporter la définition d’application dans un fichier</span><span class="sxs-lookup"><span data-stu-id="613db-311">To export the application definition to a file</span></span>  
  
1.  <span data-ttu-id="613db-312">Dans le volet objets de métadonnées, cliquez sur le **Customer_Order** nœud, puis cliquez sur **exporter**.</span><span class="sxs-lookup"><span data-stu-id="613db-312">In the Metadata Objects pane, right-click the **Customer_Order** node, and then click **Export**.</span></span>  
  
2.  <span data-ttu-id="613db-313">Enregistrez le fichier sous Customer_Order.xml.</span><span class="sxs-lookup"><span data-stu-id="613db-313">Save the file as Customer_Order.xml.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="613db-314">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="613db-314">Next Steps</span></span>  
 <span data-ttu-id="613db-315">Vous devez maintenant créer une application SharePoint pour récupérer des données à partir d’un système SAP.</span><span class="sxs-lookup"><span data-stu-id="613db-315">You must now create a SharePoint application to retrieve data from an SAP system.</span></span> <span data-ttu-id="613db-316">Consultez [étape 3 : créer une Application SharePoint pour récupérer des données à partir de SAP](../../adapters-and-accelerators/adapter-sap/step-3-create-a-sharepoint-application-to-retrieve-data-from-sap.md) pour obtenir des instructions.</span><span class="sxs-lookup"><span data-stu-id="613db-316">See [Step 3: Create a SharePoint Application to Retrieve Data from SAP](../../adapters-and-accelerators/adapter-sap/step-3-create-a-sharepoint-application-to-retrieve-data-from-sap.md) for instructions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="613db-317">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="613db-317">See Also</span></span>  
 [<span data-ttu-id="613db-318">Didacticiel 1 : Présentation des données à partir d’un système SAP sur un Site SharePoint</span><span class="sxs-lookup"><span data-stu-id="613db-318">Tutorial 1: Presenting Data from an SAP System on a SharePoint Site</span></span>](../../adapters-and-accelerators/adapter-sap/tutorial-1-presenting-data-from-an-sap-system-on-a-sharepoint-site.md)