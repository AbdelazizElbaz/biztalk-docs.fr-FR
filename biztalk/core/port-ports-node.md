---
title: "Port (nœud Ports) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Port node [binding file]
ms.assetid: 6c9a3e5f-0b3c-40f8-9a8d-5a83bd559021
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 01a808f4415019ba48deb1b3b80ad8aae9e1db04
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="port-ports-node"></a>Port (Nœud Ports)
Le nœud port d'un fichier de liaison contient des informations spécifiques sur un port ou une liste de distribution liée à un service exporté avec le fichier de liaison.  
  
> [!NOTE]
>  Une liste de distribution est référencée comme un groupe de ports d'envoi dans la console Administration de BizTalk Server.  
  
## <a name="nodes-in-the-port-node"></a>Nœuds du nœud Port  
 Le tableau suivant répertorie les propriétés que vous pouvez définir pour ce nœud d'un fichier de liaison :  
  
|**Nom**|**Type de nœud**|**Type de données**|**Description**|**Restrictions**|**Commentaires**|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|Nom|Attribut|xs:string|Spécifie le nom du port.|Facultatif|Valeur par défaut : vide|  
|Modificateur|Attribut|xs:int|Spécifie le modificateur de type pour le port.|Requis|Valeur par défaut : Aucun<br /><br /> Les valeurs possibles sont celles qui sont disponibles dans le [Microsoft.BizTalk.ExplorerOM.PortModifier](http://msdn.microsoft.com/library/microsoft.biztalk.explorerom.portmodifier.aspx) énumération.|  
|BindingOption|Attribut|xs:int|Définit le type de liaison pour le port.|Requis|Valeur par défaut : Aucun<br /><br /> Les valeurs possibles sont celles qui sont disponibles dans le [Microsoft.BizTalk.ExplorerOM.BindingType](http://msdn.microsoft.com/library/microsoft.biztalk.explorerom.bindingtype.aspx) énumération.|  
|[SendPortRef](../core/sendportref-port-node.md)|Record|SendPortRef (ComplexType)|Nœud du conteneur pour les ports d'envoi référencés par un service.|Facultatif|Valeur par défaut : vide|  
|[DistributionListRef](../core/distributionlistref-port-node.md)|Record|DistributionListRef (ComplexType)|Nœud du conteneur pour les listes de distribution référencées par un service.|Facultatif|Valeur par défaut : vide|  
|[ReceivePortRef](../core/receiveportref-port-node.md)|Record|ReceivePortRef (ComplexType)|Nœud du conteneur pour les ports de réception référencés par un service.|Facultatif|Valeur par défaut : vide|