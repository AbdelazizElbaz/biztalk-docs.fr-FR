---
title: "Modèle XML sortant non valide | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0f29bb60-8c04-4921-84bf-c629540a1c83
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f58d230b481e611879637ff1b6ae08c2eed0313f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="invalid-outbound-xml-template"></a><span data-ttu-id="90659-102">Modèle XML sortant non valide</span><span class="sxs-lookup"><span data-stu-id="90659-102">Invalid outbound XML template</span></span>
## <a name="details"></a><span data-ttu-id="90659-103">Détails</span><span class="sxs-lookup"><span data-stu-id="90659-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="90659-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="90659-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="90659-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="90659-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="90659-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="90659-106">Event ID</span></span>|<span data-ttu-id="90659-107">0</span><span class="sxs-lookup"><span data-stu-id="90659-107">0</span></span>|  
|<span data-ttu-id="90659-108">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="90659-108">Event Source</span></span>|<span data-ttu-id="90659-109">0</span><span class="sxs-lookup"><span data-stu-id="90659-109">0</span></span>|  
|<span data-ttu-id="90659-110">Composant</span><span class="sxs-lookup"><span data-stu-id="90659-110">Component</span></span>|<span data-ttu-id="90659-111">0</span><span class="sxs-lookup"><span data-stu-id="90659-111">0</span></span>|  
|<span data-ttu-id="90659-112">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="90659-112">Symbolic Name</span></span>|<span data-ttu-id="90659-113">0</span><span class="sxs-lookup"><span data-stu-id="90659-113">0</span></span>|  
|<span data-ttu-id="90659-114">Texte du message</span><span class="sxs-lookup"><span data-stu-id="90659-114">Message Text</span></span>|<span data-ttu-id="90659-115">Modèle XML sortant non valide</span><span class="sxs-lookup"><span data-stu-id="90659-115">Invalid outbound XML template</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="90659-116">Explication</span><span class="sxs-lookup"><span data-stu-id="90659-116">Explanation</span></span>  
 <span data-ttu-id="90659-117">Plusieurs raisons peuvent expliquer cette erreur.</span><span class="sxs-lookup"><span data-stu-id="90659-117">There could be multiple reasons.</span></span> <span data-ttu-id="90659-118">Le code XML du modèle de corps du message WCF sortant n'est peut-être pas valide.</span><span class="sxs-lookup"><span data-stu-id="90659-118">The outbound WCF message body template may not be valid XML.</span></span> <span data-ttu-id="90659-119">Il peut contenir des caractères non valides par rapport au codage donné.</span><span class="sxs-lookup"><span data-stu-id="90659-119">It may contain invalid characters in the given encoding.</span></span> <span data-ttu-id="90659-120">L'élément racine est peut-être manquant.</span><span class="sxs-lookup"><span data-stu-id="90659-120">The root element may be missing.</span></span> <span data-ttu-id="90659-121">Les données au niveau racine sont peut-être non valides.</span><span class="sxs-lookup"><span data-stu-id="90659-121">The data at the root level may be invalid.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="90659-122">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="90659-122">User Action</span></span>  
 <span data-ttu-id="90659-123">Vérifiez que le code XML de l'expression de modèle est valide,</span><span class="sxs-lookup"><span data-stu-id="90659-123">Ensure that template expression has valid XML code.</span></span> <span data-ttu-id="90659-124">qu'il ne contient aucun caractère non valide et qu'il n'inclut qu'un seul élément racine.</span><span class="sxs-lookup"><span data-stu-id="90659-124">Ensure that It doesn’t contain any invalid characters and that there is only one root element.</span></span>  
  
1.  <span data-ttu-id="90659-125">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="90659-125">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="90659-126">Dans la racine de la Console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez **groupe BizTalk**, développez **Applications**.</span><span class="sxs-lookup"><span data-stu-id="90659-126">In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand  **Applications**.</span></span>  
  
3.  <span data-ttu-id="90659-127">Recherchez votre application, puis recherchez votre transport.</span><span class="sxs-lookup"><span data-stu-id="90659-127">Locate your application and then locate your transport.</span></span>  
  
4.  <span data-ttu-id="90659-128">Cliquez avec le bouton droit sur le nom du transport.</span><span class="sxs-lookup"><span data-stu-id="90659-128">Right-click the transport name.</span></span>  
  
5.  <span data-ttu-id="90659-129">Cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="90659-129">Click **Properties**.</span></span>  
  
6.  <span data-ttu-id="90659-130">Dans le port **Type** , sélectionnez le port approprié.</span><span class="sxs-lookup"><span data-stu-id="90659-130">In the port **Type** list, select the correct port.</span></span>  
  
7.  <span data-ttu-id="90659-131">Cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="90659-131">Click **Configure**.</span></span>  
  
8.  <span data-ttu-id="90659-132">Dans le **WCF [***type de transport***] propriétés du Transport** boîte de dialogue, cliquez sur le **Messages** onglet.</span><span class="sxs-lookup"><span data-stu-id="90659-132">In the **WCF [***transport type***] Transport Properties** dialog box, click the **Messages** tab.</span></span>  
  
9. <span data-ttu-id="90659-133">Dans le **le corps du message WCF sortant** section, sélectionnez **modèle--contenu spécifié par le modèle**.</span><span class="sxs-lookup"><span data-stu-id="90659-133">In the **Outbound WCF message body** section, select **Template--content specified by template**.</span></span>  
  
10. <span data-ttu-id="90659-134">Dans le **XML** texte zone, assurez-vous que le code XML est valide.</span><span class="sxs-lookup"><span data-stu-id="90659-134">In the **XML** text box, ensure that the XML code is valid.</span></span>  
  
 <span data-ttu-id="90659-135">Pour plus d'informations sur les modèles, consultez les ressources suivantes dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="90659-135">For additional information on templates, see the following resources in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="90659-136">En spécifiant le corps du Message pour les adaptateurs WCF</span><span class="sxs-lookup"><span data-stu-id="90659-136">Specifying the Message Body for the WCF Adapters</span></span>](../core/specifying-the-message-body-for-the-wcf-adapters.md)