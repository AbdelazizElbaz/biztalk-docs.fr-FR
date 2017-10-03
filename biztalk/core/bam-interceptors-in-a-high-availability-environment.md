---
title: "Les intercepteurs BAM dans un environnement à haute disponibilité | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 555c8200-949f-4c7d-8041-5ba4b6cbaed5
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 79a697eb2a1a27ceeec1538ad8d46127413e7ed1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="bam-interceptors-in-a-high-availability-environment"></a>Intercepteurs BAM dans un environnement haute disponibilité
Cette rubrique décrit le processus de basculement pour les intercepteurs WF BAM et WCF BAM dans un environnement à haute disponibilité lors d'un basculement SQL Server.  
  
## <a name="bam-wf-interceptor"></a>Intercepteur WF BAM  
 Dans un environnement à haute disponibilité, l'intercepteur WF BAM tente à nouveau de récupérer le fichier de configuration de l'intercepteur si un problème de connexion SQL Server survient lors d'un basculement SQL Server. L'intercepteur n'effectue toutefois pas de nouvelle tentative lors de l'écriture des données dans la base de données d'importation principale BAM si un basculement SQL Server est en cours. Il s’agit, car l’intercepteur s’appuie sur le comportement de la **WorkflowCommitBatchService** classe lors de l’écriture des données à la base de données d’importation principale BAM.  
  
 Dans l’exemple suivant, **DefaultWorkflowCommitWorkBatchService** est ajouté en tant qu’un service d’exécution enableretries = « true » afin qu’il effectue une nouvelle tentative du lot comme indiqué dans l’extrait suivant d’un fichier App.config :  
  
```  
<add type="System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService, System.Workflow.Runtime, Version=3.0.00000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"  enableRetries="True"/>  
```  
  
 Toutefois, s’il existe des transactions ambiantes lors de la **CommitWorkBatch** méthode est appelée, l’instance de workflow est arrêtée immédiatement quand une connexion SQL Server n’est pas disponible.  
  
 Pour plus d’informations sur le comportement de la **WorkflowCommitBatchService** de classe dans un environnement à haute disponibilité, consultez la section « Reliability and High Availability » dans « Introduction à hébergement Windows Workflow Foundation » à [http://go.microsoft.com/fwlink/?LinkId=88068](http://go.microsoft.com/fwlink/?LinkId=88068).  
  
## <a name="bam-wcf-interceptor"></a>Intercepteur WCF BAM  
 Dans un environnement à haute disponibilité, l'intercepteur WCF BAM ne tente pas à nouveau de récupérer le fichier de configuration de l'intercepteur si un problème de connexion SQL Server survient lors d'un basculement SQL Server. Vous devez donc personnaliser le code WCF pour compenser l'échec ou utiliser la fiabilité de la messagerie pour renvoyer les messages.  
  
## <a name="see-also"></a>Voir aussi  
 [Intercepteur WF BAM](../core/bam-wf-interceptor.md)