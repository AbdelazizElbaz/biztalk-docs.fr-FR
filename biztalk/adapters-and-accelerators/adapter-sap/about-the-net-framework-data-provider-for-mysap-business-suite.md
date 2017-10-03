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
# <a name="about-the-net-framework-data-provider-for-mysap-business-suite"></a>Sur le fournisseur de données .NET Framework pour mySAP Business Suite
Cette section fournit des informations sur la [!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)] ([!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]) et de ses fonctionnalités. Pour obtenir des instructions sur la façon d’utiliser le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)], consultez [utiliser le fournisseur de données .NET Framework pour mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/use-the-net-framework-data-provider-for-mysap-business-suite.md).  
  
> [!NOTE]
>  Même si vous avez choisi d’installer le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] dans le cadre de la [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] installation, votre [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] est toujours incomplète jusqu'à ce que vous installiez un RFC personnalisé dans le système SAP. Pour obtenir des instructions sur la façon d’installer le RFC personnalisé, consultez [installer les RFC personnalisés pour le fournisseur de données pour SAP](../../adapters-and-accelerators/adapter-sap/install-custom-rfcs-for-the-data-provider-for-sap.md).  
  
 Vous pouvez utiliser la [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] comme suit :  
  
-   Pour écrire un client ADO.NET pour se connecter au système SAP. Le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] présente certaines classes qui vous permettent d’interagir avec le fournisseur.  
  
-   Pour exécuter une requête SELECT sur le système SAP. Le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] utilise le RFC personnalisé pour cette fonctionnalité.  
  
-   Pour exécuter une opération d’exécution sur le système SAP. Vous pouvez utiliser cette opération pour effectuer des requêtes sur le système SAP.  
  
-   Pour exécuter une opération EXECQUERY sur le système SAP. Cette opération vous permet d’exécuter des requêtes qui sont déjà définis dans le système SAP.  
  
-   À son tour, utiliser le [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] DDEX plug-in pour les tables de surface et les modules de la fonction à partir du système SAP. Les noms des objets détectés à partir du système SAP sont écrites dans un fichier de configuration SAPDiscoveredObjects.xml.  
  
-   Pour utiliser le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] avec SQL Server Integration Services (SSIS).  
  
-   Pour utiliser le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] avec SQL Server Reporting Services (SSRS).  
  
 Pour plus d’informations sur l’exécution de ces tâches, consultez [utiliser le fournisseur de données .NET Framework pour mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/use-the-net-framework-data-provider-for-mysap-business-suite.md). Pour plus d’informations sur le RFC personnalisé, le fichier de configuration SAPDiscoveredObjects.xml et les limitations liées à la [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)], consultez les liens suivants.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [RFC personnalisés utilisés par le fournisseur dans SAP](../../adapters-and-accelerators/adapter-sap/custom-rfcs-used-by-the-provider-in-sap.md)  
  
-   [Sur le fichier SAPDiscoveredObjects.xml dans SAP](../../adapters-and-accelerators/adapter-sap/about-the-sapdiscoveredobjects-xml-file-in-sap.md)  
  
-   [Limitations du fournisseur de données .NET Framework pour mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/limitations-of-the-net-framework-data-provider-for-mysap-business-suite.md)