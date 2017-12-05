---
title: "Étape 3 : Configurer le contrôleur de domaine | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuring, domain controller
- domain controller
ms.assetid: 1c513225-378b-4e57-ba29-7532b6cbcc9a
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5b2c89b3db94ce28376ab988a4342931c6d7dcad
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="step-3-configuring-the-domain-controller"></a>Étape 3 : Configurer le contrôleur de domaine
Cette section décrit comment configurer le contrôleur de domaine dans votre [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] déploiement. Plus précisément, cette section décrit comment installer et configurer [!INCLUDE[btsAD](../../includes/btsad-md.md)] en procédant comme suit :  
  
-   L’installation de DNS et Active Directory  
  
-   Créer les comptes requis  
  
-   Joindre le domaine  
  
## <a name="installing-active-directory-and-dns"></a>L’installation de DNS et Active Directory  
 Utilisez le [!INCLUDE[btsAD](../../includes/btsad-md.md)] Assistant Installation pour simplifier le processus de configuration d’un contrôleur de domaine. Après avoir installé Active Directory, créer une zone de recherche inversée de nom de domaine (DNS). Puis créer et ajouter des ordinateurs hôtes pour les zones de recherche directes et inversées.  
  
## <a name="creating-the-required-accounts"></a>Créer les comptes requis  
 Le tableau suivant fournit des détails sur la façon de créer les groupes de sécurité Global. Créez les éléments suivants **sécurité Global** groupes et les utilisateurs sur le contrôleur de domaine à l’aide de vos propres conventions d’affectation de noms. Par souci de simplicité, les exemples fournis ci-dessous sont utilisés. Ajouter les membres spécifiés dans la liste pour les groupes créés.  
  
 Lorsque vous créez des groupes, sélectionnez **Global** pour l’étendue du groupe et **sécurité** pour le Type de groupe.  
  
|Nom de compte ou groupe|Type| Description|Membres|  
|---------------------------|----------|-----------------|-------------|  
|Administratifs|Utilisateur|Compte d’administrateur local pour tous les ordinateurs BizTalk, contrôleur de domaine et tous les ordinateurs exécutant SQL Server.<br /><br /> Il s’agit d’un compte d’utilisateur de domaine qui est utilisé pour installer des applications (BizTalk Server, [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]et SQL Server) et la configuration de BizTalk Accelerator pour A4SWIFT au moment du design. Vous n’avez pas à disposer de privilèges d’administrateur de domaine pour effectuer l’installation d’A4SWIFT. Le compte d’utilisateur administrateur doit être membre du groupe utilisateurs du domaine, le groupe d’administrateurs BizTalk Server de domaine et du groupe Administrateurs local||  
|SQLSvc|Utilisateur|Compte pour exécuter le service SQL Server||  
|SSOSvc|Utilisateur|Compte pour exécuter le service d’authentification unique (SSO)||  
|HostSvc|Utilisateur|Compte pour le service d’hôte BizTalk en cours d’exécution||  
|IsolatedSvc|Utilisateur|Compte pour exécuter le service BizTalk isolé||  
|BAMSvc|Utilisateur|Requis pour la configuration de BizTalk Server de BAMPortal, BAMAlerts et BAMTools||  
|BRESvc|Utilisateur|Compte pour exécuter le service du Service de mise à jour du moteur de règles||  
|Admins du domaine|Groupe de domaine|Compte de groupe de domaine global pour les administrateurs de domaine||  
|Utilisateurs d'hôtes BizTalk isolés|Groupe de domaine|Groupe de domaine global pour les comptes ayant accès aux hôtes BizTalk isolés (processus hôte s’exécute ne pas sur BizTalk Server, tels que HTTP et SOAP).|\<IsolatedSvc\>, \<HostSvc\>|  
|Administrateurs BizTalk Server|Groupe de domaine|Compte de groupe global de domaine qui dispose des privilèges nécessaires pour effectuer des tâches d’administration inclus dans l’Assistant de Configuration Framework et pour administrer le serveur BizTalk.|\<Admin\>|  
|Utilisateurs d'applications BizTalk|Groupe de domaine|Compte de groupe de domaine global pour les utilisateurs d’applications BizTalk.|\<HostSvc\>|  
|Opérateurs BizTalk Server|Groupe de domaine|Le groupe qui dispose des privilèges nécessaires pour effectuer les tâches requises pour l’exploitation de l’environnement BizTalk Server après l’installation.||  
|SharePoint activé hôtes|Groupe de domaine|Le groupe Windows qui dispose des autorisations pour appeler les services Web de l’adaptateur Windows SharePoint Services.|\<HostSvc\>|  
|Administrateurs SSO|Groupe de domaine|Compte de groupe de domaine global pour les administrateurs SSO.|\<Administrateur\>, \<SSOSvc\>|  
|Administrateurs d'applications associées à authentification unique|Groupe de domaine|Les administrateurs d’applications associées compte du groupe global de domaine pour l’authentification unique|\<Admin\>|  
|Utilisateurs d’A4SWIFT|Groupe de domaine|Compte de groupe global de domaine qui possède les privilèges minimaux nécessaires pour effectuer des tâches de base dans A4SWIFT.|\<HostSvc\>, d’autres utilisateurs du réseau|  
|Administrateurs d’A4SWIFT|Groupe de domaine|Compte de groupe global de domaine qui dispose des privilèges nécessaires pour administrer A4SWIFT.|\<Admin\>|  
  
> [!NOTE]
>  Tous les comptes de groupe doivent être des comptes de sécurité globale et des comptes de domaine non local. Si les comptes de groupe de domaine local (créés à l’aide de net localgroup) sont utilisés, le programme d’installation pour [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] ne peut pas valider spécifique [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] utilisateurs du domaine.  
  
## <a name="joining-the-domain"></a>Joindre le domaine  
 Après avoir créé le domaine et les contrôleurs de domaine ont redémarré, joignez chaque serveur au domaine.