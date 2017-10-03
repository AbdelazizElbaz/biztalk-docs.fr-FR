---
title: "Comment créer des Ports d’envoi pour TIBCO Rendezvous | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating send ports
- ports, send
- send ports, creating
ms.assetid: 0c8d9fdc-b273-4876-9f93-b5a85539a3c1
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7d0b6e7dbb1a3b32979c94ec1af9483bd9fcb7cb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-send-ports-for-tibco-rendezvous"></a><span data-ttu-id="03b5f-102">Création de ports d'envoi pour TIBCO Rendezvous</span><span class="sxs-lookup"><span data-stu-id="03b5f-102">How to Create Send Ports for TIBCO Rendezvous</span></span>
<span data-ttu-id="03b5f-103">Les étapes suivantes permettent de créer un port d'envoi à l'aide de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="03b5f-103">Follow these steps to create a send port using [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span></span>  
  
### <a name="to-create-a-send-port"></a><span data-ttu-id="03b5f-104">Pour créer un port d’envoi</span><span class="sxs-lookup"><span data-stu-id="03b5f-104">To create a send port</span></span>  
  
1.  <span data-ttu-id="03b5f-105">Dans la Console Administration de BizTalk Server, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, puis développez souhaité application.</span><span class="sxs-lookup"><span data-stu-id="03b5f-105">In the BizTalk Server Administration Console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, and then expand the desired application.</span></span>  
  
2.  <span data-ttu-id="03b5f-106">Avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi statique avec sollicitation-réponse**.</span><span class="sxs-lookup"><span data-stu-id="03b5f-106">Right-click **Send Ports**, point to **New**, and then click **Static Solicit-Response Send Port**.</span></span>  
  
3.  <span data-ttu-id="03b5f-107">Dans le **propriétés de Port d’envoi** boîte de dialogue zone, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="03b5f-107">In the **Send Port Properties** dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="03b5f-108">Tapez un nom pour le port d’envoi, par exemple, `SendToTIBCORV`.</span><span class="sxs-lookup"><span data-stu-id="03b5f-108">Type a name for the send port, for example, `SendToTIBCORV`.</span></span>  
  
    2.  <span data-ttu-id="03b5f-109">À partir de la **Type** la liste déroulante, sélectionnez **TIBCO Rendezvous**.</span><span class="sxs-lookup"><span data-stu-id="03b5f-109">From the **Type** drop-down list, select **TIBCO Rendezvous**.</span></span>  
  
    3.  <span data-ttu-id="03b5f-110">À partir de la **Gestionnaire d’envoi** liste déroulante, sélectionnez l’URI.</span><span class="sxs-lookup"><span data-stu-id="03b5f-110">From the **Send handler** drop-down list, select the URI.</span></span>  
  
    4.  <span data-ttu-id="03b5f-111">Dans la liste déroulante Pipeline d’envoi, sélectionnez **Microsoft.BizTalk.DefaultPipelines.XMLTransmit**.</span><span class="sxs-lookup"><span data-stu-id="03b5f-111">From the Send Pipeline drop-down list, select **Microsoft.BizTalk.DefaultPipelines.XMLTransmit**.</span></span>  
  
    5.  <span data-ttu-id="03b5f-112">À partir de la **Pipeline de réception** la liste déroulante, sélectionnez **Microsoft.BizTalk.DefaultPiplelines.XMLReceive**.</span><span class="sxs-lookup"><span data-stu-id="03b5f-112">From the **Receive Pipeline** drop-down list, select **Microsoft.BizTalk.DefaultPiplelines.XMLReceive**.</span></span>  
  
    6.  <span data-ttu-id="03b5f-113">Cliquez sur **configurer** pour configurer le port d’envoi.</span><span class="sxs-lookup"><span data-stu-id="03b5f-113">Click **Configure** to configure the send port.</span></span>  
  
4.  <span data-ttu-id="03b5f-114">Dans le **propriétés du Transport TIBCO Rendezvous** boîte de dialogue zone, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="03b5f-114">In the **TIBCO Rendezvous Transport Properties** dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="03b5f-115">Saisissez les propriétés.</span><span class="sxs-lookup"><span data-stu-id="03b5f-115">Enter the properties.</span></span>  
  
         <span data-ttu-id="03b5f-116">Il n'est pas nécessaire de définir les informations de connexion.</span><span class="sxs-lookup"><span data-stu-id="03b5f-116">You do not have to set the logon information.</span></span>  
  
    2.  <span data-ttu-id="03b5f-117">Dans la liste, sélectionnez l'application SSO associée que vous avez créée pour représenter le système TIBCO Rendezvous.</span><span class="sxs-lookup"><span data-stu-id="03b5f-117">In the list, select the SSO affiliate application you created to represent the TIBCO Rendezvous system.</span></span>  
  
    3.  <span data-ttu-id="03b5f-118">Pour **utiliser SSO**, sélectionnez **Oui**.</span><span class="sxs-lookup"><span data-stu-id="03b5f-118">For **Use SSO**, select **Yes**.</span></span>  
  
    4.  <span data-ttu-id="03b5f-119">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="03b5f-119">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="03b5f-120">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="03b5f-120">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03b5f-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="03b5f-121">See Also</span></span>  
 [<span data-ttu-id="03b5f-122">Création gestionnaires d’envoi TIBCO Rendezvous</span><span class="sxs-lookup"><span data-stu-id="03b5f-122">Creating TIBCO Rendezvous Send Handlers</span></span>](../core/creating-tibco-rendezvous-send-handlers.md)