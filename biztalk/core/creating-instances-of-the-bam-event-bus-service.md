---
title: "Création d’Instances de Service Bus d’événements BAM | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 454bdde7-45a6-41ab-9196-f662273f0f2b
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: afbe8f2e70baa3a963150991ced54a9d38adba88
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="creating-instances-of-the-bam-event-bus-service"></a>Création d’Instances de Service Bus d’événements BAM
Le service Bus d'événements BAM s'exécute au sein d'un hôte de l'application BizTalk. Vous pouvez utiliser l'hôte par défaut pour héberger ce service ou en créer un. Si un hôte héberge le service Bus d'événements BAM, toutes les nouvelles instances que vous créez pour cet hôte hébergeront également le service.  
  
 Pour plus d’informations sur l’hôte par défaut, consultez [hôtes](../core/hosts.md).  
  
 Pour plus d’informations sur la création d’ordinateurs hôtes, consultez [la création d’un nouvel hôte](../core/how-to-create-a-new-host.md).  
  
 Pour plus d’informations sur la création d’instances d’hôte, consultez [l’ajout d’une Instance d’hôte](../core/how-to-add-a-host-instance.md).  
  
 Pour plus d’informations sur la création et la configuration des ordinateurs hôtes et les instances d’hôte, consultez [gestion d’hôtes BizTalk et les Instances d’hôte](../core/managing-biztalk-hosts-and-host-instances.md).  
  
### <a name="to-create-the-host-that-hosts-the-bam-event-bus-service"></a>Pour créer l'hôte qui héberge le service Bus d'événements BAM  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, cliquez sur **Microsoft**[!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans la fenêtre de la Console Administration de BizTalk, développez le **Administration de BizTalk Server** nœud, développez le **groupe Biztalk** nœud et développez le **paramètres de plateforme** nœud , avec le bouton droit le **hôtes** nœud, sélectionnez **nouveau**, puis cliquez sur **hôte**.  
  
3.  Dans le **propriétés de l’hôte** boîte de dialogue le **nom** zone, tapez un nom descriptif pour l’hôte.  
  
4.  Sur le **général** onglet, sélectionnez le **autoriser le suivi de hôte** case à cocher.  
  
     Un nouveau nœud enfant s’affiche sous le **hôtes** nœud portant le nom du nouvel hôte.  
  
5.  Dans le **groupe Windows** , tapez le nom du groupe Windows à affecter à cet ordinateur hôte, puis cliquez sur **OK**.  
  
     Un nouveau nœud enfant s’affiche sous le **hôtes** nœud portant le nom du nouvel hôte.  
  
### <a name="to-create-a-new-host-instance-of-the-host"></a>Pour créer une instance d'hôte de l'hôte  
  
1.  Avec le bouton droit le **Instance d’hôte** nœud, sélectionnez **nouveau**, puis cliquez sur **Instance d’hôte**.  
  
2.  Sélectionnez un serveur sur lequel l’instance d’hôte s’exécuter, puis cliquez sur **OK**.  
  
### <a name="to-add-hosting-tracking-to-the-host"></a>Pour activer le suivi de l'hôte  
  
1.  Cliquez sur l’hôte que vous voulez reconfigurer, puis cliquez sur **propriétés** .  
  
2.  Sur le **général** onglet, sélectionnez **autoriser le suivi de hôte**, puis cliquez sur **OK**.  
  
3.  Redémarrez toutes les instances de cet hôte.  
  
### <a name="to-remove-hosting-tracking-from-the-host"></a>Pour désactiver le suivi de l'hôte  
  
1.  Cliquez sur l’ordinateur hôte à partir de laquelle vous souhaitez supprimer le suivi de l’hôte, puis cliquez sur **propriétés**.  
  
2.  Désactivez le **suivi de l’hôte d’autoriser** case à cocher, puis cliquez sur **OK**.  
  
3.  Redémarrer les instances de cet hôte.  
  
## <a name="see-also"></a>Voir aussi  
 [La gestion de Service Bus d’événements BAM](../core/managing-the-bam-event-bus-service.md)   
 [Recommandations de sécurité BAM](../core/bam-security-recommendations.md)   
 [Business Activity Monitoring (BAM)](../core/business-activity-monitoring-bam.md)