---
title: "Délai d’attente de fermeture non valide | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b4510329-9fd9-428f-91a3-d72723e9a5e4
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b86a75ab524a91ddf7fab7b6e764557150d55606
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="invalid-close-timeout"></a><span data-ttu-id="1efb3-102">Délai d'attente de clôture non valide</span><span class="sxs-lookup"><span data-stu-id="1efb3-102">Invalid close timeout</span></span>
## <a name="details"></a><span data-ttu-id="1efb3-103">Détails</span><span class="sxs-lookup"><span data-stu-id="1efb3-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1efb3-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="1efb3-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="1efb3-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="1efb3-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="1efb3-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="1efb3-106">Event ID</span></span>|<span data-ttu-id="1efb3-107">0</span><span class="sxs-lookup"><span data-stu-id="1efb3-107">0</span></span>|  
|<span data-ttu-id="1efb3-108">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="1efb3-108">Event Source</span></span>|<span data-ttu-id="1efb3-109">0</span><span class="sxs-lookup"><span data-stu-id="1efb3-109">0</span></span>|  
|<span data-ttu-id="1efb3-110">Composant</span><span class="sxs-lookup"><span data-stu-id="1efb3-110">Component</span></span>|<span data-ttu-id="1efb3-111">0</span><span class="sxs-lookup"><span data-stu-id="1efb3-111">0</span></span>|  
|<span data-ttu-id="1efb3-112">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="1efb3-112">Symbolic Name</span></span>|<span data-ttu-id="1efb3-113">0</span><span class="sxs-lookup"><span data-stu-id="1efb3-113">0</span></span>|  
|<span data-ttu-id="1efb3-114">Texte du message</span><span class="sxs-lookup"><span data-stu-id="1efb3-114">Message Text</span></span>|<span data-ttu-id="1efb3-115">Délai d'attente de clôture non valide.</span><span class="sxs-lookup"><span data-stu-id="1efb3-115">Invalid close timeout.</span></span> <span data-ttu-id="1efb3-116">Plage valide : 0 à 23 heures, 0 à 59 minutes et 0 à 59 secondes.</span><span class="sxs-lookup"><span data-stu-id="1efb3-116">Valid range: 0 to 23 hours, 0 to 59 minutes, and 0 to 59 seconds.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="1efb3-117">Explication</span><span class="sxs-lookup"><span data-stu-id="1efb3-117">Explanation</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="1efb3-118">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="1efb3-118">User Action</span></span>  
 <span data-ttu-id="1efb3-119">La procédure suivante permet de configurer la plage du délai d'attente.</span><span class="sxs-lookup"><span data-stu-id="1efb3-119">Use the following procedure to configure the timeout range.</span></span>  
  
#### <a name="to-configure-the-timeout-range"></a><span data-ttu-id="1efb3-120">Pour configurer la plage du délai d'attente</span><span class="sxs-lookup"><span data-stu-id="1efb3-120">To configure the timeout range</span></span>  
  
1.  <span data-ttu-id="1efb3-121">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="1efb3-121">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="1efb3-122">Dans la racine de la Console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez **groupe BizTalk**, développez **Applications**.</span><span class="sxs-lookup"><span data-stu-id="1efb3-122">In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand  **Applications**.</span></span>  
  
3.  <span data-ttu-id="1efb3-123">Recherchez votre application, puis recherchez votre transport.</span><span class="sxs-lookup"><span data-stu-id="1efb3-123">Locate your application and then locate your transport.</span></span>  
  
4.  <span data-ttu-id="1efb3-124">Cliquez avec le bouton droit sur le nom du transport.</span><span class="sxs-lookup"><span data-stu-id="1efb3-124">Right-click the transport name.</span></span>  
  
5.  <span data-ttu-id="1efb3-125">Cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="1efb3-125">Click **Properties**.</span></span>  
  
6.  <span data-ttu-id="1efb3-126">Dans le port **Type** , sélectionnez le port approprié.</span><span class="sxs-lookup"><span data-stu-id="1efb3-126">In the port **Type** list, select the correct port.</span></span>  
  
7.  <span data-ttu-id="1efb3-127">Cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="1efb3-127">Click **Configure**.</span></span>  
  
8.  <span data-ttu-id="1efb3-128">Dans le **WCF [***type de transport***] propriétés** boîte de dialogue, cliquez sur le **liaison** onglet.</span><span class="sxs-lookup"><span data-stu-id="1efb3-128">In the **WCF [***transport type***] Properties** dialog box, click the **Binding** tab.</span></span>  
  
9. <span data-ttu-id="1efb3-129">Vérifiez que la plage de délai d'attente est valide.</span><span class="sxs-lookup"><span data-stu-id="1efb3-129">Ensure the timeout range is valid.</span></span> <span data-ttu-id="1efb3-130">Les valeurs acceptables vont de 0 à 23 heures, 0 à 59 minutes et 0 à 59 secondes.</span><span class="sxs-lookup"><span data-stu-id="1efb3-130">Acceptable values are 0 to 23 hours, 0 to 59 minutes, and 0 to 59 seconds.</span></span>