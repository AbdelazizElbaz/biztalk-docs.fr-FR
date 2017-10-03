---
title: "Comment créer des Ports de réception dans TIBCO Enterprise Message Service | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- receive ports, creating
- creating receive ports
ms.assetid: ca623c81-3dd3-4824-a586-28055d01fe9f
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a85fad9dc0936baa0c3f584581d5483a30fedf6f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-receive-ports-in-tibco-enterprise-message-service"></a><span data-ttu-id="83d9b-102">Création de ports de réception pour TIBCO Enterprise Message Service</span><span class="sxs-lookup"><span data-stu-id="83d9b-102">How to Create Receive Ports in TIBCO Enterprise Message Service</span></span>
<span data-ttu-id="83d9b-103">Les étapes suivantes permettent de créer un port de réception.</span><span class="sxs-lookup"><span data-stu-id="83d9b-103">Follow these steps to create a receive port.</span></span>  
  
### <a name="to-create-a-receive-port"></a><span data-ttu-id="83d9b-104">Pour créer un port de réception</span><span class="sxs-lookup"><span data-stu-id="83d9b-104">To create a receive port</span></span>  
  
1.  <span data-ttu-id="83d9b-105">Dans la Console Administration de BizTalk Server, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, puis développez souhaité application.</span><span class="sxs-lookup"><span data-stu-id="83d9b-105">In the BizTalk Server Administration Console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, and then expand the desired application.</span></span>  
  
2.  <span data-ttu-id="83d9b-106">Avec le bouton droit **Ports de réception**, pointez sur **nouveau**, puis cliquez sur **Ports de réception unidirectionnels**.</span><span class="sxs-lookup"><span data-stu-id="83d9b-106">Right-click **Receive Ports**, point to **New**, and then click **One-way Receive Ports**.</span></span>  
  
3.  <span data-ttu-id="83d9b-107">Dans le **propriétés du Port de réception** fenêtre, dans le **général** page, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="83d9b-107">In the **Receive Port Properties** window, on the **General** page, do the following:</span></span>  
  
    1.  <span data-ttu-id="83d9b-108">Dans le **nom** , tapez `ReceiveFromTIBCOEMS`.</span><span class="sxs-lookup"><span data-stu-id="83d9b-108">In the **Name** field, type `ReceiveFromTIBCOEMS`.</span></span>  
  
    2.  <span data-ttu-id="83d9b-109">Dans le **authentification** zone de groupe, spécifiez le traitement des messages lors de l’utilisation de l’authentification.</span><span class="sxs-lookup"><span data-stu-id="83d9b-109">In the **Authentication** group box, specify how messages are handled when using authentication.</span></span>  
  
    3.  <span data-ttu-id="83d9b-110">Sélectionnez le **activer le routage pour les messages ayant échoué** case à cocher.</span><span class="sxs-lookup"><span data-stu-id="83d9b-110">Select the **Enable routing for failed messages** checkbox.</span></span>  
  
4.  <span data-ttu-id="83d9b-111">Sur le **emplacements de réception** page, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="83d9b-111">On the **Receive Locations** page, do the following:</span></span>  
  
    1.  <span data-ttu-id="83d9b-112">Cliquez sur **Nouveau**.</span><span class="sxs-lookup"><span data-stu-id="83d9b-112">Click **New**.</span></span>  
  
    2.  <span data-ttu-id="83d9b-113">Dans le **emplacements de réception** fenêtre, dans le **général** , tapez le **nom** l’emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="83d9b-113">In the **Receive Locations** window, on the **General** page, type the **Name** of the receive location.</span></span>  
  
    3.  <span data-ttu-id="83d9b-114">À partir de la **Type** liste déroulante, sélectionnez le type de transport et à partir de la **Gestionnaire de réception** liste déroulante, sélectionnez l’adresse de transport.</span><span class="sxs-lookup"><span data-stu-id="83d9b-114">From the **Type** drop-down list, select the transport type, and from the **Receive handler** drop-down list, select the transport address.</span></span>  
  
    4.  <span data-ttu-id="83d9b-115">À partir de la **pipeline de réception** liste déroulante, sélectionnez le pipeline de réception.</span><span class="sxs-lookup"><span data-stu-id="83d9b-115">From the **Receive pipeline** drop-down list, select the receive pipeline.</span></span>  
  
    5.  <span data-ttu-id="83d9b-116">Sur le **planification** page, sélectionnez le **date de début** et **date de fin** pour restreindre la réception des documents.</span><span class="sxs-lookup"><span data-stu-id="83d9b-116">On the **Schedule** page, select the **Start date** and the **End date** to restrict receiving documents.</span></span>  
  
    6.  <span data-ttu-id="83d9b-117">Sélectionnez le **activer la fenêtre de service** case à cocher.</span><span class="sxs-lookup"><span data-stu-id="83d9b-117">Select the **Enable service window** checkbox.</span></span>  
  
    7.  <span data-ttu-id="83d9b-118">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="83d9b-118">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="83d9b-119">Sur le **mappages entrants** , sélectionnez les mappages entrants pour transformer les documents sur le port sélectionné.</span><span class="sxs-lookup"><span data-stu-id="83d9b-119">On the **Inbound Maps** page, select the inbound maps for transforming documents on the selected port.</span></span>  
  
6.  <span data-ttu-id="83d9b-120">Sur le **suivi** , sélectionnez le suivi des propriétés de message et le suivi des corps de message souhaité.</span><span class="sxs-lookup"><span data-stu-id="83d9b-120">On the **Tracking** page, select the desired tracking message bodies and tracking message properties.</span></span>  
  
7.  <span data-ttu-id="83d9b-121">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="83d9b-121">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83d9b-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="83d9b-122">See Also</span></span>  
 [<span data-ttu-id="83d9b-123">Définition des propriétés du Transport TIBCO Enterprise Message Service pour le Port de réception</span><span class="sxs-lookup"><span data-stu-id="83d9b-123">Setting TIBCO Enterprise Message Service Transport Properties for the Receive Port</span></span>](../core/set-tibco-enterprise-message-service-transport-properties-for-the-receive-port.md)