---
title: "Composant de Pipeline décodeur MIME-SMIME | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipeline components, MIME/SMIME Decoder
- MIME/SMIME Decoder [pipeline component]
ms.assetid: ff6c963c-1b5c-4be4-9eef-3ec9a018e7fd
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d85fe099cb876156410ba86c5f204a154dfbac36
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="mime-smime-decoder-pipeline-component"></a>Composant de Pipeline décodeur MIME-SMIME
Le composant Décodeur MIME/SMIME offre des fonctions de décodage MIME pour les messages. Ce composant de pipeline intervient dans la phase de décodage d'un pipeline de réception. Il prend en charge les décodages 7 bits, 8 bits, binaires, Quoted Printable, UUEncode et Base64. Les modifications des jeux de caractères des données localisées n'affectent pas le décodage.  
  
 Le composant Décodeur MIME/SMIME peut déchiffrer et valider la signature d'un message entrant. Les certificats de déchiffrement proviennent du magasin de certificats personnel de l'utilisateur sous la session duquel le service est exécuté. Les certificats de validation de signature proviennent, quant à eux, du carnet d'adresses de l'ordinateur local ou du message lui-même.  
  
 Une fois le déchiffrement correctement effectué, le Décodeur MIME/SMIME associe l'empreinte du certificat de déchiffrement en tant que prédicat du message. De ce fait, tout service (orchestration ou port d'envoi) s'abonnant à ce message doit être associé à un hôte qui possède cette clé. Les associations entre hôtes et clés peuvent être définies dans la console Administration de BizTalk sous la forme d'une propriété de l'hôte. Pour plus d’informations sur la configuration de l’ordinateur hôte dans la console Administration de BizTalk, consultez [comment modifier les propriétés de l’hôte](../core/how-to-modify-host-properties.md).  
  
 Le Décodeur MIME/SMIME est le seul composant de pipeline de réception prêt à l'emploi capable de gérer des messages à parties multiples, notamment des messages MIME/SMIME. Le composant de pipeline analyse le message et crée un message BizTalk à parties multiples équivalent. Ce message BizTalk comporte une seule partie nommée corps du message. Tous les autres composants de pipeline, notamment le Désassembleur XML, traitent uniquement la partie « corps » du message BizTalk. Le MessageType correspondant au corps du message BizTalk est utilisé pour acheminer le message aux abonnés.  
  
 Les conditions ci-dessous sont évaluées par le Décodeur MIME/SMIME afin d'identifier le corps de message BizTalk correspondant à un message MIME à parties multiples. Les conditions sont évaluées dans l'ordre suivant :  
  
1.  Première partie MIME/SMIME comportant un en-tête Description-Contenu paramétré sur « corps » (sans distinction de casse)  
  
2.  Première partie MIME/SMIME comportant un en-tête Type-Contenu paramétré sur « texte/xml » (sans distinction de casse)  
  
3.  Première partie MIME/SMIME comportant un en-tête Type-Contenu paramétré sur « texte/ » (sans distinction de casse)  
  
4.  Première partie MIME/SMIME  
  
> [!NOTE]
>  L'ordre des parties du message BizTalk obtenu est identique à celui des parties MIME/SMIME du message MIME/SMIME.  
  
> [!NOTE]
>  Si le message BizTalk à plusieurs parties fait l'objet d'un abonnement ou d'une utilisation par une orchestration, le nombre de parties dans le message doit correspondre au nombre de parties du message qui active l'orchestration.  
  
 Pour plus d’informations sur la configuration du composant de pipeline Décodeur MIME/SMIME, consultez [comment configurer le composant de Pipeline décodeur MIME-SMIME](../core/how-to-configure-the-mime-smime-decoder-pipeline-component.md). Pour plus d’informations sur la prise en charge de BizTalk Server pour le déchiffrement, la validation de l’authentification et d’utilisation des certificats, consultez [sécurité pour l’envoi et réception de Messages](../core/security-for-sending-and-receiving-messages.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Composants de pipeline](../core/pipeline-components.md)   
 [Propriétés et schéma de propriété MIME-SMIME](../core/mime-smime-property-schema-and-properties.md)   
 [MIME (exemple BizTalk Server)](../core/mime-biztalk-server-sample.md)