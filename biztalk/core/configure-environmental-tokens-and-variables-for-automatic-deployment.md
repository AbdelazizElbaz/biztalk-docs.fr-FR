---
title: "Configurer des jetons de l’environnement et les variables pour un déploiement automatique | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.prod: biztalk-server
ms.topic: article
ms.assetid: 28bb2d4a-f45c-466d-ba65-0ca8cad0bffd
caps.latest.revision: "4"
author: tordgladnordahl
ms.author: tonordah
manager: anneta
ms.openlocfilehash: 7d148f79fceb68b24feb45882ab89767369ed7e6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configure-environmental-tokens-and-variables-for-automatic-deployment"></a>Configurer des jetons de l’environnement et les variables pour un déploiement automatique
Utiliser des variables Visual Studio Team Services (VSTS) dans votre [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] fichiers de liaison.

## <a name="overview"></a>Vue d'ensemble
Dans un environnement de VSTS, vous pouvez ajouter des variables et les définir sur une valeur. Par exemple, vous pouvez créer un *sendPortPath* variable et définissez sa valeur à un dossier physique sur votre [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]. 

Dans la [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] fichier de liaison d’application, les variables configurables peuvent s’agir d’une balise XML, telles que le nom d’emplacement de réception, héberger, URI du port d’envoi et ainsi de suite. 

Ces variables sont spécifiques à votre environnement de VSTS et peut être utilisés pour déployer la même application à plusieurs [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] environnements. 

Dans cette rubrique, nous montrons comment ajouter de la variable VSTS dans votre fichier de liaison et la création de la variable dans VSTS. 

## <a name="configure-the-variables-in-your-biztalk-binding-file"></a>Configurer les variables dans votre fichier de liaison BizTalk

L’exemple suivant fait partie d’un [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] fichier de liaison et montre comment appliquer les jetons.

1. Ouvrez le fichier de liaison d’application :

    ![Pack de fonctionnalités de BizTalk 1 liaison 1](../core/media/biztalk-feature-pack-1-binding-1.png)

2. Recherchez l’élément que vous souhaitez modifier :

    ![Pack de fonctionnalités de BizTalk 1 liaison 2](../core/media/biztalk-feature-pack-1-binding-2.png)
    
3. Supprimer la valeur par défaut et remplacez-la par vous variables : `$(YourValue)`. Par exemple, entrez `$(SendPort1)`: 

    ![Pack de 1 à 3 de liaison BizTalk](../core/media/biztalk-feature-pack-1-binding-3.png)


4. Lorsque vous avez terminé, enregistrez le fichier de liaison et l’appliquer à votre modèle de génération JSON.
5. Connectez-vous à votre solution de Service d’équipe Visual Studio, puis sélectionnez **créer et libérer**.
6. Accédez à **version**. Sélectionnez votre **définition de la version**, ou créez-en un.
7. Sous **environnements**, sélectionnez **ajouter un nouvel environnement**, ou modifier dans un environnement existant : 

    ![Ajouter un nouvel environnement](../core/media/add-a-new-environment.png)

8. Cliquez sur le bouton de sélection, puis sélectionnez **configurer les variables**:

    ![configurer les variables](../core/media/configure-variables.png)

9. En ajoutant les variables pour chaque environnement, en utilisant les noms de jeton créés dans le fichier de liaison, vous pouvez déployer vos applications dans plusieurs environnements avec des valeurs différentes :

    ![variables d’environnement spécifiques](../core/media/environment-specific-variables.png)
    
10. Sélectionnez **OK** pour enregistrer les nouvelles variables.
11. Une fois la build est lancée, les valeurs sont ajoutées à partir du fichier de liaison.

## <a name="next-step"></a>Étape suivante
[Ajouter une application BizTalk dans VSTS](../core/add-a-biztalk-server-application-to-visual-studio-team-services.md)