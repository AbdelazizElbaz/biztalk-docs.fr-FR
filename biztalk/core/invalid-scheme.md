---
title: "Schéma non valide | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3bb3e70a-d23c-45e9-bde5-edae6731e58a
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5736a3738a9598f4c4b419d7e291c3c3e32207f0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="invalid-scheme"></a><span data-ttu-id="bed01-102">Schéma non valide</span><span class="sxs-lookup"><span data-stu-id="bed01-102">Invalid scheme</span></span>
## <a name="details"></a><span data-ttu-id="bed01-103">Détails</span><span class="sxs-lookup"><span data-stu-id="bed01-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="bed01-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="bed01-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="bed01-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="bed01-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="bed01-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="bed01-106">Event ID</span></span>|<span data-ttu-id="bed01-107">0</span><span class="sxs-lookup"><span data-stu-id="bed01-107">0</span></span>|  
|<span data-ttu-id="bed01-108">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="bed01-108">Event Source</span></span>|<span data-ttu-id="bed01-109">0</span><span class="sxs-lookup"><span data-stu-id="bed01-109">0</span></span>|  
|<span data-ttu-id="bed01-110">Composant</span><span class="sxs-lookup"><span data-stu-id="bed01-110">Component</span></span>|<span data-ttu-id="bed01-111">0</span><span class="sxs-lookup"><span data-stu-id="bed01-111">0</span></span>|  
|<span data-ttu-id="bed01-112">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="bed01-112">Symbolic Name</span></span>|<span data-ttu-id="bed01-113">0</span><span class="sxs-lookup"><span data-stu-id="bed01-113">0</span></span>|  
|<span data-ttu-id="bed01-114">Texte du message</span><span class="sxs-lookup"><span data-stu-id="bed01-114">Message Text</span></span>|<span data-ttu-id="bed01-115">Schéma non valide ; schéma de « {0} » ou « {{1} » attendu.</span><span class="sxs-lookup"><span data-stu-id="bed01-115">Invalid scheme; expecting scheme "{0}" or "{1}"</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="bed01-116">Explication</span><span class="sxs-lookup"><span data-stu-id="bed01-116">Explanation</span></span>  
 <span data-ttu-id="bed01-117">Une des situations suivantes s’est produite : l’adresse spécifiée dans le champ URI (uniform resource identifier) doit commencer par http:// ou https://.</span><span class="sxs-lookup"><span data-stu-id="bed01-117">One of the following situations has occurred: the address that is specified in the URI (uniform resource identifier) field must start with either http:// or https://.</span></span> <span data-ttu-id="bed01-118">ou le schéma ne correspond pas aux données spécifiées dans l'implémentation de l'élément de transport de liaison.</span><span class="sxs-lookup"><span data-stu-id="bed01-118">Or the scheme does not match what is specified in the implementation of the transport binding element.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="bed01-119">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="bed01-119">User Action</span></span>  
 <span data-ttu-id="bed01-120">Entrez un URI d'adresse proxy valide commençant par http:// ou https://</span><span class="sxs-lookup"><span data-stu-id="bed01-120">Enter a valid proxy address URI that starts with http:// or https://</span></span>