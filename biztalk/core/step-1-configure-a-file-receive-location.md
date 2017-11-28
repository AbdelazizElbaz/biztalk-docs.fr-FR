---
title: "Étape 1 : Configurer un fichier de l’emplacement de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: df591263-964a-4ad8-bc3a-a553de8dae4f
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 78f8bccc187bf310b8426fc3d5fee36add44a9f3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-1-configure-a-file-receive-location"></a><span data-ttu-id="443e0-102">Étape 1 : Configurer un fichier de l’emplacement de réception</span><span class="sxs-lookup"><span data-stu-id="443e0-102">Step 1: Configure a FILE Receive Location</span></span>
<span data-ttu-id="443e0-103">Dans cette rubrique, vous allez configurer un emplacement de réception FILE qui consomme le message de requête factice que vous déposez dans un dossier pour appeler le port d’envoi.</span><span class="sxs-lookup"><span data-stu-id="443e0-103">In this topic, you configure a FILE receive location that consumes the dummy request message that you drop to a file folder to invoke the send port.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="443e0-104">Ce didacticiel suppose que vous utilisez l’application par défaut (**BizTalk Application 1**) pour créer la solution.</span><span class="sxs-lookup"><span data-stu-id="443e0-104">The steps in this tutorial assume that you use the default application (**BizTalk Application 1**) to create the solution.</span></span> <span data-ttu-id="443e0-105">Vous pouvez également créer une autre application et effectuer les mêmes étapes pour celle-ci.</span><span class="sxs-lookup"><span data-stu-id="443e0-105">You can also create another application and perform the same steps in any that application.</span></span>  
  
### <a name="to-configure-a-file-receive-location"></a><span data-ttu-id="443e0-106">Pour configurer un emplacement de réception FILE</span><span class="sxs-lookup"><span data-stu-id="443e0-106">To configure a FILE receive location</span></span>  
  
1.  <span data-ttu-id="443e0-107">À partir de la Console Administration de BizTalk Server, sous la **BizTalk Application 1** nœud, avec le bouton droit **Ports de réception**, pointez sur **nouveau**, puis cliquez sur  **Unidirectionnel Port de réception**.</span><span class="sxs-lookup"><span data-stu-id="443e0-107">From BizTalk Server Administration Console, under the **BizTalk Application 1** node, right-click **Receive Ports**, point to **New**, and then click **One-way Receive Port**.</span></span>  
  
2.  <span data-ttu-id="443e0-108">Sous l’onglet Général, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="443e0-108">On the General tab, do the following:</span></span>  
  
    |<span data-ttu-id="443e0-109">Utiliser</span><span class="sxs-lookup"><span data-stu-id="443e0-109">Use this</span></span>|<span data-ttu-id="443e0-110">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="443e0-110">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="443e0-111">**Nom**</span><span class="sxs-lookup"><span data-stu-id="443e0-111">**Name**</span></span>|<span data-ttu-id="443e0-112">Type **ReceivePortRestAzureMarketPlace**.</span><span class="sxs-lookup"><span data-stu-id="443e0-112">Type **ReceivePortRestAzureMarketPlace**.</span></span>|  
    |<span data-ttu-id="443e0-113">**Activer le routage des messages ayant échoué**</span><span class="sxs-lookup"><span data-stu-id="443e0-113">**Enable routing for failed messages**</span></span>|<span data-ttu-id="443e0-114">(désactivé)</span><span class="sxs-lookup"><span data-stu-id="443e0-114">(clear)</span></span>|  
  
3.  <span data-ttu-id="443e0-115">Cliquez sur **emplacements de réception**, puis cliquez sur **nouveau**.</span><span class="sxs-lookup"><span data-stu-id="443e0-115">Click **Receive Locations**, and then click **New**.</span></span>  
  
4.  <span data-ttu-id="443e0-116">Dans la boîte de dialogue ReceiveLocation1 - Propriétés d'emplacement de réception, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="443e0-116">From Receive Location1 – Receive Location Properties, do the following:</span></span>  
  
    |<span data-ttu-id="443e0-117">Utiliser</span><span class="sxs-lookup"><span data-stu-id="443e0-117">Use this</span></span>|<span data-ttu-id="443e0-118">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="443e0-118">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="443e0-119">**Nom**</span><span class="sxs-lookup"><span data-stu-id="443e0-119">**Name**</span></span>|<span data-ttu-id="443e0-120">Type **ReceiveLocationAzureMarketPlace**.</span><span class="sxs-lookup"><span data-stu-id="443e0-120">Type **ReceiveLocationAzureMarketPlace**.</span></span>|  
    |<span data-ttu-id="443e0-121">**Type**</span><span class="sxs-lookup"><span data-stu-id="443e0-121">**Type**</span></span>|<span data-ttu-id="443e0-122">Sélectionnez **fichier**.</span><span class="sxs-lookup"><span data-stu-id="443e0-122">Select **FILE**.</span></span>|  
    |<span data-ttu-id="443e0-123">**Gestionnaire de réception**</span><span class="sxs-lookup"><span data-stu-id="443e0-123">**Receive handler**</span></span>|<span data-ttu-id="443e0-124">Sélectionnez **BizTalkServerApplication**.</span><span class="sxs-lookup"><span data-stu-id="443e0-124">Select **BizTalkServerApplication**.</span></span>|  
    |<span data-ttu-id="443e0-125">**Pipeline de réception**</span><span class="sxs-lookup"><span data-stu-id="443e0-125">**Receive pipeline**</span></span>|<span data-ttu-id="443e0-126">Sélectionnez **PassThruReceive**.</span><span class="sxs-lookup"><span data-stu-id="443e0-126">Select **PassThruReceive**.</span></span>|  
  
5.  <span data-ttu-id="443e0-127">Cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="443e0-127">Click **Configure**.</span></span>  
  
6.  <span data-ttu-id="443e0-128">Dans la boîte de dialogue Propriétés du transport FILE, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="443e0-128">From File Transport Properties, do the following:</span></span>  
  
    |<span data-ttu-id="443e0-129">Utiliser</span><span class="sxs-lookup"><span data-stu-id="443e0-129">Use this</span></span>|<span data-ttu-id="443e0-130">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="443e0-130">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="443e0-131">**Dossier de réception**</span><span class="sxs-lookup"><span data-stu-id="443e0-131">**Receive folder**</span></span>|<span data-ttu-id="443e0-132">Tapez un emplacement dans lequel vous déposerez le message de requête factice.</span><span class="sxs-lookup"><span data-stu-id="443e0-132">Type a location where you will drop the dummy request message.</span></span>|  
    |<span data-ttu-id="443e0-133">**Nom de fichier**</span><span class="sxs-lookup"><span data-stu-id="443e0-133">**File name**</span></span>|<span data-ttu-id="443e0-134">Conserver`*.xml`</span><span class="sxs-lookup"><span data-stu-id="443e0-134">Retain `*.xml`</span></span>|  
  
7.  <span data-ttu-id="443e0-135">Cliquez sur **OK** jusqu'à ce que vous quittiez toutes les boîtes de dialogue.</span><span class="sxs-lookup"><span data-stu-id="443e0-135">Click **OK** until you exit all the dialog boxes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="443e0-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="443e0-136">See Also</span></span>  
 [<span data-ttu-id="443e0-137">Didacticiel de 5 : Appeler une Interface REST à l’aide de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="443e0-137">Tutorial 5: Invoking a REST Interface Using BizTalk Server</span></span>](../core/tutorial-5-invoking-a-rest-interface-using-biztalk-server.md)