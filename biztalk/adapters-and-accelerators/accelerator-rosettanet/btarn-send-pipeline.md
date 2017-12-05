---
title: "Pipeline d’envoi BTARN | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XML Assembler
- send pipelines, message flow
- DOCTYPE headers
- MIME/SMIME Encoder
- send pipelines, BTARN
- BTARN, send pipelines
- XML Preprocessor
- messages, message flow
ms.assetid: 88562132-0ea4-4b5a-9445-b69f6c84e5ea
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f566b37cc43f8aca2f0a36143d10d809c008d5cd
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="btarn-send-pipeline"></a>Pipeline d’envoi BTARN
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] prépare un message Framework RNIF (RosettaNet Implementation) pour la transmission du pipeline RNIFSend (RNIFSend.btp). Le pipeline d’envoi inclut les éléments suivants :  
  
-   XML de préprocesseur  
  
-   Assembleur XML  
  
-   Encodeur de Multipurpose Internet Mail Extensions/Secure Multipurpose Internet Mail Extensions (MIME/SMIME)  
  
## <a name="xml-preprocessor"></a>Préprocesseur XML  
 Le préprocesseur XML ajoute un en-tête de type de document au message. L’en-tête identifie le schéma DTD (définition) de type de document associé au message. La spécification RNIF nécessite la présence d’un en-tête de type de document pour la transmission de RNIF.  
  
## <a name="xml-assembler"></a>Assembleur XML  
 L’assembleur XML est basé sur l’assembleur XML de BizTalk Server. Il transfère les propriétés à partir du contexte de message dans les documents et les enveloppes. Il assemble le message à partir de ses parties XML et les pièces jointes. Il n’effectue pas de validation de message.  
  
 Pour plus d’informations sur natif [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] assembleur XML, consultez « Composant de Pipeline assembleur XML » dans l’aide de BizTalk Server.  
  
## <a name="mimesmime-encoder"></a>Encodeur MIME/SMIME  
 L’encodeur MIME/SMIME est basée sur l’encodeur MIME/SMIME du serveur BizTalk. Selon les paramètres de protocole dans l’accord de partenariat commercial et les paramètres de l’encodeur MIME/SMIME du serveur BizTalk, le [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] encodeur exécute les actions suivantes :  
  
-   Ajoute un en-tête binaire de 8 octets pour le message, tel que requis pour les messages RNIF 1.1.  
  
-   Encode les parties de message et calcule le condensat.  
  
-   Chiffre la charge utile (contenu du service et les pièces jointes), ou le conteneur de charge utile (contenu du service plus en-tête service ainsi que les pièces jointes). Si vous avez défini le **Encoder tous les ports** définition sur le **protocole** onglet de l’accord de partenariat commercial à `False`, l’encodeur chiffre uniquement la charge utile. Si vous avez défini le **Encoder tous les ports** à `True`, l’encodeur chiffrera le conteneur de charge utile.  
  
 Pour plus d’informations sur natif [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] encodeur MIME/SMIME, voir « Composant de Pipeline encodeur MIME/SMIME » dans l’aide de BizTalk Server.  
  
## <a name="message-flow"></a>Flux de messages  
 Le flux de messages via le [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] envoyer le pipeline est comme suit :  
  
1.  Si vous avez défini le **encoder toutes les parties** définition de l’accord de partenariat commercial à `True`, l’encodeur MIME/SMIME codera toutes les parties de message. Il utilise la méthode de codage définie dans le `Encoding` propriété de l’accord.  
  
2.  Pour RNIF 2.01, si le message est un message d’action et il existe une pièce jointe, l’encodeur procède comme suit pour chaque pièce jointe :  
  
    1.  Si la pièce jointe est binaire, l’encodeur Encoder.  
  
    2.  L’encodeur génère un ID de contenu de la pièce jointe.  
  
    3.  L’encodeur créera une partie MIME de la pièce jointe.  
  
3.  Pour RNIF 2.01, le pipeline chiffre des parties de message et générer le message RNIF selon le paramètre de **est persistant requis de la confidentialité** (tel que défini dans les paramètres de configuration de processus) :  
  
    1.  Si vous avez défini **est persistant requis de la confidentialité** à **charge utile**, l’encodeur chiffre le contenu du service et les pièces jointes. L’assembleur ajoute ensuite l’en-tête de service, l’en-tête de remise et préambule pour construire le message RNIF final.  
  
    2.  Si vous avez défini **est persistant requis de la confidentialité** à **conteneur de charge utile**, l’encodeur chiffrera l’en-tête de service, le contenu de service et les pièces jointes. L’assembleur ajoute ensuite l’en-tête de remise et le préambule pour construire le message RNIF final.  
  
    3.  Si vous avez défini **est persistant requis de la confidentialité** à **aucun**, l’assembleur pour le contenu de service et les pièces jointes (sans ajouterez l’en-tête de service, l’en-tête de remise et préambule chiffrement) pour construire le message RNIF final.  
  
4.  Pour RNIF 1.1, l’assembleur construira du dernier message RNIF sans chiffrement.  
  
5.  L’encodeur signe le message dans le cas suivant :  
  
    1.  Le message est un message de signal et le **requis Non répudiation** propriété (dans les paramètres de configuration de processus) est `True`.  
  
    2.  Le message est un message d’action et le **non-répudiation de l’origine et du contenu** propriété (dans les paramètres de configuration de processus) est `True`.  
  
6.  Pour RNIF 2.01, l’encodeur de calculer le digest sur la première partie du corps du message MIME et conserver le résumé. Elle calcule le digest à l’aide de la méthode définie dans le `Digest` propriété de méthode dans l’accord de partenariat commercial (SHA-1 ou MD5).  
  
## <a name="see-also"></a>Voir aussi  
 [Traitement de messages dans BTARN](../../adapters-and-accelerators/accelerator-rosettanet/message-processing-in-btarn.md)