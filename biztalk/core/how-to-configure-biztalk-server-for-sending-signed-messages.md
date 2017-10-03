---
title: "Comment configurer BizTalk Server pour l’envoi des Messages signés | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: be86fbb3-de80-4d9f-bcf0-c61347704229
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7ef71f5c11d6c1a000369644b822aa9f4d4ef792
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-biztalk-server-for-sending-signed-messages"></a>Configuration de BizTalk Server pour envoyer des messages signés
La procédure suivante présente les étapes à suivre afin de configurer [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour l'envoi de messages signés.  
  
-   Pour créer un pipeline afin d'envoyer des messages signés  
  
-   Configuration du port d'envoi pour l'envoi de messages signés  
  
## <a name="prerequisites"></a>Conditions préalables  
 Avant de configurer [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]s pour envoyer des messages signés, vous devez effectuer les étapes de [comment installer les certificats pour les Signatures numériques](../core/how-to-install-the-certificates-for-digital-signatures.md).  
  
### <a name="to-create-a-pipeline-to-send-signed-messages"></a>Pour créer un pipeline afin d'envoyer des messages signés  
  
1.  Dans l'Explorateur de solutions de Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], sélectionnez le projet dans lequel créer le pipeline.  
  
    1.  Sur le **fichier** menu, cliquez sur **ajouter un nouvel élément**.  
  
    2.  Dans le **ajouter un nouvel élément** boîte de dialogue, développez les éléments de projet BizTalk, cliquez sur **fichiers de Pipeline**, puis cliquez sur le **Pipeline d’envoi** modèle.  
  
    3.  Dans le **nom** , tapez un nom pour le pipeline.  
  
    4.  Cliquez sur **Ajouter**.  
  
         Le nouveau pipeline apparaît dans l'Explorateur de solutions.  
  
2.  Faites glisser le composant de pipeline Encodeur MIME/SMIME dans l'étape Encoder d'un pipeline de réception.  
  
     ![MIME &#47; Composant de pipeline encodeur SMIME](../core/media/bts-dev-mimesmimeencoder.gif "BTS_DEV_MIMESMIMEEncoder")  
  
3.  Dans la fenêtre Propriétés, configurez le composant de pipeline Encodeur MIME/SMIME **le type de Signature** propriété **ClearSign**ou **BlobSign**. Pour plus d’informations sur la **activer le chiffrement** propriété, consultez [comment configurer le composant de Pipeline encodeur MIME-SMIME](../core/how-to-configure-the-mime-smime-encoder-pipeline-component.md).  
  
    > [!IMPORTANT]
    >  Si vous utilisez également le chiffrement, vous pouvez uniquement sélectionner **BlobSign**.  
  
    > [!NOTE]
    >  Vous pouvez configurer les propriétés du composant du pipeline d'envoi à l'aide de la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] après le déploiement du pipeline dans un groupe BizTalk. Pour plus d’informations, consultez [comment configurer des propriétés de Pipeline par Instance pour un Port d’envoi](../core/how-to-configure-per-instance-pipeline-properties-for-a-send-port.md).  
  
    > [!NOTE]
    >  Le composant de pipeline Encodeur MIME/SMIME effectue à la fois le chiffrement et les opérations de signature numérique (lorsqu'il est configuré pour exécuter ces deux fonctions). Par conséquent, si vous configurez [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour envoyer des messages chiffrés et signés, vous pouvez utiliser le même pipeline d'envoi. En d'autres termes, il est inutile que vous créiez des pipelines distincts pour les opérations de chiffrement et de signature numérique.  
  
4.  Construisez et déployez le pipeline d'envoi.  
  
### <a name="to-configure-the-send-port-for-sending-signed-messages"></a>Configuration du port d'envoi pour l'envoi de messages signés  
  
1.  Ajoutez l'assembly BizTalk créé dans la procédure précédente à l'application BizTalk en incluant les emplacements de réception afin d'envoyer des messages signés. Pour plus d’informations sur l’ajout d’assemblys BizTalk, consultez [l’ajout d’un BizTalk Assembly à une Application](../core/how-to-add-a-biztalk-assembly-to-an-application.md).  
  
2.  Configurez le port d'envoi de l'application BizTalk avec le pipeline d'envoi créé dans la procédure précédente. Pour plus d’informations sur la configuration des ports d’envoi, consultez [création et configuration des Ports d’envoi](../core/creating-and-configuring-send-ports.md).  
  
3.  Configurer le groupe BizTalk avec le certificat de signature que vous avez installé dans [comment installer les certificats pour les Signatures numériques](../core/how-to-install-the-certificates-for-digital-signatures.md). Pour savoir comment configurer un groupe BizTalk, consultez [comment modifier les propriétés de groupe](../core/how-to-modify-group-properties.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Comment configurer BizTalk Server pour la réception des Messages signés](../core/how-to-configure-biztalk-server-for-receiving-signed-messages.md)   
 [Certificats utilisés par BizTalk Server pour les Messages signés](../core/certificates-that-biztalk-server-uses-for-signed-messages.md)   
 [Envoyer et recevoir des Messages signés](../core/sending-and-receiving-signed-messages.md)