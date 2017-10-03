---
title: "Contrôler le flux de l’adaptateur BizTalk pour JD Edwards OneWorld | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- connection pooling
- control flows
- apartment threading
- apartment threading, business functions
ms.assetid: 1ec865d0-2257-453b-9230-1f3787ebac38
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0fc5a8be6516b61c4049242952967ce939513e9c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="control-flow-in-biztalk-adapter-for-jd-edwards-oneworld"></a><span data-ttu-id="902d2-102">Flux de contrôle dans l'adaptateur BizTalk pour JD Edwards OneWorld</span><span class="sxs-lookup"><span data-stu-id="902d2-102">Control Flow in BizTalk Adapter for JD Edwards OneWorld</span></span>
<span data-ttu-id="902d2-103">Cette rubrique décrit les flux de contrôle de la conception et de l'exécution dans l'adaptateur BizTalk pour JD Edwards OneWorld.</span><span class="sxs-lookup"><span data-stu-id="902d2-103">This topic discusses the design time and run-time control flows in Microsoft BizTalk Adapter for JD Edwards OneWorld.</span></span>  
  
## <a name="design-time-flow"></a><span data-ttu-id="902d2-104">Flux de conception</span><span class="sxs-lookup"><span data-stu-id="902d2-104">Design-Time Flow</span></span>  
 <span data-ttu-id="902d2-105">À l'ouverture de l'adaptateur (à l'aide des informations d'identification et des informations système à partir de la boîte de dialogue Propriétés du transport), une ou plusieurs instances de la fonction d'entreprise de l'application JD Edwards OneWorld sont créées et regroupées.</span><span class="sxs-lookup"><span data-stu-id="902d2-105">When the adapter opens (using the credentials and system information from the Transport Properties dialog box), one or more instances of the JD Edwards OneWorld application business function are created and pooled.</span></span> <span data-ttu-id="902d2-106">Lorsque vous accédez à l'espace de noms dans l'Assistant Adaptateur, la liste des fonctions d'entreprise est affichée.</span><span class="sxs-lookup"><span data-stu-id="902d2-106">When you browse the namespace in the Adapter Wizard, a list of business functions appear.</span></span> <span data-ttu-id="902d2-107">Lorsque vous cliquez sur une fonction d'entreprise, les méthodes logiques associées et les signatures de celles-ci sont affichées.</span><span class="sxs-lookup"><span data-stu-id="902d2-107">Clicking a business function displays its logical methods along with the methods signatures.</span></span>  
  
## <a name="run-time-flow"></a><span data-ttu-id="902d2-108">Flux d'exécution</span><span class="sxs-lookup"><span data-stu-id="902d2-108">Run-Time Flow</span></span>  
 <span data-ttu-id="902d2-109">Les instances de la fonction d'entreprise JD Edwards OneWorld sont créées et regroupées pour chaque thread.</span><span class="sxs-lookup"><span data-stu-id="902d2-109">Instances of the JD Edwards OneWorld business function are created and pooled for each thread.</span></span> <span data-ttu-id="902d2-110">Lorsqu'un appel de méthode est envoyé à un service d'entreprise, les métadonnées de la méthode sont lues à l'aide de la fonction d'entreprise de l'application JD Edwards OneWorld. Toutefois, si celles-ci ont déjà été mises en cache, la fonction d'entreprise utilise les informations mises en cache avant d'effectuer un appel vers la méthode appropriée.</span><span class="sxs-lookup"><span data-stu-id="902d2-110">When a method call is submitted to a business service, the metadata for the method is read using the JD Edwards OneWorld application business function; however, if the metadata for the method has already been cached, the business function uses the cached information and then makes a call to the appropriate method.</span></span> <span data-ttu-id="902d2-111">Au moment de l'exécution, une couche d'interface JD Edwards OneWorld est créée dynamiquement.</span><span class="sxs-lookup"><span data-stu-id="902d2-111">At run time, a JD Edwards OneWorld interface layer is dynamically constructed.</span></span> <span data-ttu-id="902d2-112">Celle-ci permet à l'adaptateur BizTalk pour JD Edwards OneWorld de prendre en charge l'appel et la conversion des données.</span><span class="sxs-lookup"><span data-stu-id="902d2-112">It is through the interface layer that BizTalk Adapter for JD Edwards OneWorld supports invocation and data conversions.</span></span>  
  
 <span data-ttu-id="902d2-113">L'adaptateur BizTalk pour JD Edwards OneWorld mappe les descriptions d'interface des signatures de méthode de l'application JD Edwards OneWorld, ce qui permet à BizTalk Server d'interagir avec ces descriptions.</span><span class="sxs-lookup"><span data-stu-id="902d2-113">BizTalk Adapter for JD Edwards OneWorld maps interface descriptions of the method signatures of the JD Edwards OneWorld application, allowing BizTalk Server to interact with these interface descriptions.</span></span>  
  
 <span data-ttu-id="902d2-114">L'adaptateur permet aux applications de l'entreprise d'interagir avec l'application JD Edwards OneWorld en étendant les fonctionnalités de l'application sous la forme d'un ou plusieurs des éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="902d2-114">The adapter enables applications in the enterprise to interact with the JD Edwards OneWorld application by extending functionality from the application in the form of one or more of the following:</span></span>  
  
-   <span data-ttu-id="902d2-115">formats de données natifs ;</span><span class="sxs-lookup"><span data-stu-id="902d2-115">Native data formats</span></span>  
  
-   <span data-ttu-id="902d2-116">Procédures</span><span class="sxs-lookup"><span data-stu-id="902d2-116">Procedures</span></span>  
  
-   <span data-ttu-id="902d2-117">Méthodes</span><span class="sxs-lookup"><span data-stu-id="902d2-117">Methods</span></span>  
  
-   <span data-ttu-id="902d2-118">Messages</span><span class="sxs-lookup"><span data-stu-id="902d2-118">Messages</span></span>  
  
-   <span data-ttu-id="902d2-119">Propriétés</span><span class="sxs-lookup"><span data-stu-id="902d2-119">Properties</span></span>  
  
-   <span data-ttu-id="902d2-120">interfaces d'application.</span><span class="sxs-lookup"><span data-stu-id="902d2-120">Application interfaces</span></span>  
  
 <span data-ttu-id="902d2-121">Au moment de l'exécution, l'adaptateur BizTalk pour JD Edwards OneWorld génère une description des interfaces de l'application pour les applications clientes qui interagissent avec JD Edwards OneWorld.</span><span class="sxs-lookup"><span data-stu-id="902d2-121">At run time, BizTalk Adapter for JD Edwards OneWorld builds a description of application interfaces for client applications that interact with JD Edwards OneWorld.</span></span> <span data-ttu-id="902d2-122">L'adaptateur peut créer, supprimer et appeler des objets d'entreprise (le cas échéant) pour effectuer des calculs dans l'application et appeler directement des méthodes.</span><span class="sxs-lookup"><span data-stu-id="902d2-122">The adapter can create, delete, and invoke business objects as needed, to perform computations in the application and directly invoke methods.</span></span> <span data-ttu-id="902d2-123">Tous les appels vers JD Edwards OneWorld sont synchrones.</span><span class="sxs-lookup"><span data-stu-id="902d2-123">All calls into JD Edwards OneWorld are synchronous calls.</span></span> <span data-ttu-id="902d2-124">L'adaptateur reçoit les messages XML de BizTalk Server, les place dans une enveloppe SOAP et transforme les données de l'appel de messages SOAP en types Java.</span><span class="sxs-lookup"><span data-stu-id="902d2-124">The adapter receives the XML messages from BizTalk Server, encloses the messages in a SOAP envelope, and transforms the data for the call from SOAP messages into Java types.</span></span>  
  
 <span data-ttu-id="902d2-125">Le processus de réponse est similaire :</span><span class="sxs-lookup"><span data-stu-id="902d2-125">The reply is sent back following a similar process:</span></span>  
  
1.  <span data-ttu-id="902d2-126">Les types Java sont transformés en messages SOAP.</span><span class="sxs-lookup"><span data-stu-id="902d2-126">The Java types are transformed into SOAP messages.</span></span>  
  
2.  <span data-ttu-id="902d2-127">Les messages SOAP sont convertis en messages XML.</span><span class="sxs-lookup"><span data-stu-id="902d2-127">The SOAP messages are converted into XML messages.</span></span>  
  
3.  <span data-ttu-id="902d2-128">Les messages XML sont soumis à BizTalk Server pour traitement.</span><span class="sxs-lookup"><span data-stu-id="902d2-128">The XML messages are submitted to BizTalk Server for further processing.</span></span>  
  
### <a name="apartment-threading-of-business-functions"></a><span data-ttu-id="902d2-129">Thread cloisonné des fonctions d'entreprise</span><span class="sxs-lookup"><span data-stu-id="902d2-129">Apartment Threading of Business Functions</span></span>  
 <span data-ttu-id="902d2-130">Une fonction d'entreprise JD Edwards OneWorld et une instance ne peuvent être utilisées que sur le thread où elles ont été créées ou obtenues.</span><span class="sxs-lookup"><span data-stu-id="902d2-130">A JD Edwards OneWorld business function, and any instance, can only be used on the thread where it is created or obtained.</span></span> <span data-ttu-id="902d2-131">Il s’agit en tant que *de thread apartment*.</span><span class="sxs-lookup"><span data-stu-id="902d2-131">This is known as *apartment threading*.</span></span> <span data-ttu-id="902d2-132">L'infrastructure de regroupement de connexions de l'adaptateur BizTalk pour JD Edwards OneWorld gère un pool de connexions disponibles.</span><span class="sxs-lookup"><span data-stu-id="902d2-132">The connection pooling framework of BizTalk Adapter for JD Edwards OneWorld manages a pool of available connections.</span></span>  
  
### <a name="connection-pooling"></a><span data-ttu-id="902d2-133">Regroupement de connexions</span><span class="sxs-lookup"><span data-stu-id="902d2-133">Connection Pooling</span></span>  
 <span data-ttu-id="902d2-134">Le regroupement de connexions améliore les performances des appels en gardant ouvertes les connexions aux systèmes serveur et en réutilisant celles-ci au lieu de les fermer après chaque appel.</span><span class="sxs-lookup"><span data-stu-id="902d2-134">Connection pooling improves the performance of calls by keeping connections to the server systems open and reusing them instead of closing them after each call.</span></span> <span data-ttu-id="902d2-135">L'adaptateur BizTalk pour JD Edwards OneWorld permet de regrouper les connexions au sein d'ID de connexion spécifiques, tout en continuant à contrôler le nombre total de connexions parmi les différents pools.</span><span class="sxs-lookup"><span data-stu-id="902d2-135">BizTalk Adapter for JD Edwards OneWorld enables you to pool connections within particular logon IDs, but still maintains critical control of the total number of connections across all pools.</span></span>  
  
 <span data-ttu-id="902d2-136">Chaque nouvelle instance de fonction d'entreprise utilise le thread sur lequel elle a été créée, et elle est détruite après chaque opération.</span><span class="sxs-lookup"><span data-stu-id="902d2-136">Any new business function instance uses the thread on which it is created, and the instance is destroyed after each operation.</span></span> <span data-ttu-id="902d2-137">Tous les appels JD Edwards OneWorld vers les fonctions d'entreprise sont sans état ; cependant, durant l'opération, l'adaptateur vérifie que la fonction d'entreprise est utilisée sur le thread approprié.</span><span class="sxs-lookup"><span data-stu-id="902d2-137">All JD Edwards OneWorld calls to business functions are stateless; however, during the operation, the adapter ensures that the business function is used on the correct thread.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="902d2-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="902d2-138">See Also</span></span>  
 <span data-ttu-id="902d2-139">[Développement d’Applications](../core/developing-applications3.md) </span><span class="sxs-lookup"><span data-stu-id="902d2-139">[Developing Applications](../core/developing-applications3.md) </span></span>  
 [<span data-ttu-id="902d2-140">Planification et Architecture</span><span class="sxs-lookup"><span data-stu-id="902d2-140">Planning and Architecture</span></span>](../core/planning-and-architecture17.md)