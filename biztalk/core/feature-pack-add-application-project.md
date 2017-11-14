---
title: "Étape 1 : ajouter json mise à jour et de projet d’Application | Documents Microsoft"
description: "Ajouter le projet d’Application BizTalk Server dans Visual Studio et mettre à jour le fichier BizTalkServerInventory.json aux DLL, de fichiers de liaison et de séquence de déploiement de vos applications - Visual Studio Team Services"
ms.custom: 
ms.date: 11/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 46cb8a2072280e62cd8c3438521531f8cf3b55aa
ms.sourcegitcommit: a0165ec2f1e8b58545638666b7bfa2bf440036fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="step-1-add-the-biztalk-server-application-project-in-visual-studio"></a>Étape 1 : Ajouter le projet d’Application BizTalk Server dans Visual Studio

.Btaproj – lorsque vous générez vos applications à l’aide de Visual Studio Team Services, un nouveau fichier de projet BizTalk est créé. Ce projet conserve toutes les applications BizTalk que vous générez et déployez à l’aide de la génération VSTS et fonctionnalités de la version. 

Le projet d’Application BizTalk inclut le `BizTalkServerInventory.json` fichier. Dans ce fichier, ajouter vos assemblys BizTalk, ajoutez les fichiers de liaison pour votre application BizTalk, puis définissez une séquence de déploiement. 

## <a name="before-you-begin"></a>Avant de commencer

* Ces étapes supposent que vous avez un projet BizTalk existant. Si non, vous pouvez utiliser l’exemple HelloWorld SDK (\Program Files (x86) \Microsoft BizTalk Server *yourVersion*\SDK\Samples\Orchestrations\HelloWorld). 
* Avoir le chemin d’accès au fichier de liaison XML à votre projet BizTalk prêt. 
* Connaître votre compte VSTS, votre collection et détails de votre projet d’équipe.
* Être familiarisé avec les concepts de git, y compris le clonage et l’utilisation de référentiels. 
* Veillez [Feature Pack 1](https://www.microsoft.com/download/details.aspx?id=55100) est installé

## <a name="add-the-application-project"></a>Ajouter le projet d’application

1. Sur le serveur BizTalk, ouvrez votre solution (ProjectName.sln) dans Visual Studio. Ne sélectionnez pas de Visual Studio Blend.

2. Dans l’Explorateur de solutions, cliquez sur votre projet, puis sélectionnez **Build**. Assurez-vous que votre build terminée. Avec le bouton droit de votre projet, puis sélectionnez **déployer**. Assurez-vous que votre déploiement réussit.

3. Avec le bouton droit de votre solution, sélectionnez **ajouter**, puis sélectionnez **ajouter un nouveau projet**.

4. Sélectionnez le **projets BizTalk** onglet, sélectionnez **.NET Framework 4.6.1** à partir de la liste déroulante, puis sélectionnez **projet d’Application de BizTalk Server**. Entrez un nom (par exemple, appProjectHelloWorld), puis sélectionnez **OK**:  

    ![Ajouter le projet d’application](../core/media/add-application-project.png)

5. Dans l’Explorateur de solutions, cliquez sur votre projet nouvellement ajouté l’application (.btaproj), sélectionnez **ajouter**, sélectionnez **référence**. Développez le **projets** et vérifiez votre projet BizTalk (le projet que vous déployez à l’aide de VSTS). Sélectionnez **OK**.  
    Une fois ajouté, développez **références** sous votre projet d’application (par exemple, appProjectHelloWorld) pour afficher le projet BizTalk que vous venez d’ajouter. 

6. Dans l’Explorateur de solutions, cliquez sur votre projet d’application (.btaproj), sélectionnez **ajouter**, sélectionnez **élément existant**, et **ajouter** votre fichier XML de liaison.

7. Ouvrez les propriétés de binding.xml, puis définissez **copier dans le répertoire de sortie** à **toujours copier**. **Enregistrer** vos modifications :  

    ![Propriétés du fichier de liaison](../core/media/xml-binding-file-properties.png)


## <a name="configure-the-json-template"></a>Configurer le modèle JSON

1. Dans Visual Studio, dans votre projet d’application (.btaproj), ouvrez le `BizTalkServerInventory.json` fichier. 

2. Le modèle inclut les sections suivantes : 

    | | |
    |---|---|
    |BizTalkAssemblies | Les assemblys utilisés dans vos applications |
    |BindingFiles | Les fichiers de liaison que vous référencez|
    |DeploymentSequence | La séquence des éléments à installer|
    
    Exemple de modèle : 
    
    ![Image de modèle FP1 Json 1](../core/media/fp1-json-template-image-1.png)

    > [!IMPORTANT]
    > Selon la complexité de votre solution, les éléments que vous souhaitez dans la build doivent être référencées dans ce fichier de modèle JSON.

3. Dans `BizTalkAssemblies`, ajoutez les assemblys utilisés par votre projet BizTalk : 

    ```
    "BizTalkAssemblies": [
        {
            "Name": "AssemblyName"
            "Path": "PathToAssembly
        }
    ]
    ```

4. Dans `BindingsFiles`, ajoutez les fichiers de liaison pour votre projet BizTalk : 

    ```
    "BindingsFiles": [
        {
            "Name": "Binding File Name"
            "Path": "PathToBindingFile
        }
    ]
    ```

5. Dans `DeploymentSequence`, ajoutez les noms d’application dans l’ordre que vous souhaitez les déployé et installé sur le [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]: 

    ```
    "DeploymentSequence": [
        {
            "NameOfFirst", "NameOfSecond", "NameOfThird"
        }
    ]
    ```


6. **Enregistrer** vos modifications. Lorsque vous avez terminé, votre fichier .json ressemble à ceci : 

    ```
    {
      "$schema": "C:\\Program Files (x86)\\Microsoft BizTalk Server 2016\\Developer Tools\\BizTalkServerAppplicationSchema.json",
      "BizTalkAssemblies": [
        {
          "Name": "HelloWorld",
          "Path": "HelloWorld\\bin\\Release\\HelloWorld.dll"
        }
      ],
      "BindingsFiles": [
        {
          "Name": "HelloWorldBinding",
          "Path": "HelloWorld\\HelloWorldBinding.xml"
        }
      ],
      "DeploymentSequence": [
        "HelloWorld", "HelloWorldBinding"
      ]
    }
    ```

7. **Facultatif**. Avec le bouton droit de votre projet d’application (par exemple, appProjectHelloWorld), puis sélectionnez **propriétés**. Vous pouvez définir la version Debug ou Release une nouvelle valeur. Nous ne dans ces étapes, mais sachez que vous pouvez effectuer cela.  

    ![Définissez la version debug ou release](../core/media/application-project-version.png)

8. Avec le bouton droit de votre projet d’application (par exemple, appProjectHelloWorld), puis sélectionnez **Build**. Si elle réussit, un fichier zip est créé dans  ***yourApplicationProject*\bin\debug** dossier :  

    ![Générer le fichier zip](../core/media/application-project-zip-file.png)

9. Sélectionnez votre solution, puis sélectionnez le **Team Explorer** onglet. Sous VSTS, sélectionnez **connexion**.  

    ![Se connecter à Team Services](../core/media/connect-team-services.png)

10. Sélectionnez votre compte VSTS, votre collection et votre projet d’équipe. Sélectionnez **OK**. Si vous n’avez pas encore créé le compte VSTS, puis créer un ([étape 2 : créer le jeton VSTS](feature-pack-create-vsts-token.md) fournit quelques conseils). Une fois qu’elle est créée, revenez à cette étape et connectez-vous.  

    ![Sélectionnez votre projet et collection](../core/media/team-collections-projects.png)

11. Lorsque vous vous connectez, vous pouvez obtenir une invite pour cloner ce référentiel. Sélectionnez le **cloner ce référentiel** lien.  

    ![Cloner le référentiel](../core/media/vsts-clone-repository.png)

12. Notez l’URL et les chemins d’accès, puis sélectionnez **Clone**:  

    ![Chemins d’accès du référentiel](../core/media/clone-repo-paths.png)

Une fois terminé, la tâche de déploiement de Service Visual Studio Team honore les fichiers requis et la séquence d’installation. 

> [!TIP]
> Si vous apportez des modifications à votre projet une fois que vous clonez dans git, vous pouvez **étape** vos modifications, puis **Push**, dans Visual Studio. 

## <a name="what-you-did"></a>Ce que vous avez fait

Dans votre projet BizTalk, vous avez ajouté un projet d’Application de BizTalk (.btaproj). Ce projet est utilisé pour automatiser les déploiements de vos projets BizTalk Server à l’aide de VSTS. Une fois que vous avez créé le projet d’application, vous avez ajouté une référence à votre projet d’application BizTalk. Ensuite, de mise à jour un fichier JSON qui indique le déploiement automatisé, les DLL à déployer, le fichier de liaison à utiliser et la commande pour déployer les applications. 

## <a name="next-steps"></a>Étapes suivantes
[Étape 2 : Créer le jeton VSTS](feature-pack-create-vsts-token.md)  
[Étape 3 : Création de la build et définitions de version](feature-pack-add-build-release-definitions.md)  
[Configurer les variables et les jetons de l’environnement](configure-environmental-tokens-and-variables-for-automatic-deployment.md)