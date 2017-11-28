---
title: "Afficher un EDI ou le rapport d’état AS2 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 60968c3d-6329-411f-9f10-1dd4a6cc9d79
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0564a5c5d904a217ac406befebd3d7c742dc00c1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="displaying-an-edi-or-as2-status-report"></a><span data-ttu-id="9e58d-102">Affichage des rapports d'état EDI ou AS2</span><span class="sxs-lookup"><span data-stu-id="9e58d-102">Displaying an EDI or AS2 Status Report</span></span>
<span data-ttu-id="9e58d-103">Si les rapports d'état EDI et AS2 sont désactivés, vous avez accès aux rapports d'état suivants :</span><span class="sxs-lookup"><span data-stu-id="9e58d-103">When EDI and AS2 status reports are enabled, you will have access to the following status reports:</span></span>  
  
|<span data-ttu-id="9e58d-104">Type de rapport</span><span class="sxs-lookup"><span data-stu-id="9e58d-104">Type of Report</span></span>|<span data-ttu-id="9e58d-105">Rapport d'état de niveau supérieur</span><span class="sxs-lookup"><span data-stu-id="9e58d-105">Higher-level status report</span></span>|<span data-ttu-id="9e58d-106">Rapport d'état de niveau inférieur</span><span class="sxs-lookup"><span data-stu-id="9e58d-106">Lower-level status report</span></span>|  
|--------------------|---------------------------------|--------------------------------|  
|<span data-ttu-id="9e58d-107">Routage</span><span class="sxs-lookup"><span data-stu-id="9e58d-107">EDI</span></span>|<span data-ttu-id="9e58d-108">Échange EDI et état ACK corrélé</span><span class="sxs-lookup"><span data-stu-id="9e58d-108">EDI Interchange and Correlated ACK Status</span></span>|<span data-ttu-id="9e58d-109">-Échange d’état et les détails de l’accusé de réception</span><span class="sxs-lookup"><span data-stu-id="9e58d-109">- Interchange Status and ACK Details</span></span><br /><br /> <span data-ttu-id="9e58d-110">-Détails du document informatisé</span><span class="sxs-lookup"><span data-stu-id="9e58d-110">- Transaction Set Details</span></span><br /><br /> <span data-ttu-id="9e58d-111">-Contenu du Message EDI</span><span class="sxs-lookup"><span data-stu-id="9e58d-111">- EDI Message Content</span></span>|  
|<span data-ttu-id="9e58d-112">Routage</span><span class="sxs-lookup"><span data-stu-id="9e58d-112">EDI</span></span>|<span data-ttu-id="9e58d-113">état du lot ;</span><span class="sxs-lookup"><span data-stu-id="9e58d-113">Batch Status</span></span>|-|  
|<span data-ttu-id="9e58d-114">Routage</span><span class="sxs-lookup"><span data-stu-id="9e58d-114">EDI</span></span>|<span data-ttu-id="9e58d-115">Rapport d'agrégation de l'échange</span><span class="sxs-lookup"><span data-stu-id="9e58d-115">Interchange Aggregation Report</span></span>|-|  
|<span data-ttu-id="9e58d-116">Routage</span><span class="sxs-lookup"><span data-stu-id="9e58d-116">EDI</span></span>|<span data-ttu-id="9e58d-117">Rapport d'agrégation du document informatisé</span><span class="sxs-lookup"><span data-stu-id="9e58d-117">Transaction Set Aggregation Report</span></span>|-|  
|<span data-ttu-id="9e58d-118">AS2</span><span class="sxs-lookup"><span data-stu-id="9e58d-118">AS2</span></span>|<span data-ttu-id="9e58d-119">Message AS2 et état MDN corrélé</span><span class="sxs-lookup"><span data-stu-id="9e58d-119">AS2 Message and Correlated MDN Status</span></span>|<span data-ttu-id="9e58d-120">Contenu du message AS2</span><span class="sxs-lookup"><span data-stu-id="9e58d-120">AS2 Message Content</span></span>|  
  
## <a name="prerequisites"></a><span data-ttu-id="9e58d-121">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="9e58d-121">Prerequisites</span></span>  
 <span data-ttu-id="9e58d-122">La configuration requise pour exécuter la procédure décrite dans cette rubrique est la suivante :</span><span class="sxs-lookup"><span data-stu-id="9e58d-122">The following are prerequisites for performing the procedure in this topic:</span></span>  
  
-   <span data-ttu-id="9e58d-123">Pour personnaliser les rapports d'état, vous devez ouvrir une session en tant que membre du groupe Administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9e58d-123">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group to customize any of the status reports.</span></span>  
  
-   <span data-ttu-id="9e58d-124">Si vous ouvrez une session en tant que membre du groupe Opérateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], vous pouvez afficher les rapports d'état en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="9e58d-124">If you are logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Operators group, you can display read-only status reports.</span></span>  
  
## <a name="display-an-edi-or-as2-status-report"></a><span data-ttu-id="9e58d-125">Afficher un rapport d’état EDI ou AS2</span><span class="sxs-lookup"><span data-stu-id="9e58d-125">Display an EDI or AS2 status report</span></span>  
  
1.  <span data-ttu-id="9e58d-126">Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, cliquez sur le **groupe BizTalk** nœud.</span><span class="sxs-lookup"><span data-stu-id="9e58d-126">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, click the **BizTalk Group** node.</span></span>  
  
2.  <span data-ttu-id="9e58d-127">Dans le **Hub du groupe** onglet de la **vue d’ensemble du groupe** page de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, accédez au bas de la page.</span><span class="sxs-lookup"><span data-stu-id="9e58d-127">In the **Group Hub** tab of the **Group Overview** page of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, move to the bottom of the page.</span></span>  
  
3.  <span data-ttu-id="9e58d-128">Pour afficher le **échange EDI et état ACK corrélé** de rapports, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="9e58d-128">To display the **EDI Interchange and Correlated ACK Status** report, proceed as follows:</span></span>  
  
    1.  <span data-ttu-id="9e58d-129">Cliquez sur **échange EDI et état ACK corrélé** dans les **rapports d’état EDI** zone de la **Hub du groupe** onglet.</span><span class="sxs-lookup"><span data-stu-id="9e58d-129">Click **EDI Interchange and Correlated ACK Status** in the **EDI Status Reports** area of the **Group Hub** tab.</span></span>  
  
    2.  <span data-ttu-id="9e58d-130">Pour afficher les détails d’un échange et ses accusés de réception corrélés, cliquez sur une entrée dans les résultats de la **échange EDI et état ACK corrélé** de rapports, puis cliquez sur **état et l’accusé de réception de l’échange détails**.</span><span class="sxs-lookup"><span data-stu-id="9e58d-130">To display details of an interchange and its correlated acknowledgments, right-click an entry in the query results of the **EDI Interchange and Correlated ACK Status** report, and then click **Interchange status and ack details**.</span></span>  
  
    3.  <span data-ttu-id="9e58d-131">Pour afficher les détails d’un document informatisé, fermez l’échange état et l’accusé de réception détails de l’état, retour à la **échange EDI et état ACK corrélé** de rapport détaillé.</span><span class="sxs-lookup"><span data-stu-id="9e58d-131">To display details of a transaction set, close the Interchange status and ack details report, returning to the **EDI Interchange and Correlated ACK Status** details report.</span></span> <span data-ttu-id="9e58d-132">Cliquez sur une entrée dans les résultats de requête, puis cliquez sur **détails du document informatisé**.</span><span class="sxs-lookup"><span data-stu-id="9e58d-132">Right-click an entry in the query results, and then click **Transaction Set Details**.</span></span>  
  
    4.  <span data-ttu-id="9e58d-133">Pour afficher plus d’informations sur les en-têtes et la charge utile d’un document informatisé, cliquez sur une entrée dans le **détails du document informatisé** de rapports, puis cliquez sur **vue de contenu du document informatisé**.</span><span class="sxs-lookup"><span data-stu-id="9e58d-133">To display details about the headers and payload of a transaction set, right-click an entry in the **Transaction Set Details** report, and then click **View Transaction Set Content**.</span></span>  
  
    5.  <span data-ttu-id="9e58d-134">Pour afficher les données relatives à l’échange contenant le document informatisé, cliquez sur une entrée dans le **détails du document informatisé** de rapports, puis cliquez sur **état échange/ACK**.</span><span class="sxs-lookup"><span data-stu-id="9e58d-134">To display data about the interchange containing the transaction set, right-click an entry in the **Transaction Set Details** report, and then click **Interchange/ACK Status**.</span></span> <span data-ttu-id="9e58d-135">L'échange contenant le document informatisé est mis en surbrillance dans le rapport État de l'échange/de l'accusé de réception.</span><span class="sxs-lookup"><span data-stu-id="9e58d-135">The interchange containing the transaction set will be highlighted in the Interchange/ACK Status report.</span></span>  
  
4.  <span data-ttu-id="9e58d-136">Pour afficher le **état du lot** de rapports, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="9e58d-136">To display the **Batch Status** report, proceed as follows:</span></span>  
  
    1.  <span data-ttu-id="9e58d-137">Cliquez sur **état du lot** dans les **rapports d’état EDI** zone de la **Hub du groupe** onglet.</span><span class="sxs-lookup"><span data-stu-id="9e58d-137">Click **Batch Status** in the **EDI Status Reports** area of the **Group Hub** tab.</span></span>  
  
    2.  <span data-ttu-id="9e58d-138">Pour afficher les lots terminés associés à une entrée de lot dans le **état du lot** de rapports, cliquez sur l’entrée, puis sur **lots terminés**.</span><span class="sxs-lookup"><span data-stu-id="9e58d-138">To display the completed batches associated with a batch entry in the **Batch Status** report, right-click the entry and then click **Completed Batches**.</span></span>  
  
    3.  <span data-ttu-id="9e58d-139">Pour afficher les données relatives à un échange par lot terminé, cliquez sur l’échange dans le **lot terminé** de rapports, puis cliquez sur **état échange/ACK**.</span><span class="sxs-lookup"><span data-stu-id="9e58d-139">To display data about a completed batched interchange, right-click the interchange in the **Completed Batch** report, and then click **Interchange/ACK Status**.</span></span> <span data-ttu-id="9e58d-140">L'entrée associée à l'échange par lot est mis en surbrillance dans le rapport État de l'échange/de l'accusé de réception.</span><span class="sxs-lookup"><span data-stu-id="9e58d-140">The entry for the batched interchange will be highlighted in the Interchange/ACK Status report.</span></span>  
  
5.  <span data-ttu-id="9e58d-141">Pour afficher le **rapport d’agrégation d’échange**, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="9e58d-141">To display the **Interchange Aggregation Report**, proceed as follows:</span></span>  
  
    -   <span data-ttu-id="9e58d-142">Cliquez sur **rapport d’agrégation d’échange** dans les **rapports d’état EDI** zone de la **Hub du groupe** onglet.</span><span class="sxs-lookup"><span data-stu-id="9e58d-142">Click **Interchange Aggregation Report** in the **EDI Status Reports** area of the **Group Hub** tab.</span></span>  
  
6.  <span data-ttu-id="9e58d-143">Pour afficher le **rapport d’agrégation du document informatisé**, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="9e58d-143">To display the **Transaction Set Aggregation Report**, proceed as follows:</span></span>  
  
    -   <span data-ttu-id="9e58d-144">Cliquez sur **rapport d’agrégation du document informatisé** dans les **rapports d’état EDI** zone de la **Hub du groupe** onglet.</span><span class="sxs-lookup"><span data-stu-id="9e58d-144">Click **Transaction Set Aggregation Report** in the **EDI Status Reports** area of the **Group Hub** tab.</span></span>  
  
7.  <span data-ttu-id="9e58d-145">Pour afficher le **Message AS2 et état MDN corrélé** de rapports, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="9e58d-145">To display the **AS2 Message and Correlated MDN Status** report, proceed as follows:</span></span>  
  
    1.  <span data-ttu-id="9e58d-146">Cliquez sur **Message AS2 et état MDN corrélé** dans les **rapports d’état EDIINT** zone de la **Hub du groupe** onglet.</span><span class="sxs-lookup"><span data-stu-id="9e58d-146">Click **AS2 Message and Correlated MDN Status** in the **EDIINT Status Reports** area of the **Group Hub** tab.</span></span>  
  
    2.  <span data-ttu-id="9e58d-147">Pour afficher l’état de l’échange EDI dans un message AS2, cliquez sur une entrée dans le **Message AS2 et état MDN corrélé** de rapports, puis cliquez sur **état échange/ACK**.</span><span class="sxs-lookup"><span data-stu-id="9e58d-147">To display the status of the EDI interchange in an AS2 message, right-click an entry in the **AS2 Message and Correlated MDN Status** report, and then click **Interchange/ACK Status**.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="9e58d-148">Pour plus d’informations sur la corrélation entre les États EDI et état AS2, consultez la section « Mise en corrélation un AS2 Message avec une charge EDI » de [Message AS2 et rapport d’état MDN corrélé](../core/as2-message-and-correlated-mdn-status-report.md).</span><span class="sxs-lookup"><span data-stu-id="9e58d-148">For more information on how EDI status and AS2 status are correlated, see the "Correlating an AS2 Message with its EDI Payload" section of [AS2 Message and Correlated MDN Status Report](../core/as2-message-and-correlated-mdn-status-report.md).</span></span>  
  
    3.  <span data-ttu-id="9e58d-149">Pour afficher un message AS2 au format câble, cliquez sur une entrée dans le rapport d’état AS2/MDN, puis cliquez sur **Message au Format câble**.</span><span class="sxs-lookup"><span data-stu-id="9e58d-149">To display an AS2 message in wire format, right-click an entry in the AS2/MDN Status report, and then click **Message Wire Format**.</span></span>  
  
    4.  <span data-ttu-id="9e58d-150">Pour afficher un message AS2 au format décodé, cliquez sur une entrée dans le rapport d’état AS2/MDN, puis cliquez sur **Message au Format décodé**.</span><span class="sxs-lookup"><span data-stu-id="9e58d-150">To display an AS2 message in decoded format, right-click an entry in the AS2/MDN Status report, and then click **Message Decoded Format**.</span></span>  
  
    5.  <span data-ttu-id="9e58d-151">Pour afficher un message MDN, cliquez sur une entrée dans le rapport d’état AS2/MDN, puis cliquez sur **Mdn Message**.</span><span class="sxs-lookup"><span data-stu-id="9e58d-151">To display an MDN message, right-click an entry in the AS2/MDN Status report, and then click **Mdn Message**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e58d-152">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9e58d-152">See Also</span></span>  
 <span data-ttu-id="9e58d-153">[Surveillance des Solutions EDI et AS2](../core/monitoring-edi-and-as2-solutions.md) </span><span class="sxs-lookup"><span data-stu-id="9e58d-153">[Monitoring EDI and AS2 Solutions](../core/monitoring-edi-and-as2-solutions.md) </span></span>  
 <span data-ttu-id="9e58d-154">[EDI et AS2 le rapport d’état](../core/edi-and-as2-status-reporting.md) </span><span class="sxs-lookup"><span data-stu-id="9e58d-154">[EDI and AS2 Status Reporting](../core/edi-and-as2-status-reporting.md) </span></span>  
 <span data-ttu-id="9e58d-155">[L’activation des rapports d’état AS2 et EDI](../core/enabling-edi-and-as2-status-reports.md) </span><span class="sxs-lookup"><span data-stu-id="9e58d-155">[Enabling EDI and AS2 Status Reports](../core/enabling-edi-and-as2-status-reports.md) </span></span>  
 [<span data-ttu-id="9e58d-156">Configuration d’un EDI et le rapport d’état AS2</span><span class="sxs-lookup"><span data-stu-id="9e58d-156">Configuring an EDI and AS2 Status Report</span></span>](../core/configuring-an-edi-and-as2-status-report.md)