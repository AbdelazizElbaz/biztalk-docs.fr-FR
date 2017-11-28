---
title: "Erreur structurelle s’est produite pendant la sérialisation d’un message XML d’échange | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 97939bfd-d1ee-455a-9952-4f25db020e7c
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 44b56cce9fdd3704f7e6ddc2ba5b5bebb62d36e0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="structural-error-encountered-during-serialization-of-an-interchange-xml-message"></a><span data-ttu-id="57dda-102">Erreur structurelle s’est produite pendant la sérialisation d’un message XML d’échange</span><span class="sxs-lookup"><span data-stu-id="57dda-102">Structural error encountered during serialization of an interchange XML message</span></span>
## <a name="details"></a><span data-ttu-id="57dda-103">Détails</span><span class="sxs-lookup"><span data-stu-id="57dda-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="57dda-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="57dda-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="57dda-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="57dda-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="57dda-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="57dda-106">Event ID</span></span>|-|  
|<span data-ttu-id="57dda-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="57dda-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="57dda-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="57dda-108"> EDI</span></span>|  
|<span data-ttu-id="57dda-109">Composant</span><span class="sxs-lookup"><span data-stu-id="57dda-109">Component</span></span>|<span data-ttu-id="57dda-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="57dda-110">EDI Engine</span></span>|  
|<span data-ttu-id="57dda-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="57dda-111">Symbolic Name</span></span>|<span data-ttu-id="57dda-112">InvalidXmlNodeFound</span><span class="sxs-lookup"><span data-stu-id="57dda-112">InvalidXmlNodeFound</span></span>|  
|<span data-ttu-id="57dda-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="57dda-113">Message Text</span></span>|<span data-ttu-id="57dda-114">Erreur structurelle rencontrée durant la sérialisation d'un message Xml d'échange</span><span class="sxs-lookup"><span data-stu-id="57dda-114">Structural error encountered during serialization of an Interchange Xml message</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="57dda-115">Explication</span><span class="sxs-lookup"><span data-stu-id="57dda-115">Explanation</span></span>  
 <span data-ttu-id="57dda-116">Cette erreur indique qu'une erreur structurelle a été rencontrée durant la sérialisation d'un message XML d'échange.</span><span class="sxs-lookup"><span data-stu-id="57dda-116">This error indicates that a structural error was encountered during serialization of an interchange XML message.</span></span> <span data-ttu-id="57dda-117">Alors que BTS recherchait un élément XML StartElement ou EndElement, un type de nœud XML différent a été rencontré.</span><span class="sxs-lookup"><span data-stu-id="57dda-117">BTS was looking for an XML StartElement or EndElement but instead a different XML node type was encountered.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="57dda-118">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="57dda-118">User Action</span></span>  
 <span data-ttu-id="57dda-119">Pour résoudre cette erreur, assurez-vous que la structure du message est correcte, puis réessayez :</span><span class="sxs-lookup"><span data-stu-id="57dda-119">To resolve this error, make sure the message structure is correct, and try again:</span></span>  
  
1.  <span data-ttu-id="57dda-120">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="57dda-120">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="57dda-121">Dans la racine de la Console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], puis cliquez sur **groupe BizTalk**.</span><span class="sxs-lookup"><span data-stu-id="57dda-121">In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], and click **BizTalk Group**.</span></span>  
  
3.  <span data-ttu-id="57dda-122">Dans le volet droit, cliquez sur le **Hub du groupe** onglet.</span><span class="sxs-lookup"><span data-stu-id="57dda-122">In the right pane, click the **Group Hub** tab.</span></span>  
  
4.  <span data-ttu-id="57dda-123">Cliquez sur **instances de Service suspendues**.</span><span class="sxs-lookup"><span data-stu-id="57dda-123">Click **Suspended Service instances**.</span></span>  
  
5.  <span data-ttu-id="57dda-124">Double-cliquez sur le message.</span><span class="sxs-lookup"><span data-stu-id="57dda-124">Double-click the message.</span></span>  
  
6.  <span data-ttu-id="57dda-125">Dans le **détails du Service** fenêtre, cliquez sur le **Messages** onglet.</span><span class="sxs-lookup"><span data-stu-id="57dda-125">In the **Service Details** window, click the **Messages** tab.</span></span>  
  
7.  <span data-ttu-id="57dda-126">Double-cliquez de nouveau sur le message.</span><span class="sxs-lookup"><span data-stu-id="57dda-126">Double-click the message again.</span></span>  
  
8.  <span data-ttu-id="57dda-127">Dans le volet gauche, cliquez sur **parties de messages / corps**.</span><span class="sxs-lookup"><span data-stu-id="57dda-127">In the left pane, click **Message Parts / Body**.</span></span>  
  
9. <span data-ttu-id="57dda-128">Déterminez si la structure du message est correcte.</span><span class="sxs-lookup"><span data-stu-id="57dda-128">Determine if the message structure is correct.</span></span>