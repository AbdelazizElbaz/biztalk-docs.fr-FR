---
title: "Scénario 1 : Afficher des données à l’aide du composant WebPart liste de données d’entreprise | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b3831814-8b70-4352-b22f-cebd08750ef5
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e1add974ca3ad0b80b7838b120920f4de47f1650
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="scenario-1-display-data-using-business-data-list-web-part"></a><span data-ttu-id="ee6ec-102">Scénario 1 : Afficher des données à l’aide du composant WebPart liste de données métiers</span><span class="sxs-lookup"><span data-stu-id="ee6ec-102">Scenario 1: Display data using Business Data List web part</span></span>
<span data-ttu-id="ee6ec-103">Nous allons utiliser la **liste de données métiers** WebPart pour le **recherche** instance de méthode.</span><span class="sxs-lookup"><span data-stu-id="ee6ec-103">We will use the **Business Data List** Web Part for the **Finder** method instance.</span></span> <span data-ttu-id="ee6ec-104">Ce composant WebPart vous permet de spécifier une expression de recherche pour récupérer une liste d’employés à partir d’Oracle E-Business Suite.</span><span class="sxs-lookup"><span data-stu-id="ee6ec-104">This Web Part enables you to specify a search expression to retrieve a list of employees from Oracle E-Business Suite.</span></span> <span data-ttu-id="ee6ec-105">Pour ce didacticiel, cela s’appelle le composant WebPart Affichage employés.</span><span class="sxs-lookup"><span data-stu-id="ee6ec-105">For this tutorial, this is called the Display Employees Web Part.</span></span> <span data-ttu-id="ee6ec-106">Cette section fournit des instructions sur la création de ce composant WebPart.</span><span class="sxs-lookup"><span data-stu-id="ee6ec-106">This section provides instructions to create this Web Part.</span></span> <span data-ttu-id="ee6ec-107">Pour plus d’informations sur la création de composants WebPart, consultez « Personnaliser les listes de données professionnelles, composants WebPart et sites » à [http://go.microsoft.com/fwlink/?LinkId=104131](http://go.microsoft.com/fwlink/?LinkId=104131).</span><span class="sxs-lookup"><span data-stu-id="ee6ec-107">For more information about creating Web Parts, see "Customize business data lists, Web Parts, and sites" at [http://go.microsoft.com/fwlink/?LinkId=104131](http://go.microsoft.com/fwlink/?LinkId=104131).</span></span>  
  
 <span data-ttu-id="ee6ec-108">Vous devez créer une page Web avant d’ajouter les composants WebPart.</span><span class="sxs-lookup"><span data-stu-id="ee6ec-108">You must create a Web Part page before adding the Web Parts.</span></span>  
  
## <a name="creating-a-web-part-page"></a><span data-ttu-id="ee6ec-109">Création d’une Page de composants WebPart</span><span class="sxs-lookup"><span data-stu-id="ee6ec-109">Creating a Web Part Page</span></span>  
 <span data-ttu-id="ee6ec-110">Cette section fournit des instructions pour créer une page WebPart.</span><span class="sxs-lookup"><span data-stu-id="ee6ec-110">This section provides instructions to create a Web Part page.</span></span>  
  
###  <span data-ttu-id="ee6ec-111"><a name="WebPart"></a>Pour créer une page Web</span><span class="sxs-lookup"><span data-stu-id="ee6ec-111"><a name="WebPart"></a> To create a Web Part page</span></span>  
  
1.  <span data-ttu-id="ee6ec-112">Démarrez l’Administration centrale de SharePoint 3.0.</span><span class="sxs-lookup"><span data-stu-id="ee6ec-112">Start SharePoint 3.0 Central Administration.</span></span> <span data-ttu-id="ee6ec-113">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft Office Server**, puis cliquez sur **Administration centrale de SharePoint 3.0**.</span><span class="sxs-lookup"><span data-stu-id="ee6ec-113">Click **Start**, point to **All Programs**, point to **Microsoft Office Server**, and click **SharePoint 3.0 Central Administration**.</span></span>  
  
2.  <span data-ttu-id="ee6ec-114">Dans le volet de navigation gauche, cliquez sur le nom du fournisseur auquel vous souhaitez importer la définition d’application.</span><span class="sxs-lookup"><span data-stu-id="ee6ec-114">In the left navigation pane, click the name of the SSP to which you want to import the application definition.</span></span>  
  
3.  <span data-ttu-id="ee6ec-115">Dans la page Administration de Services partagés, dans le coin supérieur droit, cliquez sur **Actions du Site**, puis cliquez sur **créer**.</span><span class="sxs-lookup"><span data-stu-id="ee6ec-115">On the Shared Services Administration page, in the upper-right corner, click **Site Actions**, and then click **Create**.</span></span>  
  
     <span data-ttu-id="ee6ec-116">![Menu pour créer un composant WebPart](../../adapters-and-accelerators/adapter-oracle-ebs/media/a9872c3e-f823-4c47-a538-19242565d2e9.gif "a9872c3e-f823-4c47-a538-19242565d2e9")</span><span class="sxs-lookup"><span data-stu-id="ee6ec-116">![Menu to create a web part](../../adapters-and-accelerators/adapter-oracle-ebs/media/a9872c3e-f823-4c47-a538-19242565d2e9.gif "a9872c3e-f823-4c47-a538-19242565d2e9")</span></span>  
  
4.  <span data-ttu-id="ee6ec-117">Dans la page Créer, dans le **Pages Web** , cliquez sur **Page WebPart**.</span><span class="sxs-lookup"><span data-stu-id="ee6ec-117">On the Create page, in the **Web Pages** section, click **Web Part Page**.</span></span>  
  
5.  <span data-ttu-id="ee6ec-118">Dans la page Nouveau composant WebPart, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="ee6ec-118">On the New Web Part page, do the following:</span></span>  
  
    1.  <span data-ttu-id="ee6ec-119">Dans le **nom** , tapez un nom pour la page.</span><span class="sxs-lookup"><span data-stu-id="ee6ec-119">In the **Name** field, type a name for the page.</span></span> <span data-ttu-id="ee6ec-120">Pour ce didacticiel, tapez le nom en tant que **MS_SAMPLE_EMPLOYEE**.</span><span class="sxs-lookup"><span data-stu-id="ee6ec-120">For this tutorial, type the name as **MS_SAMPLE_EMPLOYEE**.</span></span>  
  
    2.  <span data-ttu-id="ee6ec-121">Sélectionnez le **remplacer si le fichier existe déjà** case à cocher, si vous souhaitez remplacer les anciennes pages avec le même nom que la nouvelle page que vous créez.</span><span class="sxs-lookup"><span data-stu-id="ee6ec-121">Select the **Overwrite if file already exists** check box, if you want to overwrite old pages with the same name as the new page you create.</span></span>  
  
    3.  <span data-ttu-id="ee6ec-122">Dans le **disposition** section, à partir de la **choisir un modèle de disposition** , sélectionnez une disposition de la page de composant WebPart.</span><span class="sxs-lookup"><span data-stu-id="ee6ec-122">In the **Layout** section, from the **Choose a Layout Template** box, select a layout for the Web Part page.</span></span> <span data-ttu-id="ee6ec-123">Pour ce didacticiel, sélectionnez **pleine Page, Vertical**.</span><span class="sxs-lookup"><span data-stu-id="ee6ec-123">For this tutorial, select **Full Page, Vertical**.</span></span>  
  
    4.  <span data-ttu-id="ee6ec-124">Dans le **enregistrer l’emplacement** section, dans le **bibliothèque de documents** , cliquez sur **modèles de formulaire**.</span><span class="sxs-lookup"><span data-stu-id="ee6ec-124">In the **Save Location** section, in the **Document Library** list, click **Form Templates**.</span></span>  
  
    5.  <span data-ttu-id="ee6ec-125">Cliquez sur **Créer**.</span><span class="sxs-lookup"><span data-stu-id="ee6ec-125">Click **Create**.</span></span> <span data-ttu-id="ee6ec-126">L’illustration suivante montre la page de composant WebPart après sa création.</span><span class="sxs-lookup"><span data-stu-id="ee6ec-126">The following figure shows the Web Part page after it is created.</span></span>  
  
         <span data-ttu-id="ee6ec-127">![La nouvelle page WebPart](../../adapters-and-accelerators/adapter-oracle-ebs/media/23-web-part.gif "23_Web_Part")</span><span class="sxs-lookup"><span data-stu-id="ee6ec-127">![The new WebPart page](../../adapters-and-accelerators/adapter-oracle-ebs/media/23-web-part.gif "23_Web_Part")</span></span>  
  
    6.  <span data-ttu-id="ee6ec-128">Vous devez maintenant ajouter les composants WebPart à cette page.</span><span class="sxs-lookup"><span data-stu-id="ee6ec-128">You must now add the Web Parts to this page.</span></span>  
  
## <a name="adding-a-business-data-list-web-part"></a><span data-ttu-id="ee6ec-129">Ajout d’un composant WebPart de liste de données métier</span><span class="sxs-lookup"><span data-stu-id="ee6ec-129">Adding a Business Data List Web Part</span></span>  
 <span data-ttu-id="ee6ec-130">Vous devez à présent ajouter un composant WebPart de liste de données métier à la page de composant WebPart.</span><span class="sxs-lookup"><span data-stu-id="ee6ec-130">You must now add a Business Data List Web Part to the Web Part page.</span></span> <span data-ttu-id="ee6ec-131">À l’aide de ce composant WebPart vous récupère une liste d’enregistrements d’employés à partir de la table d’interface MS_SAMPLE_EMPLOYEE dans Oracle E-Business Suite qui correspond à une expression de recherche.</span><span class="sxs-lookup"><span data-stu-id="ee6ec-131">Using this Web Part you will retrieve a list of employee records from the MS_SAMPLE_EMPLOYEE interface table in Oracle E-Business Suite that matches a search expression.</span></span> <span data-ttu-id="ee6ec-132">Ce composant WebPart correspond à la **recherche** instance de méthode (*Finder_Instance*) que vous avez créé dans Business Data Catalog Definition Editor.</span><span class="sxs-lookup"><span data-stu-id="ee6ec-132">This Web Part corresponds to the **Finder** method instance (*Finder_Instance*) that you created in the Business Data Catalog Definition Editor.</span></span>  
  
#### <a name="to-add-a-business-data-list-web-part"></a><span data-ttu-id="ee6ec-133">Pour ajouter un composant WebPart de liste de données métier</span><span class="sxs-lookup"><span data-stu-id="ee6ec-133">To add a Business Data List Web Part</span></span>  
  
1.  <span data-ttu-id="ee6ec-134">Dans la page MS_SAMPLE_EMPLOYEE, cliquez sur **ajouter un composant WebPart**.</span><span class="sxs-lookup"><span data-stu-id="ee6ec-134">On the MS_SAMPLE_EMPLOYEE page, click **Add a Web Part**.</span></span>  
  
2.  <span data-ttu-id="ee6ec-135">Dans le **ajouter des WebParts** boîte de dialogue le **données d’entreprise** section, sélectionnez le **liste de données métiers** case à cocher, puis cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="ee6ec-135">In the **Add Web Parts** dialog box, in the **Business Data** section, select the **Business Data List** check box, and then click **Add**.</span></span>  
  
     <span data-ttu-id="ee6ec-136">![Options de création d’un composant WebPart de données business](../../adapters-and-accelerators/adapter-oracle-ebs/media/ae7c952c-1592-495f-9452-c1bffd44421c.gif "ae7c952c-1592-495f-9452-c1bffd44421c")</span><span class="sxs-lookup"><span data-stu-id="ee6ec-136">![Options to create a business data Web Part](../../adapters-and-accelerators/adapter-oracle-ebs/media/ae7c952c-1592-495f-9452-c1bffd44421c.gif "ae7c952c-1592-495f-9452-c1bffd44421c")</span></span>  
  
3.  <span data-ttu-id="ee6ec-137">Dans nouvellement ajoutée Business données WebPart liste, cliquez sur le **ouvrir le volet d’outils** lien.</span><span class="sxs-lookup"><span data-stu-id="ee6ec-137">In the newly added Business Data List Web Part, click the **Open the tool pane** link.</span></span>  
  
     <span data-ttu-id="ee6ec-138">![Ouvrez le volet d’outils pour le composant WebPart](../../adapters-and-accelerators/adapter-oracle-ebs/media/4e7a1cb1-69dc-4e0d-a211-6a217dc4a549.gif "4e7a1cb1-69dc-4e0d-a211-6a217dc4a549")</span><span class="sxs-lookup"><span data-stu-id="ee6ec-138">![Open the tool pane for Web Part](../../adapters-and-accelerators/adapter-oracle-ebs/media/4e7a1cb1-69dc-4e0d-a211-6a217dc4a549.gif "4e7a1cb1-69dc-4e0d-a211-6a217dc4a549")</span></span>  
  
4.  <span data-ttu-id="ee6ec-139">Le volet d’outils liste de données métiers s’ouvre dans le volet droit.</span><span class="sxs-lookup"><span data-stu-id="ee6ec-139">The Business Data List tool pane opens in the right pane.</span></span> <span data-ttu-id="ee6ec-140">Dans le **liste de données métiers** section, pour le **Type** , cliquez sur le **Parcourir** bouton.</span><span class="sxs-lookup"><span data-stu-id="ee6ec-140">In the **Business Data List** section, for the **Type** field, click the **Browse** button.</span></span>  
  
     <span data-ttu-id="ee6ec-141">![Volet d’outils liste de données métiers](../../adapters-and-accelerators/adapter-oracle-ebs/media/24-bdc-browse.gif "24_BDC_Browse")</span><span class="sxs-lookup"><span data-stu-id="ee6ec-141">![Business Data List tool pane](../../adapters-and-accelerators/adapter-oracle-ebs/media/24-bdc-browse.gif "24_BDC_Browse")</span></span>  
  
5.  <span data-ttu-id="ee6ec-142">Dans le **sélecteur de Type de données métiers** boîte de dialogue, sélectionnez le **MS_SAMPLE_EMPLOYEE_Instance** application, puis sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="ee6ec-142">In the **Business Data Type Picker** dialog box, select the **MS_SAMPLE_EMPLOYEE_Instance** application, and then click **OK**.</span></span>  
  
     <span data-ttu-id="ee6ec-143">![Sélectionnez l’instance d’application](../../adapters-and-accelerators/adapter-oracle-ebs/media/25-bdc-picker.gif "25_BDC_Picker")</span><span class="sxs-lookup"><span data-stu-id="ee6ec-143">![Select the application instance](../../adapters-and-accelerators/adapter-oracle-ebs/media/25-bdc-picker.gif "25_BDC_Picker")</span></span>  
  
6.  <span data-ttu-id="ee6ec-144">Développez le **apparence** nœud, puis, dans le **titre** , tapez un titre pour le composant WebPart.</span><span class="sxs-lookup"><span data-stu-id="ee6ec-144">Expand the **Appearance** node, and in the **Title** box, type a title for the Web Part.</span></span> <span data-ttu-id="ee6ec-145">Pour ce composant WebPart, tapez **liste d’employés**.</span><span class="sxs-lookup"><span data-stu-id="ee6ec-145">For this Web Part, type **Employee List**.</span></span>  
  
7.  <span data-ttu-id="ee6ec-146">Dans le volet d’outils liste de données d’entreprise, cliquez sur **appliquer**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="ee6ec-146">In the Business Data List tool pane, click **Apply**, and then click **OK**.</span></span> <span data-ttu-id="ee6ec-147">Le composant WebPart de liste de données Business ressemble maintenant à ceci :</span><span class="sxs-lookup"><span data-stu-id="ee6ec-147">The Business Data List Web Part now looks like the following:</span></span>  
  
     <span data-ttu-id="ee6ec-148">![Composant WebPart de liste de données de l’entreprise](../../adapters-and-accelerators/adapter-oracle-ebs/media/26-bdc-webpart.gif "26_BDC_WebPart")</span><span class="sxs-lookup"><span data-stu-id="ee6ec-148">![Business Data List Web Part](../../adapters-and-accelerators/adapter-oracle-ebs/media/26-bdc-webpart.gif "26_BDC_WebPart")</span></span>  
  
8.  <span data-ttu-id="ee6ec-149">Le composant WebPart répertorie les champs qui sont retournés par l’exécution de l’opération Select sur la table d’interface MS_SAMPLE_EMPLOYEE.</span><span class="sxs-lookup"><span data-stu-id="ee6ec-149">The Web Part lists the fields that are returned by executing the Select operation on the MS_SAMPLE_EMPLOYEE interface table.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee6ec-150">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ee6ec-150">See Also</span></span>  
 <span data-ttu-id="ee6ec-151">[Étape 3 : Créer une Application SharePoint pour récupérer des données à partir d’Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/step-3-create-a-sharepoint-application-to-retrieve-data-from-oracle-ebs.md) </span><span class="sxs-lookup"><span data-stu-id="ee6ec-151">[Step 3: Create a SharePoint Application to Retrieve Data from Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/step-3-create-a-sharepoint-application-to-retrieve-data-from-oracle-ebs.md) </span></span>  
 [<span data-ttu-id="ee6ec-152">Scénario 2 : Effectuer une recherche avec le composant WebPart zone de recherche</span><span class="sxs-lookup"><span data-stu-id="ee6ec-152">Scenario 2: Search Using the Search Box Web Part</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/scenario-2-search-using-the-search-box-web-part.md)