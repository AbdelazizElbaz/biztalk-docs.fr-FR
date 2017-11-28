---
title: "La valeur de propriété booléenne n’est pas valide | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 62b6c178-f8ea-451a-b2dc-9396c24c0f5b
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b6aa8d79c2c3b4ce9033a164a664e27effdd2b63
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-boolean-property-value-is-not-valid"></a><span data-ttu-id="92a0d-102">La valeur de propriété booléenne n'est pas valide</span><span class="sxs-lookup"><span data-stu-id="92a0d-102">The boolean property value is not valid</span></span>
## <a name="details"></a><span data-ttu-id="92a0d-103">Détails</span><span class="sxs-lookup"><span data-stu-id="92a0d-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="92a0d-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="92a0d-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="92a0d-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="92a0d-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="92a0d-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="92a0d-106">Event ID</span></span>|-|  
|<span data-ttu-id="92a0d-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="92a0d-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="92a0d-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="92a0d-108"> EDI</span></span>|  
|<span data-ttu-id="92a0d-109">Composant</span><span class="sxs-lookup"><span data-stu-id="92a0d-109">Component</span></span>|<span data-ttu-id="92a0d-110">Moteur de traitement par lot</span><span class="sxs-lookup"><span data-stu-id="92a0d-110">Batching Engine</span></span>|  
|<span data-ttu-id="92a0d-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="92a0d-111">Symbolic Name</span></span>|<span data-ttu-id="92a0d-112">InvalidBooleanPropertyValue</span><span class="sxs-lookup"><span data-stu-id="92a0d-112">InvalidBooleanPropertyValue</span></span>|  
|<span data-ttu-id="92a0d-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="92a0d-113">Message Text</span></span>|<span data-ttu-id="92a0d-114">La valeur de propriété booléenne n'est pas valide</span><span class="sxs-lookup"><span data-stu-id="92a0d-114">The boolean property value is not valid</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="92a0d-115">Explication</span><span class="sxs-lookup"><span data-stu-id="92a0d-115">Explanation</span></span>  
 <span data-ttu-id="92a0d-116">Cet événement d'erreur/d'avertissement/d'informations indique qu'une valeur entrée pour une propriété d'une ligne dans la boîte de dialogue Filtre par lot est non valide, car la propriété requiert une valeur booléenne et la valeur qui a été entrée n'est pas de ce type.</span><span class="sxs-lookup"><span data-stu-id="92a0d-116">This Error/Warning/Information event indicates that a value entered for a property in a row of the Batch Filter dialog box was invalid, because the property required a boolean value, but the value entered was not a boolean.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="92a0d-117">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="92a0d-117">User Action</span></span>  
 <span data-ttu-id="92a0d-118">Pour résoudre cette erreur, dans la boîte de dialogue Propriétés EDI, dans la page Paramètres de création de lots d'échange, ouvrez la boîte de dialogue Filtre par lot.</span><span class="sxs-lookup"><span data-stu-id="92a0d-118">To resolve this error, open the Batch Filter dialog box from within the Interchange Batch Creation Settings page of the EDI Properties dialog box.</span></span> <span data-ttu-id="92a0d-119">Vérifiez que les valeurs entrées pour les propriétés demandant une valeur booléenne sont appropriées.</span><span class="sxs-lookup"><span data-stu-id="92a0d-119">Make sure that the value entered for a property that requires a boolean value is in fact a boolean.</span></span>