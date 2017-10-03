---
title: "Impossible d’accéder au tiers avec port d’envoi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ffacba77-76e8-4f03-be26-134a9999d6c1
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2aa582319226b114720ef234b8e3f65e416a94d1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="unable-to-access-party-using-send-port"></a><span data-ttu-id="6a7eb-102">Impossible d'accéder au tiers avec port d'envoi</span><span class="sxs-lookup"><span data-stu-id="6a7eb-102">Unable to access party using send port</span></span>
## <a name="details"></a><span data-ttu-id="6a7eb-103">Détails</span><span class="sxs-lookup"><span data-stu-id="6a7eb-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6a7eb-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="6a7eb-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="6a7eb-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="6a7eb-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="6a7eb-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="6a7eb-106">Event ID</span></span>|-|  
|<span data-ttu-id="6a7eb-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="6a7eb-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="6a7eb-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="6a7eb-108"> EDI</span></span>|  
|<span data-ttu-id="6a7eb-109">Composant</span><span class="sxs-lookup"><span data-stu-id="6a7eb-109">Component</span></span>|<span data-ttu-id="6a7eb-110">Moteur AS2</span><span class="sxs-lookup"><span data-stu-id="6a7eb-110">AS2 Engine</span></span>|  
|<span data-ttu-id="6a7eb-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="6a7eb-111">Symbolic Name</span></span>|<span data-ttu-id="6a7eb-112">UnableToLocateAS2PartyBySendPortNameError</span><span class="sxs-lookup"><span data-stu-id="6a7eb-112">UnableToLocateAS2PartyBySendPortNameError</span></span>|  
|<span data-ttu-id="6a7eb-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="6a7eb-113">Message Text</span></span>|<span data-ttu-id="6a7eb-114">Impossible d’accéder au tiers avec port d’envoi : {0}</span><span class="sxs-lookup"><span data-stu-id="6a7eb-114">Unable to access party using send port: {0}</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="6a7eb-115">Explication</span><span class="sxs-lookup"><span data-stu-id="6a7eb-115">Explanation</span></span>  
 <span data-ttu-id="6a7eb-116">Cette erreur indique que le pipeline d'envoi n'a pas réussi à trouver le tiers associé au port d'envoi spécifié pour le message AS2 sortant.</span><span class="sxs-lookup"><span data-stu-id="6a7eb-116">This error indicates the send pipeline could not find a party associated with the specified send port for the outgoing AS2 message.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="6a7eb-117">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="6a7eb-117">User Action</span></span>  
 <span data-ttu-id="6a7eb-118">Pour résoudre cette erreur, associez un tiers au port d'envoi spécifié :</span><span class="sxs-lookup"><span data-stu-id="6a7eb-118">To resolve this error, associate a party with the specified send port:</span></span>  
  
1.  <span data-ttu-id="6a7eb-119">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="6a7eb-119">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="6a7eb-120">Dans la racine de la Console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez **groupe BizTalk**, puis cliquez sur **Parties**.</span><span class="sxs-lookup"><span data-stu-id="6a7eb-120">In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and click **Parties**.</span></span>  
  
3.  <span data-ttu-id="6a7eb-121">Cliquez avec le bouton droit sur le tiers approprié.</span><span class="sxs-lookup"><span data-stu-id="6a7eb-121">Right-click the correct party.</span></span>  
  
4.  <span data-ttu-id="6a7eb-122">Cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="6a7eb-122">Click **Properties**.</span></span>  
  
5.  <span data-ttu-id="6a7eb-123">Dans le [*nom du tiers*] **propriétés de tiers** boîte de dialogue, dans le volet gauche, cliquez sur **Ports d’envoi**.</span><span class="sxs-lookup"><span data-stu-id="6a7eb-123">In the [*party name*] **Party Properties** dialog box, in the left pane, click **Send Ports**.</span></span>  
  
6.  <span data-ttu-id="6a7eb-124">Entrez le nom de port d’envoi dans le **Ports d’envoi** liste.</span><span class="sxs-lookup"><span data-stu-id="6a7eb-124">Enter the Send port name in the **Send Ports** list.</span></span>  
  
7.  <span data-ttu-id="6a7eb-125">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="6a7eb-125">Click **OK**.</span></span>