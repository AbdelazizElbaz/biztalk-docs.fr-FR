---
title: Le traitement par lots | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- batching
- Messaging Engine, batching
- batching, batch size
- batching, about batching
- batching, configuring
- batching, Messaging Engine
ms.assetid: eadc177a-d395-4f99-8dab-aa706fd8ea00
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ca31344e60daa88a37c21d0f90b6cf2d2a8aa5a7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="batching"></a>Traitement par lot
*Le traitement par lot* est un traitement sérialisé d’un ensemble de messages qui permet des optimisations en rapport à la base de données avec des boucles. Un lot est une unité de travail atomique, c'est-à-dire qui réussit globalement ou échoue globalement. Si une opération d'un lot réussit mais qu'une autre opération échoue, toutes les opérations qui constituent ce lot sont invalidées et doivent être répétées.  
  
 BizTalk Server utilise le traitement par lot pour :  
  
-   amortir le coût de la transaction sur plusieurs messages ;  
  
-   augmenter la vitesse en réduisant le nombre interne d'allers-retours vers une base de données ;  
  
-   optimiser l'utilisation de la réserve de threads de BizTalk Server en utilisant l'API asynchrone BizTalk Server.  
  
## <a name="applying-batching"></a>Application d'un traitement par lot  
 Le traitement par lot est configuré dans les propriétés avancées d'un emplacement de réception et est automatiquement activé du côté des ports d'envoi.  
  
## <a name="lowering-the-batch-size"></a>Réduction de la taille d'un lot  
 Vous devez réduire la taille des lots dans les cas suivants :  
  
-   lors du traitement de messages volumineux ;  
  
-   lorsque les allers-retours vers la base de données ne constituent pas l'engorgement.  
  
> [!NOTE]
>  Soyez prudent lorsque vous modifiez le **LargeMessageThreshold** paramètre. La taille de lot multipliée par la taille moyenne des messages doit être inférieure à la **LargeMessageThreshold** définition, sauf si la taille de lot est 1.  
  
## <a name="see-also"></a>Voir aussi  
 [Le moteur de messagerie](../core/the-messaging-engine.md)   
 [Traitement par lot des Messages pour le traitement de réception](../core/batching-messages-for-receive-processing.md)   
 [Traitement par lot des Messages pour le traitement d’envoi](../core/batching-messages-for-send-processing.md)