---
title: DistributionList (nœud DistributionListCollection) | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- DistributionList node [binding file]
ms.assetid: 51864a5c-1697-4804-ac18-8211494f3ff0
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 931443cdca27e5c06767f075298d50ff999545a0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="distributionlist-distributionlistcollection-node"></a>DistributionList (Nœud DistributionListCollection)
Le nœud DistributionList d'un fichier de liaison contient des informations spécifiques sur la liste de distribution exportée avec ce fichier. Une liste de distribution est appelée groupe de ports d'envoi dans l'Administrateur BizTalk Server.  
  
## <a name="nodes-in-the-distributionlist-node"></a>Nœuds du nœud DistributionList  
 Le tableau suivant répertorie les propriétés que vous pouvez définir pour ce nœud d'un fichier de liaison :  
  
|**Nom**|**Type de nœud**|**Type de données**|**Description**|**Restrictions**|**Commentaires**|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|Nom|Attribut|xs:string|Spécifie le nom de la liste de distribution.|Facultatif|Valeur par défaut : vide|  
|[Ports d’envoi](../core/sendports-distributionlist-node.md)|Record|ArrayOfSendPortRef (ComplexType)|Spécifie le port d'envoi ou les ports d'envoi inclus dans la liste de distribution.|Facultatif|Valeur par défaut : Aucun|  
|Filtrer|Élément|xs:string|Spécifie le nom de l'expression de filtre facultative utilisée pour la liste de distribution.|Requis|Valeur par défaut : vide|  
|ApplicationName|Élément|xs:string|Spécifie le nom de l'application à laquelle est associée la liste de distribution.|Requis|Valeur par défaut : vide|  
| Description|Élément|xs:string|Spécifie une description pour la liste de distribution.|Requis|Valeur par défaut : vide|