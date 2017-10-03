---
title: "Instructions pour l’implémentation des autorisations Active Directory sur les Installations BizTalk multiserveur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 315e25c4-b21d-4b5f-a1d2-1e2777b57f9e
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c0f6f5cb6403c752b18cbfb1c4370cbe3ca95e65
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="guidelines-for-implementing-active-directory-permissions-on-multi-server-biztalk-installations"></a>Instructions pour l'implémentation des autorisations Active Directory sur des installations BizTalk multiserveur
Cette rubrique décrit la procédure de création des unités d'organisation Active Directory, constituées des comptes d'utilisateur et des groupes d'utilisateurs à utiliser dans une installation Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
 Les comptes créés ici ne nécessitent pas d'autorisations autres que celles dont disposent déjà les utilisateurs ordinaires. Des privilèges élevés peuvent être requis pour les comptes de domaine dans la limite de confiance qui inclut :  
  
-   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]  
  
-   Microsoft [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] (sur le serveur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)])  
  
-   Microsoft [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]  
  
-   Base de données externe 1  
  
-   Base de données externe 2  
  
-   Base de données externe *N*  
  
 Par exemple, un compte de domaine peut requérir des autorisations pour réaliser certaines actions sur les systèmes hébergeant les bases de données externes. Dans d'autres cas, il peut être nécessaire d'accorder un accès en écriture à un compte pour qu'il puisse écrire dans le fichier d'un dossier de dépôt.  
  
 Utilisez le **Active Directory Users and Computers** console pour créer et gérer des comptes d’utilisateur et de groupe de domaine. Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **outils d’administration**, puis cliquez sur **Active Directory Users and Computers** à Démarrer le **Active Directory Users and Computers** console.  
  
## <a name="biztalk-server-installation-and-configuration-account"></a>Installation de BizTalk Server et compte de configuration  
 Dans l'environnement de développement, vous devez avoir recours à un compte doté de droits d'administrateur sur les systèmes [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour pouvoir exécuter le programme d'installation de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et l'Assistant Configuration de [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]. Il est possible de révoquer ces droits ou de désactiver le compte une fois l'installation et la configuration terminées. Le compte doit également appartenir à plusieurs groupes BizTalk présentés dans les sections ci-après.  
  
> [!NOTE]
>  Vous ne pourrez pas configurer les composants SSO si le compte utilisé pour l'installation appartient à une forêt Active Directory différente du serveur. Si vous ne disposez pas d'un compte d'installation [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], utilisez un compte d'administrateur local pour la configuration de SSO. Cette méthode peut impliquer certaines difficultés lors de l'installation, comme le besoin de fournir des informations d'identification différentes pour la connexion aux ressources.  
  
## <a name="biztalk-server-development-accounts"></a>Comptes de développement BizTalk Server  
 Toute personne opérant dans l'environnement de développement de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] a besoin d'un accès aux adaptateurs, aux gestionnaires de réception et d'envoi, ainsi qu'aux emplacements de réception. Cet accès requiert que le groupe de développeurs de domaine qui seront membres de la **administrateurs de BizTalk Server** et **administrateurs d’applications associées à authentification unique** groupes.  
  
> [!NOTE]
>  Active Directory comporte certaines limitations concernant les types de groupes pouvant contenir des utilisateurs de domaines étrangers et ceux pouvant être contenus dans d'autres groupes. Les groupes et comptes créés ci-dessous sont testés dans un environnement multiserveur sur un domaine unique.  
  
## <a name="biztalk-server-deployment-accounts"></a>Comptes de déploiement BizTalk Server  
 Toute personne déployant des applications [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] doit disposer de droits d'administrateur sur les systèmes locaux. D'autres autorisations peuvent par ailleurs se révéler nécessaires dans l'environnement. Un compte de déploiement BizTalk Server est présenté dans cette rubrique à cette fin.  
  
 Cet accès requiert que le groupe de déploiement de domaine qui seront membres de la **administrateurs de BizTalk Server** et **administrateurs d’applications associées à authentification unique** groupes.  
  
> [!NOTE]
>  Vous ne pourrez pas configurer les composants SSO si le compte utilisé pour l'installation appartient à une forêt Active Directory différente du serveur. Si vous ne disposez pas d'un compte de déploiement BizTalk Server, utilisez un compte d'administrateur local pour la configuration de SSO. Cette méthode peut impliquer certaines difficultés lors de l'installation, comme le besoin de fournir des informations d'identification différentes pour la connexion aux ressources.  
  
## <a name="biztalk-server-support-accounts"></a>Comptes de support BizTalk Server  
 Toute personne gérant le support des applications [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] doit disposer de droits d'administrateur sur les systèmes locaux. Un compte de support BizTalk sera présenté dans cette rubrique.  
  
 Cet accès requiert que le groupe de support de domaine qui seront membres de la **administrateurs de BizTalk Server** groupe.  
  
## <a name="sql-server-service-accounts"></a>Comptes de service SQL Server  
 Le service exécutant l'instance [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] doit appartenir au même domaine Active Directory que les comptes chargés de l'installation, du développement et du déploiement des composants [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
-   Utilisez **SQLAdmin** pour les fonctions d’administration (ouverture de session interactive).  
  
-   Utilisez **SQLService** pour gérer le service (aucune ouverture de session interactive).  
  
-   Utilisez **SQLAccess** pour accéder aux bases de données externes.  
  
-   SQLAdmin doit appartenir au groupe Administrateurs locaux sur le système [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)].  
  
-   SQLService doit être membre du groupe Administrateurs local sur le [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] système et doit se voir accorder le **ouvrir une session en tant que service** droit d’utilisateur.  
  
-   SQLAccess requiert les droits appropriés sur les serveurs de bases de données distants.  
  
 **Comptes SQL :**  
  
|**Nom d'utilisateur**|**First Name**|**Last Name**|**Nom complet**|  
|-------------------|--------------------|-------------------|-------------------|  
|SQLService|SQL|SQLService|Compte de service SQL|  
|SQLAdmin|Administratifs|SQLService|Compte administrateur SQL|  
|SQLAccess|Accès|SQLService|Compte d'accès SQL|  
  
 Définissez les mots de passe de compte en fonction des exigences de l'entreprise.  
  
> [!IMPORTANT]
>  Sur l'ordinateur exécutant [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)], modifiez les paramètres de démarrage des services SQL Server et SQLServerAgent de sorte à utiliser le compte SQLService et ses informations d'identification.  
  
> [!NOTE]
>  Les données entrées dans les champs Nom d'utilisateur sont des exemples. Vous pouvez les modifier afin d'éviter tout conflit avec d'autres comptes Active Directory.  
  
## <a name="windows-sharepoint-services-account"></a>Compte des services Windows SharePoint Services  
 Les comptes des services Windows SharePoint Services doivent être créés avant l'installation de [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)].  
  
 Recommandations et remarques sur le compte [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] :  
  
-   Utilisez le compte d'administrateur SharePoint (SPAdmin) pour les fonctions d'administration, le service du minuteur SharePoint et tous les accès à [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)].  
  
-   SPAdmin est le propriétaire du site et un alias de messagerie est requis.  
  
-   SPAdmin doit être membre du groupe Administrateurs locaux sur l'ordinateur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] local (opération effectuée lors de l'installation de Windows SharePoint Services).  
  
-   SPAdmin doit être associé aux rôles Administrateur de la sécurité et Créateur de bases de données sur l'ordinateur [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] (opération effectuée lors de l'installation de Windows SharePoint Services).  
  
 **Comptes SharePoint :**  
  
|**Nom d'utilisateur**|**First Name**|**Last Name**|**Nom complet**|  
|-------------------|--------------------|-------------------|-------------------|  
|SPAdmin|Administratifs|SPService|Compte d'administrateur Sharepoint|  
  
 Définissez les mots de passe des comptes en fonction des exigences de l'entreprise et soyez prêt à récupérer ces mots de passe lors des étapes de configuration. Reportez-vous à la **des mots de passe** section de cette rubrique pour les problèmes concernant les mots de passe générés.  
  
> [!NOTE]
>  Les informations entrées dans le champ Nom d'utilisateur sont données à titre d'exemple. Vous pouvez les modifier afin de protéger d'autres comptes Active Directory.  
  
> [!IMPORTANT]
>  Après avoir installé les services Windows SharePoint Services sur l'ordinateur exécutant [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], vérifiez que les paramètres de démarrage du service du minuteur SharePoint utilisent bien les informations d'identification et le compte SPAdmin.  
  
## <a name="biztalk-groups-and-users"></a>Utilisateurs et groupes BizTalk  
 Vous devez créer les groupes et les utilisateurs de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] avant d'exécuter l'Assistant Configuration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Dans une installation monosystème, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] utilise les comptes et groupes locaux créés lors de la configuration. Toutefois, si vous déployez des hôtes [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] distincts ou si vous installez [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] sur deux ordinateurs différents, vous devez utiliser les comptes de groupe et d'utilisateur du domaine.  
  
> [!NOTE]
>  L'Assistant Configuration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] n'est pas capable de créer des comptes de domaine.  
  
 Recommandations et remarques sur les comptes d'utilisateur et de service de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :  
  
-   Créez une unité d'organisation pour [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Tous les comptes et groupes appartiendront à cette unité.  
  
-   Soyez précis et attribuez des noms complets. Les noms figurant dans les listes ci-après doivent être suffisamment clairs pour permettre au programme d'installation de sélectionner les groupes/comptes/utilisateurs appropriés lors de la configuration.  
  
-   Les prénom et nom sont facultatifs et ne sont inclus que pour des raisons de cohérence.  
  
-   Le différentiateur **BTService** et **BTUser** fait référence à des comptes de service (automates) et les utilisateurs génériques/partagés.  
  
-   Créez des comptes de domaine et renseignez-les par le biais d'un script ADSI réservé à la création de comptes de groupes et d'utilisateurs dans les environnements parents.  
  
 **Comptes de Service BizTalk**  
  
|**Nom d'utilisateur**|**First Name**|**Last Name**|**Nom complet**|  
|-------------------|--------------------|-------------------|-------------------|  
|BTService|BTS|BTService|Compte de Service BizTalk|  
|BTServiceHost|Hôte|BTService|Compte de l'instance de l'hôte BizTalk|  
|BTServiceHostIso|HostIso|BTService|Compte de l'instance de l'hôte BizTalk isolé|  
|SSOService|AUTHENTIFICATION UNIQUE|BTService|Service d'authentification unique de l'entreprise|  
|BTServiceREU|REU|BTService|Service de mise à jour du moteur des règles|  
  
 Définissez les noms d'utilisateur en fonction des exigences de l'entreprise et de l'environnement (par exemple, devBTService, alphaBTService). Définir des mots de passe en fonction des normes de l’entreprise et être en mesure de les récupérer pour les étapes de configuration. Reportez-vous à la **considérations de mot de passe pour le développement** section de cette rubrique pour les problèmes concernant les mots de passe générés.  
  
 Le programme d'installation remarque la précision des comptes de service, et les services créés par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] font tous l'objet d'un mappage. La granularité permet à la sécurité informatique de l'entreprise d'effectuer un suivi des accès et de les restreindre en fonction des besoins. Bien que recommandée, la décision de l'utiliser dans l'environnement de l'entreprise revient entièrement au personnel chargé de la sécurité et au concepteur de systèmes.  
  
 Les comptes de service du groupe précédent sont destinés aux accès de l'automate uniquement, pas aux ouvertures de session interactives réservées aux utilisateurs.  
  
#### <a name="to-set-the-appropriate-account-options"></a>Pour définir les options de compte appropriées  
  
1.  Dans le **Active Directory Users and Computers** de la console, développez le domaine, puis cliquez sur pour développer le **utilisateurs** conteneur.  
  
2.  Cliquez sur le compte, puis sélectionnez **propriétés** pour afficher les **propriétés** boîte de dialogue pour le compte.  
  
3.  Cliquez sur le **compte** onglet de la **propriétés** boîte de dialogue.  
  
4.  Cliquez sur les options suivantes pour les activer :  
  
    -   **Utilisateur ne peut pas changer de mot de passe** (sécurité de l’entreprise modifier les mots de passe).  
  
    -   **Mot de passe n’expire jamais**  
  
5.  Cliquez sur le **se connecter à** bouton pour afficher la **stations de travail d’ouverture de session** boîte de dialogue.  
  
6.  Cliquez sur l’option pour **les ordinateurs suivants**, ajoutez chaque ordinateur exécutant [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)], puis cliquez sur **OK**.  
  
7.  Cliquez sur le **contrôle à distance** onglet de la **propriétés** boîte de dialogue, puis cliquez pour désactiver l’option pour **activer le contrôle à distance**.  
  
8.  Cliquez sur le **profil des Services Terminal Server** onglet de la **propriétés** boîte de dialogue.  
  
9. Cochez l’option à **interdire cet utilisateur pour vous connecter à n’importe quel serveur Terminal Server**.  
  
10. Cliquez sur **OK** pour fermer la **propriétés** boîte de dialogue pour le compte.  
  
11. Reprenez les étapes 3 à 10 pour chaque compte de service.  
  
 **Comptes d’utilisateur BizTalk**  
  
|**Nom d'utilisateur**|**First Name**|**Last Name**|**Nom complet**|  
|-------------------|--------------------|-------------------|-------------------|  
|BTUserAdmin|Administratifs|BTUser|Compte d'utilisateur administratif BizTalk|  
|BTUserDeploy|Déployer|BTUser|Compte d'utilisateur de déploiement BizTalk|  
|BTUserHostInstance|HostInstance|BTUser|Compte de l'instance de l'hôte BizTalk|  
|BTUserHostIsolated|IsolatedlHost|BTUser|Compte de l'instance de l'hôte BizTalk isolé|  
|BTUserInstall|Install|BTUser|Compte d'utilisateur d'installation BizTalk|  
|BTUserSupport|Support technique|BTUser|Compte d'accès de support BizTalk|  
  
#### <a name="to-set-the-appropriate-account-options-follow-these-steps"></a>Pour définir le compte approprié options, procédez comme suit  
  
1.  Dans le **Active Directory Users and Computers** cliquez pour développer le domaine de la console, puis cliquez sur pour développer le **utilisateurs** conteneur.  
  
2.  Cliquez sur le compte, puis sélectionnez **propriétés** pour afficher les **propriétés** boîte de dialogue pour le compte.  
  
3.  Cliquez sur le **compte** onglet de la **propriétés** boîte de dialogue.  
  
4.  Cliquez sur les options suivantes pour les activer :  
  
    -   **Utilisateur ne peut pas changer de mot de passe** (sécurité de l’entreprise modifier les mots de passe).  
  
    -   **Mot de passe n’expire jamais**  
  
5.  Cliquez sur le **se connecter à** bouton pour afficher la **stations de travail d’ouverture de session** boîte de dialogue.  
  
6.  Cliquez sur l’option pour **les ordinateurs suivants**, ajoutez chaque ordinateur exécutant [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)], puis cliquez sur **OK**.  
  
7.  Cliquez sur le **contrôle à distance** onglet de la **propriétés** boîte de dialogue, puis cliquez sur l’option à **activer le contrôle à distance**.  
  
8.  Cliquez sur le **profil des Services Terminal Server** onglet de la **propriétés** boîte de dialogue.  
  
9. Désactivez l’option à **interdire cet utilisateur pour vous connecter à n’importe quel serveur Terminal Server**.  
  
10. Cliquez sur **OK** pour fermer la **propriétés** boîte de dialogue pour le compte.  
  
11. Reprenez les étapes 3 à 10 pour chaque compte d'utilisateur.  
  
    > [!NOTE]
    >  Vous pouvez désactiver n'importe lequel de ces comptes si les rôles auxquels ils sont associés sont attribués à des utilisateurs réels. Dans les premières phases des versions 1 et  2, ces comptes sont utilisés dans les environnements de développement, de tests alpha et bêta.  
  
 **Comptes de groupe BizTalk**  
  
|**Nom du groupe**|**Type de groupe**|**Membres**|  
|--------------------|--------------------|-----------------|  
|Utilisateurs d'applications BizTalk|Global ou universel|-BTServiceHost<br />-BTUserHostInstance|  
|Utilisateurs de développement BizTalk|Global ou universel|(comptes de domaine locaux d’utilisateurs de développement) **Remarque :** en tant que meilleure pratique, n’activez pas le groupe d’utilisateurs de développement BizTalk dans les environnements parents.|  
|Utilisateurs du déploiement BizTalk|Global ou universel|(comptes locaux et de domaine des utilisateurs du déploiement)|  
|Utilisateurs hôtes BizTalk|Global ou universel|BTUserHostInstance|  
|Utilisateurs d'hôtes BizTalk isolés|Global ou universel|-BTServiceHostIso<br />-BTUserHostInstance|  
|Administrateurs BizTalk Server|Global ou universel|-BTUserAdmin<br />-BTUserInstall<br />-Utilisateurs de développement de BizTalk<br />-Les utilisateurs du déploiement de BizTalk|  
|Utilisateurs de support BizTalk|Global ou universel|BTUserSupport (comptes locaux et de domaine d'utilisateurs du support)|  
|Administrateurs SSO|Global ou universel|-SSOService<br />-BTUserInstall<br />-Administrateur local|  
|Administrateurs d'applications associées à authentification unique|Global ou universel|-Utilisateurs de développement de BizTalk<br />-Les utilisateurs du déploiement de BizTalk<br />-BTServiceHostIso<br />-   \<utilisateur de la console >|  
|Administrateurs de Windows SharePoint Services|Global ou universel|-SPAdmin<br />-BTUserInstall<br />-BTUserDeploy<br />-Utilisateurs de développement de BizTalk<br />-Les utilisateurs du déploiement de BizTalk|  
  
 Recommandations et remarques sur les groupes de domaine :  
  
-   Créez les groupes et ajoutez-y des membres avant d'installer [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
-   Les groupes de domaine peuvent être des groupes globaux ou universels.  
  
-   Utilisez  *\<nom_domaine >\\< nom d’utilisateur\>*  lors de la spécification des informations de compte de domaine dans l’Assistant Configuration.  
  
-   Les comptes de groupes et d'utilisateurs/de service doivent appartenir au même domaine que l'ordinateur exécutant [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] (ce point est vérifié par l'Assistant Configuration qui n'affichera pas les comptes ou groupes contenant des comptes d'autres domaines).  
  
-   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] nécessite des comptes de domaine pour tous les scénarios de mise en cluster.  
  
-   Lors de l'installation de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], l'utilisateur de la console doit être membre des groupes suivants :  
  
    -   Administrateurs BizTalk Server  
  
    -   Administrateurs de l'authentification unique (pour la configuration du serveur de secret principal exclusivement)  
  
    -   Administrateur Windows  
  
    -   Administrateur de [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]  
  
    -   Administrateur OLAP  
  
     Le compte BTUserInstall doit être utilisé pour l'installation et la configuration, et doit être désactivé une fois la configuration terminée.  
  
-   Pour permettre les événements de message et le suivi d’instance service pour attacher des orchestrations au débogueur, le développeur doit appartenir au groupe Administrateurs de BizTalk Server, comme indiqué plus haut dans la section **comptes de développement BizTalk** .  
  
## <a name="local-administrator-accounts"></a>Comptes des administrateurs locaux  
 Vérifiez ou ajoutez les comptes et groupes suivants au groupe Administrateurs local sur l'ordinateur [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] :  
  
-   Domaine\BTUserInstall (désactivé à la fin de la configuration)  
  
-   Domaine\BTUserDeploy (désactivé dans l'environnement de production à la fin du déploiement)  
  
-   Domaine\SPAdmin  
  
-   Domaine\SQLAdmin  
  
-   Domaine\SQLService  
  
-   Domaine\utilisateurs de développement (à omettre dans les environnements de ligne)  
  
-   Domaine\Utilisateurs de déploiement BizTalk (à omettre dans les environnements de développement)  
  
 Vérifiez ou ajoutez les comptes et groupes suivants au groupe Administrateurs local sur l'ordinateur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :  
  
-   Domaine\BTUserInstall (désactivé à la fin de la configuration)  
  
-   Domaine\BTUserDeploy (désactivé dans l'environnement de production à la fin du déploiement)  
  
-   Domaine\BTUserSupport  
  
-   Domaine\SPAdmin  
  
-   Domaine\Utilisateurs de développement BizTalk (à omettre dans les environnements parents)  
  
-   Domaine\Utilisateurs de déploiement BizTalk (à omettre dans les environnements de développement)  
  
## <a name="sql-server-administrator-accounts"></a>Comptes des administrateurs de SQL Server  
 Il est possible d'effectuer des saisies dans les programmes d'installation et ces derniers peuvent attribuer des rôles SQL aux utilisateurs et aux groupes :  
  
-   Lors de l'installation de [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)], le compte SPAdmin reçoit les droits Administrateur de la sécurité et Créateur de bases de données sur l'ordinateur [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]. Ces droits peuvent être supprimés si le compte SPAdmin est membre du groupe Administrateurs locaux.  
  
## <a name="e-mail-account"></a>Compte de messagerie  
 [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] envoie des messages en fonction de certains événements système. Le programme d'installation vous invite à entrer une adresse de messagerie lors de la configuration. Créez à cette fin des alias de messagerie et surveillez-les lors de l'installation et du test unitaire. Dans l'environnement de production, l'administrateur système en charge de la surveillance du système doit être en mesure d'accéder à ce compte.  
  
 Le compte de messagerie utilisé par [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] est la **par courrier électronique de l’administrateur WSS** compte.  
  
## <a name="password-considerations-for-development"></a>Observations sur les mots de passe dans l'environnement de développement  
 Dans les environnements de développement et de test, il est possible de définir les mots de passe des comptes en fonction de standards communs et de les distribuer. Les standards utilisés par le programme d'installation varient. Cette rubrique présente le modèle suivant : initiales en majuscules désignant le composant de service, suivies du reste du compte abrégé en minuscules (service ou utilisateur). Pour les comptes de service, cette rubrique utilise 'Serv', et pour les comptes d'utilisateur, elle utilise 'User'.  
  
 Exemple :  
  
-   Windows SharePoint Services (SharePoint) Service et administration (SPAdmin) mots de passe : 'SPServ'.  
  
-   Mots de passe de compte BizTalk Service : 'BTServ'.  
  
-   Mots de passe utilisateur BizTalk : 'BTUser'.  
  
 Dans certains environnements informatiques, les mots de passe doivent contenir des caractères non alpha et/ou numériques. Dans ce cas, vous pourriez substituer le signe $ à « s », et l'arobas (@) à « a ». Les symboles donnés sont des exemples. Trouvez le modèle qui correspond le mieux à vos besoins en matière de comptes partagés avec des mots de passe semi-publics.  
  
 Voici des exemples de mot de passe qu'il est possible de distribuer dans l'environnement de développement :  
  
-   BT$erv99           Comptes de service BizTalk  
  
-   BTU$er99          Comptes d'utilisateur BizTalk  
  
-   SP$erv99           Compte de service WSS (SPAdmin)  
  
-   SQL$erv99         Compte de service/d'administrateur/d'accès SQL  
  
> [!NOTE]
>  Ces recommandations concernent uniquement les environnements de développement et partagés. Elles n'empêchent ni ne conseillent tout particulièrement l'emploi de stratégies de mots de passe d'entreprise. Contactez votre administrateur réseau pour plus d'informations sur les exigences en matière de mots de passe.  
  
> [!NOTE]
>  Si la stratégie de mots de passe de votre entreprise inclut des mots de passe générés, gardez à l'esprit que certains symboles et combinaisons de symboles constituent des caractères spéciaux pour XML. Une utilisation inappropriée de ces caractères peut empêcher l'ouverture des fichiers XML de configuration lors du processus de configuration. Ces symboles incluent « & », «\<», « > », simple et double guillemet, entre autres. Testez le fichier XML de configuration avant d'exécuter la configuration basée sur ces fichiers. Pour ce faire, ouvrez le document, avec les mots de passe générés, dans Internet Explorer (ou un éditeur XML).  
  
 Pour plus d’informations sur le déploiement de mots de passe sécurisés dans les environnements parents (y compris la méthode pour tester un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] fichier de configuration), consultez [vue d’ensemble de la Configuration de BizTalk Server 2013 et 2013 R2](http://msdn.microsoft.com/library/aa58c43f-8f0e-4a5c-89b9-db7b8a852a72).  
  
## <a name="see-also"></a>Voir aussi  
 [Résolution des problèmes d’autorisations BizTalk Server](../core/troubleshooting-biztalk-server-permissions.md)