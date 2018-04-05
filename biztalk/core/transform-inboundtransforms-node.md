---
title: Transformation (nœud InboundTransforms) | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Transform node [binding file]
ms.assetid: c1bad23e-78a4-4fd4-95ef-30601393d53c
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 705b1b04b8305330ab1d5ff705c5025f24b0685c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="transform-inboundtransforms-node"></a>Transformation (nœud InboundTransforms)
Le nœud Transformation du nœud InboundTransforms d'un fichier de liaison contient des informations spécifiques sur un mappage Biztalk Server exporté avec ce fichier de liaison.  
  
## <a name="nodes-in-the-transform-node"></a>Nœuds du nœud Transform  
 Le tableau suivant répertorie les propriétés que vous pouvez définir pour ce nœud d'un fichier de liaison :  
  
|**Nom**|**Type de nœud**|**Type de données**|**Description**|**Restrictions**|**Commentaires**|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|FullName|Attribut|xs:string|Spécifie le nom complet du mappage.|Facultatif|Valeur par défaut : vide|  
|AssemblyQualifiedName|Attribut|xs:string|Spécifie le nom qualifié d'assembly du mappage.|Facultatif|Valeur par défaut : vide|