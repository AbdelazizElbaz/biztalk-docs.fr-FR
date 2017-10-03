---
title: "Configurer à l’aide de la configuration de base ou personnalisés | Documents Microsoft"
description: "Étapes pour effectuer une configuration de base ou personnalisée de BizTalk Server et pour savoir ce qui se passe avec chaque configuration"
ms.custom: 
ms.date: 08/14/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 861a1237-d77a-42db-b563-d83f7930add6
caps.latest.revision: "26"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f8989fd322fd9fc34e947a80b510619446a65f71
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configure-biztalk-server"></a>Configuration de BizTalk Server
Configurez [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] à l’aide d’une configuration de base ou d’une configuration personnalisée.

## <a name="basic-configuration-vs-custom-configuration"></a>Configuration de base / Configuration personnalisée

* Si votre configuration utilise des groupes de domaine, utilisez une configuration personnalisée.
* Si votre configuration utilise des noms de groupes personnalisés à la place des noms de groupes par défaut, utilisez une configuration personnalisée.
* Si votre configuration utilise des noms de bases de données personnalisés à la place des noms de bases de données par défaut, utilisez une configuration personnalisée.
* Si [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et SQL Server se trouvent sur des ordinateurs distincts, des groupes de domaines sont requis. De ce fait, utilisez une configuration personnalisée.
* Vous ne pouvez pas configurer l’analyse BAM sur une instance nommée de SQL Server en utilisant la configuration de base. Si vous utilisez des instances nommées et souhaitez configurer l’analyse BAM, utilisez une configuration personnalisée.
* La configuration de base est recommandée pour les utilisateurs qui configurent une installation complète de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et SQL Server sur un seul serveur.
* La configuration de base est plus rapide car elle crée automatiquement les groupes locaux et les bases de données à l'aide des noms par défaut.


## <a name="before-you-begin"></a>Avant de commencer
* [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] peut être configuré à l’aide d’instances par défaut et d’instances nommées de SQL Server. 
* Le compte avec lequel vous vous connectez doit être membre du groupe des administrateurs locaux et disposer de droits d’administrateur système sur SQL Server.
* Si vous utilisez des groupes de domaines, ceux-ci doivent exister *avant* la configuration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].
* Les comptes par défaut générés par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et répertoriés dans la configuration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sont des groupes locaux. Dans un environnement multiserveur, remplacez les groupes locaux par des groupes de domaines.
* Si vous configurez des services d’analyse BAM, le compte avec lequel vous avez ouvert une session doit être membre du groupe Administrateurs OLAP sur l’ordinateur OLAP.


## <a name="basic-configuration"></a>Configuration de base

1. Dans le menu Démarrer, cliquez avec le bouton droit sur **Configuration de BizTalk Server**, puis sélectionnez **Exécuter en tant qu’administrateur**. Cela ouvre l’Assistant Configuration. 
2. Sélectionnez les options suivantes : 
    1. Sélectionnez **Configuration de base**.
    2. Le **nom du serveur de base de données** indique automatiquement par défaut le nom de l’ordinateur local.   
    3. Entrez le **nom d’utilisateur** et le **mot de passe** du compte sous lequel les services BizTalk s’exécuteront. Comme bonne pratique, créez un compte unique. N’utilisez pas votre nom d’utilisateur personnel.  
        ![bts2016BasicConfig](../install-and-config-guides/media/bts2016basicconfig.gif)  
    Si vous entrez un nom d’utilisateur disposant d’informations d’identification d’administration sur cet ordinateur, vous recevez un avertissement. Ceci est normal. Sélectionnez **OK** pour continuer.
    
3. Sélectionnez **Configurer**.
4. Passez en revue les détails de configuration, puis sélectionnez **Suivant**.
5. Une fois l’Assistant Configuration terminé, sélectionnez **Terminer**.

Un fichier journal de configuration est généré dans un dossier temporaire, similaire à : `
C:\Users\username\AppData\Local\Temp\ConfigLog(01-12-2017 0h37m59s).log`.

Lorsque vous utilisez une configuration de base, voici ce qui se produit :

- Tous les noms de bases de données sont générés automatiquement par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].
- Toutes les informations de connexion à la base de données sont exécutées sous le compte spécifié. 
- Tous les services BizTalk sont générés automatiquement par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].
- Tous les services BizTalk s’exécutent sous le compte spécifié. Le processus de configuration dote ce compte des autorisations de sécurité nécessaires sur le serveur et les objets SQL Server.
- Toutes les fonctionnalités sont configurées en fonction des logiciels prérequis que vous avez installés sur l’ordinateur.
- Les groupes sont créés automatiquement localement sur l’ordinateur à l’aide des noms par défaut.
- Le site Web par défaut dans Internet Information Services (IIS) est utilisé pour toute fonctionnalité qui nécessite IIS.

## <a name="custom-configuration"></a>Configuration personnalisée
  
1. Dans le menu Démarrer, cliquez avec le bouton droit sur **Configuration de BizTalk Server**, puis sélectionnez **Exécuter en tant qu’administrateur**. Cela ouvre l’Assistant Configuration.
2. Sélectionnez **Configuration personnalisée**, puis **Configurer**.

### <a name="configure-enterprise-single-sign-on-sso"></a>Configuration de l’authentification unique (SSO) de l’entreprise

* Lorsque l’authentification unique (SSO) est configurée, elle ne peut pas être reconfigurée à l’aide de la configuration de BizTalk Server. Pour reconfigurer l’authentification unique, utilisez Administration de BizTalk Server.
* Lorsque vous configurez les comptes Windows SSO à l’aide de comptes locaux, ne spécifiez que le nom du compte. N’entrez pas le nom de l’ordinateur.
* Lorsque vous utilisez une instance nommée SQL Server locale comme magasin de données, utilisez `LocalMachineName\InstanceName`. N’utilisez pas `LocalMachineName\InstanceName, PortNumber`. 

1. Sélectionnez **SSO de l’entreprise**.
2. Configurez les éléments suivants :

    | Utilisez ceci | Pour effectuer cette opération |
    | --- | --- |
    |Activer l'authentification unique de l'entreprise sur cet ordinateur | Configurer ce serveur avec les paramètres d’authentification unique. |
    |Créer un nouveau système SSO | S’il s’agit du premier serveur SSO que vous configurez, sélectionnez cette option. Cela crée et configure la base de données SSO, crée le secret principal (une clé de sécurité chiffrée) et installe les services utilisés par SSO. Vous devez sauvegarder le secret sur ce serveur de secret.<br/><br/>Détails clés : <br/><ul><li>Il est recommandé de configurer le serveur de secret principal comme serveur autonome.</li><li>Seul un administrateur SSO peut effectuer cette tâche de configuration.</li><li>Un serveur de secret principal ne peut être associé qu'à un seul groupe BizTalk. L'association de deux serveurs de secret principal au même groupe BizTalk n'est pas prise en charge.</li></ul>|
    |Joindre un système SSO existant | Si vous ajoutez un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] à un groupe existant, sélectionnez cette option. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] partage les mêmes bases de données et configuration SSO avec les autres serveurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] du groupe. |
    |Banques de données | Entrez le nom de serveur de votre serveur SSO. Si vous êtes sur le serveur SSO, sélectionnez le nom du serveur local. Vous pouvez conserver **SSODB** comme nom de base de données par défaut ou entrer un nom personnalisé.|
    |Service Windows| Entrez le compte utilisé pour exécuter le service d’authentification unique de l’entreprise. Si SQL Server est sur un autre ordinateur, entrez le compte de domaine. |
    |Comptes Windows|Vous pouvez conserver les noms de groupes par défaut ou entrer des noms personnalisés. Si SQL Server est sur un autre ordinateur, entrez les comptes de domaine. |

3. Sélectionnez **Sauvegarde du secret SSO de l’entreprise**. Cette option enregistre le secret principal dans un fichier de sauvegarde chiffré. 
4. Configurez les éléments suivants :  

    |Utilisez ceci|Pour effectuer cette opération|
    | --- | --- |
    |Mot de passe de sauvegarde secrète | Entrer le mot de passe secret principal.|
    |Confirmer le mot de passe|Entrer de nouveau le mot de passe secret principal.|
    |Rappel de mot de passe|Tapez un rappel pour le mot de passe entré. Sérieusement, n’ignorez pas cette étape. |
    |Emplacement du fichier de sauvegarde|Répertorie le nom de fichier et l’emplacement de sauvegarde. Par défaut, ce fichier est conservé sous \Program Files\Common Files\Enterprise Single Sign-On\ *nom_de_fichier*.bak.|

Sauvegardez **TOUJOURS** le secret principal et partagez le mot de passe avec un autre administrateur BizTalk.
    
### <a name="configure-groups"></a>Configuration de groupes

* Lorsque vous utilisez une instance nommée SQL Server locale comme magasin de données, utilisez `LocalMachineName\InstanceName`. N’utilisez pas `LocalMachineName\InstanceName, PortNumber`.

1. Sélectionnez **Groupe**.
2. Configurez les éléments suivants :

    |Utilisez ceci|Pour effectuer cette opération|
    | --- | --- |
    |Activer le groupe BizTalk Server sur cet ordinateur|Sélectionnez cette option pour créer un groupe BizTalk sur ce serveur ou joindre un groupe existant. |
    |Créer un groupe BizTalk| S’il s’agit du premier serveur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dans le groupe, sélectionnez cette option. Vous utilisez cette option pour créer les bases de données et ajouter les groupes.|
    |Joindre un groupe BizTalk existant| Si vous joignez ce serveur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] à un groupe existant, sélectionnez cette option.|
    |Créer une base de données d'analyse pour le suivi des agrégations|Sélectionnez cette option pour installer SQL Server Analysis Services, si vous souhaitez suivre et stocker les cubes OLAP de contrôle d’intégrité.|
    |Banques de données| Entrez le nom du serveur qui héberge vos bases de données BizTalk. Si BizTalk et SQL sont tous les deux installés sur ce serveur, entrez le nom du serveur local. Si SQL Server figure sur un autre ordinateur, entrez le nom du serveur SQL Server.<br/><br/>Vous pouvez conserver les noms de bases de données par défaut ou entrer des noms personnalisés.|
    |Rôles d'administration BizTalk|Vous pouvez conserver les noms de groupes par défaut ou entrer des noms personnalisés. Si SQL Server est sur un autre ordinateur, entrez les comptes de domaine.|

### <a name="configure-the-biztalk-runtime"></a>Configuration du moteur d’exécution BizTalk

* Une fois que le moteur d’exécution est configuré, il ne peut pas être reconfiguré à l’aide de la configuration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Pour reconfigurer le moteur d’exécution, utilisez Administration [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].
* Le premier hôte que vous créez au sein du groupe doit être un hôte in-process et une instance d’hôte.
* Lorsque vous configurez le moteur d’exécution sur plusieurs serveurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dans le même groupe, le même compte de service ne peut pas être utilisé pour les applications d’hôte approuvées et non approuvées. Vous devez utiliser un compte unique pour l’application approuvée et pour l’application non approuvée. 

1. Sélectionnez **Moteur d’exécution BizTalk**.
2. Configurez les éléments suivants :

    |Utilisez ceci|Pour effectuer cette opération|
    | --- | --- |
    | Enregistrer les composants du moteur d’exécution [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] | Sélectionnez cette option pour créer les hôtes et les instances d’hôte sur ce serveur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. |
    | Créer un hôte et une instance de type In-process | Crée l’hôte et l’instance BizTalkServerApplication sur cet ordinateur.<br/><br/>Options supplémentaires : <ul><li>**Approuvé(e)** : Transmet les informations d’identification (SSID et/ou ID tiers) de l’expéditeur lors du transfert des messages à la base de données MessageBox. Cela revient à créer une relation de confiance entre les serveurs. La plupart des hôtes et des instances ne sont pas approuvés.</li><li>**32 bits seulement** : Certains adaptateurs s’exécutent uniquement dans un processus 32 bits, mais la plupart sont compatibles 64 bits. Ce paramètre peut être activé ou désactivé dans la console Administration de BizTalk, une fois que vous avez configuré BizTalk. Aussi, ne vous inquiétez pas.</li><li>**Nom d’hôte** : BizTalkServerApplication est la valeur par défaut. Si/quand vous créez de nouveaux hôtes et instances dans la console Administration de BizTalk, vous pouvez être spécifique avec les noms, tels que TrackingHost ou ReceivingHost. Laissez-le donc en l’état.</li></ul>|
    | Créer un hôte et une instance isolés| L’hôte isolé s’exécute dans IIS. Dans de nombreux environnements, il est préférable de conserver les valeurs par défaut.<br/><br/>Options supplémentaires : <ul><li>**Approuvé(e)** : Transmet les informations d’identification (SSID et/ou ID tiers) de l’expéditeur lors du transfert des messages à la base de données MessageBox. Cela revient à créer une relation de confiance entre les serveurs. La plupart des hôtes et des instances ne sont pas approuvés.</li><li>**32 bits seulement** : Certains adaptateurs s’exécutent uniquement dans un processus 32 bits, mais la plupart sont compatibles 64 bits. Ce paramètre peut être activé ou désactivé dans la console Administration de BizTalk, une fois que vous avez configuré BizTalk.</li><li>**Nom de l’hôte isolé** : BizTalkServerIsolatedHost est la valeur par défaut. Laissez-la en l’état. </li></ul>|
    |Service Windows| Entrez les comptes utilisés pour exécuter les instances d’hôte. Si SQL Server est sur un autre ordinateur, entrez les comptes de domaine. |
    |Groupes Windows|Vous pouvez conserver les noms de groupes par défaut ou entrer des noms personnalisés. Si SQL Server est sur un autre ordinateur, entrez les comptes de domaine. |


### <a name="configure-business-rules-engine-bre"></a>Configuration du moteur des règles d’entreprise

Si vous n’utilisez pas le moteur des règles d’entreprise, ignorez cette section.

- Il est recommandé de configurer un groupe [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] avant de paramétrer le moteur des règles d’entreprise. Si vous configurez ce dernier avant de configurer un groupe [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], la configuration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] n’ajoute pas de rôles d’administration liés aux groupes dans la base de données du moteur des règles.

1. Sélectionnez **Moteur des règles d’entreprise**.
2. Configurez les éléments suivants :

    |Utilisez ceci|Pour effectuer cette opération|
    | --- | --- |
    |Activer le moteur des règles d’entreprise sur cet ordinateur | Si vous utilisez le moteur des règles d’entreprise sur ce serveur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], sélectionnez cette option. |
    |Banques de données| Entrez le nom du serveur qui héberge votre base de données de règles. Si BizTalk et SQL sont tous les deux installés sur ce serveur, entrez le nom du serveur local. Si SQL Server figure sur un autre ordinateur, entrez le nom du serveur SQL Server.<br/><br/>Vous pouvez conserver le nom de base de données par défaut ou entrer un nom personnalisé.|
    |Service Windows| Entrez les comptes utilisés pour exécuter le service de mise à jour des règles. Si SQL Server est sur un autre ordinateur, entrez le compte de domaine. |


### <a name="configure-bam-tools"></a>Configuration des outils BAM

Si vous n’utilisez pas les outils BAM, ignorez cette section.

Les outils d’analyse BAM incluent :

- Complément BAM pour Excel
- Gestionnaire BAM
- Portail BAM


- La configuration des outils BAM nécessite certaines fonctionnalités d’administration SQL Server et doit être effectuée à partir d’un ordinateur doté d’Integration Services.
- Les outils BAM peuvent être utilisés par plusieurs groupes BizTalk. Lorsque vous annulez la configuration des outils BAM, la connexion au groupe BizTalk est supprimée. Toutefois, l’infrastructure SQL Server BAM continue à fonctionner pour les autres groupes BizTalk pointant vers les tables d’importation principale BAM.
- La page des outils d’analyse BAM permet de reconfigurer instantanément la base de données BAM. Vous pouvez, par exemple, reconfigurer la base de données BAM sans supprimer la configuration existante. La reconfiguration de ces bases de données BAM démantèle toutes les vues OLAP déjà déployées, ainsi que toutes les alertes. Si vous avez des vues et des alertes que vous souhaitez conserver dans les bases de données nouvellement configurées, effectuez l’une des opérations suivantes :  
    - Annulez le déploiement des vues et des alertes avant de reconfigurer, puis redéployez-les après la reconfiguration. Les données archivées ne figurent pas dans ces vues.
    - Si vous n'utilisez pas d'alertes BAM, sauvegardez les bases de données avant de reconfigurer. Une fois la reconfiguration terminée, restaurez les bases de données dans le nouvel emplacement configuré.
- Si vous consolidez des bases de données [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], vous devez exclure les bases de données d’analyse BAM et d’archivage BAM.


1. Sélectionnez **Outils BAM**.
2. Configurez les éléments suivants :

    |Utilisez ceci|Pour effectuer cette opération|
    | --- | --- |
    |Activer les outils d'analyse BAM | Activer et installer les outils BAM sur cet ordinateur. |
    | Activer Analysis Services pour les agrégations BAM | Fournit des informations de suivi pour les alertes BAM.|
    |Banques de données| Entrer le nom du serveur qui héberge les bases de données BAM. Si BizTalk et SQL sont tous les deux installés sur ce serveur, entrez le nom du serveur local. Si SQL Server figure sur un autre ordinateur, entrez le nom du serveur SQL Server.<br/><br/>Vous pouvez conserver le nom de base de données par défaut ou entrer un nom personnalisé.|
    |Supprimez les outils d'analyse BAM pour ce groupe BizTalk | Désinstalle et supprime les outils BAM du groupe BizTalk. |
    
 ### <a name="configure-bam-alerts"></a>Configuration des alertes BAM 

Pour bénéficier des alertes BAM, il est nécessaire d'activer les outils BAM.

1. Sélectionnez **Alertes BAM**.
2. Configurez les éléments suivants :

    |Utilisez ceci|Pour effectuer cette opération|
    | --- | --- |
    | Activer les alertes BAM | Si vous utilisez des alertes BAM, cochez cette option. <br/><br/>N’oubliez pas que vous devez avoir déjà configuré SQL Database Mail pour utiliser les alertes BAM. |
    | Service Windows | Entrer les comptes utilisés pour exécuter le service Alertes BAM. Si SQL Server est sur un autre ordinateur, entrez le compte de domaine. |
    | Serveur SMTP d'Alertes BAM| Entrer le nom du serveur SMTP que vous avez configuré avec SQL Database Mail. |
    | Emplacement du fichier Alertes BAM| Entrer un partage réseau pour stocker les alertes BAM. <br/><br/>**Remarque** <br/>Vous devez créer manuellement ce partage avant que les alertes BAM puissent stocker les fichiers.|
    | Serveur SQL Server pour les bases de données d'alertes | Entrer le nom du serveur SQL Server qui héberge la base de données des alertes.<br/><br/>**Remarque** <br/>L'utilisation d'adresses IPv6 dans le but de spécifier le serveur NS SQL associé à la base de données d'alertes n'est pas prise en charge. Vous pouvez toutefois utiliser un nom d'ordinateur ; la conversion DNS se chargera de traiter la recherche.|
    |Préfixe des noms de base de données d'alertes| Entrer un préfixe à utiliser pour les bases de données d’alertes.|  

### <a name="configure-the-bam-portal"></a>Configuration du portail BAM

1. Sélectionnez **Portail BAM**.
2. Configurez les éléments suivants :

    |Utilisez ceci|Pour effectuer cette opération|
    | --- | --- |
    |Activer le portail BAM | Si vous utilisez le portail BAM, cliquez sur cette option. | 
    |Comptes de service Web | Entrer les comptes utilisés pour exécuter les services IIS. Si SQL Server est sur un autre ordinateur, entrez les comptes de domaine.|
    |Groupes Windows | Vous pouvez conserver le nom de groupe par défaut ou entrer un nom personnalisé. Si SQL Server est sur un autre ordinateur, entrez le compte de domaine.|
    |Site Web du portail BAM|Sélectionner le site web à utiliser pour héberger le portail BAM. Dans certains environnements, le site web par défaut est le seul site web configuré. |

### <a name="configure-biztalk-edias2-runtime"></a>Configuration du composant d’exécution EDI/AS2 de BizTalk 

* Les paramètres SSO de l’entreprise, Groupe et Moteur d’exécution BizTalk doivent être configurés pour que vous puissiez configurer le composant d’exécution EDI/AS2 de BizTalk. 
* Les outils BAM doit être activés avant de configurer les fonctionnalités de rapport d’état du composant d’exécution EDI/AS2.
* Si vous configurez uniquement le composant EDI, l'analyse BAM n'est pas obligatoire.

1. Sélectionnez **Composant d’exécution EDI/AS2 de BizTalk**.
2. Configurez les éléments suivants :

    |Utilisez ceci|Pour effectuer cette opération|
    | --- | --- |
    |Activer le composant d'exécution EDI/AS2 sur cet ordinateur| Si vous envisagez d’utiliser les protocoles X12, EDIFACT ou AS2 pour la messagerie interentreprises, sélectionnez cette option. |
    |Activer EDI BizTalk pour ce groupe BizTalk | Sélectionnez cette option si vous utilisez X12 ou EDIFACT. |
    | Activer AS2 BizTalk pour ce groupe BizTalk | Sélectionnez cette option si vous utilisez AS2. |
    | Activer le rapport d'état EDI/AS2 BizTalk pour ce groupe BizTalk | Activer l’expérience utilisateur de création de rapports pour fournir l’état des échanges EDI et les accusés de réception. |
    |Supprimez les fonctionnalités EDI, AS2 et Rapport d'état de BizTalk pour ce groupe BizTalk | Désinstaller et supprimer la fonctionnalité de création de rapports à partir du groupe. |

### <a name="configure-windows-sharepoint-services-web-service---biztalk-server-2013-and-r2-only"></a>Configuration du service web de Windows SharePoint Services - BizTalk Server 2013 et R2 uniquement 

> [!IMPORTANT] 
> Cette section s’applique UNIQUEMENT à BizTalk Server 2013 R2 et à BizTalk Server 2013. Si vous n’utilisez pas BizTalk Server 2013 R2 ni BizTalk Server 2013, ignorez cette section.

* Ce service web de SharePoint Services (SSOM) est supprimé à partir de BizTalk Server 2016 et déconseillé dans BizTalk Server 2013 R2. Il est remplacé par l’adaptateur SharePoint Services (CSOM). L’option CSOM n’est pas affichée dans la configuration de BizTalk. L’option CSOM est installée automatiquement avec BizTalk, tout comme l’adaptateur de fichier, ou l’adaptateur HTTP est installé automatiquement.

1. Sélectionnez **Adaptateur Windows SharePoint Services**.
2. Configurez les éléments suivants :

    |Utilisez ceci|Pour effectuer cette opération|
    | --- | --- |
    | Activer l’adaptateur Windows SharePoint Services sur cet ordinateur | Sélectionnez cette option pour installer le service web SharePoint Services. Un service web IIS est installé sur l’ordinateur SharePoint Services, qui peut se trouver sur le même ordinateur que BizTalk Server ou sur un ordinateur distinct. Dans la plupart des environnements, BizTalk Server et SharePoint Services se trouvent sur des ordinateurs distincts.|
    |Groupe Windows|Vous pouvez conserver le nom de groupe par défaut ou entrer un nom personnalisé. |
    |Site Web de l'adaptateur Windows SharePoint Services|Sélectionner le site web qui héberge le service web de l’adaptateur Windows SharePoint Services.|
    
    
### <a name="apply-your-configuration"></a>Application de votre configuration

Sélectionnez **Appliquer la configuration** et poursuivez la configuration. 

1. Dans **Résumé**, passez en revue les composants sélectionnés et cliquez sur **suivant**.
2. Lorsque vous avez terminé, sélectionnez **Terminer**.

Une fois terminé, un fichier journal de configuration est généré dans un dossier temporaire, similaire à : `
C:\Users\username\AppData\Local\Temp\ConfigLog(1-12-2017 2h39m30s).log`.

## <a name="iis-application-pools-and-web-sites"></a>Pools d’applications IIS et les sites web
Après avoir configuré [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], les pools d’applications suivants Internet Information Services (IIS) et des applications virtuelles peuvent être créées : 
  
### <a name="application-pools"></a>Pools d’applications  
  
|Pool d'applications|Identité du pool d'applications par défaut| Description|  
|----------------------|---------------------------------------|-----------------|  
|BAMAppPool|*Défini par l’utilisateur*|Pool d'applications pour le portail BAM.|  
|BTSSharePointAdapterWSAppPool|*Défini par l’utilisateur*|Pool d'applications pour le service Web de l'adaptateur Windows SharePoint Service.|  
|STSWebServiceAppPool|*Défini par l’utilisateur*|Pool d'applications pour les outils de gestion des partenaires commerciaux.|  
|TpmWSAppPool|*Défini par l’utilisateur*|Pool d'applications pour le service Web de gestion GPC.|  
  
### <a name="virtual-applications"></a>Applications virtuelles  
  
|Application virtuelle|Pool d'applications par défaut| Description|  
|-------------------------|------------------------------|-----------------|  
|BAM|BAMAppPool|Application virtuelle qui héberge les composants du portail BAM (pages, images, code précompilé et autres ressources). Cette application virtuelle est utilisée avec l'application BAMManagementService pour communiquer avec les bases de données BAM. **Remarque :** pour personnaliser le portail BAM, vous pouvez modifier le contenu de cette application.|  
|BAMManagementService|BAMAppPool|Application virtuelle qui héberge le service Web BAMManagementService. Ce service Web est utilisé par l'application Portail BAM pour communiquer avec les tables d'importation principale BAM. La communication avec la base de données s'effectue à l'aide des informations d'identification stockées dans le registre et créées pendant la configuration. Les méthodes exposées par ce service Web peuvent être utilisées par des clients personnalisés pour obtenir des vues et leurs détails, les activités associées et des données présentées sous forme de tableau croisé dynamique pour n'importe quel utilisateur. Elles peuvent aussi servir à gérer les alertes dans la base de données.|  
|BTSharePointAdapterWS|BTSSharePointAdapterWSAppPool|Application virtuelle qui héberge le service Web de l'adaptateur Windows SharePoint Service. S’applique à BizTalk Server 2013 R2 2013 uniquement.|  

 
## <a name="more-configuration-topics"></a>Autres rubriques relatives à la configuration  
  
 [Configuration de BizTalk Server sur une machine virtuelle Azure](http://msdn.microsoft.com/library/azure/jj248689.aspx)  
  
[Configuration de BizTalk Server dans un cluster](../install-and-config-guides/configure-biztalk-server-in-a-cluster.md)

[Étapes d’optimisation de l’environnement après configuration](../install-and-config-guides/post-configuration-steps-to-optimize-your-environment.md)

 [Sécurisation d’un déploiement BizTalk Server](../install-and-config-guides/securing-your-biztalk-server-deployment.md)  
  
 