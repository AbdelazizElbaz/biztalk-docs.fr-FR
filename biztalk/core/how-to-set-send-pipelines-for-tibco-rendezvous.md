---
title: "Comment configurer l’envoi de Pipelines pour TIBCO Rendezvous | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- send pipelines
- pipelines, send
ms.assetid: a28a02c1-6f30-4749-b819-c1e707757680
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 48d3a72c2282e335f2d3e020ec0e77a8b7afbd35
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-set-send-pipelines-for-tibco-rendezvous"></a><span data-ttu-id="1fd43-102">Définition de pipelines d'envoi pour TIBCO Rendezvous</span><span class="sxs-lookup"><span data-stu-id="1fd43-102">How to Set Send Pipelines for TIBCO Rendezvous</span></span>
<span data-ttu-id="1fd43-103">L'adaptateur Microsoft BizTalk pour TIBCO Rendezvous requiert la sélection des options XMLTransmit et XMLReceive pour les pipelines d'envoi et de réception, respectivement.</span><span class="sxs-lookup"><span data-stu-id="1fd43-103">Microsoft BizTalk Adapter for TIBCO Rendezvous requires that you select XMLTransmit and XMLReceive for the send and receive pipelines respectively.</span></span>  
  
### <a name="to-set-pipelines"></a><span data-ttu-id="1fd43-104">Pour définir les pipelines</span><span class="sxs-lookup"><span data-stu-id="1fd43-104">To set pipelines</span></span>  
  
1.  <span data-ttu-id="1fd43-105">Dans la Console Administration de BizTalk Server, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, puis développez souhaité application.</span><span class="sxs-lookup"><span data-stu-id="1fd43-105">In the BizTalk Server Administration Console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, and then expand the desired application.</span></span>  
  
2.  <span data-ttu-id="1fd43-106">Avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi statique avec sollicitation-réponse**.</span><span class="sxs-lookup"><span data-stu-id="1fd43-106">Right-click **Send Ports**, point to **New**, and then click **Static Solicit-Response Send Port**.</span></span>  
  
3.  <span data-ttu-id="1fd43-107">Dans le **propriétés de Port d’envoi** boîte de dialogue zone, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="1fd43-107">In the **Send Port Properties** dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="1fd43-108">Tapez un nom pour le port d’envoi, par exemple, `SendToTIBCORV`.</span><span class="sxs-lookup"><span data-stu-id="1fd43-108">Type a name for the send port, for example, `SendToTIBCORV`.</span></span>  
  
    2.  <span data-ttu-id="1fd43-109">À partir de la **Type** la liste déroulante, sélectionnez **TIBCO Rendezvous**.</span><span class="sxs-lookup"><span data-stu-id="1fd43-109">From the **Type** drop-down list, select **TIBCO Rendezvous**.</span></span>  
  
    3.  <span data-ttu-id="1fd43-110">À partir de la **Gestionnaire d’envoi** liste déroulante, sélectionnez l’URI.</span><span class="sxs-lookup"><span data-stu-id="1fd43-110">From the **Send handler** drop-down list, select the URI.</span></span>  
  
    4.  <span data-ttu-id="1fd43-111">Dans la liste déroulante Pipeline d’envoi, sélectionnez **Microsoft.BizTalk.DefaultPipelines.XMLTransmit**.</span><span class="sxs-lookup"><span data-stu-id="1fd43-111">From the Send Pipeline drop-down list, select **Microsoft.BizTalk.DefaultPipelines.XMLTransmit**.</span></span>  
  
    5.  <span data-ttu-id="1fd43-112">À partir de la **Pipeline de réception** la liste déroulante, sélectionnez **Microsoft.BizTalk.DefaultPiplelines.XMLReceive**.</span><span class="sxs-lookup"><span data-stu-id="1fd43-112">From the **Receive Pipeline** drop-down list, select **Microsoft.BizTalk.DefaultPiplelines.XMLReceive**.</span></span>  
  
4.  <span data-ttu-id="1fd43-113">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="1fd43-113">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1fd43-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1fd43-114">See Also</span></span>  
 <span data-ttu-id="1fd43-115">[Création gestionnaires d’envoi TIBCO Rendezvous](../core/creating-tibco-rendezvous-send-handlers.md) </span><span class="sxs-lookup"><span data-stu-id="1fd43-115">[Creating TIBCO Rendezvous Send Handlers](../core/creating-tibco-rendezvous-send-handlers.md) </span></span>  
 [<span data-ttu-id="1fd43-116">Gestionnaires de réception création TIBCO Rendezvous</span><span class="sxs-lookup"><span data-stu-id="1fd43-116">Creating TIBCO Rendezvous Receive Handlers</span></span>](../core/creating-tibco-rendezvous-receive-handlers.md)