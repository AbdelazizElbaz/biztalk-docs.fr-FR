---
title: "Comment utiliser l’appel de règles de forme | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Call Rules shape [Orchestration Designer], how to
- Call Rules shape [Orchestration Designer], configuring
- Call Rules shape [Orchestration Designer], policies
- policies, Call Rules shape [Orchestration Designer]
ms.assetid: e4bc8a2c-de7e-4e3a-81b8-12bcebb17d27
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a634c2e0a97e627925390610bf4c3039c8afc85c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-use-the-call-rules-shape"></a><span data-ttu-id="eea26-102">Utilisation de la forme Appeler règles</span><span class="sxs-lookup"><span data-stu-id="eea26-102">How to Use the Call Rules Shape</span></span>
<span data-ttu-id="eea26-103">Dans le Concepteur d’Orchestration, vous pouvez utiliser la **appeler règles** forme pour appeler une stratégie d’entreprise.</span><span class="sxs-lookup"><span data-stu-id="eea26-103">In Orchestration Designer, you can use the **Call Rules** shape to call a business policy.</span></span>  
  
### <a name="to-configure-the-call-rules-shape"></a><span data-ttu-id="eea26-104">Pour configurer la forme Appeler règles</span><span class="sxs-lookup"><span data-stu-id="eea26-104">To configure the Call Rules shape</span></span>  
  
1.  <span data-ttu-id="eea26-105">À partir de la boîte à outils, dans le **Orchestrations BizTalk** onglet, faites glisser le **appeler règles** forme sur une ligne de connexion sur l’aire de conception d’Orchestration.</span><span class="sxs-lookup"><span data-stu-id="eea26-105">From the Toolbox, in the **BizTalk Orchestrations** tab, drag the **Call Rules** shape onto a connecting line on the Orchestration Design Surface.</span></span>  
  
     <span data-ttu-id="eea26-106">— Ou :</span><span class="sxs-lookup"><span data-stu-id="eea26-106">—Or—</span></span>  
  
     <span data-ttu-id="eea26-107">Avec le bouton droit de la ligne de connexion ou l’espace réservé où vous souhaitez ajouter la forme, pointez sur **insérer une forme** dans le menu contextuel, puis cliquez sur **appeler règles**.</span><span class="sxs-lookup"><span data-stu-id="eea26-107">Right-click the connecting line or the shape placeholder where you want to add the shape, point to **Insert Shape** on the context menu, and then click **Call Rules**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="eea26-108">Dans [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)], vous n’avez pas besoin d’avoir une étendue atomique pour insérer un **appeler règles** forme.</span><span class="sxs-lookup"><span data-stu-id="eea26-108">In [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)], you do not need to have an atomic scope to insert a **Call Rules** shape.</span></span> <span data-ttu-id="eea26-109">Vous pouvez faire glisser un **appeler règles** mettre en forme dans l’aire de conception d’Orchestration à partir de la boîte à outils.</span><span class="sxs-lookup"><span data-stu-id="eea26-109">You can drag a **Call Rules** shape into the Orchestration Design Surface from the Toolbox.</span></span> <span data-ttu-id="eea26-110">Toutefois, dans [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)], le **appeler règles** élément de menu est désactivé dans le menu contextuel si vous essayez d’insérer un **appeler règles** forme à l’intérieur d’une orchestration qui ne dispose pas d’une étendue atomique.</span><span class="sxs-lookup"><span data-stu-id="eea26-110">However, in [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)], the **Call Rules** menu item is disabled in the context menu if you try to insert a **Call Rules** shape inside an orchestration that does not have an atomic scope.</span></span> <span data-ttu-id="eea26-111">Il s'agit d'une restriction liée au produit [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="eea26-111">This is a limitation with the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] product.</span></span>  
  
2.  <span data-ttu-id="eea26-112">Dans le Concepteur d’Orchestration, sélectionnez la **appeler règles** forme.</span><span class="sxs-lookup"><span data-stu-id="eea26-112">In Orchestration Designer, select the **Call Rules** shape.</span></span>  
  
3.  <span data-ttu-id="eea26-113">Double-cliquez sur la forme pour afficher les **configuration de la stratégie RèglesAppel** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="eea26-113">Double-click the shape to display the **CallRules policy configuration** dialog box.</span></span>  
  
4.  <span data-ttu-id="eea26-114">Dans le **sélectionnez la stratégie commerciale que vous souhaitez appeler** liste déroulante, sélectionnez la stratégie que vous avez besoin.</span><span class="sxs-lookup"><span data-stu-id="eea26-114">In the **Select the business policy you wish to call** drop-down list, select the policy you need.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="eea26-115">La configuration de la forme Appeler règles examine la toute dernière version enregistrée d'une stratégie lors de la détermination des types utilisés dans la stratégie.</span><span class="sxs-lookup"><span data-stu-id="eea26-115">Call Rules configuration will look at the latest saved version of a policy when determining the types used in the policy.</span></span> <span data-ttu-id="eea26-116">Lors de l’exécution, la dernière version déployée de la stratégie est utilisée.</span><span class="sxs-lookup"><span data-stu-id="eea26-116">At run time, the latest deployed version of the policy will be used.</span></span>  
  
5.  <span data-ttu-id="eea26-117">Dans le **spécifier les paramètres de stratégie** zone de liste, sélectionnez une variable à partir de la **nom de paramètre** propriété.</span><span class="sxs-lookup"><span data-stu-id="eea26-117">In the **Specify policy parameters** list box, select a variable from the **Parameter Name** property.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="eea26-118">Le **appeler règles** forme essentiellement reconstruit le message, comme si vous utilisez un **construire** forme, ce qui peut entraîner des propriétés de contexte du message soit perdu.</span><span class="sxs-lookup"><span data-stu-id="eea26-118">The **Call Rules** shape is essentially reconstructing the message, as if using a **Construct** shape, which in turn may cause context properties of the message to be lost.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="eea26-119">Vous pouvez spécifier un message ou une variable .NET en tant que paramètre à une stratégie BRE.</span><span class="sxs-lookup"><span data-stu-id="eea26-119">You can specify a message or a .NET variable as a parameter to a BRE policy.</span></span> <span data-ttu-id="eea26-120">Pour passer un **TypedXmlDocument** faits, spécifiez le message correspondant est déclaré dans l’orchestration en tant que paramètre.</span><span class="sxs-lookup"><span data-stu-id="eea26-120">To pass a **TypedXmlDocument** fact, specify the corresponding message declared in the orchestration as a parameter.</span></span> <span data-ttu-id="eea26-121">Pour transmettre un fait .NET, spécifiez une variable .NET qui a été déclarée en tant que paramètre dans l'orchestration.</span><span class="sxs-lookup"><span data-stu-id="eea26-121">To pass a .NET fact, specify a .NET variable declared in the orchestration as a parameter.</span></span> <span data-ttu-id="eea26-122">Pour transmettre un fait de la base de données, spécifiez une variable .NET de type **DataConnection** ou **TypedDataTable** en tant que paramètre à la stratégie.</span><span class="sxs-lookup"><span data-stu-id="eea26-122">To pass a database fact, specify a .NET variable of type **DataConnection** or **TypedDataTable** as a parameter to the policy.</span></span>