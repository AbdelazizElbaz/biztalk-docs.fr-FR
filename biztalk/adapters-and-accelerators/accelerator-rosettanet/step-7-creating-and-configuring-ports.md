---
title: "Étape 7 : Création et configuration des Ports | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- private process tutorial, creating ports
- private process tutorial, configuring ports
ms.assetid: c00344c6-506a-4560-a948-e5fed2b9fd58
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7c93f7c07f92c7517dbc84403747da869e0d4ceb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-7-creating-and-configuring-ports"></a><span data-ttu-id="a4637-102">Étape 7 : Création et configuration des Ports</span><span class="sxs-lookup"><span data-stu-id="a4637-102">Step 7: Creating and Configuring Ports</span></span>
<span data-ttu-id="a4637-103">Dans cette étape, vous créez et configurez les ports que vous utilisez pour communiquer avec les processus d’entreprise.</span><span class="sxs-lookup"><span data-stu-id="a4637-103">In this step, you create and configure the ports you use to communicate with business processes.</span></span> <span data-ttu-id="a4637-104">Chaque port a un type, la direction et la propriété de liaison.</span><span class="sxs-lookup"><span data-stu-id="a4637-104">Each port has a type, direction, and binding property.</span></span> <span data-ttu-id="a4637-105">Ces propriétés d’établir la direction et le modèle de communication, l’emplacement d’où le message est envoyé ou reçu, et comment la communication se produit.</span><span class="sxs-lookup"><span data-stu-id="a4637-105">These properties establish the direction and pattern of communication, the location of where the message is sent or received, and how the communication occurs.</span></span>  
  
### <a name="to-create-a-logical-send-port"></a><span data-ttu-id="a4637-106">Pour créer un port d’envoi logique</span><span class="sxs-lookup"><span data-stu-id="a4637-106">To create a logical send port</span></span>  
  
1.  <span data-ttu-id="a4637-107">Dans Visual Studio, à partir de la boîte à outils, faites glisser le **Port** forme sur l’aire de conception d’orchestration et déposez-la sur la **Surface du Port** pour ouvrir le **Assistant Configuration du Port**.</span><span class="sxs-lookup"><span data-stu-id="a4637-107">In Visual Studio, from the Toolbox, drag the **Port** shape to the orchestration design surface and drop it on the **Port Surface** to open the **Port Configuration Wizard**.</span></span>  
  
2.  <span data-ttu-id="a4637-108">Sur le **Assistant Configuration du Port** , cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="a4637-108">On the **Port Configuration Wizard** page, click **Next**.</span></span>  
  
3.  <span data-ttu-id="a4637-109">Sur le **propriétés de Port** page, dans le **nom** , tapez **ContosoSQLReqResponsePort**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="a4637-109">On the **Port Properties** page, in the **Name** box, type **ContosoSQLReqResponsePort**, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="a4637-110">Sur le **sélectionner un Type de Port** page, dans le **nom du Type de Port** , tapez **ContosoSQLReqResponsePortName**.</span><span class="sxs-lookup"><span data-stu-id="a4637-110">On the **Select a Port Type** page, in the **Port Type Name** box, type **ContosoSQLReqResponsePortName**.</span></span>  
  
5.  <span data-ttu-id="a4637-111">Pour **modèle de Communication**, sélectionnez **demande-réponse**.</span><span class="sxs-lookup"><span data-stu-id="a4637-111">For **Communication Pattern**, select **Request-Response**.</span></span>  
  
6.  <span data-ttu-id="a4637-112">Pour **Restrictions d’accès**, sélectionnez **interne - limité au projet**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="a4637-112">For **Access Restrictions**, select **Internal - limited to this project**, and then click **Next**.</span></span>  
  
7.  <span data-ttu-id="a4637-113">Sur le **liaison de Port** page, sélectionnez **puis-je envoyer une demande et recevoir une réponse**, laissez le **liaison de Port** option la valeur **spécifier plus tard**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="a4637-113">On the **Port Binding** page, select **I'll be sending a request and receiving a response**, leave the **Port Binding** option set to **Specify Later**, and then click **Next**.</span></span>  
  
8.  <span data-ttu-id="a4637-114">Cliquez sur **Terminer** pour créer le port.</span><span class="sxs-lookup"><span data-stu-id="a4637-114">Click **Finish** to create the port.</span></span>  
  
### <a name="to-change-the-variable-type-for-the-orchestration-ports"></a><span data-ttu-id="a4637-115">Pour modifier le type de variable pour les ports d’orchestration</span><span class="sxs-lookup"><span data-stu-id="a4637-115">To change the variable type for the orchestration ports</span></span>  
  
1.  <span data-ttu-id="a4637-116">Dans la vue Orchestration, développez **Types**, développez **Types de ports**, développez **ContosoSQLReqResponsePortName**, développez **Operation_1**, puis sélectionnez **demande**.</span><span class="sxs-lookup"><span data-stu-id="a4637-116">In Orchestration View, expand **Types**, expand **Port Types**, expand **ContosoSQLReqResponsePortName**, expand **Operation_1**, and then select **Request**.</span></span>  
  
2.  <span data-ttu-id="a4637-117">Dans la fenêtre Propriétés, sélectionnez le **Type de Message** propriétés, développez **schémas** puis cliquez sur  **\<sélectionner dans l’assembly référencé >**.</span><span class="sxs-lookup"><span data-stu-id="a4637-117">In the Properties window, select the **Message Type** property, expand **Schemas** and then click **\<Select from referenced assembly>**.</span></span>  
  
3.  <span data-ttu-id="a4637-118">Dans la boîte de dialogue Sélectionner le Type d’artefact, cliquez sur **ContosoPriceAndAvailability**.</span><span class="sxs-lookup"><span data-stu-id="a4637-118">In the Select Artifact Type dialog box, click **ContosoPriceAndAvailability**.</span></span>  
  
4.  <span data-ttu-id="a4637-119">Dans le volet droit, sélectionnez **rootPriceRequest**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="a4637-119">In the right pane, select **rootPriceRequest**, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="a4637-120">Dans Vue Orchestration, sous **Operation_1**, sélectionnez **réponse** pour le **ContosoSQLReqResponsePortName** type de port.</span><span class="sxs-lookup"><span data-stu-id="a4637-120">In Orchestration View, under **Operation_1**, select **Response** for the **ContosoSQLReqResponsePortName** port type.</span></span>  
  
6.  <span data-ttu-id="a4637-121">Dans la fenêtre Propriétés, sélectionnez le **Type de Message** propriétés, développez **schémas** puis cliquez sur \< **sélectionner dans l’assembly référencé >**.</span><span class="sxs-lookup"><span data-stu-id="a4637-121">In the Properties window, select the **Message Type** property, expand **Schemas** and then click \<**Select from referenced assembly>**.</span></span>  
  
7.  <span data-ttu-id="a4637-122">Dans le **sélectionner le Type d’artefact** boîte de dialogue, cliquez sur **ContosoPriceAndAvailability**.</span><span class="sxs-lookup"><span data-stu-id="a4637-122">In the **Select Artifact Type** dialog box, click **ContosoPriceAndAvailability**.</span></span>  
  
8.  <span data-ttu-id="a4637-123">Dans le volet droit, sélectionnez **rootPriceResponse**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="a4637-123">In the right pane, select **rootPriceResponse**, and then click **OK**.</span></span>  
  
### <a name="to-connect-the-ports-to-the-receive-shapes"></a><span data-ttu-id="a4637-124">Pour connecter les ports aux formes réception</span><span class="sxs-lookup"><span data-stu-id="a4637-124">To connect the ports to the Receive shapes</span></span>  
  
1.  <span data-ttu-id="a4637-125">Sur l’aire de conception d’orchestration, sélectionnez la **Send_1** forme.</span><span class="sxs-lookup"><span data-stu-id="a4637-125">On the orchestration design surface, select the **Send_1** shape.</span></span>  
  
2.  <span data-ttu-id="a4637-126">Dans la fenêtre Propriétés, sélectionnez le **Message** propriété, puis sélectionnez **Contoso3A2RequestMessage** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="a4637-126">In the Properties window, select the **Message** property, and then select **Contoso3A2RequestMessage** from the drop-down list.</span></span>  
  
3.  <span data-ttu-id="a4637-127">Se connecter le **ContosoSQLReqResponsePort** en activant la poignée verte en regard du **demande** étiquette et en le faisant glisser sur la poignée verte la **Send_1** forme.</span><span class="sxs-lookup"><span data-stu-id="a4637-127">Connect the **ContosoSQLReqResponsePort** by selecting the green handle next to the **Request** label and dragging it to the green handle on the **Send_1** shape.</span></span>  
  
4.  <span data-ttu-id="a4637-128">Sur l’aire de conception d’orchestration, sélectionnez la **Receive_1** forme.</span><span class="sxs-lookup"><span data-stu-id="a4637-128">On the orchestration design surface, select the **Receive_1** shape.</span></span>  
  
5.  <span data-ttu-id="a4637-129">Dans la fenêtre Propriétés, sélectionnez le **Message** propriété, puis sélectionnez **Contoso3A2ResponseMessage** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="a4637-129">In the Properties window, select the **Message** property, and then select **Contoso3A2ResponseMessage** from the drop-down list.</span></span>  
  
6.  <span data-ttu-id="a4637-130">Se connecter le **ContosoSQLReqResponsePort** en activant la poignée verte en regard du **réponse** étiquette et en le faisant glisser sur la poignée verte la **Receive_1** forme.</span><span class="sxs-lookup"><span data-stu-id="a4637-130">Connect the **ContosoSQLReqResponsePort** by selecting the green handle next to the **Response** label and dragging it to the green handle on the **Receive_1** shape.</span></span>  
  
7.  <span data-ttu-id="a4637-131">Dans le **fichier** Menu, cliquez sur **Enregistrer tout**.</span><span class="sxs-lookup"><span data-stu-id="a4637-131">In the **File** Menu, click **Save All**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4637-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a4637-132">See Also</span></span>  
 [<span data-ttu-id="a4637-133">Étape 8 : Création et déploiement de l’Orchestration Contoso</span><span class="sxs-lookup"><span data-stu-id="a4637-133">Step 8: Building and Deploying the Contoso Orchestration</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-8-building-and-deploying-the-contoso-orchestration.md)