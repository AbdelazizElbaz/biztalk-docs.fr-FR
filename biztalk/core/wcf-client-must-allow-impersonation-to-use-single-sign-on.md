---
title: "Client WCF doit autoriser l’emprunt d’identité à utiliser l’authentification unique sur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b5b9f294-4d8a-4a12-91e8-8d325db7c420
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f5e43039a69d057b0d20767ff9061a8d6b4e4f70
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="wcf-client-must-allow-impersonation-to-use-single-sign-on"></a><span data-ttu-id="44004-102">Le client WCF doit autoriser l'emprunt d'identité pour utiliser l'authentification unique</span><span class="sxs-lookup"><span data-stu-id="44004-102">WCF client must allow impersonation to use Single Sign-On</span></span>
## <a name="details"></a><span data-ttu-id="44004-103">Détails</span><span class="sxs-lookup"><span data-stu-id="44004-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="44004-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="44004-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="44004-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="44004-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="44004-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="44004-106">Event ID</span></span>|<span data-ttu-id="44004-107">0</span><span class="sxs-lookup"><span data-stu-id="44004-107">0</span></span>|  
|<span data-ttu-id="44004-108">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="44004-108">Event Source</span></span>|<span data-ttu-id="44004-109">0</span><span class="sxs-lookup"><span data-stu-id="44004-109">0</span></span>|  
|<span data-ttu-id="44004-110">Composant</span><span class="sxs-lookup"><span data-stu-id="44004-110">Component</span></span>|<span data-ttu-id="44004-111">0</span><span class="sxs-lookup"><span data-stu-id="44004-111">0</span></span>|  
|<span data-ttu-id="44004-112">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="44004-112">Symbolic Name</span></span>|<span data-ttu-id="44004-113">0</span><span class="sxs-lookup"><span data-stu-id="44004-113">0</span></span>|  
|<span data-ttu-id="44004-114">Texte du message</span><span class="sxs-lookup"><span data-stu-id="44004-114">Message Text</span></span>|<span data-ttu-id="44004-115">Le client WCF doit autoriser l'emprunt d'identité pour utiliser l'authentification unique.</span><span class="sxs-lookup"><span data-stu-id="44004-115">The WCF client must allow impersonation to use Single Sign-On</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="44004-116">Explication</span><span class="sxs-lookup"><span data-stu-id="44004-116">Explanation</span></span>  
 <span data-ttu-id="44004-117">Bien que l'authentification unique soit activée dans l'emplacement de réception, le client WCF n'autorise pas l'emprunt d'identité.</span><span class="sxs-lookup"><span data-stu-id="44004-117">Single Sign-On (SSO) is enabled in the receive location but the WCF client does not allow impersonation.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="44004-118">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="44004-118">User Action</span></span>  
 <span data-ttu-id="44004-119">Vérifiez que le client WCF appelant le service autorise l'emprunt d'identité.</span><span class="sxs-lookup"><span data-stu-id="44004-119">Ensure that the WCF client invoking the service allows impersonation.</span></span>  
  
1.  <span data-ttu-id="44004-120">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="44004-120">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="44004-121">Dans la racine de la Console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez **groupe BizTalk**, développez **Applications**.</span><span class="sxs-lookup"><span data-stu-id="44004-121">In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand  **Applications**.</span></span>  
  
3.  <span data-ttu-id="44004-122">Recherchez votre application, puis recherchez votre transport.</span><span class="sxs-lookup"><span data-stu-id="44004-122">Locate your application and then locate your transport.</span></span>  
  
4.  <span data-ttu-id="44004-123">Cliquez avec le bouton droit sur le nom du transport.</span><span class="sxs-lookup"><span data-stu-id="44004-123">Right-click the transport name.</span></span>  
  
5.  <span data-ttu-id="44004-124">Cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="44004-124">Click **Properties**.</span></span>  
  
6.  <span data-ttu-id="44004-125">Dans le port **Type** liste, sélectionnez **WCF-Custom** (ou **WCF-CustomIsolate**).</span><span class="sxs-lookup"><span data-stu-id="44004-125">In the port **Type** list, select **WCF-Custom** (or **WCF-CustomIsolate**).</span></span>  
  
7.  <span data-ttu-id="44004-126">Cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="44004-126">Click **Configure**.</span></span>  
  
8.  <span data-ttu-id="44004-127">Dans le **WCF [***type de transport***] propriétés du Transport** boîte de dialogue, cliquez sur le **comportement** onglet.</span><span class="sxs-lookup"><span data-stu-id="44004-127">In the **WCF [***transport type***] Transport Properties** dialog box, click the **Behavior** tab.</span></span>  
  
9. <span data-ttu-id="44004-128">Dans le **comportement** , cliquez sur **ServiceAuthorization**.</span><span class="sxs-lookup"><span data-stu-id="44004-128">In the **Behavior** section, click **ServiceAuthorization**.</span></span> <span data-ttu-id="44004-129">Dans le **Configuration** section, la propriété **ImpersonateCallerForAllOperations** doit être défini sur **True**.</span><span class="sxs-lookup"><span data-stu-id="44004-129">In the **Configuration** section, the property **ImpersonateCallerForAllOperations** should be set to **True**.</span></span>  
  
10. <span data-ttu-id="44004-130">Dans le **WCF [***type de transport***] propriétés du Transport** boîte de dialogue, cliquez sur le **autres** onglet.</span><span class="sxs-lookup"><span data-stu-id="44004-130">In the **WCF [***transport type***] Transport Properties** dialog box, click the **Other** tab.</span></span>  
  
11. <span data-ttu-id="44004-131">Dans les sections informations d’identification, sélectionnez l’option **utilisez Single Sign-On**.</span><span class="sxs-lookup"><span data-stu-id="44004-131">In the Credentials sections, select the option **Use Single Sign-On**.</span></span>