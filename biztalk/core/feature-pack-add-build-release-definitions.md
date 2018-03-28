---
title: 'Étape 3 : créer les définitions de build et de version | Documents Microsoft'
description: Dans VSTS, créez une définition de build pour générer les projets de votre git ou le référentiel TFS, puis créer une définition de mise en production pour déployer l’application BizTalk Server
ms.custom: ''
ms.date: 11/20/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5ce84071fbc105fd9faddd794792273aae2e76b9
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="step-3-create-the-build-and-release-definition"></a>Étape 3 : Créer la version et définition de version

Les définitions de build et de mise en production sont des tâches de Visual Studio Team Services et probablement doivent être effectuées que par un administrateur de VSTS. La définition de build génère votre projet au sein de votre référentiel git et les définitions de mise en production déploie sur votre environnement BizTalk Server. 

## <a name="before-you-begin"></a>Avant de commencer
Complète [étape 2 : jeton de VSTS de créer et installer l’agent](feature-pack-create-vsts-token.md).

## <a name="add-the-build-tasks"></a>Ajouter les tâches de génération
1. Dans votre projet, sélectionnez **créer et libérer**. L’onglet de Builds s’ouvre. Créer un **nouveau** définition :

    ![Nouvelle définition de build](../core/media/vsts-new-definition.png)

2. Sélectionnez le **vide** modèle, puis sélectionnez **appliquer**:  

    ![Sélectionner un modèle vide](../core/media/vsts-emtpy-template.png)
 
3. Définir le **file d’attente de l’Agent** par défaut : 

    ![Choisissez la file d’attente par défaut](../core/media/vsts-select-agent-queue.png)

4. Dans **Phase 1**, ajoutez une tâche, sélectionnez **Visual Studio Build**, puis sélectionnez **ajouter**:

    ![Ajouter la que tâche de génération de Visual Studio](../core/media/vsts-add-visual-studio-task.png)

5. Cliquez sur la tâche de génération de Visual Studio vous venez d’ajouter et définissez les propriétés suivantes :  

    | Propriété | La valeur |
    | --- | --- | 
    | Nom complet | *Votre_nom_de_projet* générer solution **\*.sln | 
    | Version de Visual Studio | Visual Studio 2015 | 
    | Architecture de MSBuild | MSBuild x86 | 

6. Dans **Phase 1**, ajoutez une tâche, sélectionnez **publier des artefacts de Build**, puis sélectionnez **ajouter**: 

    ![Ajouter la que tâche de génération de Visual Studio](../core/media/vsts-add-publish-build-task.png)

7. Sélectionnez le **publier un artefact** de tâches, puis entrez votre choix **nom d’affichage**. Pour **chemin d’accès à la publication**, sélectionnez le **...**  affiché, puis choisissez le dossier de projet d’application (par exemple, appProjectHelloWorld). Sélectionnez **OK**.

8. Le **nom de l’objet** peut être comme vous le souhaitez. Sélectionnez **enregistrer**. 

9. Accédez à **déclencheurs**et définissez la **déclencher état** à **activé**:  

    ![Ajouter la que tâche de génération de Visual Studio](../core/media/vsts-continuous-integration.png)

10. **Enregistrer et de file d’attente** pour tester votre définition de build. Lorsque vous la file d’attente, vous êtes invité à entrer votre branche et de la file d’attente de l’agent. Sélectionnez le **par défaut** agent file d’attente et choisissez votre branche. Sélectionnez **file d’attente**.  

11. Une nouvelle build est démarrée, et vous pouvez le sélectionner pour vérifier la réussite ou l’échec. 

## <a name="add-the-release-tasks"></a>Ajoutez les tâches de mise en production

Lorsque la build réussit, la définition de la mise en production déploie votre application sur votre serveur BizTalk Server. 

1. Sélectionnez le **versions** onglet, sélectionnez **nouvelle définition**. 

2. Sélectionnez le **vide** modèle, puis sélectionnez **appliquer**:

    ![Ajouter un modèle vide](../core/media/vsts-empty-release-template.png)

3. Modifier la **nom de l’environnement** à **Dev**, ou tout ce que vous voulez appeler. 

4. Sélectionnez **ajouter artefact**, sélectionnez votre projet, votre définition de build, puis sélectionnez **ajouter**: 

5. Accédez à la **tâches** onglet, ajoutez une nouvelle tâche : 

    ![Ajouter une tâche de mise en production](../core/media/vsts-new-release-tasks.png)

6. Dans la liste, filtrer les résultats, sélectionnez le **déploiement d’Application BizTalk Server** de tâches, puis sélectionnez **ajouter**:  

    ![Ajouter la tâche de déploiement BizTalk](../core/media/vsts-biztalk-application-deployment-task.png)

    Si **déploiement d’Application BizTalk Server** ins't dans la liste, puis installez-le à [déployer l’Application BizTalk](https://marketplace.visualstudio.com/items?itemName=ms-biztalk.deploy-biztalk-application).

7. Sélectionnez le **déployer** , entrez les valeurs et de la tâche : 

    **Nom de l’opération**: les options disponibles : * **créer la nouvelle Application BizTalk**: déploie une nouvelle application. Si l’application existe déjà, il désinstalle les applications actuelles (point) et installe la nouvelle application. Si l’intégration continue est activée, elle automatiquement redéploie l’application lorsqu’elle est mise à jour dans le référentiel. 
        * **Mettre à jour une Application BizTalk existante**: ajoute des modifications, tels que des schémas à une application déjà en cours d’exécution. Il ne nécessite pas un redéploiement complet de l’application.
        * **Installer l’Application BizTalk Server**: [installer les applications](../core/how-to-install-a-biztalk-application.md), et que vous entrez le nom d’ordinateur de gestion BizTalk et le chemin d’accès du package de déploiement.

        ![Deploy operations](../core/media/vsts-deploy-operations.png)

    **Nom de l’application**: le texte que vous entrez sera le nom de l’application dans l’Administration de BizTalk. Faire **pas** Entrez BizTalk Application 1.

    **Package de déploiement**: sélectionnez le fichier zip dans votre projet d’application, puis sélectionnez **OK**. 

8. Sélectionnez le **phase Agent** tâche. Sélectionnez le **par défaut** file d’attente de l’Agent. **Enregistrer** vos modifications.

9. Sélectionnez **Release** > **créer version**:  

    ![La version finale, créez la mise en production](../core/media/vsts-create-release.png)

10. Sélectionnez **file d’attente**. Vérifiez l’état en cliquant sur le lien mise en production. En cas d’échec, l’erreur s’affiche. Si elle réussit, l’application est ajoutée à la console Administration de BizTalk. 

## <a name="what-you-did"></a>Ce que vous avez fait

Dans VSTS, vous avez créé une définition de build qui génère votre application dans Git ou Team Foundation Version Control (que vous avez choisi). Lorsque des modifications sont apportées dans le contrôle de code source, les modifications sont détectées automatiquement et vous pouvez les envoyer. Une fois la build terminée, vous avez créé une définition de mise en production qui déploie l’application à BizTalk Server, que vous pouvez visualiser dans Administration de BizTalk Server. 

## <a name="next-step"></a>Étape suivante
À ce stade, vous avez terminé. Si vous préférez, vous pouvez créer des jetons de l’environnement dans votre fichier de liaison XML BizTalk et créer des variables dans VSTS qui correspondent aux jetons de l’environnement. Consultez [configurer des jetons de l’environnement et les variables](configure-environmental-tokens-and-variables-for-automatic-deployment.md) pour plus d’informations. 