---
title: "Scénario 2 : Effectuer une recherche avec le composant WebPart zone de recherche | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a233772f-7577-4ac5-b55a-cb1ba2f464c7
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 03e536df00499e8965632a3952eb3ae50e3f83df
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="scenario-2--search-using-the-search-box-web-part"></a><span data-ttu-id="de0a0-102">Scénario 2 : Effectuer une recherche avec le composant WebPart zone de recherche</span><span class="sxs-lookup"><span data-stu-id="de0a0-102">Scenario 2:  Search using the search box web part</span></span>
<span data-ttu-id="de0a0-103">Nous configurerons les paramètres de recherche dans Microsoft Office SharePoint Server pour configurer une application de recherche à l’aide de laquelle vous pouvez effectuer une recherche en texte intégral sur la table d’interface MS_SAMPLE_EMPLOYEE dans Oracle E-Business Suite.</span><span class="sxs-lookup"><span data-stu-id="de0a0-103">We will configure the search settings in Microsoft Office SharePoint Server to configure a search application using which you can perform a full text search on the MS_SAMPLE_EMPLOYEE interface table in Oracle E-Business Suite.</span></span> <span data-ttu-id="de0a0-104">Une version ultérieure, nous allons ajouter une zone WebPart de recherche à d’où vous pouvez effectuer la recherche.</span><span class="sxs-lookup"><span data-stu-id="de0a0-104">Later, we will add a Search Box Web Part to from where you can perform the search.</span></span>  
  
 
  
##  <span data-ttu-id="de0a0-105"><a name="Define"></a>Définir la Source de contenu</span><span class="sxs-lookup"><span data-stu-id="de0a0-105"><a name="Define"></a> Define the Content Source</span></span>  
 <span data-ttu-id="de0a0-106">Cette section présente sur la définition d’une source de contenu à partir de sur lequel Microsoft Office SharePoint Server peut analyser les données.</span><span class="sxs-lookup"><span data-stu-id="de0a0-106">This section talks about defining a content source from where Microsoft Office SharePoint Server can crawl the data.</span></span> <span data-ttu-id="de0a0-107">Cela implique le mappage du contenu à l’énumérateur d’Id instance de méthode créé dans [étape 2 : créer un fichier de définition d’application pour les artefacts d’Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/step-2-create-an-application-definition-file-for-the-oracle-ebs-artifacts.md).</span><span class="sxs-lookup"><span data-stu-id="de0a0-107">This involves mapping the content to the Id Enumerator method instance created in [Step 2: Create an application definition file for the Oracle E-Business Suite artifacts](../../adapters-and-accelerators/adapter-oracle-ebs/step-2-create-an-application-definition-file-for-the-oracle-ebs-artifacts.md).</span></span>  
  
#### <a name="to-define-a-content-source"></a><span data-ttu-id="de0a0-108">Pour définir une source de contenu</span><span class="sxs-lookup"><span data-stu-id="de0a0-108">To define a content source</span></span>  
  
1.  <span data-ttu-id="de0a0-109">Démarrez l’Administration centrale de SharePoint 3.0.</span><span class="sxs-lookup"><span data-stu-id="de0a0-109">Start SharePoint 3.0 Central Administration.</span></span> <span data-ttu-id="de0a0-110">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft Office Server**, puis cliquez sur **Administration centrale de SharePoint 3.0**.</span><span class="sxs-lookup"><span data-stu-id="de0a0-110">Click **Start**, point to **All Programs**, point to **Microsoft Office Server**, and then click **SharePoint 3.0 Central Administration**.</span></span>  
  
2.  <span data-ttu-id="de0a0-111">Dans le volet de navigation gauche, cliquez sur le nom de la Service fournisseur partagés (SSP) dans lequel vous souhaitez configurer l’application de recherche.</span><span class="sxs-lookup"><span data-stu-id="de0a0-111">In the left navigation pane, click the name of the Shared Service Provider (SSP) where you want to configure the search application.</span></span>  
  
3.  <span data-ttu-id="de0a0-112">Sur la page d’accueil, dans le **recherche** , cliquez sur **paramètres de recherche**.</span><span class="sxs-lookup"><span data-stu-id="de0a0-112">On the Home page, in the **Search** section, click **Search settings**.</span></span>  
  
4.  <span data-ttu-id="de0a0-113">Dans la page Configurer les paramètres de recherche, dans le volet gauche sous **analyse**, cliquez sur **compte d’accès au contenu par défaut** pour spécifier un compte à utiliser en tant que le compte par défaut lors de l’analyse de contenu.</span><span class="sxs-lookup"><span data-stu-id="de0a0-113">On the Configure Search Settings page, in the left pane under **Crawling**, click **Default content access account** to specify an account to use as the default account when crawling content.</span></span>  
  
5.  <span data-ttu-id="de0a0-114">Dans la page compte d’accès au contenu par défaut, spécifiez les informations d’identification utilisateur et mot de passe, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="de0a0-114">On the Default Content Access Account page, specify the user name and password credentials, and click **OK**.</span></span> <span data-ttu-id="de0a0-115">Vous revenez à la page d’Administration de la recherche.</span><span class="sxs-lookup"><span data-stu-id="de0a0-115">You will return to the Search Administration page.</span></span>  
  
6.  <span data-ttu-id="de0a0-116">Dans le volet gauche sous **analyse**, cliquez sur **Sources de contenu**.</span><span class="sxs-lookup"><span data-stu-id="de0a0-116">In the left pane under **Crawling**, click **Content Sources**.</span></span>  
  
7.  <span data-ttu-id="de0a0-117">Dans la page Gérer les Sources de contenu, cliquez sur **nouvelle Source de contenu**.</span><span class="sxs-lookup"><span data-stu-id="de0a0-117">On the Manage Content Sources page, click **New Content Source**.</span></span>  
  
8.  <span data-ttu-id="de0a0-118">Dans la page Gérer les Sources de contenu, cliquez sur **nouvelle Source de contenu**.</span><span class="sxs-lookup"><span data-stu-id="de0a0-118">On the Manage Content Sources page, click **New Content Source**.</span></span>  
  
9. <span data-ttu-id="de0a0-119">Dans la page Source de contenu à ajouter :</span><span class="sxs-lookup"><span data-stu-id="de0a0-119">On the Add Content Source page:</span></span>  
  
    1.  <span data-ttu-id="de0a0-120">Type `MS_SAMPLE_EMPLOYEE` dans les **nom** boîte.</span><span class="sxs-lookup"><span data-stu-id="de0a0-120">Type `MS_SAMPLE_EMPLOYEE` in the **Name** box.</span></span>  
  
    2.  <span data-ttu-id="de0a0-121">Dans le **le Type de Source de contenu** zone, cliquez sur **données d’entreprise**.</span><span class="sxs-lookup"><span data-stu-id="de0a0-121">In the **Content Source Type** area, click **Business Data**.</span></span>  
  
    3.  <span data-ttu-id="de0a0-122">Dans le **Applications** zone, cliquez sur **analyse des applications sélectionnées**, puis sélectionnez le **MS_SAMPLE_EMPLOYEE_Instance** case à cocher.</span><span class="sxs-lookup"><span data-stu-id="de0a0-122">In the **Applications** area, click **Crawl selected applications**, and then select the **MS_SAMPLE_EMPLOYEE_Instance** check box.</span></span>  
  
    4.  <span data-ttu-id="de0a0-123">Dans le **démarrer l’analyse complète** zone, sélectionnez le **démarrer une analyse complète de cette source de contenu** case à cocher, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="de0a0-123">In the **Start Full Crawl** area, select the **Start full crawl of this content source** check box, and then click **OK**.</span></span>  
  
         <span data-ttu-id="de0a0-124">![Ajouter une source de contenu](../../adapters-and-accelerators/adapter-oracle-ebs/media/27-add-content-source.gif "27_Add_Content_Source")</span><span class="sxs-lookup"><span data-stu-id="de0a0-124">![Add content source](../../adapters-and-accelerators/adapter-oracle-ebs/media/27-add-content-source.gif "27_Add_Content_Source")</span></span>  
  
10. <span data-ttu-id="de0a0-125">Vous revenez à la page Gérer les Sources de contenu avec la nouvelle source de contenu ajoutée.</span><span class="sxs-lookup"><span data-stu-id="de0a0-125">You will return to the Manage Content Sources page with the new content source added.</span></span> <span data-ttu-id="de0a0-126">La source de contenu analyse les données de la table d’interface MS_SAMPLE_EMPLOYEE dans Oracle E-Business Suite.</span><span class="sxs-lookup"><span data-stu-id="de0a0-126">The content source will crawl through the data in the MS_SAMPLE_EMPLOYEE interface table in the Oracle E-Business Suite.</span></span> <span data-ttu-id="de0a0-127">Attendez que l’analyse est terminée.</span><span class="sxs-lookup"><span data-stu-id="de0a0-127">Wait until the crawling is completed.</span></span>  
  
11. <span data-ttu-id="de0a0-128">Dans le volet gauche sous **analyse**, cliquez sur **journal d’analyse**, puis vérifiez le fichier journal pour vous assurer que l’analyse a réussi.</span><span class="sxs-lookup"><span data-stu-id="de0a0-128">In the left pane under **Crawling**, click **Crawl Log**, and then verify the log file to ensure that the crawling is successful.</span></span>  
  
##  <span data-ttu-id="de0a0-129"><a name="Scope"></a>Définir une étendue pour le contenu analysé</span><span class="sxs-lookup"><span data-stu-id="de0a0-129"><a name="Scope"></a> Define a Scope for the Crawled Content</span></span>  
  
1.  <span data-ttu-id="de0a0-130">Démarrez l’Administration centrale de SharePoint 3.0.</span><span class="sxs-lookup"><span data-stu-id="de0a0-130">Start SharePoint 3.0 Central Administration.</span></span> <span data-ttu-id="de0a0-131">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft Office Server**, puis cliquez sur **Administration centrale de SharePoint 3.0**.</span><span class="sxs-lookup"><span data-stu-id="de0a0-131">Click **Start**, point to **All Programs**, point to **Microsoft Office Server**, and then click **SharePoint 3.0 Central Administration**.</span></span>  
  
2.  <span data-ttu-id="de0a0-132">Dans le volet de navigation gauche, cliquez sur le nom de la Service fournisseur partagés (SSP) dans lequel vous souhaitez configurer l’application de recherche.</span><span class="sxs-lookup"><span data-stu-id="de0a0-132">In the left navigation pane, click the name of the Shared Service Provider (SSP) where you want to configure the search application.</span></span>  
  
3.  <span data-ttu-id="de0a0-133">Sur la page d’accueil, dans le **recherche** , cliquez sur **paramètres de recherche**.</span><span class="sxs-lookup"><span data-stu-id="de0a0-133">On the Home page, in the **Search** section, click **Search settings**.</span></span>  
  
4.  <span data-ttu-id="de0a0-134">Dans la page Configurer les paramètres de recherche, dans le volet gauche sous **interroge et résultats**, cliquez sur **étendues** pour définir une étendue de l’analyse de données.</span><span class="sxs-lookup"><span data-stu-id="de0a0-134">On the Configure Search Settings page, in the left pane under **Queries and Results**, click **Scopes** to define a scope for the crawling of data.</span></span>  
  
5.  <span data-ttu-id="de0a0-135">Dans la page Afficher les étendues, cliquez sur **nouvelle étendue**.</span><span class="sxs-lookup"><span data-stu-id="de0a0-135">On the View Scopes page, click **New Scope**.</span></span>  
  
6.  <span data-ttu-id="de0a0-136">Dans la page Créer une étendue, tapez `MS_SAMPLE_EMPLOYEE_Search` dans les **titre** zone, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="de0a0-136">On the Create Scope page, type `MS_SAMPLE_EMPLOYEE_Search` in the **Title** box, and then click **OK**.</span></span>  
  
     <span data-ttu-id="de0a0-137">![Créer une étendue](../../adapters-and-accelerators/adapter-oracle-ebs/media/28-create-scope.gif "28_Create_Scope")</span><span class="sxs-lookup"><span data-stu-id="de0a0-137">![Create a scope](../../adapters-and-accelerators/adapter-oracle-ebs/media/28-create-scope.gif "28_Create_Scope")</span></span>  
  
7.  <span data-ttu-id="de0a0-138">Vous revenez à la page Afficher les étendues avec la nouvelle étendue ajoutée.</span><span class="sxs-lookup"><span data-stu-id="de0a0-138">You will return to the View Scopes page with the new scope added.</span></span> <span data-ttu-id="de0a0-139">Dans le **état de mise à jour** colonne pour l’étendue nouvellement ajoutée, cliquez sur le **ajouter des règles** lien.</span><span class="sxs-lookup"><span data-stu-id="de0a0-139">In the **Update Status** column for the newly added scope, click the **Add rules** link.</span></span>  
  
8.  <span data-ttu-id="de0a0-140">Dans la page Ajouter une règle d’étendue :</span><span class="sxs-lookup"><span data-stu-id="de0a0-140">On the Add Scope Rule page:</span></span>  
  
    1.  <span data-ttu-id="de0a0-141">Dans le **Type de règle d’étendue** zone, cliquez sur **Source de contenu**.</span><span class="sxs-lookup"><span data-stu-id="de0a0-141">In the **Scope Rule Type** area, click **Content Source**.</span></span>  
  
    2.  <span data-ttu-id="de0a0-142">Dans le **Source du contenu** , cliquez sur **MS_SAMPLE_EMPLOYEE**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="de0a0-142">In the **Content Source** list, click **MS_SAMPLE_EMPLOYEE**, and then click **OK**.</span></span>  
  
         <span data-ttu-id="de0a0-143">![Ajouter une règle d’étendue](../../adapters-and-accelerators/adapter-oracle-ebs/media/29-add-scope-rule.gif "29_Add_Scope_Rule")</span><span class="sxs-lookup"><span data-stu-id="de0a0-143">![Add a scope rule](../../adapters-and-accelerators/adapter-oracle-ebs/media/29-add-scope-rule.gif "29_Add_Scope_Rule")</span></span>  
  
9. <span data-ttu-id="de0a0-144">Vous revenez à la page Afficher les étendues à la règle ajoutée pour l’étendue.</span><span class="sxs-lookup"><span data-stu-id="de0a0-144">You will return to the View Scopes page with the rule added for the scope.</span></span> <span data-ttu-id="de0a0-145">Dans le volet gauche, cliquez sur **Administration de la recherche**.</span><span class="sxs-lookup"><span data-stu-id="de0a0-145">In the left pane, click **Search Administration**.</span></span>  
  
10. <span data-ttu-id="de0a0-146">Dans la page Administration de la recherche, recherchez le **étendues nécessitant une mise à jour** de ligne, puis cliquez sur le **démarrer la mise à jour maintenant** lien.</span><span class="sxs-lookup"><span data-stu-id="de0a0-146">On the Search Administration page, locate the **Scopes needing update** row, and click the **Start update now** link.</span></span>  
  
 <span data-ttu-id="de0a0-147">Le **état de mise à jour de l’étendue** ligne affiche l’état de la mise à jour de l’étendue.</span><span class="sxs-lookup"><span data-stu-id="de0a0-147">The **Scope update status** row will display the status of the scope update.</span></span> <span data-ttu-id="de0a0-148">Attendez que la mise à jour est terminée.</span><span class="sxs-lookup"><span data-stu-id="de0a0-148">Wait until the update is complete.</span></span> <span data-ttu-id="de0a0-149">Une fois la mise à jour est terminée, l’étendue est prête à être utilisée.</span><span class="sxs-lookup"><span data-stu-id="de0a0-149">After the updated is completed, the scope is ready to be used.</span></span>  
  
##  <span data-ttu-id="de0a0-150"><a name="AddScope"></a>Ajout de l’étendue à la liste déroulante de recherche</span><span class="sxs-lookup"><span data-stu-id="de0a0-150"><a name="AddScope"></a> Add the Scope to the Search Dropdown</span></span>  
 <span data-ttu-id="de0a0-151">Après avoir créé l’étendue de recherche, vous devez ajouter l’étendue à la liste déroulante de recherche dans Microsoft Office SharePoint Server afin qu’il peut être utilisé.</span><span class="sxs-lookup"><span data-stu-id="de0a0-151">After you have created the search scope, you must add the scope to the search dropdown in Microsoft Office SharePoint Server so that it can be used.</span></span>  
  
#### <a name="to-add-the-scope-to-the-search-dropdown"></a><span data-ttu-id="de0a0-152">Pour ajouter l’étendue à la liste déroulante de recherche</span><span class="sxs-lookup"><span data-stu-id="de0a0-152">To add the scope to the search dropdown</span></span>  
  
1.  <span data-ttu-id="de0a0-153">Démarrez l’Administration centrale de SharePoint 3.0.</span><span class="sxs-lookup"><span data-stu-id="de0a0-153">Start SharePoint 3.0 Central Administration.</span></span> <span data-ttu-id="de0a0-154">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft Office Server**, puis cliquez sur **Administration centrale de SharePoint 3.0**.</span><span class="sxs-lookup"><span data-stu-id="de0a0-154">Click **Start**, point to **All Programs**, point to **Microsoft Office Server**, and then click **SharePoint 3.0 Central Administration**.</span></span>  
  
2.  <span data-ttu-id="de0a0-155">Dans le volet de navigation gauche, cliquez sur le nom de la Service fournisseur partagés (SSP) dans lequel vous souhaitez configurer l’application de recherche.</span><span class="sxs-lookup"><span data-stu-id="de0a0-155">In the left navigation pane, click the name of the Shared Service Provider (SSP) where you want to configure the search application.</span></span>  
  
3.  <span data-ttu-id="de0a0-156">Dans la page Administration de Services partagés, dans le coin supérieur droit, cliquez sur **Actions du Site**, puis cliquez sur **paramètres du Site**.</span><span class="sxs-lookup"><span data-stu-id="de0a0-156">On the Shared Services Administration page, in the upper-right corner, click **Site Actions**, and then click **Site Settings**.</span></span>  
  
4.  <span data-ttu-id="de0a0-157">Dans la page Paramètres du Site, dans le **Administration de Collection de sites** , cliquez sur **zones de recherche**.</span><span class="sxs-lookup"><span data-stu-id="de0a0-157">On the Site Settings page, in the **Site Collection Administration** section, click **Search scopes**.</span></span>  
  
5.  <span data-ttu-id="de0a0-158">Dans la page Afficher les étendues, cliquez sur le **liste déroulante de recherche** lien.</span><span class="sxs-lookup"><span data-stu-id="de0a0-158">On the View Scopes page, click the **Search Dropdown** link.</span></span>  
  
     <span data-ttu-id="de0a0-159">![Afficher les étendues](../../adapters-and-accelerators/adapter-oracle-ebs/media/30-view-scope.gif "30_View_Scope")</span><span class="sxs-lookup"><span data-stu-id="de0a0-159">![View scopes](../../adapters-and-accelerators/adapter-oracle-ebs/media/30-view-scope.gif "30_View_Scope")</span></span>  
  
6.  <span data-ttu-id="de0a0-160">Dans la page Modifier le groupe affichage étendue :</span><span class="sxs-lookup"><span data-stu-id="de0a0-160">On the Edit Scope Display Group page:</span></span>  
  
    1.  <span data-ttu-id="de0a0-161">Dans le **étendues** zone, sélectionnez le **MS_SAMPLE_EMPLOYEE_Search** case à cocher.</span><span class="sxs-lookup"><span data-stu-id="de0a0-161">In the **Scopes** area, select the **MS_SAMPLE_EMPLOYEE_Search** check box.</span></span>  
  
    2.  <span data-ttu-id="de0a0-162">Dans le **étendue par défaut** zone, cliquez sur **MS_SAMPLE_EMPLOYEE_Search** dans les **étendue par défaut** liste, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="de0a0-162">In the **Default Scope** area, click **MS_SAMPLE_EMPLOYEE_Search** in the **Default Scope** list, and then click **OK**.</span></span>  
  
         <span data-ttu-id="de0a0-163">![Page Modifier le groupe affichage étendue](../../adapters-and-accelerators/adapter-oracle-ebs/media/31-edit-scope-display-group.gif "31_Edit_Scope_Display_Group")</span><span class="sxs-lookup"><span data-stu-id="de0a0-163">![Edit Scope Display Group page](../../adapters-and-accelerators/adapter-oracle-ebs/media/31-edit-scope-display-group.gif "31_Edit_Scope_Display_Group")</span></span>  
  
7.  <span data-ttu-id="de0a0-164">Vous revenez à la page Afficher les étendues avec l’étendue MS_SAMPLE_EMPLOYEE_Search ajouté dans le groupe d’affichage de liste déroulante de recherche.</span><span class="sxs-lookup"><span data-stu-id="de0a0-164">You will return to the View Scopes page with the MS_SAMPLE_EMPLOYEE_Search scope added in the Search Dropdown display group.</span></span>  
  
##  <span data-ttu-id="de0a0-165"><a name="SearchWebPart"></a>Ajouter le composant WebPart zone de recherche</span><span class="sxs-lookup"><span data-stu-id="de0a0-165"><a name="SearchWebPart"></a> Add the Search Box Web Part</span></span>  
 <span data-ttu-id="de0a0-166">Pour permettre aux utilisateurs d’effectuer une recherche en texte intégral sur la table d’interface MS_SAMPLE_EMPLOYEE dans Oracle E-Business Suite, vous devez maintenant créer une page de composants WebPart et ajouter un composant WebPart zone de recherche à celui-ci.</span><span class="sxs-lookup"><span data-stu-id="de0a0-166">To enable the users to perform a full-text search on the MS_SAMPLE_EMPLOYEE interface table in Oracle E-Business Suite, you must now create a Web part page, and add a Search Box Web Part to it.</span></span>  
  
#### <a name="to-add-the-search-box-web-part"></a><span data-ttu-id="de0a0-167">Pour ajouter le composant WebPart zone de recherche</span><span class="sxs-lookup"><span data-stu-id="de0a0-167">To add the Search Box Web Part</span></span>  
  
1.  <span data-ttu-id="de0a0-168">Créer une page WebPart appelée **MS_SAMPLE_EMPLOYEE_Search**.</span><span class="sxs-lookup"><span data-stu-id="de0a0-168">Create a Web Part page called **MS_SAMPLE_EMPLOYEE_Search**.</span></span> <span data-ttu-id="de0a0-169">Pour connaître les étapes de création d’une page Web, voir [scénario 1 : afficher des données à l’aide du composant WebPart liste de données métiers](../../adapters-and-accelerators/adapter-oracle-ebs/scenario-1-display-data-using-business-data-list-web-part.md) dans [scénario 1 : afficher des données à l’aide du composant WebPart liste de données métiers](../../adapters-and-accelerators/adapter-oracle-ebs/scenario-1-display-data-using-business-data-list-web-part.md).</span><span class="sxs-lookup"><span data-stu-id="de0a0-169">To know the steps for creating a Web Part page, see [Scenario 1: Display data using Business Data List web part](../../adapters-and-accelerators/adapter-oracle-ebs/scenario-1-display-data-using-business-data-list-web-part.md) in [Scenario 1: Display data using Business Data List web part](../../adapters-and-accelerators/adapter-oracle-ebs/scenario-1-display-data-using-business-data-list-web-part.md).</span></span>  
  
2.  <span data-ttu-id="de0a0-170">Dans la page MS_SAMPLE_EMPLOYEE_Search, cliquez sur **ajouter un composant WebPart**.</span><span class="sxs-lookup"><span data-stu-id="de0a0-170">On the MS_SAMPLE_EMPLOYEE_Search page, click **Add a Web Part**.</span></span>  
  
3.  <span data-ttu-id="de0a0-171">Dans le **ajouter des WebParts** boîte de dialogue le **recherche** section, sélectionnez le **zone de recherche** case à cocher, puis cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="de0a0-171">In the **Add Web Parts** dialog box, in the **Search** section, select the **Search Box** check box, and then click **Add**.</span></span>  
  
     <span data-ttu-id="de0a0-172">![Ajouter le composant WebPart zone de recherche](../../adapters-and-accelerators/adapter-oracle-ebs/media/32-search-web-part.gif "32_Search_Web_Part")</span><span class="sxs-lookup"><span data-stu-id="de0a0-172">![Add the Search Box Web Part](../../adapters-and-accelerators/adapter-oracle-ebs/media/32-search-web-part.gif "32_Search_Web_Part")</span></span>  
  
4.  <span data-ttu-id="de0a0-173">Le composant WebPart zone recherche est ajouté à la page MS_SAMPLE_EMPLOYEE_Search.</span><span class="sxs-lookup"><span data-stu-id="de0a0-173">The Search Box Web part is added to the MS_SAMPLE_EMPLOYEE_Search page.</span></span>  
  
     <span data-ttu-id="de0a0-174">![Composant WebPart zone de recherche](../../adapters-and-accelerators/adapter-oracle-ebs/media/33-search-web-part-final.gif "33_Search_Web_Part_Final")</span><span class="sxs-lookup"><span data-stu-id="de0a0-174">![Search Box Web Part](../../adapters-and-accelerators/adapter-oracle-ebs/media/33-search-web-part-final.gif "33_Search_Web_Part_Final")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de0a0-175">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="de0a0-175">See Also</span></span>  
 [<span data-ttu-id="de0a0-176">Étape 3 : Créer une application SharePoint pour récupérer des données à partir d’Oracle E-Business Suite</span><span class="sxs-lookup"><span data-stu-id="de0a0-176">Step 3: Create a SharePoint application to retrieve data from Oracle E-Business Suite</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/step-3-create-a-sharepoint-application-to-retrieve-data-from-oracle-ebs.md)  
 [<span data-ttu-id="de0a0-177">Scénario 1 : Afficher des données à l’aide du composant WebPart liste de données métiers</span><span class="sxs-lookup"><span data-stu-id="de0a0-177">Scenario 1: Display data using Business Data List web part</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/scenario-1-display-data-using-business-data-list-web-part.md)