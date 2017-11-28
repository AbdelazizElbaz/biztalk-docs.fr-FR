---
title: "MSCIT : À l’aide de Microsoft Azure BizTalk Services pour les chaînes logistiques | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 22091261-cd17-45b2-8746-dc174b52dcff
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a6a1609be7326db4988d31d51597cde3fd280227
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="mscit-using-microsoft-azure-biztalk-services-for-supply-chain-orders"></a><span data-ttu-id="e6d70-102">MSCIT : À l’aide de Microsoft Azure BizTalk Services pour les chaînes logistiques</span><span class="sxs-lookup"><span data-stu-id="e6d70-102">MSCIT: Using Microsoft Azure BizTalk Services for Supply Chain Orders</span></span>
<span data-ttu-id="e6d70-103">**Appareils Microsoft & Studios : à l’aide de Microsoft Azure BizTalk Services pour les chaînes logistiques**</span><span class="sxs-lookup"><span data-stu-id="e6d70-103">**Microsoft Devices & Studios: Using Microsoft Azure BizTalk Services for Supply Chain Orders**</span></span>  
  
 <span data-ttu-id="e6d70-104">Article de la technique de BizTalk</span><span class="sxs-lookup"><span data-stu-id="e6d70-104">BizTalk Technical Article</span></span>  
  
 <span data-ttu-id="e6d70-105">**Enregistreur :** Anil Kongari (Microsoft), Dipti Sharma (Microsoft), Mandi Ohlinger (Microsoft)</span><span class="sxs-lookup"><span data-stu-id="e6d70-105">**Writer:** Anil Kongari (Microsoft), Dipti Sharma (Microsoft), Mandi Ohlinger (Microsoft)</span></span>  
  
 <span data-ttu-id="e6d70-106">**Réviseurs techniques :** Anil Kongari (Microsoft), Hariharan Sundaram (Microsoft), Dipti Sharma (Microsoft), Heena Parmar (Microsoft)</span><span class="sxs-lookup"><span data-stu-id="e6d70-106">**Technical Reviewers:** Anil Kongari (Microsoft), Hariharan Sundaram (Microsoft), Dipti Sharma (Microsoft), Heena Parmar (Microsoft)</span></span>  
  
 <span data-ttu-id="e6d70-107">**Date de publication :** octobre 2013</span><span class="sxs-lookup"><span data-stu-id="e6d70-107">**Published:** October 2013</span></span>  
  
 <span data-ttu-id="e6d70-108">**S’applique à :** Microsoft Azure BizTalk Services (MABS) et BizTalk Server 2013</span><span class="sxs-lookup"><span data-stu-id="e6d70-108">**Applies To:** Microsoft Azure BizTalk Services (MABS) and BizTalk Server 2013</span></span>  
  
 <span data-ttu-id="e6d70-109">**Résumé :** le groupe de fabrication, chaîne logistique et informations Services (MSCIS) est un groupe de gestion de la chaîne logistique mondiale chez Microsoft.</span><span class="sxs-lookup"><span data-stu-id="e6d70-109">**Summary:** The Manufacturing, Supply Chain, and Information Services (MSCIS) group is a Global Supply Chain Management group at Microsoft.</span></span> <span data-ttu-id="e6d70-110">Chaque année, Microsoft lance des nouveaux produits.</span><span class="sxs-lookup"><span data-stu-id="e6d70-110">Every year, Microsoft launches new products.</span></span> <span data-ttu-id="e6d70-111">MSCIS est responsable de la commercialisation de ces nouveaux produits à.</span><span class="sxs-lookup"><span data-stu-id="e6d70-111">MSCIS is responsible for bringing these new products to market.</span></span> <span data-ttu-id="e6d70-112">Pour prendre en charge de ces produits, les nouveaux partenaires sont ajoutés à la chaîne logistique, y compris le fournisseur, fabricant, distributeur, détaillant, centre de gestion, support et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="e6d70-112">To support these products, new partners are added to the Supply Chain, including Supplier, Manufacturer, Distributor, Retailer, Service Center, Carrier, and so on.</span></span>  
  
 <span data-ttu-id="e6d70-113">Le nombre de transactions avec les partenaires augmente chaque année.</span><span class="sxs-lookup"><span data-stu-id="e6d70-113">The number of partner transactions increases yearly.</span></span> <span data-ttu-id="e6d70-114">Au cours d’une charge élevée, il existe les problèmes liés au débit.</span><span class="sxs-lookup"><span data-stu-id="e6d70-114">During high load, there are issues related to throughput.</span></span> <span data-ttu-id="e6d70-115">Pendant que le concentrateur BizTalk de chaîne fournir traite plus de transactions (volume croissant), le système principal ou le système de partenaire n’est pas en mesure de suivre.</span><span class="sxs-lookup"><span data-stu-id="e6d70-115">While the Supply Chain BizTalk hub processes more transactions (increased volume), the end system or partner system is not able to keep up.</span></span>  
  
 <span data-ttu-id="e6d70-116">Est de la demande en cours de préparation des systèmes business-to-business (B2B) pour les ventes de pointe.</span><span class="sxs-lookup"><span data-stu-id="e6d70-116">The current challenge is to prepare the business-to-business (B2B) systems for peak sales.</span></span> <span data-ttu-id="e6d70-117">Dans le cadre du programme TAP (Technology Adoption), MSCIS envisage plateforme en tant que Service (PaaS) à l’aide de Microsoft Azure BizTalk Services (MABS).</span><span class="sxs-lookup"><span data-stu-id="e6d70-117">As part of Technology Adoption Program (TAP), MSCIS is exploring Platform as a Service (PaaS) using Microsoft Azure BizTalk Services (MABS).</span></span> <span data-ttu-id="e6d70-118">MABS fournit des fonctionnalités clés qui peuvent résoudre la situation de l’échelle.</span><span class="sxs-lookup"><span data-stu-id="e6d70-118">MABS provides key capabilities that can solve the scale situation.</span></span> <span data-ttu-id="e6d70-119">MSCIS créé une preuve de Concept (POC) impliquant une solution hybride qui utilise Microsoft Azure BizTalk Services (MABS) et BizTalk Server 2013.</span><span class="sxs-lookup"><span data-stu-id="e6d70-119">MSCIS created a Proof of Concept (POC) involving a hybrid solution that uses Microsoft Azure BizTalk Services (MABS) and BizTalk Server 2013.</span></span> <span data-ttu-id="e6d70-120">La configuration requise est de fournir des vous procéderez à partir de bout en bout, y compris la possibilité de monter en puissance pour les ventes de pointe et l’échelle vers le bas pour les ventes normales.</span><span class="sxs-lookup"><span data-stu-id="e6d70-120">The requirement is to provide flawless execution from end-to-end, including the ability to scale up for peak sales and scale down for normal sales.</span></span>  
  
 <span data-ttu-id="e6d70-121">Ce livre blanc décrit les solutions testées à l’aide de Microsoft Azure BizTalk Services (MABS) et BizTalk Server 2013.</span><span class="sxs-lookup"><span data-stu-id="e6d70-121">This white paper discusses the solutions tested using Microsoft Azure BizTalk Services (MABS) and BizTalk Server 2013.</span></span>  
  
 <span data-ttu-id="e6d70-122">Pour consulter le document, téléchargez le [à l’aide de Microsoft Azure BizTalk Services pour fournir des commandes de chaîne](http://download.microsoft.com/download/6/D/E/6DEE8EE9-0F26-4991-8FE5-B0E5239C0980/Using%20Windows%20Azure%20BizTalk%20Services%20for%20Supply%20Chain%20Orders.docx) document Word.</span><span class="sxs-lookup"><span data-stu-id="e6d70-122">To review the document, please download the [Using Microsoft Azure BizTalk Services for Supply Chain Orders](http://download.microsoft.com/download/6/D/E/6DEE8EE9-0F26-4991-8FE5-B0E5239C0980/Using%20Windows%20Azure%20BizTalk%20Services%20for%20Supply%20Chain%20Orders.docx) Word document.</span></span>