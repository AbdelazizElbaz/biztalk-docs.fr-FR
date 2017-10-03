---
title: "Comment attribuer un certificat à un Port d’envoi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- certificates, assigning
- managing [send ports], certificates
- assigning certificates
- certificates, send ports
ms.assetid: ba9e9c8b-f5b6-4fee-9e89-31b0f1df6ed4
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ec19c845c6b0cfb5d19bd7a961fe9ddfbcf2a3d7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-assign-a-certificate-to-a-send-port"></a>Attribution d'un certificat à un port d'envoi
Cette rubrique décrit comment attribuer un certificat de sécurité à un port d'envoi à l'aide de la console Administration de BizTalk Server. Le certificat doit figurer dans le magasin de certificats Autres personnes sur l'ordinateur exécutant BizTalk Server, faute de quoi les messages associés à ce port d'envoi ne seront pas traités et des erreurs seront consignées.  
  
> [!NOTE]
>  Le développeur peut attribuer un certificat de sécurité à un port d'envoi au cours du processus de développement à l'aide de la procédure décrite dans cette rubrique.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe d'administrateurs BizTalk Server. Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### <a name="to-assign-a-certificate-to-a-send-port"></a>Pour attribuer un certificat à un port d'envoi  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l'arborescence de la console, développez le groupe BizTalk, puis l'application BizTalk dont dépend le port d'envoi auquel attribuer un certificat.  
  
3.  Développez **Ports d’envoi**, cliquez sur le port d’envoi, cliquez sur **propriétés**, puis cliquez sur **certificat**.  
  
4.  Si le certificat existe sur l’ordinateur local, cliquez sur **Parcourir**, accédez au certificat que vous souhaitez attribuer à ce port d’envoi, puis cliquez sur **OK**. Sinon, ignorez cette étape.  
  
    > [!NOTE]
    >  Même si le certificat existe sur l'ordinateur local, il doit également figurer sur l'ordinateur exécutant BizTalk Server (au cas où cet ordinateur serait différent du premier), avant que le port d'envoi puisse traiter les messages.  
  
5.  Si le certificat n’existe pas sur l’ordinateur local, dans le **l’empreinte numérique** zone, tapez ou collez l’empreinte numérique du certificat, puis cliquez sur **OK**. Le format de l'empreinte du certificat est HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH, où H est un nombre hexadécimal.  
  
## <a name="see-also"></a>Voir aussi  
 [Création et configuration des Ports d’envoi](../core/creating-and-configuring-send-ports.md)