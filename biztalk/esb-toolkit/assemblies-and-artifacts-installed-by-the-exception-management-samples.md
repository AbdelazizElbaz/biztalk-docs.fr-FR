---
title: "Assemblys et des artefacts installés par les exemples de gestion d’Exception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: af580992-73d4-4b16-a1cc-fa819b441fca
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 65bcb2681cceb450995b18b7dc00d3d8f5a44d30
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="assemblies-and-artifacts-installed-by-the-exception-management-samples"></a>Assemblys et des artefacts installés par les exemples de gestion des exceptions
Le tableau suivant répertorie les assemblys et autres artefacts installés pour l’exemple de gestion des exceptions ESB.  
  
|Emplacement|Catégorie|Nom et la version du composant|  
|--------------|--------------|---------------------------------------|  
|Application BizTalk GlobalBank.ESB|Orchestrations|GlobalBank.ESB.ExceptionHandling.Processes.EAIProcess|  
|||GlobalBank.ESB.ExceptionHandling.Handlers.EAIGenericHandler|  
|||GlobalBank.ESB.ExceptionHandling.Handlers.EAIProcessHandler|  
|Application BizTalk GlobalBank.ESB|Ports d'envoi|EAIProcessHandler.RepairSubmit|  
|||EAIGenericHandler.PostTmpMsg|  
|||EAIProcess.PostApproval|  
|||EAIProcessHandler.PostDecline|  
|||TOUS LES. Exceptions_FILE (fait référence le pipeline GlobalFaultProcessor)|  
|Application BizTalk GlobalBank.ESB|Ports de réception|EAIProcess.RequestPort|  
|Application BizTalk GlobalBank.ESB|Emplacements de réception|EAIProcess.RequestPort_FILE|  
|||EAIProcess.ReSubmit_HTTP|  
|Application BizTalk GlobalBank.ESB|Schémas|GlobalBank.ESB.ExceptionHandling.Schemas.System_Properties Version 2.0.0.0|  
|||GlobalBank.ESB.ExceptionHandling.Schemas.Request Version 2.0.0.0|  
|||GlobalBank.ESB.ExceptionHandling.Schemas.RequestDenied Version 2.0.0.0|  
|Application BizTalk GlobalBank.ESB|Pipelines|GlobalBank.ESB.ExceptionHandling.Pipelines.GlobalFaultProcessor Version 2.0.0.0|  
|Application BizTalk GlobalBank.ESB|Ressources|GlobalBank.ESB.ExceptionHandling.Handlers Version 2.0.0.0|  
|||GlobalBank.ESB.ExceptionHandling.Processes Version 2.0.0.0|  
|||GlobalBank.ESB.ExceptionHandling.Schemas Version 2.0.0.0|  
|||GlobalBank.ESB.ExceptionHandling.Pipelines Version 2.0.0.0|  
|Application BizTalk GlobalBank.ESB|Stratégies||  
|Application BizTalk GlobalBank.ESB|Cartes|GlobalBank.ESB.ExceptionHandling.Schemas.MapToReqDenied Version 2.0.0.0|  
|Cache d’assembly global|Assemblys|GlobalBank.ESB.ExceptionHandling.Handlers Version 2.0.0.0|  
|||GlobalBank.ESB.ExceptionHandling.Processes Version 2.0.0.0|  
|||GlobalBank.ESB.ExceptionHandling.Schemas Version 2.0.0.0|  
|||GlobalBank.ESB.ExceptionHandling.Pipelines Version 2.0.0.0|  
|%Program Files%\\[!INCLUDE[prague](../includes/prague-md.md)]\Pipeline composants|Composants de pipeline||