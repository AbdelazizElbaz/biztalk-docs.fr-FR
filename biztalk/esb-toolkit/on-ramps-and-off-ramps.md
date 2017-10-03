---
title: "Sur les écarts et écarter | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c0cce5d2-f16f-4bda-94ac-20c4f457cfc7
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a0aafa69315dba07219ad8510c77cdc9de2d4bce
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="on-ramps-and-off-ramps"></a>Sur les écarts et les écarts
Dans un environnement où [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] est déployé, un emplacement de réception BizTalk responsable pour recevoir les messages destinés à l’ESB est appelé un « rampe d’entrée. » Pour configurer un emplacement de réception BizTalk standard pour une architecture ESB rampe d’entrée, associer l’emplacement de réception à l’un des pipelines fournis dans le cadre de la boîte à outils, puis configurer correctement les composants de ce pipeline de déterminer ou de lire la feuille de route pour le message entrant, en fonction de votre scénario.  
  
 Une architecture ESB « rampe » correspond à un port d’envoi dynamique BizTalk. Comme un itinéraire est en cours de traitement, les valeurs sont promues vers les propriétés de contexte du message associé à l’aide du schéma.xsd de système. BizTalk de publication / abonnement utilise mécanisme ces promues pour acheminer un message via un dynamique propriétés port d’envoi (rampe) pour effectuer une remise de messages.  
  
 Le tableau suivant répertorie les sur écarts fournis par le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)].  
  
|Nom|Modèle d'échange de message|**Description**|  
|----------|------------------------------|---------------------|  
|ESB. ItineraryServices|Unidirectionnel|ASMX rampe d’entrée ; attend le contenu d’itinéraire ESB dans l’en-tête SOAP.|  
|ESB. ItineraryServices.Response|Requête-réponse|ASMX rampe d’entrée ; attend le contenu d’itinéraire ESB dans l’en-tête SOAP.|  
|ESB. ItineraryServices.WCF|Unidirectionnel|Windows Communication Foundation (WCF) rampe d’entrée ; attend la référence d’itinéraire d’ESB dans l’en-tête SOAP.|  
|ESB. ItineraryServices.Response.WCF|Requête-réponse|WCF rampe d’entrée ; attend la référence d’itinéraire d’ESB dans l’en-tête SOAP.|  
|ESB. ItineraryServices.Generic.WCF|Unidirectionnel|WCF rampe d’entrée ; attend un message de demande uniquement.|  
|ESB. ItineraryServices.Generic.Response.WCF|Requête-réponse|WCF rampe d’entrée ; attend un message de demande uniquement.|  
  
 [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]sur les écarts qui ne sont pas QU'ASMX doit être configurée pour sélectionner les itinéraires ESB. Pour plus d’informations sur la sélection d’un itinéraire ESB, consultez [à l’aide d’un composant de Pipeline pour sélectionner un itinéraire existant](../esb-toolkit/using-a-pipeline-component-to-select-an-existing-itinerary.md).