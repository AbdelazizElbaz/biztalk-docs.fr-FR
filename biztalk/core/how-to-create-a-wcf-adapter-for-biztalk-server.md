---
title: "Comment créer un adaptateur WCF pour BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7ddaeb72-d263-4291-bd79-485fc736e6e7
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ebe1bbb9282db88f1b4370cea4b59ff4fcbfe6a0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-a-wcf-adapter-for-biztalk-server"></a>Comment créer un adaptateur WCF pour BizTalk Server
La création d'un adaptateur [!INCLUDE[firstref_btsWinCommFoundation](../includes/firstref-btswincommfoundation-md.md)] BizTalk s'effectue en trois étapes.  
  
-   Créez un service Web [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] à l'aide de l'Assistant Publication de services [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] BizTalk. Pour plus d’informations sur l’utilisation de BizTalk [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] Assistant Publication de services, consultez [publication des Services WCF](../core/publishing-wcf-services.md).  
  
-   Configurez des emplacements et ports de réception et d'envoi [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] à l'aide de la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Pour obtenir un exemple de procédure à suivre, consultez [comment configurer recevoir et envoyer des emplacements et Ports pour l’Interception de BAM WCF](../core/how-to-configure-receive-and-send-locations-and-ports-for-bam-wcf-interception.md).  
  
-   Si vous hébergez votre solution dans IIS, vous devez configurer le service Web [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] à l'aide du Gestionnaire des services Internet.  
  
    -   Vous devez accorder des autorisations à l'utilisateur du pool d'applications. Pour ce faire, consultez [considérations de sécurité pour l’emprunt d’identité IIS](../core/security-considerations-for-iis-impersonation.md).  
  
    -   Vous devez définir la sécurité de répertoire pour votre application, comme décrit dans la procédure suivante.  
  
## <a name="setting-the-directory-security"></a>Configuration de la sécurité de répertoire  
 Vérifiez que le contrôle d'accès à la sécurité de répertoire pour le service [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] autorise l'accès anonyme. Ceci simplifie l'accès à l'application.  
  
 Par exemple, si votre application est nommée MyBizTalkService3 et que le site Web MyBizTalkService3 fait partie des sites Web par défaut, suivez cette procédure pour définir le contrôle d'accès.  
  
#### <a name="to-set-the-access-control-in-windows-server-2008"></a>Pour définir le contrôle d'accès dans Windows Server 2008  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, développez **outils d’administration**, puis cliquez sur **Gestionnaire des Services Internet (IIS)**.  
  
2.  Dans la fenêtre Gestionnaire des Services Internet (IIS), développez le nom de votre serveur, **Sites**, développez **Internet Information Services**, puis développez **Site Web par défaut**.  
  
3.  Avec le bouton droit **MyBizTalkService3**, puis cliquez sur **modifier les autorisations**.  
  
4.  Sur le **sécurité** onglet de la **propriétés de MyBizTalkService3** boîte de dialogue, cliquez sur **modifier**.  
  
5.  Dans le **autorisations de MyBizTalkService3** boîte de dialogue, cliquez sur **ajouter**.  
  
6.  Dans le **sélectionnez utilisateurs, ordinateurs ou groupes** boîte de dialogue, tapez `anonymous logon` puis cliquez sur **OK**.  
  
7.  Sélectionnez **ouverture de session anonyme** dans le **noms d’utilisateur ou groupe** section, sélectionnez **en lecture & exécution** dans le **autorisations d’ouverture de session anonyme** section, puis cliquez sur **OK**.  
  
8.  Cliquez sur **OK** pour fermer la **propriétés de MyBizTalkService3** boîte de dialogue.  
  
 Pour confirmer que le service est correctement configuré, cliquez sur le service, puis cliquez sur **Parcourir**.  
  
 Si le service est correctement configuré, une page semblable à la suivante est affichée.  
  
 ![Écran du Service BizTalkServiceInstance](../core/media/ff0e4ba0-59e7-47d9-a252-2859179f5645.gif "ff0e4ba0-59e7-47d9-a252-2859179f5645")  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration de l’adaptateur WCF pour intercepter les données BAM](../core/configuring-the-wcf-adapter-to-intercept-bam-data.md)