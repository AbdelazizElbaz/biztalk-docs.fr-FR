---
title: "À l’aide de l’Assistant Configuration de l’application MQSAgent COM + | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.mqsagent.wizard
helpviewer_keywords:
- MQSeries adapters, MQSAgent COM+ Configuration Wizard
- configuring [MQSeries adapters], MQSAgent COM+ Configuration Wizard
- MQSAgent COM+ Configuration Wizard
ms.assetid: f106700a-7f57-4c83-9344-6525fc10544d
caps.latest.revision: "23"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0f6e8b625bcc3accbefda193c52459616691c265
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="using-the-mqsagent-com-configuration-wizard"></a>À l’aide de l’Assistant Configuration de l’application MQSAgent COM +
L'Assistant Configuration de l'application MQSAgent COM+ configure MQSAgent, la partie de l'adaptateur de l'application COM+ (composant MQSeries). L'assistant définit l'identité de l'application du composant, ainsi que le nom de rôle et les utilisateurs qui font partie de ce rôle. Le nom du composant MQSAgent COM + créé avec l’Assistant de Configuration de MQSAgent COM + est **MQSAgent2**.  
  
> [!NOTE]
>  L’application MQSAgent COM+ est prise en charge sur une version 64 bits de Windows Server. Elle est exécutée en tant que processus 32 bits sous WOW64. Un ordinateur sur lequel [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est installé et qui exécute une version 64 bits de Windows Server peut communiquer avec un ordinateur distant 32 bits sur lequel MQSAgent est installé.  
  
> [!NOTE]
>  MQSeries Agent et l’exécutable de l’Assistant Configuration MQSAgent COM + **MQSConfigWiz.exe** ne sont pas installés si vous mettez à niveau à partir de BizTalk Server 2009 à BizTalk Server. Après la mise à niveau vers BizTalk Server à partir de BizTalk Server 2009 et réexécutez le programme d’installation, sélectionnez le **modifier** option et sélectionnez MQSeries Agent sous logiciels supplémentaires pour installer ces composants.  
  
## <a name="to-set-the-application-identity"></a>Pour définir l'identité de l'application  
  
-   Utilisez le **identité de l’Application** page de l’application MQSAgent COM + Assistant Configuration pour définir l’identité de l’application pour MQSAgent comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Utilisateur interactif**|Sélectionner cette option pour utiliser le compte de connexion actuel comme identité de l'application.|  
    |**Service local**|Définissez l'identité de l'application sur un compte du service intégré.|  
    |**Service réseau**|Définissez l'identité de l'application sur un compte intégré avec accès réseau.|  
    |**Cet utilisateur**|Définissez l'identité de l'application sur le nom d'utilisateur indiqué.|  
  
> [!NOTE]
>  Il n'est pas recommandé d'utiliser un compte avec autorisations administratives pour l'identité de l'application. Le compte doit bénéficier des privilèges minimaux requis : autorisation en lecture/écriture pour les files d'attente MQSeries.  
  
## <a name="to-name-the-role-and-add-users-to-it"></a>Pour définir le nom du rôle et y ajouter des utilisateurs  
  
-   Utilisez le **nom du rôle** page de l’application MQSAgent COM + Assistant Configuration pour affecter un nom et les utilisateurs au rôle comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Nom du rôle**|Permet de saisir le nom du rôle.|  
    |**Utilisateurs**|Affiche les utilisateurs qui appartiennent à ce rôle|  
    |**Ajouter**|Ajouter des utilisateurs au rôle Il s'agit des comptes de service [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] qui utilisent l'adaptateur.|  
  
> [!NOTE]
>  Ajoutez au rôle uniquement les comptes qui nécessitent un accès à l'adaptateur.  
  
## <a name="to-set-the-msdtc-security-configuration-on-the-windows-server-2008-computer-to-no-authentication-required"></a>Définition de la configuration de la sécurité MSDTC de l'ordinateur Windows Server 2008 sur Aucune authentification requise  
 Si l’application MQSAgent COM + est installée sur un [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] ordinateur et l’adaptateur MQSeries (qui est installé avec BizTalk Server) est installé sur un [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] ou [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] ordinateur, la configuration de sécurité MSDTC sur le [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] ou [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] ordinateur doit être définie sur **aucune authentification requise**. Pour définir la configuration de la sécurité MSDTC sur Aucune authentification requise, procédez comme suit :  
  
1.  Cliquez sur **Démarrer** puis cliquez sur **le panneau de configuration**.  
  
2.  Double-cliquez sur **outils d’administration**.  
  
3.  Double-cliquez sur **Services de composants** pour lancer le **Services de composants** interface de gestion.  
  
4.  Développez **Services de composants**, développez **ordinateurs**, puis développez **poste**.  
  
5.  Avec le bouton droit **poste** et cliquez sur le **propriétés** élément de menu.  
  
6.  Dans le **poste** boîte de dialogue, cliquez sur le **MSDTC** onglet, puis cliquez sur **Configuration de la sécurité**.  
  
7.  Dans le **Configuration de la sécurité** boîte de dialogue le **Communication du Gestionnaire de transactions** section, sélectionnez **aucune authentification requise**. Si vous êtes invité à une boîte de dialogue, cliquez sur **Oui** pour redémarrer le Service MS DTC.  
  
8.  Une fois le service MS DTC a redémarré, cliquez sur **OK** et cliquez sur **OK** à nouveau pour fermer la **poste** boîte de dialogue.  
  
9. Fermer le **Services de composants** interface de gestion.  
  
## <a name="to-configure-the-mqsagent-runtime-components-to-run-under-an-alternative-set-of-credentials"></a>Pour configurer les composants d'exécution MQSAgent pour qu'ils s'exécutent avec différentes informations d'identification  
 L'application MQSAgent COM+ comprend des composants d'administration et d'exécution. Si vous souhaitez diviser cette fonctionnalité en plusieurs applications COM+ pour des raisons de sécurité, procédez comme suit sur l'ordinateur sur lequel l'application MQSAgent COM+ est installée :  
  
1.  Activez les modifications pour le composant MQSAgent COM+.  
  
    -   Cliquez sur **Démarrer** puis cliquez sur **le panneau de configuration**.  
  
    -   Double-cliquez sur **outils d’administration**.  
  
    -   Double-cliquez sur **Services de composants** pour lancer le **Services de composants** interface de gestion.  
  
    -   Développez **Services de composants**, développez **poste**, développez **Applications COM +**, avec le bouton droit le **MQSAgent2** l’application COM + puis cliquez sur **propriétés**.  
  
    -   Cliquez sur le **avancé** onglet et décochez la case **désactiver les modifications**.  
  
    -   Cliquez sur **OK**.  
  
2.  Créez une nouvelle application COM+ pour les composants d'exécution MQSAgent.  
  
    -   Avec le bouton droit **Applications COM +**, cliquez sur **nouveau**, **Application** pour afficher les **Assistant Installation d’applications COM +** et cliquez sur  **Suivant**.  
  
    -   Cliquez sur **créer une application vide**.  
  
    -   Entrez le nom **MQSAgent2RunTime**, laissez l’option par défaut **application serveur** activé, puis cliquez **suivant**.  
  
    -   Sélectionnez l’option de **cet utilisateur**, entrez les informations de compte approprié, puis cliquez sur **suivant**.  
  
        > [!NOTE]
        >  Ce compte doit avoir **connecter** et **put** et/ou **obtenir** autorisations sur IBM WebSphere MQ appropriées pour les files d’attente de Windows. Vous pouvez définir les autorisations appropriées pour ce compte avec le **setmqaut** commande disponible avec IBM WebSphere MQ. Pour plus d’informations sur la **setmqaut** commande consultez la documentation IBM WebSphere MQ.  
  
    -   Cliquez sur **suivant** sur la **ajouter des rôles d’Application** boîte de dialogue.  
  
    -   Cliquez sur **suivant** sur la **ajouter des utilisateurs aux rôles** boîte de dialogue.  
  
    -   Cliquez sur **Terminer**.  
  
3.  Déplacez les composants d'exécution vers la nouvelle application COM+  
  
    -   Développez le **MQSAgent2** l’application COM +.  
  
    -   Développez **composants**.  
  
    -   Avec le bouton droit le **MQSAgent2.MQSAgent.1** composant et cliquez sur **déplacer** pour afficher les **déplacer les composants (s)** boîte de dialogue.  
  
    -   Sélectionnez **MQSAgent2RunTime** sous **Veuillez sélectionner une destination** et cliquez sur **OK**.  
  
    -   Répétez ces étapes pour le **MQSAgent2.MQSBroker.1** et **MQSAgent2.MQSProxy.1** composants.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment configurer l’adaptateur MQSeries envoyer et recevoir des gestionnaires](../core/how-to-configure-mqseries-adapter-send-and-receive-handlers.md)   
 [Configuration de l’adaptateur MQSeries](../core/configuring-the-mqseries-adapter.md)