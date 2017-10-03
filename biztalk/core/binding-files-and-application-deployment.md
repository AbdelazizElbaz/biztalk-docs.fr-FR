---
title: "Fichiers de liaison et déploiement d’Application | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- bindings
- deploying [applications], binding files
- assemblies, binding files
- bindings, applying
- groups, assemblies
- applications, binding files
- binding files, applications
- bindings, hosts
- deploying, assemblies
- updating, assemblies
- assemblies, updating
- hosts, bindings
- binding files, assemblies
- applications, moving
- assemblies, deploying
- binding files, about binding files
- bindings, about bindings
- groups, deploying
- binding files, deploying
- bindings, binding files
ms.assetid: 396ad021-8001-4ed8-8b28-85b72f981fae
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dc6908f962cd3bb8f9fdec3fcaab6bc131c889da
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="binding-files-and-application-deployment"></a>Fichiers de liaison et déploiement d'applications
Cette rubrique explique comment utiliser les fichiers de liaison pour faciliter le déploiement d'applications et d'assemblys BizTalk. Les fichiers de liaison peuvent accélérer le processus de déploiement dans les cas suivants en évitant le recours à la configuration manuelle :  
  
-   Déplacement d'une application d'un environnement de déploiement à un autre  
  
-   Mise à jour d'un assembly  
  
-   Déploiement d’un assembly dans plusieurs groupes BizTalk.  
  
## <a name="what-is-a-binding"></a>Qu'est-ce qu'une liaison ?  
 Une liaison crée un mappage entre un point de terminaison logique, tel qu'un port d'orchestration ou un lien de rôle, et un point de terminaison physique, tel qu'un tiers ou un port de réception/envoi. Elle permet aux différents composants d'une solution d'entreprise BizTalk de communiquer. Vous pouvez créer des liaisons dans la console Administration de BizTalk Server.  
  
## <a name="what-is-a-binding-file"></a>Qu'est-ce qu'un fichier de liaison ?  
 Un fichier de liaison est un fichier .xml contenant les informations de liaison pour chaque orchestration, pipeline, mappage ou schéma BizTalk dans l'étendue d'un assembly, d'une application ou d'un groupe BizTalk. Il décrit l'hôte auquel est liée chaque orchestration, son niveau de confiance, ainsi que les paramètres des différents ports d'envoi, groupes de ports d'envoi, port de réception, emplacement de réception et tiers configurés. Vous pouvez générer des fichiers de liaison et appliquer les liaisons qu'ils contiennent à un assembly, une application ou un groupe afin d'éviter d'avoir à configurer manuellement les liaisons dans différents environnements de déploiement.  
  
## <a name="why-use-binding-files"></a>Pourquoi utiliser des fichiers de liaison ?  
 Vous pouvez utiliser des fichiers de liaison dans les situations suivantes.  
  
### <a name="moving-from-one-environment-to-another"></a>Déplacement d'une application d'un environnement à un autre  
 Les fichiers de liaison peuvent faciliter le déplacement d'une application d'un environnement de déploiement à un autre, par exemple d'un environnement de développement à un environnement de test. Les liaisons nécessitent souvent d'être reconfigurées pour les différents environnements de déploiement, or les fichiers de liaison permettent d'éviter cette reconfiguration manuelle répétitive.  
  
 Pour ce faire, vous pouvez créer une bibliothèque de liaisons dans laquelle faire votre choix lorsqu'il vous faut déployer l'application dans un nouvel environnement. Vous pouvez ainsi créer un fichier de liaison pour votre environnement de test et un autre pour celui de production, puis les ajouter tous les deux à l'application. Lorsque vous importez l'application dans l'environnement de test, vous pouvez sélectionner une option pour appliquer les liaisons de test. De même, lorsque vous importez l'application dans l'environnement de production, il vous suffit de sélectionner une option pour appliquer les liaisons de production. Cette procédure vous évite d'avoir à reconfigurer les liaisons manuellement pour chaque environnement. Une autre méthode consiste à importer les liaisons créées pour l'environnement actuel après y avoir importé l'application. Les liaisons sont alors automatiquement appliquées.  
  
### <a name="updating-an-assembly"></a>Mise à jour d’un assembly  
 Lorsque vous mettez à jour un assembly dans une application, ses liaisons sont généralement remplacées, faute de quoi l'assembly risque de ne pas être lié, vous obligeant à une reconfiguration manuelle des liaisons. Pour remédier à ce problème, utilisez un fichier de liaison comme suit :  
  
-   **Mise à jour de la même version d’un assembly.** si l'assembly possède des ports dynamiques ou des ports à liaison anticipée et que vous ayez modifié leur configuration dans la console Administration de BizTalk Server, vous perdez ces paramètres lors de la mise à jour de l'assembly avec un assembly de même version. Exportez un fichier de liaison pour l'assembly à mettre à jour. Après la mise à jour de l'assembly, vous pouvez l'importer dans l'application, puis importer son fichier de liaison afin de réappliquer les liaisons précédentes.  
  
-   **Mise à jour d’un assembly avec une version plus récente.** vous pouvez exporter un fichier de liaison pour l'assembly à mettre à jour, puis le modifier afin de prendre en compte la nouvelle version. Après l'importation de la nouvelle version de l'assembly dans l'application, vous pouvez importer le fichier de liaison dans l'application afin d'appliquer les liaisons. Pour obtenir des instructions sur la modification d’un fichier de liaison, consultez [personnalisation des fichiers de liaison](../core/customizing-binding-files.md).  
  
### <a name="deploying-an-assembly-to-multiple-biztalk-groups"></a>Déploiement d'un assembly dans plusieurs groupes BizTalk  
 Lorsque vous déployez un assembly dans plusieurs groupes BizTalk, vous pouvez transporter ses liaisons en même temps que lui. Cette procédure vous évite d'avoir à configurer séparément les liaisons de l'assembly dans chaque groupe. Vous pouvez le faire comme suit :  
  
1.  Créez un fichier de liaison pour l'assembly à déployer en exportant les liaisons de l'assembly.  
  
2.  Ajoutez l'assembly et son fichier de liaison à une application. Si le déploiement de l'assembly s'effectue sans autres artefacts, l'application ne peut contenir que l'assembly et le fichier de liaison.  
  
3.  Exportez un fichier .msi pour l'application, en vous assurant de sélectionner également le fichier de liaison à exporter.  
  
4.  Importez le fichier .msi de l'application dans les groupes et applications BizTalk dans lesquels le déployer. Les liaisons du fichier sont automatiquement appliquées à l'assembly au moment de l'importation.  
  
## <a name="how-can-i-generate-and-use-binding-files"></a>Comment générer et utiliser des fichiers de liaison ?  
 Un fichier de liaison n’est pas généré automatiquement pour un assembly, une application ou un groupe BizTalk, mais vous pouvez générer un fichier de liaison en exportant des liaisons, comme décrit dans [exportation des liaisons](../core/exporting-bindings6.md). Vous pouvez ensuite importer le fichier de liaison dans une application ou un groupe, comme décrit dans [comment importer les liaisons dans une Application BizTalk](../core/how-to-import-bindings-into-a-biztalk-application.md) et [comment importer les liaisons dans un groupe BizTalk](../core/how-to-import-bindings-into-a-biztalk-group.md), qui automatiquement s’applique ses liaisons.  
  
 Vous pouvez également ajouter le fichier de liaison à une application afin que ses liaisons sont appliquées lorsque l’application est importée dans un autre groupe, plutôt que d’immédiatement, comme décrit dans [l’ajout d’un fichier de liaison à une Application](../core/how-to-add-a-binding-file-to-an-application2.md). Cette dernière méthode permet d'ajouter plusieurs fichiers de liaison à une application et, éventuellement, d'indiquer un environnement de déploiement cible pour chacun d'eux. Lorsque vous importez l’application, vous pouvez ensuite sélectionner les liaisons à appliquer, en fonction de l’environnement de déploiement cible, comme décrit dans [comment importer une Application BizTalk](../core/how-to-import-a-biztalk-application.md). La dernière méthode permet également d'importer des fichiers de liaison distincts pour les différents assemblys de votre application.  
  
 Vous pouvez modifier les fichiers de liaison après leur génération s'il vous faut modifier leurs informations de liaison. Pour plus d’informations, consultez [personnalisation des fichiers de liaison](../core/customizing-binding-files.md).  
  
## <a name="how-are-bindings-applied"></a>Comment les liaisons sont-elles appliquées ?  
 Les liaisons sont appliquées dès qu'un fichier de liaison est importé dans une application, ou dès qu'une application est importée dans un nouveau groupe BizTalk. Lorsque vous utilisez des fichiers de liaison, vous devez comprendre comment fonctionnent les liaisons entre les artefacts et les hôtes, ainsi que l'ordre dans lequel elles sont appliquées.  
  
### <a name="binding-to-hosts"></a>Liaison avec les hôtes  
 Lorsque les liaisons sont exportées, seules ou dans le cadre d'une application, les hôtes et niveaux de confiance sont enregistrés dans le fichier de liaison comme suit :  
  
-   **Port d’envoi.** niveau de confiance de l'hôte associé au gestionnaire d'envoi.  
  
-   **Emplacement de réception.** niveau de confiance de l'hôte associé au gestionnaire de réception.  
  
-   **Orchestration.** niveau de confiance de l'hôte.  
  
 Lorsque les liaisons sont importées dans une application, ou qu'une application est importée depuis le fichier .msi dans un nouveau groupe BizTalk, les hôtes et niveaux de confiance des fichiers de liaison sont mis en correspondance avec les hôtes et niveaux de confiance de l'application, comme suit :  
  
-   **Port d’envoi.** le port d'envoi est lié à un gestionnaire d'envoi du même nom et à un hôte doté d'un niveau de confiance identique à celui enregistré dans le fichier de liaison.  
  
-   **Emplacement de réception.** l'emplacement de réception est lié à un gestionnaire de réception du même nom et à un hôte doté d'un niveau de confiance identique à celui enregistré dans le fichier de liaison.  
  
-   **Orchestrations.** l'orchestration est liée à un hôte doté du même nom et d'un niveau de confiance identique à celui enregistré dans le fichier de liaison.  
  
### <a name="order-in-which-bindings-are-applied"></a>Ordre d'application des liaisons  
 Lorsque vous importez une application, les liaisons sont appliquées dans l'ordre suivant :  
  
1.  Liaisons d'application générées par BizTalk Server, n'ayant pas été explicitement ajoutées à l'application au moyen d'un fichier de liaison, mais ayant été sélectionnées par l'utilisateur pour leur exportation dans le fichier .msi de l'application.  
  
2.  Liaisons des fichiers de liaison ajoutés à l'application et pour lesquels aucun environnement de déploiement cible n'a été défini. L'application de ces liaisons ne respecte pas d'ordre particulier.  
  
3.  Liaisons des fichiers de liaisons ajoutés à l'application et associés à un environnement de déploiement cible correspondant à l'environnement de déploiement sélectionné pour l'importation de l'application. L'application de ces liaisons ne respecte pas d'ordre particulier.  
  
 À mesure que des liaisons sont appliquées au cours du processus d'importation, les liaisons déjà appliquées sont remplacées par de nouvelles liaisons qui portent le même nom. Autrement dit, la liaison d'un nom donné la plus récente est celle qui est effectivement appliquée.  
  
 Par exemple, si une application existante inclut un port d’envoi nommé SendPort1 et un fichier de liaison est appliqué qui décrit un port d’envoi avec le même nom, les paramètres dans le fichier de liaison remplace les paramètres existants de SendPort1. Si une application existante inclut une orchestration nommée ErrorHandling.ErrorHandler.ResubmitLogic, par exemple, et un fichier de liaison décrit une orchestration portant le même nom, toutes les liaisons existantes de l’orchestration seront enregistrés avec le liaisons du fichier de liaison.  
  
## <a name="see-also"></a>Voir aussi  
 [Présentation de gestion et déploiement d’applications BizTalk](../core/understanding-biztalk-application-deployment-and-management.md)