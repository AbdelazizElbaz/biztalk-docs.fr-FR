---
title: "Conserver les en-têtes JMS lors du routage via une Orchestration | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d9a59ff3-0cbf-499f-92b2-cf5b808d8b3f
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 362f41919a050b08bdba9c70c7771698ab71ce33
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="preserving-jms-headers-when-routing-through-an-orchestration"></a><span data-ttu-id="ba575-102">Préservation des en-têtes JMS lors du routage via une Orchestration</span><span class="sxs-lookup"><span data-stu-id="ba575-102">Preserving JMS Headers When Routing Through an Orchestration</span></span>
<span data-ttu-id="ba575-103">Dans ce cas de figure, les composants fournis avec [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] extraire les en-têtes de Message Service JMS (Java) à partir d’un message entrant et les reconstruit ensuite dans le message sortant.</span><span class="sxs-lookup"><span data-stu-id="ba575-103">In this use case, components provided with [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] extract Java Message Service (JMS) headers from an incoming message and then reconstructs them in the outgoing message.</span></span> <span data-ttu-id="ba575-104">Cela montre conservation des en-tête de message JMS et l’accès au contexte d’en-tête à partir d’à l’intérieur d’une orchestration, comme illustré dans la Figure 1.</span><span class="sxs-lookup"><span data-stu-id="ba575-104">This demonstrates JMS message header preservation and access to header context from inside an orchestration, as illustrated in Figure 1.</span></span>  
  
 <span data-ttu-id="ba575-105">![Conservation de JMS](../esb-toolkit/media/ch3-preservingjms.gif "Ch3-PreservingJMS")</span><span class="sxs-lookup"><span data-stu-id="ba575-105">![Preserving JMS](../esb-toolkit/media/ch3-preservingjms.gif "Ch3-PreservingJMS")</span></span>  
  
 <span data-ttu-id="ba575-106">**Figure 1**</span><span class="sxs-lookup"><span data-stu-id="ba575-106">**Figure 1**</span></span>  
  
 <span data-ttu-id="ba575-107">**Conservation des informations d’en-tête JMS tout au long d’une orchestration ESB et traitement**</span><span class="sxs-lookup"><span data-stu-id="ba575-107">**Preserving JMS header information throughout an ESB orchestration and processing**</span></span>  
  
 <span data-ttu-id="ba575-108">L’exemple de composant de MQRFH2 JMS fourni avec le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] illustre ce cas de figure et se compose de trois éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="ba575-108">The JMS MQRFH2 Component sample included with the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] demonstrates this use case and consists of the following three parts:</span></span>  
  
-   <span data-ttu-id="ba575-109">Partie 1 illustre la conservation de l’en-tête de haute fidélité comme un message transite d’IBM WebSphere MQ, ESB et BizTalk Server et revenir à IBM WebSphere MQ.</span><span class="sxs-lookup"><span data-stu-id="ba575-109">Part 1 demonstrates full-fidelity header preservation as a message travels from IBM WebSphere MQ, through ESB and BizTalk Server, and back to IBM WebSphere MQ.</span></span>  
  
-   <span data-ttu-id="ba575-110">Partie 2 illustre comment le code dans une orchestration ESB peut accéder aux propriétés d’en-tête MQRFH2.</span><span class="sxs-lookup"><span data-stu-id="ba575-110">Part 2 demonstrates how code in an ESB orchestration can access MQRFH2 header properties.</span></span> <span data-ttu-id="ba575-111">Dans ce cas, le code modifie une propriété d’en-tête JMS pour spécifier le nom de file d’attente de destination.</span><span class="sxs-lookup"><span data-stu-id="ba575-111">In this case, the code modifies a JMS header property to specify the destination queue name.</span></span>  
  
-   <span data-ttu-id="ba575-112">Partie 3 illustre une file d’attente des messages de chargement en masse et montre comment l’application achemine les messages pour les files d’attente de destination spécifiés en tant que partie du contenu du message.</span><span class="sxs-lookup"><span data-stu-id="ba575-112">Part 3 demonstrates bulk loading a queue with messages and shows how the application routes messages to the destination queues specified as part of the message content.</span></span>  
  
 <span data-ttu-id="ba575-113">Pour plus d’informations, consultez [installer et exécuter l’exemple de composant JMS MQRFH2](../esb-toolkit/installing-and-running-the-jms-mqrfh2-component-sample.md).</span><span class="sxs-lookup"><span data-stu-id="ba575-113">For more information, see [Installing and Running the JMS MQRFH2 Component Sample](../esb-toolkit/installing-and-running-the-jms-mqrfh2-component-sample.md).</span></span>