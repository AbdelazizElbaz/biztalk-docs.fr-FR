---
title: "Délai de bail non valide | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 81b7b2a0-e9e6-4165-88bc-f712b5cbacb6
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6de2eef0627a4297524e0aca62fa9ae64c85e5c9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="invalid-lease-timeout"></a><span data-ttu-id="57602-102">Délai d'expiration du bail non valide</span><span class="sxs-lookup"><span data-stu-id="57602-102">Invalid lease timeout</span></span>
## <a name="details"></a><span data-ttu-id="57602-103">Détails</span><span class="sxs-lookup"><span data-stu-id="57602-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="57602-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="57602-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="57602-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="57602-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="57602-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="57602-106">Event ID</span></span>|<span data-ttu-id="57602-107">0</span><span class="sxs-lookup"><span data-stu-id="57602-107">0</span></span>|  
|<span data-ttu-id="57602-108">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="57602-108">Event Source</span></span>|<span data-ttu-id="57602-109">0</span><span class="sxs-lookup"><span data-stu-id="57602-109">0</span></span>|  
|<span data-ttu-id="57602-110">Composant</span><span class="sxs-lookup"><span data-stu-id="57602-110">Component</span></span>|<span data-ttu-id="57602-111">0</span><span class="sxs-lookup"><span data-stu-id="57602-111">0</span></span>|  
|<span data-ttu-id="57602-112">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="57602-112">Symbolic Name</span></span>|<span data-ttu-id="57602-113">0</span><span class="sxs-lookup"><span data-stu-id="57602-113">0</span></span>|  
|<span data-ttu-id="57602-114">Texte du message</span><span class="sxs-lookup"><span data-stu-id="57602-114">Message Text</span></span>|<span data-ttu-id="57602-115">Délai d'expiration du bail non valide.</span><span class="sxs-lookup"><span data-stu-id="57602-115">Invalid lease timeout.</span></span> <span data-ttu-id="57602-116">Plage valide : 0 à 23 heures, 0 à 59 minutes et 0 à 59 secondes</span><span class="sxs-lookup"><span data-stu-id="57602-116">Valid range: 0 to 23 hours, 0 to 59 minutes, and 0 to 59 seconds</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="57602-117">Explication</span><span class="sxs-lookup"><span data-stu-id="57602-117">Explanation</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="57602-118">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="57602-118">User Action</span></span>  
 <span data-ttu-id="57602-119">La procédure suivante permet de configurer les paramètres du délai d'attente.</span><span class="sxs-lookup"><span data-stu-id="57602-119">Use the following procedure to configure the timeout settings.</span></span>  
  
#### <a name="to-configure-the-timeout-settings"></a><span data-ttu-id="57602-120">Pour configurer les paramètres du délai d'attente</span><span class="sxs-lookup"><span data-stu-id="57602-120">To configure the timeout settings</span></span>  
  
1.  <span data-ttu-id="57602-121">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="57602-121">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="57602-122">Dans la racine de la Console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez **groupe BizTalk**, développez **Applications**.</span><span class="sxs-lookup"><span data-stu-id="57602-122">In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand  **Applications**.</span></span>  
  
3.  <span data-ttu-id="57602-123">Recherchez votre application, puis recherchez votre transport.</span><span class="sxs-lookup"><span data-stu-id="57602-123">Locate your application and then locate your transport.</span></span>  
  
4.  <span data-ttu-id="57602-124">Cliquez avec le bouton droit sur le nom du transport.</span><span class="sxs-lookup"><span data-stu-id="57602-124">Right-click the transport name.</span></span>  
  
5.  <span data-ttu-id="57602-125">Cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="57602-125">Click **Properties**.</span></span>  
  
6.  <span data-ttu-id="57602-126">Dans le port **Type** liste, sélectionnez **WCF-NetTcP**.</span><span class="sxs-lookup"><span data-stu-id="57602-126">In the port **Type** list, select **WCF-NetTcP**.</span></span>  
  
7.  <span data-ttu-id="57602-127">Cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="57602-127">Click **Configure**.</span></span>  
  
8.  <span data-ttu-id="57602-128">Dans le **propriétés du Transport WCF-NetTcP** boîte de dialogue, cliquez sur le **liaison** onglet.</span><span class="sxs-lookup"><span data-stu-id="57602-128">In the **WCF-NetTcP Transport Properties** dialog box, click the **Binding** tab.</span></span>  
  
9. <span data-ttu-id="57602-129">Dans le **les paramètres de Pool de connexions** section, vérifiez que le **le délai de bail (hh : mm :)** plage est valide.</span><span class="sxs-lookup"><span data-stu-id="57602-129">In the **Connection Pool settings** section, ensure the **Lease timeout (hh:mm:ss)** range is valid.</span></span> <span data-ttu-id="57602-130">Les valeurs acceptables vont de 0 à 23 heures, 0 à 59 minutes et 0 à 59 secondes.</span><span class="sxs-lookup"><span data-stu-id="57602-130">Acceptable values are 0 to 23 hours, 0 to 59 minutes, and 0 to 59 seconds.</span></span>