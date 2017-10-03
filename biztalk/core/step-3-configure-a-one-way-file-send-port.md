---
title: "Étape 3 : Configurer un Port d’envoi FILE unidirectionnel | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c52c6b6b-6f9c-48f2-8732-450fe3a15eae
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ceb055f0d4d41eb82eb79cb549b082212fd1bbd8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-3-configure-a-one-way-file-send-port"></a><span data-ttu-id="1e7b0-102">Étape 3 : Configurer un Port d’envoi FILE unidirectionnel</span><span class="sxs-lookup"><span data-stu-id="1e7b0-102">Step 3: Configure a One-way FILE Send Port</span></span>
<span data-ttu-id="1e7b0-103">Dans cette étape, vous configurez un port d’envoi FILE unidirectionnel qui consomme le message de réponse reçu de l’interface REST et le copie dans un emplacement de fichier.</span><span class="sxs-lookup"><span data-stu-id="1e7b0-103">In this step you configure a one-way FILE send port that consumes the response message received from the REST interface and copies it to a file location.</span></span>  
  
### <a name="to-configure-a-file-send-port"></a><span data-ttu-id="1e7b0-104">Pour configurer un port d’envoi FILE</span><span class="sxs-lookup"><span data-stu-id="1e7b0-104">To configure a FILE send port</span></span>  
  
1.  <span data-ttu-id="1e7b0-105">À partir de la Console Administration de BizTalk Server, sous la **BizTalk Application 1** nœud, avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **statique Port d’envoi unidirectionnel**.</span><span class="sxs-lookup"><span data-stu-id="1e7b0-105">From BizTalk Server Administration Console, under the **BizTalk Application 1** node, right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port**.</span></span>  
  
2.  <span data-ttu-id="1e7b0-106">Sous l’onglet Général, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="1e7b0-106">On the General tab, do the following:</span></span>  
  
    |<span data-ttu-id="1e7b0-107">Utiliser</span><span class="sxs-lookup"><span data-stu-id="1e7b0-107">Use this</span></span>|<span data-ttu-id="1e7b0-108">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="1e7b0-108">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="1e7b0-109">**Nom**</span><span class="sxs-lookup"><span data-stu-id="1e7b0-109">**Name**</span></span>|<span data-ttu-id="1e7b0-110">Type **SendPortOutAzureMarketPlaceData**.</span><span class="sxs-lookup"><span data-stu-id="1e7b0-110">Type **SendPortOutAzureMarketPlaceData**.</span></span>|  
    |<span data-ttu-id="1e7b0-111">**Type**</span><span class="sxs-lookup"><span data-stu-id="1e7b0-111">**Type**</span></span>|<span data-ttu-id="1e7b0-112">Sélectionnez **fichier**.</span><span class="sxs-lookup"><span data-stu-id="1e7b0-112">Select **FILE**.</span></span>|  
    |<span data-ttu-id="1e7b0-113">**Gestionnaire d’envoi**</span><span class="sxs-lookup"><span data-stu-id="1e7b0-113">**Send handler**</span></span>|<span data-ttu-id="1e7b0-114">Sélectionnez **BizTalkServerApplication**.</span><span class="sxs-lookup"><span data-stu-id="1e7b0-114">Select **BizTalkServerApplication**.</span></span>|  
    |<span data-ttu-id="1e7b0-115">**Pipeline d’envoi**</span><span class="sxs-lookup"><span data-stu-id="1e7b0-115">**Send pipeline**</span></span>|<span data-ttu-id="1e7b0-116">Sélectionnez **PassThruTransmit**.</span><span class="sxs-lookup"><span data-stu-id="1e7b0-116">Select **PassThruTransmit**.</span></span>|  
  
     <span data-ttu-id="1e7b0-117">Cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="1e7b0-117">Click **Configure**.</span></span>  
  
3.  <span data-ttu-id="1e7b0-118">Dans la boîte de dialogue Propriétés du transport FILE, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="1e7b0-118">From File Transport Properties, do the following:</span></span>  
  
    |<span data-ttu-id="1e7b0-119">Utiliser</span><span class="sxs-lookup"><span data-stu-id="1e7b0-119">Use this</span></span>|<span data-ttu-id="1e7b0-120">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="1e7b0-120">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="1e7b0-121">**Dossier de réception**</span><span class="sxs-lookup"><span data-stu-id="1e7b0-121">**Receive folder**</span></span>|<span data-ttu-id="1e7b0-122">Tapez un emplacement dans lequel [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] copie le message de réponse.</span><span class="sxs-lookup"><span data-stu-id="1e7b0-122">Type a location where [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] copies the response message.</span></span>|  
    |<span data-ttu-id="1e7b0-123">**Nom de fichier**</span><span class="sxs-lookup"><span data-stu-id="1e7b0-123">**File name**</span></span>|<span data-ttu-id="1e7b0-124">Conserver`%MessageID%.xml`</span><span class="sxs-lookup"><span data-stu-id="1e7b0-124">Retain `%MessageID%.xml`</span></span>|  
  
4.  <span data-ttu-id="1e7b0-125">Sur le **filtres** onglet, spécifiez le filtre pour utiliser tous les messages sont écrits dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] base de données de la boîte de Message par le port de réception que vous avez créé dans [étape 2 : configurer un Port d’envoi de WCF-WebHttp bidirectionnel](../core/step-2-configure-a-two-way-wcf-webhttp-send-port.md).</span><span class="sxs-lookup"><span data-stu-id="1e7b0-125">On the **Filters** tab, specify the filter to consume all messages that are written to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Message Box database by the receive port you created in [Step 2: Configure a Two-way WCF-WebHttp Send Port](../core/step-2-configure-a-two-way-wcf-webhttp-send-port.md).</span></span>  
  
    |||  
    |-|-|  
    |<span data-ttu-id="1e7b0-126">**Propriété**</span><span class="sxs-lookup"><span data-stu-id="1e7b0-126">**Property**</span></span>|<span data-ttu-id="1e7b0-127">La valeur **BTS. SPName**</span><span class="sxs-lookup"><span data-stu-id="1e7b0-127">Set to **BTS.SPName**</span></span>|  
    |<span data-ttu-id="1e7b0-128">**Opérateur**</span><span class="sxs-lookup"><span data-stu-id="1e7b0-128">**Operator**</span></span>|<span data-ttu-id="1e7b0-129">La valeur**==**</span><span class="sxs-lookup"><span data-stu-id="1e7b0-129">Set to **==**</span></span>|  
    |<span data-ttu-id="1e7b0-130">**Valeur**</span><span class="sxs-lookup"><span data-stu-id="1e7b0-130">**Value**</span></span>|<span data-ttu-id="1e7b0-131">La valeur`SendPortRESTAzureMarketPlace`</span><span class="sxs-lookup"><span data-stu-id="1e7b0-131">Set to `SendPortRESTAzureMarketPlace`</span></span>|  
  
5.  <span data-ttu-id="1e7b0-132">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="1e7b0-132">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e7b0-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1e7b0-133">See Also</span></span>  
 [<span data-ttu-id="1e7b0-134">Didacticiel de 5 : Appeler une Interface REST à l’aide de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="1e7b0-134">Tutorial 5: Invoking a REST Interface Using BizTalk Server</span></span>](../core/tutorial-5-invoking-a-rest-interface-using-biztalk-server.md)