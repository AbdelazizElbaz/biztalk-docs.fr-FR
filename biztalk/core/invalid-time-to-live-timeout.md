---
title: "Durée de vie non valide | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c2ddb6de-8c3b-4dee-a984-980e1caea95e
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9171fd311a07317c0480e6e4d1ef35742e0e8bcd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="invalid-time-to-live-timeout"></a><span data-ttu-id="b2edb-102">Durée de vie non valide</span><span class="sxs-lookup"><span data-stu-id="b2edb-102">Invalid time to live timeout</span></span>
## <a name="details"></a><span data-ttu-id="b2edb-103">Détails</span><span class="sxs-lookup"><span data-stu-id="b2edb-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b2edb-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="b2edb-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="b2edb-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="b2edb-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="b2edb-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="b2edb-106">Event ID</span></span>|<span data-ttu-id="b2edb-107">0</span><span class="sxs-lookup"><span data-stu-id="b2edb-107">0</span></span>|  
|<span data-ttu-id="b2edb-108">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="b2edb-108">Event Source</span></span>|<span data-ttu-id="b2edb-109">0</span><span class="sxs-lookup"><span data-stu-id="b2edb-109">0</span></span>|  
|<span data-ttu-id="b2edb-110">Composant</span><span class="sxs-lookup"><span data-stu-id="b2edb-110">Component</span></span>|<span data-ttu-id="b2edb-111">0</span><span class="sxs-lookup"><span data-stu-id="b2edb-111">0</span></span>|  
|<span data-ttu-id="b2edb-112">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="b2edb-112">Symbolic Name</span></span>|<span data-ttu-id="b2edb-113">0</span><span class="sxs-lookup"><span data-stu-id="b2edb-113">0</span></span>|  
|<span data-ttu-id="b2edb-114">Texte du message</span><span class="sxs-lookup"><span data-stu-id="b2edb-114">Message Text</span></span>|<span data-ttu-id="b2edb-115">Durée de vie non valide.</span><span class="sxs-lookup"><span data-stu-id="b2edb-115">Invalid time to live timeout.</span></span> <span data-ttu-id="b2edb-116">Plage valide : 0 à 23 heures, 0 à 59 minutes et 0 à 59 secondes</span><span class="sxs-lookup"><span data-stu-id="b2edb-116">Valid range: 0 to 23 hours, 0 to 59 minutes, and 0 to 59 seconds</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="b2edb-117">Explication</span><span class="sxs-lookup"><span data-stu-id="b2edb-117">Explanation</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="b2edb-118">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="b2edb-118">User Action</span></span>  
 <span data-ttu-id="b2edb-119">La procédure suivante permet de configurer la plage du délai d'attente.</span><span class="sxs-lookup"><span data-stu-id="b2edb-119">Use the following procedure to configure the timeout range.</span></span>  
  
#### <a name="to-configure-the-timeout-range"></a><span data-ttu-id="b2edb-120">Pour configurer la plage du délai d'attente</span><span class="sxs-lookup"><span data-stu-id="b2edb-120">To configure the timeout range</span></span>  
  
1.  <span data-ttu-id="b2edb-121">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="b2edb-121">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="b2edb-122">Dans la racine de la Console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez **groupe BizTalk**, développez **Applications**.</span><span class="sxs-lookup"><span data-stu-id="b2edb-122">In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand  **Applications**.</span></span>  
  
3.  <span data-ttu-id="b2edb-123">Recherchez votre application, puis recherchez votre transport.</span><span class="sxs-lookup"><span data-stu-id="b2edb-123">Locate your application and then locate your transport.</span></span>  
  
4.  <span data-ttu-id="b2edb-124">Cliquez avec le bouton droit sur le nom du transport.</span><span class="sxs-lookup"><span data-stu-id="b2edb-124">Right-click the transport name.</span></span>  
  
5.  <span data-ttu-id="b2edb-125">Cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="b2edb-125">Click **Properties**.</span></span>  
  
6.  <span data-ttu-id="b2edb-126">Dans le port **Type** liste, sélectionnez **WCF-NetMsmq**.</span><span class="sxs-lookup"><span data-stu-id="b2edb-126">In the port **Type** list, select **WCF-NetMsmq**.</span></span>  
  
7.  <span data-ttu-id="b2edb-127">Cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="b2edb-127">Click **Configure**.</span></span>  
  
8.  <span data-ttu-id="b2edb-128">Dans le **propriétés du Transport WCF-NetMsmq** boîte de dialogue, cliquez sur le **liaison** onglet.</span><span class="sxs-lookup"><span data-stu-id="b2edb-128">In the **WCF-NetMsmq Transport Properties** dialog box, click the **Binding** tab.</span></span>  
  
9. <span data-ttu-id="b2edb-129">Dans le **les paramètres de file d’attente** section, vérifiez que le **(dd:hh:mm:ss) en direct de temps du Message** plage est valide.</span><span class="sxs-lookup"><span data-stu-id="b2edb-129">In the **Queue Settings** section, ensure the **Message time to live (dd:hh:mm:ss)** range is valid.</span></span> <span data-ttu-id="b2edb-130">Les valeurs acceptables vont de 0 à 23 heures, 0 à 59 minutes et 0 à 59 secondes.</span><span class="sxs-lookup"><span data-stu-id="b2edb-130">Acceptable values are 0 to 23 hours, 0 to 59 minutes, and 0 to 59 seconds.</span></span>