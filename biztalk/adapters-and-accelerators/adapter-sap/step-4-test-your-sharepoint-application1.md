---
title: "Étape 4 : Tester votre SharePoint Application1 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f7ded5a5-88d5-40aa-814b-70bc0a7dcfa3
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9b8be51df02bd9796b41201c0495758c281e8f14
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-4-test-your-sharepoint-application"></a><span data-ttu-id="010a3-102">Étape 4 : Tester votre Application SharePoint</span><span class="sxs-lookup"><span data-stu-id="010a3-102">Step 4: Test Your SharePoint Application</span></span>
<span data-ttu-id="010a3-103">![Étape 4 sur 4](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-4of4.gif "Step_4of4")</span><span class="sxs-lookup"><span data-stu-id="010a3-103">![Step 4 of 4](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-4of4.gif "Step_4of4")</span></span>  
  
 <span data-ttu-id="010a3-104">**Durée :** 10 minutes</span><span class="sxs-lookup"><span data-stu-id="010a3-104">**Time to complete:** 10 minutes</span></span>  
  
 <span data-ttu-id="010a3-105">**Objectif :** une fois que vous avez ajouté des composants WebPart dans le site SharePoint et créé une application, vous devez tester l’application en récupérant des données à partir du système SAP.</span><span class="sxs-lookup"><span data-stu-id="010a3-105">**Objective:** After you have added Web Parts in the SharePoint site and created an application, you must test the application by retrieving some data from the SAP system.</span></span> <span data-ttu-id="010a3-106">Cette rubrique fournit des instructions sur l’utilisation de l’application pour récupérer les données à partir du système SAP.</span><span class="sxs-lookup"><span data-stu-id="010a3-106">This topic provides instructions on how to use the application to retrieve the data from the SAP system.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="010a3-107">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="010a3-107">Prerequisites</span></span>  
  
-   <span data-ttu-id="010a3-108">Il convient que vous avez créé la page Web qui contient les composants WebPart approprié pour récupérer des données d’entreprise.</span><span class="sxs-lookup"><span data-stu-id="010a3-108">You should have created the Web Part page that contains the appropriate Web Parts to retrieve business data.</span></span> <span data-ttu-id="010a3-109">Consultez [étape 3 : créer une Application SharePoint pour récupérer des données à partir de SAP](../../adapters-and-accelerators/adapter-sap/step-3-create-a-sharepoint-application-to-retrieve-data-from-sap.md).</span><span class="sxs-lookup"><span data-stu-id="010a3-109">See [Step 3: Create a SharePoint Application to Retrieve Data from SAP](../../adapters-and-accelerators/adapter-sap/step-3-create-a-sharepoint-application-to-retrieve-data-from-sap.md).</span></span>  
  
### <a name="to-test-the-sharepoint-application"></a><span data-ttu-id="010a3-110">Pour tester l’application SharePoint</span><span class="sxs-lookup"><span data-stu-id="010a3-110">To test the SharePoint application</span></span>  
  
1.  <span data-ttu-id="010a3-111">Démarrez l’Administration centrale de SharePoint 3.0.</span><span class="sxs-lookup"><span data-stu-id="010a3-111">Start SharePoint 3.0 Central Administration.</span></span> <span data-ttu-id="010a3-112">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft Office Server**, puis cliquez sur **Administration centrale de SharePoint 3.0**.</span><span class="sxs-lookup"><span data-stu-id="010a3-112">Click **Start**, point to **All Programs**, point to **Microsoft Office Server**, and then click **SharePoint 3.0 Central Administration**.</span></span>  
  
2.  <span data-ttu-id="010a3-113">Dans le volet de navigation gauche, cliquez sur le nom du fournisseur sous lequel vous avez créé l’application.</span><span class="sxs-lookup"><span data-stu-id="010a3-113">In the left navigation pane, click the name of the SSP under which you created the application.</span></span>  
  
3.  <span data-ttu-id="010a3-114">Dans le volet gauche, cliquez sur **afficher tout le contenu du Site**.</span><span class="sxs-lookup"><span data-stu-id="010a3-114">In the left pane, click **View All Site Content**.</span></span> <span data-ttu-id="010a3-115">Dans le volet droit, cliquez sur **modèles de formulaire**.</span><span class="sxs-lookup"><span data-stu-id="010a3-115">In the right pane, click **Form Templates**.</span></span>  
  
4.  <span data-ttu-id="010a3-116">Dans le **catégorie de formulaire** , cliquez sur **Customer_SalesOrders**.</span><span class="sxs-lookup"><span data-stu-id="010a3-116">In the **Form Category** list, click **Customer_SalesOrders**.</span></span> <span data-ttu-id="010a3-117">Vous avez spécifié ce nom lorsque vous avez créé la page de composant WebPart.</span><span class="sxs-lookup"><span data-stu-id="010a3-117">You specified this name when you created the Web Part page.</span></span> <span data-ttu-id="010a3-118">L’illustration suivante montre la page de composant WebPart que vous avez créé.</span><span class="sxs-lookup"><span data-stu-id="010a3-118">The following figure shows the Web Part page that you created.</span></span>  
  
     <span data-ttu-id="010a3-119">![Page composant WebPart terminée](../../adapters-and-accelerators/adapter-sap/media/3e9f22b1-8285-40f4-a67d-b51173c93671.gif "3e9f22b1-8285-40f4-a67d-b51173c93671")</span><span class="sxs-lookup"><span data-stu-id="010a3-119">![Completed Web Part page](../../adapters-and-accelerators/adapter-sap/media/3e9f22b1-8285-40f4-a67d-b51173c93671.gif "3e9f22b1-8285-40f4-a67d-b51173c93671")</span></span>  
  
5.  <span data-ttu-id="010a3-120">Rechercher des clients basés sur une chaîne de recherche.</span><span class="sxs-lookup"><span data-stu-id="010a3-120">Search for customers based on a search string.</span></span> <span data-ttu-id="010a3-121">Par exemple, rechercher des clients avec des noms commençant par « John E ».</span><span class="sxs-lookup"><span data-stu-id="010a3-121">For example, search for customers with names starting with "John E".</span></span> <span data-ttu-id="010a3-122">Pour cela :</span><span class="sxs-lookup"><span data-stu-id="010a3-122">To do so:</span></span>  
  
    1.  <span data-ttu-id="010a3-123">Dans la liste de clients, à partir de la première liste, cliquez sur **CustomerName**.</span><span class="sxs-lookup"><span data-stu-id="010a3-123">In the Customer List section, from the first list, click **CustomerName**.</span></span>  
  
    2.  <span data-ttu-id="010a3-124">Dans la deuxième liste, cliquez sur **commence par**.</span><span class="sxs-lookup"><span data-stu-id="010a3-124">From the second list, click **starts with**.</span></span>  
  
    3.  <span data-ttu-id="010a3-125">Dans la zone de texte, tapez **John E**.</span><span class="sxs-lookup"><span data-stu-id="010a3-125">In the text box, type **John E**.</span></span>  
  
    4.  <span data-ttu-id="010a3-126">Cliquez sur le **récupérer les données** lier ou appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="010a3-126">Click the **Retrieve Data** link or press ENTER.</span></span> <span data-ttu-id="010a3-127">L’illustration suivante montre les enregistrements récupérés à partir du système SAP qui répondent aux critères de recherche.</span><span class="sxs-lookup"><span data-stu-id="010a3-127">The following figure shows the records retrieved from the SAP system that satisfy the search criteria.</span></span>  
  
         <span data-ttu-id="010a3-128">![Rechercher les résultats à partir du système SAP](../../adapters-and-accelerators/adapter-sap/media/c97e9e2c-0908-46af-9a54-8a4354847c47.gif "c97e9e2c-0908-46af-9a54-8a4354847c47")</span><span class="sxs-lookup"><span data-stu-id="010a3-128">![Search results from the SAP system](../../adapters-and-accelerators/adapter-sap/media/c97e9e2c-0908-46af-9a54-8a4354847c47.gif "c97e9e2c-0908-46af-9a54-8a4354847c47")</span></span>  
  
6.  <span data-ttu-id="010a3-129">Vous pouvez maintenant voir les détails d’un client dans la liste et les commandes client associés aux clients, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="010a3-129">You can now see the details of any customer in the list and the sales orders associated with the customers, if any.</span></span> <span data-ttu-id="010a3-130">Pour ce faire, cliquez sur la case d’option par rapport à un numéro de client.</span><span class="sxs-lookup"><span data-stu-id="010a3-130">To do so, click the option button against a customer number.</span></span> <span data-ttu-id="010a3-131">La page est actualisée pour présenter les détails et les commandes pour un client spécifique dans les composants WebPart respectifs.</span><span class="sxs-lookup"><span data-stu-id="010a3-131">The page refreshes to present the details and the sales orders for a specific customer in the respective Web Parts.</span></span>  
  
     <span data-ttu-id="010a3-132">![Données SAP présentées sur SharePoint](../../adapters-and-accelerators/adapter-sap/media/29fc4a9e-facd-4455-bcfe-5f4d866b2dc7.gif "29fc4a9e-facd-4455-bcfe-5f4d866b2dc7")</span><span class="sxs-lookup"><span data-stu-id="010a3-132">![SAP data presented on SharePoint](../../adapters-and-accelerators/adapter-sap/media/29fc4a9e-facd-4455-bcfe-5f4d866b2dc7.gif "29fc4a9e-facd-4455-bcfe-5f4d866b2dc7")</span></span>  
  
     <span data-ttu-id="010a3-133">Si les détails des clients et la commande client associée sont affichent correctement, vous avez terminé le didacticiel.</span><span class="sxs-lookup"><span data-stu-id="010a3-133">If the details of the customers and the associated sales order are displayed correctly, you have successfully completed the tutorial.</span></span> <span data-ttu-id="010a3-134">Si aucun ou des données incorrectes s’affiche, vérifiez soigneusement votre travail pour vous assurer que vous avez effectué toutes les tâches correctement.</span><span class="sxs-lookup"><span data-stu-id="010a3-134">If no or incorrect data is displayed, carefully check your work to make sure you performed all the tasks correctly.</span></span>  
  
## <a name="summary"></a><span data-ttu-id="010a3-135">Résumé</span><span class="sxs-lookup"><span data-stu-id="010a3-135">Summary</span></span>  
 <span data-ttu-id="010a3-136">Dans ce didacticiel, vous avez créé un service WCF pour les artefacts SAP que vous souhaitez accéder à partir d’un portail SharePoint.</span><span class="sxs-lookup"><span data-stu-id="010a3-136">In this tutorial you created a WCF service for the SAP artifacts you want to access from a SharePoint Portal.</span></span> <span data-ttu-id="010a3-137">Vous avez créé également une définition d’application pour les artefacts SAP qui est importée dans un portail SharePoint pour créer des composants WebPart pour présenter des données à partir d’un système SAP.</span><span class="sxs-lookup"><span data-stu-id="010a3-137">You also created an application definition for the SAP artifacts that is imported into a SharePoint portal to create Web Parts to present data from an SAP system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="010a3-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="010a3-138">See Also</span></span>  
 [<span data-ttu-id="010a3-139">Didacticiel 1 : Présentation des données à partir d’un système SAP sur un Site SharePoint</span><span class="sxs-lookup"><span data-stu-id="010a3-139">Tutorial 1: Presenting Data from an SAP System on a SharePoint Site</span></span>](../../adapters-and-accelerators/adapter-sap/tutorial-1-presenting-data-from-an-sap-system-on-a-sharepoint-site.md)