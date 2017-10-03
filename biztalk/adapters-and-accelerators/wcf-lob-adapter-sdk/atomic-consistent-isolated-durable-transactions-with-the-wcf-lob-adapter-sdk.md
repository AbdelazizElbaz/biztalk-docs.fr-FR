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
# <a name="configure-atomic-consistent-isolated-and-durable-transactions-using-the-wcf-lob-adapter-sdk"></a>Configurer les transactions atomiques, cohérentes, isolées et durables à l’aide de WCF LOB Adapter SDK
Le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] prend en charge des transactions en vous appuyant sur les fonctionnalités exposées par le [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]. À l’aide de l’API exposée par [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)], votre adaptateur peut prendre en charge les transactions et les opérations qui sont :  
  
-   **Atomique**, vous être assuré que toutes les en attente de mises à jour sont validées ou none sont validées et sont restaurées dans leur état précédent.  
  
-   **Cohérence**, garantissant que les modifications apportées sont d’un état cohérent à un autre.  
  
-   **Isolé**, empêche une transaction pour accéder à des modifications non validées dans d’autres transactions en attente.  
  
-   **Durabilité**, c'est-à-dire qu’une fois validées, les mises à jour seront persistantes en cas de défaillances.  
  
 Les développeurs ciblant relationnelle les systèmes de base de données ou autres systèmes métier-qui prend en charge (ou prévoyez) transactions devrez identifier comment le système cible prend en charge et expose la prise en charge de la transaction, puis identifiez un approprié[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]modèle de transaction à utiliser.  
  
 Pour plus d’informations sur [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] transactions, consultez [vue d’ensemble de Windows Communication Foundation Transactions](https://msdn.microsoft.com/library/ms733904.aspx). 
  
## <a name="see-also"></a>Voir aussi  
 [Planifier et concevoir votre adaptateur à l’aide de WCF LOB Adapter SDK](../../adapters-and-accelerators/wcf-lob-adapter-sdk/plan-and-design-your-adapter-using-the-wcf-lob-adapter-sdk.md)