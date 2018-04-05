---
title: Tiers (nœud tiers inscrits) inscrit | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Enlisted Parties node [binding file]
ms.assetid: 2ff7b563-17c5-48e9-b33e-62c821188448
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 624f74d3b49b80e8000723c3f7451c52b37c8d3d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="enlisted-party-enlisted-parties-node"></a>Tiers inscrit (nœud Tiers inscrits)
Le nœud Tiers inscrit d'un fichier de liaison contient des informations sur le tiers enregistré associé à un transport exporté avec le fichier de liaison.  
  
## <a name="nodes-in-the-enlisted-party-node"></a>Nœuds figurant dans le nœud Tiers inscrits  
 Le tableau suivant répertorie les propriétés que vous pouvez définir pour ce nœud d'un fichier de liaison :  
  
|**Nom**|**Type de nœud**|**Type de données**|**Description**|**Restrictions**|**Commentaires**|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|Nom|Attribut|xs:string|Indique le nom du tiers inscrit.|Facultatif|Valeur par défaut : vide|  
|[Mappages](../core/mappings-enlisted-party-node.md)|Record|ArrayOfEnlistedPartyMapping (ComplexType)|Le nœud du conteneur des mappages entre les ports de tiers et les opérations de type de ports de rôle.|Facultatif|Valeur par défaut : Aucun|