---
title: "Planifier les performances de la base de données | Documents Microsoft"
ms.custom: 
ms.date: 11/29/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7212fa37-88e0-4b5f-af97-c72063357645
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 878320cf7c6a5762626087964033430afcf611cf
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="planning-for-database-performance"></a>Planification des performances de la base de données

## <a name="overview"></a>Vue d'ensemble
Microsoft BizTalk Server est extrêmement de base de données applications exigeantes qui peuvent nécessiter la création de bases de données distinctes jusqu'à 13 dans Microsoft SQL Server. En raison de la base de données intensif de BizTalk Server, il est essentiel que vous choisissez la version appropriée et l’édition de SQL Server qui hébergera les bases de données BizTalk Server. Pour optimiser les performances des ordinateurs exécutant SQL Server qui hébergent les bases de données BizTalk Server, suivez les recommandations dans cette rubrique et dans le [l’optimisation de base de données BizTalk Server](optimizing-database-performance.md).
  

> [!NOTE]  
>  Alors que ce guide est écrit pour d’autres versions de BizTalk Server et SQL Server, vous pouvez probablement utiliser les mêmes recommandations pour les versions plus récentes.
  
## <a name="considerations-for-sql-server-editions"></a>Considérations pour les éditions de SQL Server  
 Bases de données BizTalk Server doivent être configurés pour s’exécuter sur une instance dédiée de SQL Server chaque fois que possible. BizTalk Server est une application qui consommée beaucoup de base de données, de la sorte que la séparation des ordinateurs BizTalk Server et les ordinateurs SQL Server qui hébergent les bases de données BizTalk Server améliorent les performances et doivent être considérée comme une meilleure pratique dans une production BizTalk Server environnement.  
  
 Différentes éditions de SQL Server fournissent des fonctionnalités différentes, ce qui peuvent affecter les performances de votre environnement BizTalk Server. Par exemple, dans des conditions de forte charge, le nombre de verrous disponibles de la base de données qui sont disponibles pour la version 32 bits de SQL Server peut être dépassé, c'est-à-dire nuit aux performances de la solution BizTalk. Envisagez d’héberger votre base de données MessageBox sur une version 64 bits de SQL Server si vous rencontrez des erreurs « insuffisant de verrous » dans votre environnement de test. Le nombre de verrous disponibles est nettement supérieur sur cette version.  
  
 Envisagez le tableau ci-dessous lorsque vous choisissez le moteur de base de données des fonctionnalités que vous avez besoin pour votre environnement BizTalk. Pour les solutions à petite échelle, par exemple lors de l’exécution de BizTalk Server Édition branche, SQL Server Workgroup Edition peut convenir pour héberger les bases de données BizTalk Server. Pour les solutions au niveau de l’entreprise qui requièrent la prise en charge, de clustering à grande échelle de BizTalk journal envoi de journaux de prise en charge ou prise en charge d’Analysis Services, vous avez besoin de SQL Server Enterprise Edition pour héberger les bases de données.  
  
|Édition de SQL Server|prise en charge 64 bits|Prise en charge de plusieurs instances|Prise en charge le clustering|Analysis Services|  
|---|---|---|---|---|  
|SQL Server Enterprise Edition|Oui|Oui|Oui|Oui|  
|SQL Server Standard Edition|Oui|Oui|Oui (nœud 2)|Oui|  
|SQL Server Workgroup Edition|Oui|Oui|Non|Non|  
  
> [!NOTE]  
>  Agrégation RTA de BAM requiert SQL Server Enterprise Edition.  
  
 Pour obtenir une liste complète des fonctionnalités prises en charge par les éditions, consultez [fonctionnalités prises en charge par les éditions de SQL Server](https://docs.microsoft.com/sql/sql-server/editions-and-components-of-sql-server-2016).