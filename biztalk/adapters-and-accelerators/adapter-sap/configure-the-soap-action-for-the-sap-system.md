---
title: "Configurer l’action SOAP pour le système SAP dans BizTalk | Documents Microsoft"
description: "Entrez une action SOAP dans la forme Expression, ou utiliser l’adaptateur WCF-Custom ou WCF-SAP dans le Pack de l’adaptateur BizTalk (LOB)"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 76084bc5-7a10-4c4c-be22-bee83779a011
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 36a474d53d3fcaf61668800094a1d98d0e061aa5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configure-the-soap-action-for-the-sap-system"></a><span data-ttu-id="dfe1d-103">Configuration de l’action SOAP pour le système SAP</span><span class="sxs-lookup"><span data-stu-id="dfe1d-103">Configure the SOAP action for the SAP system</span></span>
<span data-ttu-id="dfe1d-104">Pour effectuer des opérations sur le système SAP à l’aide de la station de travail WCF [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], les utilisateurs de l’adaptateur doivent spécifier une action SOAP.</span><span class="sxs-lookup"><span data-stu-id="dfe1d-104">To perform any operation on the SAP system using the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], adapter users must specify a SOAP action.</span></span> <span data-ttu-id="dfe1d-105">L’action SOAP communique à l’adaptateur quelle action doit être effectuée.</span><span class="sxs-lookup"><span data-stu-id="dfe1d-105">The SOAP action communicates to the adapter what action should be performed.</span></span> <span data-ttu-id="dfe1d-106">Vous pouvez spécifier l’action SOAP au moment du design ou au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="dfe1d-106">You can specify the SOAP action either at design time or at run time.</span></span> <span data-ttu-id="dfe1d-107">Toutefois, si vous spécifiez l’action SOAP à la fois au moment du design et moment de l’exécution, l’action que vous avez spécifié au moment du design est remplacée.</span><span class="sxs-lookup"><span data-stu-id="dfe1d-107">However, if you specify the SOAP action both at design time and run time, the action you specified at design time will be overridden.</span></span>  
  
 <span data-ttu-id="dfe1d-108">Pour plus d’informations sur la spécification d’action SOAP, consultez [spécifiant les Actions SOAP pour les adaptateurs d’envoi WCF](../../core/specifying-soap-actions-for-wcf-send-adapters.md).</span><span class="sxs-lookup"><span data-stu-id="dfe1d-108">For more information about specifying SOAP action, see [Specifying SOAP Actions for WCF Send Adapters](../../core/specifying-soap-actions-for-wcf-send-adapters.md).</span></span>
  
## <a name="enter-soap-action-at-design-time"></a><span data-ttu-id="dfe1d-109">Entrez l’Action SOAP au moment du Design</span><span class="sxs-lookup"><span data-stu-id="dfe1d-109">Enter SOAP Action at Design Time</span></span>  
 <span data-ttu-id="dfe1d-110">Pour le moment du design, vous devez spécifier l’action SOAP dans le cadre de l’orchestration en incluant une forme expression.</span><span class="sxs-lookup"><span data-stu-id="dfe1d-110">For design time, you must specify the SOAP action as part of orchestration by including an expression shape.</span></span>  
  
 
1.  <span data-ttu-id="dfe1d-111">Dans l’orchestration BizTalk, inclure une forme Expression en le faisant glisser à partir de la **Orchestration BizTalk** boîte à outils.</span><span class="sxs-lookup"><span data-stu-id="dfe1d-111">In the BizTalk orchestration, include an Expression shape by dragging it from the **BizTalk Orchestration** toolbox.</span></span>  
  
2.  <span data-ttu-id="dfe1d-112">Double-cliquez sur le **Expression** forme pour ouvrir l’éditeur d’Expression BizTalk.</span><span class="sxs-lookup"><span data-stu-id="dfe1d-112">Double-click the **Expression** shape to open the BizTalk Expression Editor.</span></span>  
  
3.  <span data-ttu-id="dfe1d-113">Spécifiez l’action dans l’éditeur d’Expression BizTalk.</span><span class="sxs-lookup"><span data-stu-id="dfe1d-113">Specify the action in the BizTalk Expression Editor.</span></span> <span data-ttu-id="dfe1d-114">Exemple :</span><span class="sxs-lookup"><span data-stu-id="dfe1d-114">For example:</span></span>  
  
    ```  
    OutboundMessage(WCF.Action)="http://Microsoft.LobServices.Sap/2007/03/Rfc/RFC_CUSTOMER_GET"  
    ```  
  
     <span data-ttu-id="dfe1d-115">Pour plus d’informations sur la **Expression** forme et l’éditeur d’Expression BizTalk, consultez [comment créer des Expressions](../../core/how-to-create-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="dfe1d-115">For more information about the **Expression** shape and the BizTalk Expression Editor, see [How to Create Expressions](../../core/how-to-create-expressions.md).</span></span>
  
## <a name="enter-soap-action-at-run-time"></a><span data-ttu-id="dfe1d-116">Entrez l’Action SOAP en cours d’exécution</span><span class="sxs-lookup"><span data-stu-id="dfe1d-116">Enter SOAP Action at Run Time</span></span>  
 <span data-ttu-id="dfe1d-117">Temps d’exécution, vous pouvez spécifier l’action SOAP dans le cadre de la configuration du port WCF-Custom ou WCF-SAP.</span><span class="sxs-lookup"><span data-stu-id="dfe1d-117">For run time, you can specify the SOAP action as part of the WCF-Custom or WCF-SAP port configuration.</span></span>  
  
### <a name="enter-a-soap-action-for-the-wcf-custom-port"></a><span data-ttu-id="dfe1d-118">Entrez une action SOAP pour le port WCF-Custom</span><span class="sxs-lookup"><span data-stu-id="dfe1d-118">Enter a SOAP action for the WCF-Custom port</span></span>  
  
1.  <span data-ttu-id="dfe1d-119">Démarrer le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.</span><span class="sxs-lookup"><span data-stu-id="dfe1d-119">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2.  <span data-ttu-id="dfe1d-120">Dans l’arborescence de la console, développez **groupe BizTalk**, puis développez **Applications**, puis cliquez sur **Ports d’envoi**.</span><span class="sxs-lookup"><span data-stu-id="dfe1d-120">In the console tree, expand **BizTalk Group**, then expand **Applications**, and then click **Send Ports**.</span></span> <span data-ttu-id="dfe1d-121">Dans le volet droit, vous pouvez choisir de créer un port ou de sélectionner un port existant.</span><span class="sxs-lookup"><span data-stu-id="dfe1d-121">In the right pane, you can choose to create a port or select an existing port.</span></span>  
  
3.  <span data-ttu-id="dfe1d-122">Dans la boîte de dialogue Propriétés du port, à partir de la **Type** la liste déroulante, sélectionnez **WCF-Custom**, puis cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="dfe1d-122">In the port properties dialog box, from the **Type** drop-down list, select **WCF-Custom**, and then click **Configure**.</span></span>  
  
4.  <span data-ttu-id="dfe1d-123">Dans le **propriétés du Transport WCF-Custom** boîte de dialogue, cliquez sur le **général** onglet.</span><span class="sxs-lookup"><span data-stu-id="dfe1d-123">In the **WCF-Custom Transport Properties** dialog box, click the **General** tab.</span></span>  
  
5.  <span data-ttu-id="dfe1d-124">Dans le **Action** texte, spécifiez l’action SOAP pour l’opération.</span><span class="sxs-lookup"><span data-stu-id="dfe1d-124">In the **Action** text box, specify the SOAP action for the operation.</span></span> <span data-ttu-id="dfe1d-125">Vous pouvez spécifier l’action comme suit :</span><span class="sxs-lookup"><span data-stu-id="dfe1d-125">You can specify the action in the following ways:</span></span>  
  
    -   <span data-ttu-id="dfe1d-126">**En utilisant le format d’action unique**.</span><span class="sxs-lookup"><span data-stu-id="dfe1d-126">**By using the single action format**.</span></span> <span data-ttu-id="dfe1d-127">Utilisez ce format si WCF-Custom port envoie et recevoir des messages pour une seule opération.</span><span class="sxs-lookup"><span data-stu-id="dfe1d-127">Use this format if the WCF-Custom port sends and receive messages for a single operation.</span></span> <span data-ttu-id="dfe1d-128">Exemple :</span><span class="sxs-lookup"><span data-stu-id="dfe1d-128">For example:</span></span>  
  
        ```  
        http://Microsoft.LobServices.Sap/2007/03/Rfc/RFC_CUSTOMER_GET  
        ```  
  
    -   <span data-ttu-id="dfe1d-129">**En utilisant le format de mappage d’action**.</span><span class="sxs-lookup"><span data-stu-id="dfe1d-129">**By using the action mapping format**.</span></span> <span data-ttu-id="dfe1d-130">Utilisez ce format, si un seul port WCF-Custom envoie et reçoit des messages pour plusieurs opérations.</span><span class="sxs-lookup"><span data-stu-id="dfe1d-130">Use this format if a single WCF-Custom port sends and receives messages for more than one operation.</span></span> <span data-ttu-id="dfe1d-131">Par exemple, si un seul port WCF-Custom envoie et reçoit des messages pour Op1 (pour appeler RFC_CUSTOMER_GET RFC) et Op2 (pour appeler BAPI_SALESORDER_CREATEFROMDAT2 BAPI), l’action SOAP peut être spécifiée de la manière suivante :</span><span class="sxs-lookup"><span data-stu-id="dfe1d-131">For example, if a single WCF-Custom port sends and receives messages for Op1 (to invoke RFC_CUSTOMER_GET RFC) and Op2 (to invoke BAPI_SALESORDER_CREATEFROMDAT2 BAPI), the SOAP action can be specified in the following manner:</span></span>  
  
        ```  
        <BtsActionMapping>  
          <Operation Name="Op1" Action="http://Microsoft.LobServices.Sap/2007/03/Rfc/RFC_CUSTOMER_GET " />  
          <Operation Name="Op2" Action="http://Microsoft.LobServices.Sap/2007/03/Bapi/BUS2032/CREATEFROMDAT2/BAPI_SALESORDER_CREATEFROMDAT2" />  
        </BtsActionMapping>  
        ```  
  
         <span data-ttu-id="dfe1d-132">Cette approche offre une plus grande flexibilité en termes de spécification d’un ensemble d’actions et par conséquent, l’activation de messages appartenant à des types d’actions différentes de circuler via le même port.</span><span class="sxs-lookup"><span data-stu-id="dfe1d-132">This approach provides greater flexibility in terms of specifying a set of actions and hence enabling messages belonging to different action types to flow through the same port.</span></span>  
  
         <span data-ttu-id="dfe1d-133">Le format de l’action SOAP est différent pour chaque opération.</span><span class="sxs-lookup"><span data-stu-id="dfe1d-133">The format for the SOAP action is different for each operation.</span></span> <span data-ttu-id="dfe1d-134">Pour plus d’informations sur le format d’action pour chaque opération, consultez [Messages et des schémas de message](messages-and-message-schemas-for-biztalk-adapter-for-mysap-business-suite.md).</span><span class="sxs-lookup"><span data-stu-id="dfe1d-134">For more information about action format for each operation, see [Messages and message schemas](messages-and-message-schemas-for-biztalk-adapter-for-mysap-business-suite.md).</span></span>
  
### <a name="enter-a-soap-action-for-the-wcf-sap-port"></a><span data-ttu-id="dfe1d-135">Entrez une action SOAP pour le port WCF SAP</span><span class="sxs-lookup"><span data-stu-id="dfe1d-135">Enter a SOAP action for the WCF-SAP port</span></span>  
  
1.  <span data-ttu-id="dfe1d-136">Démarrer le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.</span><span class="sxs-lookup"><span data-stu-id="dfe1d-136">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2.  <span data-ttu-id="dfe1d-137">Ajouter l’adaptateur WCF-SAP pour le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.</span><span class="sxs-lookup"><span data-stu-id="dfe1d-137">Add the WCF-SAP adapter to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="dfe1d-138">Pour obtenir des instructions, consultez [ajouter l’adaptateur SAP à la Console Administration de BizTalk Server](../../adapters-and-accelerators/adapter-sap/add-the-sap-adapter-to-biztalk-server-administration-console.md).</span><span class="sxs-lookup"><span data-stu-id="dfe1d-138">For instructions, see [Add the SAP Adapter to BizTalk Server Administration Console](../../adapters-and-accelerators/adapter-sap/add-the-sap-adapter-to-biztalk-server-administration-console.md).</span></span>  
  
3.  <span data-ttu-id="dfe1d-139">Dans l’arborescence de la console, développez **groupe BizTalk**, puis développez **Applications**, puis cliquez sur **Ports d’envoi**.</span><span class="sxs-lookup"><span data-stu-id="dfe1d-139">In the console tree, expand **BizTalk Group**, then expand **Applications**, and then click **Send Ports**.</span></span> <span data-ttu-id="dfe1d-140">Dans le volet droit, vous pouvez choisir de créer un port ou de sélectionner un port existant.</span><span class="sxs-lookup"><span data-stu-id="dfe1d-140">In the right pane, you can choose to create a port or select an existing port.</span></span>  
  
4.  <span data-ttu-id="dfe1d-141">Dans la boîte de dialogue Propriétés du port, à partir de la **Type** la liste déroulante, sélectionnez l’adaptateur WCF-SAP que vous avez ajouté précédemment, puis cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="dfe1d-141">In the port properties dialog box, from the **Type** drop-down list, select the WCF-SAP adapter you added earlier, and then click **Configure**.</span></span>  
  
5.  <span data-ttu-id="dfe1d-142">Dans la boîte de dialogue Propriétés du transport, cliquez sur le **général** onglet.</span><span class="sxs-lookup"><span data-stu-id="dfe1d-142">In the transport properties dialog box, click the **General** tab.</span></span>  
  
6.  <span data-ttu-id="dfe1d-143">Dans le **Action** texte, spécifiez l’action SOAP pour l’opération.</span><span class="sxs-lookup"><span data-stu-id="dfe1d-143">In the **Action** text box, specify the SOAP action for the operation.</span></span> <span data-ttu-id="dfe1d-144">Vous pouvez spécifier l’action comme suit :</span><span class="sxs-lookup"><span data-stu-id="dfe1d-144">You can specify the action in the following ways:</span></span>  
  
    -   <span data-ttu-id="dfe1d-145">**En utilisant le format d’action unique**.</span><span class="sxs-lookup"><span data-stu-id="dfe1d-145">**By using the single action format**.</span></span> <span data-ttu-id="dfe1d-146">Utilisez ce format si WCF-Custom port envoie et recevoir des messages pour une seule opération.</span><span class="sxs-lookup"><span data-stu-id="dfe1d-146">Use this format if the WCF-Custom port sends and receive messages for a single operation.</span></span> <span data-ttu-id="dfe1d-147">Exemple :</span><span class="sxs-lookup"><span data-stu-id="dfe1d-147">For example:</span></span>  
  
        ```  
        http://Microsoft.LobServices.Sap/2007/03/Rfc/RFC_CUSTOMER_GET  
        ```  
  
    -   <span data-ttu-id="dfe1d-148">**En utilisant le format de mappage d’action**.</span><span class="sxs-lookup"><span data-stu-id="dfe1d-148">**By using the action mapping format**.</span></span> <span data-ttu-id="dfe1d-149">Utilisez ce format, si un seul port WCF-Custom envoie et reçoit des messages pour plusieurs opérations.</span><span class="sxs-lookup"><span data-stu-id="dfe1d-149">Use this format if a single WCF-Custom port sends and receives messages for more than one operation.</span></span> <span data-ttu-id="dfe1d-150">Par exemple, si un seul port WCF-Custom envoie et reçoit des messages pour Op1 (pour appeler RFC_CUSTOMER_GET RFC) et Op2 (pour appeler BAPI_SALESORDER_CREATEFROMDAT2 BAPI), l’action SOAP peut être spécifiée de la manière suivante :</span><span class="sxs-lookup"><span data-stu-id="dfe1d-150">For example, if a single WCF-Custom port sends and receives messages for Op1 (to invoke RFC_CUSTOMER_GET RFC) and Op2 (to invoke BAPI_SALESORDER_CREATEFROMDAT2 BAPI), the SOAP action can be specified in the following manner:</span></span>  
  
        ```  
        <BtsActionMapping>  
          <Operation Name="Op1" Action="http://Microsoft.LobServices.Sap/2007/03/Rfc/RFC_CUSTOMER_GET " />  
          <Operation Name="Op2" Action="http://Microsoft.LobServices.Sap/2007/03/Bapi/BUS2032/CREATEFROMDAT2/BAPI_SALESORDER_CREATEFROMDAT2" />  
        </BtsActionMapping>  
        ```  
  
         <span data-ttu-id="dfe1d-151">Cette approche offre une plus grande flexibilité en termes de spécification d’un ensemble d’actions et par conséquent, l’activation de messages appartenant à des types d’actions différentes de circuler via le même port.</span><span class="sxs-lookup"><span data-stu-id="dfe1d-151">This approach provides greater flexibility in terms of specifying a set of actions and hence enabling messages belonging to different action types to flow through the same port.</span></span>  
  
         <span data-ttu-id="dfe1d-152">Le format de l’action SOAP est différent pour chaque opération.</span><span class="sxs-lookup"><span data-stu-id="dfe1d-152">The format for the SOAP action is different for each operation.</span></span> <span data-ttu-id="dfe1d-153">Pour plus d’informations sur le format d’action pour chaque opération, consultez [Messages et des schémas de message](messages-and-message-schemas-for-biztalk-adapter-for-mysap-business-suite.md).</span><span class="sxs-lookup"><span data-stu-id="dfe1d-153">For more information about action format for each operation, see [Messages and message schemas](messages-and-message-schemas-for-biztalk-adapter-for-mysap-business-suite.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="dfe1d-154">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dfe1d-154">See Also</span></span>  
[<span data-ttu-id="dfe1d-155">Blocs de construction pour créer des applications SAP</span><span class="sxs-lookup"><span data-stu-id="dfe1d-155">Building blocks to create SAP applications</span></span>](../../adapters-and-accelerators/adapter-sap/building-blocks-to-create-sap-applications.md)