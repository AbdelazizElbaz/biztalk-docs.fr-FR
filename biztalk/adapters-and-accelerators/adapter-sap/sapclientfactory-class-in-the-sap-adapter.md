---
title: Classe SAPClientFactory dans l’adaptateur SAP | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SAPClientFactory, supported methods and classes
ms.assetid: e64de5e4-e53f-4708-ab02-9e12774e94cd
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3c82e4bea6a16085608ebf1f8fe10ea95b4db394
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="sapclientfactory-class-in-the-sap-adapter"></a><span data-ttu-id="82862-102">Classe SAPClientFactory dans l’adaptateur SAP</span><span class="sxs-lookup"><span data-stu-id="82862-102">SAPClientFactory class in the SAP adapter</span></span>
<span data-ttu-id="82862-103">La section suivante répertorie les méthodes et propriétés pour le **SAPClientFactory** classe.</span><span class="sxs-lookup"><span data-stu-id="82862-103">The following section lists the methods and properties for the **SAPClientFactory** class.</span></span> <span data-ttu-id="82862-104">Elle est dérivée de **System.Data.Common.DbProviderFactory**.</span><span class="sxs-lookup"><span data-stu-id="82862-104">This is derived from **System.Data.Common.DbProviderFactory**.</span></span>  
  
## <a name="supported-properties"></a><span data-ttu-id="82862-105">Propriétés prises en charge</span><span class="sxs-lookup"><span data-stu-id="82862-105">Supported Properties</span></span>  
  
|<span data-ttu-id="82862-106">Nom</span><span class="sxs-lookup"><span data-stu-id="82862-106">Name</span></span>|<span data-ttu-id="82862-107">Get/Set.</span><span class="sxs-lookup"><span data-stu-id="82862-107">Get/Set</span></span>|<span data-ttu-id="82862-108"> Description</span><span class="sxs-lookup"><span data-stu-id="82862-108">Description</span></span>|  
|----------|--------------|-----------------|  
|<span data-ttu-id="82862-109">**Instance**</span><span class="sxs-lookup"><span data-stu-id="82862-109">**Instance**</span></span>|-|<span data-ttu-id="82862-110">Instance singleton de SAPClientFactory</span><span class="sxs-lookup"><span data-stu-id="82862-110">Singleton instance of SAPClientFactory</span></span>|  
  
## <a name="supported-methods"></a><span data-ttu-id="82862-111">Méthodes prises en charge</span><span class="sxs-lookup"><span data-stu-id="82862-111">Supported Methods</span></span>  
  
|<span data-ttu-id="82862-112">Nom</span><span class="sxs-lookup"><span data-stu-id="82862-112">Name</span></span>|<span data-ttu-id="82862-113"> Description</span><span class="sxs-lookup"><span data-stu-id="82862-113">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="82862-114">**CreateCommand()**</span><span class="sxs-lookup"><span data-stu-id="82862-114">**CreateCommand()**</span></span>|<span data-ttu-id="82862-115">Crée une instance de SAPCommand</span><span class="sxs-lookup"><span data-stu-id="82862-115">Creates an instance of SAPCommand</span></span>|  
|<span data-ttu-id="82862-116">**CreateConnection()**</span><span class="sxs-lookup"><span data-stu-id="82862-116">**CreateConnection()**</span></span>|<span data-ttu-id="82862-117">Crée une instance de SAPConnection</span><span class="sxs-lookup"><span data-stu-id="82862-117">Creates an instance of SAPConnection</span></span>|  
|<span data-ttu-id="82862-118">**CreateConnectionStringBuilder()**</span><span class="sxs-lookup"><span data-stu-id="82862-118">**CreateConnectionStringBuilder()**</span></span>|<span data-ttu-id="82862-119">Crée une instance de SAPConnectionStringBuilder</span><span class="sxs-lookup"><span data-stu-id="82862-119">Creates an instance of SAPConnectionStringBuilder</span></span>|  
|<span data-ttu-id="82862-120">**CreateParameter()**</span><span class="sxs-lookup"><span data-stu-id="82862-120">**CreateParameter()**</span></span>|<span data-ttu-id="82862-121">Crée une instance de l’objet SAPParameter</span><span class="sxs-lookup"><span data-stu-id="82862-121">Creates an instance of SAPParameter</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="82862-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="82862-122">See Also</span></span>  
 [<span data-ttu-id="82862-123">Étendre des Interfaces ADO.NET avec l’adaptateur SAP</span><span class="sxs-lookup"><span data-stu-id="82862-123">Extend ADO.NET Interfaces with the SAP adapter</span></span>](../../adapters-and-accelerators/adapter-sap/extend-ado-net-interfaces-with-the-sap-adapter.md)