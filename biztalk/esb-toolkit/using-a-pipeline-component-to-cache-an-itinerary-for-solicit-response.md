---
title: "À l’aide d’un composant de Pipeline pour mettre en Cache un itinéraire de sollicitation-réponse | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: add07ebf-785c-4c53-be69-efd40677a758
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 64b6822a4f4ca70e88ee86277e00645982595b47
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-a-pipeline-component-to-cache-an-itinerary-for-solicit-response"></a>À l’aide d’un composant de Pipeline pour mettre en Cache un itinéraire de sollicitation-réponse
Messages envoyés via un [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] rampe d’itinéraire peut passer par un itinéraire à sens unique ou d’une feuille de route bidirectionnelle (requête-réponse). Pour prendre en charge les itinéraires de requête-réponse, le mécanisme d’itinéraire doit fournir la mise en cache pour les ports d’envoi BizTalk dynamiques avec sollicitation-réponse.  
  
 Le composant de pipeline ESB itinéraire Cache place l’itinéraire stocké dans le contexte du message sortant dans le cache et l’attache au message de réponse ; elle est retournée par le port d’envoi à l’aide de la clé de la mise en cache peut être configurée. Ainsi, le service d’itinéraire traiter et d’exécuter les services suivants définis après le service en cours dans la feuille de route.  
  
 Par défaut, le composant de pipeline ESB itinéraire Cache se trouve dans le pipeline ItineraryReceiveSend BizTalk, comme illustré dans la Figure 1. Ce pipeline doit être utilisé uniquement en tant que le pipeline de réception pour un port d’envoi de sollicitation-réponse.  
  
 ![Cache du composant de pipeline](../esb-toolkit/media/ch4-pipelinecomponentcache.gif "PipelineComponentCache de chapitre 4")  
  
 **Figure 1**  
  
 **Le composant de Pipeline de Cache d’itinéraire ESB**  
  
 Utilisez le composant de Pipeline de Cache d’itinéraire ESB dans BizTalk pipeline de réception pour un port d’envoi de sollicitation-réponse.