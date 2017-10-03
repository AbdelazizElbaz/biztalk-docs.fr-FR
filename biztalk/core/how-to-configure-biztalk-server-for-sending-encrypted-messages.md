---
title: "Comment configurer BizTalk Server pour l’envoi des Messages chiffrés | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fb751d7c-49cd-46f0-9630-254cf06c497e
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a0b3ef721c263c892690b9ac5b7d2dd15155f0dc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-biztalk-server-for-sending-encrypted-messages"></a>Configuration de BizTalk Server pour envoyer des messages chiffrés
La procédure suivante présente les étapes à suivre pour configurer [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour l'envoi de messages chiffrés.  
  
-   Pour créer un pipeline afin d'envoyer des messages chiffrés  
  
-   Pour configurer le port d'envoi pour l'envoi de messages chiffrés  
  
## <a name="prerequisites"></a>Conditions préalables  
 Avant de configurer [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]s pour l’envoi de messages chiffrés, vous devez effectuer les étapes de [comment installer les certificats pour les Messages chiffrés](../core/how-to-install-the-certificates-for-encrypted-messages.md).  
  
### <a name="to-create-a-pipeline-to-send-encrypted-messages"></a>Pour créer un pipeline afin d'envoyer des messages chiffrés  
  
1.  Dans l'Explorateur de solutions de Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], sélectionnez le projet dans lequel créer le pipeline.  
  
    1.  Sur le **fichier** menu, cliquez sur **ajouter un nouvel élément**.  
  
    2.  Dans le **ajouter un nouvel élément** boîte de dialogue, développez les éléments de projet BizTalk, cliquez sur **fichiers de Pipeline**, puis cliquez sur le **Pipeline d’envoi** modèle.  
  
    3.  Dans le **nom** , tapez un nom pour le pipeline.  
  
    4.  Cliquez sur **Ajouter**.  
  
         Le nouveau pipeline apparaît dans l'Explorateur de solutions.  
  
2.  Faites glisser le composant de pipeline Encodeur MIME/SMIME dans l'étape Encoder d'un pipeline de réception.  
  
     ![MIME &#47; Composant de pipeline encodeur SMIME](../core/media/bts-dev-mimesmimeencoder.gif "BTS_DEV_MIMESMIMEEncoder")  
  
    -   Dans la fenêtre Propriétés, configurez le composant de pipeline Encodeur MIME/SMIME **activer le chiffrement** propriété `True`. Pour plus d’informations sur la **activer le chiffrement** propriété, consultez [comment configurer le composant de Pipeline encodeur MIME-SMIME](../core/how-to-configure-the-mime-smime-encoder-pipeline-component.md).  
  
    > [!NOTE]
    >  Vous pouvez configurer les propriétés du composant du pipeline d'envoi à l'aide de la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] après le déploiement du pipeline dans un groupe BizTalk. Pour plus d’informations, consultez [comment configurer des propriétés de Pipeline par Instance pour un Port d’envoi](../core/how-to-configure-per-instance-pipeline-properties-for-a-send-port.md).  
  
    > [!NOTE]
    >  Le composant de pipeline Encodeur MIME/SMIME effectue à la fois le chiffrement et les opérations de signature numérique (lorsqu'il est configuré pour exécuter ces deux fonctions). Par conséquent, si vous configurez [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour envoyer des messages chiffrés et signés, vous pouvez utiliser le même pipeline d'envoi. En d'autres termes, il est inutile que vous créiez des pipelines distincts pour les opérations de chiffrement et de signature numérique.  
  
3.  Construisez et déployez le pipeline d'envoi.  
  
### <a name="to-configure-the-send-port-for-sending-encrypted-messages"></a>Pour configurer le port d'envoi pour l'envoi de messages chiffrés  
  
1.  Ajoutez l'assembly BizTalk créé dans la procédure précédente à l'application BizTalk en incluant les ports d’envoi pour envoyer des messages chiffrés. Pour plus d’informations sur l’ajout d’assemblys BizTalk, consultez [l’ajout d’un BizTalk Assembly à une Application](../core/how-to-add-a-biztalk-assembly-to-an-application.md).  
  
2.  Configurez le port d’envoi dans l’Application BizTalk avec le pipeline d’envoi que vous avez créé dans la procédure précédente, puis attribuez le certificat de chiffrement que vous avez installé dans [comment installer les certificats pour les Messages chiffrés](../core/how-to-install-the-certificates-for-encrypted-messages.md). Pour plus d’informations sur la configuration des ports d’envoi, consultez [comment attribuer un certificat à un Port d’envoi](../core/how-to-assign-a-certificate-to-a-send-port.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Comment configurer BizTalk Server pour recevoir des Messages chiffrés](../core/how-to-configure-biztalk-server-for-receiving-encrypted-messages.md)   
 [Certificats utilisés par BizTalk Server pour les Messages chiffrés](../core/certificates-that-biztalk-server-uses-for-encrypted-messages.md)   
 [Envoyer et recevoir des Messages chiffrés](../core/sending-and-receiving-encrypted-messages.md)