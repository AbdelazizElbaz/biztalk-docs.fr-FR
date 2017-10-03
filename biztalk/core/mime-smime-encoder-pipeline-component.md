---
title: Composant de Pipeline encodeur MIME-SMIME | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipeline components, MIME/SMIME Encoder
- MIME/SMIME Encoder [pipeline component]
- BTS.EncryptionCert property
ms.assetid: 397505e6-47d0-4b63-9197-814ee4388369
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d6c6a79052d3294420c46bff2a1ce3c0ed869e48
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="mime-smime-encoder-pipeline-component"></a>Composant de Pipeline encodeur MIME-SMIME
Le composant de pipeline Encodeur MIME/SMIME peut être placé dans la phase de codage d'un pipeline d'envoi. Il prend en charge les codages 7 bits, 8 bits, binaire, quoted-printable, base64 et UUencode. Les modifications des jeux de caractères de données localisées n'affectent pas le codage.  
  
 Ce composant peut être utilisé pour coder en MIME, pour signer ou chiffrer un message sortant avec des certificats de chiffrement et de signature.  
  
 S’il existe un composant de codage dans le pipeline d'envoi configuré pour signer des messages et que le groupe BizTalk comprenant l’hôte exécutant le pipeline n’est pas configuré avec un certificat de signature, le message sortant sera interrompu (avec l’erreur correspondante) et placé dans la file d’attente des messages interrompus de l'hôte exécutant le pipeline. Si le certificat de signature ne peut pas être trouvé dans le magasin de certificats personnels de l'utilisateur sous lequel le service s'exécute, le message sera interrompu et placé dans la file d'attente des messages interrompus de l'hôte exécutant le pipeline.  
  
 S’il existe un composant de codage dans le pipeline de sortie configuré pour chiffrer les messages sortants, et que le certificat est introuvable dans le magasin de certificats, le message sera interrompu et placé dans la file d’attente des messages interrompus de l’hôte exécutant le pipeline.  
  
 Pour chiffrer une réponse sur un port de requête-réponse recevant des messages signés et chiffrés, un composant de pipeline personnalisé doit être ajouté au pipeline avant le composant de pipeline Encodeur MIME/SMIME. Ce composant de pipeline personnalisé doit identifier l’empreinte correspondant au certificat de chiffrement et affectez-lui le **BTS. EncryptionCert** propriété dans le contexte du message. Pour plus d’informations sur les propriétés de contexte de message, consultez [comment modifier les propriétés de groupe](../core/how-to-modify-group-properties.md).  
  
 Pour plus d’informations sur la configuration du composant de pipeline Encodeur MIME/SMIME, consultez [comment configurer le composant de Pipeline encodeur MIME-SMIME](../core/how-to-configure-the-mime-smime-encoder-pipeline-component.md). Pour plus d’informations sur la prise en charge de BizTalk Server pour le chiffrement, la signature et l’utilisation de certificats, consultez [sécurité pour l’envoi et réception de Messages](../core/security-for-sending-and-receiving-messages.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Composants de pipeline](../core/pipeline-components.md)   
 [Propriétés et schéma de propriété MIME-SMIME](../core/mime-smime-property-schema-and-properties.md)   
 [MIME (exemple BizTalk Server)](../core/mime-biztalk-server-sample.md)