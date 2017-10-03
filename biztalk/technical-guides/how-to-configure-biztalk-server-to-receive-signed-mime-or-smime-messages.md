---
title: "Comment configurer BizTalk Server pour recevoir signés MIME ou Messages SMIME | Documents Microsoft"
ms.custom: 
ms.date: 06/29/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 50570257-7bb6-4ede-9026-873eefd06483
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 88487fb96c89b8a611ab591223fa1820f70de1cd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-biztalk-server-to-receive-signed-mime-or-smime-messages"></a>Comment configurer BizTalk Server pour recevoir signés MIME ou Messages SMIME
Cette rubrique explique comment configurer [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour utiliser des certificats pour recevoir les messages MIME/SMIME signés. La procédure ci-dessous s’applique également à la configuration de la réception de messages signés via le transport AS2.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter la procédure dans cette rubrique, vous devez être connecté en tant que membre de le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] groupe Administrateurs.  
  
### <a name="to-configure-biztalk-server-to-receive-signed-messages"></a>Pour configurer BizTalk Server pour recevoir des messages signés  
  
1.  Créer un pipeline afin de recevoir des messages signés, comme suit :  
  
    > [!NOTE]
    >  Cette étape n’est pas nécessaire lors de la configuration de transport AS2 pour la réception des messages signés, car le AS2Receive et AS2EdiReceive de pipelines qui sont inclus dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] cette fonction.  
  
    1.  Créer un pipeline de réception et puis faites glisser le composant de pipeline Décodeur MIME/SMIME dans l’étape décoder du pipeline de réception.  
  
    2.  Dans le **propriétés** fenêtre, configurer les propriétés de composant de pipeline Décodeur MIME/SMIME.  
  
        > [!NOTE]
        >  Vous pouvez configurer les propriétés de pipeline d'un emplacement de réception à l'aide de la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] après le déploiement du pipeline dans un groupe BizTalk. Vous pouvez configurer des propriétés de pipeline différentes pour chaque emplacement de réception du groupe BizTalk.  
  
    3.  Construisez et déployez le pipeline de réception.  
  
2.  Configurer un emplacement de réception pour la réception des messages signés, comme suit :  
  
    1.  Ajoutez l’assembly BizTalk que vous avez créé contenant le pipeline de réception à l’application BizTalk en incluant les emplacements de réception pour recevoir des messages signés.  
  
        > [!NOTE]
        >  Cette étape n’est pas nécessaire lors de la configuration de transport AS2 pour la réception des messages signés, car les pipelines AS2Receive et AS2EdiReceive sont inclus dans l’Application EDI BizTalk [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
    2.  Configurer les emplacements de réception dans l’application BizTalk avec le pipeline de réception que vous avez créé dans la procédure précédente.  
  
3.  Configurer le tiers avec un certificat pour la réception des messages signés, comme suit :  
  
    -   Ouvrez le **propriétés de tiers** boîte de dialogue dans la Console Administration de BizTalk Server, cliquez sur le **certificat** , cliquez sur **Parcourir**, sélectionnez le certificat approprié, puis cliquez sur **OK**.  
  
        > [!NOTE]
        >  Le certificat utilisé pour vérifier une signature pour un tiers doit se différencier des certificats utilisés pour vérifier les signatures pour d'autres tiers.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration des certificats pour MIME ou Messages SMIME](../technical-guides/configuring-certificates-for-mime-or-smime-messages.md)