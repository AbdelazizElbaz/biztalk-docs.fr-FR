---
title: "Le planificateur n’a pas pu planifier le traitement par lots | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5ac6d79c-c995-4c95-a4da-ee2f50b9a13a
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bef1df18d88f8497fde440383d63bc64eefdd69a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="scheduler-was-unable-to-schedule-the-batch"></a><span data-ttu-id="0d12c-102">Le planificateur n'a pas réussi à planifier le lot</span><span class="sxs-lookup"><span data-stu-id="0d12c-102">Scheduler was unable to schedule the batch</span></span>
## <a name="details"></a><span data-ttu-id="0d12c-103">Détails</span><span class="sxs-lookup"><span data-stu-id="0d12c-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0d12c-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="0d12c-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="0d12c-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="0d12c-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="0d12c-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="0d12c-106">Event ID</span></span>|-|  
|<span data-ttu-id="0d12c-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="0d12c-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="0d12c-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="0d12c-108"> EDI</span></span>|  
|<span data-ttu-id="0d12c-109">Composant</span><span class="sxs-lookup"><span data-stu-id="0d12c-109">Component</span></span>|<span data-ttu-id="0d12c-110">Moteur de traitement par lot</span><span class="sxs-lookup"><span data-stu-id="0d12c-110">Batching Engine</span></span>|  
|<span data-ttu-id="0d12c-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="0d12c-111">Symbolic Name</span></span>|-|  
|<span data-ttu-id="0d12c-112">Texte du message</span><span class="sxs-lookup"><span data-stu-id="0d12c-112">Message Text</span></span>|<span data-ttu-id="0d12c-113">Le planificateur n'a pas réussi à planifier le lot</span><span class="sxs-lookup"><span data-stu-id="0d12c-113">Scheduler was unable to schedule the batch</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="0d12c-114">Explication</span><span class="sxs-lookup"><span data-stu-id="0d12c-114">Explanation</span></span>  
 <span data-ttu-id="0d12c-115">Cette erreur indique que le planificateur n'a pas réussi à identifier l'occurrence suivante du déclenchement d'un lot.</span><span class="sxs-lookup"><span data-stu-id="0d12c-115">This error indicates the scheduler could not determine the next occurrence of a batch release.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="0d12c-116">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="0d12c-116">User Action</span></span>  
 <span data-ttu-id="0d12c-117">Pour résoudre cette erreur, assurez-vous que la planification du déclenchement du lot est valide :</span><span class="sxs-lookup"><span data-stu-id="0d12c-117">To resolve this error, make sure the batch release schedule is valid:</span></span>  
  
1.  <span data-ttu-id="0d12c-118">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="0d12c-118">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="0d12c-119">Dans la racine de la Console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez **groupe BizTalk**, puis cliquez sur **Parties**.</span><span class="sxs-lookup"><span data-stu-id="0d12c-119">In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and click **Parties**.</span></span>  
  
3.  <span data-ttu-id="0d12c-120">Cliquez avec le bouton droit sur le tiers approprié.</span><span class="sxs-lookup"><span data-stu-id="0d12c-120">Right-click the correct party.</span></span>  
  
4.  <span data-ttu-id="0d12c-121">Cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="0d12c-121">Click **Properties**.</span></span>  
  
5.  <span data-ttu-id="0d12c-122">Dans le [*nom du tiers*] **propriétés de tiers** boîte de dialogue, dans le volet gauche, cliquez sur **Ports d’envoi**.</span><span class="sxs-lookup"><span data-stu-id="0d12c-122">In the [*party name*] **Party Properties** dialog box, in the left pane, click **Send Ports**.</span></span>  
  
6.  <span data-ttu-id="0d12c-123">Entrez le nom de port d’envoi dans le **Ports d’envoi** liste.</span><span class="sxs-lookup"><span data-stu-id="0d12c-123">Enter the Send port name in the **Send Ports** list.</span></span>  
  
7.  <span data-ttu-id="0d12c-124">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="0d12c-124">Click **OK**.</span></span>