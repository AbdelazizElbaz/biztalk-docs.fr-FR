---
title: "Le composant de sélecteur d’itinéraire ESB | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c2cd8a85-e036-4817-9541-3fd720ca04ef
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c83cdd0b2022eb7dc4ad78e5702f5c21e4c4f432
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-esb-itinerary-selector-component"></a>Le composant de sélecteur d’itinéraire ESB
Le composant de sélecteur de feuille de route ESB permet les messages entrants qui n’ont pas l’en-tête SOAP à passer à l’architecture ESB en sélectionnant un itinéraire côté serveur approprié pour le message à l’aide d’un programme de résolution de l’itinéraire. Le composant est également utilisé pour les messages qui utilisent un en-tête SOAP pour définir le nom et la version d’un itinéraire, comme demandé par le client.  
  
## <a name="installation"></a>Installation  
 L’installation du noyau ESB installe automatiquement le **ItinerarySelector** composant dans le dossier composants de Pipeline BizTalk Server.  
  
## <a name="how-it-works"></a>Fonctionnement  
 Le composant de sélecteur de feuille de route ESB est un composant de pipeline Microsoft BizTalk qui peut résider que dans un pipeline de réception. Le composant sélectionne un itinéraire côté serveur pour une utilisation dans le traitement d’un message. Comme le message passe par le composant dans un pipeline de réception, le composant lit sa configuration et utilise le **ResolverConnectionString** propriété pour appeler le programme de résolution approprié pour rechercher la feuille de route appropriée à utiliser lorsque le traitement du message. Le composant de la feuille de route sélecteur effectue ensuite les mêmes étapes que le composant de pipeline de feuille de route pour valider le message et promouvoir les propriétés nécessaires pour garantir que le message continue à l’étape de traitement suivante.  
  
## <a name="using-the-esb-itinerary-selector-component"></a>À l’aide du composant de sélecteur d’itinéraire ESB  
 Vous pouvez ajouter le composant de la feuille de route ESB à un pipeline de réception et ensuite utiliser le pipeline dans un emplacement de réception. Lorsque ce composant est configuré avec la résolution de l’itinéraire statique dans WCF rampe d’entrée, le nom et la version de l’itinéraire demandé par le client (comme représenté dans l’en-tête SOAP) sera récupéré à partir du contexte de message et permet de sélectionner le texte approprié feuille de route.  
  
## <a name="component-properties"></a>Propriétés du composant  
 Le composant de sélecteur de feuille de route ESB expose trois propriétés publiques :  
  
-   **IgnoreErrorKey**. Cette propriété définit que, si une erreur est renvoyée par le programme de résolution, le message doit être traité sans l’itinéraire (lorsque la valeur **True**) ou suspendu.  
  
-   **ItineraryFactKey**. Représente la clé du dictionnaire retournées par le programme de résolution qui contient le code XML de l’itinéraire sélectionné. En règle générale, **Resolver.Itinerary**, sauf si un programme de résolution personnalisé est utilisé.  
  
-   **ResolverConnectionString**. Il s’agit d’une chaîne de connexion de programme de résolution qui contient les paires nom-valeur qui permet de sélectionner un programme de résolution et/ou de la recherche d’un itinéraire.