---
title: "Comment déployer un Assembly BizTalk à partir de Visual Studio | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 69d70c52-3e71-4eb2-876e-b467c7ca24b7
caps.latest.revision: "39"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8fc232edf6d99e31b5679932eb19873481fa579b
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="how-to-deploy-a-biztalk-assembly-from-visual-studio"></a>Déploiement d'un assembly BizTalk à partir de Visual Studio
Cette rubrique fournit des instructions sur l'utilisation de l'Explorateur de solutions [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] ou l'invite de commandes [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] pour déployer des assemblys BizTalk à partir de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] dans une application BizTalk. Bien que vous puissiez déployer un assembly unique au niveau du projet (par exemple, en cliquant avec le bouton droit sur le projet, puis en cliquant sur Déployer), ou déployer tous les assemblys de la solution en une seule opération au niveau de la solution (par exemple, en cliquant avec le bouton droit sur la solution, puis en cliquant sur Déployer), il est fortement conseillé de déployer tous les assemblys simultanément au niveau de la solution.  
  
 Avec les versions antérieures de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], si vous souhaitiez déployer plusieurs assemblys en une solution, et que certains d'entre eux présentaient des dépendances par rapport à d'autres assemblys, vous deviez déployer les assemblys individuellement, dans l'ordre inverse de leurs dépendances. Par exemple, si l'Assembly1 présentait une dépendance vis à vis de l'Assembly2, vous deviez déployer l'Assembly2 d'abord, puis l'Assembly1.  
  
 C'est toujours le cas si vous déployez les assemblys au niveau du projet. Avec BizTalk Server, toutefois, lorsque vous déployez les assemblys de niveau de la solution, au lieu de niveau du projet, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] se charge automatiquement de toutes les étapes de déploiement, y compris pour déployer des assemblys dans le bon ordre. Par conséquent, pour simplifier le déploiement, si un autre assembly dépend de celui que vous déployez, vous avez intérêt à effectuer le déploiement des assemblys au niveau de la solution.  
  
 Lorsque vous sélectionnez l'option de déploiement d'un projet ou d'une solution à partir de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], le ou les assemblys sont automatiquement compilés et déployés dans l'application BizTalk spécifiée dans le groupe BizTalk local. Si l'application n'existe pas encore dans le groupe, le déploiement la crée automatiquement. Les assemblys et les artefacts qu'ils contiennent sont enregistrés et leurs données sont stockées dans la base de données (de configuration) de gestion BizTalk pour ce groupe BizTalk. En outre, si vous spécifiez cette option dans les propriétés de déploiement pour le projet, les assemblys sont ajoutés au GAC (Global Assembly Cache).  
  
 Un « artefact » est un élément inclus dans une application BizTalk, y compris les ressources avec lesquelles vous travaillez dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], par exemple les assemblys et orchestrations ainsi que les autres éléments que vous créez ou ajoutez après avoir déployé l'application, comme les ports d'envoi et de réception, les certificats et les scripts. Une fois l'assembly déployé, vous pouvez afficher et gérer ses artefacts dans le nœud Applications de la console [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]. Chaque application est stockée dans son propre dossier, les sous-dossiers contenant les artefacts de l'application. Pour plus d’informations, consultez [à l’aide de la Console Administration de BizTalk Server](../core/using-the-biztalk-server-administration-console.md). Pour plus d’informations sur la création et la gestion des applications, consultez [déploiement et la gestion des Applications BizTalk](../core/deploying-and-managing-biztalk-applications.md).  
  
 Avant de déployer un assembly, vous devez procédez comme suit :  
  
-   Créer un fichier de clé de nom fort assembly et assigné à chaque projet, comme décrit dans [comment configurer un fichier de clé de Assembly de nom fort](../core/how-to-configure-a-strong-name-assembly-key-file.md).  
  
-   Définissez les propriétés de déploiement pour le projet, comme décrit dans [comment définir les propriétés de déploiement dans Visual Studio](../core/how-to-set-deployment-properties-in-visual-studio.md).  
  
-   Si vous avez déjà déployé l'assembly, activez l'option de redéploiement pour le projet. Pour obtenir des instructions et autres informations importantes sur le redéploiement, consultez [comment redéployer un BizTalk Assembly à partir de Visual Studio](../core/how-to-redeploy-a-biztalk-assembly-from-visual-studio.md).  
  
> [!IMPORTANT]
>  Vous ne devez jamais exécuter les tâches décrites dans cette rubrique sur un ordinateur de production. En phase de développement, les développeurs redéploient souvent les assemblys à partir de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]. Pour activer le redéploiement, [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] peut annuler le déploiement, supprimer la liaison, arrêter et désinscrire les artefacts existant dans les mêmes ou dans différentes applications. Bien que tout ceci soit nécessaire et approprié à l'environnement de développement, cela peut entraîner des conséquences inattendues et indésirables dans l'environnement de production. En outre, afin d'éviter qu'un développeur ne tente de déployer un assembly à partir de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] sur un ordinateur de production, il est déconseillé d'installer [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] sur les ordinateurs de production.  
  
> [!NOTE]
>  La stratégie de sécurité d'exécution de .NET Framework empêche le déploiement des assemblys à partir d'un partage réseau par défaut. Si vous tentez de déployer un assembly à partir d'un partage réseau et rencontrez des difficultés, adressez-vous à l'administrateur de la sécurité .NET Framework ou consultez « Gestion de la stratégie de sécurité » dans la collection combinée [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter les procédures décrites dans cette rubrique, vous devez ouvrir une session à l'aide d'un compte membre du groupe Administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. If, dans **déploiement** propriétés, vous avez activé l’option Installer un assembly dans le global assembly cache (GAC), vous devez également les autorisations de lecture/écriture sur le GAC. Le compte des administrateurs de l'ordinateur local dispose de cette autorisation. Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
## <a name="to-deploy-a-biztalk-assembly-or-assemblies"></a>Déploiement d'un ou plusieurs assemblys BizTalk  
  
#### <a name="using-visual-studio-solution-explorer"></a>Utilisation de l'Explorateur de solutions de Visual Studio  
  
-   Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] l’Explorateur de solutions, cliquez sur un projet ou solution BizTalk, puis cliquez sur **déployer**.  
  
     L'assembly du projet ou les assemblys de la solution sont déployés dans l'application BizTalk spécifiée. L'état du processus de compilation et de déploiement s'affiche dans l'angle inférieur gauche de la page.  
  
#### <a name="using-the-visual-studio-command-prompt"></a>Utilisation de l'invite de commandes Visual Studio  
  
1.  Démarrer **invite de commandes Visual Studio**.  
  
2.  Tapez la commande suivante en utilisant les valeurs appropriées, comme décrit dans le tableau suivant :  
  
     **devenv / déployer***Nomconfigsoln* *SolutionName* [**/projet** *NomProj*] [**/ /projectconfig** *ProjConfigName*]  
  
     Exemple :  
  
     **devenv, déployer la version « C:\Documents et Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln », « MyBizTalkApp\MyBizTalkApp.csproj » /projectconfig version du projet**  
  
    |Paramètre|Valeur|  
    |---------------|-----------|  
    |**/ déployer**|Déploie une solution après une génération ou une régénération.|  
    |*Nomconfigsoln*|Nom de la configuration de solution qui sera utilisée pour générer la solution nommée dans SolutionName.|  
    |*SolutionName*|Chemin d'accès complet et nom du fichier de la solution.|  
    |**/ projet***NomProj* |Chemin d'accès et nom du fichier projet dans la solution. Vous pouvez entrer un chemin d'accès relatif du dossier SolutionName au fichier projet, le nom complet du projet ou le chemin d'accès complet et le nom du fichier projet.|  
    |**/projectconfig***ProjConfigName* |Nom d'une configuration de génération de projet à utiliser lors de la génération du projet.|  
  
     Lorsque vous déployez pour la première fois un assembly contenant une orchestration, il est possible que vous receviez un message d'avertissement signalant que l'orchestration n'est pas contenue dans le fichier de liaison. Cela est dû au fait que les orchestrations ne sont pas automatiquement liées à l'hôte lors du déploiement. Vous devez dans ce cas effectuer cette étape manuellement.  
  
## <a name="see-also"></a>Voir aussi  
 [Déploiement des assemblys BizTalk à partir de Visual Studio dans une application BizTalk](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md)