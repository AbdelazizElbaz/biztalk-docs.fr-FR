---
title: "Utiliser des compteurs de performance avec l’adaptateur de base de données Oracle | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- performance counters, using
- performance counter, LOB Time Cumulative
- performance counters, enabling
- performance counters, and the WCF LOB Adapter SDK
ms.assetid: beb80896-7594-411e-a83c-169d5278e2ce
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ce36fe948daeb89d8fc248dbe33191aa69cdd9ec
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="use-performance-counters-with-the-oracle-database-adapter"></a>Utiliser des compteurs de performance avec l’adaptateur de base de données Oracle
Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] les clients peuvent utiliser des compteurs de performance pour évaluer les performances des adaptateurs. Le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] programme d’installation crée la catégorie de compteur de performances **.NET l’adaptateur BizTalk pour Oracle DB** ainsi que l’installation de le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].  
  
## <a name="lob-time-cumulative-performance-counter"></a>Compteur de Performance de temps (cumulatif) de cœur de métier  
 Le **.NET l’adaptateur BizTalk pour Oracle DB** catégorie possède un compteur de performances « LOB heure (Cumulative). » Ce compteur de performance indique la durée, en millisecondes, qui la bibliothèque cliente LOB prend pour effectuer une action qui initialise de l’adaptateur. Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] crée une instance du compteur de performance dans un des modèles suivants :  
  
```  
<process id>:<app domain id>:<oracle data source>:<string>  
```  
  
 Où « chaîne » pourrait être :  
  
-   Connection.Open  
  
-   Connection.Close, mais  
  
-   Métadonnées  
  
-   Action de message. Par exemple, si l’action est `http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Insert` la chaîne sera alors SCOTT. Table.EMP.Insert.  
  
 La source de données Oracle est identique à celui spécifié dans l’URI de connexion.  
  
 Le compteur de performance est initialisé uniquement après que l’adaptateur effectue le premier appel à la base de données Oracle. En outre, la propriété InstanceLifetime a du compteur de performance est définie à « Processus », ce qui signifie que le compteur de performances cesse d’exister dès que le programme qui crée le compteur se termine. Pour plus d’informations sur la `InstanceLifetime property`, consultez [http://go.microsoft.com/fwlink/p/?LinkId=104181](http://go.microsoft.com/fwlink/p/?LinkId=104181).  
  
> [!NOTE]
>  La précision du compteur de performance de temps LOB (cumulé) est 16 millisecondes.  
  
## <a name="enabling-performance-counters"></a>Activation des compteurs de performances  
 Les compteurs de performance peuvent être activés ou désactivés en définissant la propriété de liaison **EnablePerformanceCounters**. Pour activer les compteurs de performances, définissez la **EnablePerformanceCounters** liaison de propriété **True**. Pour désactiver les compteurs de performances, définissez **EnablePerformanceCounters** à **False**. Par défaut, **EnablePerformanceCounters** a la valeur **False**.  
  
## <a name="performance-counters-and-the-wcf-lob-adapter-sdk"></a>Compteurs de performance et le Kit de développement logiciel de l’adaptateur LOB WCF  
 Modification de la valeur de la **EnablePerformanceCounters** également de propriété de liaison modifie la valeur du compteur de performance correspondant pour le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]. En outre, la propriété de liaison pour le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] est statique, tandis que pour les [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] est dynamique. Par conséquent, s’il existe deux instances de la [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] de liaison dans le domaine d’application et le **EnablePerformanceCounters** liaison de la propriété est définie sur **True** dans un et **False** dans l’autre, le compteur spécifique à l’adaptateur sera activé dans un et désactivé pour l’autre. Toutefois, étant donné que la propriété de liaison pour [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] est statique, elle est soit définie **True** ou **False** selon quelle valeur a été spécifié en dernier.  
  
## <a name="see-also"></a>Voir aussi  
[Dépanner l’adaptateur de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/troubleshoot-the-oracle-database-adapter.md)