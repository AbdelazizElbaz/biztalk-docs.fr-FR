---
title: "Identification de perte des données de suivi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data loss, HAT
- reporting tools
- Orchestration Debugger
- Tracking database, data loss
- HAT, data loss
- HAT, Operation View tool
- HAT, reporting tools
- Operation View tool, MessageBox database
- MessageBox database, Operation View tool
- Operation View tool, data loss
ms.assetid: 1ac13e2c-cd5e-437e-b924-d4547931874e
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c2d7a61d974a51e3a811a8cce84a1e22c24a5e84
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="identifying-lost-tracking-data"></a><span data-ttu-id="a0031-102">Identification des données de suivi perdues</span><span class="sxs-lookup"><span data-stu-id="a0031-102">Identifying Lost Tracking Data</span></span>
<span data-ttu-id="a0031-103">La console Administration de BizTalk Server permet d'identifier les données de suivi perdues à la suite d'une défaillance matérielle.</span><span class="sxs-lookup"><span data-stu-id="a0031-103">You can use the BizTalk Server Administration console to help identify which tracking data has been lost as a result of a hardware failure.</span></span> <span data-ttu-id="a0031-104">Elle peut être utilisée tant pour les données actives que pour les données archivées.</span><span class="sxs-lookup"><span data-stu-id="a0031-104">You can use the BizTalk Server Administration console for live or archived data.</span></span>  
  
 <span data-ttu-id="a0031-105">Vous pouvez utiliser la console Administration de BizTalk Server pour déterminer les services qui étaient actives au moment de que la MessageBox a été récupérée.</span><span class="sxs-lookup"><span data-stu-id="a0031-105">You can use the BizTalk Server Administration console to determine which services were active at the time the MessageBox was recovered.</span></span> <span data-ttu-id="a0031-106">En raison de l'écart existant entre l'heure de la défaillance matérielle et l'heure de récupération de la base de données, vous ne pourrez peut-être pas déterminer l'état de certaines transactions.</span><span class="sxs-lookup"><span data-stu-id="a0031-106">Because there is a gap between the time that the database was recovered and the time of the hardware failure, you may not be able to determine the state of some of the transactions.</span></span>  
  
 <span data-ttu-id="a0031-107">Les données de suivi permettent d'identifier les instances de service terminées et celles démarrées après le point de récupération, comme suit :</span><span class="sxs-lookup"><span data-stu-id="a0031-107">You can use tracking data to identify which service instances completed and started after the point of recovery, as follows:</span></span>  
  
-   <span data-ttu-id="a0031-108">Recherchez les instances terminées et démarrées depuis la dernière sauvegarde de la base de données.</span><span class="sxs-lookup"><span data-stu-id="a0031-108">Look for which instances completed or started since the last time you backed up the database.</span></span>  
  
-   <span data-ttu-id="a0031-109">Si les données de la base de données des suivis BizTalk (BizTalkDTADb) indiquent qu'un message démarré n'est pas terminé, et que celui-ci ne figure pas dans la base de données, cela signifie que ce message a été envoyé après la dernière sauvegarde.</span><span class="sxs-lookup"><span data-stu-id="a0031-109">If data in the BizTalk Tracking (BizTalkDTADb) database indicates that the message started but did not complete, and the message is not in the database, then that message was sent after the last backup.</span></span>  
  
 <span data-ttu-id="a0031-110">Le suivi permet de répertorier les services terminés et les services démarrés.</span><span class="sxs-lookup"><span data-stu-id="a0031-110">Tracking can report on any service that completed, and it can indicate that a service started.</span></span> <span data-ttu-id="a0031-111">Les données de suivi sont mises en lot dans la base de données MessageBox avant d'être déplacées vers la base de données des suivis BizTalk.</span><span class="sxs-lookup"><span data-stu-id="a0031-111">Tracking data is first staged to the MessageBox and then moved to the BizTalk Tracking database.</span></span> <span data-ttu-id="a0031-112">Les données mises en lot sont susceptibles d'être perdues dans l'accumulation des messages du service de bus d'événements BAM.</span><span class="sxs-lookup"><span data-stu-id="a0031-112">The data that was staged may have been lost to the backlog of the BAM Event Bus service.</span></span>  
  
 <span data-ttu-id="a0031-113">Si toutes les bases de données doivent être restaurées au niveau de la même marque pour des raisons opérationnelles, vous pouvez utiliser une base de données des suivis BizTalk (non perdue) en mode Archive pour afficher les événements postérieurs à la marque.</span><span class="sxs-lookup"><span data-stu-id="a0031-113">While all databases need to be restored to the same mark for operational reasons, you can use a BizTalk Tracking database (that was not lost) in Archive mode to see what happened after the mark.</span></span>  
  
 <span data-ttu-id="a0031-114">Si le suivi affiche une instance de service comme terminée, vous pouvez mettre fin à cette instance.</span><span class="sxs-lookup"><span data-stu-id="a0031-114">If tracking shows a service instance as having completed, you can terminate that instance.</span></span> <span data-ttu-id="a0031-115">Le suivi peut également afficher les instances démarrées après le point de récupération.</span><span class="sxs-lookup"><span data-stu-id="a0031-115">It may show instances that started after the point of recovery.</span></span> <span data-ttu-id="a0031-116">Dans ce cas, vous devez compenser chaque action effectuée par ces instances, puis renvoyer leurs messages d'activation initiaux.</span><span class="sxs-lookup"><span data-stu-id="a0031-116">If so, you will need to compensate for any actions these instances took and then resubmit their initial activation messages.</span></span>  
  
 <span data-ttu-id="a0031-117">Utilisez le débogueur de l'orchestration pour afficher les dernières formes exécutées, puis le flux de messages pour identifier les messages qui auraient dû être envoyés ou reçus.</span><span class="sxs-lookup"><span data-stu-id="a0031-117">You can use the Orchestration Debugger to see the last shapes that executed, and then use Message Flow to see what message should have been sent or received.</span></span>  
  
 <span data-ttu-id="a0031-118">En cas de perte de la base de données des suivis BizTalk, vous devez utiliser les mécanismes de création de rapports des systèmes externes pour découvrir les événements survenus après le point de récupération.</span><span class="sxs-lookup"><span data-stu-id="a0031-118">If the BizTalk Tracking database was lost, all discovery of what happened past the point of recovery will need to be done by using the external systems reporting mechanisms.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0031-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a0031-119">See Also</span></span>  
 [<span data-ttu-id="a0031-120">Résolution de la perte de données</span><span class="sxs-lookup"><span data-stu-id="a0031-120">Resolving Data Loss</span></span>](../core/resolving-data-loss.md)