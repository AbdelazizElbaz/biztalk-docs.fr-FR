---
title: Rôle (nœud rôles) | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Role node [binding file]
ms.assetid: dfe2a579-7090-4d85-87e5-d627598c4ee8
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8d70e99568db262ef5abd5b0885cb814c722347f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="role-roles-node"></a>Rôle (nœud Rôles)
Le nœud Role du nœud Roles d'un fichier de liaison spécifie des informations sur un rôle lié à un service exporté avec le fichier de liaison.  
  
## <a name="nodes-in-the-role-node"></a>Nœuds du nœud Role  
 Le tableau suivant répertorie les propriétés que vous pouvez définir pour ce nœud d'un fichier de liaison :  
  
|**Nom**|**Type de nœud**|**Type de données**|**Description**|**Restrictions**|**Commentaires**|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|Nom|Attribut|xs:string|Spécifie le nom du rôle.|Facultatif|Valeur par défaut : vide|  
|RoleLinkTypeName|Attribut|xs:string|Spécifie le nom du type de lien de rôle associé au rôle.|Facultatif|Valeur par défaut : vide|  
|RoleType|Attribut|RoleRefType (SimpleType)|Spécifie le type de rôle associé au rôle.|Requis|Valeur par défaut : Aucun<br /><br /> Les valeurs possibles sont :<br /><br /> -Inconnu<br />-Implémente<br />-Utilise|  
|[Tiers inscrits](../core/enlisted-parties-role-node.md)|Record|ArrayOfEnlistedParty (ComplexType)|Nœud du conteneur des tiers inscrits liés au rôle.|Facultatif|Valeur par défaut : Aucun|