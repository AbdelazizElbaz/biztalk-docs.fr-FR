---
title: "SendPort (nœud SendPortCollection) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5cf7a6f9-9240-48b9-b196-8838afd4f41e
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 43db1aa63fb828ebbc0ee6d857ce79968b846aea
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="sendport-sendportcollection-node"></a>SendPort (Nœud SendPortCollection)
Le nœud SendPort d'un fichier de liaison contient des informations spécifiques sur un port d'envoi exporté avec ce fichier.  
  
## <a name="nodes-in-the-sendport-node"></a>Nœuds du nœud SendPort  
 Le tableau suivant répertorie les propriétés que vous pouvez définir pour ce nœud d'un fichier de liaison :  
  
|**Nom**|**Type de nœud**|**Type de données**|**Description**|**Restrictions**|**Commentaires**|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|Nom|Attribut|xs:string|Spécifie le nom du port d'envoi.|Facultatif|Valeur par défaut : vide|  
|IsStatic|Attribut|xs:boolean|Indique si le port d'envoi est statique ou dynamique.|Requis|Valeur par défaut : Aucun|  
|IsTwoWay|Attribut|xs:boolean|Indique si le port d'envoi est unidirectionnel ou de type sollicitation-réponse (bidirectionnel).|Requis|Valeur par défaut : Aucun<br /><br /> Les valeurs possibles sont dans le **propriété MSBTS_SendPort.IsTwoWay (WMI)**.|  
|BindingOption|Attribut|xs:int|Spécifie le type de liaison du port d’orchestration.|Requis|Valeur par défaut : Aucun<br /><br /> Les valeurs possibles sont dans le **Microsoft.BizTalk.ExplorerOM.BindingType** énumération.|  
| Description|Élément|xs:string|Spécifie une description pour le port d'envoi.|Requis|Valeur par défaut : vide|  
|[TransmitPipeline (nœud SendPort)](../core/transmitpipeline-sendport-node.md)|Record|PipelineRef (ComplexType)|Spécifie le pipeline d'envoi associé au port d'envoi.|Facultatif|Valeur par défaut : Aucun|  
|SendPipelineData|Élément|xs:string|Spécifie la configuration personnalisée spécifique à cette instance de l’utilisation du pipeline.|Facultatif|Valeur par défaut : vide.|  
|[PrimaryTransport](../core/primarytransport-sendport-node.md)|Record|TransportInfo (ComplexType)|Spécifie les informations relatives au transport principal pour lequel le port d'envoi est configuré.|Facultatif|Valeur par défaut : Aucun|  
|[SecondaryTransport](../core/secondarytransport-sendport-node.md)|Record|TransportInfo (ComplexType)|Spécifie les informations relatives au transport secondaire pour lequel le port d'envoi est configuré.|Facultatif|Valeur par défaut : Aucun|  
|[EncryptionCert](../core/encryptioncert-sendport-node.md)|Record|CertificateInfo (ComplexType)|Spécifie les informations relatives au certificat de chiffrement utilisé avec le port d'envoi.|Facultatif|Valeur par défaut : Aucun|  
|[ReceivePipeline](../core/receivepipeline-sendport-node.md)|Record|PipelineRef (ComplexType)|Spécifie les informations relatives aux pipelines de réception utilisés avec le port d'envoi.|Facultatif|Valeur par défaut : Aucun|  
|ReceivePipelineData|Élément|xs:string|Spécifie la configuration personnalisée spécifique à cette instance de l’utilisation du pipeline.|Requis|Valeur par défaut : vide|  
|Suivi|Élément|xs:int|Spécifie le niveau de suivi des documents pour le port d'envoi.|Requis|Valeur par défaut : Aucun<br /><br /> Les valeurs possibles sont dans le **Microsoft.BizTalk.ExplorerOM.TrackingTypes** énumération.|  
|Filtrer|Élément|xs:string|Spécifie le nom de l'expression de filtre facultative utilisée pour le port d'envoi.|Requis|Valeur par défaut : vide<br /><br /> Les valeurs possibles sont dans le **propriété MSBTS_SendPort.Filter (WMI)**|  
|[TRANSFORMS (nœud SendPort)](../core/transforms-sendport-node.md)|Record|ArrayOfTransform (ComplexType)|Spécifie la collection des transformations en sortie d'un port d'envoi unidirectionnel.|Facultatif|Valeur par défaut : Aucun|  
|[InboundTransforms](../core/inboundtransforms-sendport-node.md)|Record|ArrayOfTransform (ComplexType)|Spécifie la collection des transformations en entrée d'un port d'envoi bidirectionnel.|Facultatif|Valeur par défaut : Aucun|  
|OrderedDelivery|Élément|xs:boolean|Indique si le port d'envoi livre les messages de manière chronologique ou pas.|Requis|Valeur par défaut : Aucun<br /><br /> Les valeurs possibles sont dans le **propriété MSBTS_SendPort.OrderedDelivery (WMI)**|  
|Priorité|Élément|xs:int|Spécifie la priorité du port d'envoi.|Requis|Valeur par défaut : 5<br /><br /> Les valeurs possibles sont dans le **propriété MSBTS_SendPort.Priority (WMI)**|  
|StopSendingOnFailure|Élément|xs:boolean|Indique si le port d'envoi arrête ou non d'envoyer des messages en cas d'échec.|Requis|Valeur par défaut : Aucun<br /><br /> Les valeurs possibles sont dans le **propriété MSBTS_SendPort.StopSendingOnFailure (WMI)**|  
|RouteFailedMessage|Élément|xs:boolean|Spécifie si les messages qui ont échoué doivent ou non être acheminés vers les abonnés aux messages ayant échoué.|Requis|Valeur par défaut : Aucun<br /><br /> Les valeurs possibles sont dans le **propriété MSBTS_SendPort.RouteFailedMessage (WMI)**|  
|ApplicationName|Élément|xs:string|Spécifie le nom de l'application associée au port d'envoi.|Requis|Valeur par défaut : vide<br /><br /> Les valeurs possibles sont dans le **propriété ISSOMapping.ApplicationName** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].|

## <a name="see-also"></a>Voir aussi
Plus d’informations sur ces propriétés [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].