---
title: Publier des Services WCF | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 70b7851b-77c1-4ab3-a61f-e7165ceb56fb
caps.latest.revision: 
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 00136b64d5feaf552f77b92b3ad4442da4e447cc
ms.sourcegitcommit: 32f380810b90b70e5df7be72a6a14988a747868e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2018
---
# <a name="publish-wcf-services"></a><span data-ttu-id="aabc0-102">Publier des Services WCF</span><span class="sxs-lookup"><span data-stu-id="aabc0-102">Publish WCF Services</span></span>
<span data-ttu-id="aabc0-103">Une orchestration peut être publiée comme service WCF dans BizTalk Server d’être appelée par les clients WCF.</span><span class="sxs-lookup"><span data-stu-id="aabc0-103">An orchestration can be published as a WCF service in BizTalk Server to be called by WCF clients.</span></span>  
  
## <a name="publish-wcf-services-with-the-isolated-wcf-adapters"></a><span data-ttu-id="aabc0-104">Publier les services WCF avec les adaptateurs WCF isolés</span><span class="sxs-lookup"><span data-stu-id="aabc0-104">Publish WCF services with the isolated WCF adapters</span></span> 
  
 <span data-ttu-id="aabc0-105">L'Assistant Publication de services WCF BizTalk permet de créer et de publier des services WCF pour les adaptateurs WCF isolés tels que les adaptateurs WCF-BasicHttp, WCF-WSHttp et WCF-CustomIsolated.</span><span class="sxs-lookup"><span data-stu-id="aabc0-105">You create and publish WCF services by using the BizTalk WCF Service Publishing Wizard for the isolated WCF adapters such as the WCF-BasicHttp adapter, the WCF-WSHttp adapter, and the WCF-CustomIsolated adapter.</span></span> <span data-ttu-id="aabc0-106">L'emplacement de réception créé dans ce cadre existe comme une application hors processus dans IIS.</span><span class="sxs-lookup"><span data-stu-id="aabc0-106">This creates a receive location which exists as an out of process application in IIS.</span></span>  
  
 <span data-ttu-id="aabc0-107">Avant de publier un service WCF avec les adaptateurs WCF isolés, vous devez être familiarisé avec l'hébergement des services WCF dans IIS (Internet Information Services).</span><span class="sxs-lookup"><span data-stu-id="aabc0-107">Before you publish a WCF service with the isolated WCF adapters, you should have an understanding of how to host WCF services in Internet Information Services (IIS).</span></span>  
  
## <a name="publish-service-metadata-for-the-wcf-receive-locations"></a><span data-ttu-id="aabc0-108">Publier les métadonnées de service pour les emplacements de réception WCF</span><span class="sxs-lookup"><span data-stu-id="aabc0-108">Publish service metadata for the WCF receive locations</span></span>
  
 <span data-ttu-id="aabc0-109">L'Assistant Publication de services WCF BizTalk permet de créer des métadonnées de service pour les emplacements de réception WCF publiés.</span><span class="sxs-lookup"><span data-stu-id="aabc0-109">You create service metadata for published WCF receive locations by using the BizTalk WCF Service Publishing Wizard.</span></span> <span data-ttu-id="aabc0-110">Pour générer un code de client de modèle de service à partir de documents de métadonnées publiés, vous pouvez utiliser l’outil Service Model Metadata Utility (SvcUtil.exe) inclus dans le Kit de développement logiciel (SDK) Windows et les composants d’exécution .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="aabc0-110">To generate service model client code from the published metadata documents you can use the Service Model Metadata Utility tool (SvcUtil.exe) included in the Windows Software Development Kit (SDK) and .NET Framework Runtime Components.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="aabc0-111">Avant d'exécuter l'Assistant Publication de services WCF BizTalk, vous devez activer les services WCF.</span><span class="sxs-lookup"><span data-stu-id="aabc0-111">Before running the BizTalk WCF Service Publishing Wizard, you must enable WCF services.</span></span> <span data-ttu-id="aabc0-112">Pour plus d’informations sur l’activation des services WCF pour votre système, consultez [de configurer IIS pour les adaptateurs de réception WCF isolés](../core/configuring-iis-for-the-isolated-wcf-receive-adapters.md).</span><span class="sxs-lookup"><span data-stu-id="aabc0-112">For more information about enabling WCF services for your system, see [Configuring IIS for the Isolated WCF Receive Adapters](../core/configuring-iis-for-the-isolated-wcf-receive-adapters.md).</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="aabc0-113">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="aabc0-113">Next steps</span></span>
  
-   [<span data-ttu-id="aabc0-114">Publication des services WCF avec les adaptateurs de réception WCF isolés</span><span class="sxs-lookup"><span data-stu-id="aabc0-114">Publishing WCF Services with the Isolated WCF Receive Adapters</span></span>](../core/publishing-wcf-services-with-the-isolated-wcf-receive-adapters.md)  
  
-   [<span data-ttu-id="aabc0-115">Publication des métadonnées de service pour les adaptateurs de réception WCF</span><span class="sxs-lookup"><span data-stu-id="aabc0-115">Publishing Service Metadata for the WCF Receive Adapters</span></span>](../core/publishing-service-metadata-for-the-wcf-receive-adapters.md)  
  
-   [<span data-ttu-id="aabc0-116">Considérations à prendre en compte lors de la publication de services WCF avec les adaptateurs de réception WCF</span><span class="sxs-lookup"><span data-stu-id="aabc0-116">Considerations When Publishing WCF Services with the WCF Receive Adapters</span></span>](../core/considerations-when-publishing-wcf-services-with-the-wcf-receive-adapters.md)  
  
-   [<span data-ttu-id="aabc0-117">En-têtes SOAP avec les services WCF publiés</span><span class="sxs-lookup"><span data-stu-id="aabc0-117">SOAP Headers with Published WCF Services</span></span>](../core/soap-headers-with-published-wcf-services.md)  
  
-   [<span data-ttu-id="aabc0-118">Lever des exceptions d’erreur à partir d’orchestrations publiées sous forme de services WCF</span><span class="sxs-lookup"><span data-stu-id="aabc0-118">Throw Fault Exceptions from Orchestrations Published as WCF Services</span></span>](../core/how-to-throw-fault-exceptions-from-orchestrations-published-as-wcf-services.md)