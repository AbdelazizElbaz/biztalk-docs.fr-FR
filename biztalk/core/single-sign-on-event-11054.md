---
title: "Single Sign-On : Événement 11054 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 59dc801d-fc78-4561-8a26-9d815c86d842
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2c4d71bc77f36231ddec939faf5e904e45017614
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-11054"></a><span data-ttu-id="d9c8b-102">Single Sign-On : Événement 11054</span><span class="sxs-lookup"><span data-stu-id="d9c8b-102">Single Sign-On: Event 11054</span></span>
## <a name="details"></a><span data-ttu-id="d9c8b-103">Détails</span><span class="sxs-lookup"><span data-stu-id="d9c8b-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d9c8b-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="d9c8b-104">Product Name</span></span>|<span data-ttu-id="d9c8b-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="d9c8b-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="d9c8b-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="d9c8b-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="d9c8b-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="d9c8b-107">Event ID</span></span>|<span data-ttu-id="d9c8b-108">11054</span><span class="sxs-lookup"><span data-stu-id="d9c8b-108">11054</span></span>|  
|<span data-ttu-id="d9c8b-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="d9c8b-109">Event Source</span></span>|<span data-ttu-id="d9c8b-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="d9c8b-110">ENTSSO</span></span>|  
|<span data-ttu-id="d9c8b-111">Composant</span><span class="sxs-lookup"><span data-stu-id="d9c8b-111">Component</span></span>|<span data-ttu-id="d9c8b-112">Néant</span><span class="sxs-lookup"><span data-stu-id="d9c8b-112">N/A</span></span>|  
|<span data-ttu-id="d9c8b-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="d9c8b-113">Symbolic Name</span></span>|<span data-ttu-id="d9c8b-114">SSO_WARN_APP_USERS_NOT_GROUP</span><span class="sxs-lookup"><span data-stu-id="d9c8b-114">SSO_WARN_APP_USERS_NOT_GROUP</span></span>|  
|<span data-ttu-id="d9c8b-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="d9c8b-115">Message Text</span></span>|<span data-ttu-id="d9c8b-116">Le compte Utilisateurs d'applications contient un ou plusieurs comptes individuels (différents des comptes de groupe).</span><span class="sxs-lookup"><span data-stu-id="d9c8b-116">The Application Users account contains one or more individual (not group) accounts.</span></span> <span data-ttu-id="d9c8b-117">Si ces comptes individuels sont supprimés dans Active Directory ou sur l'ordinateur local, ils doivent être retirés rapidement du système SSO, sinon ils présentent un risque pour la sécurité.%r</span><span class="sxs-lookup"><span data-stu-id="d9c8b-117">If these individual accounts are deleted from Active Directory or the local computer they must be promptly removed from the SSO system or they could become a security risk.%r</span></span><br /><br /> <span data-ttu-id="d9c8b-118">Nom de l’application : %1 %r</span><span class="sxs-lookup"><span data-stu-id="d9c8b-118">Application Name: %1%r</span></span><br /><br /> <span data-ttu-id="d9c8b-119">Utilisateurs de l’application : %2 %r</span><span class="sxs-lookup"><span data-stu-id="d9c8b-119">Application Users: %2%r</span></span><br /><br /> <span data-ttu-id="d9c8b-120">Les comptes individuels : %3</span><span class="sxs-lookup"><span data-stu-id="d9c8b-120">Individual accounts: %3</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="d9c8b-121">Explication</span><span class="sxs-lookup"><span data-stu-id="d9c8b-121">Explanation</span></span>  
 <span data-ttu-id="d9c8b-122">La suppression d'un compte individuel dans Active Directory ou sur l'ordinateur local ne le supprime pas automatiquement du système SSO.</span><span class="sxs-lookup"><span data-stu-id="d9c8b-122">Deleting an individual account from the Active Directory or local computer does not automatically delete that account from the SSO System.</span></span> <span data-ttu-id="d9c8b-123">Cela signifie que si le compte UTILISATEUR1 était supprimé localement, puis qu'un autre utilisateur (par exemple, un nouvel employé) se connectait au système en utilisant ce nom, le système SSO accorderait au nouvel UTILISATEUR1 tous les droits de sécurité détenus par l'UTILISATEUR1 d'origine.</span><span class="sxs-lookup"><span data-stu-id="d9c8b-123">This means that if the account USER1 was deleted locally, and then a different user (for instance, a new employee) joined the system using that same name, the SSO System would grant the new USER1 all security rights possessed by the original USER1.</span></span> <span data-ttu-id="d9c8b-124">Cela pose un problème de sécurité.</span><span class="sxs-lookup"><span data-stu-id="d9c8b-124">This poses a security risk.</span></span>  
  
 <span data-ttu-id="d9c8b-125">Il est recommandé que les comptes d'administration SSO utilisent des comptes de groupe Active Directory (et non des comptes individuels).</span><span class="sxs-lookup"><span data-stu-id="d9c8b-125">As a best practice, it is recommended that SSO Administration accounts use Active Directory group (not individual) accounts.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="d9c8b-126">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="d9c8b-126">User Action</span></span>  
 <span data-ttu-id="d9c8b-127">Aucune action n'est nécessaire tant qu'un compte individuel n'est pas supprimé dans Active Directory ou sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="d9c8b-127">No action is necessary until an individual account is deleted from Active Directory or the local computer.</span></span> <span data-ttu-id="d9c8b-128">Vous devez alors supprimer le compte individuel sur le système SSO dès que possible.</span><span class="sxs-lookup"><span data-stu-id="d9c8b-128">At that point, you must delete the individual account from the SSO System as soon as possible.</span></span>