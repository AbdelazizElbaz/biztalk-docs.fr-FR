---
redirect_url: /biztalk/core/creating-tibco-enterprise-message-service-send-handlers/
redirect_document_id: True
ROBOTS: NOINDEX
ms.openlocfilehash: dc9746babaa80520b2a99948c5796c9b064899e0
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="how-to-set-send-pipelines-for-tibco-enterprise-message-service"></a><span data-ttu-id="d06ed-101">Configuration des pipelines d'envoi pour TIBCO Enterprise Message Service</span><span class="sxs-lookup"><span data-stu-id="d06ed-101">How to Set Send Pipelines for TIBCO Enterprise Message Service</span></span>
<span data-ttu-id="d06ed-102">L'adaptateur Microsoft BizTalk pour TIBCO Enterprise Message Service requiert la sélection de XMLTransmit et XMLReceive pour les pipelines d'envoi et de réception, respectivement.</span><span class="sxs-lookup"><span data-stu-id="d06ed-102">Microsoft BizTalk Adapter for TIBCO Enterprise Message Service requires that you select XMLTransmit and XMLReceive for the Send and Receive pipelines respectively.</span></span>  
  
### <a name="to-set-pipelines"></a><span data-ttu-id="d06ed-103">Pour définir les pipelines</span><span class="sxs-lookup"><span data-stu-id="d06ed-103">To set pipelines</span></span>  
  
1.  <span data-ttu-id="d06ed-104">Dans la Console Administration de BizTalk Server, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, puis développez souhaité application.</span><span class="sxs-lookup"><span data-stu-id="d06ed-104">In the BizTalk Server Administration Console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, and then expand the desired application.</span></span>  
  
2.  <span data-ttu-id="d06ed-105">Avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi statique avec sollicitation-réponse**.</span><span class="sxs-lookup"><span data-stu-id="d06ed-105">Right-click **Send Ports**, point to **New**, and then click **Static Solicit-Response Send Port**.</span></span>  
  
3.  <span data-ttu-id="d06ed-106">Dans le **propriétés de Port d’envoi** boîte de dialogue zone, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="d06ed-106">In the **Send Port Properties** dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="d06ed-107">Tapez un nom pour le port d’envoi, par exemple, `SendToTIBCOEMS`.</span><span class="sxs-lookup"><span data-stu-id="d06ed-107">Type a name for the send port, for example, `SendToTIBCOEMS`.</span></span>  
  
    2.  <span data-ttu-id="d06ed-108">À partir de la **Type** la liste déroulante, sélectionnez **TIBCO EMS**.</span><span class="sxs-lookup"><span data-stu-id="d06ed-108">From the **Type** drop-down list, select **TIBCO EMS**.</span></span>  
  
    3.  <span data-ttu-id="d06ed-109">À partir de la **Gestionnaire d’envoi** liste déroulante, sélectionnez l’URI.</span><span class="sxs-lookup"><span data-stu-id="d06ed-109">From the **Send handler** drop-down list, select the URI.</span></span>  
  
    4.  <span data-ttu-id="d06ed-110">Dans la liste déroulante Pipeline d’envoi, sélectionnez **Microsoft.BizTalk.DefaultPipelines.XMLTransmit**.</span><span class="sxs-lookup"><span data-stu-id="d06ed-110">From the Send Pipeline drop-down list, select **Microsoft.BizTalk.DefaultPipelines.XMLTransmit**.</span></span>  
  
    5.  <span data-ttu-id="d06ed-111">À partir de la **Pipeline de réception** la liste déroulante, sélectionnez **Microsoft.BizTalk.DefaultPiplelines.XMLReceive**.</span><span class="sxs-lookup"><span data-stu-id="d06ed-111">From the **Receive Pipeline** drop-down list, select **Microsoft.BizTalk.DefaultPiplelines.XMLReceive**.</span></span>  
  
4.  <span data-ttu-id="d06ed-112">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="d06ed-112">Click **OK**.</span></span>  
  
