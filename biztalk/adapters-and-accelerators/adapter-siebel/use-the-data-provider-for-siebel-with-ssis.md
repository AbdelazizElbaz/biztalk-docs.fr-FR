---
title: "Utiliser le fournisseur de données pour Siebel avec SSIS | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SSIS
- SQL Server Integration Services
- Data Provider for Siebel, using with SSIS
ms.assetid: e72cecf2-6c05-4df7-8e6e-aff3a9df8b79
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a0c46c1437d7eeedd56ee37b054f9f6eb6b72ada
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="use-the-data-provider-for-siebel-with-ssis"></a><span data-ttu-id="b1246-102">Utiliser le fournisseur de données pour Siebel avec SSIS</span><span class="sxs-lookup"><span data-stu-id="b1246-102">Use the Data Provider for Siebel with SSIS</span></span>
<span data-ttu-id="b1246-103">Vous pouvez utiliser la [!INCLUDE[adoprovidersiebellong](../../includes/adoprovidersiebellong-md.md)] ([!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]) en même temps que SQL Server Integration Services (SSIS) pour importer des données dans des tables de base de données SQL Server à partir d’un système Siebel, plat de fichiers ou autres types de destination compatible.</span><span class="sxs-lookup"><span data-stu-id="b1246-103">You can use the [!INCLUDE[adoprovidersiebellong](../../includes/adoprovidersiebellong-md.md)] ([!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]) along with SQL Server Integration Services (SSIS) to import data from a Siebel system into SQL Server database tables, flat files, or other compatible destination types.</span></span> <span data-ttu-id="b1246-104">Plus précisément, vous pouvez créer un package SSIS qui peut être exécuté pour importer ces données.</span><span class="sxs-lookup"><span data-stu-id="b1246-104">Specifically, you can create an SSIS package that can be executed to import this data.</span></span>  
  
 <span data-ttu-id="b1246-105">Pour importer des données dans la base de données SQL Server, utilisez le SQL Server Assistant Importation et exportation et fournir une requête SELECT pour spécifier les données à importer.</span><span class="sxs-lookup"><span data-stu-id="b1246-105">To import data into the SQL Server database, use the SQL Server Import and Export Wizard, and provide a SELECT query to specify the data to be imported.</span></span> <span data-ttu-id="b1246-106">La requête doit respecter la sémantique de prise en charge par le [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b1246-106">The query must confirm to the semantics supported by the [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)].</span></span> <span data-ttu-id="b1246-107">Pour plus d’informations sur la grammaire pour, sélectionnez une requête pour le [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)], consultez [syntaxe pour une instruction SELECT dans Siebel](../../adapters-and-accelerators/adapter-siebel/syntax-for-a-select-statement-in-siebel.md).</span><span class="sxs-lookup"><span data-stu-id="b1246-107">For more information about the grammar for a SELECT query for the [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)], see [Syntax for a SELECT Statement in Siebel](../../adapters-and-accelerators/adapter-siebel/syntax-for-a-select-statement-in-siebel.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b1246-108">Le [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] ne prend pas en charge à l’aide d’une instruction EXEC avec SSIS.</span><span class="sxs-lookup"><span data-stu-id="b1246-108">The [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] does not support using an EXEC statement with SSIS.</span></span>  
  
 <span data-ttu-id="b1246-109">Vous pouvez démarrer l’Assistant Importation de SQL Server et l’exportation à partir de SQL Server Management Studio ou à partir d’un projet de Service d’intégration dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b1246-109">You can start the SQL Server Import and Export wizard either from the SQL Server Management Studio or from an Integration Service project in Visual Studio.</span></span> <span data-ttu-id="b1246-110">Cette section fournit des instructions sur l’exécution de l’Assistant à partir des interfaces de SQL Server Management Studio et de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b1246-110">This section provides instructions on running the wizard from both the SQL Server Management Studio and Visual Studio interfaces.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b1246-111">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="b1246-111">In This Section</span></span>  
  
-   [<span data-ttu-id="b1246-112">Importer des données Siebel à l’aide de SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="b1246-112">Import Siebel Data Using SQL Server Management Studio</span></span>](../../adapters-and-accelerators/adapter-siebel/import-siebel-data-using-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="b1246-113">Importer des données Siebel à l’aide de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b1246-113">Import Siebel Data Using Visual Studio</span></span>](../../adapters-and-accelerators/adapter-siebel/import-siebel-data-using-visual-studio.md)  
  
## <a name="see-also"></a><span data-ttu-id="b1246-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b1246-114">See Also</span></span>  
 [<span data-ttu-id="b1246-115">Utiliser le fournisseur de données .NET Framework pour Siebel eBusiness Applications</span><span class="sxs-lookup"><span data-stu-id="b1246-115">Use the .NET Framework Data Provider for Siebel eBusiness Applications</span></span>](../../adapters-and-accelerators/adapter-siebel/use-the-net-framework-data-provider-for-siebel-ebusiness-applications.md)