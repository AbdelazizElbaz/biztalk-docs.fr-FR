---
title: "Liste de vérification : Mise à jour les artefacts dans une Application BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deploying, redeploying
- updating, applications
- redeploying
- checklists, applications
- updating, checklists
- updating
- applications, updating
- applications, redeploying
- applications, checklists
- checklists, redeploying
ms.assetid: 07ea4a2b-4ada-4d04-9eec-604b63b77415
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 321ef2c6c9bbd522c54f5d9352995788d8843455
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="checklist-update-the-artifacts-in-a-biztalk-application"></a>Liste de vérification : Mise à jour les artefacts dans une Application BizTalk
Suivez les étapes de cette liste de vérification pour modifier ou mettre à jour un ou plusieurs artefacts d'une application qui a déjà été déployée, puis redéployer cette application.  
  
|Étape|Référence|  
|----------|---------------|  
|Passez en revue les considérations importantes à prendre en compte lors de la mise à jour d'artefacts dans une application.|[Considérations importantes pour la mise à jour des Applications](../core/important-considerations-for-updating-applications.md)|  
|Vérifiez que vous disposez des autorisations adéquates pour effectuer le déploiement.|[Autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)|  
|Utilisez Visual Studio pour procéder aux modifications nécessaires de vos assemblys. Si vous mettez à jour un assembly qui s'exécute dans un environnement de production, vous devez toujours augmenter le numéro de version de l'assembly d'un incrément. Pour plus d’informations, consultez [mise à jour des Applications BizTalk](../core/updating-biztalk-applications.md). Déployez ensuite les assemblys à partir de Visual Studio dans l'environnement de production d'une application BizTalk.|[Comment déployer un Assembly BizTalk à partir de Visual Studio](../core/how-to-deploy-a-biztalk-assembly-from-visual-studio.md)|  
|Testez tous les artefacts nouveaux ou modifiés, en veillant à tester également tous les artefacts dépendants. Pour le test, n'oubliez pas de prendre en compte les dépendances qui peuvent exister entre cette application et d'autres applications.|[Tâches de test pour le déploiement d’applications BizTalk](../core/testing-tasks-for-biztalk-application-deployment.md)|  
|Procédez à l'ajout, la suppression ou la reconfiguration des artefacts dans l'application si nécessaire.|[Comment créer ou ajouter un artefact](../core/how-to-create-or-add-an-artifact.md), [comment supprimer un artefact d’une Application](../core/how-to-remove-an-artifact-from-an-application.md), [la gestion des artefacts](../core/managing-artifacts.md)|  
|Cette commande permet d'exporter l'application contenant les artefacts nouveaux ou modifiés dans un fichier .msi. Vous pouvez exporter soit l'ensemble des artefacts de l'application, soit uniquement les artefacts que vous voulez ajouter ou mettre à jour. Notez que les artefacts de fichiers peuvent être remplacés. Si vous exportez un artefact de fichier, assurez-vous qu'il s'agit de la version que vous voulez utiliser dans l'application.|[Exportation de stratégies, les liaisons et les Applications BizTalk](../core/exporting-biztalk-applications-bindings-and-policies.md)|  
|Si vous pensez que la mise à jour interfèrera avec l'exécution de l'application, arrêtez l'application que vous voulez mettre à jour. Si vous mettez à jour un assembly avec une version plus récente, il n'est pas nécessaire de redémarrer l'application. **Remarque :** bien qu’il n’est pas nécessaire d’arrêter une application afin de mettre à jour un artefact ou installer l’application, nous vous recommandons de toujours arrêter une application lorsque vous mettez à jour un artefact.|[Comment démarrer et arrêter une Application BizTalk](../core/how-to-start-and-stop-a-biztalk-application.md)|  
|Importez les artefacts modifiés ou mis à jour depuis le fichier .msi vers l'application que vous voulez mettre à jour. Vérifiez que vous avez choisi l'option de remplacement des artefacts existants.|[Comment importer une Application BizTalk](../core/how-to-import-a-biztalk-application.md)|  
|Installez l'application ou les artefacts mis à jour depuis le fichier .msi sur tous les ordinateurs qui exécutent l'application, ainsi que sur tout les ordinateurs qui exécutent des applications dépendant de cette application. Si vous mettez à jour un assembly BizTalk, vérifiez que la nouvelle version de l'assembly est installée dans le Global Assembly Cache (GAC) de chaque ordinateur sur lequel l'assembly sera exécuté. Si ce n'est pas le cas, installez l'assembly dans chaque GAC.|[Comment installer une Application BizTalk](../core/how-to-install-a-biztalk-application.md), [comment installer un Assembly dans le GAC](../core/how-to-install-an-assembly-in-the-gac.md)|  
|Démarrez l'application.|[Comment démarrer et arrêter une Application BizTalk](../core/how-to-start-and-stop-a-biztalk-application.md)|  
|Si l'application vers laquelle vous importez un assembly contenant une orchestration contient déjà un assembly ayant le même nom, le même jeton de clé publique et la même version, arrêtez et redémarrez les instances de l'hôte de destination de l'orchestration. Ainsi, vous êtes sûr que la nouvelle version de l'assembly sera utilisée par BizTalk Server.|[Comment arrêter une Instance d’hôte](../core/how-to-stop-a-host-instance.md), [comment démarrer une Instance d’hôte](../core/how-to-start-a-host-instance.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Déploiement d’applications BizTalk et la gestion des listes de contrôle](../core/biztalk-application-deployment-and-management-checklists.md)   
 [Mise à jour des Applications BizTalk](../core/updating-biztalk-applications.md)