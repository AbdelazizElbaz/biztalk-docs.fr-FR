---
title: "Suivi des événements - Définition | Microsoft Docs"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuring [HAT tracking], events
- DTA_Services audit table [HAT]
- HAT, events
- events, tracking
- tracking, events
- Tracking database, DTA_Services audit table
- events, HAT
ms.assetid: dd211752-d1af-4287-967a-908b8d067ebb
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: faa53881cf42ae2769621e10ce21e1160f9b7be0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="what-is-event-tracking"></a><span data-ttu-id="d4fa4-103">Suivi des événements - Définition</span><span class="sxs-lookup"><span data-stu-id="d4fa4-103">What is Event Tracking?</span></span>
<span data-ttu-id="d4fa4-104">Les données d'événements de messages suivis sont basées sur les événements (par exemple, le démarrage ou l'arrêt d'un service, ou l'envoi ou la réception d'un message).</span><span class="sxs-lookup"><span data-stu-id="d4fa4-104">Tracked message event data is based upon events (for example, when a service begins or ends, or when a message is sent or received).</span></span> <span data-ttu-id="d4fa4-105">Le processus de suivi des événements de message renvoie la liste des événements qui se sont produits, ce qui vous permet de voir tout ce qui s'est passé sur la base des filtres de suivi définis.</span><span class="sxs-lookup"><span data-stu-id="d4fa4-105">The message event tracking process returns a list of the events that have occurred, enabling you to see everything that happened based on the tracking filters you have set.</span></span>  
  
 <span data-ttu-id="d4fa4-106">Vous pouvez suivre le démarrage et l'arrêt des orchestrations et des ports, les heures d'envoi et de réception des messages ou encore l'exécution de chaque forme d'une orchestration.</span><span class="sxs-lookup"><span data-stu-id="d4fa4-106">You can track the start and end of orchestrations and ports, when messages are sent and received, as well as the execution of each shape in an orchestration.</span></span>  
  
 <span data-ttu-id="d4fa4-107">La base de données des suivis BizTalk (BizTalkDTADb) comporte une table d'audit dénommée DTA_Services.</span><span class="sxs-lookup"><span data-stu-id="d4fa4-107">The BizTalk Tracking (BizTalkDTADb) database contains a DTA_Services audit table.</span></span> <span data-ttu-id="d4fa4-108">Celle-ci contient l'historique de tous les services déployés (pipelines, transports et orchestrations).</span><span class="sxs-lookup"><span data-stu-id="d4fa4-108">This table contains history of all deployed services—pipelines, transports, and orchestrations.</span></span> <span data-ttu-id="d4fa4-109">Elle ne conserve pas de trace des annulations de déploiement.</span><span class="sxs-lookup"><span data-stu-id="d4fa4-109">It does not keep track of undeployments.</span></span>  
  
 <span data-ttu-id="d4fa4-110">Vous pouvez suivre le contenu et les propriétés promues d'un message.</span><span class="sxs-lookup"><span data-stu-id="d4fa4-110">You can track the contents of a message as well as the promoted properties of a message.</span></span> <span data-ttu-id="d4fa4-111">Suivi des événements de message présente ces actions comme **le corps du Message** suivi et **propriété de Message** de suivi.</span><span class="sxs-lookup"><span data-stu-id="d4fa4-111">Tracking message events defines these actions as **Message Body** tracking and **Message Property** tracking.</span></span> <span data-ttu-id="d4fa4-112">Il affiche les enveloppes, mais ne vous permet pas de suivre les propriétés des messages à partir de celles-ci.</span><span class="sxs-lookup"><span data-stu-id="d4fa4-112">Although envelopes appear in the message event tracking output, you cannot track message properties from them.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4fa4-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d4fa4-113">See Also</span></span>  
 [<span data-ttu-id="d4fa4-114">Configuration du suivi à l’aide de la Console Administration de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="d4fa4-114">Configuring Tracking Using the BizTalk Server Administration Console</span></span>](http://msdn.microsoft.com/en-us/49b7f9d3-60b5-41bd-ba8b-029253926bef)