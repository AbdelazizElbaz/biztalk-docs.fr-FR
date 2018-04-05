---
title: ReceiveHandler (nœud ReceiveLocation) | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ReceiveHandler node [binding file]
ms.assetid: dd105052-ec71-4762-aa74-e8cdb806a6bf
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e865886624731414f979c77f3f2e898e417c8b11
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="receivehandler-receivelocation-node"></a>ReceiveHandler (nœud ReceiveLocation)
Le nœud ReceiveHandler du nœud ReceiveLocation d'un fichier de liaison contient des informations sur le gestionnaire de réception associé à un transport exporté avec le fichier de liaison.  
  
## <a name="nodes-in-the-receivehandler-node"></a>Nœuds du nœud ReceiveHandler  
 Le tableau suivant répertorie les propriétés que vous pouvez définir pour ce nœud d'un fichier de liaison :  
  
|**Nom**|**Type de nœud**|**Type de données**|**Description**|**Restrictions**|**Commentaires**|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|Nom|Attribut|xs:string|Spécifie le nom du gestionnaire de réception associé au transport.|Facultatif|Valeur par défaut : vide|  
|HostTrusted|Attribut|xs:boolean|Spécifie si l'hôte associé au gestionnaire de réception est approuvé.|Requis|Valeur par défaut : Aucun<br /><br /> La valeur **true** si l’hôte est approuvé, sinon la valeur **false**.|  
|[TransportType (nœud ReceiveHandler)](../core/transporttype-receivehandler-node.md)|Record|ProtocolType (ComplexType)|Spécifie le type de transport, qui correspond également au nom de l'adaptateur utilisé avec ce gestionnaire de réception.|Requis|Valeur par défaut : Aucun|