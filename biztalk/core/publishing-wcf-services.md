---
title: Publication de Services WCF | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- publishing, WCF services
- WCF services, publishing
ms.assetid: 70b7851b-77c1-4ab3-a61f-e7165ceb56fb
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d5f72f2b300738f2e9a1a643e152048b64cf8f55
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="publishing-wcf-services"></a><span data-ttu-id="89286-102">Publication des Services WCF</span><span class="sxs-lookup"><span data-stu-id="89286-102">Publishing WCF Services</span></span>
<span data-ttu-id="89286-103">Une orchestration peut être publiée comme service WCF dans [!INCLUDE[btsCoName](../includes/btsconame-md.md)] [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] à être appelé par les clients WCF.</span><span class="sxs-lookup"><span data-stu-id="89286-103">An orchestration can be published as a WCF service in [!INCLUDE[btsCoName](../includes/btsconame-md.md)][!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to be called by WCF clients.</span></span>  
  
 <span data-ttu-id="89286-104">**Publication de services WCF avec les adaptateurs WCF isolés**</span><span class="sxs-lookup"><span data-stu-id="89286-104">**Publishing WCF services with the isolated WCF adapters**</span></span>  
  
 <span data-ttu-id="89286-105">L'Assistant Publication de services WCF BizTalk permet de créer et de publier des services WCF pour les adaptateurs WCF isolés tels que les adaptateurs WCF-BasicHttp, WCF-WSHttp et WCF-CustomIsolated.</span><span class="sxs-lookup"><span data-stu-id="89286-105">You create and publish WCF services by using the BizTalk WCF Service Publishing Wizard for the isolated WCF adapters such as the WCF-BasicHttp adapter, the WCF-WSHttp adapter, and the WCF-CustomIsolated adapter.</span></span> <span data-ttu-id="89286-106">L'emplacement de réception créé dans ce cadre existe comme une application hors processus dans IIS.</span><span class="sxs-lookup"><span data-stu-id="89286-106">This creates a receive location which exists as an out of process application in IIS.</span></span>  
  
 <span data-ttu-id="89286-107">Avant de publier un service WCF avec les adaptateurs WCF isolés, vous devez être familiarisé avec l'hébergement des services WCF dans IIS (Internet Information Services).</span><span class="sxs-lookup"><span data-stu-id="89286-107">Before you publish a WCF service with the isolated WCF adapters, you should have an understanding of how to host WCF services in Internet Information Services (IIS).</span></span>  
  
 <span data-ttu-id="89286-108">**Publication des métadonnées de service pour les emplacements de réception WCF**</span><span class="sxs-lookup"><span data-stu-id="89286-108">**Publishing service metadata for the WCF receive locations**</span></span>  
  
 <span data-ttu-id="89286-109">L'Assistant Publication de services WCF BizTalk permet de créer des métadonnées de service pour les emplacements de réception WCF publiés.</span><span class="sxs-lookup"><span data-stu-id="89286-109">You create service metadata for published WCF receive locations by using the BizTalk WCF Service Publishing Wizard.</span></span> <span data-ttu-id="89286-110">Pour générer le code de client de modèle de service à partir de documents de métadonnées publiés, vous pouvez utiliser l’outil Service Model Metadata Utility (SvcUtil.exe) inclus dans le [!INCLUDE[btsCoName](../includes/btsconame-md.md)] [!INCLUDE[btsWinNoVersion](../includes/btswinnoversion-md.md)] Kit de développement logiciel (SDK) pour [!INCLUDE[btsWinVista](../includes/btswinvista-md.md)] et [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)] Composants d’exécution.</span><span class="sxs-lookup"><span data-stu-id="89286-110">To generate service model client code from the published metadata documents you can use the Service Model Metadata Utility tool (SvcUtil.exe) included in the [!INCLUDE[btsCoName](../includes/btsconame-md.md)][!INCLUDE[btsWinNoVersion](../includes/btswinnoversion-md.md)] Software Development Kit (SDK) for [!INCLUDE[btsWinVista](../includes/btswinvista-md.md)] and [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)] Runtime Components.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="89286-111">Avant d'exécuter l'Assistant Publication de services WCF BizTalk, vous devez activer les services WCF.</span><span class="sxs-lookup"><span data-stu-id="89286-111">Before running the BizTalk WCF Service Publishing Wizard, you must enable WCF services.</span></span> <span data-ttu-id="89286-112">Pour plus d’informations sur l’activation des services WCF pour votre système, consultez [de configurer IIS pour les adaptateurs de réception WCF isolés](../core/configuring-iis-for-the-isolated-wcf-receive-adapters.md).</span><span class="sxs-lookup"><span data-stu-id="89286-112">For more information about enabling WCF services for your system, see [Configuring IIS for the Isolated WCF Receive Adapters](../core/configuring-iis-for-the-isolated-wcf-receive-adapters.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="89286-113">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="89286-113">In This Section</span></span>  
  
-   [<span data-ttu-id="89286-114">Publication des Services WCF avec WCF isolé des adaptateurs de réception</span><span class="sxs-lookup"><span data-stu-id="89286-114">Publishing WCF Services with the Isolated WCF Receive Adapters</span></span>](../core/publishing-wcf-services-with-the-isolated-wcf-receive-adapters.md)  
  
-   [<span data-ttu-id="89286-115">Publication des métadonnées de Service WCF pour les adaptateurs de réception</span><span class="sxs-lookup"><span data-stu-id="89286-115">Publishing Service Metadata for the WCF Receive Adapters</span></span>](../core/publishing-service-metadata-for-the-wcf-receive-adapters.md)  
  
-   [<span data-ttu-id="89286-116">Considérations relatives à la publication de Services WCF avec WCF des adaptateurs de réception</span><span class="sxs-lookup"><span data-stu-id="89286-116">Considerations When Publishing WCF Services with the WCF Receive Adapters</span></span>](../core/considerations-when-publishing-wcf-services-with-the-wcf-receive-adapters.md)  
  
-   [<span data-ttu-id="89286-117">En-têtes SOAP avec les Services WCF publiés</span><span class="sxs-lookup"><span data-stu-id="89286-117">SOAP Headers with Published WCF Services</span></span>](../core/soap-headers-with-published-wcf-services.md)  
  
-   [<span data-ttu-id="89286-118">Levée des Exceptions d’erreur à partir d’Orchestrations publiées en tant que Services WCF</span><span class="sxs-lookup"><span data-stu-id="89286-118">How to Throw Fault Exceptions from Orchestrations Published as WCF Services</span></span>](../core/how-to-throw-fault-exceptions-from-orchestrations-published-as-wcf-services.md)