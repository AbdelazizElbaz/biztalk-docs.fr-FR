---
title: Configuration de la signature, la Compression et le chiffrement dans le Transport AS2 | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bc3537a7-c065-4a33-a375-29e7902b5ffa
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 88309f17e335708b6e73109972c6c02d75ee483c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-signing-compression-and-encryption-in-as2-transport"></a>Configuration de la signature, de la compression et du chiffrement dans le transport AS2
Vous pouvez configurer les signatures numériques, la vérification des signatures, le chiffrement et le déchiffrement à partir de la console Administration [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Cette configuration requiert que vous définissiez les propriétés adéquates pour les pipelines AS2 et tiers BizTalk.  
  
## <a name="using-as2-pipelines"></a>Utilisation de Pipelines AS2  
 Pour aider à sécuriser un message AS2 entrant, utilisez un pipeline de réception AS2 (AS2EdiReceive ou AS2Receive) dans votre emplacement de réception. Le décodeur AS2 déchiffre, décompresse et/ou procède à la vérification des signatures sur les messages AS2. Pour plus d’informations sur la façon dont il le fait, consultez la section « Décodeur AS2 » de [les composants de réception AS2](../core/as2-receive-components.md).  
  
 Pour aider à sécuriser un message AS2 sortant, utilisez un pipeline d'envoi AS2 (AS2EdiSend ou AS2Send) dans votre port d'envoi. L'encodeur AS2 signe, compresse et chiffre les messages AS2 sortants. Pour plus d’informations sur la façon dont il le fait, consultez la section « Encodeur AS2 » de [composants d’envoi AS2](../core/as2-send-components.md).  
  
> [!IMPORTANT]
>  Une fois qu'un message a été signé, le blob de signature ne doit plus être modifié. S'il l'est, la signature sera corrompue. L'en-tête limite ou tout élément hors des en-têtes limites, peut être modifié, tandis que tout élément se trouvant à l'intérieur ne doit pas l'être.  
  
## <a name="setting-as2-agreement-properties"></a>Définition des propriétés de l'accord AS2  
 Pour configurer le traitement des signatures et du chiffrement, définissez les propriétés de l'accord AS2 comme suit :  
  
-   Pour signer, compresser et/ou chiffrer un message sortant, vérifiez le **Message doit être signé**, **Message doit être compressé**, et **Message doit être chiffré** propriétés de la **Validation** page de l’onglet d’accord unidirectionnel (pour le message AS2 sortant) dans le **propriétés de l’accord** boîte de dialogue.  
  
-   Pour demander un MDN signé en réponse à un message sortant, vérifiez le **exiger le MDN** et **exiger le MDN signé** propriétés sur le **accusés de réception (MDN)** page de la onglet d’accord unidirectionnel de la **propriétés de l’accord** boîte de dialogue.  
  
-   Pour indiquer qu’un message entrant est signé, compressé, et/ou chiffré, vérifiez le **utiliser les paramètres de l’accord pour validation et MDN au lieu de l’en-tête de message** propriété, le **Message doit être signé** propriété, le **Message doit être compressé** propriété et le **Message doit être chiffré** propriété sur le **Validation** page de l’accord unidirectionnel onglet (pour le message AS2 entrant) dans le **propriétés de l’accord** boîte de dialogue.  
  
    > [!NOTE]
    >  Lorsque le **utiliser les paramètres de l’accord pour validation et MDN au lieu de l’en-tête de message** propriété est sélectionnée, tous les détails de l’en-tête du message entrant sont ignorées et le message est traité selon les paramètres de l’accord.  
  
-   Pour spécifier un MDN signé en réponse à un message entrant, lorsque les propriétés de message entrant sont remplacées en sélectionnant le **utiliser les paramètres de l’accord pour validation et MDN au lieu de l’en-tête de message** propriété, vérifiez le **Exiger le MDN signé** propriété sur **accusés de réception (MDN)** page de la **propriétés de l’accord** boîte de dialogue.  
  
    > [!NOTE]
    >  Lorsque le **utiliser les paramètres de l’accord pour validation et MDN au lieu de l’en-tête de message** propriété est sélectionnée, tous les détails de l’en-tête du message entrant sont ignorées et le message est traité selon les paramètres de l’accord.  
  
-   Pour spécifier un MDN signé en réponse à un message entrant, lorsque les propriétés de message entrant ne sont pas remplacées (le **utiliser les paramètres de l’accord pour validation et MDN au lieu de l’en-tête de message** est désactivée), mais pas les en-têtes de message spécifier la signature, vérifiez le **signer le MDN si l’en-tête Disposition-Notification-Option n’est pas présent ou si l’en-tête Signed-Receipt-Protocol est défini comme facultatif** propriété sur le **paramètres MDN du récepteur**page de la **propriétés de l’accord** boîte de dialogue.  
  
-   Pour spécifier un certificat de signature différent de celui spécifié dans les propriétés du groupe BizTalk pour les messages AS2 sortants, sélectionnez **remplacer le certificat de Signature du groupe** dans les **lecertificatdeSignature**page de l’onglet d’accord unidirectionnel de la **propriétés de l’accord** boîte de dialogue zone et spécifiez un certificat de signature. Si cette propriété est définie, tout message AS2 correspondant à l’accord est signé à l’aide du certificat fourni dans le **le certificat de Signature** page et non par le certificat fourni dans le cadre des propriétés du groupe BizTalk.  
  
 Pour plus d’informations sur la configuration des propriétés de tiers, consultez [configuration des propriétés AS2](../core/configuring-as2-properties.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité AS2](../core/as2-security.md)   
 [Configuration des certificats pour AS2](../core/configuring-certificates-for-as2.md)   
 [Messages AS2](../core/as2-messages.md)   
 [AS2 Composants de réception](../core/as2-receive-components.md)   
 [AS2 Composants d’envoi](../core/as2-send-components.md)   
 [Configuration des propriétés AS2](../core/configuring-as2-properties.md)