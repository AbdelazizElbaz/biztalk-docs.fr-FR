---
title: "Tâches de développement pour le déploiement d’applications BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- developing, deploying
- deploying [applications], developing
- applications, tasks
- deploying [applications], warnings
- applications, developing
- developing, tasks
ms.assetid: b441d4f4-122e-4caf-8381-723c6142b0b6
caps.latest.revision: "28"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 237a3f95fa33b8265be9d7af2a55ed14e2bbe408
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="development-tasks-for-biztalk-application-deployment"></a>Tâches de développement impliquées dans le déploiement d'applications BizTalk
Cette rubrique présente les étapes impliquées dans le déploiement d'assemblys BizTalk à partir de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] dans une application BizTalk, dans la finalisation de l'application et dans sa préparation pour le déploiement en environnement de test. Ce scénario de déploiement est courant dans un environnement de développement, dans lequel un programmeur développe et débogue une solution d'entreprise BizTalk spécifique.  
  
> [!IMPORTANT]
>  Vous ne devez jamais exécuter les tâches décrites dans cette rubrique sur un ordinateur de production. En phase de développement, les développeurs redéploient souvent les assemblys à partir de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]. Pour activer le redéploiement, [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] peut annuler le déploiement, supprimer la liaison, arrêter et désinscrire les assemblys existant dans les mêmes ou dans différentes applications. Bien que tout ceci soit nécessaire et approprié à l'environnement de développement, cela peut entraîner des conséquences inattendues et indésirables dans l'environnement de production. En outre, afin d'éviter qu'un développeur ne tente de déployer un assembly à partir de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] sur un ordinateur de production, il est déconseillé d'installer [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] sur les ordinateurs de production.  
  
1.  **Développer et créer les assemblys BizTalk.** Vous commencez par créer votre solution d’entreprise BizTalk dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], à l’aide des orchestrations, schémas, mappages et pipelines. En travaillant sur la solution, vous la créez dans un ou plusieurs assemblys BizTalk. Pour plus d’informations, consultez [développement d’Applications BizTalk Server](../core/developing-biztalk-server-applications.md). Vous développez et construisez également des assemblys .NET non-BizTalk qui sont nécessaires pour que votre solution fonctionne.  
  
2.  **Définir les propriétés de déploiement.** Lorsque vous êtes prêt à déployer vos assemblys BizTalk, vous définissez les propriétés de déploiement sur chaque [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] projet dans la solution. Outre les propriétés de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] (Serveur, Configuration, Base de données, Redéployer, Redémarrer les instances d'hôte et Installer dans le Global Assembly Cache), vous pouvez également définir la propriété Nom de l'application. Cette propriété spécifie l'application BizTalk dans laquelle vous déployez chaque assembly. Si la propriété Nom de l'application est vide, l'assembly est déployé dans l'application par défaut. Pour plus d’informations, consultez [comment définir les propriétés de déploiement dans Visual Studio](../core/how-to-set-deployment-properties-in-visual-studio.md). Vous devez déployer vos assemblys .NET non-BizTalk en les ajoutant à l'application BizTalk. Cette procédure est décrite ultérieurement à l'étape 4.  
  
3.  **Déployer les assemblys BizTalk à BizTalk Server est en cours d’exécution sur l’ordinateur local.** Vous pouvez déployer les assemblys BizTalk à partir d’une option de menu, en cliquant sur un [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] solutions et en sélectionnant la commande déployer. Cette opération construit les assemblys BizTalk dans les projets contenus dans la solution et les ajoute à l'application BizTalk définie dans les propriétés de déploiement de chaque projet. Si l'application n'existe pas déjà, elle est créée. Les assemblys et leurs ressources, appelées « artefacts », sont également déployés dans la base de données de gestion BizTalk associée au groupe, et vous pouvez les afficher et les gérer à l'aide de la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou d'autres outils. Pour plus d’informations sur cette étape, consultez [comment déployer un BizTalk Assembly à partir de Visual Studio](../core/how-to-deploy-a-biztalk-assembly-from-visual-studio.md).  
  
4.  **Ajouter des artefacts qui sont requis pour l’application de fonctionner correctement.** Depuis la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration, vous pouvez facilement modifier une application de compléter, par exemple en ajoutant et supprimant des artefacts, tels que l’envoi et ports de réception, scripts, stratégies, les assemblys .NET non - BizTalk et ainsi de suite. Pour plus d’informations, consultez [création et modification des Applications BizTalk](../core/creating-and-modifying-biztalk-applications.md).  
  
5.  **Factoriser les artefacts dans plusieurs applications.** Pendant le processus de déploiement, vous pouvez avoir déployé vos assemblys dans une seule application à des fins pratiques. Pour diverses raisons, vous pouvez être amené à factoriser les artefacts dans plusieurs applications avant de les déployer en production. Pour plus d’informations sur les meilleures pratiques pour la factorisation des applications, consultez [meilleures pratiques pour déployer une Application BizTalk](../core/best-practices-for-deploying-a-biztalk-application.md).  
  
6.  **Créer des fichiers .msi pour toutes les applications dans la solution et les installer localement.** Vous pouvez utiliser l’Assistant Exportation, accessible à partir de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration ou de l’outil de ligne de commande BTSTask pour créer un fichier .msi contenant les artefacts de chaque application. Pour plus d’informations, consultez [exportation des Applications BizTalk, les liaisons et les stratégies](../core/exporting-biztalk-applications-bindings-and-policies.md). Vous pouvez également installer les artefacts à partir des fichiers .msi si vous souhaitez exécuter la solution sur l'ordinateur local et vérifier qu'il fonctionne comme prévu. Pour plus d’informations, consultez [comment installer une Application BizTalk](../core/how-to-install-a-biztalk-application.md). Vérifiez que la solution fonctionne comme prévu.  
  
7.  **Redéployer les assemblys BizTalk en fonction des besoins.** En cours de développement et le débogage de vos assemblys BizTalk, vous devrez peut-être les redéployer plusieurs fois. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]fournit un mécanisme simple de redéploiement. Pour plus d’informations, consultez [comment redéployer un BizTalk Assembly à partir de Visual Studio](../core/how-to-redeploy-a-biztalk-assembly-from-visual-studio.md).  
  
8.  **Exporter des fichiers de liaison et les ajouter dans les applications (facultatives).** Pour faciliter la réimportation ultérieure des applications dans votre environnement de développement afin de pouvoir procéder à des modifications ou ajouts, vous pouvez exporter les liaisons de chaque application, puis les ajouter à nouveau, en spécifiant un environnement cible de développement pour celles-ci. Lorsque par la suite vous réimportez les fichiers .msi de l'application dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sur votre ordinateur de développement, vous pouvez spécifier que ces liaisons soient appliquées. Pour plus d’informations, consultez [déploiement d’applications et des fichiers de liaison](../core/binding-files-and-application-deployment.md).  
  
9. **Générer un fichier .msi pour chaque application de transférer hors tension à votre équipe de test**. Une fois que vous avez terminé de développer et déboguer votre solution BizTalk, vous pouvez utiliser l’Assistant Exportation ou BTSTask pour générer les fichiers .msi d’application, comme décrit précédemment à l’étape 6. Vous devez importer ces fichiers dans un autre groupe BizTalk dans votre environnement de développement, installez-les, puis vérifiez que la solution fonctionne comme prévu. Vous pouvez ensuite remettre à votre équipe de test les fichiers .msi, ce qui peut les utiliser pour importer les applications dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] en cours d’exécution sur les ordinateurs de test, et les installer, comme décrit dans [des tâches de test pour le déploiement d’Application BizTalk](../core/testing-tasks-for-biztalk-application-deployment.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches de déploiement d’application](../core/application-deployment-tasks.md)