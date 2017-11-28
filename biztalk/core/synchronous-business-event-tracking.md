---
title: "Suivi des événements commerciaux synchrone | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- performance, BAM
- events, tracking [BAM]
- BAM, event tracking
- BAM, performance
ms.assetid: 302c7918-bc62-46f1-a949-fbf94a7073e3
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 84223714e2e04cec6c079862693a09786cb19a7f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="synchronous-business-event-tracking"></a><span data-ttu-id="87b2b-102">Suivi synchrone des événements commerciaux</span><span class="sxs-lookup"><span data-stu-id="87b2b-102">Synchronous Business Event Tracking</span></span>
<span data-ttu-id="87b2b-103">La façon la plus simple d'envoyer des données d'événements à BAM consiste à utiliser une instance de la classe DirectEventStream.</span><span class="sxs-lookup"><span data-stu-id="87b2b-103">The simplest way to send event data to BAM is to use an instance of the class DirectEventStream.</span></span> <span data-ttu-id="87b2b-104">Cette classe enregistre les données d'événement directement dans la Base de données d'importation principale BAM dans le contexte de la transaction en cours de l'application (le cas échéant).</span><span class="sxs-lookup"><span data-stu-id="87b2b-104">This class saves the event data directly into the BAM Primary Import Database in the context of the current transaction of the application (if present).</span></span>  
  
 <span data-ttu-id="87b2b-105">Si une erreur se produit pendant cette opération, l'appel de méthode utilisé renvoie une exception dans l'application appelante.</span><span class="sxs-lookup"><span data-stu-id="87b2b-105">If any error happens during this operation, the method call will throw an exception back in the calling application.</span></span> <span data-ttu-id="87b2b-106">C'est le cas lorsque le nom d'un élément traité par l'activité de mise à jour ne correspond pas à la définition de l'activité BAM ou si vous n'avez pas encore déployé cette définition.</span><span class="sxs-lookup"><span data-stu-id="87b2b-106">This will happen for example if the name of an item passed in UpdateActivity mismatches the BAM Activity Definition, or you did not deploy the BAM Definition yet.</span></span> <span data-ttu-id="87b2b-107">Cela permet à l'application appelante d'intercepter et de résoudre n'importe quelle erreur se produisant lors de l'enregistrement des données de l'analyse BAM. La gestion ultérieure de ces données s'en trouve facilitée.</span><span class="sxs-lookup"><span data-stu-id="87b2b-107">This allows the calling application to catch and recover from any errors when saving the BAM data, which results in much easier management later.</span></span>  
  
 <span data-ttu-id="87b2b-108">L'enregistrement des données de manière synchrone peut avoir un impact sur les performances du système, car l'application appelante doit attendre que le composant d'analyse BAM ait exécuté toutes les procédures et tous les déclencheurs stockés.</span><span class="sxs-lookup"><span data-stu-id="87b2b-108">Saving the data synchronously might have a performance impact, because the calling application has to wait until BAM executes all stored procedures and triggers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87b2b-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="87b2b-109">See Also</span></span>  
 [<span data-ttu-id="87b2b-110">Suivi des événements commerciaux asynchrone</span><span class="sxs-lookup"><span data-stu-id="87b2b-110">Asynchronous Business Event Tracking</span></span>](../core/asynchronous-business-event-tracking.md)