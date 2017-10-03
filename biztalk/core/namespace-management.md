---
title: Gestion de Namespace | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4638c47c-3cdd-43af-aa00-da98e7293503
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 897ab6de3e7fddb362cb59356e6a4808d35f8f47
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="namespace-management"></a>Gestion des espaces de noms
L'Éditeur BizTalk prend en charge les espaces de noms. Un espace de noms XML est un ensemble de noms qui peuvent être utilisés comme noms d'élément ou d’attribut dans un message XML. L'espace de noms qualifie des noms d'élément et d’attribut de façon à éviter les conflits entre des noms d'élément et d’attribut identiques pouvant être définis ailleurs dans le même schéma.  
  
 Les espaces de noms sont identifiés par un URI (Universal Resource Identifier), en tant qu'URL (Uniform Resource Locator) ou URN (Uniform Resource Name). On leur ajoute également un alias de préfixe généralement court, séparé par un deux-points (:) du nom de l'élément ou de l'attribut lui-même. Par exemple, il est courant de voir la déclaration d’espace de noms suivantes au sein de la **schéma** élément dans la représentation XSD du schéma.  
  
```  
xmlns:xs="http://www.w3.org/2001/XMLSchema"  
  
```  
  
 Le préfixe est xs, que vous voyez dans la représentation XSD, qualifie des éléments tels que les **élément** élément (xs : Element) et le **attribut** élément (xs : Attribute).  
  
 Lorsque vous créez un nouveau schéma, qu’il s’agisse d’un schéma de message ou un schéma de propriété, il est important de définir la **cible Namespace** propriété de la **schéma** nœud correctement. Vous devez établir l'espace de noms cible avant que le schéma ne soit utilisé par un autre schéma avec les mécanismes importer, inclure et redéfinir, et avant que toute promotion de propriété ne soit définie.  
  
> [!WARNING]
>  Si vous utilisez deux espaces de noms qui varient uniquement par la casse, la base de données BizTalk doit être installé avec un classement qui respecte la casse. Des classements binaires ou non binaires pour lesquels le respect de la casse est activé sont des exemples de classements respectant la casse. Si vous ne procédez pas à une telle installation, la résolution de schéma échoue, car le format XML fait la distinction entre majuscules et minuscules.  
  
 Les deux espaces de noms suivants sont automatiquement ajoutés en tant que déclaration d’espaces de noms à l'élément de schéma dans la représentation XSD (XML Schema definition) du schéma :  
  
-   xmlns:b="http://schemas.microsoft.com/BizTalk/2003"  
  
-   xmlns:xs="http://www.w3.org/2001/XMLSchema"  
  
 Tandis que vous utilisez d’autres schémas dans le schéma que vous créez, d'autres espaces de noms seront déclarés. Vous pouvez examiner ces espaces de noms, ainsi que les espaces de noms inclus automatiquement dans le **importations** boîte de dialogue que vous pouvez accéder à l’aide de la **importations** propriété de la **deschéma** nœud. Pour plus d’informations sur l’utilisation d’autres types de données déclarés dans d’autres schémas dans le schéma que vous créez, consultez [schémas utilisant d’autres schémas](../core/schemas-that-use-other-schemas.md) et [création de schémas utilisant d’autres schémas](../core/how-to-create-schemas-that-use-other-schemas.md).  
  
 Espace de noms associés à des schémas de propriété peut être examinés dans le **promouvoir les propriétés** boîte de dialogue.  
  
## <a name="see-also"></a>Voir aussi  
 [Considérations relatives à la création de schémas](../core/considerations-when-creating-schemas.md)