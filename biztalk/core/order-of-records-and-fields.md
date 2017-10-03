---
title: Ordre des enregistrements et champs | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BizTalk Mapper, sorting
- XSLT, sorting
ms.assetid: 7fa9b5cd-73bc-496f-a081-4a45da3afe42
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5826d46fef73400a5d54e2d1154a1647af85294e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="order-of-records-and-fields"></a>Ordre des enregistrements et des champs
Le langage de transformation de feuille de style extensible (XSLT) tel qu'il est utilisé par le Mappeur BizTalk ne garantit pas l'ordre de sortie des éléments et attributs de sortie. En effet, le Mappeur BizTalk génère XSLT en examinant la structure de schéma de destination, puis procède à la propagation des éléments en revenant dans les pages de grille afin d'extraire les valeurs de la structure de schéma source. Par exemple, si vous souhaitez créer un fichier de sortie dont l'enregistrement BillTo Address est répertorié avant l'enregistrement ShipTo Address, vous devez vous assurer que BillTo Address précède ShipTo Address dans le schéma de destination.  
  
> [!IMPORTANT]
>  L'ordre dans lequel les éléments et les attributs apparaissent dans un message d'instance de sortie dépend de l'ordre des enregistrements et des champs du schéma de destination correspondant.  
  
## <a name="see-also"></a>Voir aussi  
 [Mappages](../core/maps.md)   
 [Création de mappages à l’aide du Mappeur BizTalk](../core/creating-maps-using-biztalk-mapper.md)