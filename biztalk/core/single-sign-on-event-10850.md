---
title: "Single Sign-On : Événement 10850 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 04e2af52-d35b-491a-a983-d80442dd6aef
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 94e9bef6d104b8da3c41d295005a7a274a1d2610
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10850"></a><span data-ttu-id="1a364-102">Single Sign-On : Événement 10850</span><span class="sxs-lookup"><span data-stu-id="1a364-102">Single Sign-On: Event 10850</span></span>
## <a name="details"></a><span data-ttu-id="1a364-103">Détails</span><span class="sxs-lookup"><span data-stu-id="1a364-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1a364-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="1a364-104">Product Name</span></span>|<span data-ttu-id="1a364-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="1a364-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="1a364-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="1a364-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="1a364-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="1a364-107">Event ID</span></span>|<span data-ttu-id="1a364-108">10850</span><span class="sxs-lookup"><span data-stu-id="1a364-108">10850</span></span>|  
|<span data-ttu-id="1a364-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="1a364-109">Event Source</span></span>|<span data-ttu-id="1a364-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="1a364-110">ENTSSO</span></span>|  
|<span data-ttu-id="1a364-111">Composant</span><span class="sxs-lookup"><span data-stu-id="1a364-111">Component</span></span>|<span data-ttu-id="1a364-112">Néant</span><span class="sxs-lookup"><span data-stu-id="1a364-112">N/A</span></span>|  
|<span data-ttu-id="1a364-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="1a364-113">Symbolic Name</span></span>|<span data-ttu-id="1a364-114">ENTSSO_E_ENABLED_NOT_ALLOWED_CREATE</span><span class="sxs-lookup"><span data-stu-id="1a364-114">ENTSSO_E_ENABLED_NOT_ALLOWED_CREATE</span></span>|  
|<span data-ttu-id="1a364-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="1a364-115">Message Text</span></span>|<span data-ttu-id="1a364-116">Une application ne peut pas être créée avec l'indicateur « enabled » spécifié.</span><span class="sxs-lookup"><span data-stu-id="1a364-116">An application cannot be created with the 'enabled' flag specified.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="1a364-117">Explication</span><span class="sxs-lookup"><span data-stu-id="1a364-117">Explanation</span></span>  
 <span data-ttu-id="1a364-118">Avant d'activer une application, il est nécessaire de créer l'application et d'entrer des informations dans ses champs (UserID et Password).</span><span class="sxs-lookup"><span data-stu-id="1a364-118">Before enabling an application, it is necessary to both create the application and enter the field information for each of its fields (i.e. UserID and Password).</span></span> <span data-ttu-id="1a364-119">Il n'est pas possible de créer une application avec le champ « enabled » déjà activé.</span><span class="sxs-lookup"><span data-stu-id="1a364-119">It is not possible to create an application with the “enabled” field already set.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="1a364-120">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="1a364-120">User Action</span></span>  
 <span data-ttu-id="1a364-121">Créez à nouveau l'application (à l'aide de l'API Création d'une application ou de l'Assistant Création d'une application associée).</span><span class="sxs-lookup"><span data-stu-id="1a364-121">Create the application again (using either the Create Application API or the Create New Affiliate Application Wizard).</span></span> <span data-ttu-id="1a364-122">Lorsque cette application est terminée et les champs renseignés, activez l'application.</span><span class="sxs-lookup"><span data-stu-id="1a364-122">When the application is complete and the fields populated, enable the application.</span></span>