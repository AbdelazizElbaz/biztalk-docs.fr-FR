---
title: Utilisation des Services WCF | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF services
- Windows Communication Foundation (WCF)
ms.assetid: 34fe5e4c-6a92-4627-b2aa-e8b58a708320
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 29b984bcda798796565113739c6088af6d569f7c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-wcf-services"></a><span data-ttu-id="dbb51-102">utilisation des services WCF</span><span class="sxs-lookup"><span data-stu-id="dbb51-102">Using WCF Services</span></span>
<span data-ttu-id="dbb51-103">Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] assure la prise en charge intégrée de Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="dbb51-103">Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] provides built-in support for Windows Communication Foundation (WCF).</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="dbb51-104"> vous permet de réutiliser et d'agréger vos services WCF existants dans vos orchestrations.</span><span class="sxs-lookup"><span data-stu-id="dbb51-104"> enables you to reuse and aggregate all your existing WCF services within your orchestrations.</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="dbb51-105">implémente également la prise en charge pour les adaptateurs natifs dans les services WCF.</span><span class="sxs-lookup"><span data-stu-id="dbb51-105"> also implements support for native adapters in WCF services.</span></span> <span data-ttu-id="dbb51-106">Une telle prise en charge offre une évolutivité, une tolérance aux pannes et des capacités de suivi pour vos services WCF sans que vous ayez besoin d'écrire un code.</span><span class="sxs-lookup"><span data-stu-id="dbb51-106">Native adapter support provides scalability, fault tolerance, and tracking capabilities for WCF services without requiring you to write code.</span></span> <span data-ttu-id="dbb51-107">Pour plus d’informations sur les adaptateurs WCF, consultez [adaptateurs WCF](../core/wcf-adapters.md).</span><span class="sxs-lookup"><span data-stu-id="dbb51-107">For information about the WCF adapters, see [WCF Adapters](../core/wcf-adapters.md).</span></span>  
  
 <span data-ttu-id="dbb51-108">Prise en charge dans les services WCF [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] se répartissent en deux catégories : publication ou création de services WCF, ou l’appel ou utilisation des services WCF.</span><span class="sxs-lookup"><span data-stu-id="dbb51-108">The WCF services support in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] falls into two categories: publishing or creating WCF services, or calling or consuming WCF services.</span></span>  
  
 <span data-ttu-id="dbb51-109">**Publication des services WCF**</span><span class="sxs-lookup"><span data-stu-id="dbb51-109">**Publishing WCF services**</span></span>  
  
 <span data-ttu-id="dbb51-110">Grâce aux adaptateurs WCF, vous pouvez publier (exposer) les orchestrations et schémas en tant que services WCF afin de séparer la logique de service WCF de celle du processus d'entreprise.</span><span class="sxs-lookup"><span data-stu-id="dbb51-110">You can publish (expose) your orchestrations and schemas as WCF services with the WCF adapters to separate the WCF service logic from the business process logic.</span></span> <span data-ttu-id="dbb51-111">Pour les adaptateurs WCF isolés, l'Assistant Publication de services WCF BizTalk vous permet de créer des emplacements de réception WCF isolés qui sont hébergés sur des applications Web exécutées dans les services Internet (IIS).</span><span class="sxs-lookup"><span data-stu-id="dbb51-111">For isolated WCF adapters, you can use the BizTalk WCF Service Publishing Wizard to create isolated WCF receive locations hosted by Web applications running in Internet Information Services (IIS).</span></span> <span data-ttu-id="dbb51-112">Pour les adaptateurs WCF In-process, l'Assistant Publication de services WCF BizTalk vous permet de publier des métadonnées de service pour tout emplacement WCF.</span><span class="sxs-lookup"><span data-stu-id="dbb51-112">For the in-process WCF adapters, you can publish service metadata for any WCF locations with the BizTalk WCF Service Publishing Wizard.</span></span>  <span data-ttu-id="dbb51-113">La publication de métadonnées permet de créer un code client à l'aide de l'utilitaire svcutil.exe.</span><span class="sxs-lookup"><span data-stu-id="dbb51-113">The publishing of metadata allows the creation of client code using the svcutil.exe utility.</span></span>  
  
 <span data-ttu-id="dbb51-114">**Utilisation des services WCF**</span><span class="sxs-lookup"><span data-stu-id="dbb51-114">**Consuming WCF services**</span></span>  
  
 <span data-ttu-id="dbb51-115">Utilisez l'Assistant Consommation de service WCF BizTalk pour générer les artefacts BizTalk, par exemple des orchestrations et des types BizTalk, afin d'utiliser un service WCF basé sur le document de métadonnées du service WCF.</span><span class="sxs-lookup"><span data-stu-id="dbb51-115">You can use the BizTalk WCF Service Consuming Wizard to generate the BizTalk artifacts, such as BizTalk orchestrations and types, to consume a WCF service based on the metadata document of the WCF service.</span></span> <span data-ttu-id="dbb51-116">Les métadonnées permettent à un port d'envoi d'accéder à un service externe en tant que client.</span><span class="sxs-lookup"><span data-stu-id="dbb51-116">Metadata allows a send port to access an external service as a client.</span></span> <span data-ttu-id="dbb51-117">Elles permettent avant tout de décrire l'adresse du point de terminaison, la liaison et le contrat.</span><span class="sxs-lookup"><span data-stu-id="dbb51-117">Metadata is used purely for describing the endpoint address, binding, and contract.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="dbb51-118">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="dbb51-118">In This Section</span></span>  
  
-   [<span data-ttu-id="dbb51-119">Publication des Services WCF</span><span class="sxs-lookup"><span data-stu-id="dbb51-119">Publishing WCF Services</span></span>](../core/publishing-wcf-services.md)  
  
-   [<span data-ttu-id="dbb51-120">Utilisation des Services WCF</span><span class="sxs-lookup"><span data-stu-id="dbb51-120">Consuming WCF Services</span></span>](../core/consuming-wcf-services.md)  
  
-   [<span data-ttu-id="dbb51-121">En spécifiant le corps du Message pour les adaptateurs WCF</span><span class="sxs-lookup"><span data-stu-id="dbb51-121">Specifying the Message Body for the WCF Adapters</span></span>](../core/specifying-the-message-body-for-the-wcf-adapters.md)  
  
-   [<span data-ttu-id="dbb51-122">Procédures pas à pas l’adaptateur WCF</span><span class="sxs-lookup"><span data-stu-id="dbb51-122">WCF Adapter Walkthroughs</span></span>](../core/wcf-adapter-walkthroughs.md)