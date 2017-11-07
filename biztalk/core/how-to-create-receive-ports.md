---
redirect_url: /biztalk/core/creating-tibco-rendezvous-receive-handlers/
redirect_document_id: True
ROBOTS: NOINDEX
ms.openlocfilehash: 0cd93bcd2d1855f137600214b6a07d52b6f52e4f
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="how-to-create-receive-ports"></a><span data-ttu-id="8e9ad-101">Comment créer des Ports de réception</span><span class="sxs-lookup"><span data-stu-id="8e9ad-101">How to Create Receive Ports</span></span>
<span data-ttu-id="8e9ad-102">Suivez ces étapes pour créer un port de réception en utilisant Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8e9ad-102">Follow these steps to create a receive port using Visual Studio.</span></span>  
  
### <a name="to-create-a-receive-port"></a><span data-ttu-id="8e9ad-103">Pour créer un port de réception</span><span class="sxs-lookup"><span data-stu-id="8e9ad-103">To create a receive port</span></span>  
  
1.  <span data-ttu-id="8e9ad-104">Dans la Console Administration de BizTalk Server, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, puis développez souhaité application.</span><span class="sxs-lookup"><span data-stu-id="8e9ad-104">In the BizTalk Server Administration Console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, and then expand the desired application.</span></span>  
  
2.  <span data-ttu-id="8e9ad-105">Avec le bouton droit **Ports de réception**, pointez sur **nouveau**, puis cliquez sur **Ports de réception unidirectionnels**.</span><span class="sxs-lookup"><span data-stu-id="8e9ad-105">Right-click **Receive Ports**, point to **New**, and then click **One-way Receive Ports**.</span></span>  
  
3.  <span data-ttu-id="8e9ad-106">Dans le **propriétés du Port de réception** fenêtre, dans le **général** page, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="8e9ad-106">In the **Receive Port Properties** window, on the **General** page, do the following:</span></span>  
  
    1.  <span data-ttu-id="8e9ad-107">Dans le **nom** , tapez `ReceiveFromTIBCORV`.</span><span class="sxs-lookup"><span data-stu-id="8e9ad-107">In the **Name** field, type `ReceiveFromTIBCORV`.</span></span>  
  
    2.  <span data-ttu-id="8e9ad-108">Dans le **authentification** zone de groupe, spécifiez le traitement des messages lors de l’utilisation de l’authentification.</span><span class="sxs-lookup"><span data-stu-id="8e9ad-108">In the **Authentication** group box, specify how messages are handled when using authentication.</span></span>  
  
    3.  <span data-ttu-id="8e9ad-109">Sélectionnez le **activer le routage pour les messages ayant échoué** case à cocher.</span><span class="sxs-lookup"><span data-stu-id="8e9ad-109">Select the **Enable routing for failed messages** checkbox.</span></span>  
  
4.  <span data-ttu-id="8e9ad-110">Sur le **emplacements de réception** page, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="8e9ad-110">On the **Receive Locations** page, do the following:</span></span>  
  
    1.  <span data-ttu-id="8e9ad-111">Cliquez sur **Nouveau**.</span><span class="sxs-lookup"><span data-stu-id="8e9ad-111">Click **New**.</span></span>  
  
    2.  <span data-ttu-id="8e9ad-112">Dans le **emplacements de réception** fenêtre, dans le **général** , tapez le **nom** l’emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="8e9ad-112">In the **Receive Locations** window, on the **General** page, type the **Name** of the receive location.</span></span>  
  
    3.  <span data-ttu-id="8e9ad-113">À partir de la **Type** liste déroulante, sélectionnez le type de transport et à partir de la **Gestionnaire de réception** liste déroulante, sélectionnez l’adresse de transport.</span><span class="sxs-lookup"><span data-stu-id="8e9ad-113">From the **Type** drop-down list, select the transport type, and from the **Receive handler** drop-down list, select the transport address.</span></span>  
  
    4.  <span data-ttu-id="8e9ad-114">À partir de la **pipeline de réception** liste déroulante, sélectionnez le pipeline de réception.</span><span class="sxs-lookup"><span data-stu-id="8e9ad-114">From the **Receive pipeline** drop-down list, select the receive pipeline.</span></span>  
  
    5.  <span data-ttu-id="8e9ad-115">Sur le **planification** page, sélectionnez le **date de début** et **date de fin** pour restreindre la réception des documents.</span><span class="sxs-lookup"><span data-stu-id="8e9ad-115">On the **Schedule** page, select the **Start date** and the **End date** to restrict receiving documents.</span></span>  
  
    6.  <span data-ttu-id="8e9ad-116">Sélectionnez le **activer la fenêtre de service** case à cocher.</span><span class="sxs-lookup"><span data-stu-id="8e9ad-116">Select the **Enable service window** checkbox.</span></span>  
  
    7.  <span data-ttu-id="8e9ad-117">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="8e9ad-117">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="8e9ad-118">Sur le **mappages entrants** , sélectionnez les mappages entrants pour transformer les documents sur le port sélectionné.</span><span class="sxs-lookup"><span data-stu-id="8e9ad-118">On the **Inbound Maps** page, select the inbound maps for transforming documents on the selected port.</span></span>  
  
6.  <span data-ttu-id="8e9ad-119">Sur le **suivi** , sélectionnez le suivi des propriétés de message et le suivi des corps de message souhaité.</span><span class="sxs-lookup"><span data-stu-id="8e9ad-119">On the **Tracking** page, select the desired tracking message bodies and tracking message properties.</span></span>  
  
7.  <span data-ttu-id="8e9ad-120">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="8e9ad-120">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e9ad-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8e9ad-121">See Also</span></span>  
 [<span data-ttu-id="8e9ad-122">Création de gestionnaires de réception TIBCO Rendezvous</span><span class="sxs-lookup"><span data-stu-id="8e9ad-122">Creating TIBCO Rendezvous Receive Handlers</span></span>](../core/creating-tibco-rendezvous-receive-handlers.md)