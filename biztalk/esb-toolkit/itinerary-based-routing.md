---
title: "Le routage basé sur la feuille de route | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 28028721-798c-4302-a532-d863ed8ea88b
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1fbfe8877202a2f691bd30fd2b56fc3032240ee9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="itinerary-based-routing"></a>Le routage basé sur la feuille de route
Une des fonctionnalités principales de la [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] est la fourniture de routage basé sur un itinéraire qui simplifie le développement d’applications de messagerie au niveau de l’entreprise et réduit les coûts de maintenance d’un grand nombre de statique des ports d’envoi et emplacements de réception.  
  
 Un itinéraire se compose de la liste des services à exécuter (ce qui peut contenir le routage, de transformation et de services personnalisés) et les informations de configuration requises pour résoudre les métadonnées nécessaires pour l’exécution de chacun de ces services. Par exemple, une étape de l’itinéraire peut être un service de routage ; les instructions de résolution associées à ce service peuvent demander au service d’effectuer une recherche de Universal Description, Discovery et Integration (UDDI) ou du moteur de règles d’entreprise (BRE) pour plus d’informations sur un point de terminaison cible spécifique à laquelle il achemine le message.  
  
 Itinéraires peuvent être associés à un message entrant comme suit :  
  
-   Le message envoyé par un client ne contient pas toutes les données relatives à l’itinéraire. Le pipeline de réception est résolue, récupère et attache l’itinéraire approprié basé sur le contenu du message ou le contexte.  
  
-   Le message envoyé par un client peut contenir un en-tête SOAP qui définit les données de référence d’itinéraire, qui contient le nom d’itinéraire et de version, ainsi que d’un identificateur unique pour le suivi de l’analyse BAM (Business Activity). Le pipeline de réception évalue ces informations et récupère l’itinéraire approprié à partir de la base de données ESBItineraryDb.  
  
-   Le message envoyé par un client peut avoir un en-tête SOAP d’itinéraire, qui contient l’ensemble du contenu de l’itinéraire. Cette conception n’est pas recommandée et doit être utilisée uniquement pour des tests.  
  
 Une fois un itinéraire est résolu pour un message entrant, le pipeline de réception promeut les données d’itinéraire pour le contexte du message, rendant ainsi les propriétés disponibles pour être accessible par n’importe quel composant de Microsoft BizTalk Server qui s’abonne à ce message. Composants de BizTalk Server peuvent obtenir des détails de l’étape de l’itinéraire, termine le traitement requis et/ou avancer l’itinéraire à l’étape suivante. Cela entraîne le service suivant dans la feuille de route pour traiter le message, en fonction de la publication-abonnement des fonctionnalités de BizTalk Server.  
  
 Pour plus d’informations sur le mécanisme de résolution dynamique ESB, transformations, le traitement d’itinéraire et la création du message, consultez [principaux scénarios et tâches de développement](../esb-toolkit/key-scenarios-and-development-tasks.md).