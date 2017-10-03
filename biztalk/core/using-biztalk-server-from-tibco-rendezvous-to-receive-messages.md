---
title: "À l’aide de BizTalk Server à partir de TIBCO Rendezvous pour recevoir des Messages | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, receiving
- receiving messages
- memory use
ms.assetid: 4eee9c3a-2966-4d5f-ba49-201bb488458c
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4ac81f269e19526f5466e8c12115d617b8171da3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-biztalk-server-from-tibco-rendezvous-to-receive-messages"></a><span data-ttu-id="207fe-102">Utilisation de BizTalk Server à partir de TIBCO Rendezvous pour recevoir des messages</span><span class="sxs-lookup"><span data-stu-id="207fe-102">Using BizTalk Server from TIBCO Rendezvous to Receive Messages</span></span>
<span data-ttu-id="207fe-103">L'adaptateur Microsoft BizTalk pour TIBCO Rendezvous distribue des événements à partir d'une file d'attente sur plusieurs threads.</span><span class="sxs-lookup"><span data-stu-id="207fe-103">Microsoft BizTalk Adapter for TIBCO Rendezvous dispatches events from a queue on multiple threads.</span></span> <span data-ttu-id="207fe-104">Un emplacement de réception BizTalk Server est associé à une file d'attente TIBCO Rendezvous et à son pool de threads du répartiteur.</span><span class="sxs-lookup"><span data-stu-id="207fe-104">A BizTalk Server receive location is associated with one TIBCO Rendezvous event queue and its pool of dispatcher threads.</span></span>  
  
## <a name="memory-use-and-errors"></a><span data-ttu-id="207fe-105">Utilisation de la mémoire et erreurs</span><span class="sxs-lookup"><span data-stu-id="207fe-105">Memory Use and Errors</span></span>  
 <span data-ttu-id="207fe-106">L'adaptateur surveille les ressources utilisées lors du traitement d'événements.</span><span class="sxs-lookup"><span data-stu-id="207fe-106">While processing events, the adapter keeps an eye on used resources.</span></span> <span data-ttu-id="207fe-107">Si l'utilisation de la mémoire dépasse la limite supérieure, l'adaptateur arrête la distribution des événements jusqu'à ce que la consommation de mémoire atteigne la limite inférieure.</span><span class="sxs-lookup"><span data-stu-id="207fe-107">If memory use goes above the high-watermark, the adapter stops dispatching events until it reaches the low-watermark memory consumption.</span></span> <span data-ttu-id="207fe-108">Notez que des messages TIBCO Rendezvous non certifiés peuvent ainsi être manqués (un utilisateur de TIBCO RV dispose de 60 secondes pour supprimer des messages dans une file d'attente).</span><span class="sxs-lookup"><span data-stu-id="207fe-108">Note that this might result in TIBCO Rendezvous messages being missed for non certified messages (a TIBCO RV consumer has 60 seconds to remove messages from a queue).</span></span> <span data-ttu-id="207fe-109">Cette perte de données est signalée en tant qu'erreur.</span><span class="sxs-lookup"><span data-stu-id="207fe-109">This data loss is reported as an error.</span></span> <span data-ttu-id="207fe-110">Si l'adaptateur reçoit un message d'avertissement NO_MEMORY en provenance du système TIBCO Rendezvous, cela signifie que des messages ont déjà été perdus.</span><span class="sxs-lookup"><span data-stu-id="207fe-110">If the adapter receives a TIBCO Rendezvous system advisory NO_MEMORY message, messages have already been lost.</span></span>  
  
 <span data-ttu-id="207fe-111">L'adaptateur BizTalk pour TIBCO Rendezvous conserve un état et exécute des tâches de différentes façons en fonction de cet état.</span><span class="sxs-lookup"><span data-stu-id="207fe-111">BizTalk Adapter for TIBCO Rendezvous maintains a state, and it executes tasks differently based on that state.</span></span> <span data-ttu-id="207fe-112">Si le moteur de messagerie BizTalk renvoie une erreur et si l'adaptateur est configuré en tant qu'écouteur certifié, le moteur la signale à TIBCO Rendezvous afin qu'il puisse renvoyer le message.</span><span class="sxs-lookup"><span data-stu-id="207fe-112">If the BizTalk Message Engine reports an error, and the adapter is configured to be a certified listener, it reports the error to TIBCO Rendezvous so that it can resubmit the message.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="207fe-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="207fe-113">See Also</span></span>  
 <span data-ttu-id="207fe-114">[Concepts de TIBCO Rendezvous](../core/tibco-rendezvous-concepts.md) </span><span class="sxs-lookup"><span data-stu-id="207fe-114">[TIBCO Rendezvous Concepts](../core/tibco-rendezvous-concepts.md) </span></span>  
 [<span data-ttu-id="207fe-115">Gestionnaires de réception création TIBCO Rendezvous</span><span class="sxs-lookup"><span data-stu-id="207fe-115">Creating TIBCO Rendezvous Receive Handlers</span></span>](../core/creating-tibco-rendezvous-receive-handlers.md)