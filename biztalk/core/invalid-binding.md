---
title: Liaison non valide | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3e851f7f-ffc8-4f55-b06e-501a7f41b32a
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2e5733df4d4d7d6ef9e70e6a2a16302cc19ac5d9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="invalid-binding"></a><span data-ttu-id="d8268-102">Liaison non valide</span><span class="sxs-lookup"><span data-stu-id="d8268-102">Invalid binding</span></span>
## <a name="details"></a><span data-ttu-id="d8268-103">Détails</span><span class="sxs-lookup"><span data-stu-id="d8268-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d8268-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="d8268-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="d8268-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="d8268-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="d8268-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="d8268-106">Event ID</span></span>|<span data-ttu-id="d8268-107">0</span><span class="sxs-lookup"><span data-stu-id="d8268-107">0</span></span>|  
|<span data-ttu-id="d8268-108">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="d8268-108">Event Source</span></span>|<span data-ttu-id="d8268-109">0</span><span class="sxs-lookup"><span data-stu-id="d8268-109">0</span></span>|  
|<span data-ttu-id="d8268-110">Composant</span><span class="sxs-lookup"><span data-stu-id="d8268-110">Component</span></span>|<span data-ttu-id="d8268-111">0</span><span class="sxs-lookup"><span data-stu-id="d8268-111">0</span></span>|  
|<span data-ttu-id="d8268-112">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="d8268-112">Symbolic Name</span></span>|<span data-ttu-id="d8268-113">0</span><span class="sxs-lookup"><span data-stu-id="d8268-113">0</span></span>|  
|<span data-ttu-id="d8268-114">Texte du message</span><span class="sxs-lookup"><span data-stu-id="d8268-114">Message Text</span></span>|<span data-ttu-id="d8268-115">Liaison non valide</span><span class="sxs-lookup"><span data-stu-id="d8268-115">Invalid binding</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="d8268-116">Explication</span><span class="sxs-lookup"><span data-stu-id="d8268-116">Explanation</span></span>  
 <span data-ttu-id="d8268-117">Cette erreur indique que l'adaptateur ne peut pas créer la liaison spécifiée dans la  configuration de liaison de l'emplacement de réception ou du port d'envoi.</span><span class="sxs-lookup"><span data-stu-id="d8268-117">This error indicates the adapter cannot create the binding specified in the binding configuration of the receive location or send port.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="d8268-118">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="d8268-118">User Action</span></span>  
 <span data-ttu-id="d8268-119">La procédure suivante permet de vérifier les éléments de liaison.</span><span class="sxs-lookup"><span data-stu-id="d8268-119">Use the following procedure to verify binding elements.</span></span>  
  
#### <a name="to-verify-binding-elements"></a><span data-ttu-id="d8268-120">Pour vérifier les éléments de liaison</span><span class="sxs-lookup"><span data-stu-id="d8268-120">To verify binding elements</span></span>  
  
1.  <span data-ttu-id="d8268-121">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="d8268-121">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="d8268-122">Dans la racine de la Console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez **groupe BizTalk**, développez **Applications**.</span><span class="sxs-lookup"><span data-stu-id="d8268-122">In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand  **Applications**.</span></span>  
  
3.  <span data-ttu-id="d8268-123">Recherchez votre application, puis recherchez votre transport.</span><span class="sxs-lookup"><span data-stu-id="d8268-123">Locate your application and then locate your transport.</span></span>  
  
4.  <span data-ttu-id="d8268-124">Cliquez avec le bouton droit sur le nom du transport.</span><span class="sxs-lookup"><span data-stu-id="d8268-124">Right-click the transport name.</span></span>  
  
5.  <span data-ttu-id="d8268-125">Cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="d8268-125">Click **Properties**.</span></span>  
  
6.  <span data-ttu-id="d8268-126">Dans le port **Type** , sélectionnez le port approprié.</span><span class="sxs-lookup"><span data-stu-id="d8268-126">In the port **Type** list, select the correct port.</span></span>  
  
7.  <span data-ttu-id="d8268-127">Cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="d8268-127">Click **Configure**.</span></span>  
  
8.  <span data-ttu-id="d8268-128">Dans le **WCF [***type de transport***] propriétés du Transport** boîte de dialogue, cliquez sur le **liaison** onglet.</span><span class="sxs-lookup"><span data-stu-id="d8268-128">In the **WCF [***transport type***] Transport Properties** dialog box, click the **Binding** tab.</span></span>  
  
9. <span data-ttu-id="d8268-129">Assurez-vous que les éléments de liaison spécifiés dans la configuration sont valides.</span><span class="sxs-lookup"><span data-stu-id="d8268-129">Ensure the binding elements specified in the configuration are valid.</span></span>