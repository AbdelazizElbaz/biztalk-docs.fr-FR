---
title: "Single Sign-On : Événement 10595 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1517478c-7217-4e34-a5cb-ff7deea367ed
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9139eb7479b0a048e2fab197863b42c47f87992a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10595"></a><span data-ttu-id="29ad8-102">Single Sign-On : Événement 10595</span><span class="sxs-lookup"><span data-stu-id="29ad8-102">Single Sign-On: Event 10595</span></span>
## <a name="details"></a><span data-ttu-id="29ad8-103">Détails</span><span class="sxs-lookup"><span data-stu-id="29ad8-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="29ad8-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="29ad8-104">Product Name</span></span>|<span data-ttu-id="29ad8-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="29ad8-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="29ad8-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="29ad8-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="29ad8-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="29ad8-107">Event ID</span></span>|<span data-ttu-id="29ad8-108">10595</span><span class="sxs-lookup"><span data-stu-id="29ad8-108">10595</span></span>|  
|<span data-ttu-id="29ad8-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="29ad8-109">Event Source</span></span>|<span data-ttu-id="29ad8-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="29ad8-110">ENTSSO</span></span>|  
|<span data-ttu-id="29ad8-111">Composant</span><span class="sxs-lookup"><span data-stu-id="29ad8-111">Component</span></span>|<span data-ttu-id="29ad8-112">Néant</span><span class="sxs-lookup"><span data-stu-id="29ad8-112">N/A</span></span>|  
|<span data-ttu-id="29ad8-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="29ad8-113">Symbolic Name</span></span>|<span data-ttu-id="29ad8-114">SSO_WARN_APP_INCOMPLETE_FIELDS</span><span class="sxs-lookup"><span data-stu-id="29ad8-114">SSO_WARN_APP_INCOMPLETE_FIELDS</span></span>|  
|<span data-ttu-id="29ad8-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="29ad8-115">Message Text</span></span>|<span data-ttu-id="29ad8-116">L'application ne peut pas être activée car les champs sont incomplets pour cette application.%r</span><span class="sxs-lookup"><span data-stu-id="29ad8-116">The application cannot be enabled because the fields are incomplete for this application.%r</span></span><br /><br /> <span data-ttu-id="29ad8-117">Nom de l’application : %1 %r</span><span class="sxs-lookup"><span data-stu-id="29ad8-117">Application Name: %1%r</span></span><br /><br /> <span data-ttu-id="29ad8-118">Nombre de champs définis : %2 %r</span><span class="sxs-lookup"><span data-stu-id="29ad8-118">Number of Fields Defined: %2%r</span></span><br /><br /> <span data-ttu-id="29ad8-119">Nombre de champs créés : %3</span><span class="sxs-lookup"><span data-stu-id="29ad8-119">Number of Fields Created: %3</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="29ad8-120">Explication</span><span class="sxs-lookup"><span data-stu-id="29ad8-120">Explanation</span></span>  
 <span data-ttu-id="29ad8-121">Lors de la création d'une application au niveau de l'API, vous avez spécifié le nombre de champs (UserID, Password) définis par l'application.</span><span class="sxs-lookup"><span data-stu-id="29ad8-121">When creating an application at the API level, you specified the number of fields (i.e. UserID, Password) the application would define.</span></span> <span data-ttu-id="29ad8-122">Chaque champ défini doit également être créé.</span><span class="sxs-lookup"><span data-stu-id="29ad8-122">Each field that has been defined must also be created.</span></span> <span data-ttu-id="29ad8-123">Ce message d'avertissement répertorie le nom de l'application, le nombre de champs définis et le nombre de champs créés.</span><span class="sxs-lookup"><span data-stu-id="29ad8-123">This warning message lists the application name, number of fields defined, and number of fields created.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="29ad8-124">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="29ad8-124">User Action</span></span>  
 <span data-ttu-id="29ad8-125">Identifiez les champs définis mais non créés, puis revenez en arrière et créez-les.</span><span class="sxs-lookup"><span data-stu-id="29ad8-125">Determine which fields were defined but not created, and then go back and create them.</span></span>