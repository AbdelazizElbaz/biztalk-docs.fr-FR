---
title: "Problèmes courants liés aux intercepteurs BAM | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a32145e2-1367-4576-9103-86c9182c11a8
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 312bcd2ea1eaedcf44f02e2d3b702989095969d1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="common-issues-with-the-bam-interceptors"></a>Problèmes courants avec les intercepteurs BAM
Cette rubrique décrit les problèmes courants suivants qui peuvent survenir lorsque vous utilisez des intercepteurs BAM :  
  
-   Exception SQL relative à une transaction distribuée  
  
## <a name="you-receive-a-sql-exception-concerning-a-completed-distributed-transaction-or-a-transaction-descriptor"></a>Vous recevez une exception SQL relative à une transaction distribuée terminée ou à un descripteur de transaction  
 Lors de l'exécution de l'intercepteur WCF (Windows Communication Framework ) BAM, il se peut que vous voyiez les exceptions suivantes :  
  
-   La transaction distribuée est terminée. Inscrivez cette session, soit dans une nouvelle transaction, soit dans une transaction NULL.  
  
-   Le démarrage de la nouvelle requête n'est pas autorisé parce qu'elle doit être accompagnée d'un descripteur de transaction valide.  
  
 Voici quelques suggestions pour résoudre ce problème :  
  
-   Activez le suivi BAM. Ce suivi inclut tous les messages pertinents, y compris la cause première de l'erreur. Pour plus d’informations sur le suivi BAM, consultez [comment activer le traçage de l’analyse BAM](../core/how-to-enable-tracing-in-bam.md).  
  
-   Lorsque vous voyez cette exception DTC (Distributed Transaction Coordinator), essayez de réexécuter le même scénario, mais sans transaction.  
  
-   À l'aide de SQL Server Profiler, recherchez des erreurs dans le suivi qui entraîneront un abandon de la transaction.  
  
## <a name="you-receive-an-error-similar-to-interceptor-configuration-polling-interval-0-must-be-at-least-5-seconds-when-using-the-wcf-interceptor"></a>Lors de l'utilisation de l'intercepteur WCF, vous obtenez une erreur similaire à « l'intervalle d'interrogation '0' de la configuration de l'intercepteur doit être d'au moins '5' secondes »  
 Il se peut que vous rencontriez cette erreur si vous ne fournissez pas explicitement une valeur d'intervalle d'interrogation de la configuration de l'intercepteur dans le fichier de configuration de l'application ou si vous fournissez une valeur inférieure à 5 secondes qui est la valeur minimale requise.  
  
 Pour résoudre le problème, fournissez une valeur valide pour PollingIntervalSec comme indiqué :  
  
```  
<BamEndpointBehaviorExtension ConnectionString="Initial Catalog=BamPrimaryImport;Data Source=MyMachine;Integrated Security=SSPI;" PollingIntervalSec="1500" />  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Dépannage des intercepteurs BAM](../core/troubleshooting-bam-interceptors.md)