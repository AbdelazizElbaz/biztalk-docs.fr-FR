---
title: "Comment installer les certificats pour les Messages chiffrés | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e11fdb81-041c-4ba6-849d-d511ead0e8be
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3b1df2e9e5bf42a215420dac155fafac8e92ae21
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-install-the-certificates-for-encrypted-messages"></a>Installation des certificats pour les messages chiffrés
La procédure suivante présente les étapes à suivre pour installer les certificats permettant de recevoir et d'envoyer des messages chiffrés.  
  
-   Pour installer les certificats dans le magasin dans un objectif de déchiffrement  
  
-   Pour installer les certificats dans le magasin dans un objectif de chiffrement  
  
-   Pour configurer les hôtes BizTalk pour la réception de messages chiffrés  
  
> [!NOTE]
>  Vous pouvez utiliser un seul certificat pour les opérations de signature et de déchiffrement, ou en utiliser un pour chaque fonction.  
  
### <a name="to-install-the-decryption-certificates-in-the-certificates-store"></a>Pour installer les certificats de déchiffrement dans le magasin  
  
1.  L'un des administrateurs de votre entreprise demande auprès de l'autorité de certification une paire de clés publique/privée pour le chiffrement qui sera utilisée par le serveur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
2.  Il envoie au Partenaire A la clé publique de chiffrement.  
  
3.  Dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], ouvrez une session en tant que compte de service pour l'instance d'hôte exécutant le gestionnaire qui recevra les messages du Partenaire A. Installez le certificat de clé privée du serveur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour le déchiffrement des messages dans le magasin personnel du compte de service. La figure suivante présente le magasin dans lequel vous installez le certificat.  
  
     ![Certificats requis pour recevoir des messages sécurisés](../core/media/bpi-sp-msgsec-certmgmt-certstores-receive.gif "BPI_SP_MSGSEC_CertMgmt_CertStores_Receive")  
  
4.  Dans Partenaire A, installez le certificat de clé publique du serveur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour le chiffrement des messages envoyés au Partenaire A dans le magasin approprié. (Si le partenaire a utilise [!INCLUDE[btsWin2kSvr](../includes/btswin2ksvr-md.md)], [!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)], [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)], installez la clé publique dans le magasin autres personnes.)  
  
### <a name="to-install-the-encryption-certificates-in-the-certificates-store"></a>Pour installer les certificats de chiffrement dans le magasin  
  
1.  Le Partenaire A demande une paire de clés publique/privée pour le chiffrement auprès de l'autorité de certification.  
  
2.  Le Partenaire A installe le certificat de clé privée pour déchiffrer les messages dans le magasin approprié. (Si le Partenaire A exécute [!INCLUDE[btsWin2kSvr](../includes/btswin2ksvr-md.md)], [!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)] ou [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)], installez la clé privée dans le magasin de certificats personnel.)  
  
3.  Le Partenaire A vous envoie sa clé publique pour le chiffrement des messages vers le Partenaire A.  
  
4.  Dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], connectez-vous au serveur ayant une instance d'hôte qui exécute un gestionnaire qui enverra les messages au Partenaire A. Installez le certificat de clé publique de ce partenaire afin de chiffrer les messages envoyés au Partenaire A dans le magasin Autres personnes. La figure suivante présente le magasin dans lequel vous installez le certificat.  
  
     ![Certificats requis pour envoyer des messages sécurisés](../core/media/bpi-sp-msgsec-certmgmt-certstores-send.gif "BPI_SP_MSGSEC_CertMgmt_CertStores_Send")  
  
### <a name="to-configure-biztalk-hosts-for-receiving-encrypted-messages"></a>Pour configurer les hôtes BizTalk pour la réception de messages chiffrés  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la console, développez **paramètres de plateforme**, développez **hôtes**.  
  
    1.  Dans le volet droit, cliquez sur un hôte BizTalk qui est le Gestionnaire de réception des messages chiffrés, puis cliquez sur **propriétés**.  
  
    2.  Sur le **propriétés de l’hôte** boîte de dialogue, cliquez sur **certificat**, cliquez sur **Parcourir**.  
  
    3.  Sur le **sélectionner un certificat** boîte de dialogue, sélectionnez le certificat de déchiffrement que vous avez installé, puis fermez toutes les boîtes de dialogue.  
  
        > [!NOTE]
        >  Pour plus d’informations, consultez [comment modifier les propriétés de l’hôte](../core/how-to-modify-host-properties.md).  
  
## <a name="next-steps"></a>Étapes suivantes  
 Vous créez un pipeline afin de recevoir des messages chiffrés dans [comment configurer BizTalk Server pour recevoir des Messages chiffrés](../core/how-to-configure-biztalk-server-for-receiving-encrypted-messages.md)  
  
 Pour créer un pipeline pour envoyer des messages chiffrés [comment configurer BizTalk Server pour envoyer des Messages chiffrés](../core/how-to-configure-biztalk-server-for-sending-encrypted-messages.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Certificats utilisés par BizTalk Server pour les Messages chiffrés](../core/certificates-that-biztalk-server-uses-for-encrypted-messages.md)   
 [Envoyer et recevoir des Messages chiffrés](../core/sending-and-receiving-encrypted-messages.md)