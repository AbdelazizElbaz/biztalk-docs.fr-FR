---
title: "Classe SiebelClientFactory dans l’adaptateur Siebel | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SiebelClientFactory
- Data Provider for Siebel, SiebelClientFactory
- SiebelClientFactory, supported properties and methods
ms.assetid: f3a807d3-a030-47d8-b145-e18075ec353c
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 50e47b22c1d5a2575b0da3fae432acd79886e2c3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="siebelclientfactory-class-in-the-siebel-adapter"></a><span data-ttu-id="577a3-102">Classe SiebelClientFactory dans l’adaptateur Siebel</span><span class="sxs-lookup"><span data-stu-id="577a3-102">SiebelClientFactory class in the Siebel adapter</span></span>
<span data-ttu-id="577a3-103">Un client ADO.NET accède à la [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] à l’aide des classes ADO.NET génériques et les interfaces.</span><span class="sxs-lookup"><span data-stu-id="577a3-103">An ADO.NET client accesses the [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] using generic ADO.NET classes and interfaces.</span></span> <span data-ttu-id="577a3-104">Pour activer cette fonctionnalité, le [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] hérite le **System.Data.Common.DbProviderFactory** classe.</span><span class="sxs-lookup"><span data-stu-id="577a3-104">To enable this feature, the [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] inherits the **System.Data.Common.DbProviderFactory** class.</span></span> <span data-ttu-id="577a3-105">Le programme client utilise le client comme suit :</span><span class="sxs-lookup"><span data-stu-id="577a3-105">The client program consumes the client as follows:</span></span>  
  
```  
  
DbProviderFactory factory = DbProviderFactories.GetFactory("Microsoft.Data.SiebelClient");  
DbConnection connection = factory.CreateConnection();  
```  
  
 <span data-ttu-id="577a3-106">Une autre approche est la suivante :</span><span class="sxs-lookup"><span data-stu-id="577a3-106">An alternative approach is as follows:</span></span>  
  
```  
SiebelClientFactory factory = SiebelClientFactory.Instance;  
DbConnection connection = factory.CreateConnection();  
```  
  
 <span data-ttu-id="577a3-107">SiebelClientFactory existe dans l’espace de noms Microsoft.Data.SiebelClient.</span><span class="sxs-lookup"><span data-stu-id="577a3-107">SiebelClientFactory exists in the namespace Microsoft.Data.SiebelClient.</span></span>  
  
## <a name="supported-members"></a><span data-ttu-id="577a3-108">Membres pris en charge</span><span class="sxs-lookup"><span data-stu-id="577a3-108">Supported Members</span></span>  
 <span data-ttu-id="577a3-109">**SiebelClientFactory** étend **System.Data.CommonDbProviderFactory**.</span><span class="sxs-lookup"><span data-stu-id="577a3-109">**SiebelClientFactory** extends **System.Data.CommonDbProviderFactory**.</span></span>  <span data-ttu-id="577a3-110">Le tableau suivant fournit une description des membres qui **SiebelClientFactory** substitue.</span><span class="sxs-lookup"><span data-stu-id="577a3-110">The following table provides a description of the members that **SiebelClientFactory** overrides.</span></span>  
  
|<span data-ttu-id="577a3-111">Nom</span><span class="sxs-lookup"><span data-stu-id="577a3-111">Name</span></span>|<span data-ttu-id="577a3-112"> Description</span><span class="sxs-lookup"><span data-stu-id="577a3-112">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="577a3-113">**Instance**</span><span class="sxs-lookup"><span data-stu-id="577a3-113">**Instance**</span></span>|<span data-ttu-id="577a3-114">Il s’agit d’une variable membre.</span><span class="sxs-lookup"><span data-stu-id="577a3-114">This is a member variable.</span></span>  <span data-ttu-id="577a3-115">Il fournit une instance singleton de SiebelClientFactory.</span><span class="sxs-lookup"><span data-stu-id="577a3-115">It provides a singleton instance of SiebelClientFactory.</span></span>|  
|<span data-ttu-id="577a3-116">**CreateCommand()**</span><span class="sxs-lookup"><span data-stu-id="577a3-116">**CreateCommand()**</span></span>|<span data-ttu-id="577a3-117">Crée une instance de SiebelCommand.</span><span class="sxs-lookup"><span data-stu-id="577a3-117">Creates an instance of SiebelCommand.</span></span>|  
|<span data-ttu-id="577a3-118">**CreateConnection()**</span><span class="sxs-lookup"><span data-stu-id="577a3-118">**CreateConnection()**</span></span>|<span data-ttu-id="577a3-119">Crée une instance de SiebelConnection.</span><span class="sxs-lookup"><span data-stu-id="577a3-119">Creates an instance of SiebelConnection.</span></span>|  
|<span data-ttu-id="577a3-120">**CreateConnectionStringBuilder()**</span><span class="sxs-lookup"><span data-stu-id="577a3-120">**CreateConnectionStringBuilder()**</span></span>|<span data-ttu-id="577a3-121">Crée une instance de SiebelConnectionStringBuilder.</span><span class="sxs-lookup"><span data-stu-id="577a3-121">Creates an instance of SiebelConnectionStringBuilder.</span></span>|  
|<span data-ttu-id="577a3-122">**CreateParameter()**</span><span class="sxs-lookup"><span data-stu-id="577a3-122">**CreateParameter()**</span></span>|<span data-ttu-id="577a3-123">Crée une instance de SiebelParameter.</span><span class="sxs-lookup"><span data-stu-id="577a3-123">Creates an instance of SiebelParameter.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="577a3-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="577a3-124">See Also</span></span>  
 [<span data-ttu-id="577a3-125">Étendre des Interfaces ADO.NET avec l’adaptateur Siebel</span><span class="sxs-lookup"><span data-stu-id="577a3-125">Extend ADO.NET Interfaces with the Siebel adapter</span></span>](../../adapters-and-accelerators/adapter-siebel/extend-ado-net-interfaces-with-the-siebel-adapter.md)