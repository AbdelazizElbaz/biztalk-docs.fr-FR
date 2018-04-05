---
title: Hôte (nœud de Service) | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Host node [binding file]
ms.assetid: 597522db-0336-43b1-b464-d17cffbf25be
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a9c70c23105a8d2f2ebe389b22ddf910b4166994
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="host-service-node"></a>Hôte (nœud de service)
Le nœud Hôte du nœud Service d'un fichier de liaison décrit l'hôte associé au service exporté avec le fichier de liaison.  
  
## <a name="nodes-in-the-host-node"></a>Nœuds du nœud Hôte  
 Le tableau suivant répertorie les propriétés que vous pouvez définir pour ce nœud d'un fichier de liaison :  
  
|**Nom**|**Type de nœud**|**Type de données**|**Description**|**Restrictions**|**Commentaires**|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|Nom|Attribut|xs:string|Spécifie le nom de l'hôte.|Facultatif|Valeur par défaut : vide|  
|NTGroupName|Attribut|xs:string|Indique le nom du groupe Windows NT associé à l'hôte.|Facultatif|Valeur par défaut : vide|  
|Type|Attribut|xs:int|Spécifie le type d'hôte en tant qu'hôte in-process ou isolé.|Requis|Valeur par défaut : Aucun<br /><br /> Les valeurs possibles sont décrites dans le [Microsoft.BizTalk.ExplorerOM.HostType](http://msdn.microsoft.com/library/microsoft.biztalk.explorerom.hosttype.aspx) énumération.|  
|Approuvée|Attribut|xs:boolean|Spécifie si l'hôte BizTalk est autorisé à collecter les informations d'authentification.|Requis|Valeur par défaut : Aucun<br /><br /> La valeur **true** si l’hôte est approuvé, sinon la valeur **false**.|