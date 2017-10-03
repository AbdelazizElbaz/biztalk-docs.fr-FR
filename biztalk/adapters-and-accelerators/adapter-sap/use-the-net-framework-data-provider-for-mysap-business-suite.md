---
title: "Utiliser le fournisseur de données .NET Framework pour mySAP Business Suite | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DDEX plug-in
- NET Framework Data Provider for mySAP Business Suite
- function module
- SSIS
- installation
- EXEC query
- SELECT query
- SAPDiscoveredObjects.xml
- SQL Server Integration Services
- Data Provider for SAP
- custom RFC
- installing
- configuration file
ms.assetid: 3abe9c34-b81b-4c0a-9bfd-bf05f89f29b8
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: faa813fa6218d5afcb470406097d745ddf93522b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="use-the-net-framework-data-provider-for-mysap-business-suite"></a><span data-ttu-id="8943f-102">Utiliser le fournisseur de données .NET Framework pour mySAP Business Suite</span><span class="sxs-lookup"><span data-stu-id="8943f-102">Use the .NET Framework Data Provider for mySAP Business Suite</span></span>
<span data-ttu-id="8943f-103">Cette section fournit des instructions sur l’utilisation de la [!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8943f-103">This section provides instructions on using the [!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)].</span></span> <span data-ttu-id="8943f-104">Pour plus d’informations sur le RFC personnalisé utilisé par [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] et les limitations du fournisseur d’informations, consultez [sur le .NET Framework Data Provider pour mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/about-the-net-framework-data-provider-for-mysap-business-suite.md).</span><span class="sxs-lookup"><span data-stu-id="8943f-104">For information about the custom RFC used by [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] and the limitations of the provider see [About the .NET Framework Data Provider for mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/about-the-net-framework-data-provider-for-mysap-business-suite.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8943f-105">Même si vous avez choisi d’installer le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] dans le cadre de la [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] installation, vous devez installer certains RFC personnalisés au niveau du système SAP à utiliser le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8943f-105">Even if you chose to install the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] as part of the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] installation, you must install some custom RFCs at the SAP system to use the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)].</span></span> <span data-ttu-id="8943f-106">Pour obtenir des instructions sur la façon d’installer les RFC personnalisés, consultez [installer les RFC personnalisés pour le fournisseur de données pour SAP](../../adapters-and-accelerators/adapter-sap/install-custom-rfcs-for-the-data-provider-for-sap.md).</span><span class="sxs-lookup"><span data-stu-id="8943f-106">For instructions on how to install the custom RFCs, see [Installing Custom RFCs for the Data Provider for SAP](../../adapters-and-accelerators/adapter-sap/install-custom-rfcs-for-the-data-provider-for-sap.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8943f-107">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="8943f-107">In This Section</span></span>  
  
-   [<span data-ttu-id="8943f-108">Étendre des Interfaces ADO.NET avec l’adaptateur SAP</span><span class="sxs-lookup"><span data-stu-id="8943f-108">Extend ADO.NET Interfaces with the SAP adapter</span></span>](../../adapters-and-accelerators/adapter-sap/extend-ado-net-interfaces-with-the-sap-adapter.md)  
  
-   [<span data-ttu-id="8943f-109">En savoir plus sur les types de fournisseur de données pour la chaîne de connexion SAP</span><span class="sxs-lookup"><span data-stu-id="8943f-109">Read about Data Provider types for the SAP Connection String</span></span>](../../adapters-and-accelerators/adapter-sap/read-about-data-provider-types-for-the-sap-connection-string.md)  
  
-   [<span data-ttu-id="8943f-110">Syntaxe pour une instruction SELECT dans SAP</span><span class="sxs-lookup"><span data-stu-id="8943f-110">Syntax for a SELECT Statement in SAP</span></span>](../../adapters-and-accelerators/adapter-sap/syntax-for-a-select-statement-in-sap.md)  
  
-   [<span data-ttu-id="8943f-111">Syntaxe pour une instruction EXEC dans SAP</span><span class="sxs-lookup"><span data-stu-id="8943f-111">Syntax for an EXEC Statement in SAP</span></span>](../../adapters-and-accelerators/adapter-sap/syntax-for-an-exec-statement-in-sap.md)  
  
-   [<span data-ttu-id="8943f-112">Prise en charge pour l’exécution de requêtes SAP</span><span class="sxs-lookup"><span data-stu-id="8943f-112">Support for Executing SAP Queries</span></span>](https://msdn.microsoft.com/library/dd788118.aspx)  
  
-   [<span data-ttu-id="8943f-113">Appel des RFC et BAPI à l’aide de la commande EXEC dans SAP</span><span class="sxs-lookup"><span data-stu-id="8943f-113">Invoking RFCs and BAPIs by using the EXEC Command in SAP</span></span>](../../adapters-and-accelerators/adapter-sap/invoke-rfcs-and-bapis-using-the-exec-command-in-sap.md)  
  
-   [<span data-ttu-id="8943f-114">Exécution d’une requête à l’aide de la commande SELECT dans SAP</span><span class="sxs-lookup"><span data-stu-id="8943f-114">Performing a Query by using the SELECT Command in SAP</span></span>](../../adapters-and-accelerators/adapter-sap/run-a-query-using-the-select-command-in-sap.md)  
  
-   [<span data-ttu-id="8943f-115">Exécution d’une requête SAP à l’aide de la commande EXECQUERY</span><span class="sxs-lookup"><span data-stu-id="8943f-115">Executing an SAP Query Using the EXECQUERY Command</span></span>](../../adapters-and-accelerators/adapter-sap/execute-an-sap-query-using-the-execquery-command.md)  
  
-   [<span data-ttu-id="8943f-116">À l’aide du fournisseur de données pour SAP avec le plug-in DDEX</span><span class="sxs-lookup"><span data-stu-id="8943f-116">Using the Data Provider for SAP with the DDEX Plug-in</span></span>](../../adapters-and-accelerators/adapter-sap/use-the-data-provider-for-sap-with-the-ddex-plug-in.md)  
  
-   [<span data-ttu-id="8943f-117">À l’aide du fournisseur de données pour SAP avec SSIS</span><span class="sxs-lookup"><span data-stu-id="8943f-117">Using the Data Provider for SAP with SSIS</span></span>](../../adapters-and-accelerators/adapter-sap/use-the-data-provider-for-sap-with-ssis.md)  
  
-   [<span data-ttu-id="8943f-118">À l’aide du fournisseur de données pour SAP avec SSRS</span><span class="sxs-lookup"><span data-stu-id="8943f-118">Using the Data Provider for SAP with SSRS</span></span>](../../adapters-and-accelerators/adapter-sap/use-the-data-provider-for-sap-with-ssrs.md)