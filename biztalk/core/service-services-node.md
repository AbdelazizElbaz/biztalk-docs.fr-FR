---
title: "Service (nœud Services) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Service node [binding file]
ms.assetid: 19e977b4-55bd-453f-9053-5590b9553b07
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 834555f43620d428d18a04938e18612793b2ab51
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="service-services-node"></a>Service (nœud Services)
Le nœud Service d'un fichier de liaison contient des informations spécifiques sur un service exporté avec ce fichier. Le nœud Service contient également des nœuds qui décrivent les ports et les rôles associés au service et un nœud décrivant l'hôte associé au service.  
  
## <a name="nodes-in-the-service-node"></a>Nœuds du nœud Service  
 Le tableau suivant répertorie les propriétés que vous pouvez définir pour ce nœud d'un fichier de liaison :  
  
|**Nom**|**Type de nœud**|**Type de données**|**Description**|**Restrictions**|**Commentaires**|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|Nom|Attribut|xs:string|Spécifie le nom du service.|Requis|Valeur par défaut : vide|  
|État|Attribut|ServiceRefState (SimpleType)|Indique l'état du service.|Requis|Valeur par défaut : par défaut<br /><br /> Les valeurs possibles sont :<br /><br /> -Par défaut<br />-Désinscrit<br />-Inscrite<br />-Started|  
|TrackingOption|Attribut|OrchestrationTrackingTypes (SimpleType)|Spécifie les options de suivi des messages pour le service.|Requis|Valeur par défaut : Aucun<br /><br /> Les valeurs possibles sont celles qui sont disponibles dans le [Microsoft.BizTalk.ExplorerOM.OrchestrationTrackingTypes](http://msdn.microsoft.com/library/microsoft.biztalk.explorerom.orchestrationtrackingtypes.aspx) énumération.|  
| Description|Attribut|xs:string|Spécifie une description pour le service.|Facultatif|Valeur par défaut : vide|  
|[Ports](../core/ports-service-node.md)|Record|ArrayOfServicePortRef (ComplexType)|Nœud du conteneur pour les ports liés au service.|Facultatif|Valeur par défaut : Aucun|  
|[Roles](../core/roles-service-node.md)|Record|ArrayOfRoleRef (ComplexType)|Nœud du conteneur pour les rôles liés au service.|Facultatif|Valeur par défaut : Aucun|  
|[Ordinateur hôte](../core/host-service-node.md)|Record|HostRef (ComplexType)|Nœud du conteneur pour l'hôte lié au service.|Requis|Valeur par défaut : Aucun|