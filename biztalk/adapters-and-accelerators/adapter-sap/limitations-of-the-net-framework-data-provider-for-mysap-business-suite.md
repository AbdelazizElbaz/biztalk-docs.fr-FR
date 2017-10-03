---
title: "Limitations du fournisseur de données .NET Framework pour mySAP Business Suite | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Data Provider for SAP, limitations of
- .NET Framework Data Provider for mySAP Business Suite, limitations of
ms.assetid: 462e627d-41da-4456-bc62-e8cf7296f5b4
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5fd4ad3a57e2b762a53582ceb77eb65f23a535fc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="limitations-of-the-net-framework-data-provider-for-mysap-business-suite"></a>Limitations du fournisseur de données .NET Framework pour mySAP Business Suite
Les éléments suivants sont connus des limitations de la [!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)] ([!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]) :  
  
-   Le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] ne prend pas en charge la connexion à un système SAP à l’aide de la connexion de réseau sécurisée (SNC). Pour plus d’informations sur SNC, consultez [sécurité entre le système SAP et la carte](../../adapters-and-accelerators/adapter-sap/security-between-the-sap-system-and-the-adapter.md).
  
-   Le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] ne prend pas en charge la `DbType` ou `Size` propriétés de la `SAPParameter`. Au lieu de cela, lorsque l’utilisateur spécifie une valeur pour le `SAPParameter`, la valeur est effectuée en interne pour un type de données .NET selon le mappage établi entre les types de données .NET et SAP.  
  
-   La longueur maximale autorisée pour les valeurs de champ de types de données SAP `CURR`, `DEC`, et `QUAN` est 29 chiffres. Bien que SAP fournit les 31 emplacements pour ces valeurs de type de données en mode natif, le type de données decimal .NET dans lequel ils sont convertis impose une limite de 29 chiffres.  
  
-   Une limitation de mappage entre le type de données .NET `Double` et SAP `FLTP` type de données peut provoquer une erreur de dépassement de capacité lors de la lecture des données à partir du système SAP dans le type .NET. Bien que le type .NET peut représenter un nombre de 64 bits double précision avec des valeurs allant de moins 1, 79769313486232E308 à plus 1, 79769313486232E308, un SAP `FLTP` type analysé par le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] ne peut pas dépasser 1.8446744073709552E + 19 ; la limite effective pour le `FLTP` type correspond à la plage négative 1.8446744073709552E + 19 1.8446744073709552E + 19 positif.  
  
-   En raison de problèmes de délai d’attente un traitement par la bibliothèque cliente sous-jacente, le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] ne prend pas en charge le délai d’attente de connexion et de commande.  
  
-   Le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] ne prend pas en charge le comportement asynchrone de la commande.  
  
-   Lorsqu’il est utilisé avec un projet SQL Server Integration Services (SSIS), le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] ne parvient pas à récupérer des données pour les colonnes qui contiennent des valeurs avec plus de 8 000 caractères. Il s’agit en raison d’une restriction SSIS en fonction desquelles :  
  
    -   Les valeurs supérieures à 4 000 caractères dans la variable SSIS ne sont pas pris en charge.  
  
    -   Les valeurs supérieures à 4 000 caractères larges ne sont pas pris en charge.  
  
    -   Les valeurs supérieures à 8 000 caractères codés sur un octet ne sont pas pris en charge.  
  
## <a name="see-also"></a>Voir aussi  
 [Sur le fournisseur de données .NET Framework pour mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/about-the-net-framework-data-provider-for-mysap-business-suite.md)