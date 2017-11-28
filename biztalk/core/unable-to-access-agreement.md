---
title: "Impossible d’accéder au contrat | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 72890ee9-54c9-48ed-8c6e-8b329d79c68b
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c5a28b2b3587781d66e8788ca88931c7c5522bac
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="unable-to-access-agreement"></a><span data-ttu-id="2d827-102">Impossible d'accéder à l'accord</span><span class="sxs-lookup"><span data-stu-id="2d827-102">Unable to access agreement</span></span>
## <a name="details"></a><span data-ttu-id="2d827-103">Détails</span><span class="sxs-lookup"><span data-stu-id="2d827-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2d827-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="2d827-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="2d827-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="2d827-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="2d827-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="2d827-106">Event ID</span></span>|-|  
|<span data-ttu-id="2d827-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="2d827-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="2d827-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="2d827-108"> EDI</span></span>|  
|<span data-ttu-id="2d827-109">Composant</span><span class="sxs-lookup"><span data-stu-id="2d827-109">Component</span></span>|<span data-ttu-id="2d827-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="2d827-110">EDI Engine</span></span>|  
|<span data-ttu-id="2d827-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="2d827-111">Symbolic Name</span></span>|<span data-ttu-id="2d827-112">UnableToLocateAS2PartyError</span><span class="sxs-lookup"><span data-stu-id="2d827-112">UnableToLocateAS2PartyError</span></span>|  
|<span data-ttu-id="2d827-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="2d827-113">Message Text</span></span>|<span data-ttu-id="2d827-114">Impossible d'accéder à l'accord.</span><span class="sxs-lookup"><span data-stu-id="2d827-114">Unable to access agreement.</span></span> <span data-ttu-id="2d827-115">AS2From : {0} AS2To : {1}.</span><span class="sxs-lookup"><span data-stu-id="2d827-115">AS2From: {0} AS2To: {1}.</span></span> <span data-ttu-id="2d827-116">Erreur : {{2}</span><span class="sxs-lookup"><span data-stu-id="2d827-116">Error: {2}</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="2d827-117">Explication</span><span class="sxs-lookup"><span data-stu-id="2d827-117">Explanation</span></span>  
 <span data-ttu-id="2d827-118">Cette erreur indique que BizTalk Server n'a pas pu détecter un tiers correspondant au qualificateur et à la valeur donnés.</span><span class="sxs-lookup"><span data-stu-id="2d827-118">This error indicates BizTalk Server could not find a party for the given qualifier and value.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="2d827-119">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="2d827-119">User Action</span></span>  
 <span data-ttu-id="2d827-120">Pour résoudre cette erreur, créez un alias de tiers pour le qualificateur donné :</span><span class="sxs-lookup"><span data-stu-id="2d827-120">To resolve this error, create a party alias for the given qualifier:</span></span>  
  
1.  <span data-ttu-id="2d827-121">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="2d827-121">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="2d827-122">Dans la racine de la Console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez **groupe BizTalk**, puis cliquez sur **Parties**.</span><span class="sxs-lookup"><span data-stu-id="2d827-122">In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and click **Parties**.</span></span>  
  
3.  <span data-ttu-id="2d827-123">Cliquez avec le bouton droit sur le tiers approprié.</span><span class="sxs-lookup"><span data-stu-id="2d827-123">Right-click the correct party.</span></span>  
  
4.  <span data-ttu-id="2d827-124">Cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="2d827-124">Click **Properties**.</span></span>  
  
5.  <span data-ttu-id="2d827-125">Dans le [*nom du tiers*] **propriétés de tiers** boîte de dialogue, entrez **EDIINT-AS2 From Value** dans les **nom** colonne.</span><span class="sxs-lookup"><span data-stu-id="2d827-125">In the [*party name*] **Party Properties** dialog box, enter **EDIINT-AS2 From Value** in the **Name** column.</span></span>  
  
6.  <span data-ttu-id="2d827-126">Entrez le nom du tiers dans le **valeur** colonne.</span><span class="sxs-lookup"><span data-stu-id="2d827-126">Enter the party name in the **Value** column.</span></span>  
  
7.  <span data-ttu-id="2d827-127">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="2d827-127">Click **OK**.</span></span>