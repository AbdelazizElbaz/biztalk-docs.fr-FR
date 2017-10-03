---
title: "Dépendances et déploiement d’Application | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deploying [applications], dependencies
- assemblies, dependencies
- artifacts, dependencies
- applications, dependencies
ms.assetid: b78c5a0d-b042-4862-bce7-59469365b369
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5cc7e4b44a09da04e62062d90cd99da0354cca34
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="dependencies-and-application-deployment"></a>Dépendances et déploiement des applications
Cette rubrique décrit les effets des dépendances entre les artefacts de plusieurs applications BizTalk sur la gestion et le déploiement des applications.  
  
 Lorsqu’un artefact doit en utiliser un autre pour fonctionner correctement, elle est dite *dépendants* sur un autre artefact. Exemple de ce type de dépendance : lorsqu'une orchestration doit utiliser un schéma spécifique pour la résolution de message ou un pipeline spécifique afin de transmettre les messages correctement. Dans ces deux scénarios, l'orchestration est dépendante d'un autre artefact.  
  
 Avant de pouvoir mettre à jour un artefact dans une application, vous devez d'abord annuler son déploiement et celui des artefacts qui dépendent de celui-ci. Lorsque des artefacts dépendants existent dans la même application, BizTalk Server gère automatiquement les tâches d'annulation du déploiement et de redéploiement pour les artefacts mis à jour et dépendants. Ce n'est pas le cas, cependant, lorsque des artefacts dépendants existent dans différentes applications. Vous devez annuler manuellement le déploiement des artefacts dépendants avant de pouvoir mettre à jour un artefact dont ils dépendent. Ensuite, vous devez redéployer manuellement les artefacts dépendants.  
  
 Pour éviter d'avoir à le faire manuellement, vous pouvez conserver tous les artefacts dépendants dans la même application. Toutefois, cela n'est pas toujours possible. Comme décrit dans [artefacts que doit être Unique dans une Application ou d’un groupe](../core/artifacts-that-must-be-unique-in-an-application-or-group.md), la plupart des types d’artefacts doivent être uniques dans un groupe BizTalk. Vous ne pouvez avoir le même artefact dans deux applications du même groupe, même si celles-ci contiennent des artefacts qui dépendent du même artefact.  
  
 Lorsque cela se produit, vous pouvez ajouter l'artefact requis à une application, puis ajouter une référence à celle-ci à partir de n'importe quelle autre application contenant les artefacts qui dépendent de celui-ci. Lorsque vous ajoutez une référence à une application, les artefacts qu'elle contient peuvent utiliser ceux de l'application à laquelle elle fait référence. Pour obtenir des instructions sur l’ajout d’une référence, consultez [comment ajouter une référence à une autre Application](../core/how-to-add-a-reference-to-another-application.md).  
  
 Le schéma suivant représente deux applications qui dépendent chacune des artefacts d'une troisième. L'application Order Processing utilise Schema1, contenu dans l'application Schemas, et contient donc une référence à l'application Schemas. L'application Mortgage utilise Schema2, contenu également dans l'application Schemas, et, à l'instar de l'application précédente, contient une référence à l'application Schemas.  
  
 ![Deux applications référençant une troisième application](../core/media/applicationdependencies.gif "ApplicationDependencies")  
  
 L'ajout d'une référence d'une application à une autre application crée une dépendance entre elles qui affecte la manière dont vous les déployez et les gérez. En raison des divers effets des dépendances entre applications décrits plus loin dans cette rubrique, nous vous recommandons de suivre les meilleures pratiques pour ajouter des artefacts à l’application, comme décrit dans [meilleures pratiques pour déployer une Application BizTalk](../core/best-practices-for-deploying-a-biztalk-application.md).  
  
 Le schéma suivant présente les étapes de mise à jour d'un assembly en cas de chaîne de dépendances, ainsi que l'ensemble des assemblys dépendant de celui-ci et existant dans la même application.  
  
 ![Mise à jour d’un assembly avec dépendances](../core/media/simpleadminredeploy.gif "SimpleAdminRedeploy")  
  
 Le schéma suivant présente les étapes de mise à jour d'un assembly en cas de chaîne de dépendances, ainsi que l'un des assemblys dépendants existant dans une autre application.  
  
 ![Mise à jour d’un assembly avec dépendances externes](../core/media/complexadminredeploy.gif "ComplexAdminRedeploy")  
  
> [!NOTE]
>  L'arrêt complet avant la mise à jour d'un assembly est justifié par le fait que la procédure automatique désinscrit l'orchestration, puis arrête et termine tous les messages. Si vous devez poursuivre le traitement des messages, vous pouvez déployer une autre version du même assembly et ainsi éviter d'avoir à arrêter et terminer les messages. Pour plus d’informations, consultez [mise à jour des Applications BizTalk](../core/updating-biztalk-applications.md).  
  
 Effets pouvant résulter des dépendances entre les applications :  
  
-   **Arrêt d’un artefact.** Si vous arrêtez un artefact dans une application (qui peut être dû à l'arrêt de l'ensemble de l'application) dont une autre application dépend, l'application dépendante ne fonctionne pas correctement. Pour plus d’informations sur l’arrêt d’une application, consultez [comment démarrer et arrêter une Application BizTalk](../core/how-to-start-and-stop-a-biztalk-application.md).  
  
-   **Suppression ou modification de l’état d’un artefact.** Si vous ajoutez une référence d'une application à une autre et modifiez l'état d'un artefact dont une autre application dépend, ou que vous supprimez l'artefact, l'application dépendante ne fonctionne pas correctement. Pour plus d’informations sur la modification de l’état d’un artefact, consultez la section sur l’artefact approprié dans [la gestion des artefacts](../core/managing-artifacts.md).  
  
-   **Importation d’applications qui ont des dépendances.** Pour importer une application dans un autre groupe BizTalk et l'exécuter dans celui-ci, vous devez également importer les artefacts dont cette application dépend. Pour ce faire, vous pouvez dans un premier temps importer l'autre application ou ajouter l'artefact nécessaire à l'application le requérant. Pour plus d’informations sur l’importation d’applications, consultez [comment importer une Application BizTalk](../core/how-to-import-a-biztalk-application.md).  
  
    > [!NOTE]
    >  BizTalk Server vérifie l'identité d'une application en faisant correspondre les noms des applications dans les groupes BizTalk sources et de destination. Il ne vérifie pas les artefacts dont dépend votre application. Lorsque vous importez une application dépendante et celle à laquelle elle fait référence, nous vous recommandons de vérifier que l'application référencée contient les artefacts requis.  
  
-   **Importation d’applications qui ont des références.** Si une application que vous importez est dépendante d'un artefact présent dans une autre application, vous devez ajouter une référence à cette application. L'Assistant Importation fournit cette option. Si vous utilisez la commande ImportApp de BTSTask, toutefois, vous devez ajouter la référence à l’application après l’importation, comme décrit dans [comment ajouter une référence à une autre Application](../core/how-to-add-a-reference-to-another-application.md). Même si BizTalk Server vérifie que l'application référencée existe, nous vous recommandons de vérifier également que l'application référencée contient l'artefact requis.  
  
-   **L’installation d’applications qui ont des dépendances.** Lorsque vous installez une application, vous devez également installer les applications dont elle dépend. Lorsque vous installez une application dépendant d'un artefact, tel qu'un assembly BizTalk, contenu dans une autre application, vous devez installer au préalable l'application contenant cet artefact. Par exemple, si vous souhaitez installer l'application A, et que celle-ci dépend d'un assembly contenu dans l'application B, vous devez installer au préalable l'application B. Vous pouvez ensuite installer l’Application a Pour plus d’informations sur l’installation des applications, consultez [comment installer une Application BizTalk](../core/how-to-install-a-biztalk-application.md).  
  
-   **Déplacement d’un artefact.** Lorsque vous déplacez un artefact vers une nouvelle application, les autres artefacts dont il dépend sont également déplacés, sauf si la nouvelle application comporte une référence aux applications contenant les artefacts dont celui déplacé dépend. En outre, tous les artefacts ayant des dépendances sur l’artefact déplacé également seront déplacés, sauf si les applications les contenant comportent une référence à la nouvelle application. Lors du déplacement d'un artefact, la liste des ceux qui seront également déplacés s'affiche. Pour obtenir des instructions sur le déplacement d’un artefact, voir [comment déplacer un artefact vers une autre Application](../core/how-to-move-an-artifact-to-a-different-application.md).  
  
-   **Mise à jour un artefact lorsqu’un artefact dans une autre application qui en dépend.** Lorsque vous mettez à jour un artefact dans une application dépendant d'un artefact dans la même application, BizTalk Server gère automatiquement les tâches d'annulation du déploiement et de redéploiement de l'artefact dépendant. Cependant, si vous souhaitez mettre à jour un artefact dans une application, et qu'un artefact dans une autre application dépend de celui-ci, vous devez annuler le déploiement et redéployer manuellement l'artefact dépendant en procédant comme suit :  
  
    1.  Arrêtez, désinscrivez et supprimez la liaison de l'artefact dépendant.  
  
    2.  Mettez à jour l'artefact dont il dépend.  
  
    3.  Liez, inscrivez et démarrez l'artefact dépendant.  
  
## <a name="see-also"></a>Voir aussi  
 [Présentation de gestion et déploiement d’applications BizTalk](../core/understanding-biztalk-application-deployment-and-management.md)