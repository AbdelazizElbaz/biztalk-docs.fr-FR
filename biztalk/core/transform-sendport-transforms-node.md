---
title: Transformation (nœud SendPort-transformations) | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Transform node [binding file]
ms.assetid: db9a82b2-9bc1-4bd8-8d98-a708a8d25b35
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0a54ed1f25b762d12f598bca84da9b9c3ddd26a9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="transform-sendport-transforms-node"></a>Transformation (nœud SendPort-transformations)
Le nœud de transformation du nœud Transforms d'un fichier de liaison contient des informations sur un mappage Biztalk server  associé à un transport exporté avec le fichier de liaison.  
  
## <a name="nodes-in-the-transform-node"></a>Nœuds du nœud Transform  
 Le tableau suivant répertorie les propriétés que vous pouvez définir pour ce nœud d'un fichier de liaison :  
  
|**Nom**|**Type de nœud**|**Type de données**|**Description**|**Restrictions**|**Commentaires**|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|FullName|Attribut|xs:string|Spécifie le nom complet du mappage.|Facultatif|Valeur par défaut : vide|  
|AssemblyQualifiedName|Attribut|xs:string|Spécifie le nom qualifié d'assembly du mappage.|Facultatif|Valeur par défaut : vide|