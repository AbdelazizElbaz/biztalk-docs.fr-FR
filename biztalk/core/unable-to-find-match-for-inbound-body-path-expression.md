---
title: "Impossible de trouver une correspondance pour l’expression de chemin de corps entrant | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c0382348-96c4-414c-9dda-a390d491dee8
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4f733099d35150c22e888f89e720d4039208ce24
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="unable-to-find-match-for-inbound-body-path-expression"></a><span data-ttu-id="e840f-102">Correspondance introuvable pour l'expression de chemin de corps entrant</span><span class="sxs-lookup"><span data-stu-id="e840f-102">Unable to find match for inbound body path expression</span></span>
## <a name="details"></a><span data-ttu-id="e840f-103">Détails</span><span class="sxs-lookup"><span data-stu-id="e840f-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e840f-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="e840f-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="e840f-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="e840f-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="e840f-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="e840f-106">Event ID</span></span>|<span data-ttu-id="e840f-107">0</span><span class="sxs-lookup"><span data-stu-id="e840f-107">0</span></span>|  
|<span data-ttu-id="e840f-108">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="e840f-108">Event Source</span></span>|<span data-ttu-id="e840f-109">0</span><span class="sxs-lookup"><span data-stu-id="e840f-109">0</span></span>|  
|<span data-ttu-id="e840f-110">Composant</span><span class="sxs-lookup"><span data-stu-id="e840f-110">Component</span></span>|<span data-ttu-id="e840f-111">0</span><span class="sxs-lookup"><span data-stu-id="e840f-111">0</span></span>|  
|<span data-ttu-id="e840f-112">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="e840f-112">Symbolic Name</span></span>|<span data-ttu-id="e840f-113">0</span><span class="sxs-lookup"><span data-stu-id="e840f-113">0</span></span>|  
|<span data-ttu-id="e840f-114">Texte du message</span><span class="sxs-lookup"><span data-stu-id="e840f-114">Message Text</span></span>|<span data-ttu-id="e840f-115">Correspondance introuvable pour l'expression de chemin de corps entrant « {0} » dans le message</span><span class="sxs-lookup"><span data-stu-id="e840f-115">Unable to find match for inbound body path expression "{0}" in message</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="e840f-116">Explication</span><span class="sxs-lookup"><span data-stu-id="e840f-116">Explanation</span></span>  
 <span data-ttu-id="e840f-117">L'expression de chemin de corps exécutée sur le message entrant n'a renvoyé aucune correspondance.</span><span class="sxs-lookup"><span data-stu-id="e840f-117">The body path expression executed on the incoming message did not return any match.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="e840f-118">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="e840f-118">User Action</span></span>  
 <span data-ttu-id="e840f-119">Vérifiez l'exactitude de l'expression de chemin de corps et des données du message entrant.</span><span class="sxs-lookup"><span data-stu-id="e840f-119">Make sure that body path expression is correct, and the incoming message has the correct data.</span></span>  
  
1.  <span data-ttu-id="e840f-120">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="e840f-120">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="e840f-121">Dans la racine de la Console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez **groupe BizTalk**, développez **Applications**.</span><span class="sxs-lookup"><span data-stu-id="e840f-121">In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand  **Applications**.</span></span>  
  
3.  <span data-ttu-id="e840f-122">Recherchez votre application, puis recherchez votre transport.</span><span class="sxs-lookup"><span data-stu-id="e840f-122">Locate your application and then locate your transport.</span></span>  
  
4.  <span data-ttu-id="e840f-123">Cliquez avec le bouton droit sur le nom du transport.</span><span class="sxs-lookup"><span data-stu-id="e840f-123">Right-click the transport name.</span></span>  
  
5.  <span data-ttu-id="e840f-124">Cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="e840f-124">Click **Properties**.</span></span>  
  
6.  <span data-ttu-id="e840f-125">Dans le port **Type** , sélectionnez le port approprié.</span><span class="sxs-lookup"><span data-stu-id="e840f-125">In the port **Type** list, select the correct port.</span></span>  
  
7.  <span data-ttu-id="e840f-126">Cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="e840f-126">Click **Configure**.</span></span>  
  
8.  <span data-ttu-id="e840f-127">WCF **[***type de transport***] propriétés du Transport** boîte de dialogue, cliquez sur le **Messages** onglet.</span><span class="sxs-lookup"><span data-stu-id="e840f-127">In the WCF **[***transport type***] Transport Properties** dialog box, click the **Messages** tab.</span></span>  
  
9. <span data-ttu-id="e840f-128">Dans le **le corps du message BizTalk entrant** section, vérifiez les informations de **expression de chemin de corps**.</span><span class="sxs-lookup"><span data-stu-id="e840f-128">In the **Inbound BizTalk message body** section, check the information for **Body path expression**.</span></span>