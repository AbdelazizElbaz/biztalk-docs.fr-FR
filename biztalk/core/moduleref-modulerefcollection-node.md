---
title: "ModuleRef (nœud ModuleRefCollection) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: ModuleRef node [binding file]
ms.assetid: 61787779-33bd-499a-a5c1-c1e0bd306b48
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8ed580b022e9896ade824c8cf8eccc2458c7ddce
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="moduleref-modulerefcollection-node"></a>ModuleRef (nœud ModuleRefCollection)
Le nœud ModuleRef d'un fichier de liaison contient des informations spécifiques sur un assembly .NET exporté avec ce fichier. Un nœud ModuleRef peut comporter, entre autres, des descriptions d'assemblys qui contiennent un code personnalisé, des schémas et des orchestrations.  
  
## <a name="nodes-in-the-moduleref-node"></a>Nœuds du nœud ModuleRef  
 Le tableau suivant répertorie les propriétés que vous pouvez définir pour ce nœud d'un fichier de liaison :  
  
|**Nom**|**Type de nœud**|**Type de données**|**Description**|**Restrictions**|**Commentaires**|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|[Services](../core/services-moduleref-node.md)|Record|ArrayOfServiceRef (ComplexType)|Nœud conteneur pour les services associés à cet assembly .NET.|Facultatif|Valeur par défaut : Aucun|  
|[TrackedSchemas (nœud ModuleRef)](../core/trackedschemas-moduleref-node.md)|Record|ArrayOfSchema (ComplexType)|Nœud conteneur pour les schémas associés à cet assembly .NET.|Facultatif|Valeur par défaut : Aucun|