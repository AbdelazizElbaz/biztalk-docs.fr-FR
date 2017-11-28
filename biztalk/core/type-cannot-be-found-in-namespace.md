---
title: "Type est introuvable dans l’espace de noms | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 66387fa6-3ba3-499f-99d6-bb0033c68adc
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 515dd9b6b73b43bee22ffc7b67745bb45adcaf6c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="type-cannot-be-found-in-namespace"></a><span data-ttu-id="377cc-102">Type introuvable dans l'espace de noms</span><span class="sxs-lookup"><span data-stu-id="377cc-102">Type cannot be found in namespace</span></span>
## <a name="details"></a><span data-ttu-id="377cc-103">Détails</span><span class="sxs-lookup"><span data-stu-id="377cc-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="377cc-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="377cc-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="377cc-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="377cc-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="377cc-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="377cc-106">Event ID</span></span>|<span data-ttu-id="377cc-107">0</span><span class="sxs-lookup"><span data-stu-id="377cc-107">0</span></span>|  
|<span data-ttu-id="377cc-108">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="377cc-108">Event Source</span></span>|<span data-ttu-id="377cc-109">0</span><span class="sxs-lookup"><span data-stu-id="377cc-109">0</span></span>|  
|<span data-ttu-id="377cc-110">Composant</span><span class="sxs-lookup"><span data-stu-id="377cc-110">Component</span></span>|<span data-ttu-id="377cc-111">0</span><span class="sxs-lookup"><span data-stu-id="377cc-111">0</span></span>|  
|<span data-ttu-id="377cc-112">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="377cc-112">Symbolic Name</span></span>|<span data-ttu-id="377cc-113">0</span><span class="sxs-lookup"><span data-stu-id="377cc-113">0</span></span>|  
|<span data-ttu-id="377cc-114">Texte du message</span><span class="sxs-lookup"><span data-stu-id="377cc-114">Message Text</span></span>|<span data-ttu-id="377cc-115">Erreur : Le Type « {0} » ne peut pas être trouvé dans l’espace de noms « {{1} »</span><span class="sxs-lookup"><span data-stu-id="377cc-115">Error: Type "{0}" cannot be found in namespace "{1}"</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="377cc-116">Explication</span><span class="sxs-lookup"><span data-stu-id="377cc-116">Explanation</span></span>  
 <span data-ttu-id="377cc-117">Cette erreur indique que des artefacts créés font référence à des types introuvables dans l'espace de noms spécifié.</span><span class="sxs-lookup"><span data-stu-id="377cc-117">This error indicates artifacts that are created are referencing types which cannot be found in the namespace specified.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="377cc-118">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="377cc-118">User Action</span></span>  
 <span data-ttu-id="377cc-119">Ajoutez une référence contenant le type introuvable, puis réexécutez l'Assistant (si vous êtes le propriétaire du service WCF que vous tentez d'utiliser).</span><span class="sxs-lookup"><span data-stu-id="377cc-119">Add a reference that contain the type that is not found, and run the wizard again (if you own the WCF service that you are trying to consume).</span></span> <span data-ttu-id="377cc-120">Sinon, contactez le fournisseur de services.</span><span class="sxs-lookup"><span data-stu-id="377cc-120">Otherwise, contact the service provider.</span></span>