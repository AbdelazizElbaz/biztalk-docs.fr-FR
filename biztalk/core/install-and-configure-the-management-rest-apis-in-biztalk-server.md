---
title: Installer et configurer la gestion des API REST | Documents Microsoft
description: "Interroger l’état des artefacts dans votre environnement BizTalk à l’aide des données de gestion des API REST avec Feature Pack 1 dans BizTalk Server"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 39442756-5886-4ddd-b700-3800a237de4a
caps.latest.revision: "8"
author: tordgladnordahl
ms.author: tonordah
manager: anneta
ms.openlocfilehash: 009b3b0bb333b8f92f6235da57b0c3e9f5daca96
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="install-and-configure-the-management-rest-apis-in-biztalk-server"></a>Installer et configurer l’API REST de gestion dans BizTalk Server
Utiliser un script Windows PowerShell pour activer l’API REST gérer à distance votre [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)].

## <a name="what-are-management-data-apis"></a>Quelles sont les données de gestion des API
API de données de gestion est les points de terminaison qui vous permettent de mettre à jour à distance, ajouter et interroger l’état des différents artefacts dans votre [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] environnement. Les points de terminaison sont ajoutés à l’aide de REST et être accompagnée d’une définition Swagger. 

**En commençant par [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [!INCLUDE[featurepack1](../includes/featurepack1.md)]** , il existe un script Windows PowerShell qui installe ces API REST et leurs définitions swagger. Ces API effectuer des appels REST pour gérer à distance des ports, orchestrations, partenaires, accords, pipelines et bien plus encore. 

Cette rubrique vous montre comment installer les API REST.

## <a name="prerequisites"></a>Conditions préalables
* Installer [Feature Pack 1](https://www.microsoft.com/download/details.aspx?id=55100) sur votre[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]

* Installer IIS sur le [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]. Dans la plupart des [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] environnements, IIS est déjà installé. Consultez [matérielle et logicielle requise pour BizTalk Server 2016](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2016.md).

## <a name="enable-the-rest-apis"></a>Activer l’API REST

1. Exécutez Windows PowerShell en tant qu’administrateur (**Démarrer** menu, tapez **PowerShell**avec le bouton droit et cliquez sur Sélectionner **exécuter en tant qu’administrateur**). 
2. Accédez au dossier BizTalk sous **Program Files (x86)/Microsoft BizTalk Server 2016**
3. Exécutez la commande suivante : Veillez à mettre à jour votre `website`, `domain/user`, `password`, et `domain\group` avec vos valeurs : 

    ```Powershell
    FeaturePack.ConfigureServices.ps1 -Service management -WebSiteName '<Default Web Site>' -ApplicationPool <mgmtServiceAppPool> -ApplicationPoolUser <domain>\<user> -ApplicationPoolUserPassword <password> -AuthorizationRoles '<domain>\<group>, <domain>\<group>'
    ```
4. Après avoir exécuté le script, accédez à la nouvelle application IIS :  
    1. Ouvrez votre navigateur web
    2. Accédez à **http://localhost/OperationalDataService/swagger**

5. Les charges de définitions Swagger. Vous pouvez également modifier qui a accès en mettant à jour le **web.config** fichier dans le dossier racine de l’Application de gestion.

Les API REST sont exposées via un ordinateur et peut être accessible et exécutés par d’autres applications. 


## <a name="see-also"></a>Voir aussi
 [Configurer le Pack de fonctionnalités](../core/configure-the-feature-pack.md)