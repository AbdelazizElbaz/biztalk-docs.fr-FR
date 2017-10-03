---
title: Chiffrement et les certificats de signature | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- certificates, security
- security, certificates
- security, messages
- certificates, encryption
- encryption certificates, messages
- messages, encryption
- messages, certificates
- security, encryption
ms.assetid: 3c3f9de5-4156-4133-8d5e-c30b142b6d61
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 633484a6c5599b9323bfd7798f621b27a501ce6b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="encryption-and-signing-certificates"></a>Chiffrement et les certificats de signature
Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] s'appuie en grande partie sur la sécurité fournie par les certificats. En utilisant les certificats pour le chiffrement et les signatures numériques, BizTalk Server peut envoyer et recevoir des données fiables et garantir que les données qu'il traite sont sécurisées. Pour le chiffrement et les signatures numériques, un certificat de clé publique et un certificat de clé privée sont disponibles. Pour le chiffrement, l'expéditeur du message utilise le certificat de clé publique du récepteur pour chiffrer le message, tandis que le récepteur du message (BizTalk Server) utilise sa clé privée pour déchiffrer le message. Pour les signatures numériques, l'expéditeur du message utilise un certificat de clé privée pour signer le message, et le récepteur du message (BizTalk Server) utilise le certificat de clé publique de l'expéditeur pour vérifier la signature.  
  
 BizTalk Server utilise les certificats de clé publique pour vérifier les signatures numériques des messages entrants et chiffrer les messages sortants. BizTalk Server utilise les certificats de clé privée pour déchiffrer les messages entrants et signer les messages sortants.  
  
 Les certificats utilisés par BizTalk Server sont configurés dans l'Explorateur BizTalk et la console Administration de BizTalk.  
  
 Pour plus d’informations sur les certificats numériques, consultez le site Web Microsoft TechNet à l’adresse [http://go.microsoft.com/fwlink/?LinkId=60508](http://go.microsoft.com/fwlink/?LinkId=60508).  
  
> [!NOTE]
>  Dans le cadre du traitement des messages S/MIME (Secure Multipurpose Internet Mail Extensions), vous pouvez choisir de faire vérifier la liste de révocation des certificats par le moteur BizTalk Server pour vous assurer qu'un certificat n'a pas expiré et qu'il est approuvé par une autorité de certification racine. Cette vérification est effectuée pendant le traitement du message par le pipeline, dans le composant Décodeur MIME/SMIME. Pour plus d’informations sur la définition **vérifier la liste de révocation** propriété, consultez [comment configurer le composant de Pipeline décodeur MIME-SMIME](../core/how-to-configure-the-mime-smime-decoder-pipeline-component.md).  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Magasins de certificats par BizTalk Server](../core/certificate-stores-that-biztalk-server-uses.md)  
  
-   [Certificats utilisés par BizTalk Server pour les Messages signés](../core/certificates-that-biztalk-server-uses-for-signed-messages.md)  
  
-   [Certificats utilisés par BizTalk Server pour les Messages chiffrés](../core/certificates-that-biztalk-server-uses-for-encrypted-messages.md)