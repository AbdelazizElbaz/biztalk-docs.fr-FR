---
redirect_url: /biztalk/core/creating-tibco-enterprise-message-service-send-handlers/
redirect_document_id: True
ROBOTS: NOINDEX
ms.openlocfilehash: 6b15d9d03ef967bcf7189ef756da8fc63a0eb3f6
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="how-to-create-send-ports-for-tibco-enterprise-message-service"></a><span data-ttu-id="af3e0-101">Création de ports d'envoi pour TIBCO Enterprise Message Service</span><span class="sxs-lookup"><span data-stu-id="af3e0-101">How to Create Send Ports for TIBCO Enterprise Message Service</span></span>
<span data-ttu-id="af3e0-102">Les étapes suivantes permettent de créer un port d'envoi.</span><span class="sxs-lookup"><span data-stu-id="af3e0-102">Follow these steps to create a send port.</span></span>  
  
## <a name="creating-a-send-port"></a><span data-ttu-id="af3e0-103">Création d'un port d'envoi</span><span class="sxs-lookup"><span data-stu-id="af3e0-103">Creating a Send Port</span></span>  
  
#### <a name="to-create-a-send-port"></a><span data-ttu-id="af3e0-104">Pour créer un port d’envoi</span><span class="sxs-lookup"><span data-stu-id="af3e0-104">To create a send port</span></span>  
  
1.  <span data-ttu-id="af3e0-105">Dans la Console Administration de BizTalk Server, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, puis développez souhaité application.</span><span class="sxs-lookup"><span data-stu-id="af3e0-105">In the BizTalk Server Administration Console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, and then expand the desired application.</span></span>  
  
2.  <span data-ttu-id="af3e0-106">Avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi statique avec sollicitation-réponse**.</span><span class="sxs-lookup"><span data-stu-id="af3e0-106">Right-click **Send Ports**, point to **New**, and then click **Static Solicit-Response Send Port**.</span></span>  
  
3.  <span data-ttu-id="af3e0-107">Dans le **propriétés de Port d’envoi** boîte de dialogue zone, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="af3e0-107">In the **Send Port Properties** dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="af3e0-108">Tapez un nom pour le port d’envoi, par exemple, `SendToTIBCOEMS`.</span><span class="sxs-lookup"><span data-stu-id="af3e0-108">Type a name for the send port, for example, `SendToTIBCOEMS`.</span></span>  
  
    2.  <span data-ttu-id="af3e0-109">À partir de la **Type** la liste déroulante, sélectionnez **TIBCO EMS**.</span><span class="sxs-lookup"><span data-stu-id="af3e0-109">From the **Type** drop-down list, select **TIBCO EMS**.</span></span>  
  
    3.  <span data-ttu-id="af3e0-110">À partir de la **Gestionnaire d’envoi** liste déroulante, sélectionnez l’URI.</span><span class="sxs-lookup"><span data-stu-id="af3e0-110">From the **Send handler** drop-down list, select the URI.</span></span>  
  
    4.  <span data-ttu-id="af3e0-111">Dans la liste déroulante Pipeline d’envoi, sélectionnez **Microsoft.BizTalk.DefaultPipelines.XMLTransmit**.</span><span class="sxs-lookup"><span data-stu-id="af3e0-111">From the Send Pipeline drop-down list, select **Microsoft.BizTalk.DefaultPipelines.XMLTransmit**.</span></span>  
  
    5.  <span data-ttu-id="af3e0-112">À partir de la **Pipeline de réception** la liste déroulante, sélectionnez **Microsoft.BizTalk.DefaultPiplelines.XMLReceive**.</span><span class="sxs-lookup"><span data-stu-id="af3e0-112">From the **Receive Pipeline** drop-down list, select **Microsoft.BizTalk.DefaultPiplelines.XMLReceive**.</span></span>  
  
    6.  <span data-ttu-id="af3e0-113">Cliquez sur **configurer** pour configurer le port d’envoi.</span><span class="sxs-lookup"><span data-stu-id="af3e0-113">Click **Configure** to configure the send port.</span></span>  
  
4.  <span data-ttu-id="af3e0-114">Dans le **propriétés du Transport TIBCO EMS** boîte de dialogue zone, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="af3e0-114">In the **TIBCO EMS Transport Properties** dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="af3e0-115">Entrez **la gestion des messages**, **définition de la connexion serveur**, **prise en charge des transactions**, **nom d’utilisateur**et le  **mot de passe**.</span><span class="sxs-lookup"><span data-stu-id="af3e0-115">Enter **Message Handling**, **Server Connection Definition**, **Transaction Support**, **Username**, and the **password**.</span></span>  
  
         <span data-ttu-id="af3e0-116">Il n'est pas nécessaire de définir les informations de connexion.</span><span class="sxs-lookup"><span data-stu-id="af3e0-116">You do not have to set the logon information.</span></span>  
  
    2.  <span data-ttu-id="af3e0-117">Dans la liste, sélectionnez l'application associée que vous avez créée pour représenter le système TIBCO EMS.</span><span class="sxs-lookup"><span data-stu-id="af3e0-117">In the list, select the affiliate application you created to represent the TIBCO EMS system.</span></span>  
  
    3.  <span data-ttu-id="af3e0-118">Pour **utiliser SSO**, sélectionnez **Oui**.</span><span class="sxs-lookup"><span data-stu-id="af3e0-118">For **Use SSO**, select **Yes**.</span></span>  
  
    4.  <span data-ttu-id="af3e0-119">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="af3e0-119">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="af3e0-120">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="af3e0-120">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af3e0-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="af3e0-121">See Also</span></span>  
  [<span data-ttu-id="af3e0-122">Création de gestionnaires d’envoi TIBCO Enterprise Message Service</span><span class="sxs-lookup"><span data-stu-id="af3e0-122">Creating  TIBCO Enterprise Message Service Send Handlers</span></span>](../core/creating-tibco-enterprise-message-service-send-handlers.md)