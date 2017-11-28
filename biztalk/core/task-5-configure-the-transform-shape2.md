---
title: "Tâche 5 : Configurer la transformation Shape2 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3e92874e-9021-4cf6-bab6-d4173308c469
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 596afdecc38f25ef92dbeb368197d9c71adaffc5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="task-5-configure-the-transform-shape"></a><span data-ttu-id="1b4b1-102">Tâche 5 : Configurer la forme Transformer</span><span class="sxs-lookup"><span data-stu-id="1b4b1-102">Task 5: Configure the Transform Shape</span></span>
<span data-ttu-id="1b4b1-103">Les procédures suivantes permettent de configurer la forme Transformer.</span><span class="sxs-lookup"><span data-stu-id="1b4b1-103">Use the following procedure to configure the Transform shape.</span></span>  
  
### <a name="to-configure-the-transform-shape"></a><span data-ttu-id="1b4b1-104">Pour configurer la forme Transformer</span><span class="sxs-lookup"><span data-stu-id="1b4b1-104">To configure the Transform shape</span></span>  
  
1.  <span data-ttu-id="1b4b1-105">Faites glisser une forme Construire un message après ReceiveBeginDocResponse.</span><span class="sxs-lookup"><span data-stu-id="1b4b1-105">Drag a Construct Message shape after ReceiveBeginDocResponse.</span></span>  
  
    -   <span data-ttu-id="1b4b1-106">**Messages construits :** EditLineMsg</span><span class="sxs-lookup"><span data-stu-id="1b4b1-106">**Messages Constructed:** EditLineMsg</span></span>  
  
    -   <span data-ttu-id="1b4b1-107">**Nom :** ConstructEditLineMessageWithData</span><span class="sxs-lookup"><span data-stu-id="1b4b1-107">**Name:** ConstructEditLineMessageWithData</span></span>  
  
    1.  <span data-ttu-id="1b4b1-108">Avec le bouton droit au milieu, sélectionnez **insérer une forme**, puis sélectionnez **transformer**.</span><span class="sxs-lookup"><span data-stu-id="1b4b1-108">Right-click in the middle, select **Insert Shape**, and then select **Transform**.</span></span>  
  
         <span data-ttu-id="1b4b1-109">![Insérer la forme transformer](../core/media/insert-shape-transform.gif "insert_shape_transform")</span><span class="sxs-lookup"><span data-stu-id="1b4b1-109">![Insert Shape Transform](../core/media/insert-shape-transform.gif "insert_shape_transform")</span></span>  
  
    2.  <span data-ttu-id="1b4b1-110">À l'aide de la forme Transformer, mappez les données depuis les données que vous envoyez vers les données envoyées.</span><span class="sxs-lookup"><span data-stu-id="1b4b1-110">Using Transform, map data from the data you are sending to the data that is sent.</span></span>  
  
     <span data-ttu-id="1b4b1-111">Vous devez envoyer un document (au lieu de BeginDoc) pour votre environnement de travail, avec toutes les valeurs possibles afin de construire tous les messages possibles (BeginDoc, EditLine et EndDoc).</span><span class="sxs-lookup"><span data-stu-id="1b4b1-111">For your work environment you would send a document (instead of BeginDoc) with all values possible allowing you to construct all possible messages, BeginDoc, EditLine, and EndDoc.</span></span> <span data-ttu-id="1b4b1-112">Toutefois, seules des données codées en dur sont utilisées dans cet exemple.</span><span class="sxs-lookup"><span data-stu-id="1b4b1-112">For this example, however, there is only hard coded data.</span></span>  
  
2.  <span data-ttu-id="1b4b1-113">Double-cliquez sur Transform_1 pour l'ouvrir.</span><span class="sxs-lookup"><span data-stu-id="1b4b1-113">Double-click Transform_1 to open.</span></span>  
  
    1.  <span data-ttu-id="1b4b1-114">Sélectionnez Source, cliquez dans la ligne Ajouter sous **nom de la Variable** et sélectionnez **BeginDocResponseMsg**.</span><span class="sxs-lookup"><span data-stu-id="1b4b1-114">Select Source and click in the Add row under **Variable Name** and select **BeginDocResponseMsg**.</span></span>  
  
         <span data-ttu-id="1b4b1-115">![Transformation Source](../core/media/transform-source.gif "transform_source")</span><span class="sxs-lookup"><span data-stu-id="1b4b1-115">![Transform Source](../core/media/transform-source.gif "transform_source")</span></span>  
  
    2.  <span data-ttu-id="1b4b1-116">Sélectionnez **Destination** et cliquez sur dans la ligne Ajouter sous **nom de la Variable**, sélectionnez **EditLineMsg**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="1b4b1-116">Select **Destination** and click in the Add row under **Variable Name**, select **EditLineMsg**, and click **OK**.</span></span>  
  
         <span data-ttu-id="1b4b1-117">![Transformer la Destination](../core/media/transform-destination.gif "transform_destination")</span><span class="sxs-lookup"><span data-stu-id="1b4b1-117">![Transform Destination](../core/media/transform-destination.gif "transform_destination")</span></span>  
  
3.  <span data-ttu-id="1b4b1-118">Dans l’Explorateur de solutions, double-cliquez sur **Transform_1.btm** pour ouvrir l’outil de mappage.</span><span class="sxs-lookup"><span data-stu-id="1b4b1-118">In the Solution Explorer, double-click **Transform_1.btm** to open the mapping tool.</span></span> <span data-ttu-id="1b4b1-119">Liez les quatre éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="1b4b1-119">Link the following four items:</span></span>  
  
    -   <span data-ttu-id="1b4b1-120">mnCMJobNo</span><span class="sxs-lookup"><span data-stu-id="1b4b1-120">mnCMJobNo</span></span>  
  
    -   <span data-ttu-id="1b4b1-121">szCMComputerID</span><span class="sxs-lookup"><span data-stu-id="1b4b1-121">szCMComputerID</span></span>  
  
    -   <span data-ttu-id="1b4b1-122">mnProcessID</span><span class="sxs-lookup"><span data-stu-id="1b4b1-122">mnProcessID</span></span>  
  
    -   <span data-ttu-id="1b4b1-123">mnTransactionID</span><span class="sxs-lookup"><span data-stu-id="1b4b1-123">mnTransactionID</span></span>  
  
     <span data-ttu-id="1b4b1-124">![Exemple transformer mappage](../core/media/example-transformmapping.gif "example_transformmapping")</span><span class="sxs-lookup"><span data-stu-id="1b4b1-124">![Example Transform Mapping](../core/media/example-transformmapping.gif "example_transformmapping")</span></span>  
  
     <span data-ttu-id="1b4b1-125">Dans un souci de simplicité d'utilisation, cet exemple inclut des valeurs codées en dur.</span><span class="sxs-lookup"><span data-stu-id="1b4b1-125">For ease of use, this example has hardcoded values.</span></span> <span data-ttu-id="1b4b1-126">Cliquez sur l'élément dans le schéma de destination et définissez la valeur suivante.</span><span class="sxs-lookup"><span data-stu-id="1b4b1-126">Click the item in the Destination Schema and set the following Value.</span></span>  
  
     <span data-ttu-id="1b4b1-127">![Mappage de codé dur](../core/media/hardcoded-mapping-example.gif "hardcoded_mapping_example")</span><span class="sxs-lookup"><span data-stu-id="1b4b1-127">![Hard Coded Mapping](../core/media/hardcoded-mapping-example.gif "hardcoded_mapping_example")</span></span>  
  
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
  
4.  <span data-ttu-id="1b4b1-128">Faites glisser une forme Construire un message après ReceiveEditLine.</span><span class="sxs-lookup"><span data-stu-id="1b4b1-128">Drag a Construct Message after ReceiveEditLine.</span></span>  
  
    -   <span data-ttu-id="1b4b1-129">**Messages construits :** EndDocMsg</span><span class="sxs-lookup"><span data-stu-id="1b4b1-129">**Messages Constructed:** EndDocMsg</span></span>  
  
    -   <span data-ttu-id="1b4b1-130">**Nom :** ConstructEndDocMessageWithData</span><span class="sxs-lookup"><span data-stu-id="1b4b1-130">**Name:** ConstructEndDocMessageWithData</span></span>  
  
         <span data-ttu-id="1b4b1-131">Avec le bouton droit dans le milieu et sélectionnez **insérer une forme**, puis sélectionnez **transformer**.</span><span class="sxs-lookup"><span data-stu-id="1b4b1-131">Right-click in the middle and select **Insert Shape**, and then select **Transform**.</span></span>  
  
5.  <span data-ttu-id="1b4b1-132">Double-cliquez sur Transform_2 pour l'ouvrir.</span><span class="sxs-lookup"><span data-stu-id="1b4b1-132">Double-click Transform_2 to open.</span></span>  
  
    1.  <span data-ttu-id="1b4b1-133">Sélectionnez **Source** et cliquez sur dans la ligne Ajouter sous **nom de la Variable** et sélectionnez **BeginDocResponseMsg**.</span><span class="sxs-lookup"><span data-stu-id="1b4b1-133">Select **Source** and click in the Add row under **Variable Name** and select **BeginDocResponseMsg**.</span></span>  
  
    2.  <span data-ttu-id="1b4b1-134">Sélectionnez **Destination** et cliquez sur dans la ligne Ajouter sous **nom de la Variable**, sélectionnez **EndDocMsg**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="1b4b1-134">Select **Destination** and click in the Add row under **Variable Name**, select **EndDocMsg**, and click **OK**.</span></span>  
  
6.  <span data-ttu-id="1b4b1-135">Dans l’Explorateur de solutions, double-cliquez sur **Transform_2.btm** pour ouvrir l’outil de mappage.</span><span class="sxs-lookup"><span data-stu-id="1b4b1-135">In the Solution Explorer, double-click **Transform_2.btm** to open the mapping tool.</span></span> <span data-ttu-id="1b4b1-136">Liez les quatre éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="1b4b1-136">Link the following four items:</span></span>  
  
    -   <span data-ttu-id="1b4b1-137">mnCMJobNo</span><span class="sxs-lookup"><span data-stu-id="1b4b1-137">mnCMJobNo</span></span>  
  
    -   <span data-ttu-id="1b4b1-138">szCMComputerID</span><span class="sxs-lookup"><span data-stu-id="1b4b1-138">szCMComputerID</span></span>  
  
    -   <span data-ttu-id="1b4b1-139">mnProcessID</span><span class="sxs-lookup"><span data-stu-id="1b4b1-139">mnProcessID</span></span>  
  
    -   <span data-ttu-id="1b4b1-140">mnTransactionID</span><span class="sxs-lookup"><span data-stu-id="1b4b1-140">mnTransactionID</span></span>  
  
     <span data-ttu-id="1b4b1-141">Dans un souci de simplicité d'utilisation, cet exemple inclut des valeurs codées en dur.</span><span class="sxs-lookup"><span data-stu-id="1b4b1-141">For ease of use, this example has hardcoded values.</span></span> <span data-ttu-id="1b4b1-142">Cliquez sur l'élément dans le schéma de destination et définissez la valeur suivante.</span><span class="sxs-lookup"><span data-stu-id="1b4b1-142">Click the item in the Destination Schema and set the following Value.</span></span>  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <ns0:F4211FSEndDoc xmlns:ns0="http://schemas.microsoft.com/  
        [JDE://CSALES/B4200310]">  
       <ns0:szCMProgramID>XMLInterop</ns0:szCMProgramID>  
       <ns0:szCMVersion>ZJDE0001</ns0:szCMVersion>  
       <ns0:cCMUseWorkFiles>2</ns0:cCMUseWorkFiles>  
    </ns0:F4211FSEndDoc>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="1b4b1-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1b4b1-143">See Also</span></span>  
 <span data-ttu-id="1b4b1-144">[Tâche 1 : Créer les Ports](../core/task-1-create-the-ports1.md) </span><span class="sxs-lookup"><span data-stu-id="1b4b1-144">[Task 1: Create the Ports](../core/task-1-create-the-ports1.md) </span></span>  
 <span data-ttu-id="1b4b1-145">[Tâche 2 : Créer les Messages](../core/task-2-create-the-messages2.md) </span><span class="sxs-lookup"><span data-stu-id="1b4b1-145">[Task 2: Create the Messages](../core/task-2-create-the-messages2.md) </span></span>  
 <span data-ttu-id="1b4b1-146">[Tâche 3 : Configurer l’envoi et réception des formes](../core/task-3-configure-the-send-and-receive-shapes2.md) </span><span class="sxs-lookup"><span data-stu-id="1b4b1-146">[Task 3: Configure the Send and Receive Shapes](../core/task-3-configure-the-send-and-receive-shapes2.md) </span></span>  
 [<span data-ttu-id="1b4b1-147">Tâche 4 : Configurer la forme construire un Message</span><span class="sxs-lookup"><span data-stu-id="1b4b1-147">Task 4: Configure the Construct Message Shape</span></span>](../core/task-4-configure-the-construct-message-shape1.md)