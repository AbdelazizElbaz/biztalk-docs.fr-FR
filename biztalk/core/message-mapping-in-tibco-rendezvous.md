---
title: Message de mappage dans TIBCO Rendezvous | Documents Microsoft
description: "Champs de message et mappage des messages au format XML dans l’adaptateur BizTalk pour TIBCO Rendezvous"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 62793bec-f076-425c-b25e-c4be5bd93cc8
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fb80ea4f908aa50dc32755c333aa3ccf2ea4db91
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="message-mapping-in-tibco-rendezvous"></a>Mappage des messages dans TIBCO Rendezvous
Les messages TIBCO Rendezvous sont constitués d'informations d'en-tête et d'un ensemble de champs de message. Les informations d'en-tête sont directement mappées aux propriétés de contexte du message.  
  
## <a name="message-field-elements"></a>Éléments des champs de message  
 Un champ de message est constitué des éléments suivants :  
  
|Élément| Description|  
|-------------|-----------------|  
|**Nom**|Chaîne de caractères. Ne doit pas être nécessairement unique dans un message.|  
|**Identificateur**|Entier court. Unique dans un message. Limite de manière implicite le nombre de champs de message à 65535. L’étendue de l’identificateur est le message (ou sub). Le même identificateur peut être utilisé dans deux sous-messages, qui font eux-mêmes partie d'un message conteneur.|  
|**Valeur**|Données du champ de message.|  
|**Count**|Nombre d'éléments (dans le cas d'un tableau)|  
|**Type**|Type du champ de message.|  
  
### <a name="mapping-process"></a>Processus de mappage  
 Les messages structurés TIBCO Rendezvous sont mappés aux éléments XML comme suit :  
  
-   **Nom** est utilisé comme nom de l’élément. Le nom de champ TIBCO Rendezvous peut contenir des caractères dont l'utilisation n'est pas valide dans les noms d'élément XML. L'adaptateur génère des mappages de caractères valides entre les messages structurés XML et TIBCO Rendezvous.  
  
-   **Identificateur** est placé dans un attribut 'id'.  
  
-   **Valeur** contient une représentation de chaîne qui est le corps de l’élément.  
  
-   **Nombre de** est ignoré.  
  
-   **Type** informations sont placées dans un attribut xsi : type pour l’élément généré.  
  
     Pour plus d’informations, consultez [mappage de Type de données pour les gestionnaires de réception dans TIBCO Rendezvous](../core/data-type-mapping-for-receive-handlers-in-tibco-rendezvous.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Concepts de TIBCO Rendezvous](../core/tibco-rendezvous-concepts.md)   
 [Création de gestionnaires de réception TIBCO Rendezvous](../core/creating-tibco-rendezvous-receive-handlers.md)