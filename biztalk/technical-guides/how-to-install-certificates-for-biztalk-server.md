---
title: Comment installer des certificats de BizTalk Server | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 70a89595-8828-4872-b78b-77e9b0b048b8
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d799956d25bfe8e494fcbc2fbc6cbea770a92fdb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-install-certificates-for-biztalk-server"></a>Comment installer des certificats de BizTalk Server
Transfert de données pour aider à sécuriser sur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], vous devez ajouter le certificat approprié au magasin de certificats approprié et associer les certificats aux artefacts BizTalk appropriés. Cette rubrique décrit comment afficher l’interface de la Console de gestion des certificats pour les magasins de certificats ordinateur Local et l’utilisateur actuel et comment installer le certificat approprié dans le magasin approprié.  
  
 Les certificats indiqués dans le tableau suivant sont utilisés à l’aide de l’authentification, de vérifier la signature pour, chiffrer et déchiffrer les messages.  
  
|Utilisation des certificats|Type de certificat|Magasin de certificats|  
|-----------------------|----------------------|-----------------------|  
|Signature (sortie)|Propre clé privée (.pfx)|Utilisateur actuel\\<br />Magasin personnel de chaque serveur BizTalk server qui héberge un pipeline Encodeur MIME/SMIME chaque compte de service d’instance hôte|  
|Vérification de signature (entrée)|Clé publique du partenaire commercial (.cer)|Local\Autres personnes stocker de chaque serveur BizTalk server qui héberge un pipeline de décodeur MIME/SMIME en tant que chaque compte de service d’instance hôte|  
|Chiffrement (sortie)|Clé publique du partenaire commercial (.cer)|Stocker local\Autres personnes de chaque serveur BizTalk server qui héberge un pipeline d’encodeur MIME/SMIME|  
|Déchiffrement (entrée)|Propre clé privée (.pfx)|Actuel\Personnel stocker de chaque serveur BizTalk server qui héberge un pipeline de décodeur MIME/SMIME en tant que chaque compte de service d’instance hôte|  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour effectuer les procédures décrites dans cette rubrique, vous devez être connecté en tant que membre de le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] groupe Administrateurs.  
  
### <a name="to-display-the-certificates-management-console"></a>Pour afficher la Console de gestion des certificats  
  
1.  Cliquez sur **Démarrer**, cliquez sur **exécuter**, type **MMC**, puis cliquez sur **OK** pour ouvrir le **Microsoft Management Console**.  
  
2.  Cliquez sur le **fichier** menu, puis sur **ajouter ou supprimer des composants logiciels enfichables** pour afficher les **ajouter ou supprimer des composants logiciels enfichables** boîte de dialogue.  
  
3.  Cliquez sur le **ajouter** bouton pour afficher la **ajouter Standalone Snap-in** boîte de dialogue.  
  
4.  Sélectionnez **certificats** dans la liste des composants logiciel enfichables, puis cliquez sur **ajouter**.  
  
5.  Sélectionnez **compte d’ordinateur**, cliquez sur **suivant**, puis cliquez sur **Terminer**. Cette opération ajoute le **Console de gestion des certificats** pour l’interface **ordinateur Local**.  
  
6.  Vérifiez que **certificats** est toujours sélectionné dans la liste des composants logiciel enfichables, puis cliquez sur **ajouter** à nouveau.  
  
7.  Sélectionnez **mon compte d’utilisateur**, puis cliquez sur **Terminer**. Cette opération ajoute le **Console de gestion des certificats** pour l’interface **utilisateur actuel**.  
  
    > [!NOTE]  
    >  Cela permet d’afficher le **Console de gestion des certificats** pour le compte que vous êtes actuellement connecté en tant que. Pour importer des certificats dans le magasin Personnel d'un compte de service, vous devez d'abord ouvrir une session avec les informations d'identification de ce compte.  
  
8.  Cliquez sur le **fermer** bouton sur le **Standalone Snap-in** boîte de dialogue.  
  
9. Cliquez sur le **OK** bouton sur le **ajouter ou supprimer des composants logiciels enfichables** boîte de dialogue.  
  
### <a name="to-install-a-certificate-for-receiving-encrypted-messages"></a>Pour installer un certificat pour la réception des messages chiffrés  
  
1.  Demander une paire de clés publique-privée pour les signatures numériques à partir de l’autorité de certification (CA) pour [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] à utiliser.  
  
2.  Envoyer au partenaire de la clé publique pour le chiffrement.  
  
3.  Dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], connecter en tant que compte de service pour l’instance d’hôte exécutant le gestionnaire qui recevra les messages du partenaire. Installer le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] certificat de clé privée pour le déchiffrement des messages dans le magasin personnel du compte de service.  
  
    > [!NOTE]  
    >  Pour plus d’informations sur la procédure utilisée pour installer des certificats pour le chiffrement, consultez [comment installer les certificats pour les Messages chiffrés](http://go.microsoft.com/fwlink/?LinkId=155156) (http://go.microsoft.com/fwlink/?LinkId=155156) dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] aide. Pour plus d’informations sur l’outil utilisé pour importer un certificat dans le magasin de certificats, consultez [l’utilitaire Assistant certificat](http://go.microsoft.com/fwlink/?LinkId=155157) (http://go.microsoft.com/fwlink/?LinkId=155157) dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] aide.  
  
4.  Installer le partenaire le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] certificat de clé publique pour chiffrer les messages dans le magasin approprié. Si le partenaire est à l’aide de Windows 2000 Server, Windows Server 2003 ou Windows Server 2008, ils doivent installer la clé publique dans le magasin autres personnes.  
  
### <a name="to-install-a-certificate-for-sending-encrypted-messages"></a>Pour installer un certificat pour l’envoi de messages chiffrés  
  
1.  Avoir le partenaire de demander une paire de clés publique-privée pour le chiffrement à partir de l’autorité de certification (CA).  
  
2.  Avoir le partenaire vous envoie sa clé publique pour chiffrer les messages à envoyer au partenaire.  
  
3.  Installer le certificat de clé privée pour le déchiffrement des messages dans le magasin approprié du partenaire. Si le partenaire est à l’aide de Windows 2000 Server, Windows Server 2003 ou Windows Server 2008, ils doivent installer la clé privée dans le magasin de certificats personnel.  
  
    > [!NOTE]  
    >  Pour plus d’informations sur la procédure utilisée pour installer des certificats pour le chiffrement, consultez [comment installer les certificats pour les Messages chiffrés](http://go.microsoft.com/fwlink/?LinkId=155156) (http://go.microsoft.com/fwlink/?LinkId=155156) dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] aide. Pour plus d’informations sur l’outil utilisé pour importer un certificat dans le magasin de certificats, consultez [l’utilitaire Assistant certificat](http://go.microsoft.com/fwlink/?LinkId=155157) (http://go.microsoft.com/fwlink/?LinkId=155157) dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] aide.  
  
4.  Dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], ouvrez une session sur le serveur qui a une instance d’hôte qui exécute un gestionnaire qui enverra les messages au partenaire. Installez le certificat de clé publique du partenaire pour le chiffrement des messages envoyés au partenaire dans le magasin autres personnes.  
  
### <a name="to-install-a-certificate-for-receiving-signed-messages"></a>Pour installer un certificat pour la réception de messages signés  
  
1.  Avoir le partenaire de demander une paire de clés publique-privée pour les signatures numériques à partir de l’autorité de certification (CA).  
  
2.  Avoir le partenaire vous envoie sa clé publique pour les signatures numériques.  
  
3.  Installer le certificat de clé privée pour signer les messages dans le magasin approprié du partenaire. Si elles sont à l’aide de Windows 2000 Server, Windows Server 2003 ou Windows Server 2008, demandez-leur d’installer la clé privée dans le magasin personnel pour le compte qui signera les messages envoyés à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
    > [!NOTE]  
    >  Pour plus d’informations sur la procédure utilisée pour installer des certificats pour le chiffrement, consultez [comment installer les certificats pour les Messages chiffrés](http://go.microsoft.com/fwlink/?LinkId=155156) ([http://go.microsoft.com/fwlink/?LinkId=155156](http://go.microsoft.com/fwlink/?LinkId=155156)) dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] aide. Pour plus d’informations sur l’outil utilisé pour importer un certificat dans le magasin de certificats, consultez [l’utilitaire Assistant certificat](http://go.microsoft.com/fwlink/?LinkId=155157) (http://go.microsoft.com/fwlink/?LinkId=155156) dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] aide.  
  
4.  Dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], ouvrez une session sur le serveur qui a une instance d’hôte qui exécute un gestionnaire qui reçoit les messages du partenaire. Installez le certificat de clé publique du partenaire afin de vérifier leur signature dans le magasin autres personnes.  
  
### <a name="to-install-a-certificate-for-sending-signed-messages"></a>Pour installer un certificat pour l’envoi de messages signés  
  
1.  Demander une paire de clés publique-privée pour les signatures numériques à partir de l’autorité de certification (CA) pour [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] à utiliser.  
  
2.  Envoyer au partenaire de la clé publique pour les signatures numériques.  
  
3.  Dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], connecter en tant que compte de service pour l’instance d’hôte exécutant le gestionnaire qui enverra les messages au partenaire. Installer le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] certificat de clé privée pour signer les messages dans le magasin personnel du compte de service.  
  
    > [!NOTE]  
    >  Pour plus d’informations sur la procédure utilisée pour installer des certificats pour le chiffrement, consultez [comment installer les certificats pour les Messages chiffrés](http://go.microsoft.com/fwlink/?LinkId=155156) (http://go.microsoft.com/fwlink/?LinkId=155156) dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] aide. Pour plus d’informations sur l’outil utilisé pour importer un certificat dans le magasin de certificats, consultez [l’utilitaire Assistant certificat](http://go.microsoft.com/fwlink/?LinkId=155157) (http://go.microsoft.com/fwlink/?LinkId=155157) dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] aide.  
  
4.  Installer le partenaire le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] certificat de clé publique pour vérifier sa signature numérique dans le magasin approprié. Si le partenaire est à l’aide de Windows 2000 Server, Windows Server 2003 ou Windows Server 2008, ils doivent installer la clé publique dans le magasin autres personnes.