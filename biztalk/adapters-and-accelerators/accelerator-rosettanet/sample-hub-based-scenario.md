---
title: "Exemple de scénario basé sur le concentrateur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- supply chains, examples
- hub-and-spoke systems
- supply chains, hub-and-spoke systems
- examples, supply chains
- trading partners, supply chains
ms.assetid: ee92c24d-a281-4950-a61e-9cb3bd08d291
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b417398786e602379d16d6734a5ed366b9d6f2ec
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="sample-hub-based-scenario"></a><span data-ttu-id="e240c-102">Exemple de scénario basé sur un hub</span><span class="sxs-lookup"><span data-stu-id="e240c-102">Sample Hub-Based Scenario</span></span>
<span data-ttu-id="e240c-103">Dans de nombreux scénarios de chaînes logistiques, les sociétés travaillent avec leurs partenaires commerciaux pour instaurer une connexion RNIF (RosettaNet Implementation Framework).</span><span class="sxs-lookup"><span data-stu-id="e240c-103">In many supply-chain scenarios, a company will work with each of their trading partners to institute a RosettaNet Implementation Framework (RNIF) connection.</span></span> <span data-ttu-id="e240c-104">Il s'agit d'un moyen efficace pour normaliser les communications tout au long de la chaîne logistique.</span><span class="sxs-lookup"><span data-stu-id="e240c-104">This is an effective way to standardize communications throughout the supply chain.</span></span> <span data-ttu-id="e240c-105">Ce scénario est décrit dans [exemple fournir un scénario de chaîne](../../adapters-and-accelerators/accelerator-rosettanet/sample-supply-chain-scenario.md).</span><span class="sxs-lookup"><span data-stu-id="e240c-105">This scenario is described in [Sample Supply Chain Scenario](../../adapters-and-accelerators/accelerator-rosettanet/sample-supply-chain-scenario.md).</span></span>  
  
 <span data-ttu-id="e240c-106">Il existe une autre façon d'automatiser les transactions dans la chaîne logistique : la société demande à une autre société de configurer et gérer le système intégré.</span><span class="sxs-lookup"><span data-stu-id="e240c-106">Another way to automate transactions throughout the supply chain is for the company to contract with another company to set up and manage the integrated system.</span></span> <span data-ttu-id="e240c-107">Il s'agit d'un scénario basé sur un hub.</span><span class="sxs-lookup"><span data-stu-id="e240c-107">This is a hub-based scenario.</span></span>  
  
## <a name="how-a-hub-based-system-works"></a><span data-ttu-id="e240c-108">Fonctionnement d'un système basé sur un hub</span><span class="sxs-lookup"><span data-stu-id="e240c-108">How a Hub-Based System Works</span></span>  
 <span data-ttu-id="e240c-109">Dans un système basé sur un hub, la société commanditaire qui sous-traite un système intégré se connecte à la société hub à l'aide d'une connexion RNIF.</span><span class="sxs-lookup"><span data-stu-id="e240c-109">In a hub-based system, the company contracting for an integrated system connects to the hub company using an RNIF connection.</span></span> <span data-ttu-id="e240c-110">Le hub se connecte ensuite à tous les partenaires commerciaux de la société via n'importe quel type de connexion électronique demandé.</span><span class="sxs-lookup"><span data-stu-id="e240c-110">The hub then connects to all the company's trading partners using whatever type of electronic connection is required.</span></span> <span data-ttu-id="e240c-111">La société hub fournit à tous les partenaires commerciaux les options de connexion suivantes : connexions RNIF, EDI, fichiers plats, applications web ou connexions propriétaires non compatibles.</span><span class="sxs-lookup"><span data-stu-id="e240c-111">The hub company provides all the trading partners with connection options: RNIF connections, EDI, flat file, Web applications, or non-compliant, proprietary connections.</span></span> <span data-ttu-id="e240c-112">La gestion du système de communications est l'affaire de la société hub.</span><span class="sxs-lookup"><span data-stu-id="e240c-112">Managing the communications system is the hub company's business.</span></span> <span data-ttu-id="e240c-113">La figure suivante illustre le fonctionnement de ce système.</span><span class="sxs-lookup"><span data-stu-id="e240c-113">The following figure shows how such a system might work.</span></span>  
  
 <span data-ttu-id="e240c-114">![&#60; Aucune modification &#62; ] (../../adapters-and-accelerators/accelerator-rosettanet/media/hub-based-scenario.gif "Hub_Based_Scenario")</span><span class="sxs-lookup"><span data-stu-id="e240c-114">![&#60;No Change&#62;](../../adapters-and-accelerators/accelerator-rosettanet/media/hub-based-scenario.gif "Hub_Based_Scenario")</span></span>  
  
 <span data-ttu-id="e240c-115">Un système basé sur un hub présente de nombreux avantages :</span><span class="sxs-lookup"><span data-stu-id="e240c-115">A hub-based system has many advantages:</span></span>  
  
-   <span data-ttu-id="e240c-116">La société commanditaire n'a pas à gérer la complexité de la chaîne logistique, car la société hub s'en charge.</span><span class="sxs-lookup"><span data-stu-id="e240c-116">The contracting company does not have to deal with the complexity of the supply chain; the hub company handles it.</span></span>  
  
-   <span data-ttu-id="e240c-117">La société commanditaire n'a pas à gérer ou mettre à niveau le système. Elle n'est pas responsable des temps d'arrêt. La société hub est responsable de la maintenance du système et des temps d'arrêt.</span><span class="sxs-lookup"><span data-stu-id="e240c-117">The contracting company does not have to maintain or upgrade the system, and it is not responsible for downtime; the hub company is responsible for system maintenance and downtime.</span></span>  
  
-   <span data-ttu-id="e240c-118">La société commanditaire tire parti des avantages d'un système compatible avec RosettaNet, notamment en matière de normalisation, d'automatisation, de réductions des coûts et de visibilité.</span><span class="sxs-lookup"><span data-stu-id="e240c-118">The contracting company gains the advantages of a RosettaNet-compliant system, including standardization, automation, cost savings, and visibility.</span></span>  
  
-   <span data-ttu-id="e240c-119">La société commanditaire a entièrement automatisé sa chaîne logistique avec une variété de connexions électroniques qui permettent à l'ensemble des partenaires commerciaux de disposer de plusieurs choix de connexions.</span><span class="sxs-lookup"><span data-stu-id="e240c-119">The contracting company has fully automated their supply chain with a variety of electronic connections that give the full array of trading partners a choice of connections.</span></span> <span data-ttu-id="e240c-120">La société commanditaire n'a pas à gérer l'expertise technologique liée à la diversité des options de connexion.</span><span class="sxs-lookup"><span data-stu-id="e240c-120">The contracting company does not have to maintain technological expertise in a variety of connection options.</span></span>  
  
-   <span data-ttu-id="e240c-121">Un partenaire commercial peut continuer à utiliser une connexion propriétaire, du moment que la société hub la prend en charge.</span><span class="sxs-lookup"><span data-stu-id="e240c-121">A trading partner can continue to use a proprietary connection, as long as the hub company supports it.</span></span>  
  
-   <span data-ttu-id="e240c-122">Le système est flexible.</span><span class="sxs-lookup"><span data-stu-id="e240c-122">The system is flexible.</span></span> <span data-ttu-id="e240c-123">Les partenaires commerciaux n'ont pas à adopter un système compatible avec RosettaNet.</span><span class="sxs-lookup"><span data-stu-id="e240c-123">Trading partners do not have to adopt a RosettaNet-compliant system.</span></span> <span data-ttu-id="e240c-124">Toutefois, s'ils le font, ils pourront tirer parti des avantages d'un tel système.</span><span class="sxs-lookup"><span data-stu-id="e240c-124">However, if they do so, they will gain the benefits from such a system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e240c-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e240c-125">See Also</span></span>  
 <span data-ttu-id="e240c-126">[Comment BizTalk Server résout les besoins de l’entreprise](../../adapters-and-accelerators/accelerator-rosettanet/how-biztalk-server-solves-the-business-need1.md) </span><span class="sxs-lookup"><span data-stu-id="e240c-126">[How BizTalk Server Solves the Business Need](../../adapters-and-accelerators/accelerator-rosettanet/how-biztalk-server-solves-the-business-need1.md) </span></span>  
 <span data-ttu-id="e240c-127">[La nécessité d’intégration de partenaires commerciaux](../../adapters-and-accelerators/accelerator-rosettanet/the-need-for-trading-partner-integration.md) </span><span class="sxs-lookup"><span data-stu-id="e240c-127">[The Need for Trading Partner Integration](../../adapters-and-accelerators/accelerator-rosettanet/the-need-for-trading-partner-integration.md) </span></span>  
 <span data-ttu-id="e240c-128">[Le défi de chaîne d’approvisionnement](../../adapters-and-accelerators/accelerator-rosettanet/the-supply-chain-challenge.md) </span><span class="sxs-lookup"><span data-stu-id="e240c-128">[The Supply Chain Challenge](../../adapters-and-accelerators/accelerator-rosettanet/the-supply-chain-challenge.md) </span></span>  
 <span data-ttu-id="e240c-129">[La Solution de chaîne d’approvisionnement](../../adapters-and-accelerators/accelerator-rosettanet/the-supply-chain-solution.md) </span><span class="sxs-lookup"><span data-stu-id="e240c-129">[The Supply Chain Solution](../../adapters-and-accelerators/accelerator-rosettanet/the-supply-chain-solution.md) </span></span>  
 [<span data-ttu-id="e240c-130">Exemple de scénario de chaîne logistique</span><span class="sxs-lookup"><span data-stu-id="e240c-130">Sample Supply Chain Scenario</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/sample-supply-chain-scenario.md)