---
title: "Étape 2 : créer un jeton VSTS et installer l’agent | Documents Microsoft"
description: "Créer le clone de jeton, l’accès de sécurité VSTS à votre projet VSTS dans Visual Studio et installez l’agent de build pour automatiser le déploiement de vos projets BizTalk Server"
ms.custom: 
ms.date: 11/20/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 77296d9f2325bebaba4f4fa1ce7c55034ef1ead6
ms.sourcegitcommit: f65e8ed2b8c18cded26b9d60868fb6a56bcc1205
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="step-2-create-the-token--install-the-agent"></a>Étape 2 : Créer le jeton et installer l’agent

Un jeton d’accès personnel (PAT) est créé dans Visual Studio Team Services. Ce jeton est votre mot de passe et est utilisé par l’agent de build VSTS pour s’authentifier. Le jeton s’affiche uniquement lorsque vous la créez. Après cela, il ne s’affiche plus. Par conséquent, une fois que vous le créez, enregistrez-le dans un autre fichier dans un emplacement en mesure de se souvenir. 

Plus d’informations sur PAT à [authentifier l’accès avec des jetons d’accès personnels pour VSTS et TFS](https://docs.microsoft.com/vsts/accounts/use-personal-access-tokens-to-authenticate). 

Après avoir créé le jeton, vous installez l’agent de build et configurez pour utiliser ce jeton. 

## <a name="before-you-begin"></a>Avant de commencer
Complète [l’étape 1 - projet d’ajouter une Application et de mettre à jour de json](feature-pack-add-application-project.md).

## <a name="sign-into-vsts-and-create-the-token"></a>Se connecter dans VSTS et créer le jeton
1. Accédez à [https://app.vsaex.visualstudio.com/go/profile](https://app.vsaex.visualstudio.com/go/profile)et connectez-vous avec votre compte professionnel ou scolaire. Une fois que vous vous connectez, votre compte VSTS est répertorié. Dans l’exemple suivant, le compte est **mandiaprojects.visualstudio.com**.  

    ![Compte VSTS](../core/media/team-services-accounts.png)

    Si vous n’avez pas un compte, sélectionnez **créer nouveau compte**et entrez un nom. Pour gérer votre code, choisissez vos préférences personnelles entre **Git ou Team Foundation Version Control**. Lorsque vous avez terminé, votre nouveau compte est créé et un site même *https://YourAccountName.visualstudio.com/MyFirstProject* s’ouvre :  

    ![GIT ou TFS](../core/media/git-or-team-foundation.png)

2. Ouvrez votre compte VSTS (https://*YourAccountName*. visualstudio.com). Sélectionnez l’icône dans le coin supérieur droit, puis sélectionnez **sécurité**: 

    ![Ouvrez la sécurité de votre compte](../core/media/vsts-account-security.png)

3. **Jetons d’accès personnels** s’ouvre automatiquement. Si vous disposez d’un agent existant, sélectionnez-le et confirmez **Pools d’agents (lecture, gérer)** est sélectionnée :

    ![Lire et de gérer les pools d’agents-](../core/media/agent-pools-read-manage.png)

    > [!IMPORTANT]
    > Vous devez connaître le jeton d’accès. Si vous n’et que vous n’avez pas à noter n’importe où, il ne peut pas être récupéré. Dans ce cas, créez un nouvel agent. 

    Si vous n’avez pas un agent existant, sélectionnez **ajouter**, entrez une description, définir la date d’expiration et sélectionnez votre compte. Dans **sélectionné étendues**, sélectionnez **Pools d’agents (lecture, gérer)**: 

    ![Créer le nouvel agent - lecture et gérer](../core/media/vsts-new-build-agent.png)

    Sélectionnez **créer un jeton**. **Notez la valeur du jeton ; vous avez besoin dans les futures opérations.**

4. Sélectionnez **Code**, puis sélectionnez **Clone dans Visual Studio**:  

    ![Dans votre projet, sélectionnez le Code](../core/media/vsts-project-code.png)  

    ![Cloner dans Visual Studio](../core/media/vsts-clone-in-visual-studio.png)

5. Visual Studio s’ouvre. Dans Visual Studio, ouvrez votre solution BizTalk. 

## <a name="install-the-build-agent"></a>Installer l’Agent de Build

L’agent de build est installé sur l’ordinateur de développement de BizTalk. Si vous utilisez des groupes de déploiement, l’agent de build est installé sur tous les serveurs BizTalk que vous voulez procéder au déploiement. Les étapes suivantes vous montrent comment installer l’agent de build sur un ordinateur unique. Pour plus d’informations sur l’utilisation de groupes de déploiement, consultez [groupes de déploiement](https://docs.microsoft.com/vsts/build-release/concepts/definitions/release/deployment-groups/index).

1. Ouvrez votre compte VSTS et le projet, qui est un élément comme *https://YourAccountName.visualstudio.com/MyFirstProject*. Sélectionnez l’icône des paramètres, puis sélectionnez **files d’attente de l’Agent**:  

    ![Paramètres > files d’attente de l’Agent](../core/media/vsts-settings-agent-queues.png)

2. Sélectionnez le **par défaut** agent, puis sélectionnez **télécharger l’Agent**. Sélectionnez le **télécharger** bouton et enregistrez le fichier à votre **télécharge** dossiers.

3. Les étapes d’installation ouvrent automatiquement. Suivez ces étapes pour plus d’informations plus récentes. Voici quelques conseils : 

    1. Ouvrez Windows PowerShell en tant qu’administrateur.

    2. Pour créer l’agent, entrez : 

        ```powershell
        PS C:\> mkdir agent ; cd agent  

        PS C:\agent> Add-Type -AssemblyName System.IO.Compression.FileSystem ; [System.IO.Compression.ZipFile]::ExtractToDirectory("$HOME\Downloads\vsts-agent-win7-x64-2.124.0.zip", "$PWD")
        ```
    
        Les modifications de version de fichier de l’agent vsts. Par conséquent, suivez les étapes d’installation VSTS pour des détails spécifiques. Une fois que vous avez atteint Entrez, il peut prendre quelques minutes pour l’invite à retourner. 

    3. Pour configurer l’agent, entrez : 

        ```powershell
        PS C:\agent> .\config.cmd
        ```

    4. Entrez les informations suivantes :  
        
        | Propriété | Valeur |
        | --- | --- |
        | URL du serveur| https://{your-account}.VisualStudio.com |
        | Type d’authentification | PAT |
        | Jeton d’accès personnel | Collez votre jeton VSTS |
        | Pool d’agents | Entrez la valeur par défaut |
        | Nom de l’agent | Entrez la valeur par défaut |
        | Remplacer | *S’affiche uniquement si vous disposez d’un agent existant* |
        | Dossier de travail | Entrez la valeur par défaut |
        | Exécutez l’agent en tant que service | O |
        | Compte d'utilisateur | Il vous revient de, mais vous risquez de rencontrer un problème d’autorisations. <br/><br/>Songez à votre session compte actuel, qui est un administrateur local |

    5. Lorsque vous avez terminé, votre fenêtre PowerShell ressemble à ceci :  
    
        ![Installation de l’agent](../core/media/vsts-agent-powershell-install.png)

4. Ouvrez services.msc pour voir le nouveau service. Il doit être en cours d’exécution :  

    ![Service est en cours d’exécution.](../core/media/vsts-service.png)

    Si le service ne parvient pas à démarrer, [supprimer et reconfigurer un agent](https://docs.microsoft.com/vsts/build-release/actions/agents/v2-windows) à l’aide d’un compte avec des privilèges plus.


## <a name="what-you-did"></a>Ce que vous avez fait

Vous connectez à votre compte VSTS et créé un jeton de sécurité. Ce jeton de sécurité est similaire à un mot de passe et vous donne accès à votre projet VSTS. Il s’affiche uniquement une fois, par conséquent, être que vous l’avez enregistré. Vous également cloné votre projet VSTS dans Visual Studio et créé un agent qui s’exécute en tant que service sur votre ordinateur de développement de BizTalk. Cet agent utilise le jeton de sécurité. 

## <a name="next-steps"></a>Étapes suivantes
[Étape 3 : Création de la build et définitions de version](feature-pack-add-build-release-definitions.md)  
[Configurer les variables et les jetons de l’environnement](configure-environmental-tokens-and-variables-for-automatic-deployment.md)