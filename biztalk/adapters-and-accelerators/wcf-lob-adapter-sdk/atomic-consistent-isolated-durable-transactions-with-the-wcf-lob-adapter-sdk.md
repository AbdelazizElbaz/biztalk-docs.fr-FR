---
title: "Configurer les transactions atomiques, cohérentes, isolées et durables à l’aide de WCF LOB Adapter SDK | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c20d2613-c77d-4b0d-b2e2-3ed28a8fb36c
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 58cf80a70b04e20aeb25b27210d88dfd861d7539
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configure-atomic-consistent-isolated-and-durable-transactions-using-the-wcf-lob-adapter-sdk"></a><span data-ttu-id="690d1-102">Configurer les transactions atomiques, cohérentes, isolées et durables à l’aide de WCF LOB Adapter SDK</span><span class="sxs-lookup"><span data-stu-id="690d1-102">Configure atomic, consistent, isolated, and durable transactions using the WCF LOB Adapter SDK</span></span>
<span data-ttu-id="690d1-103">Le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] prend en charge des transactions en vous appuyant sur les fonctionnalités exposées par le [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="690d1-103">The [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] supports transactions by relying on functionality exposed by the [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)].</span></span> <span data-ttu-id="690d1-104">À l’aide de l’API exposée par [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)], votre adaptateur peut prendre en charge les transactions et les opérations qui sont :</span><span class="sxs-lookup"><span data-stu-id="690d1-104">By using the API exposed by [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)], your adapter can support transactions and operations that are:</span></span>  
  
-   <span data-ttu-id="690d1-105">**Atomique**, vous être assuré que toutes les en attente de mises à jour sont validées ou none sont validées et sont restaurées dans leur état précédent.</span><span class="sxs-lookup"><span data-stu-id="690d1-105">**Atomic**, ensuring that either all pending updates are committed or none are committed and are rolled back to their previous state.</span></span>  
  
-   <span data-ttu-id="690d1-106">**Cohérence**, garantissant que les modifications apportées sont d’un état cohérent à un autre.</span><span class="sxs-lookup"><span data-stu-id="690d1-106">**Consistent**, ensuring that changes made are from one consistent state to another.</span></span>  
  
-   <span data-ttu-id="690d1-107">**Isolé**, empêche une transaction pour accéder à des modifications non validées dans d’autres transactions en attente.</span><span class="sxs-lookup"><span data-stu-id="690d1-107">**Isolated**, preventing a transaction to access uncommitted changes in other pending transactions.</span></span>  
  
-   <span data-ttu-id="690d1-108">**Durabilité**, c'est-à-dire qu’une fois validées, les mises à jour seront persistantes en cas de défaillances.</span><span class="sxs-lookup"><span data-stu-id="690d1-108">**Durable**, meaning that once committed, updates will be persistent in the face of failures.</span></span>  
  
 <span data-ttu-id="690d1-109">Les développeurs ciblant relationnelle les systèmes de base de données ou autres systèmes métier-qui prend en charge (ou prévoyez) transactions devrez identifier comment le système cible prend en charge et expose la prise en charge de la transaction, puis identifiez un approprié[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]modèle de transaction à utiliser.</span><span class="sxs-lookup"><span data-stu-id="690d1-109">Adapter developers targeting relational database systems or other line-of-business systems that support (or expect) transactions will need to identify how the target system supports and exposes transaction support and then identify an appropriate [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] transaction model to use.</span></span>  
  
 <span data-ttu-id="690d1-110">Pour plus d’informations sur [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] transactions, consultez [vue d’ensemble de Windows Communication Foundation Transactions](https://msdn.microsoft.com/library/ms733904.aspx).</span><span class="sxs-lookup"><span data-stu-id="690d1-110">For more information about [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] transactions, see [Windows Communication Foundation Transactions Overview](https://msdn.microsoft.com/library/ms733904.aspx).</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="690d1-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="690d1-111">See Also</span></span>  
 [<span data-ttu-id="690d1-112">Planifier et concevoir votre adaptateur à l’aide de WCF LOB Adapter SDK</span><span class="sxs-lookup"><span data-stu-id="690d1-112">Plan and Design your Adapter using the WCF LOB Adapter SDK</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/plan-and-design-your-adapter-using-the-wcf-lob-adapter-sdk.md)