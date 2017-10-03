---
title: "Comment arrêter les Instances d’Orchestration suspendues | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipelines, terminating [HAT]
- messages, saving [HAT]
- HAT, saving messages
- HAT, terminating pipelines
- HAT, terminiating orchestrations
- orchestrations, terminating [HAT]
ms.assetid: b5d44cce-b05c-47f9-9015-5b10c2312bf1
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5dc0160be5aeeef43b9595953893b4ea1af82c62
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-terminate-suspended-orchestration-instances"></a>Arrêt des instances de l'orchestration suspendues
Vous pouvez terminer des instances d'orchestration suspendues ou des ports à partir des résultats de la requête ou du volet de visualisation dans la console Administration de BizTalk Server.  
  
> [!NOTE]
>  Chaque instance d’un livraison chronologique des messages un port d’envoi peut avoir plusieurs messages sont associés. Afin d'éviter une perte des données ou un arrêt accidentel, vérifiez l'ensemble de ces associations avant de mettre fin à une instance.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez être connecté en tant que membre du groupe opérateurs BizTalk Server pour effectuer cette procédure.  
  
### <a name="to-terminate-suspended-orchestration-instances"></a>Pour terminer les instances de l'orchestration suspendues  
  
1.  Cliquez sur **Démarrer**, cliquez sur **programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l'arborescence de la console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], puis cliquez sur le groupe BizTalk.  
  
3.  Dans le volet détails, cliquez sur le **nouvelle requête** onglet.  
  
4.  Dans le **Expression de requête** groupe, dans le **valeur** colonne, sélectionnez **Instances de Service suspendues** dans la zone de liste déroulante.  
  
5.  Procédez de l'une des manières suivantes :  
  
    -   Pour mettre fin à une instance unique, dans le **nom de champ** colonne, dans la zone de liste déroulante vide en regard de l’astérisque (**\***), sélectionnez le **nom du Service** filtre puis, dans le **valeur** colonne, spécifiez le nom du service.  
  
    -   Pour arrêter les instances en bloc, dans le **nom de champ** colonne, dans la zone de liste déroulante vide en regard de l’astérisque (**\***), sélectionnez **grouper les résultats selon** , puis dans le **valeur** colonne, spécifiez le nom du service.  
  
6.  Cliquez sur **exécuter la requête**.  
  
7.  Dans la liste de résultats de requête, cliquez sur l’instance d’orchestration ou le groupe d’instances que vous souhaitez terminer, puis cliquez sur **arrêter l’Instance** ou **arrêter les Instances**.  
  
## <a name="see-also"></a>Voir aussi  
 [Enquête sur les échecs de messages, de Port et d’Orchestration](../core/investigating-orchestration-port-and-message-failures.md)