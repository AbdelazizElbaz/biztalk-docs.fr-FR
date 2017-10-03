---
title: "Dérivation de Type simple | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d43932a0-039c-4211-82c0-087bae186145
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fcc74796de8543f1e0f895d0b3dff705aeb2930e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="simple-type-derivation"></a>Dérivation de type simple
Le langage XSD (XML Schema Definition) fournit plusieurs mécanismes de définition de variantes de types simples, basés sur des dérivations de types simples existants :  
  
-   **Restriction**. la dérivation de type simple par utilisation du mécanisme de restriction implique l'introduction de restrictions concernant les valeurs possibles pour ce type. Exemples : les valeurs minimum et/ou maximum pour les types numériques, ou une longueur minimum et maximum pour les types de chaîne.  
  
-   **Liste**. la dérivation de type simple par utilisation du mécanisme de liste permet qu'une seule valeur d'attribut ou d'élément dans un message d'instance soit définie comme se composant d'une liste de valeurs séparées par des espaces et d'un type particulier.  
  
-   **Union**. la dérivation de type simple par utilisation du mécanisme d'union permet qu'une seule valeur d'attribut ou d'élément dans un message d'instance soit définie comme une valeur unique d'un ou plusieurs types spécifiés.  
  
 Cette section décrit ces dérivations de type simple de façon plus détaillée. Vous y apprendrez notamment comment les définir en définissant les propriétés de nœud appropriées dans la fenêtre Propriétés ainsi que comment l'XSD correspondant est construit.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Dérivation de Type simple à l’aide du mécanisme de Restriction](../core/simple-type-derivation-using-the-restriction-mechanism.md)  
  
-   [Dérivation de Type simple à l’aide du mécanisme de liste](../core/simple-type-derivation-using-the-list-mechanism.md)  
  
-   [Dérivation de Type simple à l’aide du mécanisme d’Union](../core/simple-type-derivation-using-the-union-mechanism.md)