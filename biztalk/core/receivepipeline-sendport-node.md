---
title: "ReceivePipeline (nœud SendPort) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: ReceivePipeline node [binding file]
ms.assetid: 5305f255-e7a2-4052-bf50-4fb207cfae8d
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 210c54b18cc174f31ff795a657f7d23044cebc58
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="receivepipeline-sendport-node"></a>ReceivePipeline (Nœud SendPort)
Le nœud ReceivePipeline du nœud SendPort d'un fichier de liaison contient des informations spécifiques sur le pipeline de réception lié à un port d'envoi bidirectionnel qui est exporté avec le fichier de liaison.  
  
## <a name="nodes-in-the-receivepipeline-node"></a>Nœuds du nœud ReceivePipeline  
 Le tableau suivant répertorie les propriétés que vous pouvez définir pour ce nœud d'un fichier de liaison :  
  
|**Nom**|**Type de nœud**|**Type de données**|**Description**|**Restrictions**|**Commentaires**|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|Nom|Attribut|xs:string|Indique le nom du pipeline d'envoi.|Facultatif|Valeur par défaut : vide|  
|FullyQualifiedName|Attribut|xs:string|Spécifie le nom qualifié complet du pipeline, qui inclut le nom de l’assembly que le pipeline a été déployé dans le cadre de.|Facultatif|Valeur par défaut : vide|  
|Type|Attribut|xs:int|Indique le type du pipeline.|Requis|Valeur par défaut : Aucun<br /><br /> Les valeurs possibles sont présentées dans l'énumération<br /><br /> [Microsoft.BizTalk.ExplorerOM.PipelineType](http://msdn.microsoft.com/library/microsoft.biztalk.explorerom.pipelinetype.aspx) énumération.|  
|TrackingOption|Attribut|PipelineTrackingTypes (SimpleType)|Spécifie les options de suivi pour le pipeline.|Requis|Valeur par défaut : Aucun<br /><br /> Les valeurs possibles sont documentées dans l'énumération [Microsoft.BizTalk.ExplorerOM.PipelineTrackingTypes](http://msdn.microsoft.com/library/microsoft.biztalk.explorerom.pipelinetrackingtypes.aspx) .|  
|Description|Attribut|xs:string|Spécifie une description pour le pipeline d'envoi.|Facultatif|Valeur par défaut : vide|