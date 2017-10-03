---
title: "Pipeline d’envoi (nœud ReceiveLocation) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: SendPipeline node [binding file]
ms.assetid: 7dcad2f1-b11f-4015-9067-b7ba40ee6cda
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 03f09d15f66d558e6d1aedf00054c6bea9397af9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="sendpipeline-receivelocation-node"></a>SendPipeline (nœud ReceiveLocation)
Le nœud SendPipeline du nœud ReceiveLocation d'un fichier de liaison fournit des informations spécifiques sur le pipeline d'envoi associé à un emplacement de réception qui est exporté avec le fichier de liaison.  
  
## <a name="nodes-in-the-sendpipeline-node"></a>Nœuds du nœud SendPipeline  
 Le tableau suivant répertorie les propriétés que vous pouvez définir pour ce nœud d'un fichier de liaison :  
  
|**Nom**|**Type de nœud**|**Type de données**|**Description**|**Restrictions**|**Commentaires**|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|Nom|Attribut|xs:string|Indique le nom du pipeline d'envoi.|Facultatif|Valeur par défaut : vide|  
|FullyQualifiedName|Attribut|xs:string|Indique le nom complet du pipeline, qui inclut le nom de l'assembly dans le cadre duquel le pipeline a été déployé.|Facultatif|Valeur par défaut : vide|  
|Type|Attribut|xs:int|Indique le type du pipeline.|Requis|Valeur par défaut : Aucun<br /><br /> Les valeurs possibles sont présentées dans l'énumération<br /><br /> [Microsoft.BizTalk.ExplorerOM.PipelineType](http://msdn.microsoft.com/library/microsoft.biztalk.explorerom.pipelinetype.aspx) énumération.|  
|TrackingOption|Attribut|PipelineTrackingTypes (SimpleType)|Spécifie les options de suivi pour le pipeline.|Requis|Valeur par défaut : Aucun<br /><br /> Les valeurs possibles sont documentées dans l'énumération [Microsoft.BizTalk.ExplorerOM.PipelineTrackingTypes](http://msdn.microsoft.com/library/microsoft.biztalk.explorerom.pipelinetrackingtypes.aspx) .|  
|Description|Attribut|xs:string|Spécifie une description pour le pipeline d'envoi.|Facultatif|Valeur par défaut : vide|