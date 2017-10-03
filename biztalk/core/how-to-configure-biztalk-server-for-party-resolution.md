---
title: "Comment configurer BizTalk Server pour la résolution du tiers | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8ac330b9-3498-4c98-a6e8-d2c02cd641dd
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f9d7a21b4edf5df4bd903763bcb3d1a8a8c6e1ea
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-biztalk-server-for-party-resolution"></a>Configuration de BizTalk Server pour la résolution de tiers
La procédure suivante présente les étapes à suivre pour configurer [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour la résolution de tiers.  
  
-   Pour installer les certificats dans le magasin de certificats afin de recevoir des messages signés  
  
-   Pour créer un tiers afin de représenter votre partenaire  
  
-   Pour créer un pipeline pour la résolution de tiers à l'aide de certificats  
  
-   Pour configurer l'emplacement de réception pour la résolution de tiers à l'aide de certificats  
  
### <a name="to-install-the-certificates-in-the-certificates-store-to-receive-signed-messages"></a>Pour installer les certificats dans le magasin de certificats afin de recevoir des messages signés  
  
1.  Le Partenaire A demande une paire de clés publique/privée pour les signatures numériques auprès de l'autorité de certification.  
  
2.  Le Partenaire A vous envoie sa clé publique pour les signatures numériques.  
  
3.  Dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], connectez-vous au serveur ayant une instance d'hôte qui exécute un gestionnaire qui reçoit les messages du Partenaire A. Installez le certificat de clé publique de ce partenaire afin de vérifier sa signature dans le magasin Autres personnes. La figure suivante présente le magasin dans lequel vous installez le certificat.  
  
     ![Certificats requis pour recevoir des messages sécurisés](../core/media/bpi-sp-msgsec-certmgmt-certstores-receive.gif "BPI_SP_MSGSEC_CertMgmt_CertStores_Receive")  
  
4.  Dans Partenaire A, installez le certificat de clé privée du Partenaire A pour signer les messages dans le magasin approprié. (Si le Partenaire A utilise [!INCLUDE[btsWin2kSvr](../includes/btswin2ksvr-md.md)], [!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)] ou [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)], installez la clé privée dans le magasin personnel du compte qui signera les messages envoyés à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].)  
  
    > [!NOTE]
    >  Cette étape est exactement le même que l’étape « pour installer les certificats dans le magasin de certificats pour recevoir des messages signés » dans [comment installer les certificats pour les Signatures numériques](../core/how-to-install-the-certificates-for-digital-signatures.md).  
  
### <a name="to-create-a-party-to-represent-your-partner"></a>Pour créer un tiers afin de représenter votre partenaire  
  
1.  Dans la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la console, la création d’un tiers pour le partenaire A. Pour plus d’informations sur la création d’un tiers, consultez [la création d’un tiers](http://msdn.microsoft.com/library/f6feca1d-bc83-4fb6-981d-26c9e0d53044).  
  
2.  Dans le **certificats** propriétés, sélectionnez la clé publique de signature de certificat à utiliser pour identifier ce tiers, partenaire A.  
  
### <a name="to-create-a-pipeline-for-party-resolution-using-certificates"></a>Pour créer un pipeline pour la résolution de tiers à l'aide de certificats  
  
1.  Dans l'Explorateur de solutions de Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], sélectionnez le projet dans lequel créer le pipeline.  
  
    1.  Sur le **fichier** menu, cliquez sur **ajouter un nouvel élément**.  
  
    2.  Dans le **ajouter un nouvel élément** boîte de dialogue, développez les éléments de projet BizTalk, cliquez sur **fichiers de Pipeline**, puis cliquez sur le **Pipeline de réception** modèle.  
  
    3.  Dans le **nom** , tapez un nom pour le pipeline.  
  
    4.  Cliquez sur **Ajouter**.  
  
         Le nouveau pipeline apparaît dans l'Explorateur de solutions.  
  
2.  Faites glisser le composant de pipeline Décodeur MIME/SMIME dans le **Decode** étape d’un pipeline de réception.  
  
     ![MIME &#47; Composant de pipeline décodeur SMIME](../core/media/bts-dev-mimesmimedecoder.gif "BTS_DEV_MIMESMIMEDecoder")  
  
    -   Configurer les propriétés du composant de pipeline Décodeur MIME/SMIME dans le **propriétés** fenêtre. Pour plus d’informations sur le décodeur MIME/SMIME, consultez [comment configurer le composant de Pipeline décodeur MIME-SMIME](../core/how-to-configure-the-mime-smime-decoder-pipeline-component.md).  
  
    > [!NOTE]
    >  Vous pouvez configurer les propriétés de pipeline d'un emplacement de réception à l'aide de la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] après le déploiement du pipeline dans un groupe BizTalk. Vous pouvez configurer des propriétés de pipeline différentes pour chaque emplacement de réception du groupe BizTalk. Pour plus d’informations, consultez [comment configurer les propriétés de Pipeline par instance pour un emplacement de réception](../core/how-to-configure-per-instance-pipeline-properties-for-a-receive-location.md).  
  
    > [!NOTE]
    >  Le composant de pipeline Décodeur MIME/SMIME effectue à la fois le déchiffrement et la validation des signatures numériques (lorsqu'il est configuré pour exécuter ces deux fonctions). Par conséquent, si vous configurez [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour recevoir des messages chiffrés et signés, vous pouvez utiliser le même pipeline de réception. En d'autres termes, il est inutile de créer des pipelines distincts pour le chiffrement et la validation des signatures numériques.  
  
3.  Faites glisser le composant de pipeline Résolution du tiers dans le **Résoudretiers** étape d’un pipeline de réception. Pour plus d’informations sur le composant de pipeline Résolution du tiers, consultez [comment configurer le composant de Pipeline résolution tiers](../core/how-to-configure-the-party-resolution-pipeline-component.md).  
  
    > [!NOTE]
    >  Vous pouvez également utiliser le pipeline XMLReceive par défaut au lieu d'en créer un nouveau. Ce pipeline exécute le composant résolution du tiers, qui résout le certificat soumise à l’ID de tiers. Notez que le pipeline XMLReceive a une phase de décodage vide, et par conséquent, vous ne pouvez pas l’utiliser pour recevoir des messages chiffrés ou vérifier les signatures numériques.  
  
    -   Dans la fenêtre Propriétés, configurez la propriété de pipeline Résolution du tiers **résoudre le tiers par le certificat** à `True`.  
  
4.  Construisez et déployez le pipeline de réception.  
  
### <a name="to-configure-the-receive-location-for-party-resolution-using-certificates"></a>Pour configurer l'emplacement de réception pour la résolution de tiers à l'aide de certificats  
  
1.  Ajoutez l'assembly BizTalk créé dans la procédure précédente à l'application BizTalk en incluant les emplacements de réception afin de recevoir des messages signés. Pour plus d’informations sur l’ajout d’assemblys BizTalk, consultez [l’ajout d’un BizTalk Assembly à une Application](../core/how-to-add-a-biztalk-assembly-to-an-application.md).  
  
2.  Configurez les emplacements de réception de l'application BizTalk avec le pipeline de réception créé dans la procédure précédente. Pour plus d’informations sur la façon de configurer les emplacements de réception, consultez [comment modifier les propriétés d’un emplacement de réception](../core/how-to-edit-the-properties-of-a-receive-location.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Comment configurer BizTalk Server pour la réception des Messages signés](../core/how-to-configure-biztalk-server-for-receiving-signed-messages.md)   
 [Certificats utilisés par BizTalk Server pour les Messages signés](../core/certificates-that-biztalk-server-uses-for-signed-messages.md)   
 [Authentification des messages entrants](../core/inbound-message-authentication.md)   
 [L’utilisation de certificats pour la résolution du tiers](../core/using-certificates-for-party-resolution.md)