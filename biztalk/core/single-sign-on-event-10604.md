---
title: "Single Sign-On : Événement 10604 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eea14ab1-5a89-4a62-b414-1bcb36ea339e
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0d9d6858fb13542ca642c9c48a8a187b66ba6526
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10604"></a><span data-ttu-id="3145c-102">Single Sign-On : Événement 10604</span><span class="sxs-lookup"><span data-stu-id="3145c-102">Single Sign-On: Event 10604</span></span>
## <a name="details"></a><span data-ttu-id="3145c-103">Détails</span><span class="sxs-lookup"><span data-stu-id="3145c-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3145c-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="3145c-104">Product Name</span></span>|<span data-ttu-id="3145c-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="3145c-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="3145c-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="3145c-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="3145c-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="3145c-107">Event ID</span></span>|<span data-ttu-id="3145c-108">10604</span><span class="sxs-lookup"><span data-stu-id="3145c-108">10604</span></span>|  
|<span data-ttu-id="3145c-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="3145c-109">Event Source</span></span>|<span data-ttu-id="3145c-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="3145c-110">ENTSSO</span></span>|  
|<span data-ttu-id="3145c-111">Composant</span><span class="sxs-lookup"><span data-stu-id="3145c-111">Component</span></span>|<span data-ttu-id="3145c-112">Néant</span><span class="sxs-lookup"><span data-stu-id="3145c-112">N/A</span></span>|  
|<span data-ttu-id="3145c-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="3145c-113">Symbolic Name</span></span>|<span data-ttu-id="3145c-114">SSO_ERROR_SSOCSTX_OUT_OF_PROC</span><span class="sxs-lookup"><span data-stu-id="3145c-114">SSO_ERROR_SSOCSTX_OUT_OF_PROC</span></span>|  
|<span data-ttu-id="3145c-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="3145c-115">Message Text</span></span>|<span data-ttu-id="3145c-116">L'application COM+ du « serveur ENTSSO » n'est pas configurée correctement.</span><span class="sxs-lookup"><span data-stu-id="3145c-116">The 'ENTSSO Server' COM+ application is not configured correctly.</span></span> <span data-ttu-id="3145c-117">Il doit s'agir d'une application de bibliothèque COM+.</span><span class="sxs-lookup"><span data-stu-id="3145c-117">It must be a COM+ library application.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="3145c-118">Explication</span><span class="sxs-lookup"><span data-stu-id="3145c-118">Explanation</span></span>  
 <span data-ttu-id="3145c-119">L'application COM+ doit être configurée en tant qu'application de bibliothèque COM+.</span><span class="sxs-lookup"><span data-stu-id="3145c-119">The COM+ application must be configured as a COM+ library application.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="3145c-120">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="3145c-120">User Action</span></span>  
 <span data-ttu-id="3145c-121">Dans le composant logiciel enfichable ENTSSO, développez le dossier COM+ et localisez votre serveur ENTSSO.</span><span class="sxs-lookup"><span data-stu-id="3145c-121">In the ENTSSO MMC Snap-In, expand the COM+ folder and locate your ENTSSO Server.</span></span> <span data-ttu-id="3145c-122">Cliquez avec le bouton droit sur le serveur, puis cliquez sur Propriétés.</span><span class="sxs-lookup"><span data-stu-id="3145c-122">Right-click the server, and then click Properties.</span></span> <span data-ttu-id="3145c-123">Sélectionnez l'option d'application de bibliothèque plutôt que d'application serveur, puis cliquez sur OK.</span><span class="sxs-lookup"><span data-stu-id="3145c-123">Select Library Application instead of Server Application, and click OK.</span></span>