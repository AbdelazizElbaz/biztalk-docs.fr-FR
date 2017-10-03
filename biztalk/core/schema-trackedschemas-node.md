---
title: "Schéma (nœud TrackedSchemas) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Schema node
ms.assetid: a503aad6-07f8-4650-a214-4d2f6650cb80
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5376c505332ed05507169c1db2dc54ec4e7bdfe6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="schema-trackedschemas-node"></a>Schéma (nœud TrackedSchemas)
Le nœud Schéma du nœud TrackedSchemas d'un fichier de liaison décrit un schéma lié à un service exporté avec le fichier de liaison.  
  
## <a name="nodes-in-the-schema-node"></a>Nœuds du nœud Schéma  
 Le tableau suivant répertorie les propriétés que vous pouvez définir pour ce nœud d'un fichier de liaison :  
  
|**Nom**|**Type de nœud**|**Type de données**|**Description**|**Restrictions**|**Commentaires**|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|FullName|Attribut|xs:string|Spécifie le nom complet du schéma.|Facultatif|Valeur par défaut : vide|  
|AssemblyQualifiedName|Attribut|xs:string|Spécifie le nom complet de l'assembly contenant le schéma.|Facultatif|Valeur par défaut : vide|  
|AlwaysTrackAllProperties|Attribut|xs:boolean|Indique s'il faut ou non suivre toutes les propriétés pour l'assembly spécifié.|Requis|Valeur par défaut : Aucun<br /><br /> La valeur **true** pour effectuer le suivi de toutes les propriétés, sinon la valeur **false**.|  
| Description|Attribut|xs:string|Spécifie une description pour le schéma.|Facultatif|Valeur par défaut : vide|  
|[TrackedPropertyNames (nœud de schéma)](../core/trackedpropertynames-schema-node.md)|Record|ArrayOfString (ComplexType)|Conteneur pour les éléments qui spécifient les propriétés à suivre.|Facultatif|Valeur par défaut : Aucun|