---
title: Publication des points de terminaison BizTalk | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c8e8cc81-c6c7-4269-81e3-8725082a0c98
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e33517f1261324ad01eb0d9cad0f51b74c280828
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="publishing-biztalk-endpoints"></a><span data-ttu-id="be770-102">Points de terminaison de publication BizTalk</span><span class="sxs-lookup"><span data-stu-id="be770-102">Publishing BizTalk Endpoints</span></span>
<span data-ttu-id="be770-103">Vous pouvez utiliser le portail de gestion ESB pour créer et publier des entrées dans le serveur Universal Description, Discovery and Integration (UDDI) configuré actuellement.</span><span class="sxs-lookup"><span data-stu-id="be770-103">You can use the ESB Management Portal to create and publish entries into the currently configured Universal Description, Discovery, and Integration (UDDI) server.</span></span>  
  
### <a name="to-publish-a-microsoft-biztalk-server-endpoint-into-the-current-uddi-server"></a><span data-ttu-id="be770-104">Pour publier un point de terminaison de Microsoft BizTalk Server sur le serveur UDDI en cours</span><span class="sxs-lookup"><span data-stu-id="be770-104">To publish a Microsoft BizTalk Server endpoint into the current UDDI server</span></span>  
  
1.  <span data-ttu-id="be770-105">Pointez sur le **Registre** onglet dans le menu principal de portail, puis cliquez sur **nouvelle entrée de Registre** pour ouvrir le [nouvelle Page d’entrée de Registre](../esb-toolkit/new-registry-entry-page.md).</span><span class="sxs-lookup"><span data-stu-id="be770-105">Point to the **Registry** tab on the portal main menu, and then click **New Registry Entry** to open the [New Registry Entry Page](../esb-toolkit/new-registry-entry-page.md).</span></span>  
  
2.  <span data-ttu-id="be770-106">Pour filtrer sur le type de point de terminaison, l’état et l’application où se trouve le point de terminaison, utilisez les listes déroulantes dans la page.</span><span class="sxs-lookup"><span data-stu-id="be770-106">Use the drop-down lists on the page to filter on the endpoint type, the status, and the application where the endpoint resides.</span></span>  
  
3.  <span data-ttu-id="be770-107">Cliquez sur l’icône de flèche en regard du point de terminaison que vous voulez publier pour créer une demande d’inscription UDDI.</span><span class="sxs-lookup"><span data-stu-id="be770-107">Click the arrow icon next to the endpoint you want to publish to create a UDDI registration request.</span></span>  
  
4.  <span data-ttu-id="be770-108">Si un administrateur a activé la publication automatique des points de terminaison, le portail publie automatiquement la nouvelle entrée dans le serveur UDDI.</span><span class="sxs-lookup"><span data-stu-id="be770-108">If an administrator has enabled auto-publishing of endpoints, the portal automatically publishes the new entry into the UDDI server.</span></span>  
  
5.  <span data-ttu-id="be770-109">Si un administrateur n’a pas activé la publication automatique des points de terminaison, les demandes reste dans la file d’attente jusqu'à ce qu’un administrateur approuve ou refuse la demande.</span><span class="sxs-lookup"><span data-stu-id="be770-109">If an administrator has not enabled auto-publishing of endpoints, the requests remains in the queue until an administrator approves or declines the request.</span></span>