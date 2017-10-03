---
title: Configuration des certificats pour AS2 | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c160f294-7529-4e0a-876c-5827feaed067
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cb2f9c22ddf41eec4133710de8a775bf8ff0b044
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-certificates-for-as2"></a>Configuration des certificats pour AS2
Pour sécuriser le transfert de données AS2 à l'aide du chiffrement et de signatures numériques, vous devez avoir installé les certificats appropriés, en plus de la configuration AS2 appropriée, sur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Cette rubrique décrit les certificats requis, leur configuration et leurs problèmes courants.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez ouvrir une session en tant que membre du groupe Administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
## <a name="certificates-required-for-as2-transport"></a>Certificats requis pour le transport AS2  
 Pour sécuriser le transfert de données AS2, vous devez ajouter le certificat approprié au magasin de certificats approprié et associer les certificats aux artefacts BizTalk appropriés. Les certificats suivants sont utilisés pour sécuriser les messages AS2 :  
  
|Utilisation des certificats|Type de certificat|Composant de pipeline|Contexte de l’utilisateur|Magasin de certificats|Lieu de définition|  
|-----------------------|----------------------|------------------------|------------------|-----------------------|-------------------|  
|Signature (sortie)|Propre clé privée (.pfx)|Encodeur AS2|Compte utilisé par l'instance de l'hôte associée au gestionnaire d'envoi.|Utilisateur actuel \ magasin Personnel de chaque [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] qui héberge un pipeline Encodeur AS2 pour chaque compte de service de l'instance de l'hôte|-   **Certificat** page de la **propriétés du groupe** boîte de dialogue. Il s'agit du certificat de signature par défaut utilisé lors de l'envoi de documents signés.<br />-Vous pouvez remplacer le paramètre de certificat par défaut et à la place utiliser différents certificats pour les différentes parties. Vous pouvez le faire en sélectionnant **remplacer le certificat de Signature du groupe** dans les **le certificat de Signature** page de l’onglet d’accord unidirectionnel de la **propriétés de l’accord** boîte de dialogue zone et spécifiez un certificat de signature. Si cette propriété est définie, tout message AS2 correspondant à l’accord est signé à l’aide du certificat fourni dans le **le certificat de Signature** page et non par le certificat fourni dans le cadre des propriétés du groupe BizTalk.|  
|Vérification de signature (entrée)|Clé publique du partenaire commercial (.cer)|Décodeur AS2|Compte utilisé par l'instance de l'hôte associée au gestionnaire de réception.|Ordinateur local \ magasin Autres personnes de chaque [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] qui héberge un pipeline Décodeur AS2 pour chaque compte de service de l'instance de l'hôte|**Certificat** page de la **propriétés de tiers** boîte de dialogue **Remarque :** le certificat utilisé pour vérifier une signature pour un tiers doit être unique parmi les certificats utilisés pour vérifier les signatures pour autres parties.|  
|Chiffrement (sortie)|Clé publique du partenaire commercial (.cer)|Encodeur AS2|Compte utilisé par l'instance de l'hôte associée au gestionnaire d'envoi.|Ordinateur local \ magasin Autres personnes de chaque [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] qui héberge un pipeline Encodeur AS2|**Certificat** page de la **propriétés de Port d’envoi** boîte de dialogue|  
|Déchiffrement (entrée)|Propre clé privée (.pfx)|Décodeur AS2|Compte utilisé par l'instance de l'hôte associée au gestionnaire de réception.|Utilisateur actuel \ magasin Personnel de chaque [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] qui héberge un pipeline Décodeur AS2 pour chaque compte de service de l'instance de l'hôte|Le Décodeur AS2 détermine le certificat en fonction des informations de certificat dans le message.<br /><br /> Pour le décodeur MIME BizTalk, le certificat doit être dans le **certificat** page de l’hôte utilisé pour la réception du message. Cela n'est pas nécessaire pour le Décodeur AS2.|  
  
## <a name="certificate-signing-for-outgoing-messages"></a>Certificat de signature des messages sortants  
 Les messages AS2 sortants sont signés à l'aide d'un certificat par défaut défini dans les propriétés du groupe BizTalk. Cependant, il peut arriver que les tiers recevant les messages veuillent que les messages soient signés avec un certificat privé qu'ils fournissent ou attendent un certificat différent à utiliser lors de la signature des messages sortants pour eux. Ce scénario de signature des messages sortants à l’aide d’autres certificats est activé si vous sélectionnez le **remplacer le certificat de Signature du groupe** dans les **le certificat de Signature** page de l’onglet d’accord unidirectionnel de la **propriétés de l’accord** boîte de dialogue zone et spécifiez un certificat de signature. Si un certificat est spécifié dans le cadre de l'accord AS2 pour un tiers, ce certificat est utilisé pour la signature des messages sortants. Si aucun certificat n'est défini pour le tiers, le certificat par défaut spécifié dans les propriétés du groupe BizTalk est utilisé.  
  
## <a name="adding-certificates-to-the-certificate-stores"></a>Ajout de certificats dans les magasins de certificats  
 Pour plus d’informations, consultez la section « Affichage de la Console de gestion des certificats » de [l’installation de certificats pour les adaptateurs WCF](../core/installing-certificates-for-the-wcf-adapters.md), ainsi que le [l’utilitaire Assistant certificat](../core/certificate-wizard-utility.md) rubrique.  
  
> [!IMPORTANT]
>  Le magasin de certificats Personnels sera disponible pour le traitement des messages uniquement si le profil utilisateur est chargé pour l'utilisateur dont les informations d'identification sont associées à l'instance hôte. Le magasin Personnel est utilisé pour les certificats de signature et de déchiffrement (la clé propre privée de l'utilisateur). Le profil utilisateur est chargé par défaut pour l'instance hôte In-process ; toutefois, il n'est pas chargé par défaut pour l'instance hôte isolé. Vous pouvez faire en sorte qu'une application charge le profil utilisateur pour l'hôte isolé.  Vous pouvez également contourner ce problème en utilisant le même nom de connexion pour l'instance hôte In-process et l'instance hôte isolé.  
  
## <a name="generating-certificates"></a>Génération de certificats  
 Les certificats peuvent être obtenus auprès d'une autorité de certification mais les étapes de demande d'un certificat peuvent varier selon les autorités de certification. Passez en revue les informations fournies sur le site Web de l'autorité de certification d'avant d'envoyer des demandes de certificat.  
  
> [!IMPORTANT]
>  Les certificats utilisés pour le transport AS2 doivent avoir les attributs requis pour l'utilisation prévue. Pour la signature et vérification de signature, le **utilisation de la clé** l’attribut du certificat doit être **Signature numérique**. Pour le chiffrement et le déchiffrement, la **utilisation de la clé** l’attribut du certificat doit être **chiffrement des données** ou **chiffrement de la clé**. Vous pouvez vérifier le **utilisation de la clé** attribut en double-cliquant sur le certificat, cliquez sur le **détails** onglet dans le **certificat** boîte de dialogue et en vérifiant la **Utilisation de la clé** champ.  
  
 Vous pouvez également générer des certificats dans Windows Server 2008 à l'aide des Services de certificats mais votre partenaire risque d'accepter ces certificats pour des raisons de test uniquement car ils sont auto-signés et non signés par une autorité de certification publique. Pour plus d’informations sur l’utilisation des Services de certificats pour demander des certificats, téléchargez **Windows Server 2008 Active Directory certificat Services Guide pas à pas** de [Guides pas à pas de Windows Server 2008 ](http://go.microsoft.com/fwlink/?LinkId=187916) ([http://go.microsoft.com/fwlink/?LinkId=187916](http://go.microsoft.com/fwlink/?LinkId=187916)).  
  
### <a name="to-configure-a-certificate-for-signing-outgoing-as2-messages"></a>Pour configurer un certificat pour signer des messages AS2 sortants  
  
1.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration, avec le bouton droit le **groupe BizTalk** nœud, puis cliquez sur **propriétés**.  
  
2.  Dans l’arborescence de la **propriétés d’un groupe** boîte de dialogue, cliquez sur **certificat**.  
  
3.  Dans le **certificat** volet, cliquez sur **Parcourir**, trouver le certificat que vous souhaitez utiliser pour la signature, puis cliquez sur **OK**.  
  
    > [!NOTE]
    >  Au lieu d'entrer le nom commun du certificat, vous pouvez saisir simplement l'empreinte. Vous pouvez obtenir l’empreinte numérique en double-cliquant sur le certificat dans le magasin de certificats dans la console MMC ou du système de fichiers, en cliquant sur le **détails** onglet, en cliquant sur le **l’empreinte numérique** champ, puis copiez l’empreinte .  
  
4.  Cliquez sur **OK**.  
  
### <a name="to-configure-a-certificate-for-signing-outgoing-as2-messages-for-a-specific-party"></a>Pour configurer un certificat pour la signature des messages AS2 sortants pour un tiers spécifique  
  
1.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration, cliquez sur le **Parties** nœud. À partir de la **tiers et profils d’entreprise** volet, à partir de la **accords** section, avec le bouton droit de l’accord est créé pour échanger des messages avec un tiers spécifique, puis cliquez sur  **Propriétés**.  
  
2.  Sous l’onglet accord unidirectionnel, cliquez sur **certificats de Signature**.  
  
3.  Sélectionnez le **groupe de remplacement de certificat de signature** case à cocher pour utiliser le certificat fourni dans cette page pour la signature des messages AS2 sortants et MDN.  
  
4.  Cliquez sur **Parcourir** pour afficher les **sélectionner un certificat** boîte de dialogue, dans laquelle vous sélectionnez le certificat de signature à appliquer aux messages transmis par ce tiers.  
  
5.  Le **nom commun** zone de texte affiche une description du certificat sélectionné.  
  
6.  Le **l’empreinte numérique** zone de texte affiche l’empreinte numérique du certificat. Le format de l'empreinte de certificat est HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH, où H est une valeur hexadécimale (nombre de 0 à 9 ou lettre de A à F).  
  
7.  Cliquez sur **supprimer le certificat** pour supprimer le certificat sélectionné.  
  
8.  Cliquez sur **OK** pour valider les modifications, puis fermez la boîte de dialogue.  
  
### <a name="to-configure-a-certificate-for-verifying-the-digital-signature-of-an-incoming-as2-messages"></a>Pour configurer un certificat pour vérifier la signature numérique de messages AS2 entrants  
  
1.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration, ouvrez le **groupe BizTalk** nœud, puis cliquez sur le **Parties** nœud.  
  
2.  Dans le **tiers et profils d’entreprise** volet, avec le bouton de la partie que vous allez recevoir des messages à partir de signés, puis cliquez sur **propriétés**.  
  
3.  Dans l’arborescence de la console, cliquez sur **certificat**.  
  
4.  Dans le **certificat** volet, cliquez sur **Parcourir**, recherchez le certificat que vous souhaitez utiliser pour vérifier la signature numérique, puis cliquez sur **OK**.  
  
    > [!NOTE]
    >  Au lieu d'entrer le nom commun du certificat, vous pouvez saisir simplement l'empreinte. Vous pouvez obtenir l’empreinte numérique en double-cliquant sur le certificat dans le magasin de certificats dans la console MMC ou du système de fichiers, en cliquant sur le **détails** onglet, en cliquant sur le **l’empreinte numérique** champ, puis copiez l’empreinte .  
  
5.  Cliquez sur **OK**.  
  
### <a name="to-configure-a-certificate-for-encrypting-an-outgoing-as2-messages"></a>Pour configurer un certificat pour le chiffrement de messages AS2 sortants  
  
1.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration, ouvrez le **groupe BizTalk** ouverture d’un nœud, le **Applications** nœud et ouvrez le nœud de la **application** qui contient le port d’envoi qui vous allez envoyer le message chiffré sur.  
  
2.  Ouvrez le **Ports d’envoi** nœud, cliquez sur le port d’envoi, puis cliquez sur **propriétés**.  
  
3.  Dans l’arborescence de la console, cliquez sur **certificat**.  
  
4.  Dans le **certificat** volet, cliquez sur **Parcourir**, recherchez le certificat que vous souhaitez utiliser pour le chiffrement, puis cliquez sur **OK**.  
  
    > [!NOTE]
    >  Au lieu d'entrer le nom commun du certificat, vous pouvez saisir simplement l'empreinte. Vous pouvez obtenir l’empreinte numérique en double-cliquant sur le certificat dans le magasin de certificats dans la console MMC ou du système de fichiers, en cliquant sur le **détails** onglet, en cliquant sur le **l’empreinte numérique** champ, puis copiez l’empreinte .  
  
5.  Cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité AS2](../core/as2-security.md)   
 [Configuration de la signature, la Compression et le chiffrement dans le Transport AS2](../core/configuring-signing-compression-and-encryption-in-as2-transport.md)   
 [AS2 Architecture de la Solution](../core/as2-solution-architecture.md)   
 [Installation des certificats pour les adaptateurs WCF](../core/installing-certificates-for-the-wcf-adapters.md)