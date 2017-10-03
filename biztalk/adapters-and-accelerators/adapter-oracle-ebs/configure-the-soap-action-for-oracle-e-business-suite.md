---
title: "Configurer l’action SOAP pour Oracle E-Business Suite dans BizTalk Server | Documents Microsoft"
description: "Entrez une action SOAP dans Visual Studio, ou utiliser l’adaptateur WCF-Custom ou WCF-OracleEBS dans le Pack de l’adaptateur BizTalk (LOB)"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ca799d96-66e4-4d4e-a632-cb5505e999b4
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6c29cb5ce17f0a80e42ceae908639bed48e99e3a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configure-the-soap-action-for-oracle-e-business-suite"></a><span data-ttu-id="83128-103">Configuration de l’action SOAP pour Oracle E-Business Suite</span><span class="sxs-lookup"><span data-stu-id="83128-103">Configure the SOAP action for Oracle E-Business Suite</span></span>
<span data-ttu-id="83128-104">Pour effectuer toutes les opérations d’Oracle E-Business Suite à l’aide de la station de travail WCF [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], vous devez spécifier une action SOAP.</span><span class="sxs-lookup"><span data-stu-id="83128-104">To perform any operation on Oracle E-Business Suite using the WCF-based [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], you must specify a SOAP action.</span></span> <span data-ttu-id="83128-105">L’action SOAP communique à l’adaptateur quelle action doit être effectuée.</span><span class="sxs-lookup"><span data-stu-id="83128-105">The SOAP action communicates to the adapter what action should be performed.</span></span> <span data-ttu-id="83128-106">Vous pouvez spécifier l’action SOAP à partir de [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] ou à partir de la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.</span><span class="sxs-lookup"><span data-stu-id="83128-106">You can specify the SOAP action either from [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] or from the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="83128-107">Toutefois, si vous spécifiez l’action SOAP à partir de deux emplacements, l’action vous avez spécifié à partir de [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] est remplacée.</span><span class="sxs-lookup"><span data-stu-id="83128-107">However, if you specify the SOAP action from both locations, the action you specified from [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] is overridden.</span></span>  
  
 <span data-ttu-id="83128-108">Pour plus d’informations sur la spécification d’action SOAP, consultez [spécifiant les Actions SOAP pour les adaptateurs d’envoi WCF](../../core/specifying-soap-actions-for-wcf-send-adapters.md).</span><span class="sxs-lookup"><span data-stu-id="83128-108">For more information about specifying SOAP action, see [Specifying SOAP Actions for WCF Send Adapters](../../core/specifying-soap-actions-for-wcf-send-adapters.md).</span></span>  
  
## <a name="enter-soap-action-from-visual-studio"></a><span data-ttu-id="83128-109">Entrez l’Action SOAP à partir de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="83128-109">Enter SOAP Action from Visual Studio</span></span>  
 <span data-ttu-id="83128-110">À partir de [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], vous devez spécifier l’action SOAP dans le cadre de l’orchestration en utilisant une **Expression** forme.</span><span class="sxs-lookup"><span data-stu-id="83128-110">From [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], you must specify the SOAP action as part of the orchestration by using an **Expression** shape.</span></span>  
  
1.  <span data-ttu-id="83128-111">Dans l’orchestration BizTalk, vous devez inclure une **Expression** forme en le faisant glisser à partir de la **Orchestration BizTalk** boîte à outils.</span><span class="sxs-lookup"><span data-stu-id="83128-111">In the BizTalk orchestration, include an **Expression** shape by dragging it from the **BizTalk Orchestration** toolbox.</span></span>  
  
2.  <span data-ttu-id="83128-112">Double-cliquez sur le **Expression** forme pour ouvrir l’éditeur d’Expression BizTalk.</span><span class="sxs-lookup"><span data-stu-id="83128-112">Double-click the **Expression** shape to open BizTalk Expression Editor.</span></span>  
  
3.  <span data-ttu-id="83128-113">Spécifiez l’action dans Éditeur d’Expression BizTalk.</span><span class="sxs-lookup"><span data-stu-id="83128-113">Specify the action in BizTalk Expression Editor.</span></span> <span data-ttu-id="83128-114">Exemple :</span><span class="sxs-lookup"><span data-stu-id="83128-114">For example:</span></span>  
  
    ```  
    OutboundMessage(WCF.Action)="InterfaceTables/Insert/SQLGL/GL/GL_ALLOC_HISTORY"  
    ```  
  
     <span data-ttu-id="83128-115">Pour plus d’informations sur la **Expression** forme et l’éditeur d’Expression BizTalk, consultez [comment créer des Expressions](../../core/how-to-create-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="83128-115">For more information about the **Expression** shape and BizTalk Expression Editor, see [How to Create Expressions](../../core/how-to-create-expressions.md).</span></span>  
  
## <a name="enter-soap-action-from-biztalk-server-administration"></a><span data-ttu-id="83128-116">Entrez l’Action SOAP à partir de l’Administration de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="83128-116">Enter SOAP Action from BizTalk Server Administration</span></span>  
 <span data-ttu-id="83128-117">À partir de la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration, vous devez spécifier l’action SOAP dans le cadre de la configuration du port WCF-Custom ou WCF-OracleEBS.</span><span class="sxs-lookup"><span data-stu-id="83128-117">From the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console, you must specify the SOAP action as part of the WCF-Custom or WCF-OracleEBS port configuration.</span></span>  
  
#### <a name="enter-a-soap-action-for-the-wcf-custom-port"></a><span data-ttu-id="83128-118">Entrez une action SOAP pour le port WCF-Custom</span><span class="sxs-lookup"><span data-stu-id="83128-118">Enter a SOAP action for the WCF-Custom port</span></span>  
  
1.  <span data-ttu-id="83128-119">Démarrer le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.</span><span class="sxs-lookup"><span data-stu-id="83128-119">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2.  <span data-ttu-id="83128-120">Dans l’arborescence de la console, développez **groupe BizTalk**, puis développez **Applications**, puis cliquez sur **Ports d’envoi**.</span><span class="sxs-lookup"><span data-stu-id="83128-120">In the console tree, expand **BizTalk Group**, then expand **Applications**, and then click **Send Ports**.</span></span> <span data-ttu-id="83128-121">Dans le volet droit, vous pouvez choisir de créer un port ou de sélectionner un port existant.</span><span class="sxs-lookup"><span data-stu-id="83128-121">In the right pane, you can choose to create a port or select an existing port.</span></span>  
  
3.  <span data-ttu-id="83128-122">Dans la boîte de dialogue Propriétés du port, à partir de la **Type** la liste déroulante, sélectionnez **WCF-Custom**, puis cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="83128-122">In the port properties dialog box, from the **Type** drop-down list, select **WCF-Custom**, and then click **Configure**.</span></span>  
  
4.  <span data-ttu-id="83128-123">Dans le **propriétés du Transport WCF-Custom** boîte de dialogue, cliquez sur le **général** onglet.</span><span class="sxs-lookup"><span data-stu-id="83128-123">In the **WCF-Custom Transport Properties** dialog box, click the **General** tab.</span></span>  
  
5.  <span data-ttu-id="83128-124">Dans le **Action** texte, spécifiez l’action SOAP pour l’opération.</span><span class="sxs-lookup"><span data-stu-id="83128-124">In the **Action** text box, specify the SOAP action for the operation.</span></span> <span data-ttu-id="83128-125">Vous pouvez spécifier l’action comme suit :</span><span class="sxs-lookup"><span data-stu-id="83128-125">You can specify the action in the following ways:</span></span>  
  
    -   <span data-ttu-id="83128-126">**En utilisant le format d’action unique**.</span><span class="sxs-lookup"><span data-stu-id="83128-126">**By using the single action format**.</span></span> <span data-ttu-id="83128-127">Utilisez ce format si WCF-Custom port envoie et recevoir des messages pour une seule opération.</span><span class="sxs-lookup"><span data-stu-id="83128-127">Use this format if the WCF-Custom port sends and receive messages for a single operation.</span></span> <span data-ttu-id="83128-128">Exemple :</span><span class="sxs-lookup"><span data-stu-id="83128-128">For example:</span></span>  
  
        ```  
        InterfaceTables/Insert/SQLGL/GL/GL_ALLOC_HISTORY  
        ```  
  
    -   <span data-ttu-id="83128-129">**En utilisant le format de mappage d’action**.</span><span class="sxs-lookup"><span data-stu-id="83128-129">**By using the action mapping format**.</span></span> <span data-ttu-id="83128-130">Utilisez ce format, si un seul port WCF-Custom envoie et reçoit des messages pour plusieurs opérations.</span><span class="sxs-lookup"><span data-stu-id="83128-130">Use this format if a single WCF-Custom port sends and receives messages for more than one operation.</span></span> <span data-ttu-id="83128-131">Par exemple, si un seul port WCF-Custom envoie et reçoit des messages pour Op1 (pour insérer des enregistrements dans la table GL_ALLOC_HISTORY) et Op2 (mettre à jour des enregistrements dans la table GL_ALLOC_HISTORY), l’action SOAP peut être spécifiée de la manière suivante :</span><span class="sxs-lookup"><span data-stu-id="83128-131">For example, if a single WCF-Custom port sends and receives messages for Op1 (to insert records in the GL_ALLOC_HISTORY table) and Op2 (to update records in the GL_ALLOC_HISTORY table), the SOAP action can be specified in the following manner:</span></span>  
  
        ```  
        <BtsActionMapping>  
          <Operation Name="Op1" Action="InterfaceTables/Insert/SQLGL/GL/GL_ALLOC_HISTORY" />  
          <Operation Name="Op2" Action="InterfaceTables/Update/SQLGL/GL/GL_ALLOC_HISTORY " />  
        </BtsActionMapping>  
        ```  
  
         <span data-ttu-id="83128-132">L’approche de mappage d’action fournit une plus grande flexibilité en termes de spécification d’un ensemble d’actions et par conséquent, l’activation de messages qui appartiennent à une action différente des types de circuler via le même port.</span><span class="sxs-lookup"><span data-stu-id="83128-132">The action mapping approach provides greater flexibility in terms of specifying a set of actions, and hence enabling messages that belong to different action types to flow through the same port.</span></span>  
  
         <span data-ttu-id="83128-133">Le format de l’action SOAP est différent pour chaque opération.</span><span class="sxs-lookup"><span data-stu-id="83128-133">The format for the SOAP action is different for each operation.</span></span> <span data-ttu-id="83128-134">Pour plus d’informations sur le format d’action pour chaque opération, consultez [Messages et des schémas de Message pour l’adaptateur Oracle eBusiness Suite](messages-and-message-schemas-for-biztalk-adapter-for-oracle-e-business-suite.md).</span><span class="sxs-lookup"><span data-stu-id="83128-134">For more information about the action format for each operation, see [Messages and Message Schemas for Oracle EBS adapter](messages-and-message-schemas-for-biztalk-adapter-for-oracle-e-business-suite.md).</span></span>
  
#### <a name="enter-a-soap-action-for-the-wcf-oracleebs-port"></a><span data-ttu-id="83128-135">Entrez une action SOAP pour le port WCF-OracleEBS</span><span class="sxs-lookup"><span data-stu-id="83128-135">Enter a SOAP action for the WCF-OracleEBS port</span></span>  
  
1.  <span data-ttu-id="83128-136">Démarrer le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.</span><span class="sxs-lookup"><span data-stu-id="83128-136">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2.  <span data-ttu-id="83128-137">Ajouter l’adaptateur WCF-OracleEBS à la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.</span><span class="sxs-lookup"><span data-stu-id="83128-137">Add the WCF-OracleEBS adapter to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="83128-138">Pour obtenir des instructions, consultez [Ajout de l’adaptateur Oracle E-Business Suite à la Console Administration de BizTalk Server](../../adapters-and-accelerators/adapter-oracle-ebs/add-the-oracle-ebs-adapter-to-biztalk-server-administration-console.md).</span><span class="sxs-lookup"><span data-stu-id="83128-138">For instructions, see [Adding the Oracle E-Business Suite Adapter to BizTalk Server Administration Console](../../adapters-and-accelerators/adapter-oracle-ebs/add-the-oracle-ebs-adapter-to-biztalk-server-administration-console.md).</span></span>  
  
3.  <span data-ttu-id="83128-139">Dans l’arborescence de la console, développez **groupe BizTalk**, puis développez **Applications**, puis cliquez sur **Ports d’envoi**.</span><span class="sxs-lookup"><span data-stu-id="83128-139">In the console tree, expand **BizTalk Group**, then expand **Applications**, and then click **Send Ports**.</span></span> <span data-ttu-id="83128-140">Dans le volet droit, vous pouvez choisir de créer un port ou de sélectionner un port existant.</span><span class="sxs-lookup"><span data-stu-id="83128-140">In the right pane, you can choose to create a port or select an existing port.</span></span>  
  
4.  <span data-ttu-id="83128-141">Dans la boîte de dialogue Propriétés du port, à partir de la **Type** liste déroulante, sélectionnez le WCF-OracleEBS carte vous ajoutez précédemment, puis cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="83128-141">In the port properties dialog box, from the **Type** drop-down list, select the WCF-OracleEBS adapter you add earlier, and then click **Configure**.</span></span>  
  
5.  <span data-ttu-id="83128-142">Dans la boîte de dialogue Propriétés du transport, cliquez sur le **général** onglet.</span><span class="sxs-lookup"><span data-stu-id="83128-142">In the transport properties dialog box, click the **General** tab.</span></span>  
  
6.  <span data-ttu-id="83128-143">Dans le **Action** texte, spécifiez l’action SOAP pour l’opération.</span><span class="sxs-lookup"><span data-stu-id="83128-143">In the **Action** text box, specify the SOAP action for the operation.</span></span> <span data-ttu-id="83128-144">Vous pouvez spécifier l’action comme suit :</span><span class="sxs-lookup"><span data-stu-id="83128-144">You can specify the action in the following ways:</span></span>  
  
    -   <span data-ttu-id="83128-145">**En utilisant le format d’action unique**.</span><span class="sxs-lookup"><span data-stu-id="83128-145">**By using the single action format**.</span></span> <span data-ttu-id="83128-146">Utilisez ce format si les WCF-OracleEBS port envoie et recevoir des messages pour une seule opération.</span><span class="sxs-lookup"><span data-stu-id="83128-146">Use this format if the WCF-OracleEBS port sends and receive messages for a single operation.</span></span> <span data-ttu-id="83128-147">Exemple :</span><span class="sxs-lookup"><span data-stu-id="83128-147">For example:</span></span>  
  
        ```  
        InterfaceTables/Insert/SQLGL/GL/GL_ALLOC_HISTORY  
        ```  
  
    -   <span data-ttu-id="83128-148">**En utilisant le format de mappage d’action**.</span><span class="sxs-lookup"><span data-stu-id="83128-148">**By using the action mapping format**.</span></span> <span data-ttu-id="83128-149">Utilisez ce format, si un seul port WCF-OracleEBS envoie et reçoit des messages pour plusieurs opérations.</span><span class="sxs-lookup"><span data-stu-id="83128-149">Use this format if a single WCF-OracleEBS port sends and receives messages for more than one operation.</span></span> <span data-ttu-id="83128-150">Par exemple, si un seul port WCF-OracleEBS envoie et reçoit des messages pour Op1 (pour insérer des enregistrements dans la table GL_ALLOC_HISTORY) et Op2 (mettre à jour des enregistrements dans la table GL_ALLOC_HISTORY), l’action SOAP peut être spécifiée de la manière suivante :</span><span class="sxs-lookup"><span data-stu-id="83128-150">For example, if a single WCF-OracleEBS port sends and receives messages for Op1 (to insert records in the GL_ALLOC_HISTORY table) and Op2 (to update records in the GL_ALLOC_HISTORY table), the SOAP action can be specified in the following manner:</span></span>  
  
        ```  
        <BtsActionMapping>  
          <Operation Name="Op1" Action="InterfaceTables/Insert/SQLGL/GL/GL_ALLOC_HISTORY" />  
          <Operation Name="Op2" Action="InterfaceTables/Update/SQLGL/GL/GL_ALLOC_HISTORY " />  
        </BtsActionMapping>  
        ```  
  
         <span data-ttu-id="83128-151">L’approche de mappage d’action fournit une plus grande flexibilité en termes de spécification d’un ensemble d’actions et par conséquent, l’activation de messages qui appartiennent à une action différente des types de circuler via le même port.</span><span class="sxs-lookup"><span data-stu-id="83128-151">The action mapping approach provides greater flexibility in terms of specifying a set of actions, and hence enabling messages that belong to different action types to flow through the same port.</span></span>  
  
         <span data-ttu-id="83128-152">Le format de l’action SOAP est différent pour chaque opération.</span><span class="sxs-lookup"><span data-stu-id="83128-152">The format for the SOAP action is different for each operation.</span></span> <span data-ttu-id="83128-153">Pour plus d’informations sur le format d’action pour chaque opération, consultez [Messages et des schémas de Message pour l’adaptateur Oracle eBusiness Suite](messages-and-message-schemas-for-biztalk-adapter-for-oracle-e-business-suite.md).</span><span class="sxs-lookup"><span data-stu-id="83128-153">For more information about the action format for each operation, see [Messages and Message Schemas for Oracle EBS adapter](messages-and-message-schemas-for-biztalk-adapter-for-oracle-e-business-suite.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="83128-154">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="83128-154">See Also</span></span>  
 [<span data-ttu-id="83128-155">Blocs de construction pour créer des applications d’Oracle E-Business Suite</span><span class="sxs-lookup"><span data-stu-id="83128-155">Building blocks to create Oracle E-Business Suite applications</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/building-blocks-to-create-oracle-e-business-suite-applications.md)