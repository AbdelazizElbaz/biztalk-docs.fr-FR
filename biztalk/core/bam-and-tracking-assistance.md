---
title: "Analyse BAM et l’Assistance de suivi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- HAT, BAM integration
- BAM, HAT integration
ms.assetid: b224cd7d-78db-432a-821a-728eabbf6403
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7b915d21111383ca32f2732f1a1bb86bd2c6c8f3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="bam-and-tracking-assistance"></a><span data-ttu-id="ce396-102">Assistance en matière de suivi et d'analyse BAM</span><span class="sxs-lookup"><span data-stu-id="ce396-102">BAM and Tracking Assistance</span></span>
<span data-ttu-id="ce396-103">Vous pouvez demander une assistance via le portail BAM en cliquant sur le **Assistance** bouton sur la page État de l’activité.</span><span class="sxs-lookup"><span data-stu-id="ce396-103">You can request assistance through the BAM portal by clicking the **Assistance** button on the Activity Status page.</span></span>  
  
 <span data-ttu-id="ce396-104">La requête d'assistance est ensuite placée dans le journal des événements de l'application.</span><span class="sxs-lookup"><span data-stu-id="ce396-104">The assistance request is placed in the Application Event log.</span></span> <span data-ttu-id="ce396-105">La source des requêtes est le service Web BAM et l'ID de l'événement est 1000.</span><span class="sxs-lookup"><span data-stu-id="ce396-105">The source for the requests is the BAM Web service and the Event ID is 1000.</span></span>  
  
 <span data-ttu-id="ce396-106">Le corps du message figure dans le champ Description et contient l'objet de la requête, le texte de description du problème, l'ID d'instance du service BizTalk, l'ID du message, le serveur de la base de données de gestion BizTalk et le nom de la base de données de gestion BizTalk.</span><span class="sxs-lookup"><span data-stu-id="ce396-106">The message body is in the Description field and contains the subject of the request, the text of the problem description, the BizTalk service instance ID, the message ID, the BizTalk Management database server, and the BizTalk Management Database name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce396-107">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ce396-107">See Also</span></span>  
 <span data-ttu-id="ce396-108">[Analyse de BizTalk Server](../core/monitoring-biztalk-server.md) </span><span class="sxs-lookup"><span data-stu-id="ce396-108">[Monitoring BizTalk Server](../core/monitoring-biztalk-server.md) </span></span>  
 [<span data-ttu-id="ce396-109">Demande d’Assistance</span><span class="sxs-lookup"><span data-stu-id="ce396-109">Request Assistance</span></span>](../core/request-assistance.md)