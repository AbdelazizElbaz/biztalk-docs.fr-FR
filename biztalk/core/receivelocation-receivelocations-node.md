---
title: Emplacement de réception (nœud ReceiveLocations) | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ReceiveLocation node [binding file]
ms.assetid: 706ec5b2-c26f-428a-ad56-1c01b34aa8f8
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f959dfc9aadfbf317d3843fb0ed174a2a0f22ea3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="receivelocation-receivelocations-node"></a>ReceiveLocation (nœud ReceiveLocations)
Le nœud ReceiveLocation du noeud ReceiveLocations d'un fichier de liaison contient des informations spécifiques sur un port de réception exporté avec le fichier de liaison.  
  
## <a name="nodes-in-the-receivelocation-node"></a>Nœuds du nœud ReceiveLocation   
 Le tableau suivant répertorie les propriétés que vous pouvez définir pour ce nœud d'un fichier de liaison :  
  
|**Nom**|**Type de nœud**|**Type de données**|**Description**|**Restrictions**|**Commentaires**|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|Nom|Attribut|xs:string|Spécifie le nom de l'emplacement de réception.|Facultatif|Valeur par défaut : vide|  
| Description|Élément|xs:string|Spécifie une description pour l'emplacement de réception.|Requis|Valeur par défaut : vide|  
|Adresse|Élément|xs:string|Spécifie l'adresse de l'emplacement de réception.|Requis|Valeur par défaut : vide|  
|PublicAddress|Élément|xs:string|Spécifie l'adresse publique de l'emplacement de réception.|Facultatif|Valeur par défaut : vide|  
|Principal|Élément|xs:boolean|Spécifie si l'emplacement de réception est un emplacement principal.|Requis|Valeur par défaut : Aucun|  
|ReceiveLocationServiceWindowEnabled|Élément|xs:boolean|Indique si la fenêtre de service est active.|Requis|Valeur par défaut : Aucun<br /><br /> Spécifiez **true** si la fenêtre de service est activée ; sinon, spécifiez **false.**|  
|ReceiveLocationFromTime|Élément|xs:dateTime|Spécifie l’heure de début de la fenêtre de service.|Requis|Valeur par défaut : Aucun|  
|ReceiveLocationToTime|Élément|xs:dateTime|Spécifie l'heure de fin de la fenêtre de service.|Requis|Valeur par défaut : Aucun|  
|ReceiveLocationStartDateEnabled|Élément|xs:boolean|Indique si la date de début de la fenêtre de service est activée.|Requis|Valeur par défaut : Aucun|  
|ReceiveLocationStartDate|Élément|xs:dateTime|Spécifie la date de début de la fenêtre de service.|Requis|Valeur par défaut : Aucun|  
|ReceiveLocationEndDateEnabled|Élément|xs:boolean|Indique si la date de fin de la fenêtre de service est activée.|Requis|Valeur par défaut : Aucun|  
|ReceiveLocationEndDate|Élément|xs:dateTime|Spécifie la date de fin de la fenêtre de service.|Requis|Valeur par défaut : Aucun|  
|[ReceiveLocationTransportType](../core/receivelocationtransporttype-receivelocation-node.md)|Record|ProtocolType (ComplexType)|Indique le type de transport de cet emplacement de réception.|Requis|Valeur par défaut : Aucun|  
|ReceiveLocationTransportTypeData|Élément|xs:string|Indique les propriétés du type de transport de cet emplacement de réception.|Facultatif|Valeur par défaut : vide<br /><br /> Consultez [propriétés de Configuration des adaptateurs BizTalk intégrés](../core/configuration-properties-for-integrated-biztalk-adapters.md) pour l’adaptateur spécifique d’informations sur les propriétés qui peuvent être stockées dans cette chaîne.|  
|[ReceivePipeline](../core/receivepipeline-receivelocation-node.md)|Record|PipelineRef (ComplexType)|Spécifie le pipeline de réception pour cet emplacement de réception.|Requis|Valeur par défaut : Aucun|  
|ReceivePipelineData|Élément|xs:string|Spécifie la configuration personnalisée spécifique au pipeline de réception utilisé pour cet emplacement de réception.|Requis|Valeur par défaut : vide|  
|[Pipeline d’envoi](../core/sendpipeline-receivelocation-node.md)|Record|PipelineRef (ComplexType)|Spécifie le pipeline d'envoi pour un emplacement de réception bidirectionnel. **Remarque :** dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] envoyer des pipelines pour les réceptions bidirectionnelles sont spécifiés à l’emplacement de réception plutôt qu’au niveau du port de réception. Sauf spécification contraire dans le fichier de liaisons, un emplacement de réception hérite automatiquement du pipeline d'envoi du port de réception auquel il appartient.|Requis|Valeur par défaut : Aucun|  
|SendPipelineData|Élément|xs:string|Spécifie la configuration personnalisée spécifique au pipeline d'envoi utilisé pour cet emplacement de réception.|Requis|Valeur par défaut : vide|  
|[EncryptionCert](../core/encryptioncert-receivelocation-node.md)|Record|CertificateInfo (ComplexType)|Spécifie le certificat de chiffrement associé à l'emplacement de réception.|Facultatif|Valeur par défaut : Aucun|  
|Activer|Élément|xs:boolean|Spécifie si l'emplacement de réception est activé ou non.|Requis|Valeur par défaut : Aucun|  
|[ReceiveHandler](../core/receivehandler-receivelocation-node.md)|Record|ReceiveHandlerRef (ComplexType)|Spécifie le gestionnaire de réception à utiliser pour cet emplacement de réception.|Facultatif|Valeur par défaut : Aucun|