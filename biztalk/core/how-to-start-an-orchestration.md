---
title: "Comment démarrer une Orchestration | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [orchestrations], starting
- starting, orchestrations
- orchestrations, starting
ms.assetid: 83411279-ee6f-4d68-aa3b-b5cd5e106088
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e277c078a36129a125937114ee9287a1e97999b3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-start-an-orchestration"></a>Démarrage d'une orchestration
Cette rubrique explique comment démarrer une orchestration à l'aide de la console Administration de BizTalk Server. Lorsque vous démarrez une orchestration, elle commence à traiter les messages entrants.  
  
 Lorsque vous démarrez une orchestration, gardez les points importants suivants à l'esprit :  
  
-   Avant de démarrer une orchestration, celle-ci doit être inscrite, avec tous les ports d'envoi et les groupes de ports d'envoi qui lui sont associés. Pour obtenir des instructions, consultez [comment inscrire une Orchestration](../core/how-to-enlist-an-orchestration.md) et [l’inscription d’un Port d’envoi ou un groupe de ports d’envoi](../core/how-to-enlist-a-send-port-or-send-port-group.md).  
  
-   Le démarrage d'une orchestration ne démarre pas automatiquement les ports d'envoi associés. Vous devez les démarrer séparément, comme décrit dans [comment démarrer un Port d’envoi ou un groupe de ports d’envoi](../core/how-to-start-a-send-port-or-send-port-group.md).  
  
-   Si vous inscrivez les ports d'envoi et/ou les groupes de ports d'envoi associés à cette orchestration sans les démarrer, BizTalk Server place tout message destiné à ces ports ou groupes de ports dans la file d'attente des messages interrompus de l'hôte sur lequel ces ports ont été inscrits.  
  
> [!NOTE]
>  Le développeur peut démarrer une orchestration pour tester sa fonctionnalité au cours du processus de développement à l’aide de la procédure dans cette rubrique.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter la procédure décrite dans cette rubrique, vous devez avoir ouvert une session en tant que membre du groupe des opérateurs de BizTalk Server ou du groupe d'administrateurs de BizTalk Server. Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### <a name="to-start-an-orchestration"></a>Pour démarrer une orchestration  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l’arborescence de la console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez le groupe BizTalk, **Applications**, puis développez l’application contenant l’orchestration que vous souhaitez démarrer.  
  
3.  Cliquez sur **Orchestrations**, avec le bouton droit de l’orchestration, puis cliquez sur **Démarrer**.  
  
    > [!IMPORTANT]
    >  Si vous n'avez pas inscrit le port d'envoi et les groupes de ports d'envoi associés préalablement au démarrage de l'orchestration, un message d'erreur s'affiche.  
  
    > [!NOTE]
    >  Pour démarrer plusieurs orchestrations à la fois, maintenez la touche MAJ enfoncée et sélectionnez chaque orchestration, avec le bouton droit une orchestration, puis cliquez sur **Démarrer**.  
  
## <a name="see-also"></a>Voir aussi  
 [La gestion des Orchestrations](../core/managing-orchestrations.md)   
 [Comment arrêter une Orchestration](../core/how-to-stop-an-orchestration.md)   
 [Comment démarrer et arrêter une Application BizTalk](../core/how-to-start-and-stop-a-biztalk-application.md)