---
title: SendHandler (nœud PrimaryTransport) | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SendHandler node [binding file]
ms.assetid: c0b200ee-ecbc-4708-a2c8-c37cd6cd0060
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 029285e9b56aeb91bbca7a7c9eacf6abedc7ebbc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="sendhandler-primarytransport-node"></a>SendHandler (nœud PrimaryTransport)
Le nœud SendHandler du nœud PrimaryTransport d'un fichier de liaison contient des informations sur le gestionnaire d'envoi associé à un transport exporté avec ce fichier de liaison.  
  
## <a name="nodes-in-the-sendhandler-node"></a>Nœuds du nœud SendHandler  
 Le tableau suivant répertorie les propriétés que vous pouvez définir pour ce nœud d'un fichier de liaison :  
  
|**Nom**|**Type de nœud**|**Type de données**|**Description**|**Restrictions**|**Commentaires**|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|Nom|Attribut|xs:string|Spécifie le nom du gestionnaire d'envoi associé au transport.|Facultatif|Valeur par défaut : vide|  
|HostTrusted|Attribut|xs:boolean|Spécifie si l'hôte associé au gestionnaire d'envoi est approuvé.|Requis|Valeur par défaut : Aucun<br /><br /> La valeur **true** si l’hôte est approuvé, sinon la valeur **false**.|  
|[Type de transport](../core/transporttype.md)|Record|ProtocolType (ComplexType)|Spécifie le type de transport, qui correspond également au nom de l'adaptateur utilisé avec ce gestionnaire d'envoi.|Requis|Valeur par défaut : Aucun|