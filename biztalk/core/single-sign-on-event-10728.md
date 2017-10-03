---
title: "Single Sign-On : Événement 10728 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f579189c-c9a5-4d2c-a3d5-f0ba03c5a3ef
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5052d03713808754abf04e8c2ba1590800e6cf9d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10728"></a><span data-ttu-id="da748-102">Single Sign-On : Événement 10728</span><span class="sxs-lookup"><span data-stu-id="da748-102">Single Sign-On: Event 10728</span></span>
## <a name="details"></a><span data-ttu-id="da748-103">Détails</span><span class="sxs-lookup"><span data-stu-id="da748-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="da748-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="da748-104">Product Name</span></span>|<span data-ttu-id="da748-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="da748-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="da748-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="da748-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="da748-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="da748-107">Event ID</span></span>|<span data-ttu-id="da748-108">10728</span><span class="sxs-lookup"><span data-stu-id="da748-108">10728</span></span>|  
|<span data-ttu-id="da748-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="da748-109">Event Source</span></span>|<span data-ttu-id="da748-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="da748-110">ENTSSO</span></span>|  
|<span data-ttu-id="da748-111">Composant</span><span class="sxs-lookup"><span data-stu-id="da748-111">Component</span></span>|<span data-ttu-id="da748-112">N\A</span><span class="sxs-lookup"><span data-stu-id="da748-112">N\A</span></span>|  
|<span data-ttu-id="da748-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="da748-113">Symbolic Name</span></span>|<span data-ttu-id="da748-114">SSO_ERROR_VERSION</span><span class="sxs-lookup"><span data-stu-id="da748-114">SSO_ERROR_VERSION</span></span>|  
|<span data-ttu-id="da748-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="da748-115">Message Text</span></span>|<span data-ttu-id="da748-116">Cette version du serveur SSO n'est pas compatible avec la base de données SSO.</span><span class="sxs-lookup"><span data-stu-id="da748-116">This version of the SSO server is not compatible with the SSO database.</span></span> <span data-ttu-id="da748-117">Mettez à niveau votre serveur de secret principal.%r</span><span class="sxs-lookup"><span data-stu-id="da748-117">Please upgrade your master secret server.%r</span></span><br /><br /> <span data-ttu-id="da748-118">Nom du serveur SQL : %1 %r</span><span class="sxs-lookup"><span data-stu-id="da748-118">SQL Server Name: %1%r</span></span><br /><br /> <span data-ttu-id="da748-119">Nom de base de données SSO : %2 %r</span><span class="sxs-lookup"><span data-stu-id="da748-119">SSO Database Name: %2%r</span></span><br /><br /> <span data-ttu-id="da748-120">Version de base de données SSO : %3 %r</span><span class="sxs-lookup"><span data-stu-id="da748-120">SSO Database Version: %3%r</span></span><br /><br /> <span data-ttu-id="da748-121">Version requise : %4</span><span class="sxs-lookup"><span data-stu-id="da748-121">Required Version: %4</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="da748-122">Explication</span><span class="sxs-lookup"><span data-stu-id="da748-122">Explanation</span></span>  
 <span data-ttu-id="da748-123">Cette erreur indique que la version du serveur SSO est plus récente que celle (créée à l'origine) de la base de données SSO.</span><span class="sxs-lookup"><span data-stu-id="da748-123">This Error event indicates that the SSO server version is more recent than (the version that originally created) the SSO database.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="da748-124">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="da748-124">User Action</span></span>  
 <span data-ttu-id="da748-125">Pour résoudre cette erreur, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="da748-125">To resolve this error, do the following:</span></span>  
  
-   <span data-ttu-id="da748-126">Mettez à niveau le serveur de secret principal SSO de façon à correspondre à la version actuelle de ce serveur SSO.</span><span class="sxs-lookup"><span data-stu-id="da748-126">Upgrade the SSO master secret server to match the current version of this SSO server.</span></span> <span data-ttu-id="da748-127">Ainsi, la base de données SSO sera mise à niveau vers la version actuelle.</span><span class="sxs-lookup"><span data-stu-id="da748-127">This will upgrade the SSO database to the current version.</span></span>  
  
 <span data-ttu-id="da748-128">Pour plus d'informations, consultez les ressources ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="da748-128">For more information, see the following resources:</span></span>  
  
-   [<span data-ttu-id="da748-129">Gestion du Secret</span><span class="sxs-lookup"><span data-stu-id="da748-129">Managing the Master Secret</span></span>](../core/managing-the-master-secret.md)