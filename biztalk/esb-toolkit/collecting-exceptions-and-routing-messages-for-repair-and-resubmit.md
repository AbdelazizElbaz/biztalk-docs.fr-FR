---
title: "Collecte des Exceptions et le routage des Messages pour la réparation et soumettez à nouveau | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5a61658a-0bac-4802-b506-02e61a3d2a9b
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8a1d080cc3b87cf371729c51e1b1f26e07ae521e
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="collecting-exceptions-and-routing-messages-for-repair-and-resubmit"></a><span data-ttu-id="26003-102">Collecte des Exceptions et le routage des Messages pour la réparation et soumettez à nouveau</span><span class="sxs-lookup"><span data-stu-id="26003-102">Collecting Exceptions and Routing Messages for Repair and Resubmit</span></span>
<span data-ttu-id="26003-103">Dans ce cas de figure, un gestionnaire d’exceptions personnalisé récupère un message d’erreur reçu via un service Web et l’achemine vers un fichier de disque dans un format compatible avec un modèle InfoPath inclus avec le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)].</span><span class="sxs-lookup"><span data-stu-id="26003-103">In this use case, a custom exception handler picks up a fault message received through a Web service and routes it to a disk file in a format compatible with an InfoPath template included with the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)].</span></span> <span data-ttu-id="26003-104">L’utilisateur peut ouvrir le fichier à l’aide de Microsoft InfoPath, modifier le contenu du message et renvoyer le message pour le traitement, comme illustré dans la Figure 1.</span><span class="sxs-lookup"><span data-stu-id="26003-104">The user can open the file using Microsoft InfoPath, edit the message contents, and resubmit the message for processing, as illustrated in Figure 1.</span></span>  
  
 <span data-ttu-id="26003-105">![Collecte de réparation des Exceptions](../esb-toolkit/media/ch3-collectingexceptionsrepair.gif "Ch3-CollectingExceptionsRepair")</span><span class="sxs-lookup"><span data-stu-id="26003-105">![Collecting Exceptions Repair](../esb-toolkit/media/ch3-collectingexceptionsrepair.gif "Ch3-CollectingExceptionsRepair")</span></span>  
  
 <span data-ttu-id="26003-106">**Figure 1**</span><span class="sxs-lookup"><span data-stu-id="26003-106">**Figure 1**</span></span>  
  
 <span data-ttu-id="26003-107">**Routage d’un message pour la réparation et renvoyés**</span><span class="sxs-lookup"><span data-stu-id="26003-107">**Routing a message for repair and resubmission**</span></span>  
  
 <span data-ttu-id="26003-108">L’exemple de réparation et soumettez à nouveau gestionnaire d’exceptions personnalisé fourni avec le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] illustre ce cas de figure.</span><span class="sxs-lookup"><span data-stu-id="26003-108">The Repair and Resubmit Custom Exception Handler sample included with the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] demonstrates this use case.</span></span> <span data-ttu-id="26003-109">Quand un processus dans une orchestration rencontre une erreur, le Gestionnaire d’exceptions dans cette orchestration génère et publie un message d’erreur ESB.</span><span class="sxs-lookup"><span data-stu-id="26003-109">When a process in an orchestration encounters an error, the exception handler in that orchestration generates and publishes an ESB fault message.</span></span> <span data-ttu-id="26003-110">Ce message d’erreur inclut, dans sa charge utile, les messages (y compris leurs propriétés de contexte qui sont associées à BizTalk Server) qui ont été « en vol » lorsque l’exception s’est produite et l’exception actuelle est interceptée par le moteur d’Orchestration BizTalk.</span><span class="sxs-lookup"><span data-stu-id="26003-110">This fault message includes, in its payload, the messages (including their context properties that are related to BizTalk Server) that were "in flight" when the exception occurred, and the current exception caught by the BizTalk Orchestration engine.</span></span> <span data-ttu-id="26003-111">Après la publication d’un message d’erreur ESB, il est la file d’attente une orchestration d’abonnement (un gestionnaire d’exceptions personnalisé) qui extrait et inspecte les messages en vol et l’objet d’exception système et achemine les messages en cours dans un dossier, à partir de laquelle un utilisateur peut modifier le message à l’aide d’InfoPath et le renvoyer à BizTalk Server pour traitement.</span><span class="sxs-lookup"><span data-stu-id="26003-111">After an ESB fault message is published, it is de-queued to a subscribing orchestration (a custom exception handler) that extracts and inspects the in-flight messages and the system exception object, and routes the in-flight messages to a file folder, from which a user can edit the message using InfoPath and resubmit it to BizTalk Server for processing.</span></span>  
  
 <span data-ttu-id="26003-112">Pour plus d’informations, consultez [en cours d’exécution la réparation et la soumettre à nouveau une Exception personnalisée, exemple de gestionnaire](../esb-toolkit/running-the-repair-and-resubmit-custom-exception-handler-sample.md).</span><span class="sxs-lookup"><span data-stu-id="26003-112">For more information, see [Running the Repair and Resubmit Custom Exception Handler Sample](../esb-toolkit/running-the-repair-and-resubmit-custom-exception-handler-sample.md).</span></span>