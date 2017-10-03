---
title: "Fractionnement d’un échange EDI par lot | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 29c79b06-cc88-4cc8-aa99-40f24a1bdcde
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 441eafe79de57963dc1df5ac19334542f41a23d1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="splitting-a-batched-edi-interchange"></a>Fractionnement d'un échange EDI traité par lot
> [!NOTE]
>  Toutes les options d’interface utilisateur mentionnées dans cette rubrique sont disponibles dans le **paramètres d’hôte Local** page (**paramètres du récepteur** section) des onglets d’accord unidirectionnel de la **accord Propriétés** boîte de dialogue.  
  
 EDI pipeline de réception fractionne un lot d’échange EDI entrant si vous avez défini le **entrants option de traitement par lots** propriété d’accord pour **fractionner l’échange en documents informatisés**.  
  
 Lorsque le pipeline de réception EDI fractionne un échange EDI entrant par lot, il crée un fichier XML pour chaque document informatisé/message EDI. Le pipeline promeut l'ensemble des en-têtes d'échange et de groupe dans le contexte de chaque document informatisé fractionné de l'échange. Il promeut également certains en-têtes d'échange et de groupe spécifiques, tels que ISA6, GS1 et GS2, afin que ces champs puissent être utilisés pour le routage. Vous pouvez masquer les informations de sécurité dans l’en-tête en sélectionnant le **masquer les informations de sécurité / d’autorisation/mot de passe** propriété.  
  
 Lorsque [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] tente de fractionner un échange en documents informatisés, les erreurs dans certains champs d'en-têtes ISA (ISA1 à ISA13) ou UNB font que l'échange est rejeté. C'est également le cas lorsque le numéro de contrôle de l'échange est en double, si le numéro de contrôle d'échange en double est activé dans les propriétés de l'accord ou de l'accord de secours. Un erreur dans d'autres champs d'en-tête d'échange (autres que ISA1 à ISA13 pour l'échange X12) ou dans les champs d'en-tête de groupe ne provoque pas l'échec de l'échange.  
  
 Si **fractionner l’échange en documents informatisés - suspendre les documents informatisés en cas d’erreur** est sélectionné dans les propriétés de l’accord, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] interrompt le document informatisé si une erreur se produit. Si **scinder l’échange en documents informatisés : suspendre l’échange en cas d’erreur** est sélectionnée, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] interrompt l’échange.  
  
 Chaque élément de lot XML est acheminé vers MessageBox et traité par les ports d'envoi ou les orchestrations abonnés à un élément de lot. Le classement des documents informatisés dans l'échange risque de ne pas être conservé lorsqu'ils sont traités comme des messages fractionnés. Au niveau de la réception, les messages sont traités dans l'ordre dans lequel ils figurent dans l'échange et ils sont placés dans MessageBox dans cet ordre. Pour conserver cet ordre côté envoi, vous devez utiliser des convois ou des ports d'envoi de livraison chronologique.  
  
 Si les éléments fractionnés d'un lot sont inclus dans un lot sortant, le composant de pipeline BatchMarker promeut les propriétés nécessaires. Pour plus d’informations, consultez [le traitement par lot les Messages EDI sortants](../core/batching-outgoing-edi-messages.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Traitement des lots entrants](../core/processing-incoming-batches.md)   
 [Le traitement par lot des Messages EDI sortants](../core/batching-outgoing-edi-messages.md)