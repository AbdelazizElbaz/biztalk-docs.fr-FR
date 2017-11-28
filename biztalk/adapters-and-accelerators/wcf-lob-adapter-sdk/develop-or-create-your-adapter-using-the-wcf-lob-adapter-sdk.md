---
title: "Développer ou créez votre adaptateur à l’aide de WCF LOB Adapter SDK | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2ca8c03a-1e4a-4077-b4cb-4e184b520bbb
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6e7e4c76add25b53a8b3e32707c6a09b92636559
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="develop-or-create-your-adapter-using-the-wcf-lob-adapter-sdk"></a><span data-ttu-id="f4520-102">Développer ou créez votre adaptateur à l’aide de WCF LOB Adapter SDK</span><span class="sxs-lookup"><span data-stu-id="f4520-102">Develop or create your adapter using the WCF LOB Adapter SDK</span></span>
<span data-ttu-id="f4520-103">Cette section contient des informations destinées aux développeurs qui créent des cartes à l’aide de la [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f4520-103">This section contains information for developers who are creating adapters using the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span></span> <span data-ttu-id="f4520-104">Une fois que l’adaptateur a été développé, elle est généralement utilisée par .NET ou [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] les développeurs comme un moyen pour accéder aux opérations et les données dans un système de line-of-business cible souhaitée.</span><span class="sxs-lookup"><span data-stu-id="f4520-104">Once the adapter has been developed, it is usually consumed by either .NET or [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] developers as a way to access operations and data in a desired target line-of-business system.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f4520-105">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="f4520-105">In This Section</span></span>  
  
-   [<span data-ttu-id="f4520-106">Recommandées de développement à l’aide de WCF LOB Adapter SDK</span><span class="sxs-lookup"><span data-stu-id="f4520-106">Development Best Practices using the WCF LOB Adapter SDK</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/development-best-practices-using-the-wcf-lob-adapter-sdk.md)  
  
-   [<span data-ttu-id="f4520-107">Utiliser des espaces de noms avec le Proxy WSDL dans WCF LOB Adapter SDK</span><span class="sxs-lookup"><span data-stu-id="f4520-107">Use namespaces with the WSDL-Proxy in the WCF LOB Adapter SDK</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/use-namespaces-with-the-wsdl-proxy-in-the-wcf-lob-adapter-sdk.md)  
  
-   [<span data-ttu-id="f4520-108">Décrire le schéma de Documentation WSDL PortType avec le Kit de développement logiciel de l’adaptateur LOB WCF</span><span class="sxs-lookup"><span data-stu-id="f4520-108">Describe the WSDL PortType Documentation Schema with the WCF LOB Adapter SDK</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/describe-the-wsdl-porttype-documentation-schema-with-the-wcf-lob-adapter-sdk.md)  
  
-   [<span data-ttu-id="f4520-109">Gérer les versions d’adaptateur avec WCF LOB Adapter SDK</span><span class="sxs-lookup"><span data-stu-id="f4520-109">Manage adapter versioning with the WCF LOB Adapter SDK</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/manage-adapter-versioning-with-the-wcf-lob-adapter-sdk.md)  
  
-   [<span data-ttu-id="f4520-110">Un comportement de Service permet d’entrer les informations d’identification avec WCF LOB Adapter SDK</span><span class="sxs-lookup"><span data-stu-id="f4520-110">Use a Service Behavior to enter credentials with the WCF LOB Adapter SDK</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/use-a-service-behavior-to-enter-credentials-with-the-wcf-lob-adapter-sdk.md)  
  
-   [<span data-ttu-id="f4520-111">Exposer des paramètres de la carte en tant que propriété de liaison à l’aide de WCF LOB Adapter SDK</span><span class="sxs-lookup"><span data-stu-id="f4520-111">Expose adapter settings as binding property using the WCF LOB Adapter SDK</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/expose-adapter-settings-as-a-binding-property-using-the-wcf-lob-adapter-sdk.md)  
  
-   [<span data-ttu-id="f4520-112">Parcourir et rechercher des métadonnées à l’aide de WCF LOB Adapter SDK</span><span class="sxs-lookup"><span data-stu-id="f4520-112">Browse and Search Metadata using the WCF LOB Adapter SDK</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/browse-and-search-metadata-using-the-wcf-lob-adapter-sdk.md)  
  
-   [<span data-ttu-id="f4520-113">Prise en charge des transactions</span><span class="sxs-lookup"><span data-stu-id="f4520-113">Transaction Support</span></span>](../../core/transaction-support.md)  
  
-   [<span data-ttu-id="f4520-114">Héberger un adaptateur dans IIS à l’aide de WCF LOB Adapter SDK</span><span class="sxs-lookup"><span data-stu-id="f4520-114">Host an adapter in IIS using the WCF LOB Adapter SDK</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/host-an-adapter-in-iis-using-the-wcf-lob-adapter-sdk.md) 
  
-   [<span data-ttu-id="f4520-115">Utiliser un adaptateur créé à l’aide de WCF LOB Adapter SDK</span><span class="sxs-lookup"><span data-stu-id="f4520-115">Consume an Adapter created using the WCF LOB Adapter SDK</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/consume-an-adapter-created-using-the-wcf-lob-adapter-sdk.md)  
  
## <a name="see-also"></a><span data-ttu-id="f4520-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f4520-116">See Also</span></span>  
 <span data-ttu-id="f4520-117">[Prise en main WCF LOB Adapter SDK](../../adapters-and-accelerators/wcf-lob-adapter-sdk/get-started-with-the-with-the-wcf-lob-adapter-sdk.md) </span><span class="sxs-lookup"><span data-stu-id="f4520-117">[Get started with the WCF LOB Adapter SDK](../../adapters-and-accelerators/wcf-lob-adapter-sdk/get-started-with-the-with-the-wcf-lob-adapter-sdk.md) </span></span>  
 [<span data-ttu-id="f4520-118">Dépannage des adaptateurs WCF</span><span class="sxs-lookup"><span data-stu-id="f4520-118">Troubleshooting the WCF Adapters</span></span>](../../core/troubleshooting-the-wcf-adapters.md)