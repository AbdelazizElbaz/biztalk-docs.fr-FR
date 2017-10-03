---
title: "Types de variables d’orchestration | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: orchestrations, variables
ms.assetid: 34990be2-35b6-40ec-b107-42a1c7b45aca
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f388cf112a84d1e6ace00d3930cd6d815d728d89
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="orchestration-variable-types"></a>Types de variables d’orchestration
Vous pouvez déclarer les variables des types prédéfinis suivants :  
  
|||||  
|-|-|-|-|  
|boolean|byte|char|datetime|  
|decimal|double|int16|int32|  
|int64|long|sbyte|single|  
|chaîne|timespan|uint16|uint32|  
|uint64||||  
  
 Vous pouvez également déclarer des variables de n'importe quel type .NET référencé dans votre projet.  
  
## <a name="considerations-for-declare-orchestration-variables"></a>Observations sur la déclaration des variables d'orchestration  
 Lors de la déclaration des variables d'orchestration, gardez les points suivants à l'esprit :  
  
-   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] prend en charge les propriétés de contexte à valeurs multiples pour certains scénarios de routage basés sur le contenu, mais ces propriétés ne sont pas utilisables dans les orchestrations.  
  
-   Afin de prendre en charge l'interruption et la réactivation des orchestrations, l'état de toutes les variables d'orchestration doit pouvoir être conservé.  Cela est généralement le cas lorsque la classe ou le type de la variable peut être sérialisé ou transmis.  
  
-   Ces types .NET (classes) doivent être sérialisables.  Pour ce faire, ils peuvent être déclarés avec l'attribut « [Sérialisable] » ou implémenter explicitement l'interface ISerializable .NET (dans l'espace de noms System.Runtime.Serialization).  
  
-   Si le type .NET est un wrapper RCW (Runtime Callable Wrapper) d'un composant COM sous-jacent, ce composant doit implémenter les interfaces requises pour que le RCW devienne une classe .NET sérialisable (par ex. IPersistStream, IPersistStreamInit).  
  
-   Les types .NET (ou composants COM sous-jacents) étant exécutés dans une orchestration, leurs méthodes ne doivent pas retarder l'exécution de l'orchestration (par ex. par des conflits de ressources, etc.).  En outre, toute utilisation des ressources par ces implémentations de types affectera l'instance hôte dans laquelle est exécutée l'orchestration d'appel.