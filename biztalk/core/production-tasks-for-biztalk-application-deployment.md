---
title: "Tâches de production pour le déploiement d’applications BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deploying [applications], assemblies
- applications, deploying
- assemblies, warnings
- deploying [applications], warnings
- deploying [applications], tasks
- assemblies, deploying
- deploying [applications], production
ms.assetid: e77d8921-42ef-4c51-aab2-66c086aad955
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 260afd4522d28bdd2a485a1a11edc045c7fde880
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="production-tasks-for-biztalk-application-deployment"></a>Tâches de production impliquées dans le déploiement d'applications BizTalk
Cette rubrique présente les étapes impliquées dans le déploiement d'une application BizTalk dans votre environnement de production.  
  
> [!IMPORTANT]
>  Vous ne devez jamais déployer d'assemblys de Visual Studio sur un ordinateur de production. Pour activer le redéploiement, Visual Studio peut annuler le déploiement, supprimer la liaison, arrêter et désinscrire les assemblys existant dans les mêmes ou dans différentes applications. Bien que tout ceci soit nécessaire et approprié à l'environnement de développement, cela peut entraîner des conséquences inattendues et indésirables dans l'environnement de production. En outre, afin d'éviter qu'un développeur ne tente de déployer un assembly à partir de Visual Studio sur un ordinateur de production, nous vous recommandons de ne pas installer Visual Studio sur les ordinateurs de ce type.  
  
> [!IMPORTANT]
>  Soyez vigilant lorsque vous mettez à jour des applications dont d'autres applications dépendent dans un environnement de production, afin de ne pas perturber les applications actives. Pour plus d’informations, consultez [considérations importantes pour la mise à jour des Applications](../core/important-considerations-for-updating-applications.md).  
  
1.  **Copiez le fichier .msi dans votre environnement de production.** Comme décrit dans [tâches de test pour le déploiement d’applications BizTalk](../core/testing-tasks-for-biztalk-application-deployment.md), lorsque BizTalk application terminée intermédiaire et est prête pour la production, l’administrateur informatique responsable de la configuration de mise en lots fournit un fichier .msi à à utiliser pour le déploiement de production. Vous pouvez copier ce fichier .msi sur vos ordinateurs de production, puis, comme indiqué à l'étape suivante, importer l'application BizTalk du fichier .msi vers BizTalk Server. Vous utilisez également le fichier .msi pour installer l'application sur les ordinateurs qui l'exécuteront. Une solution BizTalk complète peut être constituée d’une ou plusieurs applications, par conséquent vous pouvez recevoir plusieurs fichiers .msi à déployer.  
  
2.  **Importez l’application à partir du fichier .msi.** Vous pouvez utiliser l'Assistant Importation de fichier MSI, disponible à partir de la console Administration de BizTalk Server, pour importer le contenu du fichier .msi dans une application de l’instance actuelle de BizTalk Server. Pour plus d’informations, consultez [comment importer une Application BizTalk](../core/how-to-import-a-biztalk-application.md). Si l'application spécifiée n'existe pas encore, l'importation du fichier .msi la crée automatiquement. Vous pouvez ensuite afficher l'application et modifier sa configuration et son contenu à partir de la console d'administration. Cela peut s'avérer nécessaire, par exemple, pour configurer des certificats et des points de terminaison, tels que des URL, ainsi que pour modifier les liaisons de votre environnement de production. Pour plus d’informations, consultez [création et modification des Applications BizTalk](../core/creating-and-modifying-biztalk-applications.md). Si un fichier de liaison a été ajouté à l'application possédant les liaisons appropriées pour l'environnement de production, vous pouvez appliquer ces liaisons au cours du processus d'importation. Pour plus d’informations, consultez [déploiement d’applications et des fichiers de liaison](../core/binding-files-and-application-deployment.md).  
  
3.  **Installez et démarrez l’application.** Vous pouvez à présent installer l'application sur tous les ordinateurs qui l'exécuteront et la démarrer dans la console d'administration. Vous pouvez installer l’application en double-cliquant sur le fichier .msi. Pour plus d’informations, consultez [comment installer une Application BizTalk](../core/how-to-install-a-biztalk-application.md).  
  
4.  **Exporter des fichiers de liaison et les ajouter dans l’application (facultative).** Pour faciliter la réimportation ultérieure de l'application dans votre environnement de production afin de déployer des changements ou des ajouts, vous pouvez exporter les liaisons de l'application, puis les ajouter à nouveau dans l'application, en spécifiant un environnement cible de production pour celles-ci. Lorsque par la suite vous réimportez le fichier .msi de l'application dans votre environnement de production BizTalk Server, vous pouvez spécifier que ces liaisons soient appliquées. Pour plus d’informations, consultez [déploiement d’applications et des fichiers de liaison](../core/binding-files-and-application-deployment.md).  
  
5.  **Exporter l’application dans un nouveau fichier .msi (facultatif).** Si vous apportées les modifications de configuration ou des ajouts à l’application et que vous souhaitez que les modifications soient prises en compte dans le fichier .msi (par exemple, pour déployer l’application à d’autres groupes BizTalk), vous pouvez exporter un nouveau fichier .msi, comme décrit dans [comment exporter un L’Application BizTalk](../core/how-to-export-a-biztalk-application.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches de déploiement d’application](../core/application-deployment-tasks.md)