---
title: "Comment configurer l’envoi de l’adaptateur MQSeries et les gestionnaires de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- receive handlers, MQSeries adapters
- configuring [MQSeries adapters], receive handlers
- MQSeries adapters, send handlers
- MQSeries adapters, receive handlers
- send handlers, MQSeries adapters
- configuring [MQSeries adapters], send handlers
ms.assetid: e1cfc415-50d2-440b-9301-ad69da28ad3e
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e9a1e933f62adaf4e17fae5334e65f50610fb6f1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-mqseries-adapter-send-and-receive-handlers"></a>Comment configurer l’adaptateur MQSeries envoyer et recevoir des gestionnaires
Vous pouvez configurer des propriétés pour les gestionnaires d'envoi et de réception de l'adaptateur MQSeries par l'intermédiaire de la console Administration de BizTalk Server. Le processus décrit dans [comment configurer les emplacements de réception de la carte de MQSeries et les Ports d’envoi](../core/how-to-configure-mqseries-adapter-receive-locations-and-send-ports.md) établit les valeurs pour la majorité des propriétés du Gestionnaire d’envoi.  
  
## <a name="to-configure-the-send-and-receive-handlers"></a>Pour configurer les gestionnaires d'envoi et de réception  
 Suivez ces étapes pour configurer les gestionnaires d'envoi et de réception de l'adaptateur MSQeries :  
  
1.  Cliquez sur **Démarrer**, pointez sur **programmes**, pointez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans la console Administration de BizTalk Server, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, cliquez pour développer **paramètres de plateforme**, puis cliquez sur à Développez **cartes**.  
  
3.  Dans la liste développée des adaptateurs, sélectionnez **MQSeries**. La liste des gestionnaires d'envoi et de réception liés à l'adaptateur MQSeries apparaît dans le volet de droite.  
  
4.  Dans le volet de droite, double-cliquez sur un gestionnaire d'envoi ou de réception.  
  
5.  Dans le **propriétés du Gestionnaire d’adaptateur** boîte de dialogue, cliquez sur **propriétés**.  
  
6.  Dans le **propriétés du Transport MQSeries** boîte de dialogue zone, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Nombre maximal de Messages dans un lot**|Définissez le nombre maximal de messages dans un lot. S’applique uniquement au gestionnaire d’envoi.|  
    |**Server**|Nom de l'ordinateur exécutant MQSeries Server pour Windows.|  
  
7.  Cliquez sur **OK**.  
  
    > [!NOTE]
    >  Les propriétés Emplacement de réception et Port d'envoi remplacent les valeurs de gestionnaire de réception et de gestionnaire d'envoi. Si les propriétés Emplacement de réception et Port d'envoi ne comportent aucune valeur, l'adaptateur utilise respectivement les valeurs de gestionnaire de réception et de gestionnaire d'envoi.  
  
8.  Cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment configurer MQSeries adaptateur emplacements de réception et Ports d’envoi](../core/how-to-configure-mqseries-adapter-receive-locations-and-send-ports.md)   
 [Configuration de l’adaptateur MQSeries](../core/configuring-the-mqseries-adapter.md)