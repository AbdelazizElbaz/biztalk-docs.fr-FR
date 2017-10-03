---
title: "Création de Ports | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ports, creating
- receive ports
- creating, send ports
- creating, ports
- Configuration database [BizTalk Server], connecting
- receive ports, creating
- send ports
- send ports, creating
ms.assetid: 4f99f884-5b84-4f9f-8cec-dd5da259ba7f
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fdb7ff7d93b754285e9ed0eb627ca24b113bd2a5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="creating-ports"></a><span data-ttu-id="b6ab2-102">Création de ports</span><span class="sxs-lookup"><span data-stu-id="b6ab2-102">Creating Ports</span></span>
<span data-ttu-id="b6ab2-103">Les procédures suivantes permettent de créer des ports d'envoi et de réception [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour l'authentification unique.</span><span class="sxs-lookup"><span data-stu-id="b6ab2-103">Use the following procedures to create [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] send and receive ports for Single Sign-on.</span></span>  
  
## <a name="creating-a-send-port"></a><span data-ttu-id="b6ab2-104">Création d'un port d'envoi</span><span class="sxs-lookup"><span data-stu-id="b6ab2-104">Creating a Send Port</span></span>  
  
#### <a name="to-create-a-send-port"></a><span data-ttu-id="b6ab2-105">Pour créer un port d’envoi</span><span class="sxs-lookup"><span data-stu-id="b6ab2-105">To create a send port</span></span>  
  
1.  <span data-ttu-id="b6ab2-106">Dans la Console Administration de BizTalk Server, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, puis développez souhaité application.</span><span class="sxs-lookup"><span data-stu-id="b6ab2-106">In the BizTalk Server Administration Console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, and then expand the desired application.</span></span>  
  
2.  <span data-ttu-id="b6ab2-107">Avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi statique avec sollicitation-réponse**.</span><span class="sxs-lookup"><span data-stu-id="b6ab2-107">Right-click **Send Ports**, point to **New**, and then click **Static Solicit-Response Send Port**.</span></span>  
  
3.  <span data-ttu-id="b6ab2-108">Dans le **propriétés de Port d’envoi** boîte de dialogue zone, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="b6ab2-108">In the **Send Port Properties** dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="b6ab2-109">Tapez un nom pour le port d’envoi, par exemple, `SSOSendToPeopleSoft`.</span><span class="sxs-lookup"><span data-stu-id="b6ab2-109">Type a name for the send port, for example, `SSOSendToPeopleSoft`.</span></span>  
  
    2.  <span data-ttu-id="b6ab2-110">À partir de la **Type** la liste déroulante, sélectionnez **PeopleSoft**.</span><span class="sxs-lookup"><span data-stu-id="b6ab2-110">From the **Type** drop-down list, select **PeopleSoft**.</span></span>  
  
    3.  <span data-ttu-id="b6ab2-111">À partir de la **Gestionnaire d’envoi** liste déroulante, sélectionnez l’URI.</span><span class="sxs-lookup"><span data-stu-id="b6ab2-111">From the **Send handler** drop-down list, select the URI.</span></span>  
  
    4.  <span data-ttu-id="b6ab2-112">Dans la liste déroulante Pipeline d’envoi, sélectionnez **Microsoft.BizTalk.DefaultPipelines.XMLTransmit**.</span><span class="sxs-lookup"><span data-stu-id="b6ab2-112">From the Send Pipeline drop-down list, select **Microsoft.BizTalk.DefaultPipelines.XMLTransmit**.</span></span>  
  
    5.  <span data-ttu-id="b6ab2-113">À partir de la **Pipeline de réception** la liste déroulante, sélectionnez **Microsoft.BizTalk.DefaultPiplelines.XMLReceive**.</span><span class="sxs-lookup"><span data-stu-id="b6ab2-113">From the **Receive Pipeline** drop-down list, select **Microsoft.BizTalk.DefaultPiplelines.XMLReceive**.</span></span>  
  
    6.  <span data-ttu-id="b6ab2-114">Cliquez sur **configurer** pour configurer le port d’envoi.</span><span class="sxs-lookup"><span data-stu-id="b6ab2-114">Click **Configure** to configure the send port.</span></span>  
  
4.  <span data-ttu-id="b6ab2-115">Dans le **propriétés du Transport PeopleSoft** boîte de dialogue zone, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="b6ab2-115">In the **PeopleSoft Transport Properties** dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="b6ab2-116">Développez **propriétés obligatoires de l’adaptateur**, puis entrez **chemin d’accès au serveur d’Application**, **JAVA_HOME**, **nom d’utilisateur**,  **mot de passe**et le fichier Jar pour la connexion au système Peoplesoft.</span><span class="sxs-lookup"><span data-stu-id="b6ab2-116">Expand **Adapter Required Properties**, and enter **Application Server Path**, **JAVA_HOME**, **user name**, **password**, and the Jar file for connecting into the Peoplesoft system.</span></span>  
  
         <span data-ttu-id="b6ab2-117">Il n'est pas nécessaire de définir les informations de connexion.</span><span class="sxs-lookup"><span data-stu-id="b6ab2-117">You do not have to set the logon information.</span></span>  
  
    2.  <span data-ttu-id="b6ab2-118">Dans la liste, sélectionnez l'application associée SSO que vous avez créée pour représenter le système PeopleSoft.</span><span class="sxs-lookup"><span data-stu-id="b6ab2-118">In the list, select the SSO affiliate application you created to represent the PeopleSoft system.</span></span>  
  
    3.  <span data-ttu-id="b6ab2-119">Pour **utiliser SSO**, sélectionnez **Oui**.</span><span class="sxs-lookup"><span data-stu-id="b6ab2-119">For **Use SSO**, select **Yes**.</span></span>  
  
    4.  <span data-ttu-id="b6ab2-120">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="b6ab2-120">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="b6ab2-121">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="b6ab2-121">Click **OK**.</span></span>  
  
## <a name="creating-a-receive-port"></a><span data-ttu-id="b6ab2-122">Création d'un port de réception</span><span class="sxs-lookup"><span data-stu-id="b6ab2-122">Creating a Receive Port</span></span>  
  
#### <a name="to-create-a-receive-port"></a><span data-ttu-id="b6ab2-123">Pour créer un port de réception</span><span class="sxs-lookup"><span data-stu-id="b6ab2-123">To create a receive port</span></span>  
  
1.  <span data-ttu-id="b6ab2-124">Dans la Console Administration de BizTalk Server, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, puis développez souhaité application.</span><span class="sxs-lookup"><span data-stu-id="b6ab2-124">In the BizTalk Server Administration Console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, and then expand the desired application.</span></span>  
  
2.  <span data-ttu-id="b6ab2-125">Avec le bouton droit **Ports de réception**, pointez sur **nouveau**, puis cliquez sur **Ports de réception unidirectionnels**.</span><span class="sxs-lookup"><span data-stu-id="b6ab2-125">Right-click **Receive Ports**, point to **New**, and then click **One-way Receive Ports**.</span></span>  
  
3.  <span data-ttu-id="b6ab2-126">Dans le **propriétés du Port de réception** fenêtre, dans le **général** page, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="b6ab2-126">In the **Receive Port Properties** window, on the **General** page, do the following:</span></span>  
  
    1.  <span data-ttu-id="b6ab2-127">Dans le **nom** , tapez `ReceiveFromTIBCOEMS`.</span><span class="sxs-lookup"><span data-stu-id="b6ab2-127">In the **Name** field, type `ReceiveFromTIBCOEMS`.</span></span>  
  
    2.  <span data-ttu-id="b6ab2-128">Dans le **authentification** zone de groupe, spécifiez le traitement des messages lors de l’utilisation de l’authentification.</span><span class="sxs-lookup"><span data-stu-id="b6ab2-128">In the **Authentication** group box, specify how messages are handled when using authentication.</span></span>  
  
    3.  <span data-ttu-id="b6ab2-129">Sélectionnez le **activer le routage pour les messages ayant échoué** case à cocher.</span><span class="sxs-lookup"><span data-stu-id="b6ab2-129">Select the **Enable routing for failed messages** checkbox.</span></span>  
  
4.  <span data-ttu-id="b6ab2-130">Sur le **emplacements de réception** page, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="b6ab2-130">On the **Receive Locations** page, do the following:</span></span>  
  
    1.  <span data-ttu-id="b6ab2-131">Cliquez sur **Nouveau**.</span><span class="sxs-lookup"><span data-stu-id="b6ab2-131">Click **New**.</span></span>  
  
    2.  <span data-ttu-id="b6ab2-132">Dans le **emplacements de réception** fenêtre, dans le **général** , tapez le **nom** l’emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="b6ab2-132">In the **Receive Locations** window, on the **General** page, type the **Name** of the receive location.</span></span>  
  
    3.  <span data-ttu-id="b6ab2-133">À partir de la **Type** liste déroulante, sélectionnez le type de transport et à partir de la **Gestionnaire de réception** liste déroulante, sélectionnez l’adresse de transport.</span><span class="sxs-lookup"><span data-stu-id="b6ab2-133">From the **Type** drop-down list, select the transport type, and from the **Receive handler** drop-down list, select the transport address.</span></span>  
  
    4.  <span data-ttu-id="b6ab2-134">À partir de la **pipeline de réception** liste déroulante, sélectionnez le pipeline de réception.</span><span class="sxs-lookup"><span data-stu-id="b6ab2-134">From the **Receive pipeline** drop-down list, select the receive pipeline.</span></span>  
  
    5.  <span data-ttu-id="b6ab2-135">Sur le **planification** page, sélectionnez le **date de début** et **date de fin** pour restreindre la réception des documents.</span><span class="sxs-lookup"><span data-stu-id="b6ab2-135">On the **Schedule** page, select the **Start date** and the **End date** to restrict receiving documents.</span></span>  
  
    6.  <span data-ttu-id="b6ab2-136">Sélectionnez le **activer la fenêtre de service** case à cocher.</span><span class="sxs-lookup"><span data-stu-id="b6ab2-136">Select the **Enable service window** checkbox.</span></span>  
  
    7.  <span data-ttu-id="b6ab2-137">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="b6ab2-137">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="b6ab2-138">Sur le **mappages entrants** , sélectionnez les mappages entrants pour transformer les documents sur le port sélectionné.</span><span class="sxs-lookup"><span data-stu-id="b6ab2-138">On the **Inbound Maps** page, select the inbound maps for transforming documents on the selected port.</span></span>  
  
6.  <span data-ttu-id="b6ab2-139">Sur le **suivi** , sélectionnez le suivi des propriétés de message et le suivi des corps de message souhaité.</span><span class="sxs-lookup"><span data-stu-id="b6ab2-139">On the **Tracking** page, select the desired tracking message bodies and tracking message properties.</span></span>  
  
7.  <span data-ttu-id="b6ab2-140">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="b6ab2-140">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6ab2-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b6ab2-141">See Also</span></span>  
 [<span data-ttu-id="b6ab2-142">À l’aide de l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="b6ab2-142">Using Single Sign-On</span></span>](../core/using-single-sign-on2.md)