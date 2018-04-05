---
title: PrimaryTransport (nœud SendPort) | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- PrimaryTransport node [binding file]
ms.assetid: 22b68d27-f280-4272-84b8-8a50f230228a
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6b2d60f3b7fbb09e2e106a4d91f1eca0385aa155
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="primarytransport-sendport-node"></a>PrimaryTransport (nœud SendPort )
Le nœud PrimaryTransport du nœud SendPort d'un fichier de liaison fournit des informations spécifiques sur le transport principal lié à un port d'envoi exporté avec le fichier de liaison.  
  
## <a name="nodes-in-the-primarytransport-node"></a>Nœuds du nœud PrimaryTransport  
 Le tableau suivant répertorie les propriétés que vous pouvez définir pour ce nœud d'un fichier de liaison :  
  
|**Nom**|**Type de nœud**|**Type de données**|**Description**|**Restrictions**|**Commentaires**|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|Adresse|Élément|xs:string|Spécifie l'adresse (ou URI) du transport.|Facultatif|Valeur par défaut : vide|  
|[TransportType (nœud PrimaryTransport)](../core/transporttype-primarytransport-node.md)|Record|ProtocolType (ComplexType)|Spécifie le type de transport, qui correspond également au nom de l'adaptateur utilisé pour ce transport.|Facultatif|Valeur par défaut : Aucun|  
|TransportTypeData|Élément|xs:string|Spécifie les informations de configuration propres à l'adaptateur.|Facultatif|Valeur par défaut : vide<br /><br /> Consultez [propriétés de Configuration des adaptateurs BizTalk intégrés](../core/configuration-properties-for-integrated-biztalk-adapters.md) pour l’adaptateur spécifique d’informations sur les propriétés qui peuvent être stockées dans cette chaîne.|  
|RetryCount|Élément|xs:int|Spécifie le nombre de tentatives propre à l'adaptateur utilisé pour le transport.|Requis|Valeur par défaut : Aucun|  
|RetryInterval|Élément|xs:int|Spécifie l'intervalle avant nouvelle tentative propre à l'adaptateur utilisé pour le transport.|Requis|Valeur par défaut : Aucun|  
|ServiceWindowEnabled|Élément|xs:boolean|Spécifie si la fenêtre de service est activée pour l'adaptateur utilisé pour le transport.|Requis|Valeur par défaut : Aucun<br /><br /> La valeur **true** si la fenêtre de service est activée, sinon la valeur **false**.|  
|FromTime|Élément|xs:dateTime|Spécifie l'heure de début de la fenêtre de service.|Requis|Valeur par défaut : Aucun|  
|ToTime|Élément|xs:dateTime|Spécifie l’heure de fin de la fenêtre de service.|Requis|Valeur par défaut : Aucun|  
|Principal|Élément|xs:boolean|Spécifie si l'adaptateur utilisé pour le transport est de type principal.|Requis|Valeur par défaut : Aucun<br /><br /> La valeur **true** si l’adaptateur utilisé pour le transport est principal, sinon la valeur **false**.|  
|OrderedDelivery|Élément|xs:boolean|Spécifie si l'adaptateur utilisé pour le transport doit envoyer des messages de manière ordonnée.|Requis|Valeur par défaut : Aucun<br /><br /> La valeur **true** si le transport doit envoyer des messages dans l’ordre, sinon la valeur **false**.|  
|DeliveryNotification|Élément|xs:int|Spécifie si l'adaptateur utilisé pour le transport doit renvoyer un accusé de réception indiquant que la transmission a réussi.|Requis|Valeur par défaut : Aucun<br /><br /> La valeur **true** pour les notifications de remise, sinon la valeur **false**.|  
|[Gestionnaire d’envoi](../core/sendhandler-primarytransport-node.md)|Record|SendHandlerRef (ComplexType)|Spécifie le Gestionnaire d’envoi de l’adaptateur utilisé pour le transport.|Requis|Valeur par défaut : Aucun|