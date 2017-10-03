---
title: "Certificats utilisés par BizTalk Server pour des Messages chiffrés | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, message flow [encrypted messages]
- encrypted messages
- messages, encryption
ms.assetid: 44b06488-4ecd-436d-af3d-b95e285ecb3e
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4eb1e9629b56fa667d68c246645d00416de221a7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="certificates-that-biztalk-server-uses-for-encrypted-messages"></a>Certificats utilisés par BizTalk Server pour les messages chiffrés
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] prend en charge le chiffrement à clé publique des messages sortants et le déchiffrement des messages entrants basé sur S/MIME. BizTalk Server utilise S/MIME version 3 pour le chiffrement des messages sortants et S/MIME versions 2 et 3 pour le déchiffrement des messages entrants.  
  
-   BizTalk Server prend en charge les certificats de chiffrement RSA et Diffie Hellman.  
  
-   BizTalk Server prend en charge les algorithmes de chiffrement Data Encryption Standard (DES), 3DES et RC2.  
  
 La figure suivante illustre le flux de message lorsque BizTalk Server reçoit un message chiffré.  
  
 ![Flux de messages lors de la réception d’un message chiffré](../core/media/bpi-sp-msgsec-inboundencryption.gif "BPI_SP_MSGSEC_InboundEncryption")  
  
 Le flux de message lorsque BizTalk Server reçoit un message chiffré est le suivant :  
  
1.  Un partenaire envoie un message à BizTalk Server. Le partenaire chiffre le message avec la clé publique de BizTalk Server.  
  
2.  Le gestionnaire de réception BizTalk Server approprié reçoit le message.  
  
3.  Durant l'exécution du pipeline de réception, le composant de pipeline Décodeur MIME/SMIME déchiffre le message à l'aide de la clé privée de BizTalk Server.  
  
    > [!NOTE]
    >  Pour le déchiffrement de pipeline réussisse sur un ordinateur IIS 7.0, vérifiez que le compte pour le pool d’applications IIS et le compte utilisé par l’instance d’hôte associé au Gestionnaire de réception sont identiques et que ce compte est un membre de la \<machineName > \IIS_WPG groupe. Pour plus d’informations sur la configuration IIS traiter identité pour IIS 7.0, consultez [des recommandations pour la résolution des problèmes d’autorisation IIS](../core/guidelines-for-resolving-iis-permissions-problems.md). Ces processus doivent s'exécuter sous le même compte afin de garantir que le profil de compte est chargé, et qu'à son tour, il charge les clés de registre requises pour effectuer le déchiffrement dans le pipeline. Pour des raisons de performances, IIS 7.0 ne charge pas le profil de compte lors du démarrage du processus w3wp.exe associé. L'instance de l'hôte BizTalk doit donc être configurée avec le même compte, de façon à ce que BizTalk charge le profil de compte et les clés de Registre.  
  
4.  Un traitement supplémentaire se produit.  
  
 La figure suivante illustre le flux de message lorsque BizTalk Server envoie un message chiffré.  
  
 ![Flux de messages lors de l’envoi d’un message chiffré](../core/media/bpi-sp-msgsec-outboundencryption.gif "BPI_SP_MSGSEC_OutboundEncryption")  
  
 Le flux de message lorsque BizTalk Server envoie un message chiffré à un partenaire est le suivant :  
  
1.  Le gestionnaire d'envoi BizTalk Server approprié envoie un message au partenaire.  
  
2.  Durant l'exécution du pipeline d'envoi, le composant de pipeline Encodeur MIME/SMIME chiffre le message à l'aide de la clé publique du partenaire.  
  
3.  Le partenaire reçoit le message de BizTalk Server. Le partenaire utilise sa clé privée pour déchiffrer le message.  
  
## <a name="see-also"></a>Voir aussi  
 [Certificats utilisés par BizTalk Server pour les Messages signés](../core/certificates-that-biztalk-server-uses-for-signed-messages.md)   
 [Magasins de certificats par BizTalk Server](../core/certificate-stores-that-biztalk-server-uses.md)   
 [Chiffrement et les certificats de signature](../core/encryption-and-signing-certificates.md)   
 [Envoyer et recevoir des Messages chiffrés](../core/sending-and-receiving-encrypted-messages.md)