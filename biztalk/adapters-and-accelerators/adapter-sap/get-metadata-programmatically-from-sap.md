---
title: "Obtenir les métadonnées par programme à partir de SAP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IMetadataRetrievalContract endpoint
- metadata, retrieving programmatically
- WS-Metadata Exchange (MEX) endpoint
ms.assetid: 8d75332e-c103-4bd5-a9a2-56d21747a04e
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4c856b3629d7d7dcd3f9aa5431c0406f6c822e54
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="get-metadata-programmatically-from-sap"></a><span data-ttu-id="251f9-102">Obtenir les métadonnées par programme à partir de SAP</span><span class="sxs-lookup"><span data-stu-id="251f9-102">Get Metadata Programmatically from SAP</span></span>
<span data-ttu-id="251f9-103">Le [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] est une liaison WCF personnalisée qui expose un système SAP comme un service WCF.</span><span class="sxs-lookup"><span data-stu-id="251f9-103">The [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] is a custom WCF binding that exposes an SAP system as a WCF service.</span></span> <span data-ttu-id="251f9-104">L’adaptateur expose le système SAP en tant qu’autodescriptif service ; Autrement dit, un service qui est capable de publication des métadonnées sur les opérations qu’il prend en charge.</span><span class="sxs-lookup"><span data-stu-id="251f9-104">The adapter exposes the SAP system as a self-describing service; that is, a service that is capable of publishing metadata about the operations that it supports.</span></span> <span data-ttu-id="251f9-105">Les métadonnées décrivent l’interface logique à un service WCF ; Autrement dit, le contrat de service, les messages et les schémas de message qui doivent être utilisés pour interagir avec le service.</span><span class="sxs-lookup"><span data-stu-id="251f9-105">Metadata describes the logical interface to a WCF service; that is, the service contract, messages, and message schemas that must be used to interact with the service.</span></span>  
  
 <span data-ttu-id="251f9-106">Ces métadonnées sont utilisées par des outils tels que :</span><span class="sxs-lookup"><span data-stu-id="251f9-106">This metadata is used by tools such as:</span></span>  
  
-   <span data-ttu-id="251f9-107">Le [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] pour générer des représentations sous forme de code managé du contrat de service, et</span><span class="sxs-lookup"><span data-stu-id="251f9-107">The [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] to generate managed code representations of the service contract, and</span></span>  
  
-   <span data-ttu-id="251f9-108">Le [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] pour générer des schémas de message.</span><span class="sxs-lookup"><span data-stu-id="251f9-108">The [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] to generate message schemas.</span></span>  
  
 <span data-ttu-id="251f9-109">Toutefois, vous pouvez récupérer également de métadonnées par programme à partir de l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="251f9-109">However, you can also retrieve metadata programmatically from the adapter.</span></span> <span data-ttu-id="251f9-110">Par exemple, vous pouvez souhaiter procéder ainsi pour créer un outil de récupération de métadonnées personnalisées à utiliser dans une application existante.</span><span class="sxs-lookup"><span data-stu-id="251f9-110">For example, you might want to do this to create a custom metadata retrieval tool to use in an existing application.</span></span>  
  
 <span data-ttu-id="251f9-111">L’adaptateur publie les métadonnées via deux points de terminaison :</span><span class="sxs-lookup"><span data-stu-id="251f9-111">The adapter publishes metadata through two endpoints:</span></span>  
  
-   <span data-ttu-id="251f9-112">Un point de terminaison WS-MEX (Metadata Exchange).</span><span class="sxs-lookup"><span data-stu-id="251f9-112">A WS-Metadata Exchange (MEX) endpoint.</span></span> <span data-ttu-id="251f9-113">WCF fournit automatiquement un point de terminaison MEX pour toutes les liaisons WCF.</span><span class="sxs-lookup"><span data-stu-id="251f9-113">WCF automatically provides a MEX endpoint for all WCF bindings.</span></span> <span data-ttu-id="251f9-114">Vous pouvez utiliser l’échange de métadonnées à récupérer des métadonnées pour les opérations prises en charge par l’adaptateur sur le système SAP sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="251f9-114">You can use metadata exchange to retrieve metadata for operations supported by the adapter on the underlying SAP system.</span></span>  
  
-   <span data-ttu-id="251f9-115">Un **IMetadataRetrievalContract** point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="251f9-115">An **IMetadataRetrievalContract** endpoint.</span></span> <span data-ttu-id="251f9-116">Le **IMetadataRetrievalContract** interface est implémentée par le [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="251f9-116">The **IMetadataRetrievalContract** interface is implemented by the [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)].</span></span> <span data-ttu-id="251f9-117">Il classe les artefacts du système SAP à plusieurs niveaux logiques et les présente sous la forme d’une arborescence de nœuds de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="251f9-117">It categorizes SAP system artifacts at multiple logical levels and presents them as a tree of metadata nodes.</span></span> <span data-ttu-id="251f9-118">Vous pouvez utiliser les méthodes exposées par le **IMetadataRetrievalContract** interface pour parcourir et rechercher les nœuds de cette arborescence et pour retourner des métadonnées pour les opérations qui vous intéressent.</span><span class="sxs-lookup"><span data-stu-id="251f9-118">You can use methods exposed by the **IMetadataRetrievalContract** interface to browse and search the nodes of this tree and to return metadata for operations in which you are interested.</span></span>  
  
 <span data-ttu-id="251f9-119">Les rubriques de cette section décrivent comment utiliser MEX et **IMetadataRetrievalContract** points de terminaison pour récupérer des métadonnées par programme à partir de l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="251f9-119">The topics in this section describe how to use MEX and **IMetadataRetrievalContract** endpoints to retrieve metadata programmatically from the adapter.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="251f9-120">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="251f9-120">In This Section</span></span>  
  
-   [<span data-ttu-id="251f9-121">La récupération de métadonnées à l’aide de WS-Metadata Exchange dans SAP</span><span class="sxs-lookup"><span data-stu-id="251f9-121">Retrieving Metadata Using WS-Metadata Exchange in SAP</span></span>](../../adapters-and-accelerators/adapter-sap/get-metadata-using-ws-metadata-exchange-in-sap.md)  
  
-   [<span data-ttu-id="251f9-122">La récupération des métadonnées dans SAP à l’aide de IMetadataRetrievalContract</span><span class="sxs-lookup"><span data-stu-id="251f9-122">Retrieving Metadata in SAP Using IMetadataRetrievalContract</span></span>](../../adapters-and-accelerators/adapter-sap/get-metadata-in-sap-using-imetadataretrievalcontract.md)  
  
## <a name="see-also"></a><span data-ttu-id="251f9-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="251f9-123">See Also</span></span>  
[<span data-ttu-id="251f9-124">Développer vos applications SAP</span><span class="sxs-lookup"><span data-stu-id="251f9-124">Develop your SAP applications</span></span>](../../adapters-and-accelerators/adapter-sap/develop-your-sap-applications.md)