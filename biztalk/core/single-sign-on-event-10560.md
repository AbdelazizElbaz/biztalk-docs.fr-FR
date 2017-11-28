---
title: "Single Sign-On : Événement 10560 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8677a807-2973-4753-8816-c93c45697d92
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5d630dccdd21aaade843d4aa8fd7026d05fd71da
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10560"></a><span data-ttu-id="61263-102">Single Sign-On : Événement 10560</span><span class="sxs-lookup"><span data-stu-id="61263-102">Single Sign-On: Event 10560</span></span>
## <a name="details"></a><span data-ttu-id="61263-103">Détails</span><span class="sxs-lookup"><span data-stu-id="61263-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="61263-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="61263-104">Product Name</span></span>|<span data-ttu-id="61263-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="61263-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="61263-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="61263-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="61263-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="61263-107">Event ID</span></span>|<span data-ttu-id="61263-108">10560</span><span class="sxs-lookup"><span data-stu-id="61263-108">10560</span></span>|  
|<span data-ttu-id="61263-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="61263-109">Event Source</span></span>|<span data-ttu-id="61263-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="61263-110">ENTSSO</span></span>|  
|<span data-ttu-id="61263-111">Composant</span><span class="sxs-lookup"><span data-stu-id="61263-111">Component</span></span>|<span data-ttu-id="61263-112">Néant</span><span class="sxs-lookup"><span data-stu-id="61263-112">N/A</span></span>|  
|<span data-ttu-id="61263-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="61263-113">Symbolic Name</span></span>|<span data-ttu-id="61263-114">SSO_ERROR_BACKUP_SECRET_FAILED</span><span class="sxs-lookup"><span data-stu-id="61263-114">SSO_ERROR_BACKUP_SECRET_FAILED</span></span>|  
|<span data-ttu-id="61263-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="61263-115">Message Text</span></span>|<span data-ttu-id="61263-116">Échec lors de la sauvegarde des secrets principaux.%r</span><span class="sxs-lookup"><span data-stu-id="61263-116">Failed to back up the master secrets.%r</span></span><br /><br /> <span data-ttu-id="61263-117">Nom du fichier : %1 %r</span><span class="sxs-lookup"><span data-stu-id="61263-117">File Name: %1%r</span></span><br /><br /> <span data-ttu-id="61263-118">MSID actuel : %2 %r</span><span class="sxs-lookup"><span data-stu-id="61263-118">Current MSID: %2%r</span></span><br /><br /> <span data-ttu-id="61263-119">MSID précédent : %3 %r</span><span class="sxs-lookup"><span data-stu-id="61263-119">Previous MSID: %3%r</span></span><br /><br /> <span data-ttu-id="61263-120">L’utilisateur client : %4 %r</span><span class="sxs-lookup"><span data-stu-id="61263-120">Client User: %4%r</span></span><br /><br /> <span data-ttu-id="61263-121">Code d’erreur : %5</span><span class="sxs-lookup"><span data-stu-id="61263-121">Error Code: %5</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="61263-122">Explication</span><span class="sxs-lookup"><span data-stu-id="61263-122">Explanation</span></span>  
 <span data-ttu-id="61263-123">Une tentative de sauvegarde du secret principal a échoué.</span><span class="sxs-lookup"><span data-stu-id="61263-123">An attempt to back up the master secret has failed.</span></span> <span data-ttu-id="61263-124">Il se peut que l'utilisateur à l'origine de la tentative de sauvegarde dispose d'autorisations, d'un chemin d'accès ou d'un répertoire incorrects.</span><span class="sxs-lookup"><span data-stu-id="61263-124">The user attempting this backup may have had the wrong permissions, path, or directory.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="61263-125">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="61263-125">User Action</span></span>  
 <span data-ttu-id="61263-126">Pour plus d’informations sur la sauvegarde du secret, consultez [gestion du Secret](../core/managing-the-master-secret.md).</span><span class="sxs-lookup"><span data-stu-id="61263-126">For information on backing up the master secret, see [Managing the Master Secret](../core/managing-the-master-secret.md).</span></span>