---
title: "Single Sign-On : Événement 11052 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c797ed19-7613-4e0f-8867-9258ec3776a4
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8aa45afc85535cd0107d43e795b6e3f97fcc5f9f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-11052"></a><span data-ttu-id="41746-102">Single Sign-On : Événement 11052</span><span class="sxs-lookup"><span data-stu-id="41746-102">Single Sign-On: Event 11052</span></span>
## <a name="details"></a><span data-ttu-id="41746-103">Détails</span><span class="sxs-lookup"><span data-stu-id="41746-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="41746-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="41746-104">Product Name</span></span>|<span data-ttu-id="41746-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="41746-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="41746-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="41746-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="41746-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="41746-107">Event ID</span></span>|<span data-ttu-id="41746-108">11052</span><span class="sxs-lookup"><span data-stu-id="41746-108">11052</span></span>|  
|<span data-ttu-id="41746-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="41746-109">Event Source</span></span>|<span data-ttu-id="41746-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="41746-110">ENTSSO</span></span>|  
|<span data-ttu-id="41746-111">Composant</span><span class="sxs-lookup"><span data-stu-id="41746-111">Component</span></span>|<span data-ttu-id="41746-112">Néant</span><span class="sxs-lookup"><span data-stu-id="41746-112">N/A</span></span>|  
|<span data-ttu-id="41746-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="41746-113">Symbolic Name</span></span>|<span data-ttu-id="41746-114">SSO_WARN_SSO_AFF_ADMIN_NOT_GROUP</span><span class="sxs-lookup"><span data-stu-id="41746-114">SSO_WARN_SSO_AFF_ADMIN_NOT_GROUP</span></span>|  
|<span data-ttu-id="41746-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="41746-115">Message Text</span></span>|<span data-ttu-id="41746-116">Le compte Administrateurs d'applications associées à SSO contient un ou plusieurs comptes individuels (et non de groupe).</span><span class="sxs-lookup"><span data-stu-id="41746-116">The SSO Affiliate Administrators account contains one or more individual (not group) accounts.</span></span> <span data-ttu-id="41746-117">Si ces comptes individuels sont supprimés dans Active Directory ou sur l'ordinateur local, ils doivent être retirés rapidement du système SSO, sinon ils présentent un risque pour la sécurité.%r</span><span class="sxs-lookup"><span data-stu-id="41746-117">If these individual accounts are deleted from Active Directory or the local computer they must be promptly removed from the SSO system or they could become a security risk.%r</span></span><br /><br /> <span data-ttu-id="41746-118">Administrateurs d’applications associées SSO : %1 %r</span><span class="sxs-lookup"><span data-stu-id="41746-118">SSO Affiliate Administrators: %1%r</span></span><br /><br /> <span data-ttu-id="41746-119">Les comptes individuels : %2</span><span class="sxs-lookup"><span data-stu-id="41746-119">Individual accounts: %2</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="41746-120">Explication</span><span class="sxs-lookup"><span data-stu-id="41746-120">Explanation</span></span>  
 <span data-ttu-id="41746-121">La suppression d'un compte individuel dans Active Directory ou sur l'ordinateur local ne le supprime pas automatiquement du système SSO.</span><span class="sxs-lookup"><span data-stu-id="41746-121">Deleting an individual account from the Active Directory or local computer does not automatically delete that account from the SSO System.</span></span> <span data-ttu-id="41746-122">Cela signifie que si le compte UTILISATEUR1 était supprimé localement, puis qu'un autre utilisateur (par exemple, un nouvel employé) se connectait au système en utilisant ce nom, le système SSO accorderait au nouvel UTILISATEUR1 tous les droits de sécurité détenus par l'UTILISATEUR1 d'origine.</span><span class="sxs-lookup"><span data-stu-id="41746-122">This means that if the account USER1 was deleted locally, and then a different user (for instance, a new employee) joined the system using that same name, the SSO System would grant the new USER1 all security rights possessed by the original USER1.</span></span> <span data-ttu-id="41746-123">Cela pose un problème de sécurité.</span><span class="sxs-lookup"><span data-stu-id="41746-123">This poses a security risk.</span></span>  
  
 <span data-ttu-id="41746-124">Il est recommandé que les comptes d'administration SSO utilisent des comptes de groupe Active Directory (et non des comptes individuels).</span><span class="sxs-lookup"><span data-stu-id="41746-124">As a best practice, it is recommended that SSO Administration accounts use Active Directory group (not individual) accounts.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="41746-125">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="41746-125">User Action</span></span>  
 <span data-ttu-id="41746-126">Aucune action n'est nécessaire tant qu'un compte individuel n'est pas supprimé dans Active Directory ou sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="41746-126">No action is necessary until an individual account is deleted from Active Directory or the local computer.</span></span> <span data-ttu-id="41746-127">Vous devez alors supprimer le compte individuel sur le système SSO dès que possible.</span><span class="sxs-lookup"><span data-stu-id="41746-127">At that point, you must delete the individual account from the SSO System as soon as possible.</span></span>