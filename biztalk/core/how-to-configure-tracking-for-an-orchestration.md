---
title: "Comment configurer le suivi d’une Orchestration | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestrations, tracking
- orchestrations, HAT
- managing [orchestrations], tracking
- configuring [HAT tracking], orchestrations
- tracking, orchestrations
- HAT, orchestrations
ms.assetid: 8f5ed525-11f8-4bef-95c4-cfe9c971b663
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9ebae70ec70fb58a4a935be6b2c46f39cfafba59
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-tracking-for-an-orchestration"></a>Configuration du suivi pour une orchestration
Cette rubrique explique comment configurer le suivi pour une orchestration à l'aide de la console Administration de BizTalk Server.  
  
 Pour plus d’informations sur la création et l’utilisation de requêtes, consultez [à l’aide de la Console Administration de BizTalk Server](../core/using-the-biztalk-server-administration-console.md). Pour plus d’informations sur les fonctionnalités de suivi de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], consultez [afficher un Message de suivi et les données d’Instance](../core/viewing-tracked-message-and-instance-data.md).  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe d'administrateurs BizTalk Server. Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### <a name="to-configure-tracking-for-an-orchestration"></a>Pour configurer le suivi d'une orchestration  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l’arborescence de la console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez le groupe BizTalk, **Applications**, puis développez l’application contenant l’orchestration pour laquelle vous voulez configurer le suivi.  
  
3.  Cliquez sur **Orchestrations**, avec le bouton droit de l’orchestration pour laquelle vous souhaitez configurer le suivi, puis cliquez sur **propriétés**.  
  
4.  Cliquez sur le **suivi** onglet, sélectionnez les options de suivi, comme décrit dans le tableau suivant, puis cliquez sur **OK**.  
  
    |Option| Description|  
    |------------|-----------------|  
    |**Suivre les événements - début de l’Orchestration et de fin**|Activer cette case à cocher pour effectuer le suivi de l'instance de l'orchestration avant et après le traitement du processus d'entreprise complet. Le suivi d'une orchestration vous permet d'afficher les instances dans les vues de résultat des requêtes de suivi.|  
    |**Suivre les événements - envoi et réception de messages**|Cette case à cocher doit être activée pour effectuer le suivi des événements d'envoi et de réception des messages. Cette case à cocher est disponible uniquement si vous sélectionnez le **Orchestration début et fin** case à cocher.|  
    |**Suivre les événements - début de la forme et de fin**|Activez cette case à cocher quand vous devez déboguer des instances de l'orchestration dans le débogueur de l'orchestration. Quand cette case est activée, la liste des événements du débogueur de l'orchestration contient des données. Cette case à cocher est disponible uniquement si vous sélectionnez le **Orchestration début et fin** case à cocher.|  
    |**Suivre les corps de Message - avant le traitement de l’orchestration**|Activez cette case à cocher pour enregistrer et suivre le contenu réel du message avant le traitement par une instance de l'orchestration. Cette case à cocher est disponible uniquement si vous sélectionnez le **le Message d’envoi et réception** case à cocher.|  
    |**Suivre les corps de Message - après le traitement de l’orchestration**|Activez cette case à cocher pour enregistrer et suivre le contenu réel du message après le traitement par une instance de l'orchestration. Cette case à cocher est disponible uniquement si vous sélectionnez le **le Message d’envoi et réception** case à cocher.|  
    |**Suivre les propriétés de Message - messages entrants**|Cette case à cocher doit être activée pour le suivi des propriétés promues d'un message entrant.|  
    |**Suivre les propriétés de Message - messages sortants**|Activez cette case à cocher pour suivre les propriétés promues d'un message sortant.|  
  
## <a name="see-also"></a>Voir aussi  
 [La gestion des Orchestrations](../core/managing-orchestrations.md)