---
title: "Comment configurer IIS pour l’emplacement de réception HTTP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- 64-bit support, HTTP adapters
- HTTP adapters, IIS
- configuring [HTTP adapters], IIS
- receive locations, IIS
- IIS, receive locations
- HTTP adapters, 64-bit support
- IIS, HTTP adapters
ms.assetid: 1c420f46-01f1-4c9c-9144-d8d2acc8b0c4
caps.latest.revision: "26"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a1daa535c546bef0b390f0f7f84c45d546ac0005
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-iis-for-an-http-receive-location"></a>Comment configurer IIS pour l’emplacement de réception HTTP
Selon la version de Microsoft Windows que vous utilisez, vous devrez adapter la configuration des services IIS (Microsoft Internet Information Services) pour travailler avec l'emplacement de réception de l'adaptateur HTTP.  
  
 Si votre système d'exploitation est [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] ou [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)], IIS 7.0 offre deux modes d'isolation des applications distincts pour protéger les applications Web, dont le mode d'isolation du processus de travail (par défaut). Vous pouvez configurer l'emplacement de réception de l'adaptateur HTTP de manière à fonctionner avec les deux modes. Cependant, il est recommandé d'utiliser le mode d'isolation des processus de travail en raison de sa fonctionnalité de sécurité renforcée.  
  
> [!NOTE]
>  Si votre système d’exploitation est le x64 édition de [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] ou [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)], la version 64 bits du HTTP recevoir adaptateur est installé dans le  *\<lecteur >***\Program Files (x86) \Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **\HttpReceive64** répertoire de votre [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] par défaut. Pour la faire fonctionner dans un mode 64 bits natif, vous devez exécuter le script suivant à partir d'une ligne de commande :  
>   
>  `cscript %SystemDrive%\inetpub\AdminScripts\adsutil.vbs set w3svc/AppPools/Enable32bitAppOnWin64 0`  
>   
>  `C:\WINDOWS\Microsoft.NET\Framework64\vX.X.XXXXX>aspnet_regiis.exe -i`  
  
> [!NOTE]
>  Toute configuration IIS menant au partage du même processus par SOAP et HTTP est non valide. Vous ne pouvez utiliser qu'un seul récepteur isolé par processus.  
  
### <a name="to-configure-the-iis-70-worker-process-isolation-mode-to-work-with-the-http-adapter-receive-location"></a>Pour configurer le mode d’isolation de processus de travail de IIS 7.0 pour travailler avec l’adaptateur HTTP emplacement de réception  
  
1.  Cliquez sur **Démarrer**, pointez sur **paramètres**, puis cliquez sur **le panneau de configuration**.  
  
2.  Dans le panneau de configuration, double-cliquez sur **outils d’administration**.  
  
3.  Dans Outils d’administration, double-cliquez sur **Internet Information Services**.  
  
4.  Dans les services IIS, sélectionnez l'entrée du serveur Web racine. Dans le **affichage des fonctionnalités**, double-cliquez sur **mappages de gestionnaires**, puis dans le volet Actions, cliquez sur **ajouter un mappage de scripts**.  
  
    > [!NOTE]
    >  La configuration du mappage de scripts au niveau du serveur Web entraîne l'application de ce mappage à tous les sites Web enfants. Si vous souhaitez limiter le mappage à un site Web ou à un dossier virtuel spécifique, sélectionnez le site ou le dossier au lieu du serveur Web.  
  
5.  Dans le **ajouter un mappage de scripts** boîte de dialogue le **chemin d’accès de la demande** , tapez `BtsHttpReceive.dll`.  
  
6.  Dans le **exécutable** , cliquez sur le bouton de sélection (**...** ) bouton et accédez à [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]HttpReceive. Sélectionnez **BtsHttpReceive.dll** puis cliquez sur **OK**.  
  
7.  Dans le **nom** , tapez `BizTalk HTTP Receive`, puis cliquez sur **Restrictions des demandes**.  
  
8.  Dans le **Restrictions des demandes** boîte de dialogue, cliquez sur le **verbes** onglet, puis sélectionnez **un des verbes suivants**. Entrez `POST` le verbe.  
  
9. Sur le **accès** onglet, sélectionnez **Script**, puis cliquez sur **OK**.  
  
10. Une invite vous demande si vous souhaitez autoriser l'extension ISAPI, cliquez sur **Oui**.  
  
11. Avec le bouton droit **Pools d’applications**, pointez sur **nouveau**, puis cliquez sur **pool d’applications**.  
  
12. Dans le **ajouter un Pool d’applications** boîte de dialogue le **nom** , tapez un nom pour le pool d’applications. Sélectionnez **.NET Framework v4.0.30319** puis cliquez sur **OK**.  
  
    > [!NOTE]
    >  Le numéro de version peut varier selon la version de .NET Framework installée sur l’ordinateur.  
  
     Le pool d’applications s’affiche dans la liste des **Pools d’applications**.  
  
13. Dans **Pools d’applications**, dans le **affichage des fonctionnalités**, sélectionnez le pool d’applications, puis cliquez sur **paramètres avancés** dans le volet Actions.  
  
14. Dans le **paramètres avancés** boîte de dialogue le **modèle de processus** section, dans le **identité** , cliquez sur le bouton de sélection (**...** ) bouton.  
  
15. Dans le **identité du Pool d’applications** boîte de dialogue, sélectionnez **compte personnalisé**, puis cliquez sur **définir**. Cliquez sur **OK** pour fermer la boîte de dialogue **Paramètres avancés** .  
  
16. Dans le Gestionnaire des services Internet, ouvrez le **Sites** dossier. Cliquez sur le **Site Web par défaut** puis cliquez sur **ajouter une Application**.  
  
17. Dans le **ajouter une Application** boîte de dialogue **Alias**, entrez un alias à associer à l’application, puis cliquez sur **sélectionnez**.  
  
18. Dans le **sélectionner un Pool d’applications** boîte de dialogue, sélectionnez le nouveau pool d’applications que vous avez créé précédemment, puis cliquez sur **OK**.  
  
19. Cliquez sur le bouton de sélection (**...** ) bouton et accédez à [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]HttpReceive pour le **chemin d’accès physique**.  
  
20. Cliquez sur **connecter en tant que** et entrez le **nom d’utilisateur** et **mot de passe** pour un compte d’utilisateur qui est membre du groupe Administrateurs, puis cliquez sur **OK**.  
  
21. Cliquez sur **des paramètres de Test** et vérifiez qu’aucune erreur n’est affichés dans le **tester la connexion** boîte de dialogue. Cliquez sur **Fermer**, puis sur **OK**.  
  
22. La nouvelle application s’affiche dans la liste des **Sites Web par défaut** dans le Gestionnaire des Services Internet (IIS).  
  
## <a name="see-also"></a>Voir aussi  
 [Pour configurer les emplacement de réception HTTP](../core/how-to-configure-an-http-receive-location.md)