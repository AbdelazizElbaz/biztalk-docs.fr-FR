---
title: "Étape 3 b : lier l’orchestration avec un port d’envoi dynamique pour interagir magasin et scénario (Pull) avant | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 55eec1f3-b920-48f8-946a-9ad7afa36fd6
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b289d8478eb020067d9231fb1d4f135c7b43b289
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-3b-bind-the-orchestration-with-dynamic-send-port-for-interact-store-and-forward-pull-scenario"></a>Étape 3 b : lier l’orchestration avec un port d’envoi dynamique pour interagir magasin et scénario de (Pull) vers l’avant
Avant de commencer cette étape, vous devez effectuer [étape 3 a : création d’une orchestration pour le port d’envoi dynamique pour interagir magasin et scénario (Pull) avant](../../adapters-and-accelerators/fileact-interact/step-3a-create-orchestration-for-dynamic-send-port-interact-store-and-forward.md).  
  
### <a name="to-add-a-file-receive-location"></a>Pour ajouter un emplacement de réception de fichier  
  
1.  Démarrer **Administration de BizTalk Server**.  
  
2.  Dans la Console Administration de BizTalk Server, dans le volet gauche, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **paramètres de plateforme**, puis Cliquez sur **Instances d’hôte**. Vérifiez que l’état de la **BizTalkServerApplication** héberger l’instance et l’instance d’hôte interagir est **en cours d’exécution**. Dans le cas contraire, cliquez sur les instances d’hôte, puis cliquez sur **Démarrer**.  
  
3.  Dans le volet gauche, développez des Applications, puis BizTalk Application 1. Cliquez sur Orchestrations.  
  
4.  Avec le bouton droit **DynamicSendOrchestration** et cliquez sur **propriétés**.  
  
5.  Dans le **propriétés d’Orchestration** boîte de dialogue, dans le volet gauche, cliquez sur **liaisons** et procédez comme suit :  
  
    |**Utilisez cette**|**Pour ce faire**|  
    |------------------|--------------------|  
    |**Hôte**|Dans la liste déroulante, sélectionnez **BizTalkServer Application**.|  
    |**Extraction dynamique**|Dans la liste déroulante, sélectionnez **Tutorial_IA_DynamicSendPort**.|  
    |**SendPullResponseToSender**|Dans la liste déroulante, sélectionnez **Tutorial_IA_SendPullResponsetoReceiver**.|  
  
## <a name="see-also"></a>Voir aussi  
 [Étape 3 a : création d’une orchestration pour le port d’envoi dynamique pour interagir magasin et scénario de (Pull) vers l’avant](../../adapters-and-accelerators/fileact-interact/step-3a-create-orchestration-for-dynamic-send-port-interact-store-and-forward.md)