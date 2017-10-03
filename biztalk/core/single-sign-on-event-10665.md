---
title: "Single Sign-On : Événement 10665 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8d0de9d0-9b46-4f3a-b796-1ce3de01cf4c
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8a7d4d5c4140448914ff77b09a692cc3a2136dfc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10665"></a><span data-ttu-id="6f8e9-102">Single Sign-On : Événement 10665</span><span class="sxs-lookup"><span data-stu-id="6f8e9-102">Single Sign-On: Event 10665</span></span>
## <a name="details"></a><span data-ttu-id="6f8e9-103">Détails</span><span class="sxs-lookup"><span data-stu-id="6f8e9-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6f8e9-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="6f8e9-104">Product Name</span></span>|<span data-ttu-id="6f8e9-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="6f8e9-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="6f8e9-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="6f8e9-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="6f8e9-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="6f8e9-107">Event ID</span></span>|<span data-ttu-id="6f8e9-108">10665</span><span class="sxs-lookup"><span data-stu-id="6f8e9-108">10665</span></span>|  
|<span data-ttu-id="6f8e9-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="6f8e9-109">Event Source</span></span>|<span data-ttu-id="6f8e9-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="6f8e9-110">ENTSSO</span></span>|  
|<span data-ttu-id="6f8e9-111">Composant</span><span class="sxs-lookup"><span data-stu-id="6f8e9-111">Component</span></span>|<span data-ttu-id="6f8e9-112">N\A</span><span class="sxs-lookup"><span data-stu-id="6f8e9-112">N\A</span></span>|  
|<span data-ttu-id="6f8e9-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="6f8e9-113">Symbolic Name</span></span>|<span data-ttu-id="6f8e9-114">SSO_WARN_NO_PROPERTIES</span><span class="sxs-lookup"><span data-stu-id="6f8e9-114">SSO_WARN_NO_PROPERTIES</span></span>|  
|<span data-ttu-id="6f8e9-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="6f8e9-115">Message Text</span></span>|<span data-ttu-id="6f8e9-116">Erreur lors de la lecture des propriétés de l'adaptateur de synchronisation de mot de passe.</span><span class="sxs-lookup"><span data-stu-id="6f8e9-116">Error reading password sync adapter properties.</span></span> <span data-ttu-id="6f8e9-117">Utilisation des valeurs par défaut.%r</span><span class="sxs-lookup"><span data-stu-id="6f8e9-117">Using defaults.%r</span></span><br /><br /> <span data-ttu-id="6f8e9-118">Carte : %1 %r</span><span class="sxs-lookup"><span data-stu-id="6f8e9-118">Adapter: %1%r</span></span><br /><br /> <span data-ttu-id="6f8e9-119">Code d’erreur : %2</span><span class="sxs-lookup"><span data-stu-id="6f8e9-119">Error Code: %2</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="6f8e9-120">Explication</span><span class="sxs-lookup"><span data-stu-id="6f8e9-120">Explanation</span></span>  
 <span data-ttu-id="6f8e9-121">Cet événement d'avertissement indique la survenue d'une erreur lors de la lecture des propriétés de l'adaptateur de synchronisation de mot de passe par défaut.</span><span class="sxs-lookup"><span data-stu-id="6f8e9-121">This Warning event indicates that there was an error reading the default password sync adapter properties.</span></span> <span data-ttu-id="6f8e9-122">Chaque adaptateur de synchronisation de mot de passe est associé à des propriétés.</span><span class="sxs-lookup"><span data-stu-id="6f8e9-122">Each password sync adapter has configuration properties associated with it.</span></span> <span data-ttu-id="6f8e9-123">Celles-ci peuvent être stockées dans la banque de configuration SSO et sont créées par les outils de ligne de commande SSO ou la console MMC d'administration de l'authentification unique lorsque l'adaptateur de synchronisation de mot de passe est créé.</span><span class="sxs-lookup"><span data-stu-id="6f8e9-123">These properties are stored in the SSO config store and are created by the SSO command line tools or the SSO Admin MMC when the password sync adapter is created.</span></span>  <span data-ttu-id="6f8e9-124">Des propriétés peuvent être manquantes si l'adaptateur de synchronisation de mot de passe a été créé autrement, et cette erreur peut être générée.</span><span class="sxs-lookup"><span data-stu-id="6f8e9-124">There can be missing properties if the password sync adapter was created by any other means, then this error can be issued.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="6f8e9-125">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="6f8e9-125">User Action</span></span>  
 <span data-ttu-id="6f8e9-126">Pour résoudre cet avertissement, effectuez l'une ou plusieurs des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="6f8e9-126">To resolve this warning, do one or more of the following:</span></span>  
  
-   <span data-ttu-id="6f8e9-127">Vérifiez les propriétés de l'adaptateur de synchronisation de mot de passe.</span><span class="sxs-lookup"><span data-stu-id="6f8e9-127">Verify password sync adapter properties.</span></span>  
  
-   <span data-ttu-id="6f8e9-128">Recréez l'adaptateur de synchronisation de mot de passe.</span><span class="sxs-lookup"><span data-stu-id="6f8e9-128">Recreate the password sync adapter</span></span>  
  
## <a name="more-info"></a><span data-ttu-id="6f8e9-129">En savoir plus</span><span class="sxs-lookup"><span data-stu-id="6f8e9-129">More info</span></span>
  
-   <span data-ttu-id="6f8e9-130">**Propriétés de l’adaptateur de synchronisation de mot de passe : Options**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="6f8e9-130">**Password Sync Adapter Properties: Options** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>
  
-   [<span data-ttu-id="6f8e9-131">Synchronisation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="6f8e9-131">Password Synchronization</span></span>](../core/password-synchronization2.md)