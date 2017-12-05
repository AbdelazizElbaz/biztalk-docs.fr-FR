---
title: "Instructions pour la résolution des problèmes d’autorisation IIS | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: troubleshooting
ms.assetid: d9793a90-3aa3-46ab-a317-6d1e0fbfc1ef
caps.latest.revision: "30"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: eb91509ec3ad1c329190c848c25a60434f93499e
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="guidelines-for-resolving-iis-permissions-problems"></a>Instructions pour la résolution des problèmes d'autorisation IIS
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] exploite pleinement Microsoft Internet Information Services (IIS) pour la prise en charge des services Web et pour une utilisation avec les adaptateurs HTTP, SOAP et Windows SharePoint Services.  
  
 Avant de résoudre les problèmes d'autorisation IIS, il est utile de comprendre comment IIS implémente l'isolation des applications.  
  
 IIS fournit des fonctionnalités pour la création d'applications IIS en tant que processus hôte distincts exécutés dans leur propre espace mémoire. Une fois que vous créez un hôte d’application IIS, vous devez définir deux jeux d’autorisations, l’hôte d’application IIS **l’identité du processus** et l’hôte d’application IIS **droits d’accès utilisateur**. Lorsque vous résolvez les problèmes d'autorisation IIS, vous devez étudier ces deux ensembles d'autorisations.  
  
> [!NOTE]
>  Le **l’identité du processus** et **droits d’accès utilisateur** sont également appelées le **contexte de sécurité** du processus hôte d’application IIS.  
  
 Cette rubrique explique comment définir **l’identité du processus** et **droits d’accès utilisateur** pour un processus hôte d’application IIS et donne des recommandations générales pour la résolution des problèmes d’autorisation IIS.  
  
## <a name="setting-iis-application-host-process-identity"></a>Définition de l'identité du processus hôte d'application IIS  
 La configuration d'un processus hôte d'application IIS varie en fonction du niveau des fonctionnalités servies par le processus hôte. Par exemple, un processus hôte d’application IIS servant uniquement des pages HTML statiques est généralement configuré différemment d’un processus hôte d’application IIS servant des pages ASP ou des applications ASP.NET.  
  
 La configuration d'un processus hôte d'application IIS dépend également de la version d'IIS hébergeant l'application. L'identité du processus hôte des applications s'exécutant sur Windows Server 2008 (IIS 7.0) est régie par l'identité du pool d'applications associé à l'application.  
  
### <a name="setting-iis-process-identity-for-iis-70-on-windows-server-2008-or-windows-vista"></a>Définition de l'identité du processus IIS pour IIS 7.0 sur Windows Server 2008 ou Windows Vista  
  
1.  Cliquez sur **Démarrer**, puis **tous les programmes**, puis cliquez sur **le Gestionnaire Internet Information Services (IIS) 7**.  
  
2.  Dans le Gestionnaire des Services Internet (IIS), développez  *\<nom de l’ordinateur\>***(compte d’utilisateur)** et cliquez sur **Pools d’applications**.  
  
3.  Cliquez sur un pool d’applications, sur **afficher les Applications** pour voir les applications associées du pool d’applications.  
  
4.  Cliquez sur un pool d’applications, sur **paramètres avancés** pour afficher la boîte de dialogue Paramètres avancés pour le pool d’applications.  
  
5.  Modifiez l’identité du pool d’applications en cliquant sur le bouton de sélection (...) en regard **identité** sous le **modèle de processus** section de la **paramètres avancés** boîte de dialogue zone.  
  
## <a name="setting-user-access-rights-for-the-iis-server"></a>Définition des droits d'accès utilisateur pour le serveur IIS  
 Tandis que l'identité du processus détermine le contexte de sécurité disponible dans le processus hôte d'application IIS en cours d'exécution, les autorisations d'accès utilisateur régissent le contexte de sécurité du compte qui accède réellement aux pages Web servies. Les autorisations doivent être définies de façon appropriée pour les deux contextes, afin d'éviter toute erreur.  
  
 IIS 7.0 prend en charge les méthodes d’authentification utilisateur suivantes :  
  
-   **L’accès anonyme :** permet aux utilisateurs d’établir une connexion anonyme. Le serveur IIS connecte l'utilisateur avec le compte invité spécifié.  
  
-   **Emprunt d’identité ASP.NET** permet à une application pour s’exécuter dans un des deux contextes : en tant qu’utilisateur authentifié par IIS ou sous un compte arbitraire que vous avez configurée.  
  
-   **L’authentification de base :** transmet les mots de passe sur le réseau en texte clair, une forme non chiffrée.  
  
-   **L’authentification Digest :** fonctionne uniquement avec les comptes Active Directory envoie une valeur de hachage sur le réseau, plutôt qu’un mot de passe en texte clair. L'authentification Digest traverse les serveurs proxy et les pare-feu et est disponible dans les répertoires WebDAV (Web Distributed Authoring and Versioning). L'utilisation de l'authentification Digest nécessite que l'authentification anonyme soit au préalable désactivée.  
  
-   **L’authentification par formulaire** : héberge l’authentification pour les sites à trafic élevé ou applications sur les serveurs publics. L'authentification par formulaires vous permet de gérer l'inscription et l'authentification clientes au niveau de l'application, plutôt que de s'appuyer sur des mécanismes d'authentification fournis par le système d'exploitation.  
  
-   **L’authentification Windows :** utilise l’authentification sur votre domaine Windows pour authentifier les connexions clientes.  
  
#### <a name="to-set-user-access-rights-for-a-virtual-directory-in-iis-70"></a>Pour définir les droits d'accès utilisateur d'un répertoire virtuel dans IIS 7.0  
  
1.  Dans le Gestionnaire Internet Information Services (IIS), développez  *\<nom de l’ordinateur\>*, **Sites**, et **Site Web par défaut** dans les **Connexions** volet.  
  
2.  Sélectionnez le répertoire virtuel, puis cliquez sur le **affichage des fonctionnalités** en bas du volet espace de travail pour répertorier les fonctionnalités configurables du répertoire virtuel.  
  
3.  Double-cliquez sur le **authentification** fonctionnalité dans le volet espace de travail pour répertorier les méthodes d’authentification sont activées pour le répertoire virtuel.  
  
4.  Cliquez pour sélectionner la méthode d’authentification que vous souhaitez activer ou désactiver et cliquez sur **désactiver** ou **activer** dans les **Actions** volet du Gestionnaire IIS.  
  
    > [!NOTE]
    >  Si **activer l’accès anonyme** est activée, IIS définit les droits d’accès utilisateur en tant que l’identité de l’utilisateur anonyme configuré avant la définition de droits d’accès utilisateur avec d’autres méthodes d’authentification activées.  
    >   
    >  Pour configurer l’identité d’utilisateur anonyme, cliquez sur le **l’authentification anonyme** (méthode) et cliquez sur **modifier** pour afficher la **modifier identification anonyme**boîte de dialogue.  
  
## <a name="general-guidelines-for-resolving-iis-permissions-problems"></a>Recommandations générales pour la résolution des problèmes d'autorisation IIS  
 Pour résoudre les problèmes d'autorisation IIS, procédez comme indiqué ci-dessous :  
  
1.  Recherchez les erreurs dans le journal d'application de l'ordinateur exécutant le serveur IIS.  
  
2.  Suivez les étapes de [IIS 7.0 : configuration du suivi des demandes ayant échoué dans IIS 7.0](http://go.microsoft.com/fwlink/?LinkId=130600) pour résoudre les problèmes d’autorisations sur les ordinateurs IIS 7.0.  
  
3.  Recherchez les erreurs HTTP 401 dans les fichiers journaux IIS du serveur IIS.  
  
     Les fichiers journaux IIS d'un ordinateur exécutant Windows Server 2008 ou Windows Vista se trouvent par défaut dans le répertoire suivant :  
  
     C:\inetpub\logs\LogFiles\W3SVC1\  
  
    -   Si le fichier journal IIS pour un ordinateur IIS 7.0 contient des erreurs HTTP 401, suivez les étapes décrites dans l’article 943891 de la Base de connaissances Microsoft, « le codes d’état HTTP dans IIS 7.0 » disponible à l’adresse [http://support.microsoft.com/kb/943891](http://support.microsoft.com/kb/943891) pour déterminer le code de sous-état et résoudre les problèmes d’autorisation basée sur le code d’état.  
  
    -   Vérifiez la valeur de la **cs-username** champ associé à l’erreur HTTP 401. Ce champ contient le nom de l'utilisateur authentifié ayant accédé au serveur IIS. Le compte d'utilisateur anonyme est représenté par un trait d'union (-) dans ce champ. Vérifiez que ce compte dispose des autorisations associées aux ressources appropriées.  
  
4.  Vérifiez que les informations d'identification de l'identité du processus utilisées par le processus hôte d'application IIS sont correctement définies et que le compte dispose des autorisations appropriées. Si le compte utilisé pour l'identité du processus ne dispose pas des autorisations suffisantes, vous devez soit changer de compte, soit accorder au compte utilisé les autorisations appropriées.  
  
5.  Utilisez les utilitaires RegMon et FileMon décrits dans [outils et utilitaires à utiliser pour la résolution des problèmes](../core/tools-and-utilities-to-use-for-troubleshooting.md) pour diagnostiquer les problèmes d’autorisations accès fichier ou du Registre.  
  
## <a name="see-also"></a>Voir aussi  
 [Résolution des problèmes d’autorisations BizTalk Server](../core/troubleshooting-biztalk-server-permissions.md)   
 [IIS 7.0 : Configuration de l’authentification dans IIS 7.0](http://go.microsoft.com/fwlink/?LinkId=129909)