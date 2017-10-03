---
title: "Comment créer des schémas pour les Messages de fichier plat | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 48f2747b-7f26-4fb2-a855-523e093f3813
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 58583037b8fae945dea07aa8af62e969b96e073f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="create-schemas-for-flat-file-messages"></a>Création de schémas pour les Messages de fichier plat

## <a name="overview"></a>Vue d'ensemble
Après la création d’un schéma de message XML comme décrit dans [création de schémas pour les Messages XML](../core/how-to-create-schemas-for-xml-messages.md), utilisez le **Extensions de l’éditeur de schéma** propriété de la **schéma** nœud pour permettre la extension de fichier plat. L'activation de l'extension de fichier plat ajoute un nombre considérable de propriétés à de nombreux types de nœud au sein d’un schéma. Ces propriétés sont généralement utilisées pour contrôler la façon dont un document commercial de fichier plat est converti depuis et vers son équivalent XML, et leurs valeurs sont conservées sous forme d’annotation en langage XSD (XML Schema definition) dans le fichier de schéma. L'utilisation correcte de ces propriétés demande une certaine pratique et une bonne compréhension des aspects du format de fichier plat concernés par chacune d’elles. 

Pour conceptuel et les informations de référence sur les propriétés de fichier plat, voir [Considérations lors de la création de Message schémas de fichier plat](../core/considerations-when-creating-flat-file-message-schemas.md) et **des propriétés de nœud supplémentaires pour les schémas de fichier plat** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].  
  
## <a name="see-also"></a>Voir aussi  
-  [Gestion des schémas dans des projets](../core/managing-schemas-within-projects.md)
-  Plus d’informations sur ces propriétés.[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]