---
title: "Création de gestionnaires d’exceptions personnalisé | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 401aec8d-d9ca-4a88-9e5b-d3ab605dc0a1
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 91f725084c838d026f9028f0ac2e684ec2d727c6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="creating-custom-exception-handlers"></a>Création de gestionnaires d’exceptions personnalisées
Pour une application détecter et réagir aux exceptions, les développeurs doivent fournir un gestionnaire d’exceptions. Ce gestionnaire d’exceptions peut s’abonner à un seul type de message d’exception ou messages d’exception générés à partir de tout ou partie d’un système ou une application. Par exemple, vous pouvez avoir besoin seulement un gestionnaire unique pour tous les messages à partir d’un système particulier (par exemple, toutes les exceptions qui se produisent dans le système de paie), ou vous pouvez avoir besoin à la place de gestionnaires ciblés pour les erreurs spécifiques (par exemple, pour détecter si la vérification du processus d’impression échoue).  
  
 Pour vous abonner à un type d’exception spécifique, utilisez une orchestration qui a un filtre sur la forme réception activation, comme indiqué dans l’exemple suivant.  
  
```csharp  
Microsoft.Practices.ESB.ExceptionHandling.Schemas.Property.FaultCode == "1000";  
```  
  
 Vous avez peut-être également une condition de filtre sur un port d’envoi qui envoie un message au système de fichiers ou par courrier électronique si le message répond à une condition de filtre spécifique.  
  
## <a name="sample-exception-handling-projects"></a>Exemples de projets de la gestion des exceptions  
 La [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] inclut plusieurs exemples d’applications BizTalk qui illustrent la gestion des exceptions. Ces exemples sont accessibles dans le dossier de gestion des \Source\Samples\Exception.  
  
 Il existe quatre projets de BizTalk, situés dans la solution GlobalBank.ESB.Samples.ExceptionHandling, qui montrent comment utiliser le mécanisme d’ESB Échec de l’Orchestration Exception routage. Ces projets sont préconfigurés pour déployer dans l’application BizTalk de GlobalBank.ESB. Les projets sont les suivants :  
  
-   **ESB. ExceptionHandling.Schemas.** Ce projet contient les schémas utilisés pour les exemples d’orchestrations.  
  
-   **ESB. ExceptionHandling.Pipelines.** Ce projet contient le pipeline d’envoi configuré avec le processeur de l’exception, utilisé dans un port d’envoi qui s’abonne à toutes les exceptions. Cela inclut les exceptions générées par BizTalk et les exceptions générées par l’infrastructure de gestion d’Exception.  
  
-   **ESB. ExceptionHandling.Processes.** Ce projet contient l’orchestration EAIProcess.odx, ce qui simule une exception par la tentative de division par zéro et appelle le **CreateFaultMessage** et **AddMessage** méthodes à générer adéquat message d’erreur, comme indiqué dans la Figure 1.  
  
     ![Orchestration traite exemple](../esb-toolkit/media/ch4-orchestrationprocessessample.gif "OrchestrationProcessesSample de chapitre 4")  
  
     **Figure 1**  
  
 **L’orchestration EAIProcess.odx dans l’exemple de projet de processus**  
  
-   **ESB. ExceptionHandling.Handlers.** Ce projet contient l’orchestration EAIGenericHandler.odx, qui appelle la **GetMessages** (méthode) et effectue une itération dans les **MessageCollection** à l’aide de la **MoveNext**(méthode), comme indiqué dans la Figure 2.  
  
 ![Exemples de gestionnaires d’orchestration générique](../esb-toolkit/media/ch4-orchestrationhandlerssamplegeneric.gif "OrchestrationHandlersSampleGeneric de chapitre 4")  
  
 **Figure 2**  
  
 **L’orchestration EAIGenericHandler.odx dans l’exemple de projet de gestionnaires**  
  
 L’architecture ESB. ExceptionHandling.Handlers projet contient également l’orchestration EAIProcessHandler.odx, qui appelle la **GetMessage** et **GetException** méthodes, comme indiqué dans la Figure 3.  
  
 ![Exemples de gestionnaires d’orchestration processus](../esb-toolkit/media/ch4-orchestrationhandlerssampleprocess.gif "OrchestrationHandlersSampleProcess de chapitre 4")  
  
 **Figure 3**  
  
 **L’orchestration EAIProcessHandler.odx dans l’exemple de projet de gestionnaires**