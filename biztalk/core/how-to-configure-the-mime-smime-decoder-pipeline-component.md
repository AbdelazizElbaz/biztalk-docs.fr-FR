---
title: "Comment configurer le composant de Pipeline décodeur MIME-SMIME | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, attachments
- pipeline components, MIME/SMIME Decoder
- MIME/SMIME Decoder [pipeline component], configuring
- messages, verifying
- messages, decoding
- messages, digital signatures
- messages, security
ms.assetid: bfd44893-f1c3-4524-abc6-f820b8c0ef07
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a32137528de5ea18ea5698ab823c2e703651b71b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-the-mime-smime-decoder-pipeline-component"></a>Comment configurer le composant de Pipeline décodeur MIME-SMIME
Le composant de pipeline Décodeur MIME/SMIME sert à décoder et à déchiffrer les messages MIME/SMIME codés et à vérifier les signatures numériques des messages signés. Il est utile lorsque l'échange de documents sécurisés entre des partenaires externes et BizTalk Server est nécessaire. Il peut aussi être utilisé pour recevoir des messages avec des pièces jointes.  
  
> [!NOTE]
>  Dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], le composant de pipeline Décodeur MIME/SMIME ne dispose pas du support 64 bits natif.  Il doit donc être exécuté dans un processus d'émulation 32 bits (WOW64).  Cela implique que l'instance de l'hôte où s'exécute ce composant de décodage (ou le pipeline de réception dont il fait partie) s'exécute dans un mode d'émulation 32 bits.  Tenez compte des implications de cette restriction, notamment concernant les performances, pour les autres éléments de BizTalk qui s'exécutent dans cette même instance de l'hôte.  
  
> [!NOTE]
>  Le composant Décodeur MIME/SMIME est également utilisé dans l'adaptateur POP3.  Par conséquent, la restriction du support 64 bits natif s'applique aussi à l'instance de l'hôte où l'adaptateur POP3 s'exécute.  Consultez les informations relatives à l’adaptateur POP3 dans [l’adaptateur POP3](../core/pop3-adapter.md).  
  
### <a name="to-configure-the-properties-for-the-mimesmime-decoder-pipeline-component"></a>Pour configurer les propriétés du composant de pipeline Décodeur MIME/SMIME  
  
1.  Faites glisser le composant de pipeline Décodeur MIME/SMIME dans l'étape Décoder d'un pipeline de réception.  
  
2.  Dans la fenêtre Propriétés, dans le **propriétés du composant de Pipeline** section, procédez comme suit.  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Autoriser les messages Non MIME**|Définissez cette propriété sur **True** si vous attendez que le pipeline de réception peut recevoir des messages ne sont pas codés au format MIME. Cette option est utile lorsque le composant de pipeline Décodeur MIME/SMIME est utilisé dans un pipeline recevant des messages de formes différentes, par exemple des messages MIME codés ou XML standard. Par défaut, cette propriété est définie **False**, sens que le composant génère une erreur si elle reçoit un non MIME codés message en entrée. **Remarque :** le décodeur MIME balaie les 1 024 premiers octets du message entrant pour rechercher l’en-tête « MIME-Version ». Si cet en-tête est introuvable, le message est traité comme un message non MIME. <br /><br /> Valeur par défaut : **False**|  
    |**Type de contenu du corps**|Indiquer le type de contenu de la partie MIME. La partie MIME possédant ce type de contenu deviendra le corps du message BizTalk.<br /><br /> Valeur par défaut : Aucun|  
    |**Index du corps**|Indiquer l'index de base 1 dans la liste des parties MIME. La partie MIME au niveau de cet index dans la liste deviendra le corps du message BizTalk. Pour désactiver la sélection du corps par index, utilisez la valeur **0**.<br /><br /> Valeur par défaut : **0**|  
    |**Liste de révocation**|Définissez cette propriété sur **True** si vous souhaitez vérifier la liste de révocation de certificats pour les certificats utilisés par les expéditeurs pour signer les messages sont envoyés à BizTalk Server. La désactivation de cette option augmente les performances du composant.<br /><br /> La liste de révocation des certificats associée à un certificat est téléchargée à partir d'un site Web distant (Verisign.com, par exemple). Si le serveur BizTalk Server ne peut pas se connecter au site Web distant, le message est en échec dans le pipeline.<br /><br /> Valeur par défaut : **True**|  
  
## <a name="see-also"></a>Voir aussi  
 [Composant de Pipeline décodeur MIME-SMIME](../core/mime-smime-decoder-pipeline-component.md)   
 [Configuration des composants de Pipeline natifs](../core/configuring-native-pipeline-components.md)   
 [Propriétés et schéma de propriété MIME-SMIME](../core/mime-smime-property-schema-and-properties.md)   
 [MIME (exemple BizTalk Server)](../core/mime-biztalk-server-sample.md)