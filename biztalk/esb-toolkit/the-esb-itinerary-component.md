---
title: "Le composant d’itinéraire ESB | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 379edc6a-7d53-4338-87a5-47b5238453a4
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 80aa7c1ef4bc53ad2e2821eaf8dc4184777900a3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-esb-itinerary-component"></a>Le composant d’itinéraire ESB
Le composant de la feuille de route ESB définit les propriétés de contexte à partir de l’en-tête SOAP envoyée avec le message pour un ESB d’itinéraire rampe d’entrée.  
  
## <a name="installation"></a>Installation  
 L’installation du noyau ESB installe automatiquement le **itinéraire** composant de pipeline dans le dossier composants de Pipeline BizTalk Server.  
  
## <a name="how-it-works"></a>Fonctionnement  
 Le composant de la feuille de route ESB est un composant de pipeline Microsoft BizTalk qui peut résider que dans un pipeline de réception. Il promeut les valeurs à partir des en-têtes de message SOAP ou des paramètres de composant dans le contexte du message en tant que propriétés. Vous trouverez un exemple de promouvoir des en-têtes SOAP dans les services Web de rampe d’entrée d’itinéraire fournis avec [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]. Ces services Web exposent des en-têtes SOAP dans le cadre de leur contrat, et les applications clientes doivent définir les en-têtes. Comme le message passe par le composant dans un pipeline de réception, le composant lit les valeurs de l’en-tête SOAP et promeut (écritures) vers les propriétés de contexte de message.  
  
## <a name="using-the-esb-itinerary-component"></a>À l’aide du composant d’itinéraire ESB  
 Vous pouvez ajouter le composant de la feuille de route ESB à un pipeline de réception et ensuite utiliser le pipeline dans un emplacement de réception. Le composant promeut automatiquement les valeurs d’en-tête SOAP ou des paramètres du composant dans les propriétés de contexte du message entrant.  
  
 Pour obtenir un exemple d’utilisation de ce composant, consultez [l’installation et l’exécution de l’exemple de rampe d’entrée d’itinéraire](../esb-toolkit/installing-and-running-the-itinerary-on-ramp-sample.md).