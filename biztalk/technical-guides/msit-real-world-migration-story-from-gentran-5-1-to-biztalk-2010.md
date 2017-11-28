---
title: "MSIT : Récit de Migration réels à partir de Gentran 5.1 vers BizTalk 2010 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 31326e2f-fb86-4b2c-88cd-b9406695038b
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1b742777c5e547078c2fa3fbf1a8d5bd8c466924
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="msit-real-world-migration-story-from-gentran-51-to-biztalk-2010"></a><span data-ttu-id="21628-102">MSIT : Récit de Migration réels à partir de Gentran 5.1 vers BizTalk 2010</span><span class="sxs-lookup"><span data-stu-id="21628-102">MSIT: Real World Migration Story from Gentran 5.1 to BizTalk 2010</span></span>
<span data-ttu-id="21628-103">Article de la technique de BizTalk</span><span class="sxs-lookup"><span data-stu-id="21628-103">BizTalk Technical Article</span></span>  
  
 <span data-ttu-id="21628-104">**MSIT : Récit de Migration réels à partir de Gentran 5.1 vers BizTalk 2010**</span><span class="sxs-lookup"><span data-stu-id="21628-104">**MSIT: Real World Migration Story from Gentran 5.1 to BizTalk 2010**</span></span>  
  
 <span data-ttu-id="21628-105">**Auteur :** Amit Kumar Dua, Microsoft &#124;  Banupriya Thirumaran, Microsoft</span><span class="sxs-lookup"><span data-stu-id="21628-105">**Author:** Amit Kumar Dua, Microsoft  &#124;  Banupriya Thirumaran, Microsoft</span></span>  
  
 <span data-ttu-id="21628-106">**Révisé par :** Mandi Ohlinger, Microsoft &#124;  Nitin Mehrotra, Microsoft</span><span class="sxs-lookup"><span data-stu-id="21628-106">**Reviewed By:** Mandi Ohlinger, Microsoft  &#124;  Nitin Mehrotra, Microsoft</span></span>  
  
 <span data-ttu-id="21628-107">**Collaborateurs :** Nikhil Tayal, Microsoft &#124;  Anil Chandra Lingam, Microsoft</span><span class="sxs-lookup"><span data-stu-id="21628-107">**Contributors:** Nikhil Tayal, Microsoft  &#124;  Anil Chandra Lingam, Microsoft</span></span>  
  
 <span data-ttu-id="21628-108">**Date de publication :** octobre 2014</span><span class="sxs-lookup"><span data-stu-id="21628-108">**Published:** October 2014</span></span>  
  
 <span data-ttu-id="21628-109">**S’applique à :** BizTalk Server 2010, serveur de Gentran</span><span class="sxs-lookup"><span data-stu-id="21628-109">**Applies To:** BizTalk Server 2010, Gentran Server</span></span>  
  
 <span data-ttu-id="21628-110">**Résumé :** la plateforme d’intégration de Microsoft IT (MSIT) utilise BizTalk Server et Gentran.</span><span class="sxs-lookup"><span data-stu-id="21628-110">**Summary:** The Microsoft IT (MSIT) integration platform uses BizTalk Server and Gentran.</span></span> <span data-ttu-id="21628-111">Jusqu'à récemment, Microsoft IT avait la présence d’un bon de Gentran empreintes.</span><span class="sxs-lookup"><span data-stu-id="21628-111">Until recently, Microsoft IT had a good presence of Gentran footprints.</span></span> <span data-ttu-id="21628-112">Avec BizTalk Server prenant en charge les capacités du cloud computing et AS2/EDI, il existe une opportunité pour remplacer Gentran avec Microsoft BizTalk Server 2010.</span><span class="sxs-lookup"><span data-stu-id="21628-112">With BizTalk Server supporting cloud computing and AS2/EDI capabilities, there is an opportunity to replace Gentran with Microsoft BizTalk Server 2010.</span></span>  <span data-ttu-id="21628-113">Gentran prend en charge Windows Server 2003 et SQL server 2005 ; qui sont dans un support étendu qui se termine plus rapidement.</span><span class="sxs-lookup"><span data-stu-id="21628-113">Gentran supports Windows Server 2003 and SQL server 2005; which are in extended support that is soon ending.</span></span> <span data-ttu-id="21628-114">Il n’existe aucune feuille de route pour Gentran prendre en charge des plateformes plus récentes, y compris Windows Server 2008/2012 et SQL Server 2008/2014.</span><span class="sxs-lookup"><span data-stu-id="21628-114">There is no roadmap for Gentran to support newer platforms, including Windows Server 2008/2012 and SQL Server 2008/2014.</span></span>  
  
 <span data-ttu-id="21628-115">MSIT consulté cela comme une opportunité pour</span><span class="sxs-lookup"><span data-stu-id="21628-115">MSIT viewed this as an opportunity to:</span></span>  
  
-   <span data-ttu-id="21628-116">Obtenir sur les plateformes plus récentes de la technologie</span><span class="sxs-lookup"><span data-stu-id="21628-116">Get to the newer technology platforms</span></span>  
  
-   <span data-ttu-id="21628-117">Supprimez les contraintes de prise en charge</span><span class="sxs-lookup"><span data-stu-id="21628-117">Remove the supportability constraints</span></span>  
  
-   <span data-ttu-id="21628-118">Simplifier l’architecture globale de la plateforme d’intégration</span><span class="sxs-lookup"><span data-stu-id="21628-118">Simplify the overall architecture of the integration platform</span></span>  
  
-   <span data-ttu-id="21628-119">Vérifiez la plateforme d’intégration plus efficace et fiable</span><span class="sxs-lookup"><span data-stu-id="21628-119">Make the integration platform more cost effective and robust</span></span>  
  
 <span data-ttu-id="21628-120">BizTalk Server 2010 est une plateforme d’intégration éprouvée, a de nombreuses fonctions et fonctionnalités et prend en charge les nouvelles technologies de plateforme.</span><span class="sxs-lookup"><span data-stu-id="21628-120">BizTalk Server 2010 is a proven integration platform, has numerous capabilities and features, and supports the new platform technologies.</span></span>  
  
 <span data-ttu-id="21628-121">Ce livre blanc explique la stratégie et les étapes pour migrer de Gentran 5.1 vers BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="21628-121">This white paper discusses the strategy and steps taken to migrate from Gentran 5.1 to BizTalk Server.</span></span>  
  
 <span data-ttu-id="21628-122">Pour consulter le document, téléchargez le [MSIT : World Migration sujet à partir de Gentran 5.1 vers BizTalk 2010](http://download.microsoft.com/download/6/D/E/6DEE8EE9-0F26-4991-8FE5-B0E5239C0980/Real%20World%20Migration%20Story%20from%20Gentran%20to%20BizTalk.docx) document Word.</span><span class="sxs-lookup"><span data-stu-id="21628-122">To review the document, please download the [MSIT: Real World Migration Story from Gentran 5.1 to BizTalk 2010](http://download.microsoft.com/download/6/D/E/6DEE8EE9-0F26-4991-8FE5-B0E5239C0980/Real%20World%20Migration%20Story%20from%20Gentran%20to%20BizTalk.docx) Word document.</span></span>