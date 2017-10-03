---
title: "Comment installer les certificats pour les Signatures numériques | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 910ccd84-c022-46a5-a9de-b99046a480b8
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7a755e59c7c916f3abe037513ddbc9e2a89892fb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-install-the-certificates-for-digital-signatures"></a>Installation des certificats pour les signatures numériques
La procédure suivante présente les étapes à suivre pour installer les certificats permettant de recevoir et d'envoyer des messages signés.  
  
-   Pour installer les certificats dans le magasin de certificats afin de recevoir des messages signés  
  
-   Pour installer les certificats de signature afin d'envoyer des messages signés dans le magasin de certificats  
  
-   Pour configurer le groupe BizTalk afin d'envoyer des messages signés  
  
> [!NOTE]
>  Vous pouvez utiliser un seul certificat pour les opérations de signature et de déchiffrement, ou en utiliser un pour chaque fonction.  
  
> [!IMPORTANT]
>  Le serveur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] n'utilise qu'un seul certificat pour la signature de tous les messages sortants. En d'autres termes, vous ne pouvez pas utiliser de certificats de signature différents selon la personne à qui vous envoyez le message.  
  
### <a name="to-install-the-certificates-in-the-certificates-store-to-receive-signed-messages"></a>Pour installer les certificats dans le magasin de certificats afin de recevoir des messages signés  
  
1.  Le Partenaire A demande une paire de clés publique/privée pour les signatures numériques auprès de l'autorité de certification.  
  
2.  Le Partenaire A vous envoie sa clé publique pour les signatures numériques.  
  
3.  Dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], connectez-vous au serveur ayant une instance d'hôte qui exécute un gestionnaire qui reçoit les messages du Partenaire A. Installez le certificat de clé publique de ce partenaire afin de vérifier sa signature dans le magasin Autres personnes. La figure suivante présente le magasin dans lequel vous installez le certificat.  
  
     ![Certificats requis pour recevoir des messages sécurisés](../core/media/bpi-sp-msgsec-certmgmt-certstores-receive.gif "BPI_SP_MSGSEC_CertMgmt_CertStores_Receive")  
  
4.  Dans Partenaire A, installez le certificat de clé privée du Partenaire A pour signer les messages dans le magasin approprié. (Si le Partenaire A exécute [!INCLUDE[btsWin2kSvr](../includes/btswin2ksvr-md.md)], [!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)] ou [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)], installez la clé privée dans le magasin personnel du compte qui signera les messages envoyés à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].)  
  
### <a name="to-install-the-signing-certificates-for-sending-signed-messages-in-the-certificates-store"></a>Pour installer les certificats de signature afin d'envoyer des messages signés dans le magasin de certificats  
  
1.  L'un des administrateurs de votre entreprise demande auprès de l'autorité de certification une paire de clés publique/privée pour les signatures numériques qui sera utilisée par le serveur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
2.  Il envoie au Partenaire A (ainsi qu'à tous les autres partenaires) la clé publique pour les signatures numériques.  
  
3.  Dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], ouvrez une session en tant que compte de service pour l'instance d'hôte exécutant le gestionnaire qui enverra les messages au Partenaire A. Installez le certificat de clé privée du serveur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour la signature des messages dans le magasin personnel du compte de service. La figure suivante présente le magasin dans lequel vous installez le certificat.  
  
     ![Certificats requis pour envoyer des messages sécurisés](../core/media/bpi-sp-msgsec-certmgmt-certstores-send.gif "BPI_SP_MSGSEC_CertMgmt_CertStores_Send")  
  
4.  Dans Partenaire A, installez le certificat de clé publique du serveur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour la vérification de sa signature numérique dans le magasin approprié. (Si le Partenaire A exécute [!INCLUDE[btsWin2kSvr](../includes/btswin2ksvr-md.md)], [!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)] ou [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)], installez la clé publique dans le magasin Autres personnes.)  
  
### <a name="to-configure-the-biztalk-group-for-sending-signed-messages"></a>Pour configurer le groupe BizTalk afin d'envoyer des messages signés  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Avec le bouton droit **groupe BizTalk**, puis cliquez sur **propriétés**.  
  
3.  Sur le **propriétés d’un groupe** boîte de dialogue, cliquez sur **certificat**, cliquez sur **Parcourir**.  
  
4.  Sur le **sélectionner un certificat** boîte de dialogue, sélectionnez le certificat de signature que vous avez installé, puis fermez toutes les boîtes de dialogue.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Vous créez un pipeline afin de recevoir des messages signés dans [comment configurer BizTalk Server pour la réception de Messages signés](../core/how-to-configure-biztalk-server-for-receiving-signed-messages.md).  
  
 Pour créer un pipeline pour envoyer des messages signés [comment configurer BizTalk Server pour l’envoi de Messages signés](../core/how-to-configure-biztalk-server-for-sending-signed-messages.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Certificats utilisés par BizTalk Server pour les Messages signés](../core/certificates-that-biztalk-server-uses-for-signed-messages.md)   
 [Envoyer et recevoir des Messages signés](../core/sending-and-receiving-signed-messages.md)