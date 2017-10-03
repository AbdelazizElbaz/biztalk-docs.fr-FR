---
title: "ReceivePipeline (nœud ReceiveLocation) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: ReceivePipeline node [binding file]
ms.assetid: bd90ca2d-21e4-4d21-bc67-f16a150053e4
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 122ffcfe7fe2d2cfc49b51c98b7251a19f5a0e31
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="receivepipeline-receivelocation-node"></a>ReceivePipeline (nœud ReceiveLocation)
Le nœud ReceivePipeline du nœud ReceiveLocation d'un fichier de liaison contient des informations spécifiques sur le pipeline de réception utilisé avec un emplacement de réception exporté avec le fichier de liaison.  
  
## <a name="nodes-in-the-receivepipeline-node"></a>Nœuds du nœud ReceivePipeline  
 Le tableau suivant répertorie les propriétés que vous pouvez définir pour ce nœud d'un fichier de liaison :  
  
|**Nom**|**Type de nœud**|**Type de données**|**Description**|**Restrictions**|**Commentaires**|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|Nom|Attribut|xs:string|Spécifie le nom du pipeline de réception.|Facultatif|Valeur par défaut : vide|  
|FullyQualifiedName|Attribut|xs:string|Indique le nom complet du pipeline, qui inclut le nom de l'assembly dans le cadre duquel le pipeline a été déployé.|Facultatif|Valeur par défaut : vide|  
|Type|Attribut|xs:int|Indique le type du pipeline.|Requis|Valeur par défaut : Aucun<br /><br /> Les valeurs possibles sont présentées dans l'énumération<br /><br /> [Microsoft.BizTalk.ExplorerOM.PipelineType](http://msdn.microsoft.com/library/microsoft.biztalk.explorerom.pipelinetype.aspx) énumération.|  
|TrackingOption|Attribut|PipelineTrackingTypes (SimpleType)|Spécifie les options de suivi pour le pipeline.|Requis|Valeur par défaut : Aucun<br /><br /> Les valeurs possibles sont documentées dans l'énumération [Microsoft.BizTalk.ExplorerOM.PipelineTrackingTypes](http://msdn.microsoft.com/library/microsoft.biztalk.explorerom.pipelinetrackingtypes.aspx) .|  
|Description|Attribut|xs:string|Spécifie une description pour le pipeline de réception.|Facultatif|Valeur par défaut : vide|