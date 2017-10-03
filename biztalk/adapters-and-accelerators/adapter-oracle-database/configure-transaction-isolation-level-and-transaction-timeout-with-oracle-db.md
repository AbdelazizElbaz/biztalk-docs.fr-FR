---
title: "Configurer le niveau d’isolation de transaction et le délai d’attente de transaction avec la base de données Oracle | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4b66e764-2330-441b-89ef-29118f27b366
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 13d1beea3be34dbd818a94986fb8cae876bcdd81
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configure-transaction-isolation-level-and-transaction-timeout-with-oracle-database"></a><span data-ttu-id="f141b-102">Configurer le niveau d’isolation de transaction et le délai d’attente de transaction avec la base de données Oracle</span><span class="sxs-lookup"><span data-stu-id="f141b-102">Configure transaction isolation level and transaction timeout with Oracle Database</span></span>
<span data-ttu-id="f141b-103">Lors de l’exécution à l’aide de l’opération entrante (interrogation) le [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], vous devez configurer correctement le niveau d’isolation de transaction et les valeurs de délai d’attente de transaction.</span><span class="sxs-lookup"><span data-stu-id="f141b-103">While performing inbound operation (Polling) using the [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], you should appropriately configure the transaction isolation level and the transaction timeout values.</span></span> <span data-ttu-id="f141b-104">Pour effectuer cette opération :</span><span class="sxs-lookup"><span data-stu-id="f141b-104">To do this:</span></span>  
  
1.  <span data-ttu-id="f141b-105">Démarrer le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.</span><span class="sxs-lookup"><span data-stu-id="f141b-105">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2.  <span data-ttu-id="f141b-106">Dans l’arborescence de la console, développez le **groupe BizTalk**, puis développez **Applications**.</span><span class="sxs-lookup"><span data-stu-id="f141b-106">In the console tree, expand the **BizTalk Group**, and then expand **Applications**.</span></span>  
  
3.  <span data-ttu-id="f141b-107">Développez l’application BizTalk que vous avez déployé après la génération de métadonnées à l’aide du [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f141b-107">Expand the BizTalk application that you have deployed after generating the metadata using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span>  
  
4.  <span data-ttu-id="f141b-108">Avec le bouton droit **Ports de réception**, pointez sur **nouveau**, puis cliquez sur **Port de réception unidirectionnel**.</span><span class="sxs-lookup"><span data-stu-id="f141b-108">Right-click **Receive Ports**, point to **New**, and then click **One-way Receive Port**.</span></span>  
  
5.  <span data-ttu-id="f141b-109">Dans le **propriétés du Port de réception** boîte de dialogue le **général** , tapez un nom pour le port de réception.</span><span class="sxs-lookup"><span data-stu-id="f141b-109">In the **Receive Port Properties** dialog box, on the **General** tab, type a name for the receive port.</span></span>  
  
6.  <span data-ttu-id="f141b-110">Dans le volet gauche de la **propriétés du Port de réception** boîte de dialogue, cliquez sur **emplacements de réception**, puis cliquez sur **nouveau** dans le volet droit pour définir un nouvel emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="f141b-110">In the left pane of the **Receive Port Properties** dialog box, click **Receive Locations**, and then click **New** in the right pane to define a new receive location.</span></span>  
  
7.  <span data-ttu-id="f141b-111">Dans le **propriétés de l’emplacement de réception** boîte de dialogue, cliquez sur **WCF-Custom** dans les **Type** liste.</span><span class="sxs-lookup"><span data-stu-id="f141b-111">In the **Receive Location Properties** dialog box, click **WCF-Custom** in the **Type** list.</span></span>  
  
8.  <span data-ttu-id="f141b-112">Cliquez sur **configurer** adjacente à la **Type** liste.</span><span class="sxs-lookup"><span data-stu-id="f141b-112">Click **Configure** adjacent to the **Type** list.</span></span>  
  
9. <span data-ttu-id="f141b-113">Dans le **propriétés du Transport WCF-Custom** boîte de dialogue, cliquez sur le **comportement** onglet.</span><span class="sxs-lookup"><span data-stu-id="f141b-113">In the **WCF-Custom Transport Properties** dialog box, click the **Behavior** tab.</span></span>  
  
10. <span data-ttu-id="f141b-114">Dans le **comportement** liste, cliquez sur **ServiceBehavior**, puis cliquez sur **ajouter une extension**.</span><span class="sxs-lookup"><span data-stu-id="f141b-114">In the **Behavior** list, right-click **ServiceBehavior**, and click **Add extension**.</span></span>  
  
11. <span data-ttu-id="f141b-115">Dans le **sélectionner une Extension de comportement** boîte de dialogue, sélectionnez **oracleDBAdapterInboundTransactionBehavior**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="f141b-115">In the **Select Behavior Extension** dialog box, select **oracleDBAdapterInboundTransactionBehavior**, and click **OK**.</span></span>  
  
12. <span data-ttu-id="f141b-116">Dans le volet gauche de la **propriétés du Transport WCF-Custom**, sélectionnez le **oracleDBAdapterInboundTransactionBehavior** service sous **ServiceBehavior**.</span><span class="sxs-lookup"><span data-stu-id="f141b-116">In the left pane of the **WCF-Custom Transport Properties**, select the **oracleDBAdapterInboundTransactionBehavior** service under **ServiceBehavior**.</span></span>  
  
13. <span data-ttu-id="f141b-117">Dans le volet droit de la **propriétés du Transport WCF-Custom**, spécifiez les valeurs appropriées pour le **transactionIsolationLevel** et **transactionTimeout** paramètres.</span><span class="sxs-lookup"><span data-stu-id="f141b-117">In the right pane of the **WCF-Custom Transport Properties**, specify appropriate values for the **transactionIsolationLevel** and **transactionTimeout** parameters.</span></span> <span data-ttu-id="f141b-118">Vous pouvez choisir parmi les niveaux d’isolation de transaction suivantes : **Serializable**, **RepeatableRead**, **ReadCommitted**, **ReadUncommitted**, **Instantané**, **Chaos**, et **non spécifiée**.</span><span class="sxs-lookup"><span data-stu-id="f141b-118">You can select any of the following transaction isolation levels: **Serializable**, **RepeatableRead**, **ReadCommitted**, **ReadUncommitted**, **Snapshot**, **Chaos**, and **Unspecified**.</span></span> <span data-ttu-id="f141b-119">Pour plus d’informations sur ces niveaux d’isolation des transactions, consultez le **membres** section à [http://go.microsoft.com/fwlink/?LinkId=126983](http://go.microsoft.com/fwlink/?LinkId=126983).</span><span class="sxs-lookup"><span data-stu-id="f141b-119">For information about these transaction isolation levels, see the **Members** section at [http://go.microsoft.com/fwlink/?LinkId=126983](http://go.microsoft.com/fwlink/?LinkId=126983).</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="f141b-120">Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] prend en charge uniquement les niveaux d’isolation des deux transactions suivants : ReadCommitted et Serializable.</span><span class="sxs-lookup"><span data-stu-id="f141b-120">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] supports only the following two transaction isolation levels: ReadCommitted and Serializable.</span></span>  
  
     <span data-ttu-id="f141b-121">![Définition du niveau d’Isolation des transactions](../../adapters-and-accelerators/adapter-oracle-database/media/96a66f86-0321-4aa6-9e72-ada30d7de064.gif "96a66f86-0321-4aa6-9e72-ada30d7de064")</span><span class="sxs-lookup"><span data-stu-id="f141b-121">![Setting Transaction Isolation Level](../../adapters-and-accelerators/adapter-oracle-database/media/96a66f86-0321-4aa6-9e72-ada30d7de064.gif "96a66f86-0321-4aa6-9e72-ada30d7de064")</span></span>  
  
14. <span data-ttu-id="f141b-122">Cliquez sur **OK** dans les **propriétés du Transport WCF-Custom** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="f141b-122">Click **OK** in the **WCF-Custom Transport Properties** dialog box.</span></span>  
  
15. <span data-ttu-id="f141b-123">Cliquez sur **OK** dans la boîte de dialogue pour enregistrer les modifications.</span><span class="sxs-lookup"><span data-stu-id="f141b-123">Click **OK** in the open dialog boxes to save the changes.</span></span>