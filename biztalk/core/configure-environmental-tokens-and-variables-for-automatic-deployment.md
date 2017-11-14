---
title: "Créer des jetons de l’environnement et des variables | Documents Microsoft »"
description: "Mettre à jour le fichier de liaison pour utiliser des jetons de l’environnement et créer des variables dans VSTS pour automatiser le déploiement d’applications BizTalk Server"
ms.custom: 
ms.date: 11/08/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.prod: biztalk-server
ms.topic: article
ms.assetid: 28bb2d4a-f45c-466d-ba65-0ca8cad0bffd
caps.latest.revision: "4"
author: tordgladnordahl
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6d84fa393410e3084c87e762140530a45b0b78b5
ms.sourcegitcommit: a0165ec2f1e8b58545638666b7bfa2bf440036fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="configure-environmental-tokens-and-variables-for-automatic-deployment"></a>Configurer des jetons de l’environnement et les variables pour un déploiement automatique
Utiliser des variables Visual Studio Team Services (VSTS) dans votre [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] fichiers de liaison.

## <a name="overview"></a>Vue d'ensemble
Dans un environnement de VSTS, vous pouvez ajouter des variables et les définir sur une valeur. Par exemple, vous pouvez créer un *sendPortPath* variable et définissez sa valeur à un dossier physique sur votre [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]. 

Dans la [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] fichier de liaison d’application, les variables configurables peuvent s’agir d’une balise XML, telles que le nom d’emplacement de réception, héberger, URI du port d’envoi et ainsi de suite. 

Ces variables sont spécifiques à votre environnement de VSTS et peut être utilisés pour déployer la même application à plusieurs [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] environnements. 

Nous vous montrent comment ajouter la variable VSTS dans votre fichier de liaison et la création de la variable dans VSTS. 

## <a name="add-variables-to-the-binding-file"></a>Ajouter des variables dans le fichier de liaison

1. Ouvrez le fichier de liaison d’application :

    ![Ouvrez le fichier de liaison](../core/media/biztalk-feature-pack-1-binding-1.png)

2. Recherchez l’élément que vous souhaitez modifier :

    ![Sélectionnez l’élément](../core/media/biztalk-feature-pack-1-binding-2.png)
    
3. Supprimer la valeur par défaut et remplacez-la par vous variables : `$(YourValue)`. Par exemple, entrez `$(SendPort1)`: 

    ![Fichier de liaison](../core/media/biztalk-feature-pack-1-binding-3.png)

4. Lorsque vous avez terminé, enregistrez le fichier de liaison et l’ajouter à votre modèle de génération JSON (étapes de [étape 1 : modèle de .json & mise à jour du projet Ajouter une Application](feature-pack-add-application-project.md)).

## <a name="create-the-variables-in-vsts"></a>Créez les variables dans VSTS

1. Dans votre compte VSTS, sélectionnez **créer et libérer**, puis sélectionnez **versions**.

2. Sélectionnez votre **définition de la version**, puis sélectionnez **Variables**:  

    ![Fichier de liaison](../core/media/vsts-release-variables.png)

3. Sélectionnez **ajouter**et créer les noms de variables et les valeurs :   

    ![configurer les variables](../core/media/environment-specific-variables.png)

4. **Enregistrer** vos modifications. Lorsque le déploiement est initialisé, les valeurs sont ajoutées à partir du fichier de liaison.

## <a name="see-also"></a>Voir aussi
[Configurer le déploiement automatique avec Visual Studio Team Services](configure-automatic-deployment-with-visual-studio-team-services-in-biztalk.md)  
[Télécharger le Feature Pack](configure-the-feature-pack.md)