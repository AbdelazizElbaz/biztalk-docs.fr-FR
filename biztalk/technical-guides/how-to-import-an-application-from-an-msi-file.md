---
title: "Comment importer une Application à partir d’un fichier .msi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a5472df9-9f1e-42d5-82e0-cc559caf56b3
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fc79413b17343ff7dbf27c90af803e7b22fb0678
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="how-to-import-an-application-from-an-msi-file"></a>Comment importer une Application à partir d’un fichier .msi
Vous pouvez utiliser l’Assistant MSI d’importation dans la Console Administration de BizTalk Server ou de BTSTask pour importer une application BizTalk à partir d’un fichier .msi dans un groupe BizTalk dans l’environnement cible et installer l’application sur les instances d’hôte individuel dans le groupe. Le processus d’importation complète effectue les opérations suivantes :  
  
-   Un déploiement au niveau du groupe de l’application  
  
-   Une installation au niveau du serveur de l’application.  
  
 **Déploiement d’applications au niveau du groupe**  
  
 Vous effectuez un déploiement de groupe au niveau d’une application sur un serveur dans le groupe en exécutant l’Assistant Importation de MIS à partir de la console Administration de BizTalk Server ou en exécutant l’outil BTSTask. Le déploiement au niveau du groupe effectue les opérations suivantes :  
  
-   Crée l’application et ses artefacts dans le groupe  
  
-   Importent les liaisons qui se trouvent dans le package .msi  
  
-   Déploie tous les assemblys BizTalk Server avec leurs artefacts pour la base de données de gestion BizTalk pour le groupe  
  
-   Exécute des scripts pour s’exécuter au moment de l’importation.  
  
 Si vous avez ajouté des fichiers de liaison propres à l’environnement à l’application, vous devrez sélectionner les liaisons que vous souhaitez appliquer lors de l’importation.  
  
 **Installation de l’Application de niveau serveur**  
  
 Vous effectuez une installation au niveau du serveur d’une application sur chaque serveur dans un groupe en double-cliquant sur le fichier .msi lui-même ou en effectuant le processus d’installation à la fin de l’Assistant MSI d’importation. Au lieu d’être réalisée une fois par groupe, il est généralement réalisée sur chaque serveur BizTalk server qui est membre du groupe. L’installation au niveau du serveur effectue les opérations suivantes :  
  
-   Installe tous les assemblys BizTalk Server et les assemblys de dépendance dans le global assembly cache du serveur, afin que cet ordinateur dispose de tous les fichiers binaires dont il a besoin pour l’exécution  
  
-   Présente les services Web associés qui peuvent faire partie de la solution, par exemple, orchestrations publiées en tant que services Web.  
  
-   Applique les modifications spécifiques à l’ordinateur, telles que la création préalable des files d’attente MSMQ ou en créant des structures de dossiers de dépôt de fichiers et les autorisations, ce qui peuvent être effectuées à l’aide de scripts.  
  
 Lorsque vous exécutez un fichier .msi pour installer une application, le fichier .msi crée des entrées d’inscription dans la liste Ajouter ou supprimer des programmes et accélère le déploiement en automatisant le déploiement des artefacts et leurs dépendances dans le bon ordre.  
  
 Pour plus d’informations sur l’installation d’une application BizTalk, consultez [comment installer une Application](../technical-guides/how-to-install-an-application.md).  
  
 **Le déploiement de l’Application terminée et le processus d’Installation**  
  
 L’Assistant MSI d’importation déploie l’application sur le groupe. Il n’installe pas l’application sur des serveurs individuels dans le groupe. Si l’application inclut des artefacts basés sur un fichier, vous devez installer l’application sur chaque instance d’hôte qui exécutera les assemblys dans l’application (et tous les ordinateurs exécutant les applications qui dépendent de cette application). Vous pouvez faire sur le serveur vous avez exécuté l’Assistant MSI d’importation, toutefois, en sélectionnant le **exécuter l’Assistant Installation de Application pour installer l’application sur l’ordinateur local** case à cocher sur la page Importation réussie est affichée par le Assistant MSI d’importation. Vous pouvez le faire sur les autres serveurs dans le groupe en double-cliquant sur le fichier .msi sur chacun de ces serveurs.  
  
 Si vous êtes prêt à tester l’application, vous pouvez l’importer dans un groupe BizTalk dans un environnement de test. Si votre application est prête pour la production ou intermédiaire, vous pouvez l’importer dans un de ces environnements.  
  
## <a name="important-considerations"></a>Éléments importants à prendre en considération  
 Lorsque vous importez une application BizTalk à partir d’un fichier .msi, tenez compte les éléments suivants :  
  
-   **Vous devez spécifier que les artefacts doivent être remplacées dans un processus d’importation standard.** Si vous souhaitez remplacer les artefacts existants, sélectionnez l’option de remplacement des artefacts existants lors de l’importation du fichier .msi.  
  
-   **Les liaisons importées remplacent les liaisons existantes.** Lorsque vous importez un fichier .msi contenant des liaisons dans une application existante, les liaisons existantes sont remplacées par celles importées portant le même nom, et ce même si vous n'avez pas sélectionné l'option de remplacement des artefacts existants lors de l'importation du fichier .msi. Pour éviter que les liaisons de l'application exportée ne remplacent les liaisons de l'application dans laquelle vous importez le fichier .msi, ne sélectionnez pas le fichier de liaison en tant que ressource à exporter pendant l'opération d'exportation. Pour plus d’informations sur les ressources pour une exportation, consultez [comment exporter une Application BizTalk](http://go.microsoft.com/fwlink/?LinkID=154848) (http://go.microsoft.com/fwlink/?LinkID=154848).  
  
 À mesure que des liaisons sont appliquées au cours du processus d'importation, les liaisons déjà appliquées sont remplacées par de nouvelles liaisons qui portent le même nom. Autrement dit, la liaison d'un nom donné la plus récente est celle qui est effectivement appliquée. Lorsque vous importez une application, les liaisons sont appliquées dans l'ordre suivant :  
  
1.  Liaisons d'application générées par BizTalk Server, n'ayant pas été explicitement ajoutées à l'application au moyen d'un fichier de liaison, mais ayant été sélectionnées par l'utilisateur pour leur exportation dans le fichier .msi de l'application.  
  
2.  Fichiers de liaison ajoutés de manière explicite mais pour lesquels aucun environnement de déploiement cible n'a été défini. À l'intérieur de cet ensemble, l'application des liaisons ne respecte pas d'ordre particulier.  
  
3.  Liaisons ajoutées de manière explicite auxquelles est associé un environnement de déploiement cible correspondant à l'environnement de déploiement sélectionné pour l'importation de l'application. À l'intérieur de cet ensemble, l'application des liaisons ne respecte pas d'ordre particulier.  
  
-   **L’hôte spécifié doit exister.** Pour importer une application à partir d’un fichier .msi, un hôte correspondant à l’hôte spécifié dans les liaisons d’application contenues dans le fichier .msi doit déjà exister dans le groupe BizTalk ou l’opération d’importation échoue. En outre, le niveau de confiance de l'hôte doit correspondre.  
  
-   **Dépendances peuvent avoir des effets significatifs sur les opérations d’importation.** Lorsque vous importez une application qui a une dépendance sur une autre application, les règles suivantes s’appliquent :  
  
    -   Si une application que vous importez est dépendante d’un artefact dans une autre application, vous devez ajouter une référence à partir de la première application à l’autre application. L’application et l’artefact requis doivent déjà exister dans le groupe de destination. L’Assistant Importation vous permet de vous permet d’ajouter la référence. Toutefois, si vous utilisez la commande ImportApp de BTSTask, vous devez ajouter la référence à l’application après l’importation. Pour plus d’informations, consultez [comment ajouter une référence à une autre Application](http://go.microsoft.com/fwlink/?LinkId=155011) (http://go.microsoft.com/fwlink/?LinkId=155011). L'Assistant Importation établit des correspondances entre les références et les applications existantes du groupe et vous permet d'ajouter ou de modifier une référence. Même si BizTalk Server vérifie que l'application référencée existe, nous vous recommandons de vérifier également que l'application référencée contient l'artefact requis.  
  
    -   Lorsque vous installez une application, vous devez également installer les applications dont elle dépend. Lorsque vous installez une application dépendant d'un artefact, tel qu'un assembly BizTalk, contenu dans une autre application, vous devez installer au préalable l'application contenant cet artefact. Par exemple, si vous souhaitez installer l'application A, et que celle-ci dépend d'un assembly contenu dans l'application B, vous devez installer au préalable l'application B. Vous pouvez ensuite installer l’Application a Pour plus d’informations sur l’installation d’une application BizTalk, consultez [comment installer une Application](../technical-guides/how-to-install-an-application.md).  
  
    -   Pour importer une application dans un autre groupe BizTalk et l'exécuter dans celui-ci, vous devez également importer les artefacts dont cette application dépend. Faire cela en premier l’importation d’une application qui contient l’artefact référencé, ou en ajoutant l’artefact nécessaire à l’application qui le requiert. Pour plus d’informations sur l’importation d’une application BizTalk, consultez [comment importer une Application à partir d’un fichier .msi](../technical-guides/how-to-import-an-application-from-an-msi-file.md).  
  
 Pour plus des considérations et des informations sur l’importation d’une application BizTalk à partir d’un fichier .msi, consultez [comment importer une Application BizTalk](http://go.microsoft.com/fwlink/?LinkID=154827) (http://go.microsoft.com/fwlink/?LinkID=154827).  
  
## <a name="how-to-import-an-application"></a>Comment importer une Application  
 Pour obtenir des instructions sur l’importation d’une application BizTalk à partir d’un fichier .msi, consultez [comment importer une Application BizTalk](http://go.microsoft.com/fwlink/?LinkID=154827) (http://go.microsoft.com/fwlink/?LinkID=154827).