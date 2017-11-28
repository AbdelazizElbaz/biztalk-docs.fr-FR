---
title: "Single Sign-On : Événement 10550 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 73d63bc5-1e60-426c-a0d6-55c51dbb8d76
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9772885746f2c0519cba84db9ad1bee612607117
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10550"></a><span data-ttu-id="c9f66-102">Single Sign-On : Événement 10550</span><span class="sxs-lookup"><span data-stu-id="c9f66-102">Single Sign-On: Event 10550</span></span>
## <a name="details"></a><span data-ttu-id="c9f66-103">Détails</span><span class="sxs-lookup"><span data-stu-id="c9f66-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c9f66-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="c9f66-104">Product Name</span></span>|<span data-ttu-id="c9f66-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="c9f66-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="c9f66-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="c9f66-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="c9f66-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="c9f66-107">Event ID</span></span>|<span data-ttu-id="c9f66-108">10550</span><span class="sxs-lookup"><span data-stu-id="c9f66-108">10550</span></span>|  
|<span data-ttu-id="c9f66-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="c9f66-109">Event Source</span></span>|<span data-ttu-id="c9f66-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="c9f66-110">ENTSSO</span></span>|  
|<span data-ttu-id="c9f66-111">Composant</span><span class="sxs-lookup"><span data-stu-id="c9f66-111">Component</span></span>|<span data-ttu-id="c9f66-112">Néant</span><span class="sxs-lookup"><span data-stu-id="c9f66-112">N/A</span></span>|  
|<span data-ttu-id="c9f66-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="c9f66-113">Symbolic Name</span></span>|<span data-ttu-id="c9f66-114">SSO_ERROR_SERVICE_NOT_SSO_ADMIN</span><span class="sxs-lookup"><span data-stu-id="c9f66-114">SSO_ERROR_SERVICE_NOT_SSO_ADMIN</span></span>|  
|<span data-ttu-id="c9f66-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="c9f66-115">Message Text</span></span>|<span data-ttu-id="c9f66-116">Le service SSO n'a pas pu démarrer car le compte de service sous lequel il est exécuté n'est pas membre du compte Administrateurs de l'authentification unique.%r</span><span class="sxs-lookup"><span data-stu-id="c9f66-116">The SSO service could not start because the service account it is running under is not a member of the SSO Administrators account.%r</span></span><br /><br /> <span data-ttu-id="c9f66-117">Les administrateurs de l’authentification unique : %1 %r</span><span class="sxs-lookup"><span data-stu-id="c9f66-117">SSO Administrators: %1%r</span></span><br /><br /> <span data-ttu-id="c9f66-118">Compte du Service SSO : %2</span><span class="sxs-lookup"><span data-stu-id="c9f66-118">SSO Service Account: %2</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="c9f66-119">Explication</span><span class="sxs-lookup"><span data-stu-id="c9f66-119">Explanation</span></span>  
 <span data-ttu-id="c9f66-120">Le service SSSO doit être exécuté sous un compte de service membre du compte Administrateurs de l'authentification unique.</span><span class="sxs-lookup"><span data-stu-id="c9f66-120">The SSO service must be running under a service account that is a member of the SSO Administrators account.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="c9f66-121">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="c9f66-121">User Action</span></span>  
 <span data-ttu-id="c9f66-122">Pour plus d’informations, consultez [comment spécifier les administrateurs de l’authentification unique et Affiliate Administrators Accounts](../core/how-to-specify-sso-administrators-and-affiliate-administrators-accounts.md).</span><span class="sxs-lookup"><span data-stu-id="c9f66-122">For more information, see [How to Specify SSO Administrators and Affiliate Administrators Accounts](../core/how-to-specify-sso-administrators-and-affiliate-administrators-accounts.md).</span></span>