---
title: "Types de données XLANG-s | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestrations, expressions
- Orchestration Designer, managing data
- Orchestration Designer, variables
- orchestrations, variables
- Orchestration Designer, expressions
ms.assetid: 5b08aaa6-1533-4bac-a76d-f9162e39bf4f
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c21ed77c5fdd56485514d17ed75e921c63a56212
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="xlang-s-data-types"></a>Types de données XLANG-s
XLANG/s définit des types de valeurs standard qui sont le reflet de leurs équivalents C#. Ceux-ci incluent **booléenne**, **octets**, **Char**, **décimal**, **Double**, **Int16** , **Int32**, **Int64**, **SByte**, **unique**, **chaîne**,  **UInt16**, **UInt32**, et **UInt64**. XLANG/s prend en charge les tableaux unidimensionnels, mais pas les littéraux de tableau.  
  
 XLANG/s gère également le traitement des messages. Ces derniers peuvent être basés sur des schémas, des classes .NET, des types de messages Web (WSDL) ou des types de messages complexes. XLANG/s prend en charge les types de données complexes suivants :  
  
-   **MessageType.** ce type de données définit les types de messages à parties multiples définis en tant que combinaisons d'éléments de données et de messages XSD, et les types de messages de méthode (messages correspondant au format de signature de la méthode d'une classe ou d'une interface).  
  
-   **PortType.** ce type de données définit un ensemble d'opérations de port sur lesquelles peut agir une instance de port de ce type.  
  
-   **correlationsettype.** ce type de données définit les données qui seront utilisées dans n'importe quelle instance de variable d'un ensemble de corrélations. Les données d'un ensemble de corrélations représentent la méthode de routage utilisée pour garantir la distribution des messages circulant dans le système à l'instance d'exécution appropriée d'un processus d'entreprise. Par exemple, si un bon de commande est envoyé à un partenaire commercial pour être traité, il est impératif que l'instance appropriée du processus d'entreprise correspondant au bon de commande soit appelée à son retour.  
  
-   **servicelinktype.** Ce type de données définit l’ensemble des **porttype** valeurs qui forment un groupe logiquement cohérent de ports utilisés dans un processus d’entreprise. L'utilisation des liens de service constitue une méthode puissante d'attribution dynamique à un groupe de ports lors de l'exécution. Vous pouvez alors définir un seul processus d'entreprise qui sera utilisé pour interagir avec plusieurs partenaires commerciaux.  
  
## <a name="see-also"></a>Voir aussi  
 [Instructions XLANG-s](../core/xlang-s-statements.md)   
 [Opérateurs et Variables XLANG-s](../core/xlang-s-variables-and-operators.md)   
 [Expressions XLANG-s](../core/xlang-s-expressions.md)   
 [Mots réservés XLANG-s](../core/xlang-s-reserved-words.md)   
 [XLANG-s pour les Conversions de Type BPEL4WS](../core/xlang-s-to-bpel4ws-type-conversions.md)