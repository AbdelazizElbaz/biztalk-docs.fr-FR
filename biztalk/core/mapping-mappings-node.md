---
title: "Mappage (nœud mappages) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Mapping node [binding file]
ms.assetid: bc54c476-505c-4020-b7df-1d19f86329aa
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b2c62d46e4d5c2b73eee5094ecda0e20c039798a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="mapping-mappings-node"></a>Mappage (nœud Mappages)
Le nœud Mappage d'un fichier de liaison décrit le mappage entre un port de tiers et une opération de type de ports de rôle du tiers inscrit.  
  
## <a name="nodes-in-the-mapping-node"></a>Nœuds du nœud Mappage  
 Le tableau suivant répertorie les propriétés que vous pouvez définir pour ce nœud d'un fichier de liaison :  
  
|**Nom**|**Type de nœud**|**Type de données**|**Description**|**Restrictions**|**Commentaires**|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|PortTypeName|Attribut|xs:string|Spécifie le nom du type de port.|Facultatif|Valeur par défaut : vide|  
|NomOpération|Attribut|xs:string|Spécifie l'opération correspondant à ce type de port.|Facultatif|Valeur par défaut : vide|  
|[SendPortRef](../core/sendportref-mapping-node.md)|Record|SendPortRef (ComplexType)|Nœud du conteneur de la liste des ports d'envoi associée à un mappage.|Facultatif|Valeur par défaut : Aucun|