---
title: "Comment configurer BizTalk Server pour l’envoi chiffré des Messages MIME/SMIME | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 14f67152-5f80-4040-a9d6-0819fab7fcb5
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c83b5f28ac3716376aa93cff22f933363825615e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-biztalk-server-to-send-encrypted-mimesmime-messages"></a>Comment configurer BizTalk Server pour envoyer des Messages MIME/SMIME chiffrée
Cette rubrique décrit comment configurer BizTalk Server pour utiliser des certificats pour envoyer des messages MIME/SMIME chiffrés. La procédure ci-dessous s’applique également à la configuration de l’envoi de messages chiffrés via le transport AS2.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté en tant que membre du groupe des administrateurs de BizTalk Server.  
  
### <a name="to-configure-biztalk-server-to-send-encrypted-messages"></a>Pour configurer BizTalk Server pour envoyer des messages chiffrés  
  
1.  Créer un pipeline pour envoyer des messages chiffrés, comme suit :  
  
    > [!NOTE]  
    >  Cette étape n’est pas nécessaire lors de la configuration de transport AS2 pour envoyer des messages chiffrés, car le AS2Send et AS2EdiSend de pipelines qui sont inclus dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] cette fonction.  
  
    1.  Créer un pipeline d’envoi et puis faites glisser le composant de pipeline Encodeur MIME/SMIME dans la phase de codage du pipeline.  
  
    2.  Dans le **propriétés** fenêtre, configurez la propriété chiffrement activer de composant de pipeline Encodeur MIME/SMIME pour **True**.  
  
        > [!NOTE]  
        >  Vous pouvez configurer les propriétés du composant du pipeline d'envoi à l'aide de la console Administration de BizTalk Server après le déploiement du pipeline dans un groupe BizTalk.  
  
    3.  Construisez et déployez le pipeline d'envoi.  
  
2.  Configurer le port d’envoi pour envoyer des messages chiffrés, comme suit :  
  
    1.  Ajoutez l’assembly BizTalk que vous avez créé contenant le pipeline d’envoi à l’application BizTalk en incluant les emplacements de réception pour recevoir des messages chiffrés.  
  
        > [!NOTE]  
        >  Cette étape n’est pas nécessaire lors de la configuration de transport AS2 pour envoyer des messages chiffrés, car les pipelines AS2Send et AS2EdiSend sont inclus dans l’Application EDI BizTalk.  
  
    2.  Configurer le port d’envoi dans l’Application BizTalk avec le pipeline d’envoi que vous avez créé dans la procédure précédente.  
  
    3.  Affectez le certificat de chiffrement que vous avez installé en double-cliquant sur le port d’envoi, en cliquant sur **propriétés**, puis en cliquant sur **certificat**. Cliquez sur **Parcourir**, accédez au certificat que vous souhaitez attribuer à ce port d’envoi, puis cliquez sur **OK**.  
  
        > [!NOTE]  
        >  Si le certificat n’existe pas sur l’ordinateur local, dans le **l’empreinte numérique** zone, tapez ou collez l’empreinte numérique du certificat, puis cliquez sur **OK**. Le format de l'empreinte du certificat est HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH, où H est un nombre hexadécimal.