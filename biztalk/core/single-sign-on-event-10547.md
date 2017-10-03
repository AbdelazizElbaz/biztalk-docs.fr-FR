---
title: "Single Sign-On : Événement 10547 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: be25cdc9-d6c1-488d-9ead-877a2454c3d1
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5f6162461b1eb04993ca681049fe1fbb797ca014
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10547"></a><span data-ttu-id="41553-102">Single Sign-On : Événement 10547</span><span class="sxs-lookup"><span data-stu-id="41553-102">Single Sign-On: Event 10547</span></span>
## <a name="details"></a><span data-ttu-id="41553-103">Détails</span><span class="sxs-lookup"><span data-stu-id="41553-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="41553-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="41553-104">Product Name</span></span>|<span data-ttu-id="41553-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="41553-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="41553-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="41553-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="41553-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="41553-107">Event ID</span></span>|<span data-ttu-id="41553-108">10547</span><span class="sxs-lookup"><span data-stu-id="41553-108">10547</span></span>|  
|<span data-ttu-id="41553-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="41553-109">Event Source</span></span>|<span data-ttu-id="41553-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="41553-110">ENTSSO</span></span>|  
|<span data-ttu-id="41553-111">Composant</span><span class="sxs-lookup"><span data-stu-id="41553-111">Component</span></span>|<span data-ttu-id="41553-112">CO</span><span class="sxs-lookup"><span data-stu-id="41553-112">CO</span></span>|  
|<span data-ttu-id="41553-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="41553-113">Symbolic Name</span></span>|<span data-ttu-id="41553-114">SSO_WARN_UPDATE_FAILED</span><span class="sxs-lookup"><span data-stu-id="41553-114">SSO_WARN_UPDATE_FAILED</span></span>|  
|<span data-ttu-id="41553-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="41553-115">Message Text</span></span>|<span data-ttu-id="41553-116">Échec de la mise à jour des informations d'identification dans la base de données SSO au cours du rechiffrement</span><span class="sxs-lookup"><span data-stu-id="41553-116">Failed to update the credentials in the SSO database during re-encryption</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="41553-117">Explication</span><span class="sxs-lookup"><span data-stu-id="41553-117">Explanation</span></span>  
 <span data-ttu-id="41553-118">Cet avertissement indique qu'il n'a pas été possible de mettre à jour les informations d'identification avec les résultats du rechiffrement.</span><span class="sxs-lookup"><span data-stu-id="41553-118">This Warning event indicates that it was not possible to update the credentials with the result of the new encryption.</span></span> <span data-ttu-id="41553-119">Lorsque le secret principal est modifié, soit en générant un nouveau secret, soit en rétablissant un ancien secret, un rechiffrement est effectué sur la base de données SSO, afin de déchiffrer tous les secrets chiffrés via l'ancien secret et de procéder à un rechiffrement avec le nouveau secret.</span><span class="sxs-lookup"><span data-stu-id="41553-119">When the master secret is changed, either by generating a new secret or by restoring an old secret, a re-encryption is performed on the SSO database to decrypt all the secrets encrypted with the old secret, and re-encrypt them with the new secret.</span></span> <span data-ttu-id="41553-120">Cet événement peut se produire si les informations d'identification ont été supprimées alors qu'elles faisaient l'objet d'un rechiffrement.</span><span class="sxs-lookup"><span data-stu-id="41553-120">This event can occur if the credentials were deleted as they were in the process of being re-encrypted.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="41553-121">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="41553-121">User Action</span></span>  
 <span data-ttu-id="41553-122">Pour résoudre cet avertissement, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="41553-122">To resolve this warning, do the following:</span></span>  
  
-   <span data-ttu-id="41553-123">Attendez pendant quelques instants qu'un autre rechiffrement se produise ; s'il ne se produit pas automatiquement, redémarrez le service SSO, ce qui déclenchera un nouveau rechiffrement, s'il cela requis.</span><span class="sxs-lookup"><span data-stu-id="41553-123">Wait for another re-encryption to occur after a short delay; if that does not occur automatically, restart the SSO service which will trigger a new re-encryption if one is required.</span></span>  
  
 <span data-ttu-id="41553-124">Pour plus d'informations, consultez les ressources suivantes dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="41553-124">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="41553-125">Présentation de l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="41553-125">Understanding SSO</span></span>](../core/understanding-sso.md)