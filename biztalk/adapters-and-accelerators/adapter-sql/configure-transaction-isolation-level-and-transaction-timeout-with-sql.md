---
title: "Configurer le niveau d’Isolation de Transaction et le délai d’attente de Transaction avec SQL | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 55355272-60c0-49e4-b37e-9198458ab305
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e75d63118c24602439434c9c7ba281fa9cbc7805
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configure-transaction-isolation-level-and-transaction-timeout-with-sql"></a><span data-ttu-id="f7ab6-102">Configurer le niveau d’Isolation de Transaction et le délai d’attente de Transaction avec SQL</span><span class="sxs-lookup"><span data-stu-id="f7ab6-102">Configure Transaction Isolation Level and Transaction Timeout with SQL</span></span>
<span data-ttu-id="f7ab6-103">Lors de l’exécution d’opérations entrantes (interrogation et la Notification) à l’aide de la [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], vous devez configurer correctement le niveau d’isolation de transaction et les valeurs de délai d’attente de transaction.</span><span class="sxs-lookup"><span data-stu-id="f7ab6-103">While performing inbound operations (Polling and Notification) using the [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], you should appropriately configure the transaction isolation level and the transaction timeout values.</span></span> <span data-ttu-id="f7ab6-104">Pour effectuer cette opération :</span><span class="sxs-lookup"><span data-stu-id="f7ab6-104">To do this:</span></span>  
  
1.  <span data-ttu-id="f7ab6-105">Démarrer le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.</span><span class="sxs-lookup"><span data-stu-id="f7ab6-105">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2.  <span data-ttu-id="f7ab6-106">Dans l’arborescence de la console, développez le **groupe BizTalk**, puis développez **Applications**.</span><span class="sxs-lookup"><span data-stu-id="f7ab6-106">In the console tree, expand the **BizTalk Group**, and then expand **Applications**.</span></span>  
  
3.  <span data-ttu-id="f7ab6-107">Développez l’application sous lequel vous souhaitez déployer le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f7ab6-107">Expand the application under which you want to deploy the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span>  
  
4.  <span data-ttu-id="f7ab6-108">Avec le bouton droit **Ports de réception**, pointez sur **nouveau**, puis cliquez sur **Port de réception unidirectionnel**.</span><span class="sxs-lookup"><span data-stu-id="f7ab6-108">Right-click **Receive Ports**, point to **New**, and then click **One-way Receive Port**.</span></span>  
  
5.  <span data-ttu-id="f7ab6-109">Dans le **propriétés du Port de réception** boîte de dialogue le **général** , tapez un nom pour le port de réception.</span><span class="sxs-lookup"><span data-stu-id="f7ab6-109">In the **Receive Port Properties** dialog box, on the **General** tab, type a name for the receive port.</span></span>  
  
6.  <span data-ttu-id="f7ab6-110">Dans le volet gauche de la **propriétés du Port de réception** boîte de dialogue, cliquez sur **emplacements de réception**, puis cliquez sur **nouveau** dans le volet droit pour définir un nouvel emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="f7ab6-110">In the left pane of the **Receive Port Properties** dialog box, click **Receive Locations**, and then click **New** in the right pane to define a new receive location.</span></span>  
  
7.  <span data-ttu-id="f7ab6-111">Dans le **propriétés de l’emplacement de réception** boîte de dialogue, cliquez sur **WCF-Custom** dans les **Type** liste.</span><span class="sxs-lookup"><span data-stu-id="f7ab6-111">In the **Receive Location Properties** dialog box, click **WCF-Custom** in the **Type** list.</span></span>  
  
8.  <span data-ttu-id="f7ab6-112">Cliquez sur **configurer** adjacente à la **Type** liste.</span><span class="sxs-lookup"><span data-stu-id="f7ab6-112">Click **Configure** adjacent to the **Type** list.</span></span>  
  
9. <span data-ttu-id="f7ab6-113">Dans le **propriétés du Transport WCF-Custom** boîte de dialogue, cliquez sur le **comportement** onglet.</span><span class="sxs-lookup"><span data-stu-id="f7ab6-113">In the **WCF-Custom Transport Properties** dialog box, click the **Behavior** tab.</span></span>  
  
10. <span data-ttu-id="f7ab6-114">Dans le **comportement** liste, cliquez sur **ServiceBehavior**, puis cliquez sur **ajouter une extension**.</span><span class="sxs-lookup"><span data-stu-id="f7ab6-114">In the **Behavior** list, right-click **ServiceBehavior**, and click **Add extension**.</span></span>  
  
11. <span data-ttu-id="f7ab6-115">Dans le **sélectionner une Extension de comportement** boîte de dialogue, sélectionnez **sqlAdapterInboundTransactionBehavior**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="f7ab6-115">In the **Select Behavior Extension** dialog box, select **sqlAdapterInboundTransactionBehavior**, and click **OK**.</span></span>  
  
12. <span data-ttu-id="f7ab6-116">Dans le volet gauche de la **propriétés du Transport WCF-Custom**, sélectionnez le **sqlAdapterInboundTransactionBehavior** service sous **ServiceBehavior**.</span><span class="sxs-lookup"><span data-stu-id="f7ab6-116">In the left pane of the **WCF-Custom Transport Properties**, select the **sqlAdapterInboundTransactionBehavior** service under **ServiceBehavior**.</span></span> <span data-ttu-id="f7ab6-117">Pour la réception (message d’opération entrants), utiliser le sqlAdapterInboundTransactionBehavior pour contrôler le niveau d’isolation et la valeur par défaut est **ReadCommitted**.</span><span class="sxs-lookup"><span data-stu-id="f7ab6-117">For receive (Inbound operation message), one can use the sqlAdapterInboundTransactionBehavior to control the isolation level and the default value is **ReadCommitted**.</span></span>  
  
13. <span data-ttu-id="f7ab6-118">Dans le volet droit de la **propriétés du Transport WCF-Custom**, spécifiez les valeurs appropriées pour le **transactionIsolationLevel** et **transactionTimeout** paramètres.</span><span class="sxs-lookup"><span data-stu-id="f7ab6-118">In the right pane of the **WCF-Custom Transport Properties**, specify appropriate values for the **transactionIsolationLevel** and **transactionTimeout** parameters.</span></span> <span data-ttu-id="f7ab6-119">Vous pouvez choisir parmi les niveaux d’isolation de transaction suivantes : **Serializable**, **RepeatableRead**, **ReadCommitted**, **ReadUncommitted**, **Instantané**, **Chaos**, et **non spécifiée**.</span><span class="sxs-lookup"><span data-stu-id="f7ab6-119">You can select any of the following transaction isolation levels: **Serializable**, **RepeatableRead**, **ReadCommitted**, **ReadUncommitted**, **Snapshot**, **Chaos**, and **Unspecified**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f7ab6-120">La valeur par défaut du niveau d’Isolation de Transaction est **Serializable** pour l’adaptateur WCF-SQL pour les opérations entrantes et sortantes.</span><span class="sxs-lookup"><span data-stu-id="f7ab6-120">The default value of Transaction Isolation Level is **Serializable** for the WCF-SQL adapter for both inbound and outbound operations.</span></span> <span data-ttu-id="f7ab6-121">Pour plus d’informations sur ces niveaux d’isolation des transactions, consultez le **membres** section à [énumération du niveau d’Isolation](http://go.microsoft.com/fwlink/?LinkId=126983) (http://go.microsoft.com/fwlink/?LinkId=126983).</span><span class="sxs-lookup"><span data-stu-id="f7ab6-121">For information about these transaction isolation levels, see the **Members** section at [Isolation Level Enumeration](http://go.microsoft.com/fwlink/?LinkId=126983) (http://go.microsoft.com/fwlink/?LinkId=126983).</span></span>  
  
     <span data-ttu-id="f7ab6-122">![Définition du niveau d’Isolation des transactions](../../adapters-and-accelerators/adapter-sql/media/b39c180e-ca9f-48ca-9550-f4837826d00e.gif "b39c180e-ca9f-48ca-9550-f4837826d00e")</span><span class="sxs-lookup"><span data-stu-id="f7ab6-122">![Setting Transaction Isolation Level](../../adapters-and-accelerators/adapter-sql/media/b39c180e-ca9f-48ca-9550-f4837826d00e.gif "b39c180e-ca9f-48ca-9550-f4837826d00e")</span></span>  
  
14. <span data-ttu-id="f7ab6-123">Cliquez sur **OK** dans les **propriétés du Transport WCF-Custom** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="f7ab6-123">Click **OK** in the **WCF-Custom Transport Properties** dialog box.</span></span>  
  
15. <span data-ttu-id="f7ab6-124">Cliquez sur **OK** dans la boîte de dialogue pour enregistrer les modifications.</span><span class="sxs-lookup"><span data-stu-id="f7ab6-124">Click **OK** in the open dialog boxes to save the changes.</span></span>