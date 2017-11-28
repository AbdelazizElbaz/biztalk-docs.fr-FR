---
title: "Utiliser le fournisseur de données .NET Framework pour Siebel eBusiness Applications | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ADO.NET programming, performing operations
- Data Provider for Siebel, overview
ms.assetid: 97fe4f95-c9ae-42f1-a159-1b0e98607b31
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5acb8f96add3dcde48456751d82dc2a8e00ffe43
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="use-the-net-framework-data-provider-for-siebel-ebusiness-applications"></a><span data-ttu-id="ea556-102">Utiliser le fournisseur de données .NET Framework pour Siebel eBusiness Applications</span><span class="sxs-lookup"><span data-stu-id="ea556-102">Use the .NET Framework Data Provider for Siebel eBusiness Applications</span></span>
<span data-ttu-id="ea556-103">Cette section fournit des instructions sur l’utilisation de la [!INCLUDE[adoprovidersiebellong](../../includes/adoprovidersiebellong-md.md)] ([!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]).</span><span class="sxs-lookup"><span data-stu-id="ea556-103">This section provides instructions on using the [!INCLUDE[adoprovidersiebellong](../../includes/adoprovidersiebellong-md.md)] ([!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]).</span></span> <span data-ttu-id="ea556-104">Cette section fournit des informations sur :</span><span class="sxs-lookup"><span data-stu-id="ea556-104">This section provides information about:</span></span>  
  
-   <span data-ttu-id="ea556-105">La chaîne de connexion pour se connecter à un système Siebel à l’aide d’un client d’ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="ea556-105">The connection string to connect to a Siebel system using an ADO.NET client.</span></span>  
  
-   <span data-ttu-id="ea556-106">La syntaxe pour les instructions SELECT et EXEC.</span><span class="sxs-lookup"><span data-stu-id="ea556-106">The syntax for SELECT and EXEC statements.</span></span>  
  
-   <span data-ttu-id="ea556-107">À l’aide de la [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] avec SSIS.</span><span class="sxs-lookup"><span data-stu-id="ea556-107">Using the [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] with SSIS.</span></span>  
  
-   <span data-ttu-id="ea556-108">Les interfaces ADO.NET que le [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] étend.</span><span class="sxs-lookup"><span data-stu-id="ea556-108">The ADO.NET interfaces that the [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] extends.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ea556-109">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="ea556-109">In This Section</span></span>  
  
-   [<span data-ttu-id="ea556-110">Étendre des Interfaces ADO.NET avec l’adaptateur Siebel</span><span class="sxs-lookup"><span data-stu-id="ea556-110">Extend ADO.NET Interfaces with the Siebel adapter</span></span>](../../adapters-and-accelerators/adapter-siebel/extend-ado-net-interfaces-with-the-siebel-adapter.md)  
  
-   [<span data-ttu-id="ea556-111">Propriétés de fournisseur de données pour la chaîne de connexion de Siebel</span><span class="sxs-lookup"><span data-stu-id="ea556-111">Data Provider properties for the Siebel Connection String</span></span>](../../adapters-and-accelerators/adapter-siebel/data-provider-properties-for-the-siebel-connection-string.md)  
  
-   [<span data-ttu-id="ea556-112">Syntaxe pour une instruction SELECT dans Siebel</span><span class="sxs-lookup"><span data-stu-id="ea556-112">Syntax for a SELECT Statement in Siebel</span></span>](../../adapters-and-accelerators/adapter-siebel/syntax-for-a-select-statement-in-siebel.md)  
  
-   [<span data-ttu-id="ea556-113">Syntaxe pour une instruction EXEC dans Siebel</span><span class="sxs-lookup"><span data-stu-id="ea556-113">Syntax for an EXEC Statement in Siebel</span></span>](../../adapters-and-accelerators/adapter-siebel/syntax-for-an-exec-statement-in-siebel.md)  
  
-   [<span data-ttu-id="ea556-114">Exécutez une requête SELECT sur les composants d’entreprise Siebel</span><span class="sxs-lookup"><span data-stu-id="ea556-114">Run a SELECT Query on Business Components with Siebel</span></span>](../../adapters-and-accelerators/adapter-siebel/run-a-select-query-on-business-components-with-siebel.md)  
  
-   [<span data-ttu-id="ea556-115">Exécuter une opération d’exécution sur les Services avec Siebel</span><span class="sxs-lookup"><span data-stu-id="ea556-115">Run an EXECUTE Operation on Business Services with Siebel</span></span>](../../adapters-and-accelerators/adapter-siebel/run-an-execute-operation-on-business-services-with-siebel.md)  
  
-   [<span data-ttu-id="ea556-116">Utiliser le fournisseur de données pour Siebel avec SSIS</span><span class="sxs-lookup"><span data-stu-id="ea556-116">Use the Data Provider for Siebel with SSIS</span></span>](../../adapters-and-accelerators/adapter-siebel/use-the-data-provider-for-siebel-with-ssis.md)