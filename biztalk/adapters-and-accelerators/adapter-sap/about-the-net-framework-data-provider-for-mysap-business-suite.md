---
title: "Sur le fournisseur de données .NET Framework pour mySAP Business Suite | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SSIS
- EXEC query
- SELECT query
- SAPDiscoveredObjects.xml
- SQL Server Integration Services
- .NET Framework Data Provider for mySAP Business Suite
- Data Provider for SAP
- custom RFC
- Visual Studio DDEX plug-in
ms.assetid: 4832f789-c1d8-4c5d-a49d-b1da6b7d4bd4
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cf6b8a1657f0731fc09c4ebc1ef1fa99e0e6ae4b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="about-the-net-framework-data-provider-for-mysap-business-suite"></a><span data-ttu-id="7f749-102">Sur le fournisseur de données .NET Framework pour mySAP Business Suite</span><span class="sxs-lookup"><span data-stu-id="7f749-102">About the .NET Framework Data Provider for mySAP Business Suite</span></span>
<span data-ttu-id="7f749-103">Cette section fournit des informations sur la [!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)] ([!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]) et de ses fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="7f749-103">This section provides information about the [!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)] ([!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]) and its features.</span></span> <span data-ttu-id="7f749-104">Pour obtenir des instructions sur la façon d’utiliser le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)], consultez [utiliser le fournisseur de données .NET Framework pour mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/use-the-net-framework-data-provider-for-mysap-business-suite.md).</span><span class="sxs-lookup"><span data-stu-id="7f749-104">For instructions about how to use the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)], see [Use the .NET Framework Data Provider for mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/use-the-net-framework-data-provider-for-mysap-business-suite.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7f749-105">Même si vous avez choisi d’installer le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] dans le cadre de la [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] installation, votre [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] est toujours incomplète jusqu'à ce que vous installiez un RFC personnalisé dans le système SAP.</span><span class="sxs-lookup"><span data-stu-id="7f749-105">Even if you chose to install the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] as part of the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] installation, your [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] is still incomplete until you install a custom RFC in the SAP system.</span></span> <span data-ttu-id="7f749-106">Pour obtenir des instructions sur la façon d’installer le RFC personnalisé, consultez [installer les RFC personnalisés pour le fournisseur de données pour SAP](../../adapters-and-accelerators/adapter-sap/install-custom-rfcs-for-the-data-provider-for-sap.md).</span><span class="sxs-lookup"><span data-stu-id="7f749-106">For instructions on how to install the custom RFC, see [Install Custom RFCs for the Data Provider for SAP](../../adapters-and-accelerators/adapter-sap/install-custom-rfcs-for-the-data-provider-for-sap.md).</span></span>  
  
 <span data-ttu-id="7f749-107">Vous pouvez utiliser la [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] comme suit :</span><span class="sxs-lookup"><span data-stu-id="7f749-107">You can use the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] in the following ways:</span></span>  
  
-   <span data-ttu-id="7f749-108">Pour écrire un client ADO.NET pour se connecter au système SAP.</span><span class="sxs-lookup"><span data-stu-id="7f749-108">To write an ADO.NET client to connect to the SAP system.</span></span> <span data-ttu-id="7f749-109">Le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] présente certaines classes qui vous permettent d’interagir avec le fournisseur.</span><span class="sxs-lookup"><span data-stu-id="7f749-109">The [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] exposes certain classes that enable you to interface with the provider.</span></span>  
  
-   <span data-ttu-id="7f749-110">Pour exécuter une requête SELECT sur le système SAP.</span><span class="sxs-lookup"><span data-stu-id="7f749-110">To execute a SELECT query on the SAP system.</span></span> <span data-ttu-id="7f749-111">Le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] utilise le RFC personnalisé pour cette fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="7f749-111">The [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] uses the custom RFC for this feature.</span></span>  
  
-   <span data-ttu-id="7f749-112">Pour exécuter une opération d’exécution sur le système SAP.</span><span class="sxs-lookup"><span data-stu-id="7f749-112">To execute an EXEC operation on the SAP system.</span></span> <span data-ttu-id="7f749-113">Vous pouvez utiliser cette opération pour effectuer des requêtes sur le système SAP.</span><span class="sxs-lookup"><span data-stu-id="7f749-113">You can use this operation to perform queries on the SAP system.</span></span>  
  
-   <span data-ttu-id="7f749-114">Pour exécuter une opération EXECQUERY sur le système SAP.</span><span class="sxs-lookup"><span data-stu-id="7f749-114">To execute an EXECQUERY operation on the SAP system.</span></span> <span data-ttu-id="7f749-115">Cette opération vous permet d’exécuter des requêtes qui sont déjà définis dans le système SAP.</span><span class="sxs-lookup"><span data-stu-id="7f749-115">You can use this operation to execute queries that are already defined in the SAP system.</span></span>  
  
-   <span data-ttu-id="7f749-116">À son tour, utiliser le [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] DDEX plug-in pour les tables de surface et les modules de la fonction à partir du système SAP.</span><span class="sxs-lookup"><span data-stu-id="7f749-116">To, in turn, use the [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] DDEX plug-in to surface tables and function modules from the SAP system.</span></span> <span data-ttu-id="7f749-117">Les noms des objets détectés à partir du système SAP sont écrites dans un fichier de configuration SAPDiscoveredObjects.xml.</span><span class="sxs-lookup"><span data-stu-id="7f749-117">The names of the objects discovered from the SAP system are written to a configuration file, SAPDiscoveredObjects.xml.</span></span>  
  
-   <span data-ttu-id="7f749-118">Pour utiliser le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] avec SQL Server Integration Services (SSIS).</span><span class="sxs-lookup"><span data-stu-id="7f749-118">To use the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] with SQL Server Integration Services (SSIS).</span></span>  
  
-   <span data-ttu-id="7f749-119">Pour utiliser le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] avec SQL Server Reporting Services (SSRS).</span><span class="sxs-lookup"><span data-stu-id="7f749-119">To use the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] with SQL Server Reporting Services (SSRS).</span></span>  
  
 <span data-ttu-id="7f749-120">Pour plus d’informations sur l’exécution de ces tâches, consultez [utiliser le fournisseur de données .NET Framework pour mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/use-the-net-framework-data-provider-for-mysap-business-suite.md).</span><span class="sxs-lookup"><span data-stu-id="7f749-120">For more information about performing these tasks, see [Use the .NET Framework Data Provider for mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/use-the-net-framework-data-provider-for-mysap-business-suite.md).</span></span> <span data-ttu-id="7f749-121">Pour plus d’informations sur le RFC personnalisé, le fichier de configuration SAPDiscoveredObjects.xml et les limitations liées à la [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)], consultez les liens suivants.</span><span class="sxs-lookup"><span data-stu-id="7f749-121">For more information about the custom RFC, the SAPDiscoveredObjects.xml configuration file, and the limitations associated with the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)], see the following links.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7f749-122">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="7f749-122">In This Section</span></span>  
  
-   [<span data-ttu-id="7f749-123">RFC personnalisés utilisés par le fournisseur dans SAP</span><span class="sxs-lookup"><span data-stu-id="7f749-123">Custom RFCs Used by the Provider in SAP</span></span>](../../adapters-and-accelerators/adapter-sap/custom-rfcs-used-by-the-provider-in-sap.md)  
  
-   [<span data-ttu-id="7f749-124">Sur le fichier SAPDiscoveredObjects.xml dans SAP</span><span class="sxs-lookup"><span data-stu-id="7f749-124">About the SAPDiscoveredObjects.xml File in SAP</span></span>](../../adapters-and-accelerators/adapter-sap/about-the-sapdiscoveredobjects-xml-file-in-sap.md)  
  
-   [<span data-ttu-id="7f749-125">Limitations du fournisseur de données .NET Framework pour mySAP Business Suite</span><span class="sxs-lookup"><span data-stu-id="7f749-125">Limitations of the .NET Framework Data Provider for mySAP Business Suite</span></span>](../../adapters-and-accelerators/adapter-sap/limitations-of-the-net-framework-data-provider-for-mysap-business-suite.md)