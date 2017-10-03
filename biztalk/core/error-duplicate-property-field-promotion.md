---
title: "Erreur : Promotion de champ de propriété en double | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.edit.error.dupPropFieldPromo
ms.assetid: 59ac55c3-7613-493c-85a3-3965c250a3bb
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 87d9f6ee346f5aae98ea69c2ce4e00c4fa1d6dbf
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error---duplicate-property-field-promotion"></a>Erreur : Promotion de champ de propriété en double
**Code d’erreur**  
  
 BEC2016  
  
 **Explication**  
  
 Plusieurs nœuds de ce schéma sont en cours de promotion en tant que champs de propriété à la même **élément de champ** nœud dans le même schéma de propriété.  
  
 **Action de l’utilisateur**  
  
 Utilisez le **champs de propriété** onglet de la **promouvoir les propriétés** boîte de dialogue, accédé via la **promouvoir les propriétés** propriété de la **schéma**nœud afin de supprimer tous les mais parmi les promotions des champs de propriété qui sont associées au même **élément de champ** nœud dans le schéma de propriété. Vous pouvez souhaiter ajouter de nouveaux **élément de champ** nœuds au schéma de propriété afin que les promotions supprimées peuvent être de nouveau promues à leur propre **élément de champ** nœuds.