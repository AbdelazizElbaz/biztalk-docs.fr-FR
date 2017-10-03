---
title: Comment configurer le composant de Pipeline encodeur MIME-SMIME | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, encrypting digital signatures
- pipeline components, MIME/SMIME Encoder
- Partner Management, security
- MIME/SMIME Encoder [pipeline component], configuring
- messages, encoding
- messages, multi-parts
ms.assetid: dcbb08e8-d300-4e7f-9c1c-907fb602e721
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 07cabef8510fb2189da759ba9b0c156ef672410e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-the-mime-smime-encoder-pipeline-component"></a>Comment configurer le composant de Pipeline encodeur MIME-SMIME
Utilisez le composant de pipeline Encodeur MIME/SMIME pour coder, chiffrer et signer des messages sortants. Ce composant est utile lorsque l'échange de documents sécurisé entre BizTalk Server et des partenaires externes est nécessaire. Vous pouvez également l’utiliser pour envoyer des messages à parties multiples à BizTalk Server.  
  
> [!NOTE]
>  Dans BizTalk 2006, le composant de pipeline Encodeur MIME/SMIME ne dispose pas du support 64 bits natif.  Il doit donc être exécuté dans un processus d'émulation 32 bits (WOW64).  Cela implique que l'instance de l'hôte où s'exécute ce composant de codage (ou le pipeline d’envoi dont il fait partie) s'exécute dans un mode d'émulation 32 bits.  Tenez compte des implications de cette restriction, notamment concernant les performances, pour les autres éléments de BizTalk qui s'exécutent dans cette même instance de l'hôte.  
  
### <a name="to-configure-the-properties-for-the-mimesmime-encoder-pipeline-component"></a>Pour configurer les propriétés du composant de pipeline Encodeur MIME/SMIME  
  
1.  Faites glisser le composant de pipeline Encodeur MIME/SMIME dans la phase de codage d'un pipeline d'envoi.  
  
2.  Dans la fenêtre Propriétés, dans le **propriétés du composant de Pipeline** section, procédez comme suit.  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Ajouter le certificat de signature au Message**|Si le **le Type de Signature** propriété n’est pas **NoSign**, vous pouvez sélectionner si vous souhaitez ajouter le certificat de signature au message signé en définissant le **ajouter le certificat de signature au Message** propriété.<br /><br /> Valeur par défaut : **True**|  
    |**Liste de révocation**|Spécifie s'il convient de vérifier la liste de révocation des certificats lors du traitement d'un message SMIME.<br /><br /> Valeur par défaut : **True**|  
    |**Le codage de transfert de contenu**|Indique le format de codage.<br /><br /> Options : Base64, Quoted Printable, SevenBit, EightBit, Binary et UUEncode.<br /><br /> Valeur par défaut : **Base64**|  
    |**Activer le chiffrement**|La valeur **True** si vous souhaitez chiffrer le message sortant. Si cette option est activée, l’utilisateur peut sélectionner l’algorithme de chiffrement à utiliser en définissant le **algorithme de chiffrement** propriété. Dans le cadre du chiffrement des messages, le composant de pipeline Encodeur MIME/SMIME utilise le certificat de clé publique associé à un port d'envoi de l'Explorateur BizTalk.<br /><br /> Valeur par défaut : **False**|  
    |**Algorithme de chiffrement**|Définir l'algorithme de chiffrement.<br /><br /> Cette propriété peut uniquement être définie si **activer le chiffrement** a la valeur **True**.<br /><br />**En commençant par [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] et les versions plus récentes**, chiffrement AES est automatiquement inclus. Les options sont : DES3, DES, RC2, AES128 (par défaut), AES192 et AES256.<br /><br />Pour précédente [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] versions, options incluent : DES3 (valeur par défaut), DES, RC2.|  
    |**Envoyer le corps en tant que pièce jointe**|La valeur **True** si vous souhaitez envoyer le corps d’un message BizTalk en tant que pièce jointe MIME.<br /><br /> Valeur par défaut : **False** **Important :** vous ne devez pas définir cette propriété **True** lors de l’envoi des messages entre les serveurs BizTalk Server. Sinon, le décodage du message nécessitera un codage spécial, car le message est interprété au niveau de la réception en tant que message en deux parties.|  
    |**Type de signature**|Si vous voulez signer le message sortant, sélectionnez un format de signature avec cette propriété. Vous avez le choix parmi trois possibilités :<br /><br /> -   **NoSign**. le message n'est pas signé.<br />-   **ClearSign**. La signature est ajoutée au message. **ClearSign** ne peut pas être utilisé si **activer le chiffrement** a la valeur **True**.<br />-   **BlobSign**. le message contient une signature et est codé.<br /><br /> Dans le cadre de la signature des messages, le composant Encodeur MIME/SMIME utilise le certificat client de la clé privée associé au groupe BizTalk de la console Administration de BizTalk.<br /><br /> Valeur par défaut : **NoSign**|  
  
 Pour définir le nom de fichier des pièces jointes MIME, utilisez le **nom de fichier** propriété dans le **système** espace de noms pour la partie du message.  
  
## <a name="see-also"></a>Voir aussi  
 [Composant de Pipeline encodeur MIME-SMIME](../core/mime-smime-encoder-pipeline-component.md)   
 [Configuration des composants de Pipeline natifs](../core/configuring-native-pipeline-components.md)   
 [Propriétés et schéma de propriété MIME-SMIME](../core/mime-smime-property-schema-and-properties.md)   
 [MIME (exemple BizTalk Server)](../core/mime-biztalk-server-sample.md)