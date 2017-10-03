---
title: Les liens dans les mappages | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- functoid types, Looping
- Looping functoids
- maps, links
- BizTalk Mapper, links
ms.assetid: 3db77b8d-7b86-4c00-99a0-0513aff9b56b
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a32d2a9ef07cf2d79037d7983e49b26c6cfe5e81
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="links-in-maps"></a>Liens figurant dans les mappages
Les liens spécifient la fonction de base de copie des données d'un élément ou d'un attribut d'un message d'instance d'entrée vers un élément ou un attribut d'une instance de sortie. Vous créez des liens entre les enregistrements et les champs des schémas source et de destination au moment de la conception. Cela se traduit par la création, au moment de l’exécution, d’un message d’instance de sortie conforme au schéma de destination à partir d’un message d’instance d'entrée conforme au schéma source.  
  
 Le Mappeur BizTalk prend en charge les liens un-à-un et un-à-plusieurs. Par exemple, un lien peut connecter un enregistrement ou un champ unique d'un schéma source à un enregistrement ou un champ unique du schéma de destination. Il peut également connecter un enregistrement ou un champ unique d'un schéma source à de multiples enregistrements ou champs du schéma de destination.  
  
 Les liens peuvent également connecter plusieurs enregistrements ou champs d’un schéma source à un fonctoid, qui se connecte ensuite à un ou plusieurs enregistrements ou champs du schéma de destination. En général, les liens reliant directement plusieurs enregistrements ou champs source à un enregistrement ou un champ de destination unique ne sont pas valides et génèrent un avertissement. Une exception à cela est la **bouclage** fonctoid. Pour plus d’informations sur la **bouclage** fonctoid, consultez [fonctoid Bouclage](../core/looping-functoid.md).  
  
 Les rubriques de cette section décrivent des concepts liés à la création et à l'utilisation des liens dans le Mappeur BizTalk.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Types de liens](../core/types-of-links.md)  
  
-   [Création de liens](../core/creating-links.md)  
  
-   [Configuration des liaisons](../core/configuring-links.md)  
  
-   [Création de liens enregistrement à enregistrement](../core/record-to-record-linking.md)  
  
-   [Liens vers et à partir de tout élément et tout attribut nœuds](../core/links-to-and-from-the-any-element-and-anyattribute-nodes.md)  
  
-   [Liens et des Directives de compilateur](../core/compiler-directives-and-links.md)