---
title: "Single Sign-On : Événement 10808 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0b4efc1d-f163-4440-a78e-53065c6af36c
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b891a8cb076c332eca8918ece713385c1bbccc3a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10808"></a><span data-ttu-id="7b601-102">Single Sign-On : Événement 10808</span><span class="sxs-lookup"><span data-stu-id="7b601-102">Single Sign-On: Event 10808</span></span>
## <a name="details"></a><span data-ttu-id="7b601-103">Détails</span><span class="sxs-lookup"><span data-stu-id="7b601-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7b601-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="7b601-104">Product Name</span></span>|<span data-ttu-id="7b601-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="7b601-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="7b601-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="7b601-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="7b601-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="7b601-107">Event ID</span></span>|<span data-ttu-id="7b601-108">10808</span><span class="sxs-lookup"><span data-stu-id="7b601-108">10808</span></span>|  
|<span data-ttu-id="7b601-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="7b601-109">Event Source</span></span>|<span data-ttu-id="7b601-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="7b601-110">ENTSSO</span></span>|  
|<span data-ttu-id="7b601-111">Composant</span><span class="sxs-lookup"><span data-stu-id="7b601-111">Component</span></span>|<span data-ttu-id="7b601-112">Néant</span><span class="sxs-lookup"><span data-stu-id="7b601-112">N/A</span></span>|  
|<span data-ttu-id="7b601-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="7b601-113">Symbolic Name</span></span>|<span data-ttu-id="7b601-114">ENTSSO_E_HISSO_SYSTEM_NOT_ENABLED</span><span class="sxs-lookup"><span data-stu-id="7b601-114">ENTSSO_E_HISSO_SYSTEM_NOT_ENABLED</span></span>|  
|<span data-ttu-id="7b601-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="7b601-115">Message Text</span></span>|<span data-ttu-id="7b601-116">L'authentification unique initiée par l'hôte n'est pas activée pour le système d'authentification unique.</span><span class="sxs-lookup"><span data-stu-id="7b601-116">The SSO system is not enabled for Host Initiated Single Sign-On.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="7b601-117">Explication</span><span class="sxs-lookup"><span data-stu-id="7b601-117">Explanation</span></span>  
 <span data-ttu-id="7b601-118">L'authentification unique initiée par l'hôte n'est pas activée pour le système d'authentification unique.</span><span class="sxs-lookup"><span data-stu-id="7b601-118">The SSO system is not enabled for Host Initiated Single Sign-On.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="7b601-119">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="7b601-119">User Action</span></span>  
 <span data-ttu-id="7b601-120">Utilisez les outils d'administration pour configurer l'authentification unique initiée par l'hôte.</span><span class="sxs-lookup"><span data-stu-id="7b601-120">Use the administrative tools to configure Host Initiated Single Sign-On.</span></span> <span data-ttu-id="7b601-121">Cette action permet de définir l'indicateur</span><span class="sxs-lookup"><span data-stu-id="7b601-121">This will set the</span></span>  
  
 <span data-ttu-id="7b601-122">SSO_FLAG_SSO_EXTERNAL_TO_WINDOWS sur les informations globales.</span><span class="sxs-lookup"><span data-stu-id="7b601-122">SSO_FLAG_SSO_EXTERNAL_TO_WINDOWS flag on the global information.</span></span>