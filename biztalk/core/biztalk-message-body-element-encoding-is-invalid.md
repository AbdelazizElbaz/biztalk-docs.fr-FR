---
title: "Codage d’élément de corps du message BizTalk n’est pas valide | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b407e5c3-4655-4b2f-8ecc-30eb080ec47c
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fbf134b390af1904d74f1652aac00f6ea4b33ad2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="biztalk-message-body-element-encoding-is-invalid"></a><span data-ttu-id="b2335-102">Le codage de l'élément corps de message BizTalk est non valide</span><span class="sxs-lookup"><span data-stu-id="b2335-102">BizTalk message body element encoding is invalid</span></span>
## <a name="details"></a><span data-ttu-id="b2335-103">Détails</span><span class="sxs-lookup"><span data-stu-id="b2335-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b2335-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="b2335-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="b2335-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="b2335-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="b2335-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="b2335-106">Event ID</span></span>|<span data-ttu-id="b2335-107">0</span><span class="sxs-lookup"><span data-stu-id="b2335-107">0</span></span>|  
|<span data-ttu-id="b2335-108">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="b2335-108">Event Source</span></span>|<span data-ttu-id="b2335-109">0</span><span class="sxs-lookup"><span data-stu-id="b2335-109">0</span></span>|  
|<span data-ttu-id="b2335-110">Composant</span><span class="sxs-lookup"><span data-stu-id="b2335-110">Component</span></span>|<span data-ttu-id="b2335-111">0</span><span class="sxs-lookup"><span data-stu-id="b2335-111">0</span></span>|  
|<span data-ttu-id="b2335-112">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="b2335-112">Symbolic Name</span></span>|<span data-ttu-id="b2335-113">0</span><span class="sxs-lookup"><span data-stu-id="b2335-113">0</span></span>|  
|<span data-ttu-id="b2335-114">Texte du message</span><span class="sxs-lookup"><span data-stu-id="b2335-114">Message Text</span></span>|<span data-ttu-id="b2335-115">Le codage de l'élément corps de message BizTalk " {0}" est non valide.</span><span class="sxs-lookup"><span data-stu-id="b2335-115">BizTalk message body element encoding "{0}" is invalid.</span></span> <span data-ttu-id="b2335-116">Codage attendu : « xml », « base64 », « hex » ou « chaîne »</span><span class="sxs-lookup"><span data-stu-id="b2335-116">Expected encoding: "xml", "base64", "hex", or "string"</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="b2335-117">Explication</span><span class="sxs-lookup"><span data-stu-id="b2335-117">Explanation</span></span>  
 <span data-ttu-id="b2335-118">Cette erreur indique l'utilisation de l'option de modèle de corps BizTalk pour les messages sortants. Toutefois, le type de codage spécifié pour le corps BizTalk est non valide.</span><span class="sxs-lookup"><span data-stu-id="b2335-118">This error indicates the use of the BizTalk body template option for the outgoing messages; however, the encoding type specified for the BizTalk body is invalid.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="b2335-119">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="b2335-119">User Action</span></span>  
 <span data-ttu-id="b2335-120">La procédure suivante permet de configurer le type de codage.</span><span class="sxs-lookup"><span data-stu-id="b2335-120">Use the following procedure to configure the encoding type.</span></span>  
  
#### <a name="to-configure-the-encoding-type"></a><span data-ttu-id="b2335-121">Pour configurer le type de codage</span><span class="sxs-lookup"><span data-stu-id="b2335-121">To configure the encoding type</span></span>  
  
1.  <span data-ttu-id="b2335-122">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="b2335-122">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="b2335-123">Dans la racine de la Console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez **groupe BizTalk**, développez **Applications**.</span><span class="sxs-lookup"><span data-stu-id="b2335-123">In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand  **Applications**.</span></span>  
  
3.  <span data-ttu-id="b2335-124">Recherchez votre application, puis recherchez votre transport.</span><span class="sxs-lookup"><span data-stu-id="b2335-124">Locate your application and then locate your transport.</span></span>  
  
4.  <span data-ttu-id="b2335-125">Cliquez avec le bouton droit sur le nom du transport.</span><span class="sxs-lookup"><span data-stu-id="b2335-125">Right-click the transport name.</span></span>  
  
5.  <span data-ttu-id="b2335-126">Cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="b2335-126">Click **Properties**.</span></span>  
  
6.  <span data-ttu-id="b2335-127">Dans le port **Type** , sélectionnez le port approprié.</span><span class="sxs-lookup"><span data-stu-id="b2335-127">In the port **Type** list, select the correct port.</span></span>  
  
7.  <span data-ttu-id="b2335-128">Cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="b2335-128">Click **Configure**.</span></span>  
  
8.  <span data-ttu-id="b2335-129">Dans le **WCF [***type de transport***] propriétés du Transport** boîte de dialogue, cliquez sur le **Messages** onglet.</span><span class="sxs-lookup"><span data-stu-id="b2335-129">In the **WCF [***transport type***] Transport Properties** dialog box, click the **Messages** tab.</span></span>  
  
9. <span data-ttu-id="b2335-130">Dans le **le corps du message WCF sortant** , cliquez sur le **modèle--contenu spécifié par le modèle** case d’option.</span><span class="sxs-lookup"><span data-stu-id="b2335-130">In the **Outbound WCF message body** section, click the **Template – Content specified by template** radio button.</span></span> <span data-ttu-id="b2335-131">Dans le **XML** zone de texte, le format du corps BizTalk doit être</span><span class="sxs-lookup"><span data-stu-id="b2335-131">In the **XML** text box, the format of the BizTalk body should be</span></span>   
    <span data-ttu-id="b2335-132">\<**BTS-msg-body xmlns = « http://www.microsoft.com/schemas/bts2007 » encoding = « [xml &#124; base64 &#124; hex &#124; chaîne] » /**> (valeurs valides, qui respectent la casse, pour le codage est xml &#124; base64 &#124; hex &#124; chaîne)</span><span class="sxs-lookup"><span data-stu-id="b2335-132">\<**bts-msg-body xmlns="http://www.microsoft.com/schemas/bts2007" encoding="[xml&#124;base64&#124;hex&#124;string]"/**>  (valid values, which are case-sensitive, for encoding are xml&#124;base64&#124;hex&#124;string)</span></span>