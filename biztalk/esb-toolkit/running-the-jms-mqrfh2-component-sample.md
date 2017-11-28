---
title: "Exécution de l’exemple de composant JMS MQRFH2 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 44f4b48c-398a-4ec1-a033-1fc4a76a305c
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4fcea4bca324f73ee37b63e78673140eae250692
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="running-the-jms-mqrfh2-component-sample"></a><span data-ttu-id="2ee77-102">Exécution de l’exemple de composant MQRFH2 JMS</span><span class="sxs-lookup"><span data-stu-id="2ee77-102">Running the JMS MQRFH2 Component Sample</span></span>
<span data-ttu-id="2ee77-103">L’exemple de composant de MQRFH2 JMS se compose de trois parties :</span><span class="sxs-lookup"><span data-stu-id="2ee77-103">The JMS MQRFH2 Component sample consists of three parts:</span></span>  
  
-   <span data-ttu-id="2ee77-104">[Exécution de l’exemple de conservation de l’en-tête JMS MQRFH2](../esb-toolkit/running-the-jms-mqrfh2-header-preservation-sample.md).</span><span class="sxs-lookup"><span data-stu-id="2ee77-104">[Running the JMS MQRFH2 Header Preservation Sample](../esb-toolkit/running-the-jms-mqrfh2-header-preservation-sample.md).</span></span> <span data-ttu-id="2ee77-105">Cette partie illustre la conservation de l’en-tête de haute fidélité comme un message transite d’IBM WebSphere MQ, ESB et Microsoft BizTalk Server et revenir à IBM WebSphere MQ.</span><span class="sxs-lookup"><span data-stu-id="2ee77-105">This part demonstrates full-fidelity header preservation as a message travels from IBM WebSphere MQ, through ESB and Microsoft BizTalk Server, and back to IBM WebSphere MQ.</span></span>  
  
-   <span data-ttu-id="2ee77-106">[L’accès à la propriété en-tête en cours d’exécution à partir d’un exemple d’Orchestration](../esb-toolkit/running-the-header-property-access-from-an-orchestration-sample.md).</span><span class="sxs-lookup"><span data-stu-id="2ee77-106">[Running the Header Property Access from an Orchestration Sample](../esb-toolkit/running-the-header-property-access-from-an-orchestration-sample.md).</span></span> <span data-ttu-id="2ee77-107">Cette partie illustre comment le code au sein d’une orchestration ESB peut accéder aux propriétés d’en-tête MQRFH2.</span><span class="sxs-lookup"><span data-stu-id="2ee77-107">This part demonstrates how code within an ESB orchestration can access MQRFH2 header properties.</span></span> <span data-ttu-id="2ee77-108">Dans ce cas, le code utilise une propriété d’en-tête pour spécifier le nom de file d’attente de destination.</span><span class="sxs-lookup"><span data-stu-id="2ee77-108">In this case, the code uses a header property to specify the destination queue name.</span></span>  
  
-   <span data-ttu-id="2ee77-109">[Exécute le bloc charger l’exemple de routage basé sur le contenu](../esb-toolkit/running-the-bulk-load-content-based-routing-sample.md).</span><span class="sxs-lookup"><span data-stu-id="2ee77-109">[Running the Bulk Load Content-Based Routing Sample](../esb-toolkit/running-the-bulk-load-content-based-routing-sample.md).</span></span> <span data-ttu-id="2ee77-110">Cette partie présente une file d’attente des messages de chargement en masse, et indique comment l’application achemine les messages pour les files d’attente de destination spécifiés en tant que partie du contenu du message.</span><span class="sxs-lookup"><span data-stu-id="2ee77-110">This part demonstrates bulk loading a queue with messages, and it shows how the application routes messages to the destination queues specified as part of the message content.</span></span>