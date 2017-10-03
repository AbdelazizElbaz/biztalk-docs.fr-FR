---
title: "Configurer les données opérationnelles de flux pour Power BI avec BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fe6d3a97-c7c0-4147-baa9-ee12f93248eb
caps.latest.revision: "11"
author: tordgladnordahl
ms.author: tonordah
manager: anneta
ms.openlocfilehash: 09b1b1fd7f350e168b2bb13d6bee2e45c12d49cc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configure-the-operational-data-feed-for-power-bi-with-biztalk-server"></a>Configurer les données opérationnelles de flux pour Power BI avec BizTalk Server
Lire des données opérationnelles fournies via un flux oData dans [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]. 

**En commençant par [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [!INCLUDE[featurepack1](../includes/featurepack1.md)]** , suivi d’envoi à l’aide du modèle de Power BI fourni de Power BI ou créer vos propres. 

## <a name="what-is-operational-data"></a>Nouveautés des données opérationnelles
Données opérationnelles sont plus d’informations sur les instances et les messages transitant via votre [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] environnement. Le flux de données opérationnelles est les mêmes données que vous obtenez examinant Hub du groupe dans le [!INCLUDE[btsBizTalkServerAdminConsoleui_md](../includes/btsbiztalkserveradminconsoleui-md.md)] console. Les données sont accessibles et interrogés à l’aide des outils de visualisation, y compris Power BI. 

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
* Installer [Feature Pack 1](https://www.microsoft.com/download/details.aspx?id=55100) sur votre[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]
* Installer IIS sur le [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]. Dans la plupart des [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] environnements, IIS est déjà installé. Consultez [matérielle et logicielle requise pour BizTalk Server 2016](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2016.md). 

## <a name="enable-operational-data-feed"></a>Activer le flux de données opérationnelles

1. Exécutez Windows PowerShell en tant qu’administrateur (**Démarrer** menu, tapez **PowerShell**avec le bouton droit et cliquez sur Sélectionner **exécuter en tant qu’administrateur**). 
2. Accédez au dossier où [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] est installé **Program Files (x86)/Microsoft BizTalk Server 2016**
3. Exécutez la commande suivante : Veillez à mettre à jour votre `website`, `domain\user`, `password`, et `domain\group` avec vos valeurs : 

    ```Powershell
    FeaturePack.ConfigureServices.ps1 -Service operationaldata -WebSiteName '<Default Web Site>' -ApplicationPool <operationalDataServiceAppPool> -ApplicationPoolUser <domain>\<user> -ApplicationPoolUserPassword <password> -AuthorizationRoles '<domain>\<group1>, <domain>\<group2>'
    ```
4. Après avoir exécuté le script, accédez à la nouvelle Application IIS :  
    1. Ouvrez votre navigateur web
    2. Accédez à **http://localhost/BizTalkOperationalDataService**

## <a name="use-the-power-bi-template"></a>Utilisez le modèle de Power BI
Pour accéder au fichier de modèle Power BI et utiliser la visualisation fournie par Microsoft, procédez comme suit :

1. Téléchargez et installez le [Power BI Desktop](https://powerbi.microsoft.com/desktop/).
2. Accédez à votre dossier de BizTalk Server sous **Program Files (x86) \Microsoft BizTalk Server 2016\OperationalDataService**.
3. Ouvrez le **BizTalkOperationalData.pbit** fichier.
4. Lorsque vous êtes invité à partir de Power BI, collez la **http://localhost/\<votresiteweb\>**  URL que vous avez créé pour votre flux OData. Par exemple, entrez **http://localhost/OperationalDataService**. 

    Votre URL est similaire à ce qui suit : 
    
    ![Collez l’URL OData pour le fichier de modèle Power BI](../core/media/pasteurltopowerbitempaltefile.PNG)

5. Sélectionnez **charge** pour remplir les champs dans votre rapport Power BI. 
6. Le fichier de modèle génère automatiquement les informations et les tables disponibles à partir du flux OData.

Les données opérationnelles sont exposées via l’ordinateur et peuvent être accessible et exécutées par d’autres applications en fonction des autorisations. 

Pour en savoir plus sur Power BI et comment publier le rapport en ligne atteindre [PowerBI.com](http://powerbi.microsoft.com)

## <a name="see-also"></a>Voir aussi

[En savoir plus sur Power BI](https://www.powerbi.com)  
[Configurer le Pack de fonctionnalités](../core/configure-the-feature-pack.md)