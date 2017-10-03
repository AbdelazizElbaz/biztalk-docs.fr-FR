---
title: RetractByType | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- RetractByType function [Business Rules Engine], TypedXMLDocument
- RetractByType function [Business Rules Engine]
- RetractByType function [Business Rules Engine], .NET objects
- RetractByType function [Business Rules Engine], TypedData table
- RetractByType function [Business Rules Engine], DataConnection
- .NET objects
ms.assetid: e8867553-ee3c-46be-84cd-d5373eaf3337
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: da8cd4581007ad2bd93ed66ebce4f5de6378280c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="retractbytype"></a>RetractByType
Le **RetractByType** fonction retire toutes les instances d’un type spécifié dans la mémoire de travail, tandis que la **Retract**fonction retire seulement les éléments spécifiques d’un certain type. Les paragraphes suivants décrivent comment les **RetractByType** avec des entités de types différents.  
  
## <a name="net-objects"></a>Objets .NET  
 Tous les objets d'un type de classe donné sont retirés de la mémoire de travail. La classe faites simplement glisser à partir du volet des faits Classes .NET dans le **RetractByType** (fonction).  
  
## <a name="typedxmldocument"></a>TypedXmlDocument  
 Toutes les instances sont retirées. Cela signifie que tous les **TypedXmlDocument**comportant le même **DocumentType.Selector** sont retirées. Vous devez faire glisser le nœud approprié à partir du volet des faits schémas XML dans le **RetractByType** (fonction). Cohérent avec la **retrait** de fonction, si vous effectuez un **RetractByType** sur le nœud racine du document, il sera non seulement toutes les **TypedXmlDocuments** déclarées avec ce  **DocumentType** rétracté, mais tous les enfants **TypedXmlDocuments** (**XmlNode**s dans la hiérarchie d’arborescence) associées à ces parent **TypedXmlDocuments**  également vont être retirées.  
  
## <a name="typeddatatable-and-dataconnection"></a>TypedDataTable et DataConnection  
 **Retrait** et **RetractByType** sont équivalents pour **TypedDataTable** et **DataConnection**. Étant donné que **DataSetName.DataTableName** est un identificateur unique pour les deux types, il n'existe qu’une seule instance dans le moteur à tout moment dans le temps. Comme avec **retrait**, vous faites glisser la table dans le **RetractByType** (fonction).  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions de contrôle du moteur](../core/engine-control-functions.md)