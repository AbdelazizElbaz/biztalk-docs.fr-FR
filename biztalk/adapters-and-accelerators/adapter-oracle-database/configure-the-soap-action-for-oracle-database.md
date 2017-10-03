---
title: "Configurer l’action SOAP pour la base de données Oracle dans BizTalk | Documents Microsoft"
description: "Entrez une action SOAP dans Visual Studio, ou utiliser l’adaptateur WCF-Custom ou WCF-OracleDB dans le Pack de l’adaptateur BizTalk (LOB)"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d0d21cca-3907-4f99-af76-c1e7286e1bcf
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b2577a221385cdef2e210798b3e8170433ff0e48
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configure-the-soap-action-for-oracle-database"></a><span data-ttu-id="aa0eb-103">Configurer l’action SOAP pour la base de données Oracle</span><span class="sxs-lookup"><span data-stu-id="aa0eb-103">Configure the SOAP action for Oracle Database</span></span>
<span data-ttu-id="aa0eb-104">Pour effectuer toutes les opérations sur la base de données Oracle à l’aide de la station de travail WCF [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], les utilisateurs de l’adaptateur doivent entrer une action SOAP.</span><span class="sxs-lookup"><span data-stu-id="aa0eb-104">To complete any operation on the Oracle database using the WCF-based [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], adapter users must enter a SOAP action.</span></span> <span data-ttu-id="aa0eb-105">L’action SOAP communique à l’adaptateur quelle action doit être terminée.</span><span class="sxs-lookup"><span data-stu-id="aa0eb-105">The SOAP action communicates to the adapter what action should be completed.</span></span> <span data-ttu-id="aa0eb-106">Vous pouvez entrer l’action SOAP au moment du design ou au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="aa0eb-106">You can enter the SOAP action either at design time or at run time.</span></span> <span data-ttu-id="aa0eb-107">Toutefois, si vous entrez l’action SOAP à la fois au moment du design et moment de l’exécution, l’action que vous entrez au moment du design est modifiée.</span><span class="sxs-lookup"><span data-stu-id="aa0eb-107">However, if you enter the SOAP action both at design time and run time, the action you enter at design time is overridden.</span></span>  
  
 <span data-ttu-id="aa0eb-108">Pour plus d’informations sur la spécification d’action SOAP, consultez [spécifiant les Actions SOAP pour les adaptateurs d’envoi WCF](../../core/specifying-soap-actions-for-wcf-send-adapters.md).</span><span class="sxs-lookup"><span data-stu-id="aa0eb-108">For more information about specifying SOAP action, see [Specifying SOAP Actions for WCF Send Adapters](../../core/specifying-soap-actions-for-wcf-send-adapters.md).</span></span>  
  
## <a name="enter-soap-action-from-visual-studio"></a><span data-ttu-id="aa0eb-109">Entrez l’Action SOAP à partir de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="aa0eb-109">Enter SOAP Action from Visual Studio</span></span>  
 <span data-ttu-id="aa0eb-110">À partir de Visual Studio, vous devez spécifier l’action SOAP dans le cadre de l’orchestration en utilisant une **Expression** forme.</span><span class="sxs-lookup"><span data-stu-id="aa0eb-110">From Visual Studio, you must specify the SOAP action as part of the orchestration by using an **Expression** shape.</span></span>  
  
1.  <span data-ttu-id="aa0eb-111">Dans l’orchestration BizTalk, vous devez inclure une **Expression** forme en le faisant glisser à partir de la **Orchestration BizTalk** boîte à outils.</span><span class="sxs-lookup"><span data-stu-id="aa0eb-111">In the BizTalk orchestration, include an **Expression** shape by dragging it from the **BizTalk Orchestration** toolbox.</span></span>  
  
2.  <span data-ttu-id="aa0eb-112">Double-cliquez sur le **Expression** forme pour ouvrir l’éditeur d’Expression BizTalk.</span><span class="sxs-lookup"><span data-stu-id="aa0eb-112">Double-click the **Expression** shape to open the BizTalk Expression Editor.</span></span>  
  
3.  <span data-ttu-id="aa0eb-113">Spécifiez l’action dans l’éditeur d’Expression BizTalk.</span><span class="sxs-lookup"><span data-stu-id="aa0eb-113">Specify the action in the BizTalk Expression Editor.</span></span> <span data-ttu-id="aa0eb-114">Exemple :</span><span class="sxs-lookup"><span data-stu-id="aa0eb-114">For example:</span></span>  
  
    ```
    OutboundMessage(WCF.Action)="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Insert"  
    ```  
  
     <span data-ttu-id="aa0eb-115">Pour plus d’informations sur **Expression** forme et l’éditeur d’Expression BizTalk, consultez [comment créer des Expressions](../../core/how-to-create-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="aa0eb-115">For more information about **Expression** shape and the BizTalk Expression Editor, see [How to Create Expressions](../../core/how-to-create-expressions.md).</span></span>  
  
## <a name="enter-soap-action-from-biztalk-server-administration"></a><span data-ttu-id="aa0eb-116">Entrez l’Action SOAP à partir de l’Administration de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="aa0eb-116">Enter SOAP Action from BizTalk Server Administration</span></span>  
 <span data-ttu-id="aa0eb-117">Dans la console Administration de BizTalk Server, vous devez spécifier l’action SOAP dans le cadre de la configuration du port WCF-Custom ou WCF-OracleDB.</span><span class="sxs-lookup"><span data-stu-id="aa0eb-117">From the BizTalk Server Administration console, you must specify the SOAP action as part of the WCF-Custom or WCF-OracleDB port configuration.</span></span> 

#### <a name="enter-a-soap-action-for-the-wcf-custom-port"></a><span data-ttu-id="aa0eb-118">Entrez une action SOAP pour le port WCF-Custom</span><span class="sxs-lookup"><span data-stu-id="aa0eb-118">Enter a SOAP action for the WCF-Custom port</span></span>  
 
  
1.  <span data-ttu-id="aa0eb-119">Démarrer le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.</span><span class="sxs-lookup"><span data-stu-id="aa0eb-119">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2.  <span data-ttu-id="aa0eb-120">Dans l’arborescence de la console, développez **groupe BizTalk**, puis développez **Applications**, puis développez l’application sous lequel vous souhaitez créer un port, puis cliquez sur **Ports d’envoi**.</span><span class="sxs-lookup"><span data-stu-id="aa0eb-120">In the console tree, expand **BizTalk Group**, then expand **Applications**, then expand the application under which you want to create a port, and then click **Send Ports**.</span></span> <span data-ttu-id="aa0eb-121">Dans le volet droit, vous pouvez choisir de créer un port ou de sélectionner un port existant.</span><span class="sxs-lookup"><span data-stu-id="aa0eb-121">In the right pane, you can choose to create a port or select an existing port.</span></span>  
  
3.  <span data-ttu-id="aa0eb-122">Dans la boîte de dialogue Propriétés du port, à partir de la **Type** la liste déroulante, sélectionnez **WCF-Custom**, puis cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="aa0eb-122">In the port properties dialog box, from the **Type** drop-down list, select **WCF-Custom**, and then click **Configure**.</span></span>  
  
4.  <span data-ttu-id="aa0eb-123">Dans le **propriétés du Transport WCF-Custom** boîte de dialogue, cliquez sur le **général** onglet.</span><span class="sxs-lookup"><span data-stu-id="aa0eb-123">In the **WCF-Custom Transport Properties** dialog box, click the **General** tab.</span></span>  
  
5.  <span data-ttu-id="aa0eb-124">Dans le **Action** texte, spécifiez l’action SOAP pour l’opération.</span><span class="sxs-lookup"><span data-stu-id="aa0eb-124">In the **Action** text box, specify the SOAP action for the operation.</span></span> <span data-ttu-id="aa0eb-125">Vous pouvez spécifier l’action comme suit :</span><span class="sxs-lookup"><span data-stu-id="aa0eb-125">You can specify the action in the following ways:</span></span>  
  
    -   <span data-ttu-id="aa0eb-126">**En utilisant le format d’action unique**.</span><span class="sxs-lookup"><span data-stu-id="aa0eb-126">**By using the single action format**.</span></span> <span data-ttu-id="aa0eb-127">Utilisez ce format si WCF-Custom port envoie et recevoir des messages pour une seule opération.</span><span class="sxs-lookup"><span data-stu-id="aa0eb-127">Use this format if the WCF-Custom port sends and receive messages for a single operation.</span></span> <span data-ttu-id="aa0eb-128">Exemple :</span><span class="sxs-lookup"><span data-stu-id="aa0eb-128">For example:</span></span>  
  
        ```  
        http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Insert  
        ```  
  
    -   <span data-ttu-id="aa0eb-129">**En utilisant le format de mappage d’action**.</span><span class="sxs-lookup"><span data-stu-id="aa0eb-129">**By using the action mapping format**.</span></span> <span data-ttu-id="aa0eb-130">Utilisez ce format, si un seul port WCF-Custom envoie et reçoit des messages pour plusieurs opérations.</span><span class="sxs-lookup"><span data-stu-id="aa0eb-130">Use this format if a single WCF-Custom port sends and receives messages for more than one operation.</span></span> <span data-ttu-id="aa0eb-131">Par exemple, si un seul port WCF-Custom envoie et reçoit des messages pour Op1 (pour insérer des enregistrements dans la table EMP) et Op2 (pour mettre à jour des enregistrements dans la table EMP), l’action SOAP peut être spécifiée de la manière suivante :</span><span class="sxs-lookup"><span data-stu-id="aa0eb-131">For example, if a single WCF-Custom port sends and receives messages for Op1 (to insert records in the EMP table) and Op2 (to update records in the EMP table), the SOAP action can be specified in the following manner:</span></span>  
  
        ```  
        <BtsActionMapping>  
          <Operation Name="Op1" Action="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Insert" />  
          <Operation Name="Op2" Action="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Update " />  
        </BtsActionMapping>  
        ```  
  
         <span data-ttu-id="aa0eb-132">Cette approche offre une plus grande flexibilité en termes de spécification d’un ensemble d’actions et par conséquent, l’activation de messages appartenant à des types d’actions différentes de circuler via le même port.</span><span class="sxs-lookup"><span data-stu-id="aa0eb-132">This approach provides greater flexibility in terms of specifying a set of actions and hence enabling messages belonging to different action types to flow through the same port.</span></span>  
  
         <span data-ttu-id="aa0eb-133">Le format de l’action SOAP est différent pour chaque opération.</span><span class="sxs-lookup"><span data-stu-id="aa0eb-133">The format for the SOAP action is different for each operation.</span></span> <span data-ttu-id="aa0eb-134">Pour plus d’informations sur le format d’action pour chaque opération, consultez [Messages et des schémas de Message](messages-and-message-schemas-for-biztalk-adapter-for-oracle-database.md).</span><span class="sxs-lookup"><span data-stu-id="aa0eb-134">For more information about action format for each operation, see [Messages and Message Schemas](messages-and-message-schemas-for-biztalk-adapter-for-oracle-database.md).</span></span>  
  
#### <a name="enter-a-soap-action-for-the-wcf-oracledb-port"></a><span data-ttu-id="aa0eb-135">Entrez une action SOAP pour le port WCF-OracleDB</span><span class="sxs-lookup"><span data-stu-id="aa0eb-135">Enter a SOAP action for the WCF-OracleDB port</span></span>  
  
1.  <span data-ttu-id="aa0eb-136">Démarrer le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.</span><span class="sxs-lookup"><span data-stu-id="aa0eb-136">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2.  <span data-ttu-id="aa0eb-137">Ajouter l’adaptateur WCF-OracleDB à la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="aa0eb-137">Add the WCF-OracleDB adapter to the BizTalk Server Administration console.</span></span> <span data-ttu-id="aa0eb-138">Pour obtenir des instructions, consultez [Ajout de l’adaptateur de base de données Oracle à la Console Administration de BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/adding-the-oracle-database-adapter-to-biztalk-server-administration-console.md).</span><span class="sxs-lookup"><span data-stu-id="aa0eb-138">For instructions, see [Adding the Oracle Database Adapter to BizTalk Server Administration Console](../../adapters-and-accelerators/adapter-oracle-database/adding-the-oracle-database-adapter-to-biztalk-server-administration-console.md).</span></span>  
  
3.  <span data-ttu-id="aa0eb-139">Dans l’arborescence de la console, développez **groupe BizTalk**, puis développez **Applications**, puis développez l’application sous lequel vous souhaitez créer un port, puis cliquez sur **Ports d’envoi**.</span><span class="sxs-lookup"><span data-stu-id="aa0eb-139">In the console tree, expand **BizTalk Group**, then expand **Applications**, then expand the application under which you want to create a port, and then click **Send Ports**.</span></span> <span data-ttu-id="aa0eb-140">Dans le volet droit, vous pouvez choisir de créer un port ou de sélectionner un port existant.</span><span class="sxs-lookup"><span data-stu-id="aa0eb-140">In the right pane, you can choose to create a port or select an existing port.</span></span>  
  
4.  <span data-ttu-id="aa0eb-141">Dans la boîte de dialogue Propriétés du port, à partir de la **Type** la liste déroulante, sélectionnez le port WCF-OracleDB que vous avez ajouté précédemment, puis cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="aa0eb-141">In the port properties dialog box, from the **Type** drop-down list, select the WCF-OracleDB port you added earlier, and then click **Configure**.</span></span>  
  
5.  <span data-ttu-id="aa0eb-142">Dans le **propriétés du Transport WCF-Custom** boîte de dialogue, cliquez sur le **général** onglet.</span><span class="sxs-lookup"><span data-stu-id="aa0eb-142">In the **WCF-Custom Transport Properties** dialog box, click the **General** tab.</span></span>  
  
6.  <span data-ttu-id="aa0eb-143">Dans le **Action** texte, spécifiez l’action SOAP pour l’opération.</span><span class="sxs-lookup"><span data-stu-id="aa0eb-143">In the **Action** text box, specify the SOAP action for the operation.</span></span> <span data-ttu-id="aa0eb-144">Vous pouvez spécifier l’action comme suit :</span><span class="sxs-lookup"><span data-stu-id="aa0eb-144">You can specify the action in the following ways:</span></span>  
  
    -   <span data-ttu-id="aa0eb-145">**En utilisant le format d’action unique**.</span><span class="sxs-lookup"><span data-stu-id="aa0eb-145">**By using the single action format**.</span></span> <span data-ttu-id="aa0eb-146">Utilisez ce format si le WCF-OracleDB port envoie et recevoir des messages pour une seule opération.</span><span class="sxs-lookup"><span data-stu-id="aa0eb-146">Use this format if the WCF-OracleDB port sends and receive messages for a single operation.</span></span> <span data-ttu-id="aa0eb-147">Exemple :</span><span class="sxs-lookup"><span data-stu-id="aa0eb-147">For example:</span></span>  
  
        ```  
        http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Insert  
        ```  
  
    -   <span data-ttu-id="aa0eb-148">**En utilisant le format de mappage d’action**.</span><span class="sxs-lookup"><span data-stu-id="aa0eb-148">**By using the action mapping format**.</span></span> <span data-ttu-id="aa0eb-149">Utilisez ce format, si un seul port WCF-OracleDB envoie et reçoit des messages pour plusieurs opérations.</span><span class="sxs-lookup"><span data-stu-id="aa0eb-149">Use this format if a single WCF-OracleDB port sends and receives messages for more than one operation.</span></span> <span data-ttu-id="aa0eb-150">Par exemple, si un seul port WCF-OracleDB envoie et reçoit des messages pour Op1 (pour insérer des enregistrements dans la table EMP) et Op2 (pour mettre à jour des enregistrements dans la table EMP), l’action SOAP peut être spécifiée de la manière suivante :</span><span class="sxs-lookup"><span data-stu-id="aa0eb-150">For example, if a single WCF-OracleDB port sends and receives messages for Op1 (to insert records in the EMP table) and Op2 (to update records in the EMP table), the SOAP action can be specified in the following manner:</span></span>  
  
        ```  
        <BtsActionMapping>  
          <Operation Name="Op1" Action="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Insert" />  
          <Operation Name="Op2" Action="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Update " />  
        </BtsActionMapping>  
        ```  
  
         <span data-ttu-id="aa0eb-151">Cette approche offre une plus grande flexibilité en termes de spécification d’un ensemble d’actions et par conséquent, l’activation de messages appartenant à des types d’actions différentes de circuler via le même port.</span><span class="sxs-lookup"><span data-stu-id="aa0eb-151">This approach provides greater flexibility in terms of specifying a set of actions and hence enabling messages belonging to different action types to flow through the same port.</span></span>  
  
         <span data-ttu-id="aa0eb-152">Le format de l’action SOAP est différent pour chaque opération.</span><span class="sxs-lookup"><span data-stu-id="aa0eb-152">The format for the SOAP action is different for each operation.</span></span> <span data-ttu-id="aa0eb-153">Pour plus d’informations sur le format d’action pour chaque opération, consultez [Messages et des schémas de Message](messages-and-message-schemas-for-biztalk-adapter-for-oracle-database.md).</span><span class="sxs-lookup"><span data-stu-id="aa0eb-153">For more information about action format for each operation, see [Messages and Message Schemas](messages-and-message-schemas-for-biztalk-adapter-for-oracle-database.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="aa0eb-154">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aa0eb-154">See Also</span></span>  
[<span data-ttu-id="aa0eb-155">Blocs de construction pour développer des Applications BizTalk avec la base de données Oracle</span><span class="sxs-lookup"><span data-stu-id="aa0eb-155">Building Blocks to develop BizTalk Applications with Oracle Database</span></span>](../../adapters-and-accelerators/adapter-oracle-database/building-blocks-to-develop-biztalk-applications-with-oracle-database.md)