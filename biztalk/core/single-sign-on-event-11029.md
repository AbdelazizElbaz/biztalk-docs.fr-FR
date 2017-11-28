---
title: "Single Sign-On : Événement 11029 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dd7cb5b0-532c-4f50-849d-4d1644026463
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e5f24cee6fcbe7db5ce0b4f31d458a5a29118c3c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-11029"></a><span data-ttu-id="e741e-102">Single Sign-On : Événement 11029</span><span class="sxs-lookup"><span data-stu-id="e741e-102">Single Sign-On: Event 11029</span></span>
## <a name="details"></a><span data-ttu-id="e741e-103">Détails</span><span class="sxs-lookup"><span data-stu-id="e741e-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e741e-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="e741e-104">Product Name</span></span>|<span data-ttu-id="e741e-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="e741e-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="e741e-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="e741e-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="e741e-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="e741e-107">Event ID</span></span>|<span data-ttu-id="e741e-108">11029</span><span class="sxs-lookup"><span data-stu-id="e741e-108">11029</span></span>|  
|<span data-ttu-id="e741e-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="e741e-109">Event Source</span></span>|<span data-ttu-id="e741e-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="e741e-110">ENTSSO</span></span>|  
|<span data-ttu-id="e741e-111">Composant</span><span class="sxs-lookup"><span data-stu-id="e741e-111">Component</span></span>|<span data-ttu-id="e741e-112">Néant</span><span class="sxs-lookup"><span data-stu-id="e741e-112">N/A</span></span>|  
|<span data-ttu-id="e741e-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="e741e-113">Symbolic Name</span></span>|<span data-ttu-id="e741e-114">SSO_INFO_CASE_SENSITIVE</span><span class="sxs-lookup"><span data-stu-id="e741e-114">SSO_INFO_CASE_SENSITIVE</span></span>|  
|<span data-ttu-id="e741e-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="e741e-115">Message Text</span></span>|<span data-ttu-id="e741e-116">La base de données SSO respecte la casse.</span><span class="sxs-lookup"><span data-stu-id="e741e-116">The SSO database is case sensitive.</span></span> <span data-ttu-id="e741e-117">Le serveur SSO s'exécutera en respectant la casse.</span><span class="sxs-lookup"><span data-stu-id="e741e-117">The SSO server will run in case sensitive mode.</span></span> <span data-ttu-id="e741e-118">Pour plus d'informations, reportez-vous à la documentation.%r</span><span class="sxs-lookup"><span data-stu-id="e741e-118">See documentation for details.%r</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="e741e-119">Explication</span><span class="sxs-lookup"><span data-stu-id="e741e-119">Explanation</span></span>  
 <span data-ttu-id="e741e-120">Par défaut, le serveur SSO ne respecte pas la casse.</span><span class="sxs-lookup"><span data-stu-id="e741e-120">By default the SSO server is not case-sensitive.</span></span> <span data-ttu-id="e741e-121">Toutefois, la base de données SSO du serveur SQL Server a été configurée de façon à respecter la casse. Par conséquent, le serveur SSO respectera également la casse.</span><span class="sxs-lookup"><span data-stu-id="e741e-121">However, the SQL Server SSO database has been configured to be case-sensitive, so the SSO Server will also run in case sensitive mode.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="e741e-122">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="e741e-122">User Action</span></span>  
 <span data-ttu-id="e741e-123">Ayez cela à l'esprit lorsque vous spécifiez des noms d'applications ainsi que des noms de comptes externes, car ils respectent désormais la casse.</span><span class="sxs-lookup"><span data-stu-id="e741e-123">Be aware of this when specifying application names and external account names as they are now case-sensitive.</span></span> <span data-ttu-id="e741e-124">Pour plus d’informations, consultez [serveur SSO](../core/sso-server.md).</span><span class="sxs-lookup"><span data-stu-id="e741e-124">For more information, see [SSO Server](../core/sso-server.md).</span></span>