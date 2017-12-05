---
title: "Utiliser des compteurs de Performance avec l’adaptateur Siebel | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- performance counters, troubleshooting
- troubleshooting, performance counters
- performance counters, using
ms.assetid: 7930e8f6-5099-4a9c-b38a-13c9902635a6
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bebbd605df52e023c78112b78ad51db13d896cc7
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="use-performance-counters-with-the-siebel-adapter"></a>Utiliser des compteurs de Performance avec l’adaptateur Siebel
[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]les clients peuvent utiliser les compteurs de performance pour évaluer les performances des adaptateurs. Le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] programme d’installation crée la catégorie de compteur de performances «[!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)]», ainsi que l’installation du Pack d’adaptateurs.  
  
## <a name="the-lob-time-cumulative-performance-counter"></a>Le compteur de Performance du temps (cumulatif) LOB  
 Le **.NET l’adaptateur BizTalk pour Siebel** catégorie possède un compteur de performances « Temps LOB (cumulé) ». Ce compteur de performance indique la durée, en millisecondes, qui la bibliothèque cliente LOB prend pour effectuer une action qui initialise de l’adaptateur. Le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] crée une instance du compteur de performance pour chaque action, d’un nom de serveur Siebel spécifique. Les instances sont créées dans le modèle suivant :  
  
```  
<process id>:<app domain id>:<endpoint id>:<action id>  
```  
  
 Dans le cas de la [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)], l’id de point de terminaison est le nom du serveur Siebel, comme spécifié dans l’URI de connexion. L’id d’action peut être toute action effectuée par le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] telles que la connexion, de fermeture de session, de métadonnées, \<nom du composant métier\>.\< opération\>, \<nom de service d’entreprise\>.\< méthode de service Business\>. Si la convention d’affectation de noms précédente se traduit par un nom qui dépasse 127 caractères uniquement l’ID de l’action est affiché dans le format suivant :  
  
```  
:::<action id>  
```  
  
 Si `:::<action id>` également plus de 127 caractères, il est tronqué jusqu'à 127 caractères.  
  
 Le compteur de performance est initialisé uniquement après que l’adaptateur effectue le premier appel au système Siebel. En outre, le **InstanceLifetime a** du compteur de performance est définie sur « Processus », ce qui signifie que le compteur de performances cesse d’exister dès que le programme qui crée le compteur se termine. 
  
> [!NOTE]
>  La précision du compteur de performance de temps LOB (cumulé) est 16 millisecondes.  
  
## <a name="enabling-performance-counters"></a>Activation des compteurs de performances  
 Les compteurs de performance peuvent être activés ou désactivés en définissant la propriété de liaison **EnablePerformanceCounters**. Définissez **EnablePerformanceCounters** liaison de propriété **True** pour activer les compteurs de performances. Pour désactiver les compteurs de performances, définissez **EnablePerformanceCounters** à **False**. Par défaut, **EnablePerformanceCounters** a la valeur **False**.  
  
## <a name="performance-counters-and-the-wcf-lob-adapter-sdk"></a>Compteurs de performance et le Kit de développement logiciel de l’adaptateur LOB WCF  
 Modification de la valeur de la **EnablePerformanceCounters** propriété liaison modifie la valeur du compteur de performance correspondant pour [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]. En outre, la propriété de liaison pour le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] est statique, tandis que pour les [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] est dynamique. Par conséquent, s’il existe deux instances de la [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] de liaison dans le domaine d’application et le **EnablePerformanceCounters** liaison de la propriété est définie sur **True** dans un et **False**dans l’autre, le compteur spécifique à l’adaptateur sera activé dans un et désactivé pour l’autre. Toutefois, étant donné que la propriété de liaison pour le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] est statique, elle est soit définie **True** ou **False**, selon quelle valeur a été spécifié en dernier.  
  
## <a name="see-also"></a>Voir aussi  
[Dépanner l’adaptateur Siebel](../../adapters-and-accelerators/adapter-siebel/troubleshoot-the-siebel-adapter.md)