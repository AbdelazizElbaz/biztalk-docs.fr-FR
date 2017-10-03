---
title: "Schémas de fichier plat | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8009fba7-85f0-4795-9284-5b4e94b3fc72
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 674a862b3966088bb1d75dd17ceacd47c30bdda1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="flat-file-schemas"></a>Schémas de fichier plat

## <a name="purpose-of-flat-file-schemas"></a>Objectif des schémas de fichier plat
Les schémas de fichier plat servent deux objectifs. Ils définissent l'ensemble des mêmes caractéristiques d'enregistrement et de champ (dont la structure) que les schémas XML et offrent un mécanisme permettant de définir l'ensemble des caractéristiques de fichier plat requis pour convertir un message d'instance de fichier plat en un message d'instance XML équivalent (ou vice versa). Le premier objectif est très utile lorsqu'un schéma de fichier plat est utilisé dans le Mappeur BizTalk pour définir une transformation des messages de fichier plat conformes dans une structure différente de destination. La structure de destination, définie par le schéma de destination dans le Mappeur BizTalk, peut être ou non régie par un schéma de message de fichier plat (il peut s'agir d'un schéma XML).  
  
 Le deuxième objectif, celui qui consiste à effectuer une conversion entre le format de fichier plat du document et son format XML équivalent, utilise un large ensemble d'informations qui est ajouté au schéma de langage XSD (XML Schema Definition) utilisant sa syntaxe d'annotation. Ces informations sont superflues du point de vue du langage XSD, sur le plan de leur utilité pour valider un message d'instance XML par rapport au schéma qui régit leur structure. Néanmoins, la syntaxe d’annotation XSD offre un mécanisme commode pour stocker les informations de structure de fichier plat dans le schéma XSD dans différentes portées différentes, allant des informations de schéma à l’échelle stockées sous forme d’annotations dans le **schéma** élément, des informations spécifiques à un enregistrement particulier ou un champ, stockés sous forme d’annotations dans correspondant **élément** ou **attribut** élément.  
  
 Une autre des caractéristiques des schémas de fichier plat qui les distingue de leurs homologues XML est le fait que les messages d'instance ne peuvent pas être mis en correspondance avec les schémas les régissant sur la base de leur contenu. Au lieu de cela, un ensemble statique de schémas doit être spécifié afin d'être utilisé par le désassembleur de fichier plat lors de l'exécution.  
  
 Pour afficher les propriétés de nœud supplémentaires associées aux caractéristiques de fichiers plats, vous devez spécifier le **Extension de fichier plat** à l’aide de la **Extensions de l’éditeur de schéma** propriété de la **Schéma** nœud. Ces propriétés n'apparaissent pas par défaut.  
  
 Pour plus d’informations sur les propriétés de nœud spécifiques aux schémas de fichier plat, voir la **des propriétés de nœud supplémentaires pour les schémas de fichier plat** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
## <a name="see-also"></a>Voir aussi  
 [Différents Types de schémas BizTalk](../core/different-types-of-biztalk-schemas.md)