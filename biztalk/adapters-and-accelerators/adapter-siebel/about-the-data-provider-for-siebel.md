---
title: Sur le fournisseur de données pour Siebel | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Data Provider for Siebel, overview
ms.assetid: 461fe4d8-75f2-49d5-9fc2-3baab4ccf13f
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 81cac425bf1671166b4f40cecae3e1a3aca1c8e5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="about-the-data-provider-for-siebel"></a>Sur le fournisseur de données pour Siebel
## <a name="overview"></a>Vue d'ensemble
Le [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] repose sur le [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)]. Vous pouvez utiliser le [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] à :  
  
-   Écrire un client ADO.NET pour se connecter au système Siebel. Le [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] présente certaines classes qui vous permettent d’interagir avec le fournisseur.  
  
-   Exécutez une requête SELECT sur un composant d’entreprise Siebel
  
-   Exécuter une requête EXEC sur un service d’entreprise Siebel
  
-   Utilisez le [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] avec SQL Server Integration Services (SSIS)
  
[Utiliser le fournisseur de données .NET Framework pour Siebel eBusiness Applications](../../adapters-and-accelerators/adapter-siebel/use-the-net-framework-data-provider-for-siebel-ebusiness-applications.md) est un bon point de départ pour plus d’informations sur :  
  
-   Les interfaces ADO.NET étendu par le[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]  
  
-   La chaîne de connexion pour se connecter à un système Siebel  
  
-   Syntaxe des instructions SELECT et EXEC  
  
-   À l’aide de la [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] avec SSIS  
  
## <a name="limitations"></a>Limitations
Les éléments suivants sont connus des limitations de la [!INCLUDE[adoprovidersiebellong](../../includes/adoprovidersiebellong-md.md)]:  
  
-   Le [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] prend en charge les alias noms pour les tables dans la clause SELECT, mais pas dans la clause WHERE.  
  
-   Le [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] ne parvient pas à créer une table avec les noms de colonnes qui ont le caractère spécial, «] ». Vous pouvez ignorer le caractère spécial en incluant un autre crochet fermant. Par conséquent, vous devez inclure »]] » au lieu de «] ».  
  
-   En raison de problèmes de délai d’attente un traitement par le client Siebel sous-jacent API, le [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] ne prend pas en charge le délai d’attente de connexion et de commande.  
  
-   Le [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] ne prend pas en charge le comportement asynchrone de la commande.  
  
-   Lorsqu’il est utilisé avec un projet SQL Server Integration Services (SSIS), le [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] ne parvient pas à récupérer des données pour les colonnes qui contiennent des valeurs avec plus de 8 000 caractères. Il s’agit en raison d’une restriction SSIS en fonction desquelles :  
  
    -   Les valeurs supérieures à 4 000 caractères dans la variable SSIS ne sont pas pris en charge.  
  
    -   Les valeurs supérieures à 4 000 caractères larges ne sont pas pris en charge.  
  
    -   Les valeurs supérieures à 8 000 caractères codés sur un octet ne sont pas pris en charge.  
  
-   L’opération EXEC ne sera pas fonctionnelle lors de l’utilisation du [!INCLUDE[adoprovidersiebellong](../../includes/adoprovidersiebellong-md.md)] avec SQL Server Integration Services (SSIS). Par exemple, les clients de l’adaptateur ne pourra donc en mesure d’exécuter un service d’entreprise dans Siebel (à l’aide de [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]) tout en utilisant les fournisseurs de données avec SSIS. 

## <a name="see-also"></a>Voir aussi
[Limitations de l’adaptateur Siebel](../../adapters-and-accelerators/adapter-siebel/limitations-of-biztalk-adapter-for-siebel-ebusiness-applications.md)  
[Dépanner l’adaptateur Siebel](../../adapters-and-accelerators/adapter-siebel/troubleshoot-the-siebel-adapter.md)