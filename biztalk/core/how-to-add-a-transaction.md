---
title: "L’ajout d’une Transaction | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- adding, transactions
- transactions, adding
ms.assetid: 25385c20-3025-4cf1-bc1f-ef266e081bad
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 24c67a9c76ae87f2355bb0ea4638d3bd156cda6e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-a-transaction"></a><span data-ttu-id="d5ff8-102">Ajout d'une transaction</span><span class="sxs-lookup"><span data-stu-id="d5ff8-102">How to Add a Transaction</span></span>
<span data-ttu-id="d5ff8-103">Pour ajouter une transaction, procédez comme suit.</span><span class="sxs-lookup"><span data-stu-id="d5ff8-103">Follow these steps to add a transaction.</span></span>  
  
### <a name="to-add-a-transaction"></a><span data-ttu-id="d5ff8-104">Pour ajouter une transaction</span><span class="sxs-lookup"><span data-stu-id="d5ff8-104">To add a transaction</span></span>  
  
1.  <span data-ttu-id="d5ff8-105">Cliquez sur le **Transactions** onglet.</span><span class="sxs-lookup"><span data-stu-id="d5ff8-105">Click the **Transactions** tab.</span></span>  
  
2.  <span data-ttu-id="d5ff8-106">Cliquez sur **ajouter une Transaction**.</span><span class="sxs-lookup"><span data-stu-id="d5ff8-106">Click **Add Transaction**.</span></span>  
  
3.  <span data-ttu-id="d5ff8-107">Cliquez sur **ajouter une nouvelle valeur**.</span><span class="sxs-lookup"><span data-stu-id="d5ff8-107">Click **Add a New Value**.</span></span> <span data-ttu-id="d5ff8-108">Entrez les informations suivantes, puis cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="d5ff8-108">Enter the following information, and then click **Add**.</span></span>  
  
    1.  <span data-ttu-id="d5ff8-109">**Nom du nœud :** Vérifiez qu’il s’agit de **MSEXTERNAL**.</span><span class="sxs-lookup"><span data-stu-id="d5ff8-109">**Node Name:** Verify that this is **MSEXTERNAL**.</span></span>  
  
    2.  <span data-ttu-id="d5ff8-110">**Type de transaction :** Vérifiez qu’il s’agit de **asynchrone sortant**.</span><span class="sxs-lookup"><span data-stu-id="d5ff8-110">**Transaction Type:** Verify that this is **Outbound Asynchronous**.</span></span>  
  
    3.  <span data-ttu-id="d5ff8-111">**Message de demande :** entrez `LOCATION_SYNC`.</span><span class="sxs-lookup"><span data-stu-id="d5ff8-111">**Request Message:** Enter `LOCATION_SYNC`.</span></span>  
  
    4.  <span data-ttu-id="d5ff8-112">**Version de Message de demande :** entrez `VERSION_1`.</span><span class="sxs-lookup"><span data-stu-id="d5ff8-112">**Request Message Version:** Enter `VERSION_1`.</span></span>  
  
     ![](../core/media/psadapter-38-task-gatewayaddtransaction.gif "PSAdapter_38_Task_GatewayAddTransaction")  
  
4.  <span data-ttu-id="d5ff8-113">Sur le **détails de la Transaction** , vérifiez les paramètres suivants :</span><span class="sxs-lookup"><span data-stu-id="d5ff8-113">On the **Transaction Detail** tab, verify the following settings:</span></span>  
  
    1.  <span data-ttu-id="d5ff8-114">**État :** Active.</span><span class="sxs-lookup"><span data-stu-id="d5ff8-114">**Status:** Active.</span></span>  
  
    2.  <span data-ttu-id="d5ff8-115">**Routage :** implicite.</span><span class="sxs-lookup"><span data-stu-id="d5ff8-115">**Routing:** Implicit.</span></span>  
  
     ![](../core/media/psadapter-39-task-gatewaytransdetail.gif "PSAdapter_39_Task_GatewayTransDetail")  
  
5.  <span data-ttu-id="d5ff8-116">Cliquez sur **Enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="d5ff8-116">Click **Save**.</span></span>  
  
6.  <span data-ttu-id="d5ff8-117">Cliquez sur le **revenir à la liste des transactions** lien.</span><span class="sxs-lookup"><span data-stu-id="d5ff8-117">Click the **Return to Transaction List** link.</span></span>  
  
     <span data-ttu-id="d5ff8-118">La transaction apparaît dans la liste.</span><span class="sxs-lookup"><span data-stu-id="d5ff8-118">The transaction appears in the list of transactions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5ff8-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d5ff8-119">See Also</span></span>  
 [<span data-ttu-id="d5ff8-120">Création d’un Port et l’hôte de HTTP PeopleSoft</span><span class="sxs-lookup"><span data-stu-id="d5ff8-120">Creating a PeopleSoft HTTP Host and Port</span></span>](../core/creating-a-peoplesoft-http-host-and-port.md)