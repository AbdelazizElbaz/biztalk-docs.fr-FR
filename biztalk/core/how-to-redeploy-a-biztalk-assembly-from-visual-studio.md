---
title: "Comment redéployer un Assembly BizTalk à partir de Visual Studio | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5c4bb627-48de-4874-bb25-af2c513dbc51
caps.latest.revision: "41"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 361d2bccc783e7bfc7aa6cb0cd1f3eab51d8e640
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-redeploy-a-biztalk-assembly-from-visual-studio"></a>Redéploiement d'un assembly BizTalk à partir de Visual Studio
Au cours du développement d'un assembly, vous êtes amené à déployer l'assembly, à le tester, à le modifier et à le redéployer, et ce de manière répétée. Dans les versions précédentes de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], lorsque vous vouliez redéployer un assembly sans modifier son numéro de version, il vous fallait d'abord l'arrêter manuellement, le désinscrire et annuler la liaison des artefacts qu'il contenait dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] avant de le supprimer de la base de données de gestion (configuration) BizTalk. En outre, après le redéploiement de l'assembly, vous deviez lier, inscrire et démarrer ses artefacts dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
 Avec [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)], cependant, lorsque vous activez l'option Redéployer de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] effectue de manière automatique toutes les étapes nécessaires au redéploiement de l'assembly à votre place. Bien que vous puissiez redéployer un assembly au niveau du projet (par exemple, en cliquant avec le bouton droit sur le projet dans l'Explorateur de solutions, puis en cliquant sur Déployer) pour redéployer un assembly unique, il est vivement recommandé de toujours redéployer les assemblys au niveau de la solution (en cliquant avec le bouton droit sur la solution et en sélectionnant Déployer). Cela permet de redéployer tous les assemblys de la solution d'un coup et de gérer toutes les étapes nécessaires en présence de dépendances (voir plus loin).  
  
> [!IMPORTANT]
>  Bien qu'il existe des cas où l'assembly peut être redéployé au niveau du projet, il est de mise de toujours le redéployer au niveau de la solution.  
  
 Lorsque vous redéployez un assembly, gardez les points importants suivants à l'esprit :  
  
-   **Vous devez installer le nouvel assembly dans le GAC.** Lorsque vous redéployez un assembly, vous devez toujours installer la nouvelle version de l’assembly dans le GAC, comme décrit dans [comment installer un Assembly dans le GAC](../core/how-to-install-an-assembly-in-the-gac.md). Vous pouvez procéder à cette installation après le redéploiement de l'assembly.  
  
-   **Vous devez toujours redéployer au niveau de la solution lorsqu’il existe des dépendances.** Si votre solution comporte plusieurs assemblys et que l'un ou plusieurs d'entre eux présentent une dépendance avec l'assembly à redéployer, vous devez redéployer les assemblys au niveau de la solution. C’est parce que lorsque vous redéployez un assembly au niveau du projet, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] arrête, désinscrire, détacher et supprimer les artefacts dans tous les assemblys qui soit dépendent cet assembly dont dépend cet assembly. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]les étapes supplémentaires à déployer, lier, inscrire et démarrer les artefacts prendront. Lorsque vous redéployez la solution entière, en revanche, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] effectue automatiquement les opérations nécessaires à l'annulation du déploiement et au redéploiement de tous les artefacts de la solution en fonction de leurs dépendances.  
  
-   **Vous devrez peut-être à redéployer manuellement les assemblys dépendants.** [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Annule toujours le déploiement des assemblys dépendants, mais dans les cas suivants, vous devez effectuer les étapes supplémentaires à déployer, lier et inscrire les artefacts de chaque assembly dépendant après le redéploiement de l’assembly dont dépend l’assembly :  
  
    -   si vous redéployez au niveau du projet un assembly dont dépend un autre assembly de la même solution ;  
  
    -   si vous redéployez un assembly au niveau de la solution, mais qu'un assembly dépendant existe dans une autre solution.  
  
     Par exemple, si vous deviez redéployer uniquement l'assembly 3 indiqué dans le schéma suivant, une fois le redéploiement effectué, il vous faudrait déployer, lier et inscrire les artefacts de l'assembly 2 avant de déployer, de lier et d'inscrire les artefacts de l'assembly 1.  
  
     ![Assemblys avec dépendances](../core/media/assemblydependencies.gif "AssemblyDependencies")  
  
     Une autre approche consiste à éviter le déploiement inutile des assemblys principaux qui n'ont pas été modifiés.  Par exemple, dans le schéma ci-dessus, si d'autres assemblys dépendent des assemblys 2 et 3, et si aucun de ces assemblys n'a été mis à jour.  Désactivez le **déployer** option dans le Gestionnaire de configuration pour l’Assembly 2 et les projets Assembly 3. Ainsi, le déploiement des assemblys externes qui dépendent des assemblys 2 et 3 ne sera pas annulé et un redéploiement ne sera pas nécessaire. Pour plus d’informations, consultez [comment définir les propriétés de déploiement dans Visual Studio](../core/how-to-set-deployment-properties-in-visual-studio.md).  
  
-   **Vous devez redémarrer les instances d’hôte.** Lorsque vous redéployez un assembly qui contient une orchestration sans modifier le numéro de version de l'assembly, l'assembly existant est remplacé dans la base de données de gestion BizTalk. Pour que la modification entre en vigueur, cependant, vous devez redémarrer chaque instance de l'hôte auquel est liée l'orchestration. Vous avez la possibilité de configurer le redémarrage automatique de toutes les instances d'hôte sur l'ordinateur local au moment du redéploiement d'un assembly. Pour obtenir des instructions, consultez [comment définir les propriétés de déploiement dans Visual Studio](../core/how-to-set-deployment-properties-in-visual-studio.md). Vous pouvez également arrêter et démarrer chaque instance d’hôte, comme décrit dans [comment arrêter une Instance d’hôte](../core/how-to-stop-a-host-instance.md) et [comment démarrer une Instance d’hôte](../core/how-to-start-a-host-instance.md).  
  
> [!IMPORTANT]
>  L'option Redéployer ignorant le contrôle de version, il est recommandé de ne l'utiliser que lors du développement.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe des administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. En outre, votre compte doit également disposer d'une autorisation de lecture/écriture sur le système de fichiers local et le Global Assembly Cache (GAC). Le compte des administrateurs de l'ordinateur local dispose de ces autorisations.  
  
## <a name="to-redeploy-a-biztalk-solution"></a>Pour redéployer une solution BizTalk  
  
#### <a name="using-visual-studio-solution-explorer"></a>Utilisation de l'Explorateur de solutions de Visual Studio  
  
1.  Vérifiez que l’option redéployer est activée dans les propriétés de déploiement pour chaque projet dans la solution, comme décrit dans [comment définir les propriétés de déploiement dans Visual Studio](../core/how-to-set-deployment-properties-in-visual-studio.md). Cette option est activée par défaut.  
  
2.  Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] l’Explorateur de solutions, cliquez sur une solution BizTalk, puis cliquez sur **déployer**.  
  
     Les assemblys de la solution sont déployés dans l'application BizTalk spécifiée. L'état du processus de compilation et de déploiement s'affiche dans l'angle inférieur gauche de la page.  
  
#### <a name="using-the-visual-studio-command-prompt"></a>Utilisation de l'invite de commandes Visual Studio  
  
1.  Vérifiez que l’option redéployer est activée dans les propriétés de déploiement pour chaque projet dans la solution, comme décrit dans [comment définir les propriétés de déploiement dans Visual Studio](../core/how-to-set-deployment-properties-in-visual-studio.md). Cette option est activée par défaut.  
  
2.  Démarrer **invite de commandes Visual Studio**.  
  
3.  Tapez la commande suivante en utilisant les valeurs appropriées, comme décrit dans le tableau suivant :  
  
     **devenv / déployer***Nomconfigsoln* *SolutionName*   
  
     Exemple :  
  
     **devenv / déployer la version « C:\Documents et Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln »**  
  
    |Paramètre|Valeur|  
    |---------------|-----------|  
    |**/ déployer**|Déploie une solution après une génération ou une régénération.|  
    |*Nomconfigsoln*|Nom de la configuration de solution qui sera utilisée pour générer la solution nommée dans SolutionName.|  
    |*SolutionName*|Chemin d'accès complet et nom du fichier de la solution.|  
  
## <a name="see-also"></a>Voir aussi  
 [Déploiement d’assemblys BizTalk à partir de Visual Studio dans une Application BizTalk](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md)