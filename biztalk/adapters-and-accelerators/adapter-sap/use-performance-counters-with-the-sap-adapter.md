---
title: "Utiliser des compteurs de Performance avec l’adaptateur SAP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- performance counters, using
- troubleshooting, using performance counters
ms.assetid: 2749add3-31f1-47ff-b3b4-ef46c76fa533
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dbc7ed347bc81a8a00ff7faa826bd48203c47e63
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="use-performance-counters-with-the-sap-adapter"></a>Utiliser des compteurs de Performance avec l’adaptateur SAP
Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] les clients peuvent utiliser des compteurs de performance pour évaluer les performances des adaptateurs. Le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] programme d’installation crée la catégorie de compteur de performances «[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]» le long de l’installation de le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].  
  
## <a name="lob-time-cumulative-performance-counter"></a>Compteur de Performance de temps (cumulatif) de cœur de métier  
 Le **.NET l’adaptateur BizTalk pour SAP** catégorie possède un compteur de performances « LOB Time (cumulé) ». Ce compteur de performance indique la durée, en millisecondes, qui la bibliothèque cliente LOB prend pour effectuer une action qui initialise de l’adaptateur. Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] crée une instance du compteur de performance dans le modèle suivant :  
  
```  
<process id>:<app domain id>:<endpoint id>:<action id>  
```  
  
 L’ID de point de terminaison peut être :  
  
-   Pour les appels à partir de l’adaptateur au système SAP (sortie)  
  
    -   A,\<hôte d’application serveur\>,\<numéro du système\>  
  
    -   B,\<hôte du serveur message\>,\<R3NAME\>  
  
    -   D,\<destination\>  
  
-   Pour les appels du système SAP à l’adaptateur (entrant)  
  
    -   I,\<hôte de passerelle\>,\<serveur de passerelle\>  
  
    -   ID,\<destination\>  
  
 L’ID d’action peut être :  
  
-   \<Nom de la RFC\> (pour un appel de la RFC)  
  
-   T,\<nom de la RFC\> (pour un appel tRFC)  
  
 Le compteur de performance est initialisé uniquement après que l’adaptateur effectue le premier appel au système SAP. En outre, le [InstanceLifetime a](https://msdn.microsoft.com/library/system.diagnostics.performancecounter.instancelifetime.aspx) du compteur de performance est définie sur « Processus », ce qui signifie que le compteur de performances cesse d’exister dès que le programme qui crée le compteur se termine.
  
> [!NOTE]
>  La précision du compteur de performance de temps LOB (cumulé) est 16 millisecondes.  
  
## <a name="enabling-performance-counters"></a>Activation des compteurs de performances  
 Les compteurs de performance peuvent être activés ou désactivés en définissant la propriété de liaison *EnablePerformanceCounters*. Pour activer les compteurs de performances, définissez la *EnablePerformanceCounters* liaison de propriété **True**. Pour désactiver les compteurs de performances, définissez *EnablePerformanceCounters* à **False**. Par défaut, *EnablePerformanceCounters* a la valeur **False**.  
  
## <a name="performance-counters-and-the-wcf-lob-adapter-sdk"></a>Compteurs de performance et le Kit de développement logiciel de l’adaptateur LOB WCF  
 Modification de la valeur de la *EnablePerformanceCounters* également de propriété de liaison modifie la valeur du compteur de performance correspondant pour le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]. En outre, la propriété de liaison pour le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] est statique, tandis que pour les [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] est dynamique. Par conséquent, s’il existe deux instances de la [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] de liaison dans le domaine d’application et le *EnablePerformanceCounters* liaison de la propriété est définie sur **True** dans un et **False**dans l’autre, le compteur spécifique à l’adaptateur sera activé dans un et désactivé pour l’autre. Toutefois, étant donné que la propriété de liaison pour [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] est statique, elle est soit définie **True** ou **False** selon quelle valeur a été spécifié en dernier.  
  
## <a name="see-also"></a>Voir aussi  

[Résoudre les problèmes de l’adaptateur SAP](../../adapters-and-accelerators/adapter-sap/troubleshoot-the-sap-adapter.md)