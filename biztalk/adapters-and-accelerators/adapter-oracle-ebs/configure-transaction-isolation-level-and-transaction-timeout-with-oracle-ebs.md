---
title: "Configurer le niveau d’isolation de transaction et le délai d’attente de transaction avec Oracle E-Business Suite | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: db3d64ad-037d-486a-bdde-45c8199613f1
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 89e818d6ca3fdda05ee877f9e6ef4f04d7a66176
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configure-transaction-isolation-level-and-transaction-timeout-with-oracle-e-business-suite"></a><span data-ttu-id="4c48f-102">Configurer le niveau d’isolation de transaction et le délai d’attente de transaction avec Oracle E-Business Suite</span><span class="sxs-lookup"><span data-stu-id="4c48f-102">Configure transaction isolation level and transaction timeout with Oracle E-Business Suite</span></span>
<span data-ttu-id="4c48f-103">Lors de l’exécution d’opérations entrantes (interrogation et la Notification) à l’aide de la [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], vous devez configurer correctement le niveau d’isolation de transaction et les valeurs de délai d’attente de transaction.</span><span class="sxs-lookup"><span data-stu-id="4c48f-103">While performing inbound operations (Polling and Notification) using the [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], you should appropriately configure the transaction isolation level and the transaction timeout values.</span></span> <span data-ttu-id="4c48f-104">Pour effectuer cette opération :</span><span class="sxs-lookup"><span data-stu-id="4c48f-104">To do this:</span></span>  
  
1.  <span data-ttu-id="4c48f-105">Démarrer le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.</span><span class="sxs-lookup"><span data-stu-id="4c48f-105">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2.  <span data-ttu-id="4c48f-106">Dans l’arborescence de la console, développez le **groupe BizTalk**, puis développez **Applications**.</span><span class="sxs-lookup"><span data-stu-id="4c48f-106">In the console tree, expand the **BizTalk Group**, and then expand **Applications**.</span></span>  
  
3.  <span data-ttu-id="4c48f-107">Développez l’application BizTalk que vous avez déployé après la génération de métadonnées à l’aide du [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4c48f-107">Expand the BizTalk application that you have deployed after generating the metadata using the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].</span></span>  
  
4.  <span data-ttu-id="4c48f-108">Avec le bouton droit **Ports de réception**, pointez sur **nouveau**, puis cliquez sur **Port de réception unidirectionnel**.</span><span class="sxs-lookup"><span data-stu-id="4c48f-108">Right-click **Receive Ports**, point to **New**, and then click **One-way Receive Port**.</span></span>  
  
5.  <span data-ttu-id="4c48f-109">Dans le **propriétés du Port de réception** boîte de dialogue le **général** , tapez un nom pour le port de réception.</span><span class="sxs-lookup"><span data-stu-id="4c48f-109">In the **Receive Port Properties** dialog box, on the **General** tab, type a name for the receive port.</span></span>  
  
6.  <span data-ttu-id="4c48f-110">Dans le volet gauche de la **propriétés du Port de réception** boîte de dialogue, cliquez sur **emplacements de réception**, puis cliquez sur **nouveau** dans le volet droit pour définir un nouvel emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="4c48f-110">In the left pane of the **Receive Port Properties** dialog box, click **Receive Locations**, and then click **New** in the right pane to define a new receive location.</span></span>  
  
7.  <span data-ttu-id="4c48f-111">Dans le **propriétés de l’emplacement de réception** boîte de dialogue, cliquez sur **WCF-Custom** dans les **Type** liste.</span><span class="sxs-lookup"><span data-stu-id="4c48f-111">In the **Receive Location Properties** dialog box, click **WCF-Custom** in the **Type** list.</span></span>  
  
8.  <span data-ttu-id="4c48f-112">Cliquez sur **configurer** adjacente à la **Type** liste.</span><span class="sxs-lookup"><span data-stu-id="4c48f-112">Click **Configure** adjacent to the **Type** list.</span></span>  
  
9. <span data-ttu-id="4c48f-113">Dans le **propriétés du Transport WCF-Custom** boîte de dialogue, cliquez sur le **comportement** onglet.</span><span class="sxs-lookup"><span data-stu-id="4c48f-113">In the **WCF-Custom Transport Properties** dialog box, click the **Behavior** tab.</span></span>  
  
10. <span data-ttu-id="4c48f-114">Dans le **comportement** liste, cliquez sur **ServiceBehavior**, puis cliquez sur **ajouter une extension**.</span><span class="sxs-lookup"><span data-stu-id="4c48f-114">In the **Behavior** list, right-click **ServiceBehavior**, and click **Add extension**.</span></span>  
  
11. <span data-ttu-id="4c48f-115">Dans le **sélectionner une Extension de comportement** boîte de dialogue, sélectionnez **oracleEBSAdapterInboundTransactionBehavior**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="4c48f-115">In the **Select Behavior Extension** dialog box, select **oracleEBSAdapterInboundTransactionBehavior**, and click **OK**.</span></span>  
  
12. <span data-ttu-id="4c48f-116">Dans le volet gauche de la **propriétés du Transport WCF-Custom**, sélectionnez le **oracleEBSAdapterInboundTransactionBehavior** service sous **ServiceBehavior**.</span><span class="sxs-lookup"><span data-stu-id="4c48f-116">In the left pane of the **WCF-Custom Transport Properties**, select the **oracleEBSAdapterInboundTransactionBehavior** service under **ServiceBehavior**.</span></span>  
  
13. <span data-ttu-id="4c48f-117">Dans le volet droit de la **propriétés du Transport WCF-Custom**, spécifiez les valeurs appropriées pour le **transactionIsolationLevel** et **transactionTimeout** paramètres.</span><span class="sxs-lookup"><span data-stu-id="4c48f-117">In the right pane of the **WCF-Custom Transport Properties**, specify appropriate values for the **transactionIsolationLevel** and **transactionTimeout** parameters.</span></span> <span data-ttu-id="4c48f-118">Vous pouvez choisir parmi les niveaux d’isolation de transaction suivantes : **Serializable**, **RepeatableRead**, **ReadCommitted**, **ReadUncommitted**, **Instantané**, **Chaos**, et **non spécifiée**.</span><span class="sxs-lookup"><span data-stu-id="4c48f-118">You can select any of the following transaction isolation levels: **Serializable**, **RepeatableRead**, **ReadCommitted**, **ReadUncommitted**, **Snapshot**, **Chaos**, and **Unspecified**.</span></span> <span data-ttu-id="4c48f-119">Pour plus d’informations sur ces niveaux d’isolation des transactions, consultez le **membres** section à [http://go.microsoft.com/fwlink/?LinkId=126983](http://go.microsoft.com/fwlink/?LinkId=126983).</span><span class="sxs-lookup"><span data-stu-id="4c48f-119">For information about these transaction isolation levels, see the **Members** section at [http://go.microsoft.com/fwlink/?LinkId=126983](http://go.microsoft.com/fwlink/?LinkId=126983).</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="4c48f-120">Oracle E-Business Suite prend en charge uniquement les niveaux d’isolation des deux transactions suivants : ReadCommitted et Serializable.</span><span class="sxs-lookup"><span data-stu-id="4c48f-120">Oracle E-Business Suite supports only the following two transaction isolation levels: ReadCommitted and Serializable.</span></span>  
  
     <span data-ttu-id="4c48f-121">![Définition du niveau d’Isolation des transactions](../../adapters-and-accelerators/adapter-oracle-ebs/media/2bafbb9d-4daa-43c0-abcb-35220e6a3cb5.gif "2bafbb9d-4daa-43c0-abcb-35220e6a3cb5")</span><span class="sxs-lookup"><span data-stu-id="4c48f-121">![Setting Transaction Isolation Level](../../adapters-and-accelerators/adapter-oracle-ebs/media/2bafbb9d-4daa-43c0-abcb-35220e6a3cb5.gif "2bafbb9d-4daa-43c0-abcb-35220e6a3cb5")</span></span>  
  
14. <span data-ttu-id="4c48f-122">Cliquez sur **OK** dans les **propriétés du Transport WCF-Custom** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="4c48f-122">Click **OK** in the **WCF-Custom Transport Properties** dialog box.</span></span>  
  
15. <span data-ttu-id="4c48f-123">Cliquez sur **OK** dans la boîte de dialogue pour enregistrer les modifications.</span><span class="sxs-lookup"><span data-stu-id="4c48f-123">Click **OK** in the open dialog boxes to save the changes.</span></span>