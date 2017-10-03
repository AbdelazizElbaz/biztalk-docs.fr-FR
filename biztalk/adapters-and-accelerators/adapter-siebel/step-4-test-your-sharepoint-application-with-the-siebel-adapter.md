---
title: "Étape 4 : Votre SharePoint Application de Test avec l’adaptateur Siebel | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ec1392fa-fdc1-42be-b4dc-75a55d8fa400
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 85cebcafcdf768686ed3f7382a0838db5062d96b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-4-test-your-sharepoint-application-with-the-siebel-adapter"></a><span data-ttu-id="7fcec-102">Étape 4 : Tester votre Application SharePoint avec l’adaptateur Siebel</span><span class="sxs-lookup"><span data-stu-id="7fcec-102">Step 4: Test Your SharePoint Application with the Siebel adapter</span></span>
<span data-ttu-id="7fcec-103">![Étape 4 sur 4](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-4of4.gif "Step_4of4")</span><span class="sxs-lookup"><span data-stu-id="7fcec-103">![Step 4 of 4](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-4of4.gif "Step_4of4")</span></span>  
  
 <span data-ttu-id="7fcec-104">**Durée :** 5 minutes.</span><span class="sxs-lookup"><span data-stu-id="7fcec-104">**Time to complete:** 5 minutes.</span></span>  
  
 <span data-ttu-id="7fcec-105">**Objectif :** une fois que vous avez ajouté des composants WebPart dans le site SharePoint et créé une application, vous devez tester l’application en récupérant des données à partir du système Siebel.</span><span class="sxs-lookup"><span data-stu-id="7fcec-105">**Objective:** After you have added Web Parts in the SharePoint site and created an application, you must test the application by retrieving some data from the Siebel system.</span></span> <span data-ttu-id="7fcec-106">Cette section fournit des instructions sur l’utilisation de l’application pour récupérer les données à partir du système Siebel.</span><span class="sxs-lookup"><span data-stu-id="7fcec-106">This section provides instructions on how to use the application to retrieve the data from the Siebel system.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="7fcec-107">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="7fcec-107">Prerequisites</span></span>  
 <span data-ttu-id="7fcec-108">Il convient que vous avez créé la page de composant WebPart contenant les composants WebPart approprié pour récupérer des données d’entreprise.</span><span class="sxs-lookup"><span data-stu-id="7fcec-108">You should have created the Web Part page containing the appropriate Web Parts to retrieve business data.</span></span> <span data-ttu-id="7fcec-109">Consultez [étape 3 : créer une Application SharePoint pour récupérer des données à partir de Siebel](../../adapters-and-accelerators/adapter-siebel/step-3-create-a-sharepoint-application-to-retrieve-data-from-siebel.md).</span><span class="sxs-lookup"><span data-stu-id="7fcec-109">See [Step 3: Create a SharePoint Application to Retrieve Data from Siebel](../../adapters-and-accelerators/adapter-siebel/step-3-create-a-sharepoint-application-to-retrieve-data-from-siebel.md).</span></span>  
  
### <a name="to-test-the-sharepoint-application"></a><span data-ttu-id="7fcec-110">Pour tester l’application SharePoint</span><span class="sxs-lookup"><span data-stu-id="7fcec-110">To test the SharePoint application</span></span>  
  
1.  <span data-ttu-id="7fcec-111">Démarrez l’Administration centrale de SharePoint 3.0.</span><span class="sxs-lookup"><span data-stu-id="7fcec-111">Start SharePoint 3.0 Central Administration.</span></span> <span data-ttu-id="7fcec-112">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft Office Server**, puis cliquez sur **Administration centrale de SharePoint 3.0**.</span><span class="sxs-lookup"><span data-stu-id="7fcec-112">Click **Start**, point to **All Programs**, point to **Microsoft Office Server**, and then click **SharePoint 3.0 Central Administration**.</span></span>  
  
2.  <span data-ttu-id="7fcec-113">Dans le volet de navigation gauche, cliquez sur le nom du fournisseur sous lequel vous avez créé l’application.</span><span class="sxs-lookup"><span data-stu-id="7fcec-113">In the left navigation pane, click the name of the SSP under which you created the application.</span></span>  
  
3.  <span data-ttu-id="7fcec-114">Dans le volet gauche, cliquez sur **afficher tout le contenu du Site**.</span><span class="sxs-lookup"><span data-stu-id="7fcec-114">In the left pane, click **View All Site Content**.</span></span> <span data-ttu-id="7fcec-115">Dans le volet droit, cliquez sur **modèles de formulaire**.</span><span class="sxs-lookup"><span data-stu-id="7fcec-115">From the right pane, click **Form Templates**.</span></span>  
  
4.  <span data-ttu-id="7fcec-116">Dans le **catégorie de formulaire** , cliquez sur **compte Siebel**.</span><span class="sxs-lookup"><span data-stu-id="7fcec-116">In the **Form Category** list, click **Siebel Account**.</span></span> <span data-ttu-id="7fcec-117">Vous avez spécifié ce nom lors de la création de la page de composant WebPart.</span><span class="sxs-lookup"><span data-stu-id="7fcec-117">You specified this name while creating the Web Part page.</span></span> <span data-ttu-id="7fcec-118">L’illustration suivante montre la page de composant WebPart que vous avez créé.</span><span class="sxs-lookup"><span data-stu-id="7fcec-118">The following figure shows the Web Part page that you created.</span></span>  
  
     <span data-ttu-id="7fcec-119">![Page composant WebPart terminée](../../adapters-and-accelerators/adapter-siebel/media/a0bfe7af-0246-4f0b-aa0d-0ee084456003.gif "a0bfe7af-0246-4f0b-aa0d-0ee084456003")</span><span class="sxs-lookup"><span data-stu-id="7fcec-119">![Completed Web Part page](../../adapters-and-accelerators/adapter-siebel/media/a0bfe7af-0246-4f0b-aa0d-0ee084456003.gif "a0bfe7af-0246-4f0b-aa0d-0ee084456003")</span></span>  
  
5.  <span data-ttu-id="7fcec-120">Le composant de gestion de compte selon une chaîne de recherche de la requête.</span><span class="sxs-lookup"><span data-stu-id="7fcec-120">Query the Account business component based on a search string.</span></span> <span data-ttu-id="7fcec-121">Par exemple, spécifiez l’expression de recherche `[Name] LIKE ‘W*’`.</span><span class="sxs-lookup"><span data-stu-id="7fcec-121">For example, specify the search expression `[Name] LIKE ‘W*’`.</span></span> <span data-ttu-id="7fcec-122">Pour cela :</span><span class="sxs-lookup"><span data-stu-id="7fcec-122">To do so:</span></span>  
  
    1.  <span data-ttu-id="7fcec-123">Dans le **liste des comptes** section, dans la première liste, sélectionnez **SearchExpression**, puis sélectionnez **est égal à**.</span><span class="sxs-lookup"><span data-stu-id="7fcec-123">In the **Account List** section, from the first list, select **SearchExpression**, and then select **is equal to**.</span></span>  
  
    2.  <span data-ttu-id="7fcec-124">Dans le champ de texte, tapez `[Name] LIKE ‘W*’`.</span><span class="sxs-lookup"><span data-stu-id="7fcec-124">In the text field, type `[Name] LIKE ‘W*’`.</span></span>  
  
    3.  <span data-ttu-id="7fcec-125">Cliquez sur **récupérer les données** lier, ou appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="7fcec-125">Click **Retrieve Data** link, or press ENTER.</span></span> <span data-ttu-id="7fcec-126">L’illustration suivante montre les enregistrements récupérés à partir du système Siebel qui répondent aux critères de recherche.</span><span class="sxs-lookup"><span data-stu-id="7fcec-126">The following figure shows the records retrieved from the Siebel system that satisfy the search criteria.</span></span>  
  
         <span data-ttu-id="7fcec-127">![Rechercher les résultats à partir du système Siebel](../../adapters-and-accelerators/adapter-siebel/media/6c4721ac-c7bc-4626-9ee0-55cf322026cf.gif "6c4721ac-c7bc-4626-9ee0-55cf322026cf")</span><span class="sxs-lookup"><span data-stu-id="7fcec-127">![Search results from the Siebel system](../../adapters-and-accelerators/adapter-siebel/media/6c4721ac-c7bc-4626-9ee0-55cf322026cf.gif "6c4721ac-c7bc-4626-9ee0-55cf322026cf")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7fcec-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7fcec-128">See Also</span></span>  
 [<span data-ttu-id="7fcec-129">Didacticiel 1 : Présentation des données à partir d’un système Siebel sur un Site SharePoint</span><span class="sxs-lookup"><span data-stu-id="7fcec-129">Tutorial 1: Presenting Data From a Siebel System on a SharePoint Site</span></span>](../../adapters-and-accelerators/adapter-siebel/tutorial-1-presenting-data-from-a-siebel-system-on-a-sharepoint-site.md)