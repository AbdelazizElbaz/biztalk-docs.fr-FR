---
title: "Étape 1 : Déployer les projets | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0467c140-1f4c-4cfa-b46f-dc1d0f8755d4
caps.latest.revision: "44"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: eb4262b2bb424a339f866f3b4a14ae03c2e507f6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-1-deploy-the-projects"></a>Étape 1 : déployer les projets
![Étape 1 sur 3](../adapters-and-accelerators/adapter-oracle-database/media/step-1of3.gif "Step_1of3")  
  
 **Durée :** 5 minutes  
  
 **Objectif :** dans cette étape, vous déployez les projets EAISchemas et EAIOrchestration.  
  
 **Objectif :** lorsque vous déployez un projet ou une solution dans Visual Studio, les assemblys sont automatiquement générés et déployés dans l’application spécifiée. Dans le cadre de ce processus, l'assembly et les orchestrations, schémas et mappages qu'il contient (appelés « artefacts ») sont importés dans la base de données de gestion BizTalk locale et associés à l'application spécifiée.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Les conditions suivantes sont requises avant de commencer cette étape :  
  
-   Avant de commencer cette étape, vous devez étudier les leçons suivantes :  
  
    -   [Leçon 1 : Définir des schémas et un mappage](../core/lesson-1-define-schemas-and-a-map.md)  
  
    -   [Leçon 2 : Définir le processus d’entreprise](../core/lesson-2-define-the-business-process.md)  
  
-   Vous devez ouvrir une session en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
-   Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devez exécuter Visual Studio avec des privilèges d'administrateur.  
  
## <a name="procedures"></a>Procédures  
 Pour déployer l'application à l'aide de Visual Studio, vous devez vous connecter à Windows en tant que membre du groupe d'administrateurs BizTalk Server et exécuter Visual Studio en tant qu'administrateur.  Sinon, une erreur « Accès refusé » se produira.  
  
#### <a name="to-open-the-solution-with-administrative-privileges"></a>Pour ouvrir la solution avec des privilèges d'administrateur  
  
1.  Connectez-vous à Windows en tant que membre du groupe d'administrateurs de BizTalk Server.  
  
2.  Démarrer **Microsoft Visual Studio** en tant qu’administrateur.  
  
3.  Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], dans le **fichier** menu, pointez sur **ouvrir**, puis cliquez sur **projet/Solution**.  
  
4.  Dans le **ouvrir le projet** boîte de dialogue, cliquez sur Parcourir pour le **EAISolution.sln** fichier solution du projet, puis cliquez sur **ouvrir**.  
  
 Le processus de déploiement requiert la signature avec un nom fort de l'assembly.  Vous devez vous connecter à vos assemblys en associant le projet avec un fichier de clé de nom fort assembly.  Ce fichier est fourni dans le cadre du didacticiel.  
  
 L'application BizTalk est une fonctionnalité de BizTalk Server qui facilite et accélère le déploiement, la gestion et la résolution des incidents sur les solutions d'entreprise BizTalk Server. Une application BizTalk est un regroupement logique d'éléments, appelés « artefacts », qui sont utilisés dans une solution d'entreprise BizTalk Server. Nous pouvons spécifier un nom d'application pour un projet.  Le processus de déploiement crée automatiquement une nouvelle application qui porte le nom spécifié s'il n'existe pas.  
  
#### <a name="to-configure-and-deploy-the-projects"></a>Pour configurer et déployer les projets  
  
1.  Dans l’Explorateur de solutions, cliquez sur le **EAISchemas** de projet, puis cliquez sur **propriétés**.  
  
2.  Cliquez sur le **signature** onglet, sélectionnez **signer l’assembly**.  
  
3.  Dans la liste déroulante de la **choisir un fichier de clé de nom fort** boîte, sélectionnez  **\<Parcourir... >**.  
  
4.  Dans le **sélectionner le fichier** boîte de dialogue, accédez à **C:\BTStutorials**, cliquez sur **btsTutorials.snk**, puis cliquez sur **ouvrir**.  
  
5.  Cliquez sur le **déploiement** onglet, dans la zone à droite de **nom de l’Application**, type `EAISolution`.  
  
6.  Dans la liste déroulante dans la zone à droite de **redéployer**, sélectionnez **True**.  
  
7.  Dans l’Explorateur de solutions, cliquez sur **EAISchemas**, puis cliquez sur **déployer**.  La fenêtre Sortie doit s'afficher :  
  
    ```  
    ========== Build: 1 succeeded or up-to-date, 0 failed, 0 skipped ==========  
    ========== Deploy: 1 succeeded, 0 failed, 0 skipped ==========  
  
    ```  
  
8.  Répétez les étapes 1 à 7 pour déployer le projet EAIOrchestration.  
  
## <a name="what-did-i-just-do"></a>Actions effectuées  
 Au cours de cette étape, vous avez déployé les projets EAISchemas et EAIOrchestration.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Vous allez créer les ports physiques et les lier aux ports logiques de l'orchestration.  
  
## <a name="see-also"></a>Voir aussi  
 [Étape 2 : Configurer et démarrer l’Application](../core/step-2-configure-and-start-the-application1.md)   
 [Étape 3 : Tester la Solution](../core/step-3-test-the-solution2.md)