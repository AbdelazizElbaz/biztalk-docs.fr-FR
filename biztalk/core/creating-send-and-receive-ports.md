---
title: "Création d’envoi et Ports de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JD Edwards OneWorld adapters, receive ports
- adapters [JD Edwards OneWorld adapters], receive ports
- creating, receive ports [JD Edwards OneWorld adapters]
- send ports, creating [JD Edwards OneWorld adapters]
- adapters [JD Edwards OneWorld adapters], send ports
- adapters [JD Edwards OneWorld adapters], transport properties
- JD Edwards OneWorld adapters, send ports
- JD Edwards OneWorld adapters, transport properties
- receive ports, creating [JD Edwards OneWorld adapters]
- creating, send ports [JD Edwards OneWorld adapters]
ms.assetid: fb4ca8b1-40d9-4beb-a791-554086f8ca98
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 217a1d79dc4079c8f092985e00a1cd5636788e7b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="creating-send-and-receive-ports"></a><span data-ttu-id="e9c60-102">Création d’envoi et Ports de réception</span><span class="sxs-lookup"><span data-stu-id="e9c60-102">Creating Send and Receive Ports</span></span>
<span data-ttu-id="e9c60-103">Les procédures suivantes permettent de créer des ports d'envoi et de réception [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour l'adaptateur Microsoft BizTalk pour JD Edwards OneWorld.</span><span class="sxs-lookup"><span data-stu-id="e9c60-103">Use the following procedures to create [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] send and receive ports for BizTalk Adapter for JD Edwards OneWorld.</span></span>  
  
## <a name="creating-a-port"></a><span data-ttu-id="e9c60-104">Création d'un port</span><span class="sxs-lookup"><span data-stu-id="e9c60-104">Creating a Port</span></span>  
  
#### <a name="to-create-a-send-port"></a><span data-ttu-id="e9c60-105">Pour créer un port d’envoi</span><span class="sxs-lookup"><span data-stu-id="e9c60-105">To create a send port</span></span>  
  
1.  <span data-ttu-id="e9c60-106">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft BizTalk Server**, puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="e9c60-106">Click **Start**, point to **All Programs**, point to **Microsoft BizTalk Server**, and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="e9c60-107">Dans la console Administration de BizTalk Server, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, puis développez le application pour laquelle vous souhaitez créer un port d’envoi.</span><span class="sxs-lookup"><span data-stu-id="e9c60-107">In the BizTalk Server Administration console, expand **BizTalk Server Administration**, expand **BizTalk Group**, and expand **Applications**, and then expand the application for which you want to create a send port.</span></span>  
  
3.  <span data-ttu-id="e9c60-108">Avec le bouton droit **Ports d’envoi** et cliquez sur **nouveau**, puis cliquez sur **Port statique avec sollicitation-réponse**.</span><span class="sxs-lookup"><span data-stu-id="e9c60-108">Right-click **Send Ports** and click **New**, and then click **Static Solicit-Response Port**.</span></span>  
  
4.  <span data-ttu-id="e9c60-109">Dans le **propriétés de Port d’envoi** boîte de dialogue zone, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="e9c60-109">In the **Send Port Properties** dialog box, do the following:</span></span>  
  
    -   <span data-ttu-id="e9c60-110">Dans le **nom** , tapez le nom du port d’envoi (par exemple, `SSOSendToJDE OneWorld`).</span><span class="sxs-lookup"><span data-stu-id="e9c60-110">In the **Name** box, type a send port name (for example, `SSOSendToJDE OneWorld`).</span></span>  
  
    -   <span data-ttu-id="e9c60-111">À partir de la **Type** la liste déroulante, sélectionnez **JDEdwards**.</span><span class="sxs-lookup"><span data-stu-id="e9c60-111">From the **Type** drop-down list, select **JDEdwards**.</span></span>  
  
    -   <span data-ttu-id="e9c60-112">À partir de la **Gestionnaire d’envoi** liste déroulante, sélectionnez l’adresse du Gestionnaire d’envoi.</span><span class="sxs-lookup"><span data-stu-id="e9c60-112">From the **Send handler** drop-down list, select the send handler address.</span></span>  
  
    -   <span data-ttu-id="e9c60-113">Pour le **Pipeline d’envoi**, sélectionnez **Microsoft.BizTalk.DefaultPipelines.XMLTransmit**.</span><span class="sxs-lookup"><span data-stu-id="e9c60-113">For the **Send Pipeline**, select **Microsoft.BizTalk.DefaultPipelines.XMLTransmit**.</span></span>  
  
    -   <span data-ttu-id="e9c60-114">Pour le **Pipeline de réception**, sélectionnez **Microsoft.BizTalk.DefaultPiplelines.XMLReceive**.</span><span class="sxs-lookup"><span data-stu-id="e9c60-114">For the **Receive Pipeline**, select **Microsoft.BizTalk.DefaultPiplelines.XMLReceive**.</span></span>  
  
5.  <span data-ttu-id="e9c60-115">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="e9c60-115">Click **OK**.</span></span>  
  
## <a name="creating-a-receive-port"></a><span data-ttu-id="e9c60-116">Création d'un port de réception</span><span class="sxs-lookup"><span data-stu-id="e9c60-116">Creating a Receive Port</span></span>  
  
#### <a name="to-create-a-receive-port"></a><span data-ttu-id="e9c60-117">Pour créer un port de réception</span><span class="sxs-lookup"><span data-stu-id="e9c60-117">To create a receive port</span></span>  
  
1.  <span data-ttu-id="e9c60-118">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft BizTalk Server**, puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="e9c60-118">Click **Start**, point to **All Programs**, point to **Microsoft BizTalk Server**, and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="e9c60-119">Dans la console Administration de BizTalk Server, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, puis développez le application pour laquelle vous souhaitez créer un port d’envoi.</span><span class="sxs-lookup"><span data-stu-id="e9c60-119">In the BizTalk Server Administration console, expand **BizTalk Server Administration**, expand **BizTalk Group**, and expand **Applications**, and then expand the application for which you want to create a send port.</span></span>  
  
3.  <span data-ttu-id="e9c60-120">Avec le bouton droit **Ports de réception** et cliquez sur **nouveau**, puis cliquez sur **Port de réception unidirectionnel**.</span><span class="sxs-lookup"><span data-stu-id="e9c60-120">Right-click **Receive Ports** and click **New**, and then click **One-way Receive Port**.</span></span>  
  
     <span data-ttu-id="e9c60-121">Sur le **propriétés du Port de réception unidirectionnel** écran, dans le **nom** , tapez `ReceiveFromHttp`, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="e9c60-121">On the **One-Way Receive Port Properties** screen, in the **Name** field, type `ReceiveFromHttp`, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="e9c60-122">Entrez les informations suivantes dans le **propriétés du Port de réception unidirectionnel** fenêtre :</span><span class="sxs-lookup"><span data-stu-id="e9c60-122">Enter the following information in the **One-way Receive Port Properties** window:</span></span>  
  
    -   <span data-ttu-id="e9c60-123">Dans le **nom** , tapez `ReceiveFromHTTP`.</span><span class="sxs-lookup"><span data-stu-id="e9c60-123">In the **Name** field, type `ReceiveFromHTTP`.</span></span>  
  
    -   <span data-ttu-id="e9c60-124">Pour le **Type de Transport**, sélectionnez **HTTP**.</span><span class="sxs-lookup"><span data-stu-id="e9c60-124">For the **Transport Type**, select **HTTP**.</span></span>  
  
5.  <span data-ttu-id="e9c60-125">Cliquez sur le bouton représentant des points de suspension (...) dans l'adresse (URI).</span><span class="sxs-lookup"><span data-stu-id="e9c60-125">Click the ellipsis (…) button in the address (URI).</span></span>  
  
     ![](../core/media/siebeladapter-32-ssodemo-httptransport.gif "SiebelAdapter_32_SSODemo_HTTPTransport")  
  
    1.  <span data-ttu-id="e9c60-126">Définissez le répertoire virtuel assorti de l'extension ISAPI, /mySSODemo/BTSHTTPReceive.dll.</span><span class="sxs-lookup"><span data-stu-id="e9c60-126">Set the Virtual directory plus ISAPI extension, /mySSODemo/BTSHTTPReceive.dll.</span></span>  
  
    2.  <span data-ttu-id="e9c60-127">Sélectionnez **un descripteur de corrélation de retour en cas de réussite**.</span><span class="sxs-lookup"><span data-stu-id="e9c60-127">Select **Return correlation handle on success**.</span></span>  
  
    3.  <span data-ttu-id="e9c60-128">Sélectionnez **utilisez Single Sign-On**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="e9c60-128">Select **Use Single Sign-On**, and then click **OK**.</span></span>  
  
6.  <span data-ttu-id="e9c60-129">Dans le **Gestionnaire de réception** la liste déroulante, sélectionnez **BizTalkServerIsolatedHost**.</span><span class="sxs-lookup"><span data-stu-id="e9c60-129">In the **Receive Handler** drop-down list, select **BizTalkServerIsolatedHost**.</span></span>  
  
     ![](../core/media/siebeladapter-33-ssodemo-receivelocationproperty.gif "SiebelAdapter_33_SSODemo_ReceiveLocationProperty")  
  
7.  <span data-ttu-id="e9c60-130">Pour le **Pipeline de réception**, sélectionnez **Microsoft.BizTalk.DefaultPiplelines.XMLReceive**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="e9c60-130">For the **Receive Pipeline**, select **Microsoft.BizTalk.DefaultPiplelines.XMLReceive**, and then click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9c60-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e9c60-131">See Also</span></span>  
 <span data-ttu-id="e9c60-132">[Création de gestionnaires de JD Edwards OneWorld envoi](../core/creating-jd-edwards-oneworld-send-handlers.md) </span><span class="sxs-lookup"><span data-stu-id="e9c60-132">[Creating JD Edwards OneWorld Send Handlers](../core/creating-jd-edwards-oneworld-send-handlers.md) </span></span>  
 <span data-ttu-id="e9c60-133">[Comment définir les propriétés de JD Edwards OneWorld Transport](../core/how-to-set-jd-edwards-oneworld-transport-properties.md) </span><span class="sxs-lookup"><span data-stu-id="e9c60-133">[How to Set JD Edwards OneWorld Transport Properties](../core/how-to-set-jd-edwards-oneworld-transport-properties.md) </span></span>  
 [<span data-ttu-id="e9c60-134">À l’aide de l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="e9c60-134">Using Single Sign-On</span></span>](../core/using-single-sign-on3.md)