---
title: "Processus de déploiement | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SSO, deploying
- deploying, SSO
- LogonExternalUser test [SSO]
- security, SSO
- SSO, LogonExternalUser test
- SSO, security
ms.assetid: 7dd4c022-c70b-467a-bf94-dc4ac6029f81
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 21be32ec58c90c1fb95134a002bee82ef5d78fa5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="deployment-process"></a>Processus de déploiement
La procédure suivante donne une vue d'ensemble du déploiement sécurisé de l'authentification unique de l'entreprise. Pour obtenir des procédures détaillées relatives aux actions à effectuer dans SQL Server, consultez la documentation SQL Server.  
  
1.  Dans le contrôleur de domaine SQL Serveur, utilisez l'Assistant Nouvelle approbation pour créer une approbation dotée des propriétés suivantes :  
  
    -   **Nom :** ORCH.com  
  
    -   **Direction :** bidirectionnelle  
  
    -   **Côtés :** ce domaine uniquement  
  
    -   **Sortant de niveau de l’authentification de confiance - domaine Local :** l’authentification sélective  
  
    -   **Mot de passe :** choisir un mot de passe  
  
    -   **Confirmer l’approbation sortante :** Oui  
  
    -   **Confirmer l’approbation entrante :** N°  
  
2.  Dans le contrôleur de domaine ORCH.com, utilisez l'Assistant Nouvelle approbation pour créer une approbation dotée des propriétés suivantes :  
  
    -   **Nom :** SQL.com  
  
    -   **Direction :** bidirectionnelle  
  
    -   **Côtés :** ce domaine uniquement  
  
    -   **Sortant de niveau de l’authentification de confiance - domaine Local :** l’authentification sélective  
  
    -   **Mot de passe :** doit être le même que le mot de passe pour ORCH.com  
  
    -   **Confirmer l’approbation sortante :** Oui  
  
    -   **Confirmer l’approbation entrante :** N°  
  
3.  Dans le contrôleur de domaine ORCH.com, définissez l'approbation du domaine pour les entrées provenant de SQL.COM.  
  
4.  Dans le contrôleur de domaine SQL.com, définissez l'approbation du domaine pour les sorties provenant de ORCH.COM.  
  
5.  Dans le contrôleur de domaine ORCH.com, élevez le niveau fonctionnel du domaine à Windows Server 2008 SP2 ou Windows Server 2008 R2.  
  
6.  Dans le domaine ORCH, créez les utilisateurs suivants :  
  
    -   ORCH\SSOSvcUser  
  
    -   ORCH\TestAppUser  
  
    -   ORCH\AffAppUser  
  
7.  Ajouter **agir en tant que partie du système d’exploitation** à SSOSvcUser et TestAppUser.  
  
8.  Ajouter **autorisé à authentifier** privilège à ORCH\TestAdmin.  
  
9. Ajoutez ORCH\SSOSvcUser à SQL2 dans le domaine SQL. (Cette étape nécessite l'utilisation de la vue avancée dans Active Directory MMC.)  
  
10. Créez les deux comptes de connexion suivants sur l'ordinateur SQL2 :  
  
    -   ORCH\TestAdmin  
  
    -   ORCH\SSOSvcUser  
  
11. Créez les deux groupes globaux de domaine sur le domaine SQL2 :  
  
    -   ORCH\SSOAdminGroup  
  
    -   ORCH\SSOAffAdminGroup  
  
12. Ajouter **autorisé à authentifier** privilège au groupe ORCH\SSOAdminGroup.  
  
13. Créez le compte de connexion suivant sur la base de données SQL2 :  
  
    -   ORCH\SSOAdminGroup  
  
14. Installez le serveur de secret principal comme suit :  
  
    -   Ouvrez une session sur NTS5 à l'aide de ORCH\TestAdmin.  
  
    -   Installez l'authentification unique de l'entreprise en utilisant SQL2 en tant que serveur de secret principal.  
  
15. Ouvrez une session sur HIS1 à l'aide de ORCH\TestAdmin, puis installez l'authentification unique de l'entreprise. Configurez l'authentification unique de l'entreprise en tant qu'ajout SSO à HIS2 en utilisant le nom du serveur de base de données SQL2.  
  
16. Installez l'utilitaire d'administration de l'authentification unique de l'entreprise sur HIS3 à l'aide de ORCH\TestAdmin.  
  
17. Ajoutez les utilisateurs suivants aux groupes suivants :  
  
    -   Ajoutez ORCH\TestAppUser à ORCH\SSOAdminGroup.  
  
    -   Ajoutez ORCH\AffAppUser à ORCH\TestAffUserGroup.  
  
18. Installez SQL Server Enterprise Edition sur HIS3, puis ajoutez le compte de connexion ORCH\AffAppUser.  
  
19. Sur l'ordinateur HIS1, ouvrez une invite de commandes et utilisez les commandes suivantes pour définir la délégation contrainte et la transition de protocole :  
  
    -   **setspn-a MSSQLSvc/HIS3.ORCH.com:1433 ORCH\SSOSvcUser**  
  
    -   **setspn-a MSSQLSvc/HIS3.ORCH.com:1433 ORCH\TestAppUser**  
  
20. Sur le **ORCH\SSOSvcUser** et **ORCH\TestAppUser** pages de propriétés, définissez la délégation appropriée pour les deux comptes d’utilisateur en sélectionnant les options suivantes :  
  
    -   **N’approuver cet utilisateur pour la délégation aux services spécifiés uniquement**  
  
    -   **Utiliser tout protocole d’authentification**  
  
21. À l'aide de ORCH\TestAdmin sur l'ordinateur HIS1, procédez comme suit :  
  
    -   Ajoutez ORCH\TestAppUser au groupe d'utilisateurs du bureau distant.  
  
    -   Grant **emprunter l’identité d’une fois authentifié** privilège à orch\ssosvcuser.  
  
    -   Grant **emprunter l’identité d’une fois authentifié** privilège à orch\testappuser.  
  
22. Vérifiez votre déploiement en ouvrant une session sur HIS1 à l'aide de ORCH\TestAppUser et en exécutant la configuration d'application suivante :  
  
     Exécutez le test LogonExternalUser.  
  
    ```  
    <SSO>  
       <application name="TestApp">  
          <description>An SSO Test Affiliate Application</description>  
          <contact>AffAppUser@ESSOV2.EBiz.Com</contact>  
          <appUserAccount>ORCH\TestAffAdminGroup</appUserAccount>  
          <appAdminAccount>ORCH\TestAffUserGroup</appAdminAccount>  
          <field ordinal="0" label="User ID" masked="no" />  
          <field ordinal="1" label="Password" masked="yes" />  
          <flags   
             groupApp="no"   
             configStoreApp="no"   
             allowTickets="no"   
             validateTickets="yes"   
             allowLocalGroups="yes"   
             ticketTimeout="yes"   
             adminGroupSame="no"   
             enableApp="yes"   
             hostInitiatedSSO="yes"   
             validatePassword="yes"/>  
       </application>  
    </SSO>  
  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble du déploiement de l’authentification unique](../core/sso-deployment-overview.md)