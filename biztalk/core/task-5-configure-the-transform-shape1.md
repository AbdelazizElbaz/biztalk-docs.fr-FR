---
title: "Tâche 5 : Configurer la transformation Shape1 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 93a73fd2-0f34-4681-8aed-7d54d69c86d3
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e76313ca87ad3138da83480b46a38a802d89ff15
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="task-5-configure-the-transform-shape"></a><span data-ttu-id="47a86-102">Tâche 5 : Configurer la forme Transformer</span><span class="sxs-lookup"><span data-stu-id="47a86-102">Task 5: Configure the Transform Shape</span></span>
<span data-ttu-id="47a86-103">Les procédures suivantes permettent de configurer la forme Transformer.</span><span class="sxs-lookup"><span data-stu-id="47a86-103">Use the following procedure to configure the Transform shape.</span></span>  
  
### <a name="to-configure-the-transform-shape"></a><span data-ttu-id="47a86-104">Pour configurer la forme Transformer</span><span class="sxs-lookup"><span data-stu-id="47a86-104">To configure the Transform shape</span></span>  
  
1.  <span data-ttu-id="47a86-105">Faites glisser une forme Construire un message après ReceiveBeginDocResponse.</span><span class="sxs-lookup"><span data-stu-id="47a86-105">Drag a Construct Message shape after ReceiveBeginDocResponse.</span></span>  
  
    -   <span data-ttu-id="47a86-106">**Messages construits :** EditLineMsg</span><span class="sxs-lookup"><span data-stu-id="47a86-106">**Messages Constructed:** EditLineMsg</span></span>  
  
    -   <span data-ttu-id="47a86-107">**Nom :** ConstructEditLineMessageWithData</span><span class="sxs-lookup"><span data-stu-id="47a86-107">**Name:** ConstructEditLineMessageWithData</span></span>  
  
     <span data-ttu-id="47a86-108">Avec le bouton droit au milieu, sélectionnez **insérer une forme**, puis sélectionnez **transformer**.</span><span class="sxs-lookup"><span data-stu-id="47a86-108">Right-click in the middle, select **Insert Shape**, and then select **Transform**.</span></span>  
  
     ![](../core/media/jde-insert-shape-transform.gif "JDE_insert_shape_transform")  
  
     <span data-ttu-id="47a86-109">À l'aide de la forme Transformer, mappez les données depuis les données que vous envoyez vers les données envoyées.</span><span class="sxs-lookup"><span data-stu-id="47a86-109">Using Transform, map data from the data you are sending to the data that is sent.</span></span>  
  
     <span data-ttu-id="47a86-110">Vous devez envoyer un document (au lieu de BeginDoc) pour votre environnement de travail, avec toutes les valeurs possibles afin de construire tous les messages possibles (BeginDoc, EditLine et EndDoc).</span><span class="sxs-lookup"><span data-stu-id="47a86-110">For your work environment you would send a document (instead of BeginDoc) with all values possible allowing you to construct all possible messages, BeginDoc, EditLine, and EndDoc.</span></span> <span data-ttu-id="47a86-111">Toutefois, seules des données codées en dur sont utilisées dans cet exemple.</span><span class="sxs-lookup"><span data-stu-id="47a86-111">For this example, however, there is only hard coded data.</span></span>  
  
2.  <span data-ttu-id="47a86-112">Double-cliquez sur **Transform_1** à ouvrir.</span><span class="sxs-lookup"><span data-stu-id="47a86-112">Double-click **Transform_1** to open.</span></span>  
  
    1.  <span data-ttu-id="47a86-113">Sélectionnez Source, cliquez dans la ligne Ajouter sous **nom de la Variable** et sélectionnez **BeginDocResponseMsg**.</span><span class="sxs-lookup"><span data-stu-id="47a86-113">Select Source and click in the Add row under **Variable Name** and select **BeginDocResponseMsg**.</span></span>  
  
         ![](../core/media/jde-transform-source.gif "JDE_transform_source")  
  
    2.  <span data-ttu-id="47a86-114">Sélectionnez **Destination** et cliquez sur dans la ligne Ajouter sous **nom de la Variable**, sélectionnez **EditLineMsg**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="47a86-114">Select **Destination** and click in the Add row under **Variable Name**, select **EditLineMsg**, and click **OK**.</span></span>  
  
         ![](../core/media/jde-transform-destination.gif "JDE_transform_destination")  
  
3.  <span data-ttu-id="47a86-115">Dans l’Explorateur de solutions, double-cliquez sur **Transform_1.btm** pour ouvrir l’outil de mappage.</span><span class="sxs-lookup"><span data-stu-id="47a86-115">In the Solution Explorer, double-click **Transform_1.btm** to open the mapping tool.</span></span> <span data-ttu-id="47a86-116">Liez les quatre éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="47a86-116">Link the following four items:</span></span>  
  
    -   <span data-ttu-id="47a86-117">mnCMJobNo</span><span class="sxs-lookup"><span data-stu-id="47a86-117">mnCMJobNo</span></span>  
  
    -   <span data-ttu-id="47a86-118">szCMComputerID</span><span class="sxs-lookup"><span data-stu-id="47a86-118">szCMComputerID</span></span>  
  
    -   <span data-ttu-id="47a86-119">mnProcessID</span><span class="sxs-lookup"><span data-stu-id="47a86-119">mnProcessID</span></span>  
  
    -   <span data-ttu-id="47a86-120">mnTransactionID</span><span class="sxs-lookup"><span data-stu-id="47a86-120">mnTransactionID</span></span>  
  
     ![](../core/media/jde-example-transformmapping.gif "JDE_example_transformmapping")  
  
     <span data-ttu-id="47a86-121">Dans un souci de simplicité d'utilisation, cet exemple inclut des valeurs codées en dur.</span><span class="sxs-lookup"><span data-stu-id="47a86-121">For ease of use, this example has hardcoded values.</span></span> <span data-ttu-id="47a86-122">Cliquez sur l'élément dans le schéma de destination et définissez la valeur suivante.</span><span class="sxs-lookup"><span data-stu-id="47a86-122">Click the item in the Destination Schema and set the following Value.</span></span>  
  
     ![](../core/media/jde-hardcoded-mapping-example.gif "JDE_hardcoded_mapping_example")  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <ns0:F4211FSEditLine xmlns:ns0="http://schemas.microsoft.com/  
          [JDE://CSALES/B4200310]">  
       <ns0:cCMLineAction>A</ns0:cCMLineAction>  
       <ns0:cCMProcessEdits>1</ns0:cCMProcessEdits>  
       <ns0:cCMWriteToWFFlag>2</ns0:cCMWriteToWFFlag>  
       <ns0:szItemNo>210</ns0:szItemNo>  
       <ns0:mnQtyOrdered>1</ns0:mnQtyOrdered>  
       <ns0:cSalesTaxableYN>N</ns0:cSalesTaxableYN>  
       <ns0:szTransactionUOM>EA</ns0:szTransactionUOM>  
       <ns0:szCMProgramID>XMLInterop</ns0:szCMProgramID>  
       <ns0:szCMVersion>ZJDE0001</ns0:szCMVersion>  
    </ns0:F4211FSEditLine>  
    ```  
  
4.  <span data-ttu-id="47a86-123">Faites glisser une forme Construire un message après ReceiveEditLine.</span><span class="sxs-lookup"><span data-stu-id="47a86-123">Drag a Construct Message after ReceiveEditLine.</span></span>  
  
    -   <span data-ttu-id="47a86-124">**Messages construits :** EndDocMsg</span><span class="sxs-lookup"><span data-stu-id="47a86-124">**Messages Constructed:** EndDocMsg</span></span>  
  
    -   <span data-ttu-id="47a86-125">**Nom :** ConstructEndDocMessageWithData</span><span class="sxs-lookup"><span data-stu-id="47a86-125">**Name:** ConstructEndDocMessageWithData</span></span>  
  
     <span data-ttu-id="47a86-126">Avec le bouton droit dans le milieu et sélectionnez **insérer une forme**, puis sélectionnez **transformer**.</span><span class="sxs-lookup"><span data-stu-id="47a86-126">Right-click in the middle and select **Insert Shape**, and then select **Transform**.</span></span>  
  
5.  <span data-ttu-id="47a86-127">Double-cliquez sur **Transform_2** à ouvrir.</span><span class="sxs-lookup"><span data-stu-id="47a86-127">Double-click **Transform_2** to open.</span></span>  
  
    1.  <span data-ttu-id="47a86-128">Sélectionnez **Source** et cliquez sur dans la ligne Ajouter sous **nom de la Variable** et sélectionnez **BeginDocResponseMsg**.</span><span class="sxs-lookup"><span data-stu-id="47a86-128">Select **Source** and click in the Add row under **Variable Name** and select **BeginDocResponseMsg**.</span></span>  
  
    2.  <span data-ttu-id="47a86-129">Sélectionnez **Destination** et cliquez sur dans la ligne Ajouter sous **nom de la Variable**, sélectionnez **EndDocMsg**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="47a86-129">Select **Destination** and click in the Add row under **Variable Name**, select **EndDocMsg**, and click **OK**.</span></span>  
  
6.  <span data-ttu-id="47a86-130">Dans l’Explorateur de solutions, double-cliquez sur **Transform_2.btm** pour ouvrir l’outil de mappage.</span><span class="sxs-lookup"><span data-stu-id="47a86-130">In the Solution Explorer, double-click **Transform_2.btm** to open the mapping tool.</span></span> <span data-ttu-id="47a86-131">Liez les quatre éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="47a86-131">Link the following four items:</span></span>  
  
    -   <span data-ttu-id="47a86-132">mnCMJobNo</span><span class="sxs-lookup"><span data-stu-id="47a86-132">mnCMJobNo</span></span>  
  
    -   <span data-ttu-id="47a86-133">szCMComputerID</span><span class="sxs-lookup"><span data-stu-id="47a86-133">szCMComputerID</span></span>  
  
    -   <span data-ttu-id="47a86-134">mnProcessID</span><span class="sxs-lookup"><span data-stu-id="47a86-134">mnProcessID</span></span>  
  
    -   <span data-ttu-id="47a86-135">mnTransactionID</span><span class="sxs-lookup"><span data-stu-id="47a86-135">mnTransactionID</span></span>  
  
     <span data-ttu-id="47a86-136">Dans un souci de simplicité d'utilisation, cet exemple inclut des valeurs codées en dur.</span><span class="sxs-lookup"><span data-stu-id="47a86-136">For ease of use, this example has hardcoded values.</span></span> <span data-ttu-id="47a86-137">Cliquez sur l'élément dans le schéma de destination et définissez la valeur suivante.</span><span class="sxs-lookup"><span data-stu-id="47a86-137">Click the item in the Destination Schema and set the following Value.</span></span>  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <ns0:F4211FSEndDoc xmlns:ns0="http://schemas.microsoft.com/  
        [JDE://CSALES/B4200310]">  
       <ns0:szCMProgramID>XMLInterop</ns0:szCMProgramID>  
       <ns0:szCMVersion>ZJDE0001</ns0:szCMVersion>  
       <ns0:cCMUseWorkFiles>2</ns0:cCMUseWorkFiles>  
    </ns0:F4211FSEndDoc>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="47a86-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="47a86-138">See Also</span></span>  
 <span data-ttu-id="47a86-139">[Tâche 1 : Créer les Ports](../core/task-1-create-the-ports2.md) </span><span class="sxs-lookup"><span data-stu-id="47a86-139">[Task 1: Create the Ports](../core/task-1-create-the-ports2.md) </span></span>  
 <span data-ttu-id="47a86-140">[Tâche 2 : Créer les Messages](../core/task-2-create-the-messages1.md) </span><span class="sxs-lookup"><span data-stu-id="47a86-140">[Task 2: Create the Messages](../core/task-2-create-the-messages1.md) </span></span>  
 <span data-ttu-id="47a86-141">[Tâche 3 : Configurer l’envoi et réception des formes](../core/task-3-configure-the-send-and-receive-shapes1.md) </span><span class="sxs-lookup"><span data-stu-id="47a86-141">[Task 3: Configure the Send and Receive Shapes](../core/task-3-configure-the-send-and-receive-shapes1.md) </span></span>  
 [<span data-ttu-id="47a86-142">Tâche 4 : Configurer la forme construire un Message</span><span class="sxs-lookup"><span data-stu-id="47a86-142">Task 4: Configure the Construct Message Shape</span></span>](../core/task-4-configure-the-construct-message-shape2.md)