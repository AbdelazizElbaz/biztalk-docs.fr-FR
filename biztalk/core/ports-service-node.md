---
title: "Ports (nœud de Service) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Ports node [binding file]
ms.assetid: 498d4310-4e9e-4e74-bc3d-5cbf1319c4ff
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 31e09470b9f3287cce5ce15c2941d2165157ec48
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="ports-service-node"></a>Ports (nœud de service)
Le nœud Ports d'un fichier de liaison est le nœud parent de tous les nœuds Port qui contiennent des informations spécifiques sur les ports liés à un service exporté avec le fichier de liaison.  
  
## <a name="node-in-the-ports-node"></a>Nœud du nœud Ports  
 Le tableau suivant répertorie les propriétés que vous pouvez définir pour ce nœud d'un fichier de liaison :  
  
|**Nom**|**Type de nœud**|**Type de données**|**Description**|**Restrictions**|**Commentaires**|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|[Port](../core/port-ports-node.md)|Record|ServicePortRef (ComplexType)|Spécifie des informations sur un port lié à un service exporté avec le fichier de liaison.|Facultatif|Valeur par défaut : Aucun|