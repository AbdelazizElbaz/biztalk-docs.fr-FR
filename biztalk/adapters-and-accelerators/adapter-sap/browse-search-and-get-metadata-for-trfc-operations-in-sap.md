---
title: "Parcourir, rechercher et obtenir des métadonnées pour les opérations tRFC dans SAP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tRFC operations
- tRFC operations, browsing
- searching, tRFC operations
- tRFC operations, searching
- browsing, tRFC operations
ms.assetid: cf4a16d1-7bbf-4dea-b54d-b5315fbcd552
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5124eb4b3a56df70ec55d157ee80a394d6bff83d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="browse-search-and-get-metadata-for-trfc-operations-in-sap"></a><span data-ttu-id="3b728-102">Parcourir, rechercher et obtenir des métadonnées pour les opérations tRFC dans SAP</span><span class="sxs-lookup"><span data-stu-id="3b728-102">Browse, search, and get metadata for tRFC operations in SAP</span></span>
<span data-ttu-id="3b728-103">tRFCs ne sont pas un artefact distinct dans un système SAP.</span><span class="sxs-lookup"><span data-stu-id="3b728-103">tRFCs are not a separate artifact in an SAP system.</span></span> <span data-ttu-id="3b728-104">Ces aspects sont classés sous un nœud séparé par le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] , car leurs caractéristiques des métadonnées sont différents de ceux de RFC.</span><span class="sxs-lookup"><span data-stu-id="3b728-104">These are categorized under a separate node by the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] because their metadata characteristics are different from that of RFCs.</span></span> <span data-ttu-id="3b728-105">Toutefois, l’expérience de navigation, recherche et la récupération des métadonnées pour tRFCs sont identique à celui des RFC.</span><span class="sxs-lookup"><span data-stu-id="3b728-105">However, the experience of browsing, searching, and retrieving metadata for tRFCs is identical to that of the RFCs.</span></span> <span data-ttu-id="3b728-106">Reportez-vous à [Parcourir, rechercher et obtenir des métadonnées pour les opérations de RFC dans SAP](../../adapters-and-accelerators/adapter-sap/browse-search-and-get-metadata-for-rfc-operations-in-sap.md) pour plus d’informations sur l’utilisation de la [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] ou [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] pour parcourir, rechercher et récupérer des métadonnées pour tRFCs à partir d’un système SAP.</span><span class="sxs-lookup"><span data-stu-id="3b728-106">Refer to [Browse, search, and get metadata for RFC operations in SAP](../../adapters-and-accelerators/adapter-sap/browse-search-and-get-metadata-for-rfc-operations-in-sap.md) for information about using the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] or [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] to browse, search, and retrieve metadata for tRFCs from an SAP system.</span></span>  
  
 <span data-ttu-id="3b728-107">Notez que la [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] met en évidence une opération spéciale **RfcConfirmTransID** sous le **TRFC** nœud.</span><span class="sxs-lookup"><span data-stu-id="3b728-107">Note that the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] surfaces a special operation **RfcConfirmTransID** under the **TRFC** node.</span></span> <span data-ttu-id="3b728-108">L’adaptateur SAP utilise cette opération pour valider les appels tRFC effectués sur le serveur SAP.</span><span class="sxs-lookup"><span data-stu-id="3b728-108">The SAP adapter uses this operation to commit tRFC calls made to the SAP server.</span></span> <span data-ttu-id="3b728-109">Pour plus d’informations sur cette opération, consultez [opérations sur tRFCs dans SAP](../../adapters-and-accelerators/adapter-sap/operations-on-trfcs-in-sap.md).</span><span class="sxs-lookup"><span data-stu-id="3b728-109">For more information about this operation, see [Operations on tRFCs in SAP](../../adapters-and-accelerators/adapter-sap/operations-on-trfcs-in-sap.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b728-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3b728-110">See Also</span></span>  
 [<span data-ttu-id="3b728-111">Obtenir les métadonnées pour les opérations de SAP dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3b728-111">Get Metadata for SAP Operations in Visual Studio</span></span>](../../adapters-and-accelerators/adapter-sap/get-metadata-for-sap-operations-in-visual-studio.md)