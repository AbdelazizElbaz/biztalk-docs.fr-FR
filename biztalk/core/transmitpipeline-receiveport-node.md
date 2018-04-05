---
title: TransmitPipeline (nœud ReceivePort) | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- TransmitPipeline node [binding file]
ms.assetid: 0f3b728f-1e4a-40e5-9ca9-f7dcdf995cbe
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 64b17179b7131839dc369e9bdecf5e40dd831e4d
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="transmitpipeline-receiveport-node"></a>TransmitPipeline (nœud ReceivePort)
Le nœud TransmitPipeline du nœud ReceivePort d'un fichier de liaison fournit des informations spécifiques sur le pipeline d'envoi associé à un emplacement de réception bidirectionnel qui est exporté avec le fichier de liaison.  
  
> [!NOTE]
>  Depuis l’envoi de pipelines pour les réceptions bidirectionnelles sont liés au niveau d’emplacement de réception dans BizTalk Server, ce nœud est fourni pour compatibilité descendante avec BizTalk Server 2004. Envoyer des pipelines pour les réceptions bidirectionnelles sont liés au niveau du port de réception dans BizTalk Server 2004. Les propriétés qui sont définies pour ce nœud d’un fichier de liaison qui a été exporté à partir de BizTalk Server 2004 seront appliquées au nœud SendPipeline de chaque emplacement de réception bidirectionnel référencé par le port de réception lors de l’importation du fichier de liaison dans BizTalk Server.  
  
## <a name="nodes-in-the-transmitpipeline-node"></a>Nœuds du nœud TransmitPipeline  
 Le tableau suivant répertorie les propriétés que vous pouvez définir pour ce nœud d'un fichier de liaison :  
  
|**Nom**|**Type de nœud**|**Type de données**|**Description**|**Restrictions**|**Commentaires**|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|Nom|Attribut|xs:string|Indique le nom du pipeline d'envoi.|Facultatif|Valeur par défaut : vide|  
|FullyQualifiedName|Attribut|xs:string|Spécifie le nom qualifié complet du pipeline, qui inclut le nom de l’assembly que le pipeline a été déployé dans le cadre de.|Facultatif|Valeur par défaut : vide|  
|Type|Attribut|xs:int|Indique le type du pipeline.|Requis|Valeur par défaut : Aucun<br /><br /> Les valeurs possibles sont présentées dans l'énumération<br /><br /> [Microsoft.BizTalk.ExplorerOM.PipelineType](http://msdn.microsoft.com/library/microsoft.biztalk.explorerom.pipelinetype.aspx) énumération.|  
|TrackingOption|Attribut|PipelineTrackingTypes (SimpleType)|Spécifie les options de suivi pour le pipeline.|Requis|Valeur par défaut : Aucun<br /><br /> Les valeurs possibles sont documentées dans l'énumération [Microsoft.BizTalk.ExplorerOM.PipelineTrackingTypes](http://msdn.microsoft.com/library/microsoft.biztalk.explorerom.pipelinetrackingtypes.aspx) .|  
|Description|Attribut|xs:string|Spécifie une description pour le pipeline d'envoi.|Facultatif|Valeur par défaut : vide|  
  
## <a name="see-also"></a>Voir aussi  
 [Pipeline d’envoi](../core/sendpipeline-receivelocation-node.md)   
 [ReceiveLocation](../core/receivelocation-receivelocations-node.md)