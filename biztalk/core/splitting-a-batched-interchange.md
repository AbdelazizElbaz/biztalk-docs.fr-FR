---
title: "Fractionnement d’un échange par lot | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e67bef19-77fb-47a9-88f3-ee20043b3691
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 745f94d4ec56222d3c1d3e03c0817933248f4b8f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="splitting-a-batched-interchange"></a><span data-ttu-id="7c04d-102">Fractionnement d'un échange traité par lot</span><span class="sxs-lookup"><span data-stu-id="7c04d-102">Splitting a Batched Interchange</span></span>
<span data-ttu-id="7c04d-103">Cette rubrique présente la configuration d'un accord pour le traitement d'un échange EDI traité par lot en fractionnant les documents informatisés qu'il contient.</span><span class="sxs-lookup"><span data-stu-id="7c04d-103">This topic describes how to configure an agreement for processing a batched EDI interchange by splitting the transaction sets from the interchange.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="7c04d-104">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="7c04d-104">Prerequisites</span></span>  
 <span data-ttu-id="7c04d-105">Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7c04d-105">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  
  
### <a name="to-receive-a-split-edi-interchange"></a><span data-ttu-id="7c04d-106">Réception d'un échange EDI fractionné</span><span class="sxs-lookup"><span data-stu-id="7c04d-106">To receive a split EDI interchange</span></span>  
  
1.  <span data-ttu-id="7c04d-107">Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, cliquez sur le **Parties** nœud.</span><span class="sxs-lookup"><span data-stu-id="7c04d-107">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, click the **Parties** node.</span></span> <span data-ttu-id="7c04d-108">Dans le **tiers et profils d’entreprise** , cliquez sur le tiers qui a l’accord correspondant à l’échange par lot entrant.</span><span class="sxs-lookup"><span data-stu-id="7c04d-108">In the **Parties and Business Profiles** page, click the party that has the agreement that will resolve to the incoming batched interchange.</span></span> <span data-ttu-id="7c04d-109">Dans le **accord** section de la page, cliquez sur l’accord, sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="7c04d-109">In the **Agreement** section of the page, right-click the agreement and click **Properties**.</span></span> <span data-ttu-id="7c04d-110">Dans le **propriétés de l’accord** boîte de dialogue, sous l’onglet d’accord unidirectionnel (auquel l’échange par lot entrant résoudra), procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="7c04d-110">In the **Agreement Properties** dialog box, in the one-way agreement tab (to which the inbound batched interchange will resolve), do the following:</span></span>  
  
    1.  <span data-ttu-id="7c04d-111">Dans le **identificateurs** , vérifiez que vous entrez les valeurs correctes afin que l’échange par lot entrant corresponde à ce contrat.</span><span class="sxs-lookup"><span data-stu-id="7c04d-111">In the **Identifiers** page, make sure you enter the correct values so that the incoming batched interchange resolves to this agreement.</span></span>  
  
        -   <span data-ttu-id="7c04d-112">Dans le cas de **X12**: définir les ISA5, ISA6, ISA7 et ISA8.</span><span class="sxs-lookup"><span data-stu-id="7c04d-112">In case of **X12**: Set ISA5, ISA6, ISA7, and ISA8.</span></span>  
  
        -   <span data-ttu-id="7c04d-113">Dans le cas de **Edifact**: définir les UNB2.1, UNB2.2, UNB3.1 et UNB3.2.</span><span class="sxs-lookup"><span data-stu-id="7c04d-113">In case of **Edifact**: Set UNB2.1, UNB2.2, UNB3.1, and UNB3.2.</span></span>  
  
    2.  <span data-ttu-id="7c04d-114">Dans le **paramètres d’hôte Local** page (sous **paramètres de l’échange**), sous **paramètres du récepteur** section, pour le **entrants option de traitement par lots** , sélectionnez une les options suivantes :</span><span class="sxs-lookup"><span data-stu-id="7c04d-114">In the **Local Host Settings** page (under **Interchange Settings**), under **Receiver’s Settings** section, for the **Inbound batch processing option**, select one the following options:</span></span>  
  
        -   <span data-ttu-id="7c04d-115">**Fractionner l’échange en documents informatisés - suspendre les documents informatisés en cas d’erreur** – Sélectionnez cette option pour indiquer que BizTalk Server doit analyser chaque document informatisé d’un échange en un document XML distinct.</span><span class="sxs-lookup"><span data-stu-id="7c04d-115">**Split Interchange as Transaction Sets - suspend Transaction Sets on Error** – Select this option to specify that BizTalk Server should parse each transaction set in an interchange into a separate XML document.</span></span> <span data-ttu-id="7c04d-116">BizTalk Server applique alors l'enveloppe appropriée au document informatisé et l'achemine vers la base de données MessageBox.</span><span class="sxs-lookup"><span data-stu-id="7c04d-116">BizTalk Server will then apply the appropriate envelope to the transaction set and route the transaction set document to the MessageBox.</span></span> <span data-ttu-id="7c04d-117">Lorsque cette option est sélectionnée et si la validation d'un ou plusieurs documents informatisés de l'échange échoue, BizTalk Server interrompt uniquement ces documents informatisés.</span><span class="sxs-lookup"><span data-stu-id="7c04d-117">With this option, if one or more transaction sets in the interchange fail validation, BizTalk Server will suspend only those transaction sets.</span></span>  
  
        -   <span data-ttu-id="7c04d-118">**Fractionner l’échange en documents informatisés - suspendre l’échange en cas d’erreur** – Sélectionnez cette option pour indiquer que BizTalk Server doit analyser chaque document informatisé d’un échange en un document XML distinct.</span><span class="sxs-lookup"><span data-stu-id="7c04d-118">**Split Interchange as Transaction Sets - suspend Interchange on Error** – Select this option to specify that BizTalk Server should parse each transaction set in an interchange into a separate XML document.</span></span> <span data-ttu-id="7c04d-119">BizTalk Server applique alors l'enveloppe appropriée au document informatisé et l'achemine vers la base de données MessageBox.</span><span class="sxs-lookup"><span data-stu-id="7c04d-119">BizTalk Server will then apply the appropriate envelope to the transaction set and route the transaction set document to the MessageBox.</span></span> <span data-ttu-id="7c04d-120">Lorsque cette option est sélectionnée et si la validation d'un ou plusieurs documents informatisés de l'échange échoue, BizTalk Server interrompt l'ensemble de l'échange.</span><span class="sxs-lookup"><span data-stu-id="7c04d-120">With this option, if one or more transaction sets in the interchange fail validation, BizTalk Server will suspend the entire interchange.</span></span>  
  
2.  <span data-ttu-id="7c04d-121">Créez un projet Visual Studio pour le lot conservé en procédant comme suit :</span><span class="sxs-lookup"><span data-stu-id="7c04d-121">Create a Visual Studio project for the preserved batch as follows:</span></span>  
  
    1.  <span data-ttu-id="7c04d-122">Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], créez un projet BizTalk et ajoutez-lui les schémas pour tous les messages du lot.</span><span class="sxs-lookup"><span data-stu-id="7c04d-122">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], create a BizTalk project and add the schemas for all the messages within the batch.</span></span>  
  
    2.  <span data-ttu-id="7c04d-123">Générez et déployez le projet.</span><span class="sxs-lookup"><span data-stu-id="7c04d-123">Build and deploy the project.</span></span>  
  
3.  <span data-ttu-id="7c04d-124">Dans la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], créez un port d'envoi pour envoyer les lots fractionnés en procédant comme suit :</span><span class="sxs-lookup"><span data-stu-id="7c04d-124">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, create a send port to send split batches as follows:</span></span>  
  
    1.  <span data-ttu-id="7c04d-125">Le pipeline d’envoi la valeur **EdiSend** ou **AS2EdiSend**.</span><span class="sxs-lookup"><span data-stu-id="7c04d-125">Set the send pipeline to **EdiSend** or **AS2EdiSend**.</span></span>  
  
    2.  <span data-ttu-id="7c04d-126">Donnez au filtre du port d'envoi la valeur requise pour sélectionner chaque document informatisé, par exemple, BTS.MessageType.</span><span class="sxs-lookup"><span data-stu-id="7c04d-126">Set the filter of the send port to the value required to pick up each transaction set, for example, to BTS.MessageType.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c04d-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7c04d-127">See Also</span></span>  
 <span data-ttu-id="7c04d-128">[Configuration des lots EDI](../core/configuring-edi-batches.md) </span><span class="sxs-lookup"><span data-stu-id="7c04d-128">[Configuring EDI Batches](../core/configuring-edi-batches.md) </span></span>  
 [<span data-ttu-id="7c04d-129">Comment créer un Port d’envoi</span><span class="sxs-lookup"><span data-stu-id="7c04d-129">How to Create a Send Port</span></span>](../core/how-to-create-a-send-port2.md)