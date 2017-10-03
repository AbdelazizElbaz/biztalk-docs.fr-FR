---
title: "TransmitPipeline (nœud SendPort) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: TransmitPipeline node [binding file]
ms.assetid: cee55451-6c3f-4e37-aef9-870d4b5d23aa
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4addad5ea98781865b44470f2d07b577afce6c0f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="transmitpipeline-sendport-node"></a>TransmitPipeline (nœud SendPort)
Le nœud TransmitPipeline du nœud SendPort d'un fichier de liaison fournit des informations spécifiques sur le pipeline d'envoi associé à un port d'envoi exporté avec un fichier de liaison.  
  
## <a name="nodes-in-the-transmitpipeline-node"></a>Nœuds du nœud TransmitPipeline  
 Le tableau suivant répertorie les propriétés que vous pouvez définir pour ce nœud d'un fichier de liaison :  
  
|**Nom**|**Type de nœud**|**Type de données**|**Description**|**Restrictions**|**Commentaires**|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|Nom|Attribut|xs:string|Indique le nom du pipeline d'envoi.|Facultatif|Valeur par défaut : vide|  
|FullyQualifiedName|Attribut|xs:string|Indique le nom complet du pipeline, qui inclut le nom de l'assembly dans le cadre duquel le pipeline a été déployé.|Facultatif|Valeur par défaut : vide|  
|Type|Attribut|xs:int|Indique le type du pipeline.|Requis|Valeur par défaut : Aucun<br /><br /> Les valeurs possibles sont documentées dans l'énumération [Microsoft.BizTalk.ExplorerOM.PipelineType](http://msdn.microsoft.com/library/microsoft.biztalk.explorerom.pipelinetype.aspx) .|  
|TrackingOption|Attribut|PipelineTrackingTypes (SimpleType)|Spécifie les options de suivi pour le pipeline.|Requis|Valeur par défaut : Aucun<br /><br /> Les valeurs possibles sont documentées dans l'énumération [Microsoft.BizTalk.ExplorerOM.PipelineTrackingTypes](http://msdn.microsoft.com/library/microsoft.biztalk.explorerom.pipelinetrackingtypes.aspx) .|  
|Description|Attribut|xs:string|Spécifie une description pour le pipeline d'envoi.|Facultatif|Valeur par défaut : vide|