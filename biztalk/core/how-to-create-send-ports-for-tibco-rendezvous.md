---
redirect_url: /biztalk/core/creating-tibco-rendezvous-send-handlers/
redirect_document_id: True
ROBOTS: NOINDEX
ms.openlocfilehash: 44da7839f0bee96db332dada214bdbc503067f56
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="how-to-create-send-ports-for-tibco-rendezvous"></a><span data-ttu-id="b6140-101">Création de ports d'envoi pour TIBCO Rendezvous</span><span class="sxs-lookup"><span data-stu-id="b6140-101">How to Create Send Ports for TIBCO Rendezvous</span></span>
<span data-ttu-id="b6140-102">Les étapes suivantes permettent de créer un port d'envoi à l'aide de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b6140-102">Follow these steps to create a send port using [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span></span>  
  
### <a name="to-create-a-send-port"></a><span data-ttu-id="b6140-103">Pour créer un port d’envoi</span><span class="sxs-lookup"><span data-stu-id="b6140-103">To create a send port</span></span>  
  
1.  <span data-ttu-id="b6140-104">Dans la Console Administration de BizTalk Server, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, puis développez souhaité application.</span><span class="sxs-lookup"><span data-stu-id="b6140-104">In the BizTalk Server Administration Console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, and then expand the desired application.</span></span>  
  
2.  <span data-ttu-id="b6140-105">Avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi statique avec sollicitation-réponse**.</span><span class="sxs-lookup"><span data-stu-id="b6140-105">Right-click **Send Ports**, point to **New**, and then click **Static Solicit-Response Send Port**.</span></span>  
  
3.  <span data-ttu-id="b6140-106">Dans le **propriétés de Port d’envoi** boîte de dialogue zone, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="b6140-106">In the **Send Port Properties** dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="b6140-107">Tapez un nom pour le port d’envoi, par exemple, `SendToTIBCORV`.</span><span class="sxs-lookup"><span data-stu-id="b6140-107">Type a name for the send port, for example, `SendToTIBCORV`.</span></span>  
  
    2.  <span data-ttu-id="b6140-108">À partir de la **Type** la liste déroulante, sélectionnez **TIBCO Rendezvous**.</span><span class="sxs-lookup"><span data-stu-id="b6140-108">From the **Type** drop-down list, select **TIBCO Rendezvous**.</span></span>  
  
    3.  <span data-ttu-id="b6140-109">À partir de la **Gestionnaire d’envoi** liste déroulante, sélectionnez l’URI.</span><span class="sxs-lookup"><span data-stu-id="b6140-109">From the **Send handler** drop-down list, select the URI.</span></span>  
  
    4.  <span data-ttu-id="b6140-110">À partir de la **Pipeline d’envoi** la liste déroulante, sélectionnez **Microsoft.BizTalk.DefaultPipelines.XMLTransmit**.</span><span class="sxs-lookup"><span data-stu-id="b6140-110">From the **Send Pipeline** drop-down list, select **Microsoft.BizTalk.DefaultPipelines.XMLTransmit**.</span></span> <span data-ttu-id="b6140-111">À partir de la **Pipeline de réception** la liste déroulante, sélectionnez **Microsoft.BizTalk.DefaultPiplelines.XMLReceive**.</span><span class="sxs-lookup"><span data-stu-id="b6140-111">From the **Receive Pipeline** drop-down list, select **Microsoft.BizTalk.DefaultPiplelines.XMLReceive**.</span></span>  
  
    6.  <span data-ttu-id="b6140-112">Cliquez sur **configurer** pour configurer le port d’envoi.</span><span class="sxs-lookup"><span data-stu-id="b6140-112">Click **Configure** to configure the send port.</span></span>  
  
4.  <span data-ttu-id="b6140-113">Dans le **propriétés du Transport TIBCO Rendezvous** boîte de dialogue zone, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="b6140-113">In the **TIBCO Rendezvous Transport Properties** dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="b6140-114">Saisissez les propriétés.</span><span class="sxs-lookup"><span data-stu-id="b6140-114">Enter the properties.</span></span>  
  
         <span data-ttu-id="b6140-115">Il n'est pas nécessaire de définir les informations de connexion.</span><span class="sxs-lookup"><span data-stu-id="b6140-115">You do not have to set the logon information.</span></span>  
  
    2.  <span data-ttu-id="b6140-116">Dans la liste, sélectionnez l'application SSO associée que vous avez créée pour représenter le système TIBCO Rendezvous.</span><span class="sxs-lookup"><span data-stu-id="b6140-116">In the list, select the SSO affiliate application you created to represent the TIBCO Rendezvous system.</span></span>  
  
    3.  <span data-ttu-id="b6140-117">Pour **utiliser SSO**, sélectionnez **Oui**.</span><span class="sxs-lookup"><span data-stu-id="b6140-117">For **Use SSO**, select **Yes**.</span></span>  
  
    4.  <span data-ttu-id="b6140-118">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="b6140-118">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="b6140-119">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="b6140-119">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6140-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b6140-120">See Also</span></span>  
 [<span data-ttu-id="b6140-121">Création de gestionnaires d’envoi TIBCO Rendezvous</span><span class="sxs-lookup"><span data-stu-id="b6140-121">Creating TIBCO Rendezvous Send Handlers</span></span>](../core/creating-tibco-rendezvous-send-handlers.md)