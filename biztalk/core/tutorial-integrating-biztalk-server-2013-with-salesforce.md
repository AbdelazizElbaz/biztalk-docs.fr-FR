---
title: "Didacticiel : Intégration de BizTalk Server 2013 avec Salesforce | Documents Microsoft"
description: "Utiliser Service Bus et BIzTalk Server pour intégrer avec Salesforce"
ms.custom: 
ms.date: 12/07/2015
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 06c9ae51-3f48-4086-883b-ab4d5b6e62e3
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8af013bc97ae9618dc19cab57d52fcb4829f0842
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="tutorial-integrating-biztalk-server-2013-with-salesforce"></a><span data-ttu-id="58ea3-103">Didacticiel : Intégration de BizTalk Server 2013 avec Salesforce</span><span class="sxs-lookup"><span data-stu-id="58ea3-103">Tutorial: Integrating BizTalk Server 2013 with Salesforce</span></span>
<span data-ttu-id="58ea3-104">Relecteurs : [Nick Hauenstein](http://social.msdn.microsoft.com/profile/nick.hauenstein/), [Steef Jan Wiggers](http://social.msdn.microsoft.com/profile/steef-jan%20wiggers)</span><span class="sxs-lookup"><span data-stu-id="58ea3-104">Reviewers: [Nick Hauenstein](http://social.msdn.microsoft.com/profile/nick.hauenstein/), [Steef-Jan Wiggers](http://social.msdn.microsoft.com/profile/steef-jan%20wiggers)</span></span>  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="58ea3-105">introduit quelques nouveaux adaptateurs qui créent beaucoup de scénarios hybrides, impliquant des locaux et des technologies Azure désormais possibles.</span><span class="sxs-lookup"><span data-stu-id="58ea3-105"> introduces some new adapters that make a lot of hybrid scenarios, involving on-premises and Azure technologies now possible.</span></span> <span data-ttu-id="58ea3-106">Dans ce didacticiel, nous verrons comment intégrer une entité purement cloud comme Salesforce avec un serveur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sur site à l'aide de certains de ces nouveaux adaptateurs et [!INCLUDE[winazure](../includes/winazure-md.md)].</span><span class="sxs-lookup"><span data-stu-id="58ea3-106">In this tutorial, we see how to integrate a purely cloud entity like Salesforce integrate with an on-premises [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] using some of the new adapters and [!INCLUDE[winazure](../includes/winazure-md.md)].</span></span> <span data-ttu-id="58ea3-107">Avant de commencer, essayons de comprendre l'objectif métier que nous essayons de réaliser en intégrant [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] avec Salesforce.</span><span class="sxs-lookup"><span data-stu-id="58ea3-107">Before we start, let’s understand the business objective we try to achieve by integrating [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] with Salesforce.</span></span>  
  
 <span data-ttu-id="58ea3-108">Nous pourrions également créer des solutions hybrides impliquant [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et Salesforce avec la version précédente de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], mais la solution serait beaucoup plus complexe puisqu'elle impliquerait une interaction avec Salesforce en consommant un service Web (SOAP).</span><span class="sxs-lookup"><span data-stu-id="58ea3-108">We could also create hybrid solutions involving [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and Salesforce with previous version of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], however the solution would be much more complex involving interaction with Salesforce by consuming a Web service (SOAP).</span></span> <span data-ttu-id="58ea3-109">Avec [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et les nouveaux adaptateurs, la solution est beaucoup plus simple.</span><span class="sxs-lookup"><span data-stu-id="58ea3-109">With [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and the new adapters, the solution is that much easier.</span></span>  
  
## <a name="business-scenario"></a><span data-ttu-id="58ea3-110">Scénario d'entreprise</span><span class="sxs-lookup"><span data-stu-id="58ea3-110">Business Scenario</span></span>  
 <span data-ttu-id="58ea3-111">Northwind utilise le système CRM en ligne de Salesforce comme solution pour effectuer le suivi des clients dans le pipeline des ventes.</span><span class="sxs-lookup"><span data-stu-id="58ea3-111">Northwind uses the Salesforce online CRM system as their solution for tracking customers through the sales pipeline.</span></span> <span data-ttu-id="58ea3-112">Chaque fois qu'une opportunité de vente est créée dans le système Salesforce, Northwind veut que ses systèmes sur site, comme [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], en reçoivent notification de façon que les systèmes en aval puissent collecter les données et lancer d'autres processus pertinents.</span><span class="sxs-lookup"><span data-stu-id="58ea3-112">Every time a sales opportunity is created in the Salesforce system, Northwind wants its on-premise systems, such as [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], to be notified so that other down-stream systems can pick up that data and start other relevant processes.</span></span> <span data-ttu-id="58ea3-113">Northwind prévoit d'implémenter cette solution en utilisant les nouveaux adaptateurs disponibles avec [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et également en y intégrant quelques composants de [!INCLUDE[winazure](../includes/winazure-md.md)].</span><span class="sxs-lookup"><span data-stu-id="58ea3-113">Northwind plans to implement this solution using the new adapters available with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and also by including some components of [!INCLUDE[winazure](../includes/winazure-md.md)].</span></span> <span data-ttu-id="58ea3-114">Voici à quoi s'apparente le flux de données de bout en bout pour la solution :</span><span class="sxs-lookup"><span data-stu-id="58ea3-114">This is how the end-to-end data flow looks like for the solution:</span></span>  
  
-   <span data-ttu-id="58ea3-115">Un commercial crée une « opportunité » dans le système Salesforce.</span><span class="sxs-lookup"><span data-stu-id="58ea3-115">A sales representative creates an “opportunity” in the Salesforce system.</span></span>  
  
-   <span data-ttu-id="58ea3-116">Lorsque le statut de l'opportunité est défini sur « Fermées/gagnées », une notification est envoyée à un point de terminaison de relais hébergé sur [!INCLUDE[winazure](../includes/winazure-md.md)].</span><span class="sxs-lookup"><span data-stu-id="58ea3-116">When the status of the opportunity is set to “Closed Won”, a notification is sent to a relay endpoint hosted on [!INCLUDE[winazure](../includes/winazure-md.md)].</span></span>  
  
-   <span data-ttu-id="58ea3-117">En utilisant le nouvel adaptateur WCF-BasicHttpRelay, les informations de notification sont transmises au système [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] hébergé sur site.</span><span class="sxs-lookup"><span data-stu-id="58ea3-117">Using the new WCF-BasicHttpRelay adapter, the notification information is passed on to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] system housed on-premise.</span></span>  
  
-   <span data-ttu-id="58ea3-118">En reprenant les informations reçues dans le cadre de la notification, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] appelle un point de terminaison REST dans Salesforce, en utilisant le nouvel adaptateur WCF-WebHttp, pour obtenir plus d'informations sur l'opportunité.</span><span class="sxs-lookup"><span data-stu-id="58ea3-118">Using the information received as part of the notification, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] invokes a REST endpoint in Salesforce, using the new WCF-WebHttp adapter, to get more information about the opportunity.</span></span>  
  
-   <span data-ttu-id="58ea3-119">Enfin, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] utilise les informations reçues de Salesforce pour créer une entrée de bon de commande dans une table de base de données SQL Server interne.</span><span class="sxs-lookup"><span data-stu-id="58ea3-119">Finally, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] uses the information received from Salesforce to create a purchase order entry in an in-house SQL Server database table.</span></span>  
  
 <span data-ttu-id="58ea3-120">Ce sont là toutes les étapes que vous devez effectuer pour atteindre l'objectif d'intégration décrit dans cette solution.</span><span class="sxs-lookup"><span data-stu-id="58ea3-120">These are the set of steps that you must perform to achieve the integration objective outlined in this solution.</span></span> <span data-ttu-id="58ea3-121">Chacune de ces étapes implique un large éventail d'activités que nous allons passer en revue au fur et à mesure que nous progressons dans la création de la solution.</span><span class="sxs-lookup"><span data-stu-id="58ea3-121">Each of these steps involves broad set of activities that we’ll look at as we proceed with creating the solution.</span></span>  
  
 <span data-ttu-id="58ea3-122">Voici une illustration qui décrit la solution d'intégration de bout en bout :</span><span class="sxs-lookup"><span data-stu-id="58ea3-122">Here’s an illustration that describes the end-to-end integration solution:</span></span>  
  
 <span data-ttu-id="58ea3-123">![Scénario d’intégration de BizTalk Server et de Salesforce](../core/media/bts-sf-scenario.gif "BTS_SF_Scenario")</span><span class="sxs-lookup"><span data-stu-id="58ea3-123">![BizTalk Server and Salesforce integration scenario](../core/media/bts-sf-scenario.gif "BTS_SF_Scenario")</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="58ea3-124">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="58ea3-124">Prerequisites</span></span>  
 <span data-ttu-id="58ea3-125">Les logiciels suivants doivent être installés sur l'ordinateur sur lequel vous installez cette solution :</span><span class="sxs-lookup"><span data-stu-id="58ea3-125">You must have the following software installed on the computer where you set up this solution:</span></span>  
  
-   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]  
  
-   [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]  
  
-   [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]  
  
-   [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]  
  
 <span data-ttu-id="58ea3-126">Vous devez avoir les abonnements aux services suivants :</span><span class="sxs-lookup"><span data-stu-id="58ea3-126">You must have the following service subscriptions:</span></span>  
  
-   <span data-ttu-id="58ea3-127">Un abonnement [!INCLUDE[winazure](../includes/winazure-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58ea3-127">A [!INCLUDE[winazure](../includes/winazure-md.md)] subscription</span></span>  
  
-   <span data-ttu-id="58ea3-128">Un compte Salesforce Developer Edition</span><span class="sxs-lookup"><span data-stu-id="58ea3-128">Salesforce Developer Edition account</span></span>  
  
## <a name="more-resources"></a><span data-ttu-id="58ea3-129">Plus de ressources</span><span class="sxs-lookup"><span data-stu-id="58ea3-129">More Resources</span></span>  
 <span data-ttu-id="58ea3-130">En plus de ce didacticiel, vous pouvez également consulter les ressources suivantes pour en savoir plus sur l’intégration [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] avec Salesforce en utilisant les nouveaux adaptateurs introduites dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="58ea3-130">In addition to this tutorial, you can also look at the following resources to understand more about integrating [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] with Salesforce using the new adapters introduced in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="58ea3-131">Une démonstration de laboratoire virtuel [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et intégration de Salesforce est disponible à l’adresse [http://go.microsoft.com/fwlink/?LinkId=290930](http://go.microsoft.com/fwlink/?LinkId=290930).</span><span class="sxs-lookup"><span data-stu-id="58ea3-131">A virtual lab demonstrating [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and Salesforce integration is available at [http://go.microsoft.com/fwlink/?LinkId=290930](http://go.microsoft.com/fwlink/?LinkId=290930).</span></span>  
  
-   <span data-ttu-id="58ea3-132">Un exemple en fonction de ce didacticiel est disponible pour téléchargement à l’adresse [http://go.microsoft.com/fwlink/?LinkId=290932](http://go.microsoft.com/fwlink/?LinkId=290932).</span><span class="sxs-lookup"><span data-stu-id="58ea3-132">A sample based on this tutorial is available for download at [http://go.microsoft.com/fwlink/?LinkId=290932](http://go.microsoft.com/fwlink/?LinkId=290932).</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="58ea3-133">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="58ea3-133">Next steps</span></span>
  
-   [<span data-ttu-id="58ea3-134">Étape 1 : Créer un Namespace de Bus de Service</span><span class="sxs-lookup"><span data-stu-id="58ea3-134">Step 1: Create a Service Bus Namespace</span></span>](../core/step-1-create-a-service-bus-namespace.md)  
  
-   [<span data-ttu-id="58ea3-135">Étape 2 : Configurer le système Salesforce</span><span class="sxs-lookup"><span data-stu-id="58ea3-135">Step 2: Set up the Salesforce System</span></span>](../core/step-2-set-up-the-salesforce-system.md)  
  
-   [<span data-ttu-id="58ea3-136">Étape 3 : Créer la Solution BizTalk Server dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="58ea3-136">Step 3: Create the BizTalk Server Solution in Visual Studio</span></span>](../core/step-3-create-the-biztalk-server-solution-in-visual-studio.md)  
  
-   [<span data-ttu-id="58ea3-137">Étape 4 : Configurer la Solution BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="58ea3-137">Step 4: Configure the BizTalk Server Solution</span></span>](../core/step-4-configure-the-biztalk-server-solution.md)  
  
-   [<span data-ttu-id="58ea3-138">Étape 5 : Tester la Solution</span><span class="sxs-lookup"><span data-stu-id="58ea3-138">Step 5: Test the Solution</span></span>](../core/step-5-test-the-solution.md)  
  
## <a name="see-also"></a><span data-ttu-id="58ea3-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="58ea3-139">See Also</span></span>  
 [<span data-ttu-id="58ea3-140">Didacticiels de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="58ea3-140">BizTalk Server Tutorials</span></span>](../core/biztalk-server-tutorials.md)