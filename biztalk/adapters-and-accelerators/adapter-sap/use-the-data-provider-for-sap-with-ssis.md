---
title: "Utiliser le fournisseur de données pour SAP avec SSIS | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Data Provider for SAP, using with SSIS
- SSIS, Data Provider for SAP
ms.assetid: e8c50cc1-ac25-4993-9aee-7fd88268d65d
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a8459453e153626b6a79a5dc5f57ce041ba67d1d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="use-the-data-provider-for-sap-with-ssis"></a><span data-ttu-id="8f57c-102">Utiliser le fournisseur de données pour SAP avec SSIS</span><span class="sxs-lookup"><span data-stu-id="8f57c-102">Use the Data Provider for SAP with SSIS</span></span>
<span data-ttu-id="8f57c-103">Vous pouvez utiliser la [!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)] en même temps que SQL Server Integration Services (SSIS) pour importer des données à partir d’un système SAP dans les tables de base de données SQL Server, plat de fichiers ou autres types de destination compatible.</span><span class="sxs-lookup"><span data-stu-id="8f57c-103">You can use the [!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)] along with SQL Server Integration Service (SSIS) to import data from an SAP system into SQL Server database tables, flat files, or other compatible destination types.</span></span> <span data-ttu-id="8f57c-104">Vous pouvez créer un package SSIS qui peut être exécuté pour importer des données à partir d’un système SAP.</span><span class="sxs-lookup"><span data-stu-id="8f57c-104">You can create an SSIS package that can be executed to import data from an SAP system.</span></span>  
  
 <span data-ttu-id="8f57c-105">Vous devez utiliser l’Assistant Importation de SQL Server et d’exportation pour importer des données dans la base de données SQL Server.</span><span class="sxs-lookup"><span data-stu-id="8f57c-105">You must use the SQL Server Import and Export wizard to import data into the SQL Server database.</span></span> <span data-ttu-id="8f57c-106">Vous devez fournir une requête pour spécifier les données à importer.</span><span class="sxs-lookup"><span data-stu-id="8f57c-106">You must provide a query to specify data to be imported.</span></span> <span data-ttu-id="8f57c-107">Vous pouvez spécifier une requête à l’aide de l’instruction SELECT ou l’instruction EXECQUERY.</span><span class="sxs-lookup"><span data-stu-id="8f57c-107">You can specify a query using the SELECT statement or the EXECQUERY statement.</span></span> <span data-ttu-id="8f57c-108">La requête doit respecter la sémantique de prise en charge par le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8f57c-108">The query must confirm to the semantics supported by the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)].</span></span> <span data-ttu-id="8f57c-109">Pour plus d’informations sur la grammaire pour, sélectionnez une requête pour le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)], consultez [syntaxe pour une instruction SELECT dans SAP](../../adapters-and-accelerators/adapter-sap/syntax-for-a-select-statement-in-sap.md).</span><span class="sxs-lookup"><span data-stu-id="8f57c-109">For more information about the grammar for a SELECT query for the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)], see [Syntax for a SELECT Statement in SAP](../../adapters-and-accelerators/adapter-sap/syntax-for-a-select-statement-in-sap.md).</span></span> <span data-ttu-id="8f57c-110">Pour plus d’informations sur la grammaire d’une instruction EXECQUERY pour le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)], consultez [syntaxe pour une instruction EXECQUERY dans SAP](../../adapters-and-accelerators/adapter-sap/syntax-for-an-execquery-statement-in-sap.md).</span><span class="sxs-lookup"><span data-stu-id="8f57c-110">For more information about the grammar for an EXECQUERY statement for the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)], see [Syntax for an EXECQUERY Statement in SAP](../../adapters-and-accelerators/adapter-sap/syntax-for-an-execquery-statement-in-sap.md).</span></span>  
  
 <span data-ttu-id="8f57c-111">Vous pouvez démarrer l’Assistant Importation/exportation de serveur SQL à partir de SQL Server Management Studio ou à partir d’un projet de Service d’intégration dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8f57c-111">You can start the SQL Server Import Export wizard either from the SQL Server Management Studio or from an Integration Service project in Visual Studio.</span></span> <span data-ttu-id="8f57c-112">Cette section fournit des instructions sur l’exécution de l’Assistant à partir des interfaces de Management Studio et de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8f57c-112">This section provides instructions on running the wizard from both the Management Studio and Visual Studio interfaces.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8f57c-113">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="8f57c-113">In This Section</span></span>  
  
-   [<span data-ttu-id="8f57c-114">Importer des données SAP à l’aide de SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="8f57c-114">Import SAP Data Using SQL Server Management Studio</span></span>](../../adapters-and-accelerators/adapter-sap/import-sap-data-using-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="8f57c-115">Importer des données SAP à l’aide de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="8f57c-115">Import SAP Data Using Visual Studio</span></span>](../../adapters-and-accelerators/adapter-sap/import-sap-data-using-visual-studio.md)  
  
## <a name="see-also"></a><span data-ttu-id="8f57c-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8f57c-116">See Also</span></span>  
 [<span data-ttu-id="8f57c-117">Utiliser le fournisseur de données .NET Framework pour mySAP Business Suite</span><span class="sxs-lookup"><span data-stu-id="8f57c-117">Use the .NET Framework Data Provider for mySAP Business Suite</span></span>](../../adapters-and-accelerators/adapter-sap/use-the-net-framework-data-provider-for-mysap-business-suite.md)