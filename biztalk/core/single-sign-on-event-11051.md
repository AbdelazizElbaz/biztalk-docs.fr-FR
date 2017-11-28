---
title: "Single Sign-On : Événement 11051 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fe767818-f74e-415c-9287-5b7cc46e358a
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 26a58ee5a4fd842dd292179cea0f7461a5ab0517
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-11051"></a><span data-ttu-id="364ff-102">Single Sign-On : Événement 11051</span><span class="sxs-lookup"><span data-stu-id="364ff-102">Single Sign-On: Event 11051</span></span>
## <a name="details"></a><span data-ttu-id="364ff-103">Détails</span><span class="sxs-lookup"><span data-stu-id="364ff-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="364ff-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="364ff-104">Product Name</span></span>|<span data-ttu-id="364ff-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="364ff-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="364ff-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="364ff-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="364ff-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="364ff-107">Event ID</span></span>|<span data-ttu-id="364ff-108">11051</span><span class="sxs-lookup"><span data-stu-id="364ff-108">11051</span></span>|  
|<span data-ttu-id="364ff-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="364ff-109">Event Source</span></span>|<span data-ttu-id="364ff-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="364ff-110">ENTSSO</span></span>|  
|<span data-ttu-id="364ff-111">Composant</span><span class="sxs-lookup"><span data-stu-id="364ff-111">Component</span></span>|<span data-ttu-id="364ff-112">Néant</span><span class="sxs-lookup"><span data-stu-id="364ff-112">N/A</span></span>|  
|<span data-ttu-id="364ff-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="364ff-113">Symbolic Name</span></span>|<span data-ttu-id="364ff-114">SSO_WARN_SSO_ADMIN_NOT_GROUP</span><span class="sxs-lookup"><span data-stu-id="364ff-114">SSO_WARN_SSO_ADMIN_NOT_GROUP</span></span>|  
|<span data-ttu-id="364ff-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="364ff-115">Message Text</span></span>|<span data-ttu-id="364ff-116">Le compte Administrateurs d'applications SSO contient un ou plusieurs comptes individuels (et non de groupe).</span><span class="sxs-lookup"><span data-stu-id="364ff-116">The SSO Administrators account contains one or more individual (not group) accounts.</span></span> <span data-ttu-id="364ff-117">Si ces comptes individuels sont supprimés dans Active Directory ou sur l'ordinateur local, ils doivent être retirés rapidement du système SSO, sinon ils présentent un risque pour la sécurité.%r</span><span class="sxs-lookup"><span data-stu-id="364ff-117">If these individual accounts are deleted from Active Directory or the local computer they must be promptly removed from the SSO system or they could become a security risk.%r</span></span><br /><br /> <span data-ttu-id="364ff-118">Les administrateurs de l’authentification unique : %1 %r</span><span class="sxs-lookup"><span data-stu-id="364ff-118">SSO Administrators: %1%r</span></span><br /><br /> <span data-ttu-id="364ff-119">Les comptes individuels : %2</span><span class="sxs-lookup"><span data-stu-id="364ff-119">Individual accounts: %2</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="364ff-120">Explication</span><span class="sxs-lookup"><span data-stu-id="364ff-120">Explanation</span></span>  
 <span data-ttu-id="364ff-121">La suppression d'un compte individuel dans Active Directory ou sur l'ordinateur local ne le supprime pas automatiquement du système SSO.</span><span class="sxs-lookup"><span data-stu-id="364ff-121">Deleting an individual account from the Active Directory or local computer does not automatically delete that account from the SSO System.</span></span> <span data-ttu-id="364ff-122">Cela signifie que si le compte UTILISATEUR1 était supprimé localement, puis qu'un autre utilisateur (par exemple, un nouvel employé) se connectait au système en utilisant ce nom, le système SSO accorderait au nouvel UTILISATEUR1 tous les droits de sécurité détenus par l'UTILISATEUR1 d'origine.</span><span class="sxs-lookup"><span data-stu-id="364ff-122">This means that if the account USER1 was deleted locally, and then a different user (for instance, a new employee) joined the system using that same name, the SSO System would grant the new USER1 all security rights possessed by the original USER1.</span></span> <span data-ttu-id="364ff-123">Cela pose un problème de sécurité.</span><span class="sxs-lookup"><span data-stu-id="364ff-123">This poses a security risk.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="364ff-124">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="364ff-124">User Action</span></span>  
 <span data-ttu-id="364ff-125">Aucune action n'est nécessaire tant qu'un compte individuel n'est pas supprimé dans Active Directory ou sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="364ff-125">No action is necessary until an individual account is deleted from Active Directory or the local computer.</span></span> <span data-ttu-id="364ff-126">Vous devez alors supprimer le compte individuel sur le système SSO dès que possible.</span><span class="sxs-lookup"><span data-stu-id="364ff-126">At that point, you must delete the individual account from the SSO System as soon as possible.</span></span>