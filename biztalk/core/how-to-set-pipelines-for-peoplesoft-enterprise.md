---
redirect_url: /biztalk/core/creating-peoplesoft-send-handlers/
redirect_document_id: True
ROBOTS: NOINDEX
ms.openlocfilehash: e5f68232aa0cb59835523df0afac01f3d1949489
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="how-to-set-pipelines-for-peoplesoft-enterprise"></a><span data-ttu-id="4c33d-101">Définition de pipelines pour PeopleSoft Enterprise</span><span class="sxs-lookup"><span data-stu-id="4c33d-101">How to Set Pipelines for PeopleSoft Enterprise</span></span>
<span data-ttu-id="4c33d-102">L'adaptateur Microsoft BizTalk pour PeopleSoft Enterprise requiert la sélection d'un pipeline approprié.</span><span class="sxs-lookup"><span data-stu-id="4c33d-102">Microsoft BizTalk Adapter for PeopleSoft Enterprise requires that you select an appropriate pipeline.</span></span>  
  
## <a name="setting-pipelines"></a><span data-ttu-id="4c33d-103">Configuration des pipelines</span><span class="sxs-lookup"><span data-stu-id="4c33d-103">Setting Pipelines</span></span>  
  
#### <a name="to-set-pipelines"></a><span data-ttu-id="4c33d-104">Pour définir les pipelines</span><span class="sxs-lookup"><span data-stu-id="4c33d-104">To set pipelines</span></span>  
  
1.  <span data-ttu-id="4c33d-105">Dans la Console Administration de BizTalk Server, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, puis développez souhaité application.</span><span class="sxs-lookup"><span data-stu-id="4c33d-105">In the BizTalk Server Administration Console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, and then expand the desired application.</span></span>  
  
2.  <span data-ttu-id="4c33d-106">Avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi statique avec sollicitation-réponse**.</span><span class="sxs-lookup"><span data-stu-id="4c33d-106">Right-click **Send Ports**, point to **New**, and then click **Static Solicit-Response Send Port**.</span></span>  
  
3.  <span data-ttu-id="4c33d-107">Dans le **propriétés de Port d’envoi** boîte de dialogue zone, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="4c33d-107">In the **Send Port Properties** dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="4c33d-108">Tapez un nom pour le port d’envoi, par exemple, `SSOSendToPeopleSoft`.</span><span class="sxs-lookup"><span data-stu-id="4c33d-108">Type a name for the send port, for example, `SSOSendToPeopleSoft`.</span></span>  
  
    2.  <span data-ttu-id="4c33d-109">À partir de la **Type** la liste déroulante, sélectionnez **PeopleSoft**.</span><span class="sxs-lookup"><span data-stu-id="4c33d-109">From the **Type** drop-down list, select **PeopleSoft**.</span></span>  
  
    3.  <span data-ttu-id="4c33d-110">À partir de la **Gestionnaire d’envoi** liste déroulante, sélectionnez l’URI.</span><span class="sxs-lookup"><span data-stu-id="4c33d-110">From the **Send handler** drop-down list, select the URI.</span></span>  
  
    4.  <span data-ttu-id="4c33d-111">Dans la liste déroulante Pipeline d’envoi, sélectionnez **Microsoft.BizTalk.DefaultPipelines.XMLTransmit**.</span><span class="sxs-lookup"><span data-stu-id="4c33d-111">From the Send Pipeline drop-down list, select **Microsoft.BizTalk.DefaultPipelines.XMLTransmit**.</span></span>  
  
    5.  <span data-ttu-id="4c33d-112">À partir de la **Pipeline de réception** la liste déroulante, sélectionnez **Microsoft.BizTalk.DefaultPiplelines.XMLReceive**.</span><span class="sxs-lookup"><span data-stu-id="4c33d-112">From the **Receive Pipeline** drop-down list, select **Microsoft.BizTalk.DefaultPiplelines.XMLReceive**.</span></span>  
  
4.  <span data-ttu-id="4c33d-113">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="4c33d-113">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c33d-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4c33d-114">See Also</span></span>  
 [<span data-ttu-id="4c33d-115">Création de gestionnaires d’envoi PeopleSoft</span><span class="sxs-lookup"><span data-stu-id="4c33d-115">Creating PeopleSoft Send Handlers</span></span>](../core/creating-peoplesoft-send-handlers.md)