---
title: "Comment configurer BizTalk Server pour l’envoi signés MIME ou Messages SMIME | Documents Microsoft"
ms.custom: 
ms.date: 06/29/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ba42463b-2c12-4329-919e-aca427d14eee
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 623e8e6349494ce1d15089093b1620b4da76adbb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-biztalk-server-to-send-signed-mime-or-smime-messages"></a>Comment configurer BizTalk Server pour envoyer signés MIME ou Messages SMIME
Cette rubrique explique comment configurer [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour utiliser des certificats pour envoyer des messages MIME/SMIME signés. La procédure ci-dessous s’applique également à la configuration de l’envoi de messages signés via le transport AS2.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter la procédure dans cette rubrique, vous devez être connecté en tant que membre de le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] groupe Administrateurs.  
  
### <a name="to-configure-biztalk-server-to-send-signed-messages"></a>Pour configurer BizTalk Server pour envoyer des messages signés  
  
1.  Créer un pipeline pour envoyer des messages signés, comme suit :  
  
    > [!NOTE]
    >  Cette étape n’est pas nécessaire lors de la configuration de transport AS2 pour envoyer des messages signés, car le AS2Send et AS2EdiSend de pipelines qui sont inclus dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] cette fonction.  
  
    1.  Créer un pipeline d’envoi et puis faites glisser le composant de pipeline Encodeur MIME/SMIME dans la phase de codage du pipeline.  
  
    2.  Dans le **propriétés** fenêtre, configurer la propriété type Signature de composant de pipeline Encodeur MIME/SMIME ClearSign ou BlobSign.  
  
        > [!NOTE]
        >  Si vous utilisez également le chiffrement, vous pouvez uniquement sélectionner BlobSign.  
  
        > [!NOTE]
        >  Vous pouvez configurer les propriétés du composant du pipeline d'envoi à l'aide de la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] après le déploiement du pipeline dans un groupe BizTalk.  
  
        > [!NOTE]
        >  Le composant de pipeline Encodeur MIME/SMIME effectue à la fois le chiffrement et les opérations de signature numérique (lorsqu'il est configuré pour exécuter ces deux fonctions). Par conséquent, si vous configurez [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour envoyer des messages chiffrés et signés, vous pouvez utiliser le même pipeline d'envoi. En d'autres termes, il est inutile que vous créiez des pipelines distincts pour les opérations de chiffrement et de signature numérique.  
  
    3.  Construisez et déployez le pipeline d'envoi.  
  
2.  Configurer le port d’envoi pour envoyer des messages signés, comme suit :  
  
    1.  Ajoutez l’assembly BizTalk que vous avez créé contenant le pipeline d’envoi à l’application BizTalk qui comprend les ports d’envoi pour envoyer des messages signés.  
  
        > [!NOTE]
        >  Cette étape n’est pas nécessaire lors de la configuration de transport AS2 pour envoyer des messages signés, car les pipelines AS2Send et AS2EdiSend sont inclus dans l’Application EDI BizTalk [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
    2.  Configurer le port d’envoi dans l’application BizTalk avec le pipeline d’envoi que vous avez créé dans la procédure précédente.  
  
3.  Configurez le groupe avec un certificat pour l’envoi de messages signés, comme suit :  
  
    1.  Configurer le groupe BizTalk avec le certificat de signature que vous avez installé en développant le groupe BizTalk dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, avec le bouton droit **groupe BizTalk**, puis en cliquant sur  **Propriétés**.  
  
    2.  Cliquez sur l’onglet certificat, cliquez sur **Parcourir**, sélectionnez le certificat approprié, puis cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration des certificats pour MIME ou Messages SMIME](../technical-guides/configuring-certificates-for-mime-or-smime-messages.md)