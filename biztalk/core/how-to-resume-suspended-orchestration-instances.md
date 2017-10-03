---
title: "Comment reprendre les Instances d’Orchestration suspendues | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- instances, resuming [HAT]
- HAT, resuming orchestrations
- HAT, resuming pipelines
- orchestrations, resuming
- resuming, pipelines
- resuming, orchestrations
- HAT, debug mode
ms.assetid: da133183-68d9-48d1-9601-8f6d4d5b8898
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6696547ce3e918dc8d84b7cfcb4f24e31c8b70a0
ms.sourcegitcommit: 5355a25d120d094778fb8f68ea14cab55c68d292
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/28/2017
---
# <a name="how-to-resume-suspended-orchestration-instances"></a>Reprise des instances de l'orchestration suspendues
Si vous avez suspendu des instances de l'orchestration associées à l'état « Suspendu (peut être repris) », vous pouvez tenter de reprendre l'instance de l'orchestration à partir des résultats de requête ou du volet de visualisation. La reprise de l'instance de l'orchestration n'est possible que si vous avez remédié au problème sous-jacent qui a entraîné la suspension de cette instance.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez être connecté en tant que membre du groupe opérateurs BizTalk Server pour effectuer cette procédure.  
  
### <a name="to-resume-suspended-orchestration-instances"></a>Pour reprendre les instances de l'orchestration suspendues  
  
1.  Cliquez sur **Démarrer**, cliquez sur **programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l’arborescence de la console, développez **Administration de BizTalk Server**, puis cliquez sur le groupe BizTalk.  
  
3.  Dans le volet détails, cliquez sur le **nouvelle requête** onglet.  
  
4.  Dans le **Expression de requête** groupe, dans le **valeur** colonne, sélectionnez **Instances de Service suspendues** dans la zone de liste déroulante.  
  
5.  Procédez de l'une des manières suivantes :  
  
    -   Pour reprendre une instance unique, dans le **nom de champ** colonne, dans la zone de liste déroulante vide en regard de l’astérisque (**\***), sélectionnez le **nom du Service** filtre et Ensuite, dans le **valeur** colonne, spécifiez le nom du service.  
  
    -   Pour reprendre les instances en bloc, dans le **nom de champ** colonne, dans la zone de liste déroulante vide en regard de l’astérisque (**\***), sélectionnez **grouper les résultats selon** puis, dans le **valeur** colonne, spécifiez le nom du service.  
  
6.  Cliquez sur **exécuter la requête**.  
  
7.  Dans la liste de résultats de requête, cliquez sur l’instance d’orchestration que vous souhaitez reprendre, puis cliquez sur **reprendre une Instance** ou **reprendre les Instances**. Cela vous permet de sélectionner les instances à reprendre.  
  
     [États de l’Instance service](../core/service-instance-states.md) fournit des informations sur la sur l’état suspendu.  
  
## <a name="see-also"></a>Voir aussi  
 [Enquête sur les échecs de messages, de Port et d’Orchestration](../core/investigating-orchestration-port-and-message-failures.md)
