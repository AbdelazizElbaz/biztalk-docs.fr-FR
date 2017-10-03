---
title: Classes EventStream | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a3e7a6b3-69cc-4312-9074-acccd1175d37
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 89eafdced54927007bcc8dfc02e4834641e2ae2f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="eventstream-classes"></a>Classes EventStream
Les API EventStream de l'analyse BAM résident dans l'espace de noms Microsoft.BizTalk.BAM.EventObservation. Pour coder ces API, vous devez installer les DLL suivantes sur votre ordinateur de développement :  
  
-   Microsoft.BizTalk.BAM.EventObservation.dll  
  
-   Microsoft.Biztalk.BAM.Xlangs.dll : Cette DLL est requise lors du codage pour les flux d’événements d’Orchestration.  
  
-   Microsoft.BizTalk.Pipeline.dll : Cette DLL est requise lors de l’utilisation de contextes de pipeline de codage pour le flux d’événements de messagerie.  
  
 Ajoutez la DLL à votre référence de projet et incluez l'espace de noms dans votre code à l'aide de l'instruction using suivante :  
  
```  
using Microsoft.BizTalk.Bam.EventObservation;  
```  
  
 **Classes**  
  
|Nom| Description|  
|----------|-----------------|  
|DirectEventStream (DES)|Synchrone, pas de latence|  
|BufferedEventStream (BES)|Asynchrone, débit élevé, certaine latence|  
|OrchestrationEventStream (OES)|Asynchrone, participe aux transactions d'orchestration BizTalk|  
|Interface IPipelineContext|Asynchrone, participe aux transactions de pipeline BizTalk Server. Permet de créer des flux d'événements de messagerie (MES).|  
  
 Vous devez choisir une API en fonction des facteurs suivants :  
  
-   Si votre préoccupation est la latence, choisissez DES, les données étant conservées de manière synchrone dans la base de données d'importation principale BAM. À l'exception de DES, toutes les autres classes EventStream sont asynchrones et ont une latence. Les données sont d'abord conservées dans MessageBox, puis traitées par TDDS qui les déplace vers la base de données BAMPrimaryImport.  
  
-   Si votre préoccupation est la performance et la capacité d'insertion des événements, choisissez une API asynchrone.  
  
-   Si vous écrivez une application qui s'exécute sur un ordinateur sur lequel BizTalk Server n'est pas installé, utilisez DES et BES. (En d'autres termes, ces API peuvent être utilisées dans des applications non-BizTalk.)  
  
-   Si votre application s'exécute sur un ordinateur sur lequel BizTalk Server est installé, utilisez MES et OES. (Ces API sont uniquement disponibles à partir des applications BizTalk.)  
  
    -   Si vous souhaitez que la persistance d'événement BAM soit synchronisée avec la transaction de pipeline, utilisez un flux d'événements de messagerie.  
  
    -   OES est l'équivalent de MES, mais pour les orchestrations BizTalk.  
  
 Il existe des scénarios dans lesquels vous pouvez combiner plusieurs types EventStream. Par exemple, dans un traitement de pipeline, vous pouvez capturer les données spécifiques de l'analyse BAM que le pipeline restaure ou non sa transaction. Plus précisément, vous pouvez capturer des données sur le nombre de messages dont le traitement à échoué ou le nombre de tentatives lors du traitement de pipeline. Pour capturer les données dans ce cas précis, vous devez utiliser BES.  
  
 Tous les flux d'événements asynchrones (BES, MES et OES) conservent d'abord les données dans la base de données MessageBox BizTalk. Régulièrement, les données sont traitées et rendues persistantes dans la base de données Importation principale BAM par le service TDDS (Tracking Data Decode Service).  
  
> [!NOTE]
>  Pour s'assurer que les appels EventStream ne créent pas de goulot d'étranglement à partir d'une application BizTalk, nous vous recommandons d'utiliser des API asynchrones.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [OrchestrationEventStream](../core/orchestrationeventstream.md)  
  
-   [Flux d’événements de messagerie](../core/messaging-event-streams.md)