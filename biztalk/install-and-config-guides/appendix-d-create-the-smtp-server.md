---
title: "Annexe d : création d’un serveur SMTP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f7441ba9-a498-42ec-a04d-7f2731407373
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9f4d4acc35f5cb38be5f783ee7c4017c8ada83e2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="appendix-d-create-the-smtp-server"></a>Annexe D : Création du serveur SMTP
Créez le serveur SMTP qu’utilisera la messagerie de base de données SQL Server.  
  
La messagerie de base de données SQL Server est requise pour configurer des alertes BAM lorsque vous utilisez l’une des versions SQL suivantes : 

* [!INCLUDE[sqlserver2016_md](../includes/sqlserver2016-md.md)]
* [!INCLUDE[sqlserver2014](../includes/sqlserver2014-md.md)]
* [!INCLUDE[sqlserver2012](../includes/sqlserver2012-md.md)] 
  
 La fonctionnalité Messagerie de base de données SQL Server utilise un serveur SMTP pour envoyer les alertes BAM. SMTP Server est inclus avec Internet Information Services (IIS). SMTP peut être installé localement sur un serveur BizTalk Server ou un autre serveur avec IIS installé.  
  
> [!IMPORTANT]
>  En règle générale, les systèmes d’exploitation clients tels que Windows 10, Windows 7, etc., n’incluent pas de fonctionnalités de serveur SMTP. Vous pouvez vous connecter à un serveur SMTP existant sur ​​un serveur Windows Server à l’aide de la fonctionnalité *Courrier électronique SMTP* dans IIS. La fonctionnalité *Courrier électronique SMTP* ne correspond PAS à un serveur SMTP, lequel est nécessaire pour la messagerie de base de données SQL Server. En conséquence, cette rubrique ne comprend pas les étapes pour installer et configurer un serveur SMTP sur des systèmes d’exploitation clients.  

## <a name="install-and-configure-the-smtp-server"></a>Installation et configuration du serveur SMTP  
  
Ces procédures s’appliquent à :

* Windows Server 2016
* Windows Server 2012 R2
* Windows Server 2012
  
### <a name="install-smtp-server"></a>Installer un serveur SMTP  
   
1.  Dans le **Gestionnaire de serveur**, sélectionnez **Tableau de bord** dans le volet gauche.  
  
3.  Sélectionnez **Ajouter des rôles et fonctionnalités**. Vous pouvez aussi ouvrir **Ajouter des rôles et fonctionnalités** à partir du menu **Gérer** en haut à droite.  
  
4.  Dans **Avant de commencer**, sélectionnez **Suivant**.  
  
5.  Sélectionnez **Installation basée sur un rôle ou une fonctionnalité**, puis **Suivant**.  
  
6.  Sélectionnez successivement **Sélectionner un serveur du pool de serveurs**, le serveur souhaité et **Suivant**. La fenêtre **Sélection du serveur** répertorie les serveurs qui ont été ajoutés avec **Ajouter un serveur** dans le **Gestionnaire de serveur**. Le serveur local est sélectionné par défaut.  
  
7.  Dans **Rôles du serveur**, sélectionnez **Suivant**.  
  
8.  Dans **Fonctionnalités**, cochez **Serveur SMTP**. Si vous y êtes invité, sélectionnez **Ajouter des fonctionnalités**. Sélectionnez **Suivant**.  
  
9. Dans **Confirmation**, sélectionnez **Redémarrer automatiquement le serveur de destination, si nécessaire**, puis sélectionnez **Installer**. Lorsque vous avez terminé, sélectionnez **Fermer**.  

### <a name="configure-the-smtp-server"></a>Configurer le serveur SMTP  
 La procédure suivante permet de configurer le serveur virtuel SMTP à l'aide du Gestionnaire des services Internet (IIS) 6.0 :  
  
1.  Ouvrez le Gestionnaire des services Internet. Dans Démarrer, recherchez **inetmgr6.exe** et ouvrez-le.  
  
2.  Développez le nom d'ordinateur. Cliquez avec le bouton droit sur **[Serveur virtuel SMTP n°1]** et sélectionnez **Propriétés**.  
  
3.  Dans l’onglet **Accès**, sélectionnez le bouton **Relais**.  
  
4.  Sélectionnez **Ajouter**. Pour **Ordinateur unique**, entrez `127.0.0.1`, puis sélectionnez **OK**.  
  
     En ajoutant 127.0.0.1, nous autorisons le serveur local à envoyer des messages à partir du serveur local SMTP. Si vous voulez que d'autres ordinateurs envoient des messages à partir de ce serveur SMTP, entrez leurs adresses IP.  
  
5.  Sous l’onglet **Remise**, sélectionnez **Sécurité sortante**. Choisissez parmi les éléments suivants :  
  
     **Accès anonyme** : Un nom de compte ou mot de passe n’est pas nécessaire. Cette option désactive l'authentification du serveur SMTP.  
  
     **Authentification de base** : Le nom de compte et le mot de passe du serveur auquel vous vous connectez sont envoyés en texte clair. Le compte que vous entrez transmet les e-mails. L'authentification de base peut être sélectionnée lors de l'envoi d'un e-mail à un compte personnel ou un compte Exchange. Parce que les informations d’identification sont transmises en texte clair, il est recommandé d’activer le **chiffrement TLS**.  
  
     **Authentification Windows intégrée** : Le nom du compte de domaine Windows et le mot de passe sont utilisés à des fins d’authentification. Le compte que vous entrez transmet les e-mails.  
  
     **Chiffrement TLS** : De façon similaire à SSL, TLS sécurise la connexion. Nécessite un certificat de serveur SSL valide installé sur ce serveur.  
  
    > [!TIP]
    >  Pour tester les fonctionnalités SMTP de base avec un compte e-mail personnel, y compris un compte Exchange, sélectionnez **Accès anonyme**. Lorsque l'authentification de base est sélectionnée, SMTP utilise la commande AUTH. Certains fournisseurs de messagerie peuvent échouer en raison de la commande AUTH. Si la commande AUTH échoue, une erreur peut être consignée dans les journaux d'événements Windows sur le serveur SMTP.  
  
6.  Sous l’onglet **Remise**, sélectionnez **Connexions sortantes**. Le port TCP 25 est utilisé par défaut. Il est possible d’entrer un autre port s’il est ouvert dans le pare-feu. Sélectionnez **OK**.  
  
7.  Sous l’onglet **Remise**, sélectionnez **Avancé**. Par défaut, le **nom de domaine complet** du serveur local est répertorié. Selon votre fournisseur d’accès Internet, la propriété **Hôte actif** peut rester vide. Vous pouvez avoir besoin de contacter le fournisseur d'accès Internet pour vérifier si un hôte actif (Smart Host) est nécessaire. Sinon, vous pourriez être en mesure d’entrer smtp.*EMailProvider*.com.  
  
    > [!NOTE]
    >  Un **hôte actif** est un serveur dédié utilisé par un serveur Exchange pour acheminer tous les messages sortants. Quand l’**hôte actif** reçoit les messages, il les transfère vers un domaine distant. L’objectif d’un **hôte actif** est d’améliorer les performances d’un serveur Exchange. Le serveur Exchange Server transmet uniquement l'hôte actif ; il ne contacte pas de façon répétée le domaine distant jusqu'à ce qu'une connexion soit établie.  
  
8.  Sélectionnez **OK** pour fermer toutes les fenêtres.  
  
9. Redémarrez le serveur SMTP : cliquez avec le bouton droit sur **[Serveur virtuel SMTP n°1]**, sélectionnez **Arrêter**, puis sélectionnez **Démarrer**. Un redémarrage est nécessaire pour appliquer les paramètres du serveur SMTP. 

  
## <a name="windows-server-2008-r2-install-and-configure-smtp-server"></a>Windows Server 2008 R2 : Installation et configuration d’un serveur SMTP  
  
### <a name="install-smtp-server"></a>Installer un serveur SMTP  
 La procédure suivante permet d'installer le composant Serveur SMTP :  
  
1.  Dans le **Gestionnaire de serveur**, sélectionnez **Fonctionnalités**, puis **Ajouter des fonctionnalités**.  
  
3.  Dans **Ajouter des fonctionnalités**, sélectionnez **Serveur SMTP**. Si vous y êtes invité, sélectionnez **Ajouter les services de rôle requis**, puis **Suivant**.  
  
4.  Poursuivez l’installation en sélectionnant **Suivant**.  
  
5.  Dans la fenêtre **Confirmer les sélections d’installation**, sélectionnez **Installer**. Lorsque vous avez terminé, sélectionnez **Fermer**.  
  
### <a name="configure-the-smtp-server"></a>Configurer le serveur SMTP  
 La procédure suivante permet de configurer le serveur virtuel SMTP à l'aide du Gestionnaire des services Internet (IIS) 6.0 :  
  
1.  Ouvrez le Gestionnaire IIS 6.0 : Dans **Démarrer**, recherchez **IIS** et sélectionnez **Gestionnaire des services Internet (IIS) 6.0**.  
  
2.  Développez le nom d'ordinateur. Cliquez avec le bouton droit sur **[Serveur virtuel SMTP n°1]** et sélectionnez **Propriétés**.  
  
3.  Dans l’onglet **Accès**, sélectionnez le bouton **Relais**.  
  
4.  Sélectionnez **Ajouter**. Pour **Ordinateur unique**, entrez `127.0.0.1`, puis sélectionnez **OK**.  
  
     En ajoutant 127.0.0.1, nous autorisons le serveur local à envoyer des messages à partir du serveur local SMTP. Si vous voulez que d'autres ordinateurs envoient des messages à partir de ce serveur SMTP, entrez leurs adresses IP.  
  
5.  Sous l’onglet **Remise**, sélectionnez **Sécurité sortante**. Choisissez parmi les éléments suivants :  
  
     **Accès anonyme** : Un nom de compte ou mot de passe n’est pas nécessaire. Cette option désactive l'authentification du serveur SMTP.  
  
     **Authentification de base** : Le nom de compte et le mot de passe du serveur auquel vous vous connectez sont envoyés en texte clair. L'authentification de base peut être sélectionnée lors de l'envoi d'un e-mail à un compte personnel ou un compte Exchange. Parce que les informations d’identification sont transmises en texte clair, il est recommandé d’activer le **chiffrement TLS**.  
  
     **Authentification Windows intégrée** : Le nom du compte de domaine Windows et le mot de passe sont utilisés à des fins d’authentification. Le compte que vous entrez transmet les e-mails.  
  
     **Chiffrement TLS** : De façon similaire à SSL, TLS sécurise la connexion. Nécessite un certificat de serveur SSL valide installé sur ce serveur.  
  
    > [!TIP]
    >  Pour tester les fonctionnalités SMTP de base avec un compte e-mail personnel, y compris un compte Exchange, sélectionnez **Accès anonyme**. Lorsque l'authentification de base est sélectionnée, SMTP utilise la commande AUTH. Certains fournisseurs de messagerie peuvent échouer en raison de la commande AUTH. Si la commande AUTH échoue, une erreur peut être consignée dans les journaux d'événements Windows sur le serveur SMTP.  
  
6.  Sous l’onglet **Remise**, sélectionnez **Connexions sortantes**. Le port TCP 25 est utilisé par défaut. Il est possible d’entrer un autre port s’il est ouvert dans le pare-feu. Sélectionnez **OK**.  
  
    > [!TIP]
    >  Le port TCP peut servir aux connexions entrantes et aux connexions sortantes.  
  
7.  Sous l’onglet **Remise**, sélectionnez **Avancé**. Par défaut, le **nom de domaine complet** du serveur local est répertorié. Selon votre fournisseur d’accès Internet, la propriété **Hôte actif** peut rester vide. Vous pouvez avoir besoin de contacter le fournisseur d'accès Internet pour vérifier si un hôte actif (Smart Host) est nécessaire. Sinon, vous pourriez être en mesure d’entrer smtp.*EMailProvider*.com.  
  
    > [!NOTE]
    >  Un **hôte actif** est un serveur dédié utilisé par un serveur Exchange pour acheminer tous les messages sortants. Quand l’**hôte actif** reçoit les messages, il les transfère vers un domaine distant. L’objectif d’un **hôte actif** est d’améliorer les performances d’un serveur Exchange. Le serveur Exchange Server transmet uniquement l'hôte actif ; il ne contacte pas de façon répétée le domaine distant jusqu'à ce qu'une connexion soit établie.  
  
8.  Sélectionnez **OK** pour fermer toutes les fenêtres.  
  
9. Un redémarrage est nécessaire pour appliquer les paramètres du serveur SMTP. Pour redémarrer le serveur SMTP : cliquez avec le bouton droit sur **[Serveur virtuel SMTP n°1]**, sélectionnez **Arrêter**, puis sélectionnez **Démarrer**.  
  
  
## <a name="test-the-smtp-server"></a>Tester le serveur SMTP  
 Telnet peut être utilisé pour tester la configuration du serveur SMTP. La procédure suivante envoie un message à une adresse e-mail à l’aide de votre serveur SMTP configuré. L’article [http://support.microsoft.com/kb/153119](http://support.microsoft.com/kb/153119) fournit des descriptions des commandes telnet.  
  
1.  Ouvrez une fenêtre de commande comme administrateur.
  
2.  À l’invite de commandes, tapez :  
  
     `telnet localhost 25`  
  
     Si Telnet n'est pas installé, installez-le en tapant :  
  
     `pkgmgr /iu:"TelnetClient"`  
  
3.  Démarrez la communication en tapant :  
  
     `EHLO server`  
  
4.  Entrez l'adresse électronique de l'expéditeur :  
  
     `MAIL FROM: *YourEmailAddress*@*YourProvider*.com`  
  
     Par exemple, entrez :  
  
     `MAIL FROM: EmailAddress@outlook.com`  
  
5.  Entrez l’adresse e-mail de l’expéditeur :  
  
     `RCPT TO: *YourEmailAddress*@*YourProvider*.com`  
  
     Par exemple, entrez :  
  
     `RCPT TO: EmailAddress@outlook.com`  
  
6.  Indiquez au serveur SMTP que vous êtes prêt à envoyer des données en tapant :  
  
     `DATA`  
  
7.  Entrez l’objet en tapant :  
  
     `Subject: Test Message`  
  
8.  Appuyez deux fois sur Entrée.  
  
9. Entrez le corps du message en tapant :  
  
     `This is the message body of the test message.`  
  
10. Appuyez sur Entrée, tapez un point (.), puis appuyez sur Entrée.  
  
 Vérifiez l'adresse RCPT TO du message. Si l’e-mail n’est pas remis (consultez votre boîte de réception et le dossier Courrier indésirable), le message n’a pas été correctement envoyé et réside peut-être dans le dossier de la file d’attente SMTP (C:\inetpub\mailroot\Queue).  
  