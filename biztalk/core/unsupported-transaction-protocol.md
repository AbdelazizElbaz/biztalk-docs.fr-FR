---
title: Non pris en charge de protocole de transaction | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 11fb2497-9971-4e85-b21a-161734f071e0
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3e000c706ca438494f8b07e8ce5dba24cb4f46bd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="unsupported-transaction-protocol"></a><span data-ttu-id="e8dc5-102">Protocole de transaction non pris en charge</span><span class="sxs-lookup"><span data-stu-id="e8dc5-102">Unsupported transaction protocol</span></span>
## <a name="details"></a><span data-ttu-id="e8dc5-103">Détails</span><span class="sxs-lookup"><span data-stu-id="e8dc5-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e8dc5-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="e8dc5-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="e8dc5-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="e8dc5-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="e8dc5-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="e8dc5-106">Event ID</span></span>|<span data-ttu-id="e8dc5-107">0</span><span class="sxs-lookup"><span data-stu-id="e8dc5-107">0</span></span>|  
|<span data-ttu-id="e8dc5-108">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="e8dc5-108">Event Source</span></span>|<span data-ttu-id="e8dc5-109">0</span><span class="sxs-lookup"><span data-stu-id="e8dc5-109">0</span></span>|  
|<span data-ttu-id="e8dc5-110">Composant</span><span class="sxs-lookup"><span data-stu-id="e8dc5-110">Component</span></span>|<span data-ttu-id="e8dc5-111">0</span><span class="sxs-lookup"><span data-stu-id="e8dc5-111">0</span></span>|  
|<span data-ttu-id="e8dc5-112">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="e8dc5-112">Symbolic Name</span></span>|<span data-ttu-id="e8dc5-113">0</span><span class="sxs-lookup"><span data-stu-id="e8dc5-113">0</span></span>|  
|<span data-ttu-id="e8dc5-114">Texte du message</span><span class="sxs-lookup"><span data-stu-id="e8dc5-114">Message Text</span></span>|<span data-ttu-id="e8dc5-115">Non pris en charge de protocole de transaction : {0}</span><span class="sxs-lookup"><span data-stu-id="e8dc5-115">Unsupported transaction protocol: {0}</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="e8dc5-116">Explication</span><span class="sxs-lookup"><span data-stu-id="e8dc5-116">Explanation</span></span>  
 <span data-ttu-id="e8dc5-117">Cette erreur se produit lorsque la propriété de protocole de transaction d'un emplacement de réception ou d'un port d'envoi est définie sur une valeur erronée.</span><span class="sxs-lookup"><span data-stu-id="e8dc5-117">This error occurs when the transaction protocol property of a receive location or send port is set to an invalid value.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="e8dc5-118">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="e8dc5-118">User Action</span></span>  
 <span data-ttu-id="e8dc5-119">Pour résoudre cette erreur, procédez de l'une des manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="e8dc5-119">To resolve this error, do one or more of the following:</span></span>  
  
1.  <span data-ttu-id="e8dc5-120">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="e8dc5-120">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="e8dc5-121">Dans la racine de la Console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez **groupe BizTalk**, développez **Applications**.</span><span class="sxs-lookup"><span data-stu-id="e8dc5-121">In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand  **Applications**.</span></span>  
  
3.  <span data-ttu-id="e8dc5-122">Recherchez votre application, puis recherchez votre transport.</span><span class="sxs-lookup"><span data-stu-id="e8dc5-122">Locate your application and then locate your transport.</span></span>  
  
4.  <span data-ttu-id="e8dc5-123">Cliquez avec le bouton droit sur le nom du transport.</span><span class="sxs-lookup"><span data-stu-id="e8dc5-123">Right-click the transport name.</span></span>  
  
5.  <span data-ttu-id="e8dc5-124">Cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="e8dc5-124">Click **Properties**.</span></span>  
  
6.  <span data-ttu-id="e8dc5-125">Dans le port **Type** , sélectionnez le port approprié.</span><span class="sxs-lookup"><span data-stu-id="e8dc5-125">In the port **Type** list, select the correct port.</span></span>  
  
7.  <span data-ttu-id="e8dc5-126">Cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="e8dc5-126">Click **Configure**.</span></span>  
  
8.  <span data-ttu-id="e8dc5-127">Dans le **WCF [***type de transport***] propriétés du Transport** boîte de dialogue, cliquez sur le **liaison** onglet.</span><span class="sxs-lookup"><span data-stu-id="e8dc5-127">In the **WCF [***transport type***] Transport Properties** dialog box, click the **Binding** tab.</span></span>  
  
9. <span data-ttu-id="e8dc5-128">Dans le **Transactions** , choisissez le **activer les transactions** option.</span><span class="sxs-lookup"><span data-stu-id="e8dc5-128">In the **Transactions** section, choose the **Enable transactions** option.</span></span>  
  
10. <span data-ttu-id="e8dc5-129">Dans le **protocole de Transactions** liste déroulante, sélectionnez soit **OleTransactions** ou **WSAtomicTransactions**.</span><span class="sxs-lookup"><span data-stu-id="e8dc5-129">In the **Transactions protocol** drop-down list, choose either **OleTransactions** or **WSAtomicTransactions**.</span></span>  
  
 <span data-ttu-id="e8dc5-130">Cette procédure s'applique uniquement aux types de transports suivants :</span><span class="sxs-lookup"><span data-stu-id="e8dc5-130">These steps only apply to the following transport types:</span></span>  
  
-   <span data-ttu-id="e8dc5-131">Custom</span><span class="sxs-lookup"><span data-stu-id="e8dc5-131">Custom</span></span>  
  
-   <span data-ttu-id="e8dc5-132">CustomIsolated</span><span class="sxs-lookup"><span data-stu-id="e8dc5-132">CustomIsolated</span></span>  
  
-   <span data-ttu-id="e8dc5-133">NetNamedPipe</span><span class="sxs-lookup"><span data-stu-id="e8dc5-133">NetNamedPipe</span></span>  
  
-   <span data-ttu-id="e8dc5-134">NetTcp</span><span class="sxs-lookup"><span data-stu-id="e8dc5-134">NetTcp</span></span>  
  
-   <span data-ttu-id="e8dc5-135">WShttp</span><span class="sxs-lookup"><span data-stu-id="e8dc5-135">WShttp</span></span>