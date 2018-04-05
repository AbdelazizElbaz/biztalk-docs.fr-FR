---
title: Rôles (nœud de Service) | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Roles node [binding file]
ms.assetid: 847755c9-1697-41a0-b870-f9e795a1a2a6
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b47f5ae94326b0555c0c9cd84752cb9f1c409daa
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="roles-service-node"></a>Rôles (nœud de service)
Le nœud Rôles d'un fichier de liaison est le nœud parent de tous les nœuds Rôles qui fournissent des informations spécifiques sur chaque rôle lié à un service exporté avec le fichier de liaison.  
  
## <a name="nodes-in-the-roles-node"></a>Nœuds du nœud Rôles  
 Le tableau suivant répertorie les propriétés que vous pouvez définir pour ce nœud d'un fichier de liaison :  
  
|**Nom**|**Type de nœud**|**Type de données**|**Description**|**Restrictions**|**Commentaires**|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|[Rôle](../core/role-roles-node.md)|Record|RoleRef (ComplexType)|Spécifie des informations sur un rôle lié à un service exporté avec le fichier de liaison.|Facultatif|Valeur par défaut : Aucun|