---
title: "Tâches de mise en lots pour le déploiement d’applications BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- applications, staging
- deploying [applications], staging
- applications, deploying
- deploying [applications], tasks
ms.assetid: de60eddb-da13-412a-94f9-331387b5930e
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9f03d0cfd5db587a84a080d5963d6696e123ef2b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="staging-tasks-for-biztalk-application-deployment"></a>Tâches de construction impliquées dans le déploiement d'applications BizTalk
Cette rubrique présente les étapes impliquées dans le déploiement d'une application BizTalk dans un environnement intermédiaire.  
  
1.  **Copiez le fichier .msi dans votre environnement intermédiaire.** Comme décrit dans [tâches de test pour le déploiement d’applications BizTalk](../core/testing-tasks-for-biztalk-application-deployment.md), lorsque BizTalk application a terminé les tests et est prête pour la construction, l’équipe des tests fournit un ou des fichiers .msi plus pour l’environnement intermédiaire. Une solution complète peut être constituée d'une ou plusieurs applications BizTalk. Par conséquent, vous pouvez recevoir plusieurs fichiers .msi à tester.  Vous pouvez copier ce fichier .msi sur vos ordinateurs intermédiaires, puis, comme indiqué à l'étape suivante, importer l'application BizTalk du fichier .msi vers un groupe BizTalk de l'environnement intermédiaire. Vous utilisez également le fichier .msi pour installer l'application sur les ordinateurs qui l'exécuteront.  
  
2.  **Importez l’application à partir du fichier .msi.** Vous pouvez utiliser l'Assistant Importation de fichier MSI, disponible à partir de la console Administration de BizTalk Server, pour importer le contenu du fichier .msi dans une application d'un groupe BizTalk de l'environnement intermédiaire. Pour plus d’informations, consultez [comment importer une Application BizTalk](../core/how-to-import-a-biztalk-application.md). Si l'application spécifiée n'existe pas encore, l'importation du fichier .msi la crée automatiquement. Vous pouvez ensuite afficher l'application et modifier sa configuration et son contenu à partir de la console Administration de BizTalk Server. Cela peut s'avérer nécessaire, par exemple, pour modifier les liaisons de votre environnement intermédiaire. Pour plus d’informations, consultez [création et modification des Applications BizTalk](../core/creating-and-modifying-biztalk-applications.md). Si un fichier de liaison a été ajouté à l'application possédant les liaisons appropriées pour l'environnement intermédiaire, vous pouvez appliquer ces liaisons au cours du processus d'importation. Pour plus d’informations, consultez [déploiement d’applications et des fichiers de liaison](../core/binding-files-and-application-deployment.md).  
  
3.  **Exporter des fichiers de liaison et les ajouter dans l’application (facultative).** Pour faciliter la réimportation ultérieure de l'application dans votre environnement intermédiaire si des modifications ou des ajouts lui ont été apportés, vous pouvez exporter les liaisons de l'application, puis les ajouter à nouveau, en spécifiant un environnement intermédiaire cible pour celles-ci. Lorsque par la suite vous réimportez le fichier .msi de l'application dans votre environnement intermédiaire BizTalk Server, vous pouvez spécifier que ces liaisons soient appliquées. Pour plus d’informations, consultez [déploiement d’applications et des fichiers de liaison](../core/binding-files-and-application-deployment.md).  
  
4.  **Installer l’application.** Vous pouvez à présent installer l'application sur tous les ordinateurs qui doivent l'exécuter. Vous pouvez procéder à l'aide de l'Assistant Installation ou simplement double-cliquer sur le fichier .msi. Pour plus d’informations, consultez [comment installer une Application BizTalk](../core/how-to-install-a-biztalk-application.md).  
  
5.  **Tester l’application pour vérifier la configuration et les liaisons.** Vous pouvez à présent tester l'application afin de vérifier qu'elle fonctionne comme prévu dans l'environnement intermédiaire. Une fois que vous, ou le développeur, aurez apporté les changements requis, vous pouvez reprendre les étapes 1 à 4.  
  
6.  **Générer un fichier .msi pour déployer l’application dans l’environnement de production**. Lorsque vous avez terminé de configurer l'application BizTalk pour l'environnement de production et vérifié sa configuration, vous pouvez la déployer dans l'environnement de production. Pour ce faire, vous utilisez l’Assistant Exportation pour générer un nouveau fichier .msi, comme décrit dans [comment exporter une Application BizTalk](../core/how-to-export-a-biztalk-application.md). Vous pouvez ensuite remettre le fichier .msi à l'administrateur chargé du déploiement en production. L’administrateur informatique utilise le fichier .msi pour importer l’application dans BizTalk Server sur les ordinateurs de production, ainsi que pour l’installer sur les ordinateurs qui exécuteront, comme décrit dans [des tâches de Production pour le déploiement d’Application BizTalk](../core/production-tasks-for-biztalk-application-deployment.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches de déploiement d’application](../core/application-deployment-tasks.md)