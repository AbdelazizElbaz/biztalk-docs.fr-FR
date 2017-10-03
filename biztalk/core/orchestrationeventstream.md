---
title: OrchestrationEventStream | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d7c63610-6344-4b71-8d65-3add7883bc79
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dc1fd0dc229c38b3a060c75a9c584259175d72fd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="orchestrationeventstream"></a>OrchestrationEventStream
Vous utilisez l'API OrchestrationEventStream (OES) lorsque votre application s'exécute sur un ordinateur sur lequel BizTalk Server est installé et que vous assurez le suivi d'éléments qui font partie de transactions d'orchestrations BizTalk.  
  
 L'API OES stocke les données de suivi tout d'abord dans la base de données MessageBox BizTalk. Régulièrement, les données sont traitées et rendues persistantes dans la base de données Importation principale BAM par le service TDDS (Tracking Data Decode Service).  
  
 L'API OES se trouve dans l'espace de noms Microsoft.BizTalk.Bam.EventObservation. Pour utiliser cette API, vous devez ajouter Microsoft.Biztalk.BAM.Xlangs.dll à votre projet.  
  
## <a name="oes-members"></a>Membres OES  
 L'API OES est dérivée de la classe [Microsoft.BizTalk.Bam.EventObservation.EventStream](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.aspx) .  
  
 Elle implémente toutes les méthodes de la classe EventStream, mais présente l'exception suivante dans les comportements :  
  
 **Clear() de void statique publique ;**  
  
 Pas d'opération.  
  
 **Flush() de void statique publique ;**  
  
 Pas d'opération.  
  
## <a name="see-also"></a>Voir aussi  
 [Classes EventStream](../core/eventstream-classes.md)