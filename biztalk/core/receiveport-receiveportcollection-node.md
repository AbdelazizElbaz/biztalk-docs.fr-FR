---
title: "ReceivePort (nœud ReceivePortCollection) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 30ae9cef-4e0f-42ca-ac45-fe1fabdfc7c5
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: da486df8bf406ca61f0b06d2cbc6f9b3f16539cf
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="receiveport-receiveportcollection-node"></a>ReceivePort (Nœud ReceivePortCollection)
Le nœud ReceivePort du nœud ReceivePortCollection d'un fichier de liaison contient des informations spécifiques sur un port de réception exporté avec le fichier de liaison.  
  
## <a name="nodes-in-the-receiveport-node"></a>Nœuds du nœud ReceivePort  
 Le tableau suivant répertorie les propriétés que vous pouvez définir pour ce nœud d'un fichier de liaison :  
  
|**Nom**|**Type de nœud**|**Type de données**|**Description**|**Restrictions**|**Commentaires**|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|Nom|Attribut|xs:string|Indique le nom du port de réception.|Facultatif|Valeur par défaut : vide|  
|IsTwoWay|Attribut|xs:boolean|Indique si le port de réception est unidirectionnel ou bidirectionnel (requête-réponse).|Requis|Valeur par défaut : Aucun<br /><br /> Les valeurs possibles sont dans le **propriété MSBTS_SendPort.IsTwoWay (WMI)**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]|  
|BindingOption|Attribut|xs:int|Spécifie le type de liaison du port d’orchestration.|Requis|Valeur par défaut : Aucun<br /><br /> Les valeurs possibles sont dans le **Microsoft.BizTalk.ExplorerOM.BindingType** énumération.|  
| Description|Élément|xs:string|Spécifie une description pour le port de réception.|Requis|Valeur par défaut : vide|  
|[ReceiveLocations](../core/receivelocations-receiveport-node.md)|Record|ArrayOfReceiveLocation (ComplexType)|Nœud du conteneur pour les emplacements de réception associés à ce port de réception.|Non requis.|Valeur par défaut : Aucun|  
|[TransmitPipeline (nœud ReceivePort)](../core/transmitpipeline-receiveport-node.md)|Record|PipelineRef (ComplexType)|Spécifie le pipeline d’envoi associé au port de réception si ce dernier est un port de réception bidirectionnel.|Facultatif|Valeur par défaut : Aucun|  
|SendPipelineData|Élément|xs:string|Spécifie la configuration personnalisée spécifique à cette instance de l’utilisation du pipeline.|Facultatif|Valeur par défaut : vide.|  
|Authentification|Élément|xs:int|Spécifie une valeur d’énumération indiquant s'il est nécessaire de s'authentifier auprès de ce port de réception.|Requis|Valeur par défaut : Aucun<br /><br /> Les valeurs possibles sont dans le **Microsoft.BizTalk.ExplorerOM.AuthenticationType** énumération.|  
|Suivi|Élément|xs:int|Spécifie le niveau de suivi des documents pour le port de réception.|Requis|Valeur par défaut : Aucun<br /><br /> Les valeurs possibles sont dans le **Microsoft.BizTalk.ExplorerOM.TrackingTypes** énumération.|  
|[TRANSFORMS (nœud ReceivePort)](../core/transforms-receiveport-node.md)|Record|ArrayOfTransform (ComplexType)|Spécifie la collection des transformations en entrée d'un port de réception unidirectionnel.|Facultatif|Valeur par défaut : Aucun|  
|[OutboundTransforms](../core/outboundtransforms-receiveport-node.md)|Record|ArrayOfTransform (ComplexType)|Spécifie la collection des transformations en sortie à appliquer aux documents sur un port de réception bidirectionnel.|Facultatif|Valeur par défaut : Aucun|  
|RouteFailedMessage|Élément|xs:boolean|Spécifie si les messages qui ont échoué doivent ou non être acheminés vers les abonnés aux messages ayant échoué.|Requis|Valeur par défaut : Aucun<br /><br /> Les valeurs possibles sont dans le **propriété MSBTS_SendPort.RouteFailedMessage (WMI)**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]|  
|ApplicationName|Élément|xs:string|Spécifie le nom de l'application associée au port de réception.|Requis|Valeur par défaut : vide<br /><br /> Les valeurs possibles sont dans le **Interface ISSOMapping (COM)**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]|