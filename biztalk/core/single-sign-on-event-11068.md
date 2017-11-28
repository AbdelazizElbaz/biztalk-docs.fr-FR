---
title: "Single Sign-On : Événement 11068 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f09a1191-ae67-4156-a8a5-d24e4439fc68
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: be824a9205d81aaaeb9fd87129133b94b4f2e379
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-11068"></a><span data-ttu-id="3c651-102">Single Sign-On : Événement 11068</span><span class="sxs-lookup"><span data-stu-id="3c651-102">Single Sign-On: Event 11068</span></span>
## <a name="details"></a><span data-ttu-id="3c651-103">Détails</span><span class="sxs-lookup"><span data-stu-id="3c651-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3c651-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="3c651-104">Product Name</span></span>|<span data-ttu-id="3c651-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="3c651-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="3c651-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="3c651-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="3c651-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="3c651-107">Event ID</span></span>|<span data-ttu-id="3c651-108">11068</span><span class="sxs-lookup"><span data-stu-id="3c651-108">11068</span></span>|  
|<span data-ttu-id="3c651-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="3c651-109">Event Source</span></span>|<span data-ttu-id="3c651-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="3c651-110">ENTSSO</span></span>|  
|<span data-ttu-id="3c651-111">Composant</span><span class="sxs-lookup"><span data-stu-id="3c651-111">Component</span></span>|<span data-ttu-id="3c651-112">Néant</span><span class="sxs-lookup"><span data-stu-id="3c651-112">N/A</span></span>|  
|<span data-ttu-id="3c651-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="3c651-113">Symbolic Name</span></span>|<span data-ttu-id="3c651-114">SSO_ERROR_LOOKUP_CALLBACK_ACCESS_DENIED_NO_REMOTE</span><span class="sxs-lookup"><span data-stu-id="3c651-114">SSO_ERROR_LOOKUP_CALLBACK_ACCESS_DENIED_NO_REMOTE</span></span>|  
|<span data-ttu-id="3c651-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="3c651-115">Message Text</span></span>|<span data-ttu-id="3c651-116">Accès au serveur de recherche refusé.</span><span class="sxs-lookup"><span data-stu-id="3c651-116">Lookup server access denied.</span></span> <span data-ttu-id="3c651-117">Ce serveur SSO n'est actuellement pas configuré pour autoriser la recherche distante.</span><span class="sxs-lookup"><span data-stu-id="3c651-117">This SSO server is currently not configured to allow remote lookup.</span></span> <span data-ttu-id="3c651-118">Utilisez « ssoconfig -remoteLookup yes » ou le composant logiciel enfichable d'administration SSO.%r</span><span class="sxs-lookup"><span data-stu-id="3c651-118">Use 'ssoconfig -remoteLookup yes' or the SSO Administration MMC.%r</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="3c651-119">Explication</span><span class="sxs-lookup"><span data-stu-id="3c651-119">Explanation</span></span>  
 <span data-ttu-id="3c651-120">L'accès au serveur de recherche a été refusé car le serveur ENTSSO n'est pas configuré pour autoriser la recherche distante.</span><span class="sxs-lookup"><span data-stu-id="3c651-120">Lookup server access has been denied because the ENTSSO server is not configured to allow remote lookup.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="3c651-121">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="3c651-121">User Action</span></span>  
 <span data-ttu-id="3c651-122">Pour autoriser la recherche à distance, dans le **le composant logiciel enfichable serveurs**, **avancé** onglet, sélectionnez **autoriser la recherche distante**.</span><span class="sxs-lookup"><span data-stu-id="3c651-122">To allow remote lookup, in the **Servers Snap-In**, **Advanced** tab, select **Allow Remote Lookup**.</span></span>  
  
 <span data-ttu-id="3c651-123">Pour plus d’informations, consultez [comment utiliser le composant logiciel enfichable serveurs](../core/how-to-use-the-servers-snap-in.md).</span><span class="sxs-lookup"><span data-stu-id="3c651-123">For more information, see [How to Use the Servers Snap-in](../core/how-to-use-the-servers-snap-in.md).</span></span>