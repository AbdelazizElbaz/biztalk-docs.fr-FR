---
title: SendHandler (nœud SecondaryTransport) | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SendHandler node [binding file]
ms.assetid: 32eb3e87-25ac-461e-9c09-3d6d9bcba3b2
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1f5ecdbb1860c9132133835b8928f85b1e0e1cfb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="sendhandler-secondarytransport-node"></a>SendHandler (nœud SecondaryTransport)
Le nœud SendHandler du nœud SecondaryTransport d'un fichier de liaison contient des informations sur le gestionnaire d'envoi associé à un transport exporté avec le fichier de liaison.  
  
## <a name="nodes-in-the-sendhandler-node"></a>Nœuds du nœud SendHandler  
 Le tableau suivant répertorie les propriétés que vous pouvez définir pour ce nœud d'un fichier de liaison :  
  
|**Nom**|**Type de nœud**|**Type de données**|**Description**|**Restrictions**|**Commentaires**|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|Nom|Attribut|xs:string|Spécifie le nom du gestionnaire d'envoi associé au transport.|Facultatif|Valeur par défaut : vide|  
|HostTrusted|Attribut|xs:boolean|Spécifie si l'hôte associé au gestionnaire d'envoi est approuvé.|Requis|Valeur par défaut : Aucun<br /><br /> La valeur **true** si l’hôte est approuvé, sinon la valeur **false**.|  
|[TransportType (nœud SendHandler)](../core/transporttype-sendhandler-node.md)|Record|ProtocolType (ComplexType)|Spécifie le type de transport, qui correspond également au nom de l'adaptateur utilisé avec ce gestionnaire d'envoi.|Requis|Valeur par défaut : Aucun|