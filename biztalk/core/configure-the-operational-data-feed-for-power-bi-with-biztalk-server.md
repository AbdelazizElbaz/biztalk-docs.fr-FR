---
title: Activer Power BI | Documents Microsoft
description: "Installer le modèle de Power BI dans le Feature Pack pour BizTalk Server"
ms.custom: fp1
ms.date: 11/07/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fe6d3a97-c7c0-4147-baa9-ee12f93248eb
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 585927b494f51ddd3ab7abd0503df7586c30b041
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="configure-the-power-bi-operational-data-feed-in-biztalk-server"></a>Configurer les données opérationnelles de Power BI de flux dans BizTalk Server

**En commençant par [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [!INCLUDE[featurepack1](../includes/featurepack1.md)]** , suivi d’envoi à l’aide du modèle de Power BI fourni de Power BI ou créer vos propres. 

## <a name="what-is-operational-data"></a>Nouveautés des données opérationnelles
Données opérationnelles sont plus d’informations sur les instances et les messages transitant via votre [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] environnement. Le flux de données opérationnelles est les mêmes données que vous obtenez examinant Hub du groupe dans [!INCLUDE[btsBizTalkServerAdminConsoleui_md](../includes/btsbiztalkserveradminconsoleui-md.md)]. Les données sont accessible et interrogés à l’aide des outils de visualisation, y compris Power BI. 

Le flux inclut les tables de données suivantes :
* Données d’application
* AS2 Enregistrements d’état
* Informations de traitement par lot
* Informations sur l’instance
* Échange des enregistrements d’agrégations
* Enregistrements d’état de l’échange
* Messages
* Abonnements
* Événements suivis
* Rapports de transaction
* Documents informatisés

> [!TIP]
> [PowerBI.com](http://powerbi.microsoft.com) est un bon point de départ pour comprendre et en savoir plus sur Power BI.

## <a name="prerequisites"></a>Conditions préalables
* Téléchargez et installez [Power BI Desktop](https://powerbi.microsoft.com/desktop/) sur n’importe quel ordinateur qui dispose d’un accès réseau pour votre[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]
* Installer [Feature Pack 2](https://aka.ms/bts2016fp2) sur votre[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]
* Installer IIS sur le [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]. Dans la plupart des [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] environnements, IIS est déjà installé. Consultez [matérielle et logicielle requise pour BizTalk Server 2016](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2016.md). Vérifiez que IIS est installé en ouvrant **Gestionnaire des Services Internet**. 
* Ce paramètre est facultatif. Installer et configurer un [Power BI Gateway](https://powerbi.microsoft.com/gateway/) connecter [PowerBI.com](http://powerbi.microsoft.com) avec votre serveur de BizTalk Server sur site. Si vous n’utilisez pas un serveur de BizTalk sur site, vous ne devez la passerelle.

## <a name="step-1-enable-operational-data"></a>Étape 1 : Activer les données opérationnelles

1. Exécutez Windows PowerShell en tant qu’administrateur (**Démarrer** menu, tapez **PowerShell**avec le bouton droit et cliquez sur Sélectionner **exécuter en tant qu’administrateur**). 
2. Accédez au dossier d’installation de BizTalk (par exemple, tapez : `cd 'C:\Program Files (x86)\Microsoft BizTalk Server 2016\'`).
3. Dans le texte suivant, remplacez `Default Web Site`, `operationalDataServiceAppPool`, `domain\user`, `password`, et `domain\group` avec vos valeurs :

    ```Powershell
    FeaturePack.ConfigureServices.ps1 -Service operationaldata -WebSiteName '<Default Web Site>' -ApplicationPool <operationalDataServiceAppPool> -ApplicationPoolUser <domain>\<user\> -ApplicationPoolUserPassword <password> -AuthorizationRoles '<domain>\<group1\>, <domain>\<group2\>, <domain>\<user\>, <domain>\<user2\>'
    ```

    * **Service**: le service doit être configuré (**OperationalData** pour Power BI)
    * **WebSiteName**: le site web IIS existant qui héberge le service. La valeur par défaut est **Site Web par défaut**.
    * **ApplicationPool**: le Pool d’applications utilisé par le service. S’il en existe une autre n’est pas créée. La valeur par défaut est **DefaultAppPool**.
    * **ApplicationPoolUser**: Configure le pool d’applications à exécuter en tant qu’identité de cet utilisateur. Doit avoir l’opérateur de BizTalk Server, ou des privilèges plus élevés.
    * **ApplicationPoolUserPassword**: mot de passe pour le ApplicationPoolUser
    * **AuthorizationAccount**: liste des groupes ou utilisateurs qui peuvent utiliser ce service d’autorisés

    Dans l’exemple suivant, nous utilisons le `Default Web Site`, créer un pool d’applications nommé `PowerBIAppPool`, exécuter le pool d’applications en tant que le `bootcampbts2016\btsservice` de compte, utilisez `BIZTALK-serviceacct` comme mot de passe utilisateur, donnent le `BizTalk Server Administrators` autorisations du groupe. Veillez à entrer le texte suivant, y compris le seul devis environnantes valeurs avec des espaces : 

    ```Powershell
    FeaturePack.ConfigureServices.ps1 -Service operationaldata -WebSiteName 'Default Web Site' -ApplicationPool PowerBIAppPool -ApplicationPoolUser bootcampbts2016\btsservice -ApplicationPoolUserPassword  BIZTALK-serviceacct -AuthorizationRoles 'BOOTCAMPBTS2016\BizTalk Server Administrators'
    ```

    Lorsque vous avez terminé, l’application BizTalkOperationalDataService est créée dans IIS :  
    ![Application de BizTalkMOperationalDataServer](../core/media/biztalkmanagementservice-apppool.png)


4. Pour vérifier qu’il fonctionne, accédez à `http://localhost/BizTalkOperationalDataService`. 

    Si vous êtes invité à la connexion, connectez-vous avec un compte qui est membre de la domaine\groupe que vous avez entré à l’étape précédente (`-AuthorizationRoles 'BOOTCAMPBTS2016\BizTalk Server Administrators'`). 

    Si vous êtes invité à ouvrir ou enregistrer BizTalkOperationalDataService.json, votre installation est terminée. Vous pouvez enregistrer localement et puis ouvrez-le dans le bloc-notes ou Visual Studio pour afficher le contenu. 

> [!WARNING]
> L’application BizTalkOperationalDataService dans IIS utilise un fichier web.config. Éléments dans le fichier web.config **respectent la casse**. Par conséquent, lorsque vous exécutez le script Windows PowerShell, veillez à entrer la casse correcte pour `-AuthorizationRoles` valeur. Si vous ne savez pas le cas, Voici un moyen simple de déterminer : 
> 
> 1. Ouvrez **gestion de l’ordinateur**, développez **utilisateurs et groupes locaux**.
> 2. Sélectionnez **groupes**et faites défiler jusqu'à la **SQLServer...** groupes. 
> 3. Dans l’exemple suivant, notez **BOOTCAMPBTS2016** est en majuscules. Si vous voyez tout en majuscules, puis entrez le nom d’ordinateur dans tout en majuscules. 
> 
> ![Nom de l’ordinateur est en majuscules](../core/media/groups-case.png)

## <a name="step-2-use-the-template-in-power-bi"></a>Étape 2 : Utiliser le modèle dans Power BI

1. Téléchargez et installez le [Power BI Desktop](https://powerbi.microsoft.com/desktop/) sur votre serveur BizTalk Server. Vous pouvez choisir d’ouvrir le document, qui est facultatif. Si vous avez un compte professionnel ou scolaire, vous avez accès à Power BI. Essayez de vous connecter avec ce compte. Ou, vous pouvez l’essai gratuit après vous être inscrit. 
2. Ouvrez le `\Program Files (x86)\Microsoft BizTalk Server 2016\OperationalDataService` dossier, puis ouvrez le `BizTalkOperationalData.pbit` fichier :  
![Fichier de pbit ouvert](../core/media/operational-data-pbit.png)

3. Power BI desktop l’ouvre et vous êtes invité à entrer une URL. Entrez le `http://localhost/<yourWebSite>` URL que vous avez créé pour votre flux OData. Par exemple, entrez `http://localhost/BizTalkOperationalDataService`. Votre URL est similaire à ce qui suit :  
![Entrez l’URL](../core/media/operational-data-url.png)

4. Sélectionnez **charge**. La fenêtre de charge et se connecte aux sources différentes oData dans le fichier BizTalkOperationalDataService.json. Lorsqu’elle est terminée, le tableau de bord affiche les détails de votre environnement.

## <a name="couldnt-authenticate"></a>N’a pas pu s’authentifier
Si vous obtenez `couldn't authenticate with the credentials provided` message semblable au suivant, il est possible que votre identité de pool d’applications n’a pas suffisamment accès aux bases de données BizTalk Server. Vous pouvez modifier l’identité du pool d’applications dans IIS pour un compte avec des privilèges plus peut-être que votre compte d’utilisateur connecté (qui dispose des privilèges d’administrateur local). 

![N’a pas pu s’authentifier avec les informations d’identification fournies](../core/media/operational-data-authentication-error.png)

## <a name="do-more"></a>Faire plus
Il s’agit que du début. Power BI a également une passerelle qui peut être installée sur un serveur de BizTalk sur site. À l’aide de la passerelle, vous pouvez publier votre tableau de bord, obtenir des données en temps réel et créer une planification d’actualisation du tableau de bord. Le blog suivant est un bon outil détaillant comme suit : 

* [Comment publier des données opérationnelles de BizTalk sur Power BI – configuration pas à pas](https://blog.sandro-pereira.com/2017/05/07/biztalk-server-2016-feature-pack-1-how-to-publish-biztalk-operational-data-power-bi-step-by-step-configuration-part-3/)

Le [formation guidée](https://powerbi.microsoft.com/guided-learning/) est également un excellent point pour en savoir plus sur Power BI et toutes les opérations réalisables. 

## <a name="see-also"></a>Voir aussi

[En savoir plus sur Power BI](https://www.powerbi.com)  
[Configurer le Pack de fonctionnalités](../core/configure-the-feature-pack.md)
