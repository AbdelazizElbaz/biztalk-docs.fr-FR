---
title: "Comment configurer BizTalk Server pour recevoir MIME chiffré ou Messages SMIME | Documents Microsoft"
ms.custom: 
ms.date: 06/29/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d72002c8-6bd8-458f-8149-1c0c4cbbb682
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bd9778d6fb37058cfb70d476590b5d32fe8936e1
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="how-to-configure-biztalk-server-to-receive-encrypted-mime-or-smime-messages"></a>Comment configurer BizTalk Server pour recevoir MIME chiffré ou Messages SMIME
Cette rubrique explique comment configurer [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour utiliser des certificats pour recevoir des messages MIME/SMIME chiffrés. La procédure ci-dessous s’applique également à la configuration de la réception de messages chiffrés via le transport AS2.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter la procédure dans cette rubrique, vous devez être connecté en tant que membre de le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] groupe Administrateurs.  
  
### <a name="to-configure-biztalk-server-to-receive-encrypted-messages"></a>Pour configurer BizTalk Server pour recevoir des messages chiffrés  
  
1.  Créer un pipeline afin de recevoir des messages chiffrés, comme suit :  
  
    > [!NOTE]
    >  Cette étape n’est pas nécessaire lors de la configuration de transport AS2 pour la réception des messages chiffrés, car les pipelines AS2Receive et AS2EdiReceive qui sont inclus dans BizTalk Server répondre à cette fonction.  
  
    > [!NOTE]
    >  Le composant de pipeline Décodeur MIME/SMIME effectue à la fois le déchiffrement et la validation des signatures numériques (lorsqu'il est configuré pour exécuter ces deux fonctions). Par conséquent, si vous configurez [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour recevoir des messages chiffrés et signés, vous pouvez utiliser le même pipeline de réception. En d'autres termes, il est inutile de créer des pipelines distincts pour le chiffrement et la validation des signatures numériques.  
  
    1.  Créer un pipeline de réception et puis faites glisser le composant de pipeline Décodeur MIME/SMIME dans l’étape décoder du pipeline.  
  
    2.  Dans le **propriétés** fenêtre, configurer les propriétés de composant de pipeline Décodeur MIME/SMIME.  
  
        > [!NOTE]
        >  Configurer les propriétés de composant de pipeline Décodeur MIME/SMIME inclut la définition de la propriété vérifier la liste de révocation à True si vous souhaitez vérifier la liste de révocation de certificats pour les certificats utilisés par les expéditeurs pour signer les messages sont envoyés à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. La désactivation de cette option augmente les performances du composant. La liste de révocation de certificat associée à un certificat est téléchargée à partir du site de services de certificat approprié. Si le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ne peut pas se connecter au site Web à distance, le message échoue dans le pipeline.  
  
        > [!NOTE]
        >  Vous pouvez configurer les propriétés de pipeline d'un emplacement de réception à l'aide de la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] après le déploiement du pipeline dans un groupe BizTalk. Vous pouvez configurer des propriétés de pipeline différentes pour chaque emplacement de réception du groupe BizTalk.  
  
    3.  Construisez et déployez le pipeline de réception.  
  
2.  Configurer l’emplacement de réception pour la réception des messages chiffrés, comme suit :  
  
    1.  Ajoutez l’assembly BizTalk que vous avez créé contenant le pipeline de réception à l’application BizTalk en incluant les emplacements de réception pour recevoir des messages chiffrés.  
  
        > [!NOTE]
        >  Cette étape n’est pas nécessaire lors de la configuration de transport AS2 pour la réception des messages chiffrés, car les pipelines AS2Receive et AS2EdiReceive sont inclus dans l’Application EDI BizTalk [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
    2.  Configurer les emplacements de réception dans l’application BizTalk avec le pipeline de réception que vous avez créé à l’étape précédente.  
  
3.  Configurer l’hôte utilisé en tant que le Gestionnaire de réception pour l’emplacement de réception avec le certificat de déchiffrement, comme suit :  
  
    1.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration, avec le bouton BizTalk hôte qui est le Gestionnaire de réception des messages chiffrés, puis cliquez sur **propriétés**.  
  
        > [!NOTE]
        >  Cette procédure ne s’applique pas pour le transport AS2 disponible avec [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Elle s’applique pour le décodeur MIME BizTalk, pas le décodeur AS2. Le décodeur AS2 détermine le certificat basé sur les informations de certificat dans le message.  
  
    2.  Dans le **propriétés de l’hôte** boîte de dialogue, cliquez sur **certificat**, puis cliquez sur **Parcourir**.  
  
        > [!NOTE]
        >  La procédure ci-dessus vous permet de configurer votre [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnement afin que seuls certains hôtes peuvent recevoir et traiter des messages donnés. Lorsque vous configurez un ordinateur hôte avec l’empreinte numérique du certificat à utiliser pour le décodage du message et le déchiffrement, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] crée une propriété d’application pour l’hôte dans la base de données MessageBox. Sécuriser les messages sont reçus et déchiffrés avec cette empreinte sont ensuite acheminés uniquement à ces informations et autres ordinateurs hôtes qui sont configurés avec cette empreinte numérique.  
  
    3.  Dans le **sélectionner un certificat** boîte de dialogue, sélectionnez le certificat de déchiffrement que vous avez installé, puis fermez les boîtes de dialogue.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration des certificats pour MIME ou Messages SMIME](../technical-guides/configuring-certificates-for-mime-or-smime-messages.md)