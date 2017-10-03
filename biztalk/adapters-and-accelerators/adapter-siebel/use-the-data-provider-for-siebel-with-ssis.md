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
# <a name="use-the-data-provider-for-siebel-with-ssis"></a>Utiliser le fournisseur de données pour Siebel avec SSIS
Vous pouvez utiliser la [!INCLUDE[adoprovidersiebellong](../../includes/adoprovidersiebellong-md.md)] ([!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]) en même temps que SQL Server Integration Services (SSIS) pour importer des données dans des tables de base de données SQL Server à partir d’un système Siebel, plat de fichiers ou autres types de destination compatible. Plus précisément, vous pouvez créer un package SSIS qui peut être exécuté pour importer ces données.  
  
 Pour importer des données dans la base de données SQL Server, utilisez le SQL Server Assistant Importation et exportation et fournir une requête SELECT pour spécifier les données à importer. La requête doit respecter la sémantique de prise en charge par le [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]. Pour plus d’informations sur la grammaire pour, sélectionnez une requête pour le [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)], consultez [syntaxe pour une instruction SELECT dans Siebel](../../adapters-and-accelerators/adapter-siebel/syntax-for-a-select-statement-in-siebel.md).  
  
> [!NOTE]
>  Le [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] ne prend pas en charge à l’aide d’une instruction EXEC avec SSIS.  
  
 Vous pouvez démarrer l’Assistant Importation de SQL Server et l’exportation à partir de SQL Server Management Studio ou à partir d’un projet de Service d’intégration dans Visual Studio. Cette section fournit des instructions sur l’exécution de l’Assistant à partir des interfaces de SQL Server Management Studio et de Visual Studio.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Importer des données Siebel à l’aide de SQL Server Management Studio](../../adapters-and-accelerators/adapter-siebel/import-siebel-data-using-sql-server-management-studio.md)  
  
-   [Importer des données Siebel à l’aide de Visual Studio](../../adapters-and-accelerators/adapter-siebel/import-siebel-data-using-visual-studio.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Utiliser le fournisseur de données .NET Framework pour Siebel eBusiness Applications](../../adapters-and-accelerators/adapter-siebel/use-the-net-framework-data-provider-for-siebel-ebusiness-applications.md)