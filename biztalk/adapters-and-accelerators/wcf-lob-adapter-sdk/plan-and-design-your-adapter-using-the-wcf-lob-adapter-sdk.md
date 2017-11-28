---
title: "Planifier et concevoir votre adaptateur à l’aide de WCF LOB Adapter SDK | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2dfbfa6c-2f87-40bb-93d4-6fbb37a235c5
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ae4ff4e0263c5b652d9422324ea176496bc555aa
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="plan-and-design-your-adapter-using-the-wcf-lob-adapter-sdk"></a><span data-ttu-id="c2577-102">Planifier et concevoir votre adaptateur à l’aide de WCF LOB Adapter SDK</span><span class="sxs-lookup"><span data-stu-id="c2577-102">Plan and design your adapter using the WCF LOB Adapter SDK</span></span>

## <a name="overview"></a><span data-ttu-id="c2577-103">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="c2577-103">Overview</span></span>
<span data-ttu-id="c2577-104">La planification est une partie importante de tout effort de développement, y compris les adaptateurs développés avec le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c2577-104">Planning is an important part of any development effort, including adapters developed with the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span></span> <span data-ttu-id="c2577-105">Planifier des stratégies pour interagir avec le système de métier et les détails d’implémentation différentes impliquées votre adaptateur se comporte de manière inattendue, un manque de certaines fonctionnalités clés fournies par l’API de développement d’un adaptateur peut entraîner une défaillance et attendu par l’utilisateur, ou pour exiger la réparation et la mise à jour fréquente.</span><span class="sxs-lookup"><span data-stu-id="c2577-105">Failure to adequately plan strategies for interacting with the line-of-business system and the different implementation details involved when developing an adapter could cause your adapter to behave unexpectedly, to lack certain key features provided by the API and expected by the user, or to require frequent update and repair.</span></span>  
  
 <span data-ttu-id="c2577-106">Cette section contient les informations nécessaires à la conception de votre adaptateur.</span><span class="sxs-lookup"><span data-stu-id="c2577-106">This section contains the information needed to design your adapter.</span></span> <span data-ttu-id="c2577-107">À l’aide de ces informations, vous pouvez planifier une conception qui répond aux besoins de vos utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="c2577-107">Using this information, you can plan a design that meets the needs of your users.</span></span>  
  
## <a name="get-started"></a><span data-ttu-id="c2577-108">Prise en main</span><span class="sxs-lookup"><span data-stu-id="c2577-108">Get started</span></span>
  
-   [<span data-ttu-id="c2577-109">Connaître et comprendre votre système métier</span><span class="sxs-lookup"><span data-stu-id="c2577-109">Know and understand your LOB system</span></span>](understand-the-lob-system-with-the-wcf-lob-adapter-sdk.md) 
  
-   [<span data-ttu-id="c2577-110">Afficher les modèles d’échange de message pris en charge dans WCF LOB Adapter SDK</span><span class="sxs-lookup"><span data-stu-id="c2577-110">View the supported message exchange patterns in the WCF LOB Adapter SDK</span></span>](view-the-supported-message-exchange-patterns-in-the-wcf-lob-adapter-sdk.md)  
  
-   [<span data-ttu-id="c2577-111">Sélectionnez un schéma d’URI et le format d’adressage lors de l’utilisation de WCF LOB Adapter SDK</span><span class="sxs-lookup"><span data-stu-id="c2577-111">Select a URI scheme and addressing format when using the WCF LOB Adapter SDK</span></span>](select-a-uri-scheme-and-addressing-format-when-using-the-wcf-lob-adapter-sdk.md)  
  
-   [<span data-ttu-id="c2577-112">Comprendre la sécurité WCF sur la carte créée avec WCF LOB Adapter SDK</span><span class="sxs-lookup"><span data-stu-id="c2577-112">Understand WCF security on the adapter created with the WCF LOB Adapter SDK</span></span>](understand-wcf-security-on-the-adapter-created-with-the-wcf-lob-adapter-sdk.md)  
  
-   [<span data-ttu-id="c2577-113">Comprendre les transactions dans WCF</span><span class="sxs-lookup"><span data-stu-id="c2577-113">Understand transactions in WCF</span></span>](atomic-consistent-isolated-durable-transactions-with-the-wcf-lob-adapter-sdk.md)  
  
-   [<span data-ttu-id="c2577-114">À propos de la recherche de métadonnées et de navigation avec votre adaptateur WCF LOB Adapter SDK</span><span class="sxs-lookup"><span data-stu-id="c2577-114">About metadata search and browse with your WCF LOB Adapter SDK adapter</span></span>](about-metadata-search-and-browse-with-your-wcf-lob-adapter-sdk-adapter.md)
  
## <a name="see-also"></a><span data-ttu-id="c2577-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c2577-115">See Also</span></span>  
[<span data-ttu-id="c2577-116">Planifier et concevoir votre adaptateur</span><span class="sxs-lookup"><span data-stu-id="c2577-116">Plan and architect your adapter</span></span>](plan-and-design-an-adapter-using-the-wcf-lob-adapter-sdk.md)