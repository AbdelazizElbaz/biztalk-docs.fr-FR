---
title: "Comment utiliser l’appel de règles de forme | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Call Rules shape [Orchestration Designer], how to
- Call Rules shape [Orchestration Designer], configuring
- Call Rules shape [Orchestration Designer], policies
- policies, Call Rules shape [Orchestration Designer]
ms.assetid: e4bc8a2c-de7e-4e3a-81b8-12bcebb17d27
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c85badfaf22ff4fb6aebd9ed19c757faaa1f303c
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="how-to-use-the-call-rules-shape"></a>Utilisation de la forme Appeler règles
Dans le Concepteur d’Orchestration, vous pouvez utiliser la **appeler règles** forme pour appeler une stratégie d’entreprise.  
  
### <a name="to-configure-the-call-rules-shape"></a>Pour configurer la forme Appeler règles  
  
1.  À partir de la boîte à outils, dans le **Orchestrations BizTalk** onglet, faites glisser le **appeler règles** forme sur une ligne de connexion sur l’aire de conception d’Orchestration.  
  
     — Ou :  
  
     Avec le bouton droit de la ligne de connexion ou l’espace réservé où vous souhaitez ajouter la forme, pointez sur **insérer une forme** dans le menu contextuel, puis cliquez sur **appeler règles**.  
  
    > [!NOTE]
    >  Dans BizTalk Server, vous n’avez pas besoin d’avoir une étendue atomique pour insérer un **appeler règles** forme. Vous pouvez faire glisser un **appeler règles** mettre en forme dans l’aire de conception d’Orchestration à partir de la boîte à outils. Toutefois, dans BizTalk Server, le **appeler règles** élément de menu est désactivé dans le menu contextuel si vous essayez d’insérer un **appeler règles** forme à l’intérieur d’une orchestration qui ne dispose pas d’une étendue atomique. Il s'agit d'une restriction liée au produit [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
2.  Dans le Concepteur d’Orchestration, sélectionnez la **appeler règles** forme.  
  
3.  Double-cliquez sur la forme pour afficher les **configuration de la stratégie RèglesAppel** boîte de dialogue.  
  
4.  Dans le **sélectionnez la stratégie commerciale que vous souhaitez appeler** liste déroulante, sélectionnez la stratégie que vous avez besoin.  
  
    > [!NOTE]
    >  La configuration de la forme Appeler règles examine la toute dernière version enregistrée d'une stratégie lors de la détermination des types utilisés dans la stratégie. Lors de l’exécution, la dernière version déployée de la stratégie est utilisée.  
  
5.  Dans le **spécifier les paramètres de stratégie** zone de liste, sélectionnez une variable à partir de la **nom de paramètre** propriété.  
  
    > [!NOTE]
    >  Le **appeler règles** forme essentiellement reconstruit le message, comme si vous utilisez un **construire** forme, ce qui peut entraîner des propriétés de contexte du message soit perdu.  
  
    > [!NOTE]
    >  Vous pouvez spécifier un message ou une variable .NET en tant que paramètre à une stratégie BRE. Pour passer un **TypedXmlDocument** faits, spécifiez le message correspondant est déclaré dans l’orchestration en tant que paramètre. Pour transmettre un fait .NET, spécifiez une variable .NET qui a été déclarée en tant que paramètre dans l'orchestration. Pour transmettre un fait de la base de données, spécifiez une variable .NET de type **DataConnection** ou **TypedDataTable** en tant que paramètre à la stratégie.