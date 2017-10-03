---
title: Mappages SSO | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- maps [SSO]
- maps [SSO], creating
- SSO, maps
ms.assetid: b44f7a0c-595c-49dc-9d75-2e76f29dca88
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 98b44a1a9e8be3b275a4dd328c70323d79eb8a54
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="sso-mappings"></a><span data-ttu-id="8e0d3-102">Mappages SSO</span><span class="sxs-lookup"><span data-stu-id="8e0d3-102">SSO Mappings</span></span>
<span data-ttu-id="8e0d3-103">Lorsqu'un administrateur de l'authentification unique de l'entreprise ou un administrateur d'applications associées à SSO définit une application associée, il peut la définir soit comme une application utilisant des mappages individuels, soit comme une application utilisant un mappage de groupe.</span><span class="sxs-lookup"><span data-stu-id="8e0d3-103">When an Enterprise Single Sign-On (SSO) administrator or an SSO affiliate administrator defines an affiliate application, the administrator can define it either as an application with individual mappings, or as an application with a group mapping.</span></span>  
  
## <a name="individual-mappings"></a><span data-ttu-id="8e0d3-104">Mappages individuels</span><span class="sxs-lookup"><span data-stu-id="8e0d3-104">Individual Mappings</span></span>  
 <span data-ttu-id="8e0d3-105">Les mappages individuels SSO permettent aux administrateurs et aux utilisateurs de créer un mappage un-à-un entre les utilisateurs Windows et leurs informations d'identification non-Windows correspondantes.</span><span class="sxs-lookup"><span data-stu-id="8e0d3-105">SSO individual mappings enable administrators and users to create a one-to-one mapping between Windows users and their corresponding non-Windows credentials.</span></span> <span data-ttu-id="8e0d3-106">Lors de l'utilisation de mappages individuels, les utilisateurs peuvent gérer leurs propres mappages.</span><span class="sxs-lookup"><span data-stu-id="8e0d3-106">When using individual mappings, users can manage their own mappings.</span></span> <span data-ttu-id="8e0d3-107">Le système SSO entretient la relation un-à-un pour le compte Windows et le compte non-Windows d'un utilisateur.</span><span class="sxs-lookup"><span data-stu-id="8e0d3-107">The SSO system maintains the one-to-one relation for the user's Windows account and the user's non-Windows account.</span></span>  
  
 <span data-ttu-id="8e0d3-108">Les utilisateurs finaux Windows peuvent créer et gérer leurs propres mappages pour les applications de type individuel.</span><span class="sxs-lookup"><span data-stu-id="8e0d3-108">Windows End-users can create and manage their own mappings for individual type applications.</span></span> <span data-ttu-id="8e0d3-109">La même application associée peut jouer le rôle d'une application SSO initiée par Windows et celui d'une application SSO initiée par l'hôte.</span><span class="sxs-lookup"><span data-stu-id="8e0d3-109">The same affiliate application can act as a Windows Initiated SSO and a Host Initiated SSO type application.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="8e0d3-110">Des mappages ne peuvent être créés que pour des comptes de domaine Windows.</span><span class="sxs-lookup"><span data-stu-id="8e0d3-110">Mappings can be created only for Windows domain accounts.</span></span> <span data-ttu-id="8e0d3-111">Les comptes locaux ne peuvent pas être mappés.</span><span class="sxs-lookup"><span data-stu-id="8e0d3-111">Local accounts cannot be mapped.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8e0d3-112">Lors de l'utilisation de mappages individuels, seuls les utilisateurs individuels peuvent obtenir les informations d'identification de leur compte individuel.</span><span class="sxs-lookup"><span data-stu-id="8e0d3-112">Only individual users can obtain the credentials to their individual accounts when using individual mappings.</span></span>  
  
## <a name="group-mapping"></a><span data-ttu-id="8e0d3-113">Mappage de groupe</span><span class="sxs-lookup"><span data-stu-id="8e0d3-113">Group Mapping</span></span>  
 <span data-ttu-id="8e0d3-114">Le mappage de groupe SSO consiste à associer un groupe Windows qui contient plusieurs utilisateurs à un compte unique dans l'application associée.</span><span class="sxs-lookup"><span data-stu-id="8e0d3-114">SSO group mapping consists of mapping a Windows group, which contains multiple Windows users, to a single account in the affiliate application.</span></span>  
  
 <span data-ttu-id="8e0d3-115">Vous pouvez aussi spécifier plusieurs comptes pour le rôle des utilisateurs d'applications à authentification unique.</span><span class="sxs-lookup"><span data-stu-id="8e0d3-115">You can also specify multiple accounts for the SSO Application Users role.</span></span> <span data-ttu-id="8e0d3-116">Chaque compte que vous spécifiez peut être associé à un compte externe.</span><span class="sxs-lookup"><span data-stu-id="8e0d3-116">Each account you specify can be associated with an external account.</span></span> <span data-ttu-id="8e0d3-117">Par exemple, vous pouvez mapper successivement un compte de groupe de domaine vers EXTERNALUSER1 et un compte de domaine individuel vers EXTERNALUSER2.</span><span class="sxs-lookup"><span data-stu-id="8e0d3-117">For example, you can map a domain group account to EXTERNALUSER1 and an individual domain account to EXTERNALUSER2.</span></span> <span data-ttu-id="8e0d3-118">Si un même utilisateur dispose de plusieurs mappages, le premier apparaissant dans l'ordre des utilisateurs d'applications associées à SSO est utilisé.</span><span class="sxs-lookup"><span data-stu-id="8e0d3-118">If the same user has more than one mapping, the first mapping in the order of SSO Application Users is used.</span></span>  
  
 <span data-ttu-id="8e0d3-119">Seul un administrateur d'applications, un administrateur d'applications associées à SSO ou un administrateur de l'authentification unique peut créer ou gérer un mappage de groupe.</span><span class="sxs-lookup"><span data-stu-id="8e0d3-119">Only an application administrator, SSO affiliate administrator, or SSO administrator can create or manage a group mapping.</span></span>  
  
 <span data-ttu-id="8e0d3-120">Vous ne pouvez pas indiquer la même application de groupe pour l'authentification unique initiée par Windows et pour l'authentification unique initiée par l'hôte.</span><span class="sxs-lookup"><span data-stu-id="8e0d3-120">You cannot specify the same group application for Windows initiated SSO and Host Initiated SSO.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="8e0d3-121">Des mappages ne peuvent être créés que pour des comptes de domaine Windows.</span><span class="sxs-lookup"><span data-stu-id="8e0d3-121">Mappings can be created only for Windows domain accounts.</span></span> <span data-ttu-id="8e0d3-122">Les comptes locaux ne peuvent pas être mappés.</span><span class="sxs-lookup"><span data-stu-id="8e0d3-122">Local accounts cannot be mapped.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="8e0d3-123">Lorsque vous utilisez des mappages de groupe, les membres du groupe peuvent obtenir les informations d'identification pour le mappage de groupe.</span><span class="sxs-lookup"><span data-stu-id="8e0d3-123">When you use group mappings, the members of the group can obtain the credential information for the group mapping.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e0d3-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8e0d3-124">See Also</span></span>  
 <span data-ttu-id="8e0d3-125">[Gestion des mappages utilisateur](../core/managing-user-mappings.md) </span><span class="sxs-lookup"><span data-stu-id="8e0d3-125">[Managing User Mappings](../core/managing-user-mappings.md) </span></span>  
 [<span data-ttu-id="8e0d3-126">Applications associées SSO</span><span class="sxs-lookup"><span data-stu-id="8e0d3-126">SSO Affiliate Applications</span></span>](../core/sso-affiliate-applications.md)