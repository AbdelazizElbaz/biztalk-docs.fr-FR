---
title: "Recommandations de sécurité pour l’authentification unique | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SSO, deploying
- Kerberos protocol, SSO
- deploying, SSO
- user accounts, SSO
- deploying, security
- SQL Server, SSO
- security, SSO
- SSO, Kerberos protocol
- SSO, auditing
- best practices, deploying
- SSO, Windows groups
- SSO, best practices
- SSO, perimeter network
- Windows groups, SSO
- SSO, SQL Server access
- best practices, security
- Master Secret server, clustering
- perimeter networks
- auditing [SSO]
- SSO, security
- SSO, user accounts
- Master Secret server, best practices
ms.assetid: 7ae922b4-fd48-41f4-aaab-419a5e22c753
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0a86e669e603eaabf142ce446b8d7204a6cc0091
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="sso-security-recommendations"></a>Recommandations de sécurité pour l’authentification unique
Grâce au système d'authentification unique de l'entreprise (SSO), les utilisateurs peuvent se connecter à différents systèmes à l'aide d'un seul ensemble d'informations d'identification. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] se sert du système SSO comme d'un magasin pour stocker des informations personnelles. Bien que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] s'installe automatiquement lorsque vous installez le composant d'exécution de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], vous pouvez également installer l'authentification unique de l'entreprise en tant que composant autonome, indépendant de votre environnement [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Pour plus d’informations sur Enterprise Single Sign-On, consultez [à l’aide de l’authentification unique](../core/using-sso.md). Il est recommandé de suivre ces instructions pour sécuriser et déployer les services et ressources de l'authentification unique de l'entreprise dans votre environnement.  
  
## <a name="general-deployment-recommendations-for-sso"></a>Recommandations générales pour le déploiement de SSO  
  
-   L'environnement ne doit compter qu'un seul serveur de secret principal et une seule base de données SSO, même si vous disposez de plusieurs groupes BizTalk dans votre environnement. Vous devez configurer ces deux serveurs avant de configurer tout autre serveur BizTalk et SSO.  
  
-   Vous devez avoir un serveur de temps dans votre environnement pour assurer la synchronisation de tous les serveurs SSO. Si les horloges des serveurs SSP ne sont pas synchronisées, la sécurité de votre environnement pourrait être compromise.  
  
-   Puisqu'il n'y a qu'un seul serveur de secret principal dans tout votre environnement, il est recommandé d'utiliser une configuration de cluster active/active pour le serveur de secret principal. Pour plus d’informations sur le serveur de secret principal de clustering, consultez [mise en Cluster du serveur de secret principal](../core/how-to-cluster-the-master-secret-server1.md).  
  
-   Le serveur de secret principal contient la clé de chiffrement que le système SSO utilise pour chiffrer les informations dans la base de données SSO. Il est recommandé de ne pas installer ni configurer d'autres produits ou services sur cet ordinateur.  
  
    > [!NOTE]
    >  L'ordinateur sur lequel vous installez et configurez le serveur de secret principal ne doit pas être un serveur.  
  
-   Le serveur de secret principal doit avoir accès à un support amovible ou un dossier de système de fichiers NTFS afin de sauvegarder et restaurer le secret principal. Si vous utilisez un support amovible, assurez-vous de prendre les mesures appropriées pour protéger celui-ci. Si vous sauvegardez le secret principal sur un système de fichiers NTFS, assurez-vous de protéger le fichier et le dossier. Seul l'administrateur SSO doit avoir accès à ce fichier.  
  
-   Vous devez sauvegarder le secret principal dès sa génération par le serveur de secret principal. Cela vous permet de récupérer les données dans la base de données SSO en cas d'échec du serveur de secret principal. Pour plus d’informations sur la sauvegarde du secret, consultez [gestion du Secret](../core/managing-the-master-secret.md).  
  
-   Sauvegardez votre secret actuel ou générez un nouveau secret régulièrement, par exemple une fois par mois. Sans le secret, vous ne pouvez pas récupérer les informations de la base de données SSO. Pour plus d’informations sur la sauvegarde et restauration du secret, consultez [gestion du Secret](../core/managing-the-master-secret.md).  
  
## <a name="security-recommendations-for-sso-groups-and-accounts"></a>Recommandations de sécurité pour les groupes et comptes SSO  
  
-   Il est recommandé d'utiliser des groupes Windows, et non des comptes utilisateur uniques, en particulier pour les groupes Administrateurs SSO et Administrateurs d'applications associées à SSO. Ces groupes doivent toujours avoir au moins deux comptes utilisateur comme membres du groupe.  
  
-   Les comptes de service d'exécution SSO et les comptes utilisateur administrateurs SSO doivent être des comptes différents, même s'ils sont membres du même groupe Administrateurs SSO. Contrairement aux comptes de service d'exécution SSO, les utilisateurs administrateurs SSO réalisant des tâches administratives, telles que la génération et la sauvegarde du secret, doivent être des administrateurs Windows.  
  
    > [!IMPORTANT]
    >  Les droits administratifs Windows ne remplacent pas les droits d'utilisateur de l'administrateur SSO. Pour réaliser une tâche administrative SSO, vous devez être membre du groupe Administrateurs SSO, même si vous êtes déjà un administrateur Windows.  
  
-   Si vous utilisez la fonction de création de tickets d'authentification unique, vous devez utiliser des comptes de domaine reconnus par les ordinateurs dans le domaine de traitement (domaine où se trouvent les serveurs SSO).  
  
-   Il est recommandé d'utiliser un compte de service unique pour le service SSO correspondant au serveur de secret principal.  
  
-   Le compte administrateur SSO est un compte disposant de privilèges élevés dans le système SSO. Il est aussi le compte administrateur SQL Server pour le serveur SQL qui a la base de données SSO. Vous devez avoir des comptes dédiés pour les administrateurs SSO et ne devez pas utiliser ces comptes pour un autre but. Vous devez limiter l'appartenance au groupe Administrateurs SSO uniquement aux comptes responsables de l'exécution et de la maintenance du système SSO.  
  
-   Vous devez ajouter manuellement le groupe Administrateurs BizTalk au groupe Administrateurs d'applications associées à SSO, afin que les administrateurs BizTalk puissent utiliser le système SSO pour enregistrer les informations de configuration pour les adaptateurs dans la base de données SSO. Seuls les administrateurs BizTalk gérant des adaptateurs doivent être membres du groupe Administrateurs d'applications associées à SSO. Les administrateurs BizTalk ne doivent pas être des administrateurs SSO.  
  
## <a name="security-recommendations-for-an-sso-deployment"></a>Recommandations de sécurité pour un déploiement SSO  
  
-   Si votre réseau prend en charge l'authentification Kerberos, vous devez inscrire tous les serveurs SSO. Lorsque vous utilisez l’authentification Kerberos entre le serveur de secret principal et de la base de données SSO, vous devez configurer des noms de Principal du Service (SPN) sur le serveur SQL server où se trouve la base de données SSO. Pour plus d’informations sur la configuration des noms principaux de Service, consultez le site Web de téléchargement Microsoft à l’adresse [http://go.microsoft.com/fwlink/?LinkId=195797](http://go.microsoft.com/fwlink/?LinkId=195797).  
  
-   Lors de l'exécution de [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] ou de [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)], si le serveur de secret principal est sur un domaine différent des autres serveurs SSO et de la base de données SSO, vous devez désactiver la sécurité RPC (utilisée pour l'authentification DTC (Data Transaction Coordinator) entre ordinateurs) sur le serveur de secret principal, sur les serveurs SSO (ordinateurs de traitement dans le domaine de traitement), ainsi que sur la base de données SSO. La sécurité RPC est une fonctionnalité DTC dans [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] et [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]. Lorsque vous désactivez la sécurité RPC, le niveau de sécurité de l'authentification DTC pour les appels RPC repasse sur un niveau disponible dans Microsoft Windows Server 2003.  
  
-   Les administrateurs SSO doivent régulièrement surveiller le journal des événements dans le serveur de secret principal et le serveur SSO pour des audits SSO.  
  
-   Outre les pare-feu, il est recommandé d'utiliser la sécurité du protocole Internet (IPSec) ou le protocole SSL (Secure Sockets Layer) entre tous les serveurs SSO et la base de données SSO. Pour plus d’informations sur le protocole SSL, consultez le site Web de la prise en charge et de Microsoft Help à [http://go.microsoft.com/fwlink/?LinkId=195798](http://go.microsoft.com/fwlink/?LinkId=195798). Pour plus d’informations sur l’utilisation de SSL entre tous les serveurs SSO et la base de données SSO, consultez [comment activer SSL pour SSO](../core/how-to-enable-ssl-for-sso.md).  
  
## <a name="perimeter-network"></a>Réseau de périmètre  
 Lorsque vous exécutez les services Internet (IIS) et l'authentification unique de l'entreprise, suivez ces recommandations :  
  
-   Si les services IIS sont dans un réseau de périmètre (également appelé DMZ, zone démilitarisée, et sous-réseau filtré), placez un autre serveur IIS derrière le pare-feu pour qu'il se connecte au système SSO.  
  
-   N'ouvrez pas le port RPC (appel de procédure distante) sur IIS.  
  
## <a name="sql-server-access"></a>Accès à SQL Server  
 Tous les serveurs SSO accèdent à la base de données SSO SQL Server. Pour plus d’informations sur les bases de données SQL Server sécurisée, consultez [http://go.microsoft.com/fwlink/?LinkId=33175](http://go.microsoft.com/fwlink/?LinkId=33175).  
  
 Il est recommandé d'utiliser le protocole SSL (Secure Sockets Layer) et/ou la sécurité du protocole Internet (IPSec) pour sécuriser la transmission de données entre les serveurs SSO et la base de données SSO. Pour plus d’informations sur l’utilisation de SSL, consultez [http://go.microsoft.com/fwlink/?LinkId=195798](http://go.microsoft.com/fwlink/?LinkId=195798).  
  
 Pour activer le protocole SSL pour la connexion entre le serveur SSO et la base de données SSO, vous pouvez définir la prise en charge SSL sur chaque serveur SSO à l'aide de l'utilitaire ssoconfig. Cette option permet à SSO de toujours utiliser le protocole SSL lors de l'accès à la base de données SSO. Pour plus d’informations, consultez [comment activer SSL pour SSO](../core/how-to-enable-ssl-for-sso.md).  
  
## <a name="strong-passwords"></a>Mots de passe forts  
 Il est très important d'utiliser des mots de passe forts pour tous les comptes, notamment les comptes qui sont membres du groupe Administrateurs SSO car ces utilisateurs contrôlent tout le système SSO.  
  
## <a name="sso-administrator-accounts"></a>Comptes administrateur SSO  
 Il est recommandé d'utiliser des comptes de service différents pour les services SSO qui s'exécutent sur différents ordinateurs. Vous ne devez pas utiliser le compte administrateur SSO qui réalise des opérations administratives, telles que la génération et la sauvegarde du secret pour le service SSO. Alors que les comptes de service SSO ne doivent pas être des administrateurs locaux sur cet ordinateur, l'administrateur SSO qui réalise des opérations administratives doit être un administrateur local sur l'ordinateur, pour certaines opérations.  
  
## <a name="master-secret-server"></a>Serveur de secret principal  
 Il est vivement recommandé de sécuriser et de verrouiller le serveur de secret principal. Vous ne devez pas utiliser ce serveur comme serveur de traitement. Le seul objectif de ce serveur doit être de conserver le secret principal. Vous devez garantir la sécurité physique de cet ordinateur et seuls les administrateurs SSO doivent y accéder.  
  
## <a name="kerberos"></a>Kerberos  
 SSO prend en charge Kerberos et il est recommandé de configurer le protocole Kerberos pour SSO. Pour configurer Kerberos avec l'authentification unique, vous devez enregistrer un nom principal de service (SPN) sur le service SSO. Par défaut, lorsque vous configurez Kerberos, SSO utilise ce nom pour authentifier les composants utilisant le service SSO. Il est recommandé de configurer l'authentification Kerberos entre les sous-services administratifs SSO et le serveur SSO. Vous pouvez également utiliser l'authentification Kerberos entre les serveurs SSO et entre les serveurs SSO et le serveur SQL où se trouve la base de données SSO.  
  
 Pour configurer et vérifier Kerberos, utilisez les utilitaires setspn et kerbtray. Pour plus d’informations sur ces utilitaires, consultez [http://go.microsoft.com/fwlink/?LinkId=33178](http://go.microsoft.com/fwlink/?LinkId=33178).  
  
## <a name="delegation"></a>Délégation  
 Lors de l'utilisation de [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] ou de [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)], il est possible d'utiliser la délégation contrainte mais il est recommandé de ne pas utiliser la délégation pour effectuer les tâches de l'administrateur SSO. De même, il est recommandé de ne pas déléguer des tâches supplémentaires ou des droits d'utilisateur à l'administrateur SSO.  
  
## <a name="auditing"></a>Audit  
 L'audit est un mécanisme essentiel de suivi des informations dans votre environnement. L'authentification unique de l'entreprise (SSO) audite toutes les opérations effectuées dans la base de données SSO. SSO utilise les journaux des événements et les journaux d'audit de la base de données elle-même. SSO fournit deux niveaux d'audit pour les serveurs d'authentification unique :  
  
-   Les niveaux d'audit positifs auditent les opérations réussies.  
  
-   Les niveaux d'audit négatifs auditent les opérations qui échouent.  
  
 Les administrateurs SSO peuvent définir les niveaux d'audit positifs et négatifs selon leurs stratégies d'entreprise.  
  
 Vous pouvez définir des audits positifs et négatifs sur l'un des niveaux suivants :  
  
 0 = Aucun. Ce niveau n'émet aucun message d'audit.  
  
 1 = Faible  
  
 2 = Moyen  
  
 3 = Élevé. Ce niveau émet autant de messages d'audit que possible.  
  
 La valeur par défaut pour l'audit positif est 0 (Aucun) et la valeur par défaut pour l'audit négatif est 1 (Faible). Vous pouvez modifier ces valeurs selon le niveau d'audit souhaité pour votre système SSO.  
  
> [!IMPORTANT]
>  L'audit de l'authentification unique de l'entreprise émet des messages générés par le service d'authentification unique. Il ne s'agit pas d'un audit de sécurité et le système SSO n'enregistre pas les informations dans le journal de sécurité du journal des événements. Le système SSO enregistre les messages d'audit SSO directement dans le journal des événements de l'application.  
  
### <a name="database-level-auditing"></a>Audit au niveau de la base de données  
 Pour l'audit au niveau de la base de données, le système SSO suit les opérations effectuées dans la base de données SSO dans les tables d'audit de la base de données. La taille de ces tables d'audit est définie au niveau du système SSO. Vous pouvez auditer les applications associées supprimées, les mappages supprimés et les recherches d'informations d'identification effectuées. Par défaut, la taille de l'audit est définie sur 1000 entrées. Les administrateurs SSO peuvent modifier cette taille selon leurs stratégies d'entreprise.  
  
## <a name="using-sso-accounts"></a>Utilisation de comptes SSO  
 Cette section présente les meilleures pratiques relatives à l'utilisation des groupes de domaine et locaux et des comptes individuels dans le système d'authentification unique de l'entreprise.  
  
### <a name="domain-windows-groups-and-accounts"></a>Groupes et comptes Windows de domaine  
 Lorsque vous travaillez avec des groupes Windows de domaine, les recommandations suivantes s'appliquent :  
  
-   Utilisez des groupes de domaine et des comptes de domaine.  
  
-   Lors de l'utilisation de [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] ou [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)], le compte de service d'authentification unique de l'entreprise (ENTSSO) peut être configuré pour s'exécuter sous le compte de service réseau. Cependant, il n'est pas recommandé pour des raisons de sécurité car le compte de service réseau requiert le privilège d'administrateur SSO. Au lieu de cela, utilisez un compte de service de domaine unique pour le compte de service ENTSSO.  
  
-   Utilisez un groupe de domaine pour les administrateurs SSO. Vous ne devez pas spécifier un compte de domaine individuel comme administrateur SSO car vous ne pouvez pas modifier ce compte d'un compte individuel en un autre compte individuel.  
  
-   Bien que vous puissiez spécifier un compte de domaine individuel comme administrateur d'applications associées à SSO, vous devez utiliser un groupe de domaine.  
  
-   Bien que vous puissiez spécifier un compte de domaine individuel comme administrateur de l'application, vous devez utiliser un groupe de domaine.  
  
-   Vous devez utiliser des groupes de domaine pour le compte utilisateur de l'application. Le compte utilisateur des applications SSO ne prend pas en charge un compte individuel.  
  
-   Plusieurs comptes peuvent être spécifiés pour chacun de ces comptes d'accès à SSO.  
  
## <a name="see-also"></a>Voir aussi  
 [Ports pour l’entreprise unique serveurs d’authentification](../core/ports-for-the-enterprise-single-sign-on-servers.md)   
 [Droits d’utilisateur de sécurité minimales](../core/minimum-security-user-rights.md)