---
title: "Gestionnaires de propriétés | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 823352a0-e397-464a-a163-1dbf8feea8d7
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6aff8fc39612ed79e6e9602ed39874d014bb4a11
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="property-managers"></a>Gestionnaires de propriétés
Les gestionnaires de propriétés permettent à une extension d'ajouter des propriétés personnalisées (comme annotations XSD généralement) à des éléments et des attributs dans la représentation XSD du schéma, ainsi que d'étendre la fenêtre Propriétés pour inclure les propriétés personnalisées associées à l'extension.  
  
 Un gestionnaire de propriétés est un objet qui implémente le **IPropertyManager** interface, une référence à ce qui est obtenue en appelant **IExtension.GetPropertyManager**et en passant un  **ITreeNode** objet en tant que paramètre d’entrée. L’extension fournit généralement une **IPropertyManager** objet pour chaque **ITreeNode** objet. Le Gestionnaire de propriétés est responsable de la collection de propriétés personnalisées pour ce **ITreeNode** objet.  
  
 Une propriété personnalisée est représentée par un **System.ComponentModel.PropertyDescriptor** objet, qui peut être obtenu à partir de la collection retournée par la **IPropertyManager.GetProperties** (méthode).  
  
 À l’aide de **PropertyDescriptor** objets pour représenter les propriétés personnalisées associées à l’extension facilite l’intégration à Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] fenêtre Propriétés. Lorsque **PropertyDescriptor** objets sont utilisés, il est facile pour l’Éditeur BizTalk pour intégrer les propriétés personnalisées de l’extension de l’ensemble de propriétés de nœud standard déjà en cours d’intégration dans la fenêtre Propriétés. Informations sur les propriétés personnalisées telles que le nom d’affichage, la valeur d’affichage, le type de contrôle de la propriété, la description de la propriété et la catégorie de propriété sont obtenues à partir de la **PropertyDescriptor** objet.  
  
 Des propriétés personnalisées sont stockées dans la représentation XSD du schéma en tant qu'attributs d'un élément au sein de l'élément d'annotation dans l'élément correspondant au nœud pertinent de l'arborescence de schéma. Chaque propriété personnalisée d'un nœud d'arborescence de schéma peut être un attribut d'un élément commun mais chacune peut également avoir son propre élément associé.  
  
## <a name="see-also"></a>Voir aussi  
 [Extension de l’Éditeur BizTalk](../core/extending-biztalk-editor.md)