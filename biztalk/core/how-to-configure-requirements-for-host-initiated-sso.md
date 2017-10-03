---
title: "Configuration requise pour l’ordinateur hôte authentification unique initiée par | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- service accounts, granting privileges [SSO]
- host initiated SSO, configuring
- domain function level [SSO]
- host initiated SSO, Transaction Integrator (TI)
- SPN [SSO]
- managing [SSO], granting TCB privileges
- Transaction Integrator (TI)
- host initiated SSO, SPN
- host initiated SSO, TCB privileges
- configuring, host initiated SSO
- creating, SPNs [SSO]
- TCB privileges [SSO]
- managing [SSO], host initiated
- host initiated SSO, domain function level
- service accounts, SSO
- SSO, host initiated
- managing [SSO], creating SPNs
- SSO, service accounts
ms.assetid: 91d77c9f-bab2-4f6e-8bce-e31c59cebb20
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f9f8a004c1883a05c3fcf60324f428144591cff4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-requirements-for-host-initiated-sso"></a>Configuration des conditions requises pour l'authentification unique initiée par l'hôte
L'authentification unique de l'entreprise et l'authentification unique initiée par l'hôte ont plusieurs aspects en commun. Toutefois, certaines conditions requises concernant la plateforme et Active Directory restent uniques à l'authentification unique initiée par l'hôte. Cette rubrique présente la configuration requise et répertorie les étapes permettant de la créer ou de la vérifier sur votre système.  
  
-   L'exécution de l'authentification unique initiée par l'hôte est uniquement prise en charge sur un environnement de domaine Windows Server 2008 natif.  
  
-   Le compte de service pour le service SSO qui effectue l'authentification unique initiée par l'hôte doit être configuré de manière à disposer des privilèges TCB (Trusted Computing Base). (Vous pouvez configurer ces paramètres pour le compte de service dans la stratégie de sécurité du domaine.)  
  
 En outre, certaines conditions sont obligatoires lors de l'utilisation de l'intégrateur de transactions pour le traitement initié par l'hôte. Il exploite l'authentification unique initiée par l'hôte dans le but de mettre en place l'authentification unique pour des utilisateurs non-Windows.  
  
 Par exemple, le compte de service associé à l'intégrateur de transactions pour le traitement initié par l'hôte est exécuté sous un compte de service nom_domaine\hipsvc. Ce service peut héberger des applications qui doivent accéder à des ressources Windows locales ou distantes par l'intermédiaire du compte Windows correspondant au compte non-Windows.  
  
 Le compte nom_domaine\hipsvc doit appartenir au compte de groupe Administrateurs d'application pour l'application associée qui est utilisée pour l'authentification unique.  
  
 Le compte nom_domaine\hipsvc doit disposer de privilèges de délégation contrainte afin d'utiliser l'authentification unique initiée par l'hôte. Cette opération incombe à l'administrateur de domaine dans Active Directory. La délégation peut être configurée pour les comptes disposant de noms principaux de service enregistrés. La délégation contrainte autorise le compte de service à accéder uniquement aux composants spécifiés par l'administrateur.  
  
### <a name="to-check-your-domain-function-level"></a>Pour vérifier le niveau fonctionnel du domaine  
  
1.  Dans votre **Active Directory Domains and Trusts** enfichable MMC, droit, cliquez sur le nœud **Active Directory Domains and Trusts**, puis cliquez sur **augmenter le niveau fonctionnel de la forêt**.  
  
2.  Vérifiez que le niveau fonctionnel est **Windows Server 2008**. Si ce n'est pas le cas, consultez la documentation de Active Directory avant de tenter de modifier ce paramètre.  
  
### <a name="to-create-an-spn"></a>Pour créer un nom principal de service (SPN)  
  
1.  Téléchargez le **setspn** utilitaire à partir de l’emplacement suivant : [http://go.microsoft.com/fwlink/?LinkId=33178](http://go.microsoft.com/fwlink/?LinkId=33178).  
  
2.  Dans le menu **Démarrer** , cliquez sur **Exécuter**.  
  
3.  Dans le **exécuter** boîte de dialogue, tapez **cmd**, puis cliquez sur **OK**.  
  
4.  Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise. La valeur par défaut est \<lecteur > : \Program Files\Enterprise Single Sign-On.  
  
5.  Type **setpsn-hipsvc\computername.domain.com domain\hissvc**  
  
     où **hipsvc\computername.domain.com** est un service qui effectue l’opération et l’ordinateur, il est en cours d’exécution, et **domain\hissvc** est le compte de service associé à hipsvc.  
  
 Après avoir effectué cette opération, vous pouvez configurer la délégation contrainte dans Active Directory pour ce compte de service (domain\hissvc) afin d'accéder aux ressources appropriées sur le réseau.  
  
#### <a name="to-give-tcb-privileges-for-the-sso-service-account"></a>Pour octroyer les privilèges TCB pour le compte de service de l'authentification unique  
  
-   Sous votre **stratégie de sécurité de domaine - stratégies locales - Attribution des droits utilisateur**, ajoutez le compte de Service d’authentification unique pour le **agir en tant que partie du système d’exploitation** stratégie.  
  
     Pour plus d’informations sur Kerberos Protocol Transition and Constrained Delegation, accédez à [http://go.microsoft.com/fwlink/?LinkId=195484](http://go.microsoft.com/fwlink/?LinkId=195484).  
  
## <a name="see-also"></a>Voir aussi  
 [L’authentification unique initiée par l’hôte](../core/host-initiated-sso.md)