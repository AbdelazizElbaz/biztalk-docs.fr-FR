---
title: "Configurer l’action SOAP pour l’adaptateur SQL dans BizTalk | Documents Microsoft"
description: "Entrez une action SOAP dans Visual Studio, ou utiliser l’adaptateur WCF-Custom ou WCF-SQL dans le Pack de l’adaptateur BizTalk (LOB)"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: acd7f60b-c27f-4988-a67c-e56ef8d38f66
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d4e342353b13848cca1c332d4568f541e59924cc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configure-the-soap-action-for-the-sql-adapter"></a><span data-ttu-id="c3b3d-103">Configurer l’action SOAP pour l’adaptateur SQL</span><span class="sxs-lookup"><span data-stu-id="c3b3d-103">Configure the SOAP action for the SQL adapter</span></span>
<span data-ttu-id="c3b3d-104">Pour effectuer une quelconque opération sur SQL Server à l’aide de la station de travail WCF [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], vous devez spécifier une action SOAP.</span><span class="sxs-lookup"><span data-stu-id="c3b3d-104">To perform any operation on SQL Server using the WCF-based [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], you must specify a SOAP action.</span></span> <span data-ttu-id="c3b3d-105">L’action SOAP communique à l’adaptateur quelle action doit être effectuée.</span><span class="sxs-lookup"><span data-stu-id="c3b3d-105">The SOAP action communicates to the adapter what action should be performed.</span></span> <span data-ttu-id="c3b3d-106">Vous pouvez spécifier l’action SOAP à partir de [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] ou à partir de la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.</span><span class="sxs-lookup"><span data-stu-id="c3b3d-106">You can specify the SOAP action either from [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] or from the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="c3b3d-107">Toutefois, si vous spécifiez l’action SOAP à partir de deux emplacements, l’action vous avez spécifié à partir de [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] sera remplacé.</span><span class="sxs-lookup"><span data-stu-id="c3b3d-107">However, if you specify the SOAP action from both locations, the action you specified from [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] will be overridden.</span></span>  
  
 <span data-ttu-id="c3b3d-108">Pour plus d’informations sur la spécification d’action SOAP, consultez [spécifiant les Actions SOAP pour les adaptateurs d’envoi WCF](../../core/specifying-soap-actions-for-wcf-send-adapters.md).</span><span class="sxs-lookup"><span data-stu-id="c3b3d-108">For more information about specifying SOAP action, see [Specifying SOAP Actions for WCF Send Adapters](../../core/specifying-soap-actions-for-wcf-send-adapters.md).</span></span>
  
## <a name="enter-the-soap-action-in-visual-studio"></a><span data-ttu-id="c3b3d-109">Entrez l’action SOAP dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c3b3d-109">Enter the SOAP action in Visual Studio</span></span>  
 <span data-ttu-id="c3b3d-110">À partir de [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], vous devez spécifier l’action SOAP dans le cadre de l’orchestration en utilisant une **Expression** forme.</span><span class="sxs-lookup"><span data-stu-id="c3b3d-110">From [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], you must specify the SOAP action as part of the orchestration by using an **Expression** shape.</span></span>  
  
1.  <span data-ttu-id="c3b3d-111">Dans l’orchestration BizTalk, vous devez inclure une **Expression** forme en le faisant glisser à partir de la **Orchestration BizTalk** boîte à outils.</span><span class="sxs-lookup"><span data-stu-id="c3b3d-111">In the BizTalk orchestration, include an **Expression** shape by dragging it from the **BizTalk Orchestration** toolbox.</span></span>  
  
2.  <span data-ttu-id="c3b3d-112">Double-cliquez sur le **Expression** forme pour ouvrir l’éditeur d’Expression BizTalk.</span><span class="sxs-lookup"><span data-stu-id="c3b3d-112">Double-click the **Expression** shape to open BizTalk Expression Editor.</span></span>  
  
3.  <span data-ttu-id="c3b3d-113">Spécifiez l’action dans Éditeur d’Expression BizTalk.</span><span class="sxs-lookup"><span data-stu-id="c3b3d-113">Specify the action in BizTalk Expression Editor.</span></span> <span data-ttu-id="c3b3d-114">Exemple :</span><span class="sxs-lookup"><span data-stu-id="c3b3d-114">For example:</span></span>  
  
    ```  
    OutboundMessage(WCF.Action)="TableOp/Insert/dbo/Employee"  
    ```  
  
     <span data-ttu-id="c3b3d-115">Pour plus d’informations sur la **Expression** forme et l’éditeur d’Expression BizTalk, consultez [comment créer des Expressions](../../core/how-to-create-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="c3b3d-115">For more information about the **Expression** shape and BizTalk Expression Editor, see [How to Create Expressions](../../core/how-to-create-expressions.md).</span></span>
  
## <a name="enter-the-soap-action-from-the-biztalk-server-administration-console"></a><span data-ttu-id="c3b3d-116">Entrez l’action SOAP à partir de la console Administration de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="c3b3d-116">Enter the SOAP action from the BizTalk Server Administration console</span></span>  
 <span data-ttu-id="c3b3d-117">À partir de la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration, vous pouvez spécifier l’action SOAP dans le cadre de la configuration du port WCF-Custom ou WCF-SQL.</span><span class="sxs-lookup"><span data-stu-id="c3b3d-117">From the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console, you can specify the SOAP action as part of the WCF-Custom or WCF-SQL port configuration.</span></span>  
  
### <a name="enter-a-soap-action-for-the-wcf-custom-port"></a><span data-ttu-id="c3b3d-118">Entrez une action SOAP pour le port WCF-Custom</span><span class="sxs-lookup"><span data-stu-id="c3b3d-118">Enter a SOAP action for the WCF-Custom port</span></span>  
  
1.  <span data-ttu-id="c3b3d-119">Démarrer le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.</span><span class="sxs-lookup"><span data-stu-id="c3b3d-119">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2.  <span data-ttu-id="c3b3d-120">Dans l’arborescence de la console, développez **groupe BizTalk**, puis développez **Applications**, puis cliquez sur **Ports d’envoi**.</span><span class="sxs-lookup"><span data-stu-id="c3b3d-120">In the console tree, expand **BizTalk Group**, then expand **Applications**, and then click **Send Ports**.</span></span> <span data-ttu-id="c3b3d-121">Dans le volet droit, vous pouvez choisir de créer un port ou de sélectionner un port existant.</span><span class="sxs-lookup"><span data-stu-id="c3b3d-121">In the right pane, you can choose to create a port or select an existing port.</span></span>  
  
3.  <span data-ttu-id="c3b3d-122">Dans la boîte de dialogue Propriétés du port, à partir de la **Type** la liste déroulante, sélectionnez **WCF-Custom**, puis cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="c3b3d-122">In the port properties dialog box, from the **Type** drop-down list, select **WCF-Custom**, and then click **Configure**.</span></span>  
  
4.  <span data-ttu-id="c3b3d-123">Dans le **propriétés du Transport WCF-Custom** boîte de dialogue, cliquez sur le **général** onglet.</span><span class="sxs-lookup"><span data-stu-id="c3b3d-123">In the **WCF-Custom Transport Properties** dialog box, click the **General** tab.</span></span>  
  
5.  <span data-ttu-id="c3b3d-124">Dans le **Action** texte, spécifiez l’action SOAP pour l’opération.</span><span class="sxs-lookup"><span data-stu-id="c3b3d-124">In the **Action** text box, specify the SOAP action for the operation.</span></span> <span data-ttu-id="c3b3d-125">Vous pouvez spécifier l’action comme suit :</span><span class="sxs-lookup"><span data-stu-id="c3b3d-125">You can specify the action in the following ways:</span></span>  
  
    -   <span data-ttu-id="c3b3d-126">**En utilisant le format d’action unique**.</span><span class="sxs-lookup"><span data-stu-id="c3b3d-126">**By using the single action format**.</span></span> <span data-ttu-id="c3b3d-127">Utilisez ce format si WCF-Custom port envoie et recevoir des messages pour une seule opération.</span><span class="sxs-lookup"><span data-stu-id="c3b3d-127">Use this format if the WCF-Custom port sends and receive messages for a single operation.</span></span> <span data-ttu-id="c3b3d-128">Exemple :</span><span class="sxs-lookup"><span data-stu-id="c3b3d-128">For example:</span></span>  
  
        ```  
        TableOp/Insert/dbo/Employee  
        ```  
  
    -   <span data-ttu-id="c3b3d-129">**En utilisant le format de mappage d’action**.</span><span class="sxs-lookup"><span data-stu-id="c3b3d-129">**By using the action mapping format**.</span></span> <span data-ttu-id="c3b3d-130">Utilisez ce format, si un seul port WCF-Custom envoie et reçoit des messages pour plusieurs opérations.</span><span class="sxs-lookup"><span data-stu-id="c3b3d-130">Use this format if a single WCF-Custom port sends and receives messages for more than one operation.</span></span> <span data-ttu-id="c3b3d-131">Par exemple, si un seul port WCF-Custom envoie et reçoit des messages pour Op1 (pour insérer des enregistrements dans la table Employee) et Op2 (pour mettre à jour des enregistrements dans la table Employee), l’action SOAP peut être spécifiée de la manière suivante :</span><span class="sxs-lookup"><span data-stu-id="c3b3d-131">For example, if a single WCF-Custom port sends and receives messages for Op1 (to insert records in the Employee table) and Op2 (to update records in the Employee table), the SOAP action can be specified in the following manner:</span></span>  
  
        ```  
        <BtsActionMapping>  
          <Operation Name="Op1" Action="TableOp/Insert/dbo/Employee" />  
          <Operation Name="Op2" Action="TableOp/Update/dbo/Employee" />  
        </BtsActionMapping>  
        ```  
  
         <span data-ttu-id="c3b3d-132">L’approche de mappage d’action fournit une plus grande flexibilité en termes de spécification d’un ensemble d’actions et par conséquent, l’activation de messages qui appartiennent à une action différente des types de circuler via le même port.</span><span class="sxs-lookup"><span data-stu-id="c3b3d-132">The action mapping approach provides greater flexibility in terms of specifying a set of actions, and hence enabling messages that belong to different action types to flow through the same port.</span></span>  
  
         <span data-ttu-id="c3b3d-133">Le format de l’action SOAP est différent pour chaque opération.</span><span class="sxs-lookup"><span data-stu-id="c3b3d-133">The format for the SOAP action is different for each operation.</span></span> <span data-ttu-id="c3b3d-134">Pour plus d’informations sur le format d’action pour chaque opération, consultez [Messages et des schémas de message](messages-and-message-schemas-for-biztalk-adapter-for-sql-server.md).</span><span class="sxs-lookup"><span data-stu-id="c3b3d-134">For more information about the action format for each operation, see [Messages and message schemas](messages-and-message-schemas-for-biztalk-adapter-for-sql-server.md).</span></span>
  
### <a name="enter-a-soap-action-for-the-wcf-sql-port"></a><span data-ttu-id="c3b3d-135">Entrez une action SOAP pour le port WCF-SQL</span><span class="sxs-lookup"><span data-stu-id="c3b3d-135">Enter a SOAP action for the WCF-SQL port</span></span>  
  
1.  <span data-ttu-id="c3b3d-136">Démarrer le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.</span><span class="sxs-lookup"><span data-stu-id="c3b3d-136">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2.  <span data-ttu-id="c3b3d-137">Ajouter l’adaptateur WCF-SQL pour le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.</span><span class="sxs-lookup"><span data-stu-id="c3b3d-137">Add the WCF-SQL adapter to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="c3b3d-138">Pour obtenir des instructions, consultez [Ajout de l’adaptateur SQL à la Console Administration de BizTalk Server](../../adapters-and-accelerators/adapter-sql/adding-the-sql-adapter-to-biztalk-server-administration-console.md).</span><span class="sxs-lookup"><span data-stu-id="c3b3d-138">For instructions, see [Adding the SQL Adapter to BizTalk Server Administration Console](../../adapters-and-accelerators/adapter-sql/adding-the-sql-adapter-to-biztalk-server-administration-console.md).</span></span>  
  
3.  <span data-ttu-id="c3b3d-139">Dans l’arborescence de la console, développez **groupe BizTalk**, puis développez **Applications**, puis cliquez sur **Ports d’envoi**.</span><span class="sxs-lookup"><span data-stu-id="c3b3d-139">In the console tree, expand **BizTalk Group**, then expand **Applications**, and then click **Send Ports**.</span></span> <span data-ttu-id="c3b3d-140">Dans le volet droit, vous pouvez choisir de créer un port ou de sélectionner un port existant.</span><span class="sxs-lookup"><span data-stu-id="c3b3d-140">In the right pane, you can choose to create a port or select an existing port.</span></span>  
  
4.  <span data-ttu-id="c3b3d-141">Dans la boîte de dialogue Propriétés du port, à partir de la **Type** la liste déroulante, sélectionnez l’adaptateur WCF-SQL que vous avez ajouté précédemment, puis cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="c3b3d-141">In the port properties dialog box, from the **Type** drop-down list, select the WCF-SQL adapter you added earlier, and then click **Configure**.</span></span>  
  
5.  <span data-ttu-id="c3b3d-142">Dans la boîte de dialogue Propriétés du transport, cliquez sur le **général** onglet.</span><span class="sxs-lookup"><span data-stu-id="c3b3d-142">In the transport properties dialog box, click the **General** tab.</span></span>  
  
6.  <span data-ttu-id="c3b3d-143">Dans le **Action** texte, spécifiez l’action SOAP pour l’opération.</span><span class="sxs-lookup"><span data-stu-id="c3b3d-143">In the **Action** text box, specify the SOAP action for the operation.</span></span> <span data-ttu-id="c3b3d-144">Vous pouvez spécifier l’action comme suit :</span><span class="sxs-lookup"><span data-stu-id="c3b3d-144">You can specify the action in the following ways:</span></span>  
  
    -   <span data-ttu-id="c3b3d-145">**En utilisant le format d’action unique**.</span><span class="sxs-lookup"><span data-stu-id="c3b3d-145">**By using the single action format**.</span></span> <span data-ttu-id="c3b3d-146">Utilisez ce format si le WCF-SQL port envoie et recevoir des messages pour une seule opération.</span><span class="sxs-lookup"><span data-stu-id="c3b3d-146">Use this format if the WCF-SQL port sends and receive messages for a single operation.</span></span> <span data-ttu-id="c3b3d-147">Exemple :</span><span class="sxs-lookup"><span data-stu-id="c3b3d-147">For example:</span></span>  
  
        ```  
        TableOp/Insert/dbo/Employee  
        ```  
  
    -   <span data-ttu-id="c3b3d-148">**En utilisant le format de mappage d’action**.</span><span class="sxs-lookup"><span data-stu-id="c3b3d-148">**By using the action mapping format**.</span></span> <span data-ttu-id="c3b3d-149">Utilisez ce format, si un seul port WCF-SQL envoie et reçoit des messages pour plusieurs opérations.</span><span class="sxs-lookup"><span data-stu-id="c3b3d-149">Use this format if a single WCF-SQL port sends and receives messages for more than one operation.</span></span> <span data-ttu-id="c3b3d-150">Par exemple, si un seul port WCF-SQL envoie et reçoit des messages pour Op1 (pour insérer des enregistrements dans la table Employee) et Op2 (pour mettre à jour des enregistrements dans la table Employee), l’action SOAP peut être spécifiée de la manière suivante :</span><span class="sxs-lookup"><span data-stu-id="c3b3d-150">For example, if a single WCF-SQL port sends and receives messages for Op1 (to insert records in the Employee table) and Op2 (to update records in the Employee table), the SOAP action can be specified in the following manner:</span></span>  
  
        ```  
        <BtsActionMapping>  
          <Operation Name="Op1" Action="TableOp/Insert/dbo/Employee" />  
          <Operation Name="Op2" Action="TableOp/Update/dbo/Employee" />  
        </BtsActionMapping>  
        ```  
  
         <span data-ttu-id="c3b3d-151">L’approche de mappage d’action fournit une plus grande flexibilité en termes de spécification d’un ensemble d’actions et par conséquent, l’activation de messages qui appartiennent à une action différente des types de circuler via le même port.</span><span class="sxs-lookup"><span data-stu-id="c3b3d-151">The action mapping approach provides greater flexibility in terms of specifying a set of actions, and hence enabling messages that belong to different action types to flow through the same port.</span></span>  
  
         <span data-ttu-id="c3b3d-152">Le format de l’action SOAP est différent pour chaque opération.</span><span class="sxs-lookup"><span data-stu-id="c3b3d-152">The format for the SOAP action is different for each operation.</span></span> <span data-ttu-id="c3b3d-153">Pour plus d’informations sur le format d’action pour chaque opération, consultez [Messages et des schémas de message](messages-and-message-schemas-for-biztalk-adapter-for-sql-server.md).</span><span class="sxs-lookup"><span data-stu-id="c3b3d-153">For more information about the action format for each operation, see [Messages and message schemas](messages-and-message-schemas-for-biztalk-adapter-for-sql-server.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="c3b3d-154">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c3b3d-154">See Also</span></span>  
[<span data-ttu-id="c3b3d-155">Blocs de construction pour développer des applications BizTalk à l’adaptateur SQL</span><span class="sxs-lookup"><span data-stu-id="c3b3d-155">Building blocks to develop BizTalk applications with the SQL adapter</span></span>](../../adapters-and-accelerators/adapter-sql/building-blocks-to-develop-biztalk-applications-with-the-sql-adapter.md)