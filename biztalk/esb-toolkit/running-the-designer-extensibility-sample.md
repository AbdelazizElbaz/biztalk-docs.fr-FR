---
title: "Exécution de l’exemple de l’extensibilité du Concepteur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 05ac3b50-5bf2-4566-8654-472391476d1f
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2b26c483568e1ceb05679d7548721c1cce818fde
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="running-the-designer-extensibility-sample"></a><span data-ttu-id="a44b7-102">L’exemple de l’extensibilité du concepteur en cours d’exécution</span><span class="sxs-lookup"><span data-stu-id="a44b7-102">Running the Designer Extensibility Sample</span></span>
<span data-ttu-id="a44b7-103">L’exemple de l’extensibilité du concepteur utilise deux unités d’exemple pour illustrer comment vous pouvez fournir des options de configuration au moment du design pour les programmes de résolution personnalisés et pour les services d’itinéraire.</span><span class="sxs-lookup"><span data-stu-id="a44b7-103">The Designer Extensibility sample uses two sample extenders to demonstrate how you can provide design-time configuration options for custom resolvers and for itinerary services.</span></span>  
  
 <span data-ttu-id="a44b7-104">**Pour exécuter l’exemple de l’extensibilité du Concepteur**</span><span class="sxs-lookup"><span data-stu-id="a44b7-104">**To run the Designer Extensibility sample**</span></span>  
  
1.  <span data-ttu-id="a44b7-105">Démarrez [!INCLUDE[vs2010](../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a44b7-105">Start [!INCLUDE[vs2010](../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="a44b7-106">Dans Visual Studio, pointez sur **nouveau** sur la **fichier** menu, puis sur **projet**.</span><span class="sxs-lookup"><span data-stu-id="a44b7-106">In Visual Studio, point to **New** on the **File** menu, and then click **Project**.</span></span>  
  
3.  <span data-ttu-id="a44b7-107">Sélectionnez le modèle de bibliothèque de classes c#, type **ItineraryLibrary** dans les **nom** zone, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="a44b7-107">Select the C# Class Library template, type **ItineraryLibrary** in the **Name** box, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="a44b7-108">Dans l’Explorateur de solutions, cliquez sur le projet ItineraryLibrary, pointez sur **ajouter**, puis cliquez sur **nouvel itinéraire**.</span><span class="sxs-lookup"><span data-stu-id="a44b7-108">In Solution Explorer, right-click the ItineraryLibrary project, point to **Add**, and then click **New Itinerary**.</span></span>  
  
5.  <span data-ttu-id="a44b7-109">Dans le **nom** , tapez **TestItinerary**, puis appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="a44b7-109">In the **Name** box, type **TestItinerary**, and then press ENTER.</span></span>  
  
6.  <span data-ttu-id="a44b7-110">Dans la boîte à outils, cliquez sur un élément de modèle On rampe d’entrée, puis faites-le glisser vers l’aire de conception.</span><span class="sxs-lookup"><span data-stu-id="a44b7-110">In the Toolbox, click an On-Ramp model element, and then drag it to the design surface.</span></span>  
  
7.  <span data-ttu-id="a44b7-111">Dans la boîte à outils, cliquez sur un élément de modèle de Service de l’itinéraire, puis faites-le glisser vers l’aire de conception.</span><span class="sxs-lookup"><span data-stu-id="a44b7-111">In the Toolbox, click an Itinerary Service model element, and then drag it to the design surface.</span></span>  
  
8.  <span data-ttu-id="a44b7-112">Dans la boîte à outils, cliquez sur un autre élément de modèle de Service de l’itinéraire, puis faites-le glisser vers l’aire de conception.</span><span class="sxs-lookup"><span data-stu-id="a44b7-112">In the Toolbox, click another Itinerary Service model element, and then drag it to the design surface.</span></span>  
  
9. <span data-ttu-id="a44b7-113">Dans la boîte à outils, cliquez sur un élément de modèle de démarrage de la valeur Off, puis faites-le glisser vers l’aire de conception.</span><span class="sxs-lookup"><span data-stu-id="a44b7-113">In the Toolbox, click an Off-Ramp model element, and then drag it to the design surface.</span></span>  
  
10. <span data-ttu-id="a44b7-114">Dans la boîte à outils, cliquez sur l’outil de connecteur, puis faites glisser une connexion entre le **OnRamp1** élément de modèle et la **ItineraryService1** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="a44b7-114">In the Toolbox, click the Connector tool, and then drag a connection between the **OnRamp1** model element and the **ItineraryService1** model element.</span></span>  
  
11. <span data-ttu-id="a44b7-115">Dans la boîte à outils, cliquez sur l’outil de connecteur, puis faites glisser une connexion entre le **ItineraryService1** élément de modèle et la **ItineraryService2** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="a44b7-115">In the Toolbox, click the Connector tool, and then drag a connection between the **ItineraryService1** model element and the **ItineraryService2** model element.</span></span>  
  
12. <span data-ttu-id="a44b7-116">Dans la boîte à outils, cliquez sur l’outil de connecteur, puis faites glisser une connexion entre le **ItineraryService2** élément de modèle et la **OffRamp1** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="a44b7-116">In the Toolbox, click the Connector tool, and then drag a connection between the **ItineraryService2** model element and the **OffRamp1** model element.</span></span>  
  
13. <span data-ttu-id="a44b7-117">Cliquez sur le **OnRamp1** élément de modèle, puis dans la fenêtre Propriétés, définissez la propriété d’extendeur **Extension du Service ESB rampe d’entrée**.</span><span class="sxs-lookup"><span data-stu-id="a44b7-117">Click the **OnRamp1** model element, and then in the Properties window, set the Extender property to **On-Ramp ESB Service Extension**.</span></span>  
  
14. <span data-ttu-id="a44b7-118">Définir le **Application BizTalk** propriété **Microsoft.Practices.ESB**.</span><span class="sxs-lookup"><span data-stu-id="a44b7-118">Set the **BizTalk Application** property to **Microsoft.Practices.ESB**.</span></span>  
  
15. <span data-ttu-id="a44b7-119">Définir le **Port de réception** propriété **OnRamp.Itinerary**.</span><span class="sxs-lookup"><span data-stu-id="a44b7-119">Set the **Receive Port** property to **OnRamp.Itinerary**.</span></span>  
  
16. <span data-ttu-id="a44b7-120">Cliquez sur le **ItinearyService1** élément de modèle et, dans la fenêtre Propriétés, définissez la **extendeur** propriété **exemple d’Extension de Service d’Orchestration itinéraire**.</span><span class="sxs-lookup"><span data-stu-id="a44b7-120">Click the **ItinearyService1** model element, and then in the Properties window, set the **Extender** property to **Sample Orchestration Itinerary Service Extension**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a44b7-121">Il s’agit de l’extension personnalisée installée en tant que partie de l’exemple de l’extensibilité du concepteur.</span><span class="sxs-lookup"><span data-stu-id="a44b7-121">This is the custom extension installed as part of the Designer Extensibility sample.</span></span> <span data-ttu-id="a44b7-122">Il vous permet de vous permet d’ajouter des propriétés pour le jeu de propriétés passé à un service d’orchestration d’itinéraire.</span><span class="sxs-lookup"><span data-stu-id="a44b7-122">It allows you to add properties to the property bag passed to an orchestration-based itinerary service.</span></span>  
  
17. <span data-ttu-id="a44b7-123">Définir le **OtherValue** propriété **1**.</span><span class="sxs-lookup"><span data-stu-id="a44b7-123">Set the **OtherValue** property to **1**.</span></span>  
  
18. <span data-ttu-id="a44b7-124">Définir le **ServiceName** propriété **Microsoft.Practices.ESB.Services.Routing**.</span><span class="sxs-lookup"><span data-stu-id="a44b7-124">Set the **ServiceName** property to **Microsoft.Practices.ESB.Services.Routing**.</span></span>  
  
19. <span data-ttu-id="a44b7-125">Définir le **SomeValue** propriété **2**.</span><span class="sxs-lookup"><span data-stu-id="a44b7-125">Set the **SomeValue** property to **2**.</span></span>  
  
20. <span data-ttu-id="a44b7-126">Avec le bouton droit le **résolveur** collection de **ItineraryService1**, puis cliquez sur **ajouter le nouveau programme de résolution**.</span><span class="sxs-lookup"><span data-stu-id="a44b7-126">Right-click the **Resolver** collection of **ItineraryService1**, and then click **Add new Resolver**.</span></span>  
  
21. <span data-ttu-id="a44b7-127">Cliquez sur **Resolver1**, puis, dans la fenêtre Propriétés, définissez la **implémentation d’un programme de résolution** propriété **exemple d’Extension du programme de résolution**.</span><span class="sxs-lookup"><span data-stu-id="a44b7-127">Click **Resolver1**, and then in the Properties window, set the **Resolver Implementation** property to **Sample Resolver Extension**.</span></span>  
  
22. <span data-ttu-id="a44b7-128">Définir le **SomeResolverValue** propriété **test**, puis définissez la propriété de version **1.0**.</span><span class="sxs-lookup"><span data-stu-id="a44b7-128">Set the **SomeResolverValue** property to **test**, and then set the version property to **1.0**.</span></span>  
  
23. <span data-ttu-id="a44b7-129">Cliquez sur le **ItineraryService2** élément de modèle et, dans la fenêtre Propriétés, définissez la **d’extension du Service itinéraire** propriété **rampe itinéraire Service Extension**.</span><span class="sxs-lookup"><span data-stu-id="a44b7-129">Click the **ItineraryService2** model element, and then in the Properties window, set the **Itinerary Service Extender** property to **Off-Ramp Itinerary Service Extension**.</span></span>  
  
24. <span data-ttu-id="a44b7-130">Définir le **rampe** propriété **OffRamp1 > gestionnaires d’envoi**.</span><span class="sxs-lookup"><span data-stu-id="a44b7-130">Set the **Off-Ramp** property to **OffRamp1 > Send Handlers**.</span></span>  
  
25. <span data-ttu-id="a44b7-131">Cliquez sur le **OffRamp1** élément de modèle et, dans la fenêtre Propriétés, définissez la **extendeur** propriété **rampe ESB Service Extension**.</span><span class="sxs-lookup"><span data-stu-id="a44b7-131">Click the **OffRamp1** model element, and then in the Properties window, set the **Extender** property to **Off-Ramp ESB Service Extension**.</span></span>  
  
26. <span data-ttu-id="a44b7-132">Définir le **Application BizTalk** propriété **GlobalBank.ESB**.</span><span class="sxs-lookup"><span data-stu-id="a44b7-132">Set the **BizTalk Application** property to **GlobalBank.ESB**.</span></span>  
  
27. <span data-ttu-id="a44b7-133">Définir le **Port d’envoi** propriété **DynamicResolutionOneWay**.</span><span class="sxs-lookup"><span data-stu-id="a44b7-133">Set the **Send Port** property to **DynamicResolutionOneWay**.</span></span>  
  
28. <span data-ttu-id="a44b7-134">Cliquez sur l’aire de conception, puis cliquez sur **exporter le modèle**.</span><span class="sxs-lookup"><span data-stu-id="a44b7-134">Right-click the design surface, and then click **Export Model**.</span></span>  
  
29. <span data-ttu-id="a44b7-135">Examinez le code XML généré.</span><span class="sxs-lookup"><span data-stu-id="a44b7-135">Examine the generated XML.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a44b7-136">Notez le **PropertyBag** élément et les propriétés qu’il contient.</span><span class="sxs-lookup"><span data-stu-id="a44b7-136">Notice the **PropertyBag** element and the properties it contains.</span></span> <span data-ttu-id="a44b7-137">Notez également l’exemple de chaîne de connexion de programme de résolution et la façon dont il a été configuré selon les propriétés d’entrée.</span><span class="sxs-lookup"><span data-stu-id="a44b7-137">Also notice the Sample resolver connection string and how it was configured based on the properties entered.</span></span>