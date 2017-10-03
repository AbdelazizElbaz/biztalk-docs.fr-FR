---
title: "Comment créer des Ports d’envoi pour TIBCO Enterprise Message Service | Documents Microsoft"
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
ms.assetid: 6e569244-494e-4db4-8030-eda3b390d073
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bfadeb3306687bfcbea27c0df41973b12b003563
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-send-ports-for-tibco-enterprise-message-service"></a><span data-ttu-id="f5bec-102">Création de ports d'envoi pour TIBCO Enterprise Message Service</span><span class="sxs-lookup"><span data-stu-id="f5bec-102">How to Create Send Ports for TIBCO Enterprise Message Service</span></span>
<span data-ttu-id="f5bec-103">Les étapes suivantes permettent de créer un port d'envoi.</span><span class="sxs-lookup"><span data-stu-id="f5bec-103">Follow these steps to create a send port.</span></span>  
  
## <a name="creating-a-send-port"></a><span data-ttu-id="f5bec-104">Création d'un port d'envoi</span><span class="sxs-lookup"><span data-stu-id="f5bec-104">Creating a Send Port</span></span>  
  
#### <a name="to-create-a-send-port"></a><span data-ttu-id="f5bec-105">Pour créer un port d’envoi</span><span class="sxs-lookup"><span data-stu-id="f5bec-105">To create a send port</span></span>  
  
1.  <span data-ttu-id="f5bec-106">Dans la Console Administration de BizTalk Server, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, puis développez souhaité application.</span><span class="sxs-lookup"><span data-stu-id="f5bec-106">In the BizTalk Server Administration Console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, and then expand the desired application.</span></span>  
  
2.  <span data-ttu-id="f5bec-107">Avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi statique avec sollicitation-réponse**.</span><span class="sxs-lookup"><span data-stu-id="f5bec-107">Right-click **Send Ports**, point to **New**, and then click **Static Solicit-Response Send Port**.</span></span>  
  
3.  <span data-ttu-id="f5bec-108">Dans le **propriétés de Port d’envoi** boîte de dialogue zone, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="f5bec-108">In the **Send Port Properties** dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="f5bec-109">Tapez un nom pour le port d’envoi, par exemple, `SendToTIBCOEMS`.</span><span class="sxs-lookup"><span data-stu-id="f5bec-109">Type a name for the send port, for example, `SendToTIBCOEMS`.</span></span>  
  
    2.  <span data-ttu-id="f5bec-110">À partir de la **Type** la liste déroulante, sélectionnez **TIBCO EMS**.</span><span class="sxs-lookup"><span data-stu-id="f5bec-110">From the **Type** drop-down list, select **TIBCO EMS**.</span></span>  
  
    3.  <span data-ttu-id="f5bec-111">À partir de la **Gestionnaire d’envoi** liste déroulante, sélectionnez l’URI.</span><span class="sxs-lookup"><span data-stu-id="f5bec-111">From the **Send handler** drop-down list, select the URI.</span></span>  
  
    4.  <span data-ttu-id="f5bec-112">Dans la liste déroulante Pipeline d’envoi, sélectionnez **Microsoft.BizTalk.DefaultPipelines.XMLTransmit**.</span><span class="sxs-lookup"><span data-stu-id="f5bec-112">From the Send Pipeline drop-down list, select **Microsoft.BizTalk.DefaultPipelines.XMLTransmit**.</span></span>  
  
    5.  <span data-ttu-id="f5bec-113">À partir de la **Pipeline de réception** la liste déroulante, sélectionnez **Microsoft.BizTalk.DefaultPiplelines.XMLReceive**.</span><span class="sxs-lookup"><span data-stu-id="f5bec-113">From the **Receive Pipeline** drop-down list, select **Microsoft.BizTalk.DefaultPiplelines.XMLReceive**.</span></span>  
  
    6.  <span data-ttu-id="f5bec-114">Cliquez sur **configurer** pour configurer le port d’envoi.</span><span class="sxs-lookup"><span data-stu-id="f5bec-114">Click **Configure** to configure the send port.</span></span>  
  
4.  <span data-ttu-id="f5bec-115">Dans le **propriétés du Transport TIBCO EMS** boîte de dialogue zone, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="f5bec-115">In the **TIBCO EMS Transport Properties** dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="f5bec-116">Entrez **la gestion des messages**, **définition de la connexion serveur**, **prise en charge des transactions**, **nom d’utilisateur**et le  **mot de passe**.</span><span class="sxs-lookup"><span data-stu-id="f5bec-116">Enter **Message Handling**, **Server Connection Definition**, **Transaction Support**, **Username**, and the **password**.</span></span>  
  
         <span data-ttu-id="f5bec-117">Il n'est pas nécessaire de définir les informations de connexion.</span><span class="sxs-lookup"><span data-stu-id="f5bec-117">You do not have to set the logon information.</span></span>  
  
    2.  <span data-ttu-id="f5bec-118">Dans la liste, sélectionnez l'application associée que vous avez créée pour représenter le système TIBCO EMS.</span><span class="sxs-lookup"><span data-stu-id="f5bec-118">In the list, select the affiliate application you created to represent the TIBCO EMS system.</span></span>  
  
    3.  <span data-ttu-id="f5bec-119">Pour **utiliser SSO**, sélectionnez **Oui**.</span><span class="sxs-lookup"><span data-stu-id="f5bec-119">For **Use SSO**, select **Yes**.</span></span>  
  
    4.  <span data-ttu-id="f5bec-120">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="f5bec-120">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="f5bec-121">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="f5bec-121">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5bec-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f5bec-122">See Also</span></span>  
 <span data-ttu-id="f5bec-123">[Définition des propriétés du Transport TIBCO Enterprise Message Service pour le Port d’envoi](../core/setting-tibco-enterprise-message-service-transport-properties-for-the-send-port.md) </span><span class="sxs-lookup"><span data-stu-id="f5bec-123">[Setting TIBCO Enterprise Message Service Transport Properties for the Send Port](../core/setting-tibco-enterprise-message-service-transport-properties-for-the-send-port.md) </span></span>  
 [<span data-ttu-id="f5bec-124">Création de gestionnaires d’envoi TIBCO Enterprise Message Service</span><span class="sxs-lookup"><span data-stu-id="f5bec-124">Creating  TIBCO Enterprise Message Service Send Handlers</span></span>](../core/creating-tibco-enterprise-message-service-send-handlers.md)