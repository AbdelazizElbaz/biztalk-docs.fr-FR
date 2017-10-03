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
# <a name="use-the-data-provider-for-sap-with-ssis"></a>Utiliser le fournisseur de données pour SAP avec SSIS
Vous pouvez utiliser la [!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)] en même temps que SQL Server Integration Services (SSIS) pour importer des données à partir d’un système SAP dans les tables de base de données SQL Server, plat de fichiers ou autres types de destination compatible. Vous pouvez créer un package SSIS qui peut être exécuté pour importer des données à partir d’un système SAP.  
  
 Vous devez utiliser l’Assistant Importation de SQL Server et d’exportation pour importer des données dans la base de données SQL Server. Vous devez fournir une requête pour spécifier les données à importer. Vous pouvez spécifier une requête à l’aide de l’instruction SELECT ou l’instruction EXECQUERY. La requête doit respecter la sémantique de prise en charge par le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]. Pour plus d’informations sur la grammaire pour, sélectionnez une requête pour le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)], consultez [syntaxe pour une instruction SELECT dans SAP](../../adapters-and-accelerators/adapter-sap/syntax-for-a-select-statement-in-sap.md). Pour plus d’informations sur la grammaire d’une instruction EXECQUERY pour le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)], consultez [syntaxe pour une instruction EXECQUERY dans SAP](../../adapters-and-accelerators/adapter-sap/syntax-for-an-execquery-statement-in-sap.md).  
  
 Vous pouvez démarrer l’Assistant Importation/exportation de serveur SQL à partir de SQL Server Management Studio ou à partir d’un projet de Service d’intégration dans Visual Studio. Cette section fournit des instructions sur l’exécution de l’Assistant à partir des interfaces de Management Studio et de Visual Studio.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Importer des données SAP à l’aide de SQL Server Management Studio](../../adapters-and-accelerators/adapter-sap/import-sap-data-using-sql-server-management-studio.md)  
  
-   [Importer des données SAP à l’aide de Visual Studio](../../adapters-and-accelerators/adapter-sap/import-sap-data-using-visual-studio.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Utiliser le fournisseur de données .NET Framework pour mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/use-the-net-framework-data-provider-for-mysap-business-suite.md)