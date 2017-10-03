---
title: "Certificats utilisés par BizTalk Server pour les Messages signés | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, signed messages
- messages, message flow [digital signatures]
- S/MIME messages
- signed messages
- digital signatures, message flow
- messages, certificates
ms.assetid: 0b521e11-73ef-424f-9e6a-4fb42dc263ff
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cce82b634fffac4af0f75cdff26c7f512a132de9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="certificates-that-biztalk-server-uses-for-signed-messages"></a>Certificats utilisés par BizTalk Server pour les messages signés
BizTalk Server prend en charge la signature des messages sortants et la vérification de signature des messages S/MIME (Secure Multipurpose Internet Mail Extensions) entrants. BizTalk Server utilise S/MIME versions 2 et 3 pour signer les messages sortants et valider la signature des messages entrants. De même, vous pouvez configurer BizTalk Server pour signer puis chiffrer les messages qu'il envoie aux partenaires.  
  
-   BizTalk Server prend en charge les algorithmes de signature SHA-1 et MD5 pour la vérification des signatures numériques. BizTalk Server utilise l'algorithme de signature SHA-1 pour signer les messages sortants.  
  
-   Les systèmes d'échange de clés pris en charge par BizTalk Server pour les clés de signature sont les algorithmes RSA (Rivest-Shamir-Adleman) et la norme DSS (Digital Signature Standard). BizTalk Server ne prend pas en charge le système d'échange AES (Advanced Encryption Standard) pour les clés de signature.  
  
-   Le certificat de signature pris en charge par BizTalk Server est x.509 version 3.  
  
 La figure suivante illustre le flux de messages lorsque BizTalk Server reçoit un message signé numériquement et utilise la signature (facultatif) pour résoudre l'identité du partenaire vers un tiers dans l'environnement BizTalk Server.  
  
 ![Flux de messages lors de l’envoi d’un message signé](../core/media/6fd1674d-5a21-4272-83ca-608d7b400de7.gif "6fd1674d-5a21-4272-83ca-608d7b400de7")  
  
 Lorsque BizTalk Server reçoit un message signé numériquement, le flux de messages est le suivant :  
  
1.  Un partenaire envoie un message à BizTalk Server. Il signe le message avec son certificat de clé privée.  
  
2.  Le gestionnaire de réception BizTalk Server approprié reçoit le message.  
  
3.  Durant l'exécution du pipeline de réception, le composant de pipeline Décodeur MIME/SMIME vérifie la signature numérique à l'aide de la clé publique du partenaire.  
  
4.  Si le composant Résolution du tiers est configuré, le certificat de clé publique du partenaire est utilisé pour identifier le tiers dans le système BizTalk Server durant l'exécution du composant de pipeline de réception Résolution du tiers.  
  
5.  Un traitement supplémentaire se produit.  
  
 La figure suivante illustre le flux de messages lorsque BizTalk Server envoie un message signé numériquement.  
  
 ![](../core/media/bts-bpi-sp-msgsec-outboundsigning-r2c.gif "bts_BPI_SP_MSGSEC_OutboundSigning_R2c")  
  
 Lorsque BizTalk Server envoie un message signé numériquement à un partenaire, le flux de messages est le suivant :  
  
1.  Le gestionnaire d'envoi BizTalk Server approprié envoie un message au partenaire.  
  
2.  Durant l'exécution du pipeline d'envoi, le composant de pipeline Encodeur MIME/SMIME signe le message à l'aide de la clé privée de BizTalk Server.  
  
3.  Le partenaire reçoit le message de BizTalk Server. Il utilise la clé publique de BizTalk Server pour vérifier la signature numérique.  
  
 BizTalk Server contrôle la validité des certificats associés aux messages signés entrants en validant la chaîne d'approbation de l'autorité de certification associée et en s'assurant que le certificat n'est pas arrivé à expiration. Pour valider la chaîne d'approbation de l'autorité de certification, il parcourt la chaîne d'approbation des certificats jusqu'à ce qu'il atteigne une autorité de certification racine. Il s'assure ainsi que le certificat employé pour signer un message provient effectivement du tiers identifié. Cette validation est effectuée lors de l'exécution de chaque message signé.  
  
 BizTalk Server peut en outre vérifier que l'autorité de certification n'a pas révoqué le certificat utilisé pour signer ou chiffrer le message ; pour cela, vous devez télécharger la liste de révocation des certificats de l'autorité de certification et l'installer avec l'Explorateur Windows. Pour plus d’informations sur la façon de valider un certificat, consultez [comment configurer le composant de Pipeline décodeur MIME-SMIME](../core/how-to-configure-the-mime-smime-decoder-pipeline-component.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Certificats utilisés par BizTalk Server pour les Messages chiffrés](../core/certificates-that-biztalk-server-uses-for-encrypted-messages.md)   
 [Magasins de certificats par BizTalk Server](../core/certificate-stores-that-biztalk-server-uses.md)   
 [Chiffrement et les certificats de signature](../core/encryption-and-signing-certificates.md)   
 [Envoyer et recevoir des Messages signés](../core/sending-and-receiving-signed-messages.md)