---
title: "Single Sign-On : Événement 10679 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 645f2b74-2cbe-4c6a-b0f5-7e31f93f88c6
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f612f3cf6540340124a3f11ed99fe736df65296b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10679"></a><span data-ttu-id="db541-102">Single Sign-On : Événement 10679</span><span class="sxs-lookup"><span data-stu-id="db541-102">Single Sign-On: Event 10679</span></span>
## <a name="details"></a><span data-ttu-id="db541-103">Détails</span><span class="sxs-lookup"><span data-stu-id="db541-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="db541-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="db541-104">Product Name</span></span>|<span data-ttu-id="db541-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="db541-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="db541-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="db541-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="db541-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="db541-107">Event ID</span></span>|<span data-ttu-id="db541-108">10679</span><span class="sxs-lookup"><span data-stu-id="db541-108">10679</span></span>|  
|<span data-ttu-id="db541-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="db541-109">Event Source</span></span>|<span data-ttu-id="db541-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="db541-110">ENTSSO</span></span>|  
|<span data-ttu-id="db541-111">Composant</span><span class="sxs-lookup"><span data-stu-id="db541-111">Component</span></span>|<span data-ttu-id="db541-112">N\A</span><span class="sxs-lookup"><span data-stu-id="db541-112">N\A</span></span>|  
|<span data-ttu-id="db541-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="db541-113">Symbolic Name</span></span>|<span data-ttu-id="db541-114">SSO_WARN_PS_MAPPING_DISABLED</span><span class="sxs-lookup"><span data-stu-id="db541-114">SSO_WARN_PS_MAPPING_DISABLED</span></span>|  
|<span data-ttu-id="db541-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="db541-115">Message Text</span></span>|<span data-ttu-id="db541-116">Changement du mot de passe externe.</span><span class="sxs-lookup"><span data-stu-id="db541-116">External password change.</span></span> <span data-ttu-id="db541-117">Le mot de passe n'a pas été modifié pour le compte externe car le mappage est désactivé.%r</span><span class="sxs-lookup"><span data-stu-id="db541-117">The password was not changed for the external account because the mapping is disabled.%r</span></span><br /><br /> <span data-ttu-id="db541-118">ID de suivi : %1 %r</span><span class="sxs-lookup"><span data-stu-id="db541-118">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="db541-119">Carte : %2 %r</span><span class="sxs-lookup"><span data-stu-id="db541-119">Adapter: %2%r</span></span><br /><br /> <span data-ttu-id="db541-120">Nom de l’application : %3 %r</span><span class="sxs-lookup"><span data-stu-id="db541-120">Application Name: %3%r</span></span><br /><br /> <span data-ttu-id="db541-121">Compte externe : %4</span><span class="sxs-lookup"><span data-stu-id="db541-121">External Account: %4</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="db541-122">Explication</span><span class="sxs-lookup"><span data-stu-id="db541-122">Explanation</span></span>  
 <span data-ttu-id="db541-123">Cet événement d'avertissement indique que le mot de passe n'a pas été modifié pour le compte externe car le mappage est désactivé.</span><span class="sxs-lookup"><span data-stu-id="db541-123">This Warning event indicates that the password was not changed for the external account because the mapping is disabled.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="db541-124">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="db541-124">User Action</span></span>  
 <span data-ttu-id="db541-125">Pour résoudre cet avertissement, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="db541-125">To resolve this warning do the following:</span></span>  
  
-   <span data-ttu-id="db541-126">Utilisez les outils d'administration de l'authentification unique pour activer le mappage pour cet adaptateur.</span><span class="sxs-lookup"><span data-stu-id="db541-126">Use the SSO administration tools to enable mapping for this adapter.</span></span>  
  
## <a name="more-info"></a><span data-ttu-id="db541-127">En savoir plus</span><span class="sxs-lookup"><span data-stu-id="db541-127">More info</span></span>
  
-   [<span data-ttu-id="db541-128">Synchronisation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="db541-128">Password Synchronization</span></span>](../core/password-synchronization2.md)  
  
-   <span data-ttu-id="db541-129">**Propriétés de l’adaptateur de synchronisation de mot de passe : Options**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="db541-129">**Password Sync Adapter Properties: Options** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>