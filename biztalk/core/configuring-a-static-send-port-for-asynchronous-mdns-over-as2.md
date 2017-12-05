---
title: "Configuration d’un Port d’envoi statique pour les MDN asynchrones via AS2 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cc43e767-d9d7-4b02-b3fc-0cfdfd6e61c4
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3e023dc6f2165e9427fa57e109715dda6cdb258f
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="configuring-a-static-send-port-for-asynchronous-mdns-over-as2"></a>Configuration d'un port d'envoi statique pour les MDN asynchrones via AS2
Cette rubrique décrit la configuration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] de manière à envoyer un message EDIINT/AS2 de façon asynchrone via un port d'envoi statique. Cette configuration inclut la création du port d'envoi statique et, le cas échéant, la configuration du certificat de chiffrement utilisé par le port d'envoi.  
  
> [!NOTE]
>  À la place d'un port d'envoi statique, vous pouvez paramétrer un port d'envoi dynamique pour envoyer des messages MDN. Pour plus d’informations, consultez [configuration d’un Port d’envoi dynamique pour les MDN asynchrones via AS2](../core/configuring-a-dynamic-send-port-for-asynchronous-mdns-over-as2.md).  
  
 Pour envoyer un message MDN, créez un port d'envoi HTTP unidirectionnel doté de la configuration suivante :  
  
|Emplacement|Propriété|Paramètre|  
|--------------|--------------|-------------|  
|**Propriétés du Port d’envoi : général**|Type de port|Port d’envoi unidirectionnel statique|  
|**Propriétés du Port d’envoi : général**|Type de transport|HTTP **Remarque :** uniquement l’adaptateur HTTP peut être utilisé pour transporter les messages codés EDIINT/AS2. Ce transport ne fonctionne pas avec les autres types d'adaptateurs.|  
|**Propriétés du Port d’envoi : général**|Gestionnaire d'envoi|BizTalkServerApplication|  
|**Propriétés du Port d’envoi : général**|Pipeline d’envoi|AS2Send|  
|**Propriétés du Transport HTTP**|URL de destination|\<Chaîne d’URL de destination\>|  
|**Propriétés du Transport HTTP**|Activer le codage mémorisé en bloc|Désactivé|  
|**Propriétés du Port d’envoi : filtres**|Propriété|EdiIntAS.IsAS2AsynchronousMdn **Remarque :** vous devez également spécifier des expressions de filtre supplémentaires pour vous assurer que seuls les messages MDN destinés à l’adresse spécifiée dans ce port d’envoi sont récupérées par ce filtre d’abonnement.|  
|**Propriétés du Port d’envoi : filtres**|Opérateur|==|  
|**Propriétés du Port d’envoi : filtres**|Valeur|True|  
|**Propriétés du Port d’envoi : les certificats**|Nom commun et empreinte|Entrez le nom et l'empreinte du certificat si vous utilisez un certificat de chiffrement pour un message MDN sortant.|  
  
 Un MDN asynchrone doit être envoyé à l’adresse spécifiée dans le **Receipt-Delivery-Option** en-tête du message AS2 reçu. Un port d’envoi dynamique se charge automatiquement, tandis qu’un port d’envoi statique envoie le message à la **URL de Destination** dans les propriétés de port d’envoi. Lors de l'envoi d'un MDN asynchrone à l'aide d'un port d'envoi statique, vérifiez que l'URL de destination est correcte.  
  
## <a name="functionality"></a>Fonctionnalité  
 Le port d'envoi et le pipeline doivent effectuer les opérations suivantes pour envoyer un MDN :  
  
-   récupération du MDN via l'application d'un filtre sur la propriété `EdiIntAS.IsAS2AsynchronousMdn==True` ;  
  
-   création d'un message AS2. Pour plus d’informations sur ce processus, consultez [génération d’un Message AS2 sortant](../core/generating-an-outgoing-as2-message.md).  
  
-   acheminement du MDN vers l'adresse définie dans le port d'envoi.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration des ports pour une solution AS2](../core/configuring-ports-for-an-as2-solution.md)