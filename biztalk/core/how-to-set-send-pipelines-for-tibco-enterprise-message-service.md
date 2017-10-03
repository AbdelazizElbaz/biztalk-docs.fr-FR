---
title: "Comment configurer l’envoi de Pipelines pour TIBCO Enterprise Message Service | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- send pipelines
- setting send pipelines
- pipelines, send
ms.assetid: 6a84d874-4b4d-4b23-913f-f5c72af1e96e
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d037782e2580d52c6609c3669e2805aae92ce9eb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-set-send-pipelines-for-tibco-enterprise-message-service"></a><span data-ttu-id="a884d-102">Configuration des pipelines d'envoi pour TIBCO Enterprise Message Service</span><span class="sxs-lookup"><span data-stu-id="a884d-102">How to Set Send Pipelines for TIBCO Enterprise Message Service</span></span>
<span data-ttu-id="a884d-103">L'adaptateur Microsoft BizTalk pour TIBCO Enterprise Message Service requiert la sélection de XMLTransmit et XMLReceive pour les pipelines d'envoi et de réception, respectivement.</span><span class="sxs-lookup"><span data-stu-id="a884d-103">Microsoft BizTalk Adapter for TIBCO Enterprise Message Service requires that you select XMLTransmit and XMLReceive for the Send and Receive pipelines respectively.</span></span>  
  
### <a name="to-set-pipelines"></a><span data-ttu-id="a884d-104">Pour définir les pipelines</span><span class="sxs-lookup"><span data-stu-id="a884d-104">To set pipelines</span></span>  
  
1.  <span data-ttu-id="a884d-105">Dans la Console Administration de BizTalk Server, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, puis développez souhaité application.</span><span class="sxs-lookup"><span data-stu-id="a884d-105">In the BizTalk Server Administration Console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, and then expand the desired application.</span></span>  
  
2.  <span data-ttu-id="a884d-106">Avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi statique avec sollicitation-réponse**.</span><span class="sxs-lookup"><span data-stu-id="a884d-106">Right-click **Send Ports**, point to **New**, and then click **Static Solicit-Response Send Port**.</span></span>  
  
3.  <span data-ttu-id="a884d-107">Dans le **propriétés de Port d’envoi** boîte de dialogue zone, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="a884d-107">In the **Send Port Properties** dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="a884d-108">Tapez un nom pour le port d’envoi, par exemple, `SendToTIBCOEMS`.</span><span class="sxs-lookup"><span data-stu-id="a884d-108">Type a name for the send port, for example, `SendToTIBCOEMS`.</span></span>  
  
    2.  <span data-ttu-id="a884d-109">À partir de la **Type** la liste déroulante, sélectionnez **TIBCO EMS**.</span><span class="sxs-lookup"><span data-stu-id="a884d-109">From the **Type** drop-down list, select **TIBCO EMS**.</span></span>  
  
    3.  <span data-ttu-id="a884d-110">À partir de la **Gestionnaire d’envoi** liste déroulante, sélectionnez l’URI.</span><span class="sxs-lookup"><span data-stu-id="a884d-110">From the **Send handler** drop-down list, select the URI.</span></span>  
  
    4.  <span data-ttu-id="a884d-111">Dans la liste déroulante Pipeline d’envoi, sélectionnez **Microsoft.BizTalk.DefaultPipelines.XMLTransmit**.</span><span class="sxs-lookup"><span data-stu-id="a884d-111">From the Send Pipeline drop-down list, select **Microsoft.BizTalk.DefaultPipelines.XMLTransmit**.</span></span>  
  
    5.  <span data-ttu-id="a884d-112">À partir de la **Pipeline de réception** la liste déroulante, sélectionnez **Microsoft.BizTalk.DefaultPiplelines.XMLReceive**.</span><span class="sxs-lookup"><span data-stu-id="a884d-112">From the **Receive Pipeline** drop-down list, select **Microsoft.BizTalk.DefaultPiplelines.XMLReceive**.</span></span>  
  
4.  <span data-ttu-id="a884d-113">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="a884d-113">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a884d-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a884d-114">See Also</span></span>  
 [<span data-ttu-id="a884d-115">Procédure de Pipelines de réception pour TIBCO Enterprise Message Service</span><span class="sxs-lookup"><span data-stu-id="a884d-115">How to Set Receive Pipelines for TIBCO Enterprise Message Service</span></span>](../core/how-to-set-receive-pipelines-for-tibco-enterprise-message-service.md)