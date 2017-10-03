---
title: "Comment afficher des informations sur l’Instance d’une Orchestration | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestrations, viewing
- managing [orchestrations], viewing
ms.assetid: 860ac2b2-c556-4e1f-8b7f-18ab8be52db4
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 84129d48fba15dadfc97722ead85b1535a8fa597
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-view-instance-information-for-an-orchestration"></a>Affichage des informations sur l'instance d'une orchestration
Cette rubrique explique comment afficher les informations sur l'instance d'une orchestration à l'aide de la console Administration de BizTalk Server. Une instance de service est une instance d'une orchestration que BizTalk Server est en train de traiter ou qu'il a sérialisée dans la base de données MessageBox pour un traitement ou suivi plus approfondi.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté en tant que membre du groupe des administrateurs de BizTalk Server. Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### <a name="to-view-instance-information-for-an-orchestration"></a>Pour afficher des informations sur l'instance d'une orchestration  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l’arborescence de la console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez le groupe BizTalk, **Applications**, puis développez l’application contenant l’orchestration pour laquelle vous souhaitez afficher des informations sur l’instance.  
  
3.  Cliquez sur **Orchestrations**, sélectionnez l’orchestration pour laquelle vous souhaitez afficher les informations d’instance, cliquez sur **vue**, puis sélectionnez **informations sur l’Instance**.  
  
     Le volet de résultats de la requête situé dans la section inférieure de la page affiche toutes les instances de l'orchestration.  
  
     Pour affiner les requête et afficher des informations autre instance de l’orchestration, cliquez sur la zone sous **valeur** pour le champ Rechercher, sélectionnez le type d’instance à afficher, puis cliquez sur **exécuter la requête**. Pour plus d'informations sur la création des requêtes, consultez les rubriques relatives à la recherche dans la section Voir aussi.  
  
## <a name="see-also"></a>Voir aussi  
 [La gestion des Orchestrations](../core/managing-orchestrations.md)   
 [Comment rechercher des Instances de Service en cours d’exécution](../core/how-to-search-for-running-service-instances.md)   
 [Comment rechercher des Instances de Service suspendues](../core/how-to-search-for-suspended-service-instances.md)   
 [Comment rechercher des Messages](../core/how-to-search-for-messages.md)   
 [Comment rechercher des abonnements](../core/how-to-search-for-subscriptions.md)