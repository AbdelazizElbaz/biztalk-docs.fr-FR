---
title: "Comment suspendre, reprendre et terminer des Instances d’Orchestration | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [orchestrations], resuming
- orchestrations, terminating
- managing [orchestrations], suspending
- orchestrations, resuming
- orchestrations, suspending
- managing [orchestrations], terminating
ms.assetid: 7b373dad-57d5-4696-9b29-a6c351d44fa8
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9528ac0e810a3d4e203733ab1cc5b041d3d61d31
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-suspend-resume-and-terminate-orchestration-instances"></a>Interruption, reprise et arrêt des instances de l'orchestration
Cette rubrique décrit l'interruption, la reprise et l'arrêt d'une ou plusieurs instances de service d'une orchestration en cours d'exécution à l'aide de la console Administration de BizTalk Server. Une instance de service est une instance d'orchestration que BizTalk Server est en train de traiter ou qui a été sérialisée dans la base de données MessageBox pour un traitement ou suivi plus approfondi.  
  
 Les sections suivantes décrivent les effets de ces trois opérations :  
  
-   **Suspendre.** met l'instance de service en attente. Les messages en cours de traitement sont exécutés jusqu'à la fin. Les messages sont toujours acheminés vers les instances de service mais ils ne sont pas traités.  
  
-   **Reprendre.** reprend le traitement des instances interrompues.  
  
> [!NOTE]
>  Vous ne pouvez pas reprendre une instance à partir d'un état Point d'arrêt. La reprise d'une instance dans cet état peut afficher l'état « En attente », mais l'instance risque d'échouer.  
  
-   **Mettre fin.** termine le traitement de tous les messages. L'instance de service est supprimée des bases de données BizTalk Server. Les messages que l'instance de service est en train de traiter sont également supprimés, sauf ceux qui sont également référencés par une instance de service non arrêtée.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter la procédure décrite dans cette rubrique, vous devez avoir ouvert une session en tant que membre du groupe des opérateurs de BizTalk Server ou du groupe d'administrateurs de BizTalk Server. Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### <a name="to-view-start-stop-or-terminate-an-instance-of-an-orchestration"></a>Pour démarrer, arrêter ou terminer une instance d'orchestration  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Sélectionnez le groupe BizTalk pour afficher la page Hub associée.  
  
3.  Sous **travail en cours**, cliquez sur **des instances de service en cours d’exécution**.  
  
     Le volet de résultats de la requête situé dans la section inférieure de la page affiche toutes les instances de l'orchestration.  
  
4.  Pour affiner la requête et afficher d’autres instances de l’orchestration, cliquez sur la zone sous **valeur** pour le **recherche de** , sélectionnez le type d’instance à afficher, puis cliquez sur **exécuter la requête** . Pour plus d'informations sur la création des requêtes, consultez les rubriques relatives à la recherche dans la section Voir aussi.  
  
5.  Cliquez sur l’instance souhaitée, puis cliquez sur **Suspend**, **reprise**, ou **Terminate**. Cette fonctionnalité vous permet de sélectionner les instances à reprendre.  
  
    > [!NOTE]
    >  Pour appliquer l'opération à plusieurs instances, maintenez la touche CTRL enfoncée, puis cliquez sur les instances souhaitées. Cliquez sur une instance, puis cliquez sur **Suspend**, **reprise**, ou **Terminate**.  
  
     [États de l’Instance service](../core/service-instance-states.md) fournit des informations sur l’état suspendu.  
  
## <a name="see-also"></a>Voir aussi  
 [La gestion des Orchestrations](../core/managing-orchestrations.md)   
 [Comment rechercher des Instances de Service en cours d’exécution](../core/how-to-search-for-running-service-instances.md)   
 [Comment rechercher des Instances de Service suspendues](../core/how-to-search-for-suspended-service-instances.md)