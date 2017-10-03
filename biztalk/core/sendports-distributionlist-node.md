---
title: "SendPorts (nœud DistributionList) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: SendPorts node [binding file]
ms.assetid: 9cb645fa-cb9c-44eb-9f98-2fc507b2be67
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a9eaf692bd61913e604731fc2e2cea373fd31f48
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="sendports-distributionlist-node"></a>SendPorts (nœud DistributionList)
Le nœud SendPorts du nœud DistributionList d'un fichier de liaison est le nœud conteneur des références de port d'envoi dans la liste de distribution.  
  
> [!NOTE]
>  Une liste de distribution est appelée groupe de ports d'envoi dans l'Administrateur BizTalk.  
  
## <a name="nodes-in-the-sendports-node"></a>Nœuds du nœud SendPorts  
 Le tableau suivant répertorie les propriétés que vous pouvez définir pour ce nœud d'un fichier de liaison :  
  
|**Nom**|**Type de nœud**|**Type de données**|**Description**|**Restrictions**|**Commentaires**|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|[SendPortRef](../core/sendportref-sendports-node.md)|Record|SendPortRef (ComplexType)|Nœud conteneur pour une référence à un port d'envoi effectuée par la liste de distribution.|Facultatif|Valeur par défaut : Aucun|