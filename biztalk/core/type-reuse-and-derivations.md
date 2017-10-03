---
title: "Réutilisation et dérivations de type | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 240145ea-be41-40ce-8edd-3d4d00e2baec
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2982fdf5e46f813669ff74b513615637aa699bd4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="type-reuse-and-derivations"></a>Réutilisation et dérivations de type
Dans le langage XSD (XML Schema definition), les types globaux complexes fournissent un mécanisme permettant de définir un type de données structurées qui peut être réutilisé, et potentiellement redéfini, à différents emplacements de votre schéma. L’exemple le plus classique est peut-être celui d’une structure d'adresse qui comprend un nom, une rue, une ville, etc. Qui plus est, le nom lui-même peut correspondre à une structure qui comprend les chaînes des prénom et nom. Si cette structure complexe est définie globalement, vous pouvez l’utiliser à de nombreux emplacements de votre schéma, comme adresse de livraison et de facturation.  
  
 XSD fournit également des mécanismes permettant de dériver un type depuis un autre. Cela comprend à la fois des types de contenu simples et des types de contenu complexes. Un nouveau type peut par exemple être dérivé d'un type de chaîne simple (tel que xs:string) de façon que le nouveau type n’autorise que quelques chaînes particulières. Ce type de dérivation est connu dans XSD comme la dérivation par restriction, car les valeurs autorisées par le type dérivé sont plus restrictives que les valeurs autorisées par le type de base.  
  
 Le type d'adresse précédemment suggéré présente un exemple de dérivation impliquant un type complexe. Supposez que le type d’adresse est conçu pour gérer les adresses d’un pays ou d’une région particulière, pour lesquelles le pays ou la région sont implicites. Pour étendre un tel type d'adresse de façon qu’il gère des adresses internationales, vous pouvez déduire un nouveau type à partir du type d'adresse d'origine, puis intégrer des informations supplémentaires dans le type dérivé tel que le pays ou la région. Ce type de dérivation est connu dans XSD comme dérivation par extension, car le type dérivé est une extension du type de base.  
  
 Cette section décrit la réutilisation d’un type et la façon dont vous pouvez utiliser la dérivation pour redéfinir des types à mesure qu’ils sont réutilisés.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Définition de Type Global complexe et d’affectation de noms](../core/complex-global-type-definition-and-naming.md)  
  
-   [Modes d’utilisation des Types globaux complexes](../core/ways-to-use-complex-global-types.md)  
  
-   [Dérivation de Type simple](../core/simple-type-derivation.md)