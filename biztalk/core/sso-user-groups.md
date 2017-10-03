---
title: Groupes utilisateur SSO | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- administrator accounts, SSO
- groups, SSO
- user accounts, administrators
- service accounts, SSO
- SSO, user groups
- SSO, service accounts
- SSO, administrator accounts
ms.assetid: e279001e-c724-4a2d-8939-0ba9dd08a19c
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 949f3aa72771982321abf6904c43352b8821fc0c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="sso-user-groups"></a><span data-ttu-id="1e259-102">Groupes d’utilisateurs de l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="1e259-102">SSO User Groups</span></span>
<span data-ttu-id="1e259-103">Pour configurer et gérer le système d'authentification unique de l'entreprise, vous devez créer certains groupes et comptes Windows pour chacun de ces rôles.</span><span class="sxs-lookup"><span data-stu-id="1e259-103">To configure and manage the Enterprise Single Sign-On (SSO) system, you must create certain Windows groups and accounts for each of these roles.</span></span> <span data-ttu-id="1e259-104">Lors de la configuration de ces comptes d'accès dans l'authentification unique de l'entreprise, vous pouvez spécifier plusieurs comptes pour chaque rôle.</span><span class="sxs-lookup"><span data-stu-id="1e259-104">When configuring the access accounts in Enterprise SSO, you can specify more than one account for each of these roles.</span></span> <span data-ttu-id="1e259-105">Cette section décrit ces rôles.</span><span class="sxs-lookup"><span data-stu-id="1e259-105">This section describes these roles.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="1e259-106">Il est fortement recommandé d'utiliser les groupes de domaine lors de la configuration de l'authentification unique.</span><span class="sxs-lookup"><span data-stu-id="1e259-106">It is strongly recommended that you use domain groups when configuring SSO.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1e259-107">Pour des raisons de sécurité, le système d'authentification unique n'autorise pas les comptes intégrés.</span><span class="sxs-lookup"><span data-stu-id="1e259-107">For security purposes, the SSO system does not allow built-in accounts.</span></span>  
  
## <a name="single-sign-on-administrators"></a><span data-ttu-id="1e259-108">Administrateurs de l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="1e259-108">Single Sign-On Administrators</span></span>  
 <span data-ttu-id="1e259-109">Les administrateurs SSO disposent des droits d'utilisateur les plus élevés dans le système d'authentification unique.</span><span class="sxs-lookup"><span data-stu-id="1e259-109">SSO administrators have the highest level user rights in the SSO system.</span></span> <span data-ttu-id="1e259-110">Ils peuvent :</span><span class="sxs-lookup"><span data-stu-id="1e259-110">They can:</span></span>  
  
-   <span data-ttu-id="1e259-111">Créer et gérer la base de données SSO</span><span class="sxs-lookup"><span data-stu-id="1e259-111">Create and manage the SSO database</span></span>  
  
-   <span data-ttu-id="1e259-112">Créer et gérer le secret principal</span><span class="sxs-lookup"><span data-stu-id="1e259-112">Create and manage the master secret</span></span>  
  
-   <span data-ttu-id="1e259-113">Activer et désactiver le système d'authentification unique</span><span class="sxs-lookup"><span data-stu-id="1e259-113">Enable and disable the SSO system</span></span>  
  
-   <span data-ttu-id="1e259-114">Créer des adaptateurs de synchronisation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="1e259-114">Create password synchronization adapters</span></span>  
  
-   <span data-ttu-id="1e259-115">Activer et désactiver la synchronisation de mot de passe dans le système d'authentification unique</span><span class="sxs-lookup"><span data-stu-id="1e259-115">Enable and disable password synchronization in the SSO system</span></span>  
  
-   <span data-ttu-id="1e259-116">Activer et désactiver l'authentification unique initiée par l'hôte</span><span class="sxs-lookup"><span data-stu-id="1e259-116">Enable and disable host initiated SSO</span></span>  
  
-   <span data-ttu-id="1e259-117">Effectuer toutes les tâches d'administration</span><span class="sxs-lookup"><span data-stu-id="1e259-117">Perform all administration tasks</span></span>  
  
 <span data-ttu-id="1e259-118">Le compte d'administrateur SSO peut être un compte de groupe Windows ou un compte individuel.</span><span class="sxs-lookup"><span data-stu-id="1e259-118">The SSO administrators account can be either a Windows group account or an individual account.</span></span> <span data-ttu-id="1e259-119">Le compte d'administrateur SSO peut également être un compte individuel ou de groupe de domaine ou local.</span><span class="sxs-lookup"><span data-stu-id="1e259-119">The SSO administrators account can also be either a domain or local group or individual account.</span></span> <span data-ttu-id="1e259-120">Lorsque vous utilisez un compte individuel, vous ne pouvez pas modifier ce compte en un autre compte individuel.</span><span class="sxs-lookup"><span data-stu-id="1e259-120">When using an individual account, you cannot change this account to another individual account.</span></span> <span data-ttu-id="1e259-121">Par conséquent, il est recommandé de ne pas utiliser un compte individuel.</span><span class="sxs-lookup"><span data-stu-id="1e259-121">Therefore, it is recommended that you do not use an individual account.</span></span> <span data-ttu-id="1e259-122">Vous pouvez changer ce compte en un compte de groupe tant que le compte d'origine est membre du nouveau compte.</span><span class="sxs-lookup"><span data-stu-id="1e259-122">You can change this account to a group account as long as the original account is a member of the new account.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="1e259-123">Le compte de service exécutant le service d'authentification unique de l'entreprise doit être membre de ce compte.</span><span class="sxs-lookup"><span data-stu-id="1e259-123">The service account running the Enterprise Single Sign-On service must be a member of this account.</span></span> <span data-ttu-id="1e259-124">Pour sécuriser votre environnement, vérifiez qu'aucun autre service n'utilise le même compte de service.</span><span class="sxs-lookup"><span data-stu-id="1e259-124">To secure your environment, ensure that no other service is using the same service account.</span></span>  
  
## <a name="single-sign-on-affiliate-administrators"></a><span data-ttu-id="1e259-125">Administrateurs d'applications associées à SSO</span><span class="sxs-lookup"><span data-stu-id="1e259-125">Single Sign-On Affiliate Administrators</span></span>  
 <span data-ttu-id="1e259-126">L'administrateur d'applications associées à SSO définit les applications associées contenues dans le système d'authentification unique.</span><span class="sxs-lookup"><span data-stu-id="1e259-126">The SSO affiliate administrator defines the affiliate applications that the SSO system contains.</span></span> <span data-ttu-id="1e259-127">Les applications associées sont une entité logique qui représente le système principal auquel vous êtes connecté à l'aide de l'authentification unique.</span><span class="sxs-lookup"><span data-stu-id="1e259-127">Affiliate applications are a logical entity that represents the back-end system to which you are connecting using SSO.</span></span> <span data-ttu-id="1e259-128">Les administrateurs d'applications associées à SSO peuvent :</span><span class="sxs-lookup"><span data-stu-id="1e259-128">SSO affiliate administrators can:</span></span>  
  
-   <span data-ttu-id="1e259-129">Créer, gérer et supprimer des applications associées</span><span class="sxs-lookup"><span data-stu-id="1e259-129">Create, manage, and delete affiliate applications</span></span>  
  
-   <span data-ttu-id="1e259-130">Spécifier le compte d'administrateur d'application pour chaque application associée</span><span class="sxs-lookup"><span data-stu-id="1e259-130">Specify the application administrators account for each affiliate application</span></span>  
  
-   <span data-ttu-id="1e259-131">Effectuer toutes les tâches d'administration que les administrateurs et utilisateurs d'application peuvent réaliser</span><span class="sxs-lookup"><span data-stu-id="1e259-131">Perform all the administration tasks that the application administrators and application users can</span></span>  
  
 <span data-ttu-id="1e259-132">Le compte d'administrateur d'applications associées à SSO peut être un compte de groupe Windows ou un compte individuel.</span><span class="sxs-lookup"><span data-stu-id="1e259-132">The SSO Affiliate Administrator account can be either a Windows group account or an individual account.</span></span> <span data-ttu-id="1e259-133">Le compte d'administrateur d'applications associées à SSO peut également être un compte ou groupe de domaine ou local.</span><span class="sxs-lookup"><span data-stu-id="1e259-133">The SSO Affiliate Administrator account can also be either a domain or local group or account.</span></span>  
  
## <a name="application-administrators"></a><span data-ttu-id="1e259-134">Administrateurs d'application</span><span class="sxs-lookup"><span data-stu-id="1e259-134">Application Administrators</span></span>  
 <span data-ttu-id="1e259-135">Il existe un groupe d'administrateurs d'application par application associée.</span><span class="sxs-lookup"><span data-stu-id="1e259-135">There is one application administrators group per affiliate application.</span></span>  
  
 <span data-ttu-id="1e259-136">Les membres de ce groupe peuvent :</span><span class="sxs-lookup"><span data-stu-id="1e259-136">Members of this group can:</span></span>  
  
-   <span data-ttu-id="1e259-137">Modifier le compte du groupe d'utilisateurs d'application</span><span class="sxs-lookup"><span data-stu-id="1e259-137">Change the application users group account</span></span>  
  
-   <span data-ttu-id="1e259-138">Créer, supprimer et gérer les mappages d'informations d'identification pour tous les utilisateurs de l'application associée spécifique</span><span class="sxs-lookup"><span data-stu-id="1e259-138">Create, delete, and manage credential mappings for all users of the specific affiliate application</span></span>  
  
-   <span data-ttu-id="1e259-139">Définir des informations d'identification pour tout utilisateur dans ce compte du groupe d'utilisateurs d'application associée spécifique</span><span class="sxs-lookup"><span data-stu-id="1e259-139">Set credentials for any user in that specific affiliate application users group account</span></span>  
  
-   <span data-ttu-id="1e259-140">Effectuer toutes les tâches d'administration que les utilisateurs d'application peuvent réaliser</span><span class="sxs-lookup"><span data-stu-id="1e259-140">Perform all the administration tasks that the application users can</span></span>  
  
## <a name="application-users"></a><span data-ttu-id="1e259-141">Utilisateurs d'application</span><span class="sxs-lookup"><span data-stu-id="1e259-141">Application Users</span></span>  
 <span data-ttu-id="1e259-142">Il existe un compte du groupe d'utilisateurs d'application pour chaque application associée.</span><span class="sxs-lookup"><span data-stu-id="1e259-142">There is one application users group account for each affiliate application.</span></span> <span data-ttu-id="1e259-143">Ce compte contient la liste des utilisateurs finaux dans un environnement d'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="1e259-143">This account contains the list of end users in an Enterprise Single Sign-On environment.</span></span> <span data-ttu-id="1e259-144">Les membres de ce compte peuvent :</span><span class="sxs-lookup"><span data-stu-id="1e259-144">Members of this account can:</span></span>  
  
-   <span data-ttu-id="1e259-145">Rechercher leurs informations d'identification dans l'application associée</span><span class="sxs-lookup"><span data-stu-id="1e259-145">Look up their credentials in the affiliate application</span></span>  
  
-   <span data-ttu-id="1e259-146">Gérer leurs mappages d'informations d'identification dans l'application associée</span><span class="sxs-lookup"><span data-stu-id="1e259-146">Manage their credential mappings in the affiliate application</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1e259-147">N'oubliez pas d'être vigilant lors de l'affectation des groupes.</span><span class="sxs-lookup"><span data-stu-id="1e259-147">Remember to be vigilant when assigning groups.</span></span> <span data-ttu-id="1e259-148">Par exemple, vous pouvez utiliser un groupe d'utilisateurs de sécurité BizTalk Server pour un groupe d'utilisateurs d'application SSO.</span><span class="sxs-lookup"><span data-stu-id="1e259-148">It is possible, for example, to use a BizTalk Server security user group for the SSO application users group.</span></span> <span data-ttu-id="1e259-149">Avant de procéder, assurez-vous que tous les utilisateurs ont besoin de tout l'accès dont ils disposeront alors.</span><span class="sxs-lookup"><span data-stu-id="1e259-149">Before you do this, be certain that all users need all access that will then be available to them.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e259-150">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1e259-150">See Also</span></span>  
 <span data-ttu-id="1e259-151">[Comment mettre à jour les propriétés d’une Application associée](../core/how-to-update-the-properties-of-an-affiliate-application.md) </span><span class="sxs-lookup"><span data-stu-id="1e259-151">[How to Update the Properties of an Affiliate Application](../core/how-to-update-the-properties-of-an-affiliate-application.md) </span></span>  
 <span data-ttu-id="1e259-152">[Comment mettre à jour la base de données SSO](../core/how-to-update-the-sso-database.md) </span><span class="sxs-lookup"><span data-stu-id="1e259-152">[How to Update the SSO Database](../core/how-to-update-the-sso-database.md) </span></span>  
 <span data-ttu-id="1e259-153">[Gestion des mappages utilisateur](../core/managing-user-mappings.md) </span><span class="sxs-lookup"><span data-stu-id="1e259-153">[Managing User Mappings](../core/managing-user-mappings.md) </span></span>  
 [<span data-ttu-id="1e259-154">Présentation de l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="1e259-154">Understanding SSO</span></span>](../core/understanding-sso.md)