---
title: Compteurs de Performance des adaptateurs WCF | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- performance, WCF adapters
- performance, performance counters
- WCF adapters, performance
ms.assetid: 9feb052f-5674-419f-84ab-9b5d312a04a5
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 236eaed7401c79540274e0419b99d14d0f128332
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="wcf-adapters-performance-counters"></a><span data-ttu-id="b2786-102">Compteurs de performance des adaptateurs WCF</span><span class="sxs-lookup"><span data-stu-id="b2786-102">WCF Adapters Performance Counters</span></span>
<span data-ttu-id="b2786-103">Les compteurs de performance permettent d’analyser des aspects spécifiques du travail effectué sur un système de site ou par un service.</span><span class="sxs-lookup"><span data-stu-id="b2786-103">Performance counters enable you to monitor specific aspects of work performed on the site or system by a service.</span></span> <span data-ttu-id="b2786-104">Ils peuvent vous aider à identifier et à résoudre des problèmes de performances de serveur.</span><span class="sxs-lookup"><span data-stu-id="b2786-104">Performance counters can help you identify and troubleshoot server performance issues.</span></span> <span data-ttu-id="b2786-105">Les adaptateurs WCF ne possèdent pas leurs propres compteurs de performance.</span><span class="sxs-lookup"><span data-stu-id="b2786-105">The WCF adapters do not provide their own performance counters.</span></span> <span data-ttu-id="b2786-106">Vous pouvez toutefois surveiller les compteurs de performance de Windows Communication Foundation (WCF) pour évaluer les performances des emplacements de réception WCF.</span><span class="sxs-lookup"><span data-stu-id="b2786-106">However, you can monitor the performance counters of Windows Communication Foundation (WCF) to gauge the performance of the WCF receive locations.</span></span> <span data-ttu-id="b2786-107">Avant d'utiliser les compteurs de performance WCF pour les emplacements de réception WCF, vous devez les activer pour les instances d'hôte qui exécutent ces derniers.</span><span class="sxs-lookup"><span data-stu-id="b2786-107">To use the WCF performance counters for the WCF receive locations, you have to enable the performance counters for the host instances running the receive locations.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b2786-108">Les compteurs de performance WCF ne sont pas disponibles pour les ports d'envoi WCF.</span><span class="sxs-lookup"><span data-stu-id="b2786-108">The WCF performance counters are not available for WCF send ports.</span></span>  
  
 <span data-ttu-id="b2786-109">Pour les adaptateurs WCF In-process, vous pouvez activer les compteurs de performance via le fichier BTSNTSvc.exe.config.</span><span class="sxs-lookup"><span data-stu-id="b2786-109">For the in-process WCF adapters, you can enable the performance counters through the BTSNTSvc.exe.config file.</span></span> <span data-ttu-id="b2786-110">Pour les adaptateurs WCF isolés, vous pouvez modifier le fichier Web.config pour activer les compteurs de performance.</span><span class="sxs-lookup"><span data-stu-id="b2786-110">For the isolated WCF adapters, you can modify the Web.config file to enable the performance counters.</span></span> <span data-ttu-id="b2786-111">Pour plus d’informations sur les compteurs de performance WCF, consultez « Compteurs de Performance WCF » à [http://go.microsoft.com/fwlink/?LinkID=87245](http://go.microsoft.com/fwlink/?LinkID=87245).</span><span class="sxs-lookup"><span data-stu-id="b2786-111">For more information about the WCF performance counters, see "WCF Performance Counters" at [http://go.microsoft.com/fwlink/?LinkID=87245](http://go.microsoft.com/fwlink/?LinkID=87245).</span></span>  
  
## <a name="enabling-the-wcf-performance-counters-for-the-wcf-receive-locations"></a><span data-ttu-id="b2786-112">Activation des compteurs de performance WCF pour les emplacements de réception WCF</span><span class="sxs-lookup"><span data-stu-id="b2786-112">Enabling the WCF Performance Counters for the WCF Receive Locations</span></span>  
 <span data-ttu-id="b2786-113">Pour les adaptateurs WCF In-process, vous pouvez activer les compteurs de performance via le fichier BTSNTSvc.exe.config.</span><span class="sxs-lookup"><span data-stu-id="b2786-113">For the in-process WCF adapters, you can enable the performance counters through the BTSNTSvc.exe.config file.</span></span>  
  
 <span data-ttu-id="b2786-114">Pour les adaptateurs WCF isolés, vous pouvez activer le suivi WCF en modifiant le fichier Web.config que l'Assistant Publication de services WCF BizTalk crée dans le dossier de l'application Web</span><span class="sxs-lookup"><span data-stu-id="b2786-114">For the isolated WCF adapters, you can enable WCF tracing by modifying the Web.config file that the BizTalk WCF Service Publishing Wizard creates in the Web application folder</span></span>  
  
 <span data-ttu-id="b2786-115">Pour modifier le fichier de configuration BTSNtSvc.exe.config ou Web.config, ouvrez-le, puis configurez le suivi WCF, comme décrit dans l'exemple de configuration suivant :</span><span class="sxs-lookup"><span data-stu-id="b2786-115">To modify BTSNtSvc.exe.config or Web.config, open the configuration file, and then configure WCF tracing, as indicated in the following configuration example:</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b2786-116">Le fichier BTSNTSvc.exe.config est toujours situé dans le même répertoire que le fichier BTSNTSvc.exe (généralement, [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b2786-116">The BTSNTSvc.exe.config file is always located in the same directory as the BTSNTSvc.exe file, which is usually [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)].</span></span>  
  
```  
<configuration>  
 <system.serviceModel>  
 <diagnostics performanceCounters="All" />  
 </system.serviceModel>  
 </configuration>  
```  
  
 <span data-ttu-id="b2786-117">Le **performanceCounters** attribut peut être défini pour activer un type spécifique de compteurs de performance.</span><span class="sxs-lookup"><span data-stu-id="b2786-117">The **performanceCounters** attribute can be set to enable a specific type of performance counters.</span></span> <span data-ttu-id="b2786-118">Les valeurs valides sont :</span><span class="sxs-lookup"><span data-stu-id="b2786-118">Valid values are</span></span>  
  
-   <span data-ttu-id="b2786-119">**Tous les**: tous les compteurs de catégorie (**ServiceModelService**, **ServiceModelEndpoint**, et **ServiceModelOperation**) sont activés.</span><span class="sxs-lookup"><span data-stu-id="b2786-119">**All**: All category counters (**ServiceModelService**, **ServiceModelEndpoint**, and **ServiceModelOperation**) are enabled.</span></span>  
  
-   <span data-ttu-id="b2786-120">**ServiceOnly**: uniquement **ServiceModelService** compteurs de catégorie sont activés.</span><span class="sxs-lookup"><span data-stu-id="b2786-120">**ServiceOnly**: Only **ServiceModelService** category counters are enabled.</span></span>  
  
-   <span data-ttu-id="b2786-121">**Désactiver**: les compteurs de performance ServiceModel * sont désactivés.</span><span class="sxs-lookup"><span data-stu-id="b2786-121">**Off**: ServiceModel* performance counters are disabled.</span></span> <span data-ttu-id="b2786-122">Ceci est la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="b2786-122">This is the default value.</span></span>  
  
 <span data-ttu-id="b2786-123">Une fois le fichier BTSNTSvc.exe.config modifié, vous devez redémarrer les instances d'hôte exécutant les emplacements de réception WCF In-process.</span><span class="sxs-lookup"><span data-stu-id="b2786-123">After modifying the BTSNTSvc.exe.config file, you must restart the host instances running the in-process WCF receive locations.</span></span>  
  
## <a name="types-of-performance-counters"></a><span data-ttu-id="b2786-124">Types de compteurs de performance</span><span class="sxs-lookup"><span data-stu-id="b2786-124">Types of Performance Counters</span></span>  
 <span data-ttu-id="b2786-125">Compteurs de performance WCF sont limités à trois niveaux différents : service, point de terminaison et opération.</span><span class="sxs-lookup"><span data-stu-id="b2786-125">WCF performance counters are scoped to three different levels: service, endpoint, and operation.</span></span>  
  
 <span data-ttu-id="b2786-126">**Compteurs de performance de service**</span><span class="sxs-lookup"><span data-stu-id="b2786-126">**Service performance counters**</span></span>  
  
 <span data-ttu-id="b2786-127">Les compteurs de performance de service mesurent le comportement de l'intégralité du service et permettent de diagnostiquer les performances de celui-ci.</span><span class="sxs-lookup"><span data-stu-id="b2786-127">Service performance counters measure the service behavior as a whole and can be used to diagnose the performance of the whole service.</span></span> <span data-ttu-id="b2786-128">Ils sont trouvent sous le **ServiceModelService 3.0.0.0** objet de performance lors de l’affichage avec l’Analyseur de performances.</span><span class="sxs-lookup"><span data-stu-id="b2786-128">They are found under the **ServiceModelService 3.0.0.0** performance object when viewing with Performance Monitor.</span></span> <span data-ttu-id="b2786-129">Les instances sont nommées selon le modèle suivant :</span><span class="sxs-lookup"><span data-stu-id="b2786-129">The instances are named using the following pattern:</span></span>  
  
```  
biztalkserviceinstance@<URI of a receive location>  
```  
  
 <span data-ttu-id="b2786-130">Comme les adaptateurs WCF créent un hôte de service distinct pour chaque emplacement de réception, une instance de compteur de performance est créée pour chaque emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="b2786-130">Because the WCF adapters create a separate service host for each receive location, a performance counter instance is created for each receive location.</span></span> <span data-ttu-id="b2786-131">Pour plus d’informations sur la classe de service WCF de mise en œuvre des contrats de service, consultez le **classe BizTalkServiceInstance** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span><span class="sxs-lookup"><span data-stu-id="b2786-131">For more information about the service class implementing the WCF service contracts, see the **BizTalkServiceInstance Class** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span> 
  
 <span data-ttu-id="b2786-132">**Compteurs de performance de point de terminaison**</span><span class="sxs-lookup"><span data-stu-id="b2786-132">**Endpoint performance counters**</span></span>  
  
 <span data-ttu-id="b2786-133">Les compteurs de performance de point de terminaison permettent de consulter les données indiquant la manière dont un point de terminaison accepte les messages.</span><span class="sxs-lookup"><span data-stu-id="b2786-133">Endpoint performance counters enable you to look at data reflecting how an endpoint is accepting messages.</span></span> <span data-ttu-id="b2786-134">Ils sont trouvent sous le **ServiceModelEndpoint 3.0.0.0** objet de performance lors de l’affichage avec l’Analyseur de performances.</span><span class="sxs-lookup"><span data-stu-id="b2786-134">They are found under the **ServiceModelEndpoint 3.0.0.0** performance object when viewing with Performance Monitor.</span></span> <span data-ttu-id="b2786-135">Les instances sont nommées selon le modèle suivant :</span><span class="sxs-lookup"><span data-stu-id="b2786-135">The instances are named using the following pattern:</span></span>  
  
```  
biztalkserviceinstance.<WCF service contract>@<URI of a receive location>  
```  
  
 <span data-ttu-id="b2786-136">Une instance de compteur de performance est créée pour chaque emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="b2786-136">A performance counter instance is created for each receive location.</span></span> <span data-ttu-id="b2786-137">Dans le modèle précédent, le nom du contrat de service WCF représente le contrat de service que les adaptateurs WCF choisissent pour recevoir les messages via l'emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="b2786-137">In the preceding pattern, the name of the WCF service contract represents the service contract that the WCF adapters choose to receive messages through the receive location.</span></span> <span data-ttu-id="b2786-138">Pour plus d’informations sur la façon dont les adaptateurs WCF choisissent un contrat de service WCF disponible à partir de contrats de service, consultez **référence de contrat de Service WCF adaptateurs** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span><span class="sxs-lookup"><span data-stu-id="b2786-138">For more information about how the WCF adapters choose a service contract from the available WCF service contracts, see **WCF Adapters Service Contract Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>  
  
 <span data-ttu-id="b2786-139">**Compteurs de performance d’opération**</span><span class="sxs-lookup"><span data-stu-id="b2786-139">**Operation performance counters**</span></span>  
  
 <span data-ttu-id="b2786-140">Compteurs de performance d’opération sont trouvent sous le **ServiceModelOperation 3.0.0.0** objet de performance lors de l’affichage avec l’Analyseur de performances.</span><span class="sxs-lookup"><span data-stu-id="b2786-140">Operation performance counters are found under the **ServiceModelOperation 3.0.0.0** performance object when viewing with Performance Monitor.</span></span> <span data-ttu-id="b2786-141">Deux instances de compteur de performance sont créées pour chaque emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="b2786-141">Two performance counter instances are created for each receive location.</span></span> <span data-ttu-id="b2786-142">L'une des instances d'objet est nommée selon le modèle suivant :</span><span class="sxs-lookup"><span data-stu-id="b2786-142">One of the object instances is named using the following pattern:</span></span>  
  
```  
biztalkserviceinstance.<WCF service contract>biztalksubmit@<URI of a receive location>  
```  
  
 <span data-ttu-id="b2786-143">Dans le modèle précédent, le nom du contrat de service WCF représente le contrat de service que les adaptateurs WCF choisissent pour recevoir les messages via l'emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="b2786-143">In the preceding pattern, the name of the WCF service contract represents the service contract that the WCF adapters choose to receive messages through the receive location.</span></span> <span data-ttu-id="b2786-144">**biztalksubmit** est un nom d’opération déclaré dans le contrat de service et provoque l’exécution de la création d’opérations WSDL dans les métadonnées.</span><span class="sxs-lookup"><span data-stu-id="b2786-144">**biztalksubmit** is an operation name declared in the service contract, and causes the runtime to create WSDL operations in the metadata.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b2786-145">Pour plus d’informations sur la façon dont les adaptateurs WCF choisissent un contrat de service WCF disponible à partir de contrats de service, consultez **référence de contrat de Service WCF adaptateurs** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span><span class="sxs-lookup"><span data-stu-id="b2786-145">For more information about how the WCF adapters choose a service contract from the available WCF service contracts, see **WCF Adapters Service Contract Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
  
 <span data-ttu-id="b2786-146">L'autre instance d'objet est nommée selon le modèle suivant :</span><span class="sxs-lookup"><span data-stu-id="b2786-146">The other object instance is named using the following pattern:</span></span>  
  
```  
biztalkserviceinstance.<WCF service contract><twowaymethod|onewaymethod>@<URI of a receive location>  
```  
  
 <span data-ttu-id="b2786-147">Cette instance de compteur de performance représente l'opération qui traite de manière asynchrone les messages entrant via l'emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="b2786-147">This performance counter instance represents the operation that asynchronously processes messages incoming through the receive location.</span></span> <span data-ttu-id="b2786-148">La partie nom de l’opération de cette instance peut être **twowaymethod** ou **onewaymethod** selon le type d’adaptateur WCF utilisé dans l’emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="b2786-148">The operation name part of this instance can be **twowaymethod** or **onewaymethod** depending on the type of WCF adapter used in the receive location.</span></span> <span data-ttu-id="b2786-149">Si vous utilisez l’adaptateur WCF-NetMsmq, une instance portant le **onewaymethod** nom de l’opération est créé.</span><span class="sxs-lookup"><span data-stu-id="b2786-149">If you use the WCF-NetMsmq adapter, an instance having the **onewaymethod** operation name is created.</span></span> <span data-ttu-id="b2786-150">Pour les autres adaptateurs, **twowaymethod** est utilisé pour la partie nom de l’opération.</span><span class="sxs-lookup"><span data-stu-id="b2786-150">For the other adapters, **twowaymethod** is used for the operation name part.</span></span>