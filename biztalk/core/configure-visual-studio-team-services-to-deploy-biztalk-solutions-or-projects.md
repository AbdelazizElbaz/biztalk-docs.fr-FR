---
title: "Configurer Visual Studio Team Services pour déployer des solutions BizTalk Server ou des projets | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2555712a-dfe4-420e-9a61-1d1a6d98c322
caps.latest.revision: "6"
author: tordgladnordahl
ms.author: tonordah
manager: anneta
ms.openlocfilehash: 6368300c714811d5b3c42e07ebb804d26362bf85
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configure-visual-studio-team-services-to-deploy-biztalk-server-solutions-or-projects"></a>Configurer Visual Studio Team Services pour déployer des solutions BizTalk Server ou des projets
Configurer VSTS pour déployer automatiquement [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] projets. 

**En commençant par [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [!INCLUDE[featurepack1](../includes/featurepack1.md)]** , vous pouvez automatiquement générer votre [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] solutions à l’aide de Visual Studio Team Services (VSTS). 

Cette rubrique vous montre comment installer et configurer Visual Studio Team Services (VSTS) pour utiliser le déploiement automatique de BizTalk. 

> [!IMPORTANT]
> L’agent VSTS ne peut être installé que sur un [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] dans le groupe. 

## <a name="prerequisites"></a>Conditions préalables

* Installer [Feature Pack 1](https://www.microsoft.com/download/details.aspx?id=55100) sur votre[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]
* Certains expérience et la base de connaissances avec la création et l’utilisation avec les définitions de VSTS. Si vous êtes débutant VSTS, il peut s’agir de bonnes ressources : 

  [Vue d’ensemble de Visual Studio Team Services](https://www.visualstudio.com/docs/overview)  
  [L’élément de configuration/CD pour les internautes novices](https://www.visualstudio.com/docs/build/get-started/ci-cd-part-1)
  

## <a name="create-a-vsts-account-and-create-a-definition"></a>Créer un compte VSTS et créer une définition

1. Dans un navigateur web, accédez à votre [le profil Visual Studio online](https://app.vsaex.visualstudio.com/go/profile), connectez-vous, puis sélectionnez un **créer nouveau compte**:

    ![Créer un nouveau compte](../core/media/create-a-new-account.png)

2. Entrez un nom pour le compte de votre référentiel de code source par défaut et sélectionnez **continuer**:

    ![Créez un nouveau projet](../core/media/create-a-new-project.png)

3. Votre nouveau compte est créé et un site même `https://YourAccountName.visualstudio.com/MyFirstProject` s’ouvre.
    
4. Installer le [service de déployer l’Application BizTalk](https://marketplace.visualstudio.com/items?itemName=ms-biztalk.deploy-biztalk-application) pour le compte que vous venez de créer.

    ![Nouvelle version de build](../core/media/build-new-release.png)

5. Vous pouvez obtenir des invites. Confirmer pour continuer. Assurez-vous que vous êtes connecté à votre projet dans VSTS.

6. Sélectionnez **Build et version**et créer un **nouveau** définition de build :

    ![Sélectionner la Build et mise en production](../core/media/select-build-and-release.png)

    > [!TIP]
    > Vérifiez que vous êtes à `https://YourAccountName.visualstudio.com/MyFirstProject`. Dans le cas contraire, le **nouveau** ou **nouvelle définition** boutons ne peuvent pas être il. 
    
7. Sélectionnez le **Visual Studio** modèle, puis sélectionnez **suivant**:

    ![Sélectionnez visual studio, cliquez sur Suivant](../core/media/select-visual-studio-and-click-next.png)

8. Passez en revue vos paramètres, puis sélectionnez **créer**.

9. Supprimer les étapes que vous n’avez pas besoin. Pour ce didacticiel, vous pouvez supprimer les éléments suivants : 
* Restauration de NuGet
* Assemblys de test
* Publier le chemin d’accès des symboles 

    ![Supprimer des étapes inutiles](../core/media/delete-steps-not-needed.png)

10. **Facultatif**. Si vous souhaitez activer l’intégration continue (CI), sélectionnez **déclencheurs** dans le menu et vérifiez **l’intégration continue (CI)**.

Ensuite, installez l’agent sur votre [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]. 

## <a name="install-the-agent"></a>Installer l’Agent

Pour la solution fonctionne, activer un Agent Windows privé sur votre ordinateur local. N’oubliez pas, **l’agent doit être installé que sur un seul [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] dans le groupe**. 

1. Dans la définition, sélectionnez le **général** onglet (en haut).
2. Pour le **file d’attente de l’agent par défaut** propriété, sélectionnez le **par défaut** agent à partir de la liste. 
3. Sélectionnez **gérer** à côté du **file d’attente de l’agent par défaut** propriété. Un nouvel onglet de navigateur s’ouvre.

    ![Créer le nouvel agent de gestion](../core/media/create-new-management-agent.png)

4. Dans le volet gauche, la file d’attente par défaut est sélectionné. Si un agent est déjà répertorié, en ligne, vous avez terminé. Vous disposez d’un agent installé et en cours d’exécution. 

    Si un agent n’est pas répertorié, puis sélectionnez **agent de téléchargement**et continuer l’installation sur votre [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]. **Accédez à [déployer un agent sur Windows](https://www.visualstudio.com/docs/build/actions/agents/v2-windows) pour connaître la procédure** pour installer l’agent et démarrer un agent. 

    > [!IMPORTANT]
    > Suivez les étapes indiquées dans [déployer un agent sur Windows](https://www.visualstudio.com/docs/build/actions/agents/v2-windows). N’ignorez pas cette étape. 

5. Avec l’agent par défaut **Online**, revenez à la **général** onglet dans votre définition, puis confirmez **par défaut** est sélectionné pour le **file d’attente de l’agent par défaut**.
6. **Enregistrer** et **nouvelle build en file d’attente**.

Ensuite, créez la définition de déploiement d’Application BizTalk Server.

## <a name="create-the-biztalk-deployment-definition"></a>Créer la définition de déploiement BizTalk

1. Sélectionnez le **génère** onglet, sélectionnez **toutes les définitions de**, puis sélectionnez **nouveau**:

    ![Créer la définition de la nouvelle version](../core/media/create-new-release-defintion.png)

2. Sélectionnez le **vide** modèle, puis sélectionnez **suivant**:

    ![Créer la nouvelle définition d’un modèle vide](../core/media/create-new-defintion-from-an-empty-template.png)

3. Sélectionnez votre **référentiel** source et **branche** pour la définition.
4. **Facultatif**. Sélectionnez **intégration continue**.
5. Sélectionnez le **par défaut** agent à partir de la liste de la file d’attente, puis sélectionnez **créer**.
6. **Étape de génération ajouter**, sélectionnez le **déploiement d’Application BizTalk Server** de tâches, puis sélectionnez **ajouter**. **Fermer** le catalogue de la tâche.

    ![Ajouter nouveau déploiement de définition](../core/media/add-new-deploy-definition.png)

7. Sélectionnez le **nom de l’opération** vous souhaitez utiliser :
    * **Créer la nouvelle Application BizTalk** déploie une nouvelle application. Si l’application existe déjà, il désinstalle les applications actuelles (point) et installe la nouvelle application. Si l’intégration continue est activée, elle automatiquement redéploie l’application lorsqu’elle est mise à jour dans le référentiel.
    * **Mettre à jour une Application BizTalk existant** ajoute des modifications, par exemple **schémas** à une application déjà en cours d’exécution. Il ne nécessite pas un redéploiement complet de l’application.
8. Entrez le **nom de l’Application** dans votre [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] environnement.
9. Dans **chemin d’accès du package de déploiement**, sélectionnez le chemin d’accès vers le fichier zip dans votre référentiel.
10. Sélectionnez **déclencheurs** , dans le menu, activez **intégration continue**et sélectionnez le bon **branche** pour la build.
11. Sélectionnez **enregistrer**:

    ![Enregistrer la nouvelle définition de build](../core/media/save-the-new-build-definition.png)

12. Nommez le nouveau **définition**et définissez le chemin d’accès correct. 
13. Une fois que la définition est enregistrée, sélectionnez **la nouvelle build en file d’attente**. Ensuite, sélectionnez le **agent file d’attente**et ajouter un commentaire à la validation.

## <a name="next-step"></a>Étape suivante
[Configurer le modèle JSON pour le déploiement automatique](../core/configure-the-json-template-for-automatic-deployment.md)