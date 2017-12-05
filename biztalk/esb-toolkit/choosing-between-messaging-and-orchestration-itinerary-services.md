---
title: "Choix entre la messagerie et d’Orchestration d’itinéraire | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 694f929a-c830-4906-8e97-4fbd50e70133
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f98f48cc93e973b7170c854590359029a60ebf57
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="choosing-between-messaging-and-orchestration-itinerary-services"></a>Choix entre la messagerie et d’Orchestration d’itinéraire
Services d’itinéraire peuvent être configuré pour se produire dans le sous-système de messagerie ou le sous-système d’orchestration de BizTalk Server. Ces services de messagerie d’itinéraire ESB sont configurés pour traiter le message et peuvent être exécutées dans un pipeline BizTalk Server (rampe d’entrée ou rampe). Cette option permet aux développeurs de définir exactement où dans le pipeline le service s’exécutera. Naturellement, les services configurés pour le processus dans le sous-système de l’orchestration seront exécutés dans une orchestration BizTalk.  
  
## <a name="esb-itinerary-messaging-services"></a>Services de messagerie d’itinéraire ESB  
 Lorsqu’un message est en cours de traitement dans un pipeline BizTalk Server, à l’aide des services de messagerie d’itinéraire ESB réduit la latence de message. En implémentant des services DOS à DOS dans un seul pipeline, il est possible transformer un message plusieurs fois et acheminer le message à ses points de terminaison avec uniquement une persistance unique pour la base de données de la boîte de Message. En outre, le traitement basé sur la messagerie élimine le coût des ressources supplémentaires de traitement de l’orchestration. En règle générale, le traitement basé sur la messagerie est beaucoup moins de ressources et fournit un traitement plus rapide que le traitement basé sur l’orchestration. Dans les pipelines, le répartiteur de ESB et le désassemblage de répartiteur ESB fournies par les composants de pipeline [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] agissent comme des intercepteurs de messages et d’exécuter les services d’itinéraire basés sur la messagerie, s’il s’agit d’un routage, la transformation ou d’un service personnalisé. Pour plus d’informations sur la configuration de ces composants, consultez [le composant de répartiteur ESB](../esb-toolkit/the-esb-dispatcher-component.md) et [l’ESB répartiteur désassembler composant](../esb-toolkit/the-esb-dispatcher-disassemble-component.md).  
  
## <a name="esb-itinerary-orchestration-services"></a>Services d’Orchestration d’itinéraire ESB  
 Si le routage dynamique doit avoir lieu entre ou après le processus d’orchestration, utilisez le traitement basé sur l’orchestration pour le service d’itinéraire. Par défaut, les services d’orchestration le message sous forme de document XML. L’orchestration de routage utilise le Gestionnaire de programme de résolution pour tenter de résoudre les points de terminaison identifiés dans l’itinéraire. Le Gestionnaire d’adaptateur utilise la réponse à partir du Gestionnaire de programme de résolution pour promouvoir les détails du point de terminaison dans le contexte du message et le message est publié dans la base de données de la boîte de Message à l’aide d’un port logique à liaison directe. À ce stade, le routage de BizTalk régulière se produit, et le port d’envoi dynamique est configuré à l’aide des propriétés promues du message.  
  
 L’orchestration incluse itinéraire Service fournit un bon point de départ pour créer des services d’itinéraire personnalisés basé sur l’orchestration. Pour plus d’informations sur la création de services d’itinéraire personnalisées, consultez [modification et l’extension de BizTalk ESB Toolkit](../esb-toolkit/modifying-and-extending-the-biztalk-esb-toolkit.md).