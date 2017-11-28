---
title: "Single Sign-On : Événement 10681 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 87ce2e50-cf54-4b23-b247-f137ce64ba1d
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cd0f1b6c27f3e77220d4615da1c0b5bb343344de
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10681"></a><span data-ttu-id="7e0df-102">Single Sign-On : Événement 10681</span><span class="sxs-lookup"><span data-stu-id="7e0df-102">Single Sign-On: Event 10681</span></span>
## <a name="details"></a><span data-ttu-id="7e0df-103">Détails</span><span class="sxs-lookup"><span data-stu-id="7e0df-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7e0df-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="7e0df-104">Product Name</span></span>|<span data-ttu-id="7e0df-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="7e0df-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="7e0df-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="7e0df-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="7e0df-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="7e0df-107">Event ID</span></span>|<span data-ttu-id="7e0df-108">10681</span><span class="sxs-lookup"><span data-stu-id="7e0df-108">10681</span></span>|  
|<span data-ttu-id="7e0df-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="7e0df-109">Event Source</span></span>|<span data-ttu-id="7e0df-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="7e0df-110">ENTSSO</span></span>|  
|<span data-ttu-id="7e0df-111">Composant</span><span class="sxs-lookup"><span data-stu-id="7e0df-111">Component</span></span>|<span data-ttu-id="7e0df-112">N\A</span><span class="sxs-lookup"><span data-stu-id="7e0df-112">N\A</span></span>|  
|<span data-ttu-id="7e0df-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="7e0df-113">Symbolic Name</span></span>|<span data-ttu-id="7e0df-114">SSO_WARN_NO_WINDOWS_PASSWORD_CHANGE</span><span class="sxs-lookup"><span data-stu-id="7e0df-114">SSO_WARN_NO_WINDOWS_PASSWORD_CHANGE</span></span>|  
|<span data-ttu-id="7e0df-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="7e0df-115">Message Text</span></span>|<span data-ttu-id="7e0df-116">Changement du mot de passe externe.</span><span class="sxs-lookup"><span data-stu-id="7e0df-116">External password change.</span></span> <span data-ttu-id="7e0df-117">Le mot de passe Windows n'a pas été modifié car une ou plusieurs des modifications de compte externe ont échoué.%r</span><span class="sxs-lookup"><span data-stu-id="7e0df-117">The Windows password was not changed because one or more of the external account changes failed.%r</span></span><br /><br /> <span data-ttu-id="7e0df-118">ID de suivi : %1 %r</span><span class="sxs-lookup"><span data-stu-id="7e0df-118">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="7e0df-119">Carte : %2 %r</span><span class="sxs-lookup"><span data-stu-id="7e0df-119">Adapter: %2%r</span></span><br /><br /> <span data-ttu-id="7e0df-120">Compte Windows : %3</span><span class="sxs-lookup"><span data-stu-id="7e0df-120">Windows Account: %3</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="7e0df-121">Explication</span><span class="sxs-lookup"><span data-stu-id="7e0df-121">Explanation</span></span>  
 <span data-ttu-id="7e0df-122">Cet événement d'avertissement indique que le mot de passe Windows n'a pas été modifié car une ou plusieurs des modifications de compte externe ont échoué.</span><span class="sxs-lookup"><span data-stu-id="7e0df-122">This Warning event indicates that the Windows password was not changed because one or more of the external account changes failed.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="7e0df-123">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="7e0df-123">User Action</span></span>  
 <span data-ttu-id="7e0df-124">Pour résoudre cet avertissement, effectuez l'une ou plusieurs des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="7e0df-124">To resolve this warning, do one or more of the following:</span></span>  
  
-   <span data-ttu-id="7e0df-125">Vérifiez les journaux système et des événements d’Application pour les événements associés.</span><span class="sxs-lookup"><span data-stu-id="7e0df-125">Check the System and Application Event logs for associated events.</span></span>  
  
-   <span data-ttu-id="7e0df-126">Vérifiez la configuration de l'adaptateur à l'aide des outils d'administration de l'authentification unique.</span><span class="sxs-lookup"><span data-stu-id="7e0df-126">Verify adapter configuration using the SSO administration tools.</span></span>  
  
-   <span data-ttu-id="7e0df-127">Vérifiez les systèmes externes.</span><span class="sxs-lookup"><span data-stu-id="7e0df-127">Verify external systems.</span></span>  
  
## <a name="more-info"></a><span data-ttu-id="7e0df-128">En savoir plus</span><span class="sxs-lookup"><span data-stu-id="7e0df-128">More info</span></span>
  
-   [<span data-ttu-id="7e0df-129">Synchronisation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="7e0df-129">Password Synchronization</span></span>](../core/password-synchronization2.md)  
  
-   <span data-ttu-id="7e0df-130">**Propriétés de l’adaptateur de synchronisation de mot de passe : Options**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="7e0df-130">**Password Sync Adapter Properties: Options** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>