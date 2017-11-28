---
title: "Étape 3 (pour Azure) : Créer une file d’attente du Bus de Service | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b7192c3c-4ebf-49c4-b8ce-46a6e9fb5f4a
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d55b3222798edb245000cdde8de52565c39758a7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-3-for-azure-create-a-service-bus-queue"></a><span data-ttu-id="37cf6-102">Étape 3 (pour Azure) : Créer une file d’attente du Bus de Service</span><span class="sxs-lookup"><span data-stu-id="37cf6-102">Step 3 (For Azure): Create a Service Bus Queue</span></span>
<span data-ttu-id="37cf6-103">Dans cette rubrique, vous allez créer une file d’attente Service Bus à laquelle sera envoyée la commande client X12 après avoir été traitée et transformée à l’aide de l’accord EDI.</span><span class="sxs-lookup"><span data-stu-id="37cf6-103">In this topic, you create a Service Bus Queue to which the X12 sales order is sent after it is processed and transformed using the EDI agreement.</span></span>  
  
### <a name="to-create-a-service-bus-queue"></a><span data-ttu-id="37cf6-104">Pour créer une file d’attente Service Bus</span><span class="sxs-lookup"><span data-stu-id="37cf6-104">To create a Service Bus Queue</span></span>  
  
1.  <span data-ttu-id="37cf6-105">Se connecter à la [portail de gestion Windows Azure CTP](http://go.microsoft.com/fwlink/p/?LinkId=202886) à l’aide de votre compte Microsoft.</span><span class="sxs-lookup"><span data-stu-id="37cf6-105">Log in to the [Windows Azure CTP Management Portal](http://go.microsoft.com/fwlink/p/?LinkId=202886) using your Microsoft account.</span></span>  
  
2.  <span data-ttu-id="37cf6-106">Sur le côté inférieur gauche de la page, cliquez sur **AppFabric**.</span><span class="sxs-lookup"><span data-stu-id="37cf6-106">On the lower left-hand side of the page, click **AppFabric**.</span></span>  
  
3.  <span data-ttu-id="37cf6-107">Développez les services dans l’arborescence à gauche, développez votre abonnement, puis cliquez sur un espace de noms que vous devez avoir déjà créé.</span><span class="sxs-lookup"><span data-stu-id="37cf6-107">Expand Services in the tree on the left-hand side, expand your subscription, and click a namespace that you must have already created.</span></span> <span data-ttu-id="37cf6-108">Si vous n’avez pas déjà un espace de noms, consultez [Comment : créer ou modifier un Namespace de Service Windows Azure CTP](http://msdn.microsoft.com/library/windowsazure/hh697699.aspx).</span><span class="sxs-lookup"><span data-stu-id="37cf6-108">If you don’t have a namespace already, see [How to: Create or Modify a Windows Azure CTP Service Namespace](http://msdn.microsoft.com/library/windowsazure/hh697699.aspx).</span></span>  
  
4.  <span data-ttu-id="37cf6-109">Pour créer une file d’attente, cliquez sur **nouvelle file d’attente** à partir de la **gérer les entités** catégorie à partir de la barre d’outils en haut de la page.</span><span class="sxs-lookup"><span data-stu-id="37cf6-109">To create a Queue click **New Queue** from the **Manage Entities** category from the toolbar at the top of the page.</span></span>  
  
5.  <span data-ttu-id="37cf6-110">Dans le **nouvelle file d’attente** boîte de dialogue, entrez un nom pour la file d’attente.</span><span class="sxs-lookup"><span data-stu-id="37cf6-110">In the **New Queue** dialog box, enter a name for the Queue.</span></span> <span data-ttu-id="37cf6-111">Pour ce didacticiel, entrez le nom du `queueordersedi`, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="37cf6-111">For this tutorial, enter the name as `queueordersedi`, and then click **OK**.</span></span> <span data-ttu-id="37cf6-112">Vous avez spécifié ce nom dans le cadre de l’accord EDI que vous avez créé dans [étape 2 (pour Azure) : création d’un accord EDI](../core/step-2-for-azure-create-an-edi-agreement.md).</span><span class="sxs-lookup"><span data-stu-id="37cf6-112">You specified this name as part of the EDI agreement you created in [Step 2 (For Azure): Create an EDI Agreement](../core/step-2-for-azure-create-an-edi-agreement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37cf6-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="37cf6-113">See Also</span></span>  
 [<span data-ttu-id="37cf6-114">Didacticiel 4 : Création d’une Application hybride à l’aide de BizTalk Server 2013</span><span class="sxs-lookup"><span data-stu-id="37cf6-114">Tutorial 4: Creating a Hybrid Application Using BizTalk Server 2013</span></span>](../core/tutorial-4-creating-a-hybrid-application-using-biztalk-server-2013.md)