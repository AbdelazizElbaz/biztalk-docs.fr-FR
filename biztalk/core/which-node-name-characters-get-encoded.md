---
title: "Qui le codage des caractères de nom de nœud | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 48a581d2-48fa-4c36-b5c2-fe87c328a7f4
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3895fd74ac63380d5502a05eed7c145e13bfd681
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="which-node-name-characters-get-encoded"></a>Caractères de nom de nœud codés
XML impose certaines restrictions concernant les caractères pouvant être utilisés dans les noms XML, tels que les noms d'élément, notamment concernant le premier caractère d'un nom XML. Les objectifs conceptuels de la détermination des caractères à autoriser et à exclure des noms XML conformes sont les suivants :  
  
-   Lorsque c’est possible, soyez inclusif plutôt qu'exclusif, de sorte que les nouveaux systèmes d'écriture puissent être pris en charge lorsqu’ils sont codés en Unicode.  
  
-   Excluez les caractères qui peuvent être utilisés ou sont utilisés en tant que délimiteurs afin que les noms XML puissent apparaître plus facilement dans un contexte délimité, autre que XML.  
  
 Le tableau suivant indique les caractères pouvant être utilisés dans un nom XML, à n'importe quelle position dans le nom, autre que la première, ou non. Certains caractères autorisés sont toutefois exclus en première position d’un nom. Les caractères littéraux sont placés entre guillemets, et les séries sont placées entre crochets.  
  
|Position dans le nom|Caractères autorisés|  
|----------------------|------------------------|  
|Toute position|["A"-"Z"], ["a"-"z"], "_", [0x00C0-0x02FF], [0x0370-0x037D], [0x037F-0x1FFF], [0x200C-0x200D], [0x2070-0x218F], [0x2C00-0x2FEF], [0x3001-0xD7FF], [0xF900-0xEFFF]|  
|Toute position à l'exception de premier|"-", ".", ["0"-"9"], 0x00B7, [0x0300-0x036F], [0x203F-0x2040]|  
  
 La meilleure pratique en anglais pour un nom d’élément ou d’attribut (un nom de nœud dans une arborescence de schéma) peut se résumer ainsi :  
  
-   Utilisez des caractères alphanumériques, mais ne commencez pas par un chiffre.  
  
-   Utilisez le trait de soulignement (_), trait d’union (-), point (.) et point intermédiaire (·).  
  
-   N'utilisez pas d'espace.  
  
-   Utilisez des mots significatifs ou des combinaisons de mots issues de langues naturelles.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriété de nom de nœud](../core/node-name-property.md)   
 [Comment les caractères de nom de nœud codés](../core/how-node-name-characters-get-encoded.md)