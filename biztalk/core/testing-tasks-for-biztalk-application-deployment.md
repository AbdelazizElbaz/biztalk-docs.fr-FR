---
title: "Tâches de test pour le déploiement d’applications BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deploying [applications], testing
- testing, deploying
- testing, tasks
ms.assetid: fb043755-6d01-4ceb-b189-5a5f286c2b37
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bfd4385c4de076c8c89b409177204ee8fce5548b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="testing-tasks-for-biztalk-application-deployment"></a>Tâches de test impliquées dans le déploiement d'applications BizTalk
Cette rubrique présente les étapes impliquées dans le déploiement des artefacts d’une application BizTalk dans un environnement de test et de débogage.  
  
1.  **Copiez le fichier .msi à votre environnement de test.** Comme décrit dans [tâches de développement pour le déploiement d’applications BizTalk](../core/development-tasks-for-biztalk-application-deployment.md), lorsqu’une application BizTalk est prête à tester, le développeur exporte les artefacts de l’application dans un fichier .msi. Une solution complète peut être constituée d’une ou plusieurs applications BizTalk, par conséquent vous pouvez recevoir plusieurs fichiers .msi à tester. Vous pouvez copier le fichier .msi dans votre ordinateur de test, puis, comme il est décrit dans l'étape suivante, importer les artefacts depuis les fichiers .msi vers BizTalk Server. Vous utilisez également les fichiers .msi pour installer les applications sur les ordinateurs qui les exécuteront.  
  
2.  **Importez l’application à partir du fichier .msi.** Vous pouvez utiliser l'Assistant Importation de fichier MSI, disponible à partir de la console Administration de BizTalk Server, pour importer les artefacts du fichier .msi dans une application de l’instance actuelle de BizTalk Server. Pour plus d’informations, consultez [comment importer une Application BizTalk](../core/how-to-import-a-biztalk-application.md). Si l'application spécifiée n'existe pas encore, le processus d’importation la crée automatiquement. Vous pouvez ensuite afficher l'application et modifier sa configuration et son contenu à partir de la console Administration de BizTalk Server. Cela peut s'avérer nécessaire, par exemple, pour modifier les liaisons de votre environnement de test. Pour plus d’informations, consultez [création et modification des Applications BizTalk](../core/creating-and-modifying-biztalk-applications.md). Si un fichier de liaison a été ajouté à l'application possédant les liaisons appropriées pour l'environnement de test, vous pouvez appliquer ces liaisons au cours du processus d'importation. Pour plus d’informations, consultez [déploiement d’applications et des fichiers de liaison](../core/binding-files-and-application-deployment.md).  
  
3.  **Installer l’application.** Vous pouvez à présent installer l'application sur tous les serveurs sur lesquels vous voulez l'exécuter. Si l'application contient des artefacts basés sur un fichier, vous devez également l'installer pour qu'elle puisse fonctionner. Vous pouvez installer l’application en double-cliquant sur le fichier .msi. L’Assistant installe et enregistre les artefacts de l’application sur l’ordinateur local, de sorte que l’application peut être exécutée. Pour plus d’informations, consultez [comment installer une Application BizTalk](../core/how-to-install-a-biztalk-application.md).  
  
4.  **Tester l’application.** Vous pouvez à présent tester l’application. Une fois que le développeur aura résolu les problèmes rencontrés et vous aura fourni un fichier .msi mis à jour, vous pouvez reprendre les étapes 1 à 3.  
  
5.  **Exporter des fichiers de liaison et les ajouter dans l’application (facultative).** Pour faciliter la réimportation ultérieure de l'application dans votre environnement de test afin de pouvoir procéder au test des modifications ou ajouts, vous pouvez exporter les liaisons d’application, puis les ajouter à nouveau dans l’application, en spécifiant un environnement cible de test pour celles-ci. Lorsque par la suite vous réimportez le fichier .msi de l'application dans votre environnement de test BizTalk Server, vous pouvez spécifier que ces liaisons soient appliquées. Pour plus d’informations, consultez [déploiement d’applications et des fichiers de liaison](../core/binding-files-and-application-deployment.md).  
  
6.  **Générez un fichier .msi pour déployer l’application dans l’environnement intermédiaire**. Lorsque vous avez terminé de tester l'application BizTalk, vous pouvez la déployer dans l'environnement intermédiaire. Pour ce faire, utilisez l’Assistant Exportation pour générer un nouveau fichier .msi, comme décrit précédemment à l’étape 2. Vous pouvez ensuite remettre le fichier .msi à l’administrateur informatique responsable du déploiement intermédiaire. L’administrateur informatique utilise le fichier .msi pour importer l’application dans BizTalk Server sur des ordinateurs intermédiaires et installer l’application sur les ordinateurs qui exécuteront, comme décrit dans [de mise en lots de tâches pour le déploiement d’Application BizTalk](../core/staging-tasks-for-biztalk-application-deployment.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches de déploiement d’application](../core/application-deployment-tasks.md)