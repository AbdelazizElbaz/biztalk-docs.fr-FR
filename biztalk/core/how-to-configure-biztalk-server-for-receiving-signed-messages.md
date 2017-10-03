---
title: "Comment configurer BizTalk Server pour la réception des Messages signés | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 48479532-24a9-41d9-a3b8-2a23f4e76457
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 814aa3f25866f18a1d7fe536bc47a996f286916d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-biztalk-server-for-receiving-signed-messages"></a>Configuration de BizTalk Server pour recevoir des messages signés
La procédure suivante présente les étapes à suivre pour configurer [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour la réception de messages chiffrés.  
  
-   Pour créer un pipeline afin de recevoir les messages signés  
  
-   Pour configurer l'emplacement de réception des messages signés  
  
## <a name="prerequisites"></a>Conditions préalables  
 Avant de configurer [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]s pour la réception des messages signés, vous devez effectuer les étapes de [comment installer les certificats pour les Signatures numériques](../core/how-to-install-the-certificates-for-digital-signatures.md).  
  
### <a name="to-create-a-pipeline-to-receive-signed-messages"></a>Pour créer un pipeline afin de recevoir les messages signés  
  
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
  
3.  Construisez et déployez le pipeline de réception.  
  
### <a name="to-configure-the-receive-location-for-receiving-signed-messages"></a>Pour configurer l'emplacement de réception des messages signés  
  
1.  Ajoutez l'assembly BizTalk créé dans la procédure précédente à l'application BizTalk en incluant les emplacements de réception afin de recevoir des messages signés. Pour plus d’informations sur l’ajout d’assemblys BizTalk, consultez [l’ajout d’un BizTalk Assembly à une Application](../core/how-to-add-a-biztalk-assembly-to-an-application.md).  
  
2.  Configurez les emplacements de réception de l'application BizTalk avec le pipeline de réception créé dans la procédure précédente. Pour plus d’informations sur la façon de configurer les emplacements de réception, consultez [comment modifier les propriétés d’un emplacement de réception](../core/how-to-edit-the-properties-of-a-receive-location.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Certificats utilisés par BizTalk Server pour les Messages signés](../core/certificates-that-biztalk-server-uses-for-signed-messages.md)   
 [Comment configurer BizTalk Server pour envoyer des Messages signés](../core/how-to-configure-biztalk-server-for-sending-signed-messages.md)   
 [Authentification de l’expéditeur d’un Message](../core/authenticating-the-sender-of-a-message.md)   
 [Envoyer et recevoir des Messages signés](../core/sending-and-receiving-signed-messages.md)