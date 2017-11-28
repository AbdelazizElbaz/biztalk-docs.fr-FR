---
redirect_url: /biztalk/core/creating-tibco-rendezvous-send-handlers/
redirect_document_id: True
ROBOTS: NOINDEX
ms.openlocfilehash: 72cdd3553289df39442b71730a61e3271db381e7
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="how-to-set-send-pipelines-for-tibco-rendezvous"></a><span data-ttu-id="c7359-101">Définition de pipelines d'envoi pour TIBCO Rendezvous</span><span class="sxs-lookup"><span data-stu-id="c7359-101">How to Set Send Pipelines for TIBCO Rendezvous</span></span>
<span data-ttu-id="c7359-102">L'adaptateur Microsoft BizTalk pour TIBCO Rendezvous requiert la sélection des options XMLTransmit et XMLReceive pour les pipelines d'envoi et de réception, respectivement.</span><span class="sxs-lookup"><span data-stu-id="c7359-102">Microsoft BizTalk Adapter for TIBCO Rendezvous requires that you select XMLTransmit and XMLReceive for the send and receive pipelines respectively.</span></span>  
  
### <a name="to-set-pipelines"></a><span data-ttu-id="c7359-103">Pour définir les pipelines</span><span class="sxs-lookup"><span data-stu-id="c7359-103">To set pipelines</span></span>  
  
1.  <span data-ttu-id="c7359-104">Dans la Console Administration de BizTalk Server, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, puis développez souhaité application.</span><span class="sxs-lookup"><span data-stu-id="c7359-104">In the BizTalk Server Administration Console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, and then expand the desired application.</span></span>  
  
2.  <span data-ttu-id="c7359-105">Avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi statique avec sollicitation-réponse**.</span><span class="sxs-lookup"><span data-stu-id="c7359-105">Right-click **Send Ports**, point to **New**, and then click **Static Solicit-Response Send Port**.</span></span>  
  
3.  <span data-ttu-id="c7359-106">Dans le **propriétés de Port d’envoi** boîte de dialogue zone, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="c7359-106">In the **Send Port Properties** dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="c7359-107">Tapez un nom pour le port d’envoi, par exemple, `SendToTIBCORV`.</span><span class="sxs-lookup"><span data-stu-id="c7359-107">Type a name for the send port, for example, `SendToTIBCORV`.</span></span>  
  
    2.  <span data-ttu-id="c7359-108">À partir de la **Type** la liste déroulante, sélectionnez **TIBCO Rendezvous**.</span><span class="sxs-lookup"><span data-stu-id="c7359-108">From the **Type** drop-down list, select **TIBCO Rendezvous**.</span></span>  
  
    3.  <span data-ttu-id="c7359-109">À partir de la **Gestionnaire d’envoi** liste déroulante, sélectionnez l’URI.</span><span class="sxs-lookup"><span data-stu-id="c7359-109">From the **Send handler** drop-down list, select the URI.</span></span>  
  
    4.  <span data-ttu-id="c7359-110">Dans la liste déroulante Pipeline d’envoi, sélectionnez **Microsoft.BizTalk.DefaultPipelines.XMLTransmit**.</span><span class="sxs-lookup"><span data-stu-id="c7359-110">From the Send Pipeline drop-down list, select **Microsoft.BizTalk.DefaultPipelines.XMLTransmit**.</span></span>  
  
    5.  <span data-ttu-id="c7359-111">À partir de la **Pipeline de réception** la liste déroulante, sélectionnez **Microsoft.BizTalk.DefaultPiplelines.XMLReceive**.</span><span class="sxs-lookup"><span data-stu-id="c7359-111">From the **Receive Pipeline** drop-down list, select **Microsoft.BizTalk.DefaultPiplelines.XMLReceive**.</span></span>  
  
4.  <span data-ttu-id="c7359-112">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="c7359-112">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7359-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c7359-113">See Also</span></span>  
 <span data-ttu-id="c7359-114">[Création gestionnaires d’envoi TIBCO Rendezvous](../core/creating-tibco-rendezvous-send-handlers.md) </span><span class="sxs-lookup"><span data-stu-id="c7359-114">[Creating TIBCO Rendezvous Send Handlers](../core/creating-tibco-rendezvous-send-handlers.md) </span></span>  
 [<span data-ttu-id="c7359-115">Création de gestionnaires de réception TIBCO Rendezvous</span><span class="sxs-lookup"><span data-stu-id="c7359-115">Creating TIBCO Rendezvous Receive Handlers</span></span>](../core/creating-tibco-rendezvous-receive-handlers.md)