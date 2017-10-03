---
title: "Présentation des données suivies | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- instances, viewing
- service instances, viewing
- viewing, suspended instances
- messages, viewing
- viewing, service details
- viewing, orchestration details
- viewing, message details
- orchestrations, viewing
- suspended instances
- instances, suspended
ms.assetid: dcc3fbd5-cd2c-4780-a577-0ccd521cf5eb
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ed30934ca154c8b6921682112b12d016c57f92be
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="understanding-tracked-data"></a><span data-ttu-id="84ac1-102">Présentation des données suivies</span><span class="sxs-lookup"><span data-stu-id="84ac1-102">Understanding Tracked Data</span></span>
<span data-ttu-id="84ac1-103">Lors de l'exécution d'une requête de suivi, les informations de suivi sont affichées dans la liste des résultats, au bas de la fenêtre Résultats de la requête.</span><span class="sxs-lookup"><span data-stu-id="84ac1-103">When you run a tracking query, the tracked information appears in the results list at the bottom of the Query Results window.</span></span>  
  
## <a name="viewing-message-details"></a><span data-ttu-id="84ac1-104">Affichage des détails sur le message</span><span class="sxs-lookup"><span data-stu-id="84ac1-104">Viewing message details</span></span>  
 <span data-ttu-id="84ac1-105">Vous pouvez suivre les propriétés de message.</span><span class="sxs-lookup"><span data-stu-id="84ac1-105">You can track message properties.</span></span> <span data-ttu-id="84ac1-106">Vous pouvez également enregistrer les corps des messages suivis sur un fichier et les consulter à l'aide des outils non-Microsoft.</span><span class="sxs-lookup"><span data-stu-id="84ac1-106">You can also save tracked message bodies to a file and view them using non-Microsoft tools.</span></span>  
  
-   <span data-ttu-id="84ac1-107">Vous pouvez cliquer avec le bouton droit sur tout message référencé par une instance de service et sélectionner Détails sur le message.</span><span class="sxs-lookup"><span data-stu-id="84ac1-107">You can right-click any message referenced by a service instance and select Message details.</span></span>  
  
-   <span data-ttu-id="84ac1-108">Si le message est déjà traité mais qu'il a été suivi (vous aviez activé le suivi), vous pouvez l'enregistrer sur votre disque dur et le lire.</span><span class="sxs-lookup"><span data-stu-id="84ac1-108">If the message is already processed but it was tracked—because you had tracking turned on—you can save it to your hard disk and examine it.</span></span>  
  
-   <span data-ttu-id="84ac1-109">Vous pouvez joindre le message à l'instance d'orchestration et utiliser le débogueur de l'orchestration.</span><span class="sxs-lookup"><span data-stu-id="84ac1-109">You can attach to the orchestration instance and use the Orchestration Debugger.</span></span>  
  
## <a name="viewing-service-events"></a><span data-ttu-id="84ac1-110">Affichage des événements du service</span><span class="sxs-lookup"><span data-stu-id="84ac1-110">Viewing service events</span></span>  
 <span data-ttu-id="84ac1-111">Lorsqu’un service interrompu apparaît dans le journal des événements, vous pouvez analyser un service à l’aide de la **flux Message**, **débogueur Orchestration**, **afficher les événements de Message suivis**, **Afficher les Instances de Service Live**, options de la **contexte** menu.</span><span class="sxs-lookup"><span data-stu-id="84ac1-111">When a suspended service appears in the event log, you can investigate a service by using the **Message Flow**, **Orchestration Debugger**, **Show Tracked Message Events**, **Show Live Service Instances**, options from the **Context** menu.</span></span>  
  
## <a name="viewing-orchestration-events"></a><span data-ttu-id="84ac1-112">Affichage des événements d'orchestration</span><span class="sxs-lookup"><span data-stu-id="84ac1-112">Viewing orchestration events</span></span>  
 <span data-ttu-id="84ac1-113">Utilisez le débogueur de l'orchestration pour afficher le chemin emprunté par l'instance d'un message à travers une orchestration.</span><span class="sxs-lookup"><span data-stu-id="84ac1-113">Use the Orchestration Debugger to view the path a message instance has taken through an orchestration.</span></span> <span data-ttu-id="84ac1-114">Pendant votre analyse détaillée, une image de l'orchestration montre la progression du message et vous permet de placer des points d'arrêt dans l'orchestration à des fins de débogage.</span><span class="sxs-lookup"><span data-stu-id="84ac1-114">As you step through, a rendered image of the orchestration shows the progress of the message, and allows you to place breakpoints in the orchestration for debugging purposes.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="84ac1-115">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="84ac1-115">In This Section</span></span>  
  
-   [<span data-ttu-id="84ac1-116">Quel est le suivi des messages ?</span><span class="sxs-lookup"><span data-stu-id="84ac1-116">What is Message Tracking?</span></span>](../core/what-is-message-tracking.md)  
  
-   [<span data-ttu-id="84ac1-117">Quel est le suivi des événements ?</span><span class="sxs-lookup"><span data-stu-id="84ac1-117">What is Event Tracking?</span></span>](../core/what-is-event-tracking.md)