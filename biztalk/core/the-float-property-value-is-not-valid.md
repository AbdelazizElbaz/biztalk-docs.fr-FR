---
title: "La valeur de propriété float n’est pas valide | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 79327dc6-fc5e-4290-9663-16bb64970d4b
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7575bf01bbb08372f9dde8e1b352e1a3406bebe0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-float-property-value-is-not-valid"></a><span data-ttu-id="e0c93-102">La valeur de propriété float n'est pas valide</span><span class="sxs-lookup"><span data-stu-id="e0c93-102">The float property value is not valid</span></span>
## <a name="details"></a><span data-ttu-id="e0c93-103">Détails</span><span class="sxs-lookup"><span data-stu-id="e0c93-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e0c93-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="e0c93-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="e0c93-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="e0c93-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="e0c93-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="e0c93-106">Event ID</span></span>|-|  
|<span data-ttu-id="e0c93-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="e0c93-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="e0c93-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="e0c93-108"> EDI</span></span>|  
|<span data-ttu-id="e0c93-109">Composant</span><span class="sxs-lookup"><span data-stu-id="e0c93-109">Component</span></span>|<span data-ttu-id="e0c93-110">Moteur de traitement par lot</span><span class="sxs-lookup"><span data-stu-id="e0c93-110">Batching Engine</span></span>|  
|<span data-ttu-id="e0c93-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="e0c93-111">Symbolic Name</span></span>|<span data-ttu-id="e0c93-112">InvalidFloatPropertyValue</span><span class="sxs-lookup"><span data-stu-id="e0c93-112">InvalidFloatPropertyValue</span></span>|  
|<span data-ttu-id="e0c93-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="e0c93-113">Message Text</span></span>|<span data-ttu-id="e0c93-114">La valeur de propriété float n'est pas valide</span><span class="sxs-lookup"><span data-stu-id="e0c93-114">The float property value is not valid</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="e0c93-115">Explication</span><span class="sxs-lookup"><span data-stu-id="e0c93-115">Explanation</span></span>  
 <span data-ttu-id="e0c93-116">Cet événement d'erreur/d'avertissement/d'informations indique qu'une valeur entrée pour une propriété d'une ligne dans la boîte de dialogue Filtre par lot est non valide, car la propriété requiert une valeur float et la valeur qui a été entrée n'est pas de ce type.</span><span class="sxs-lookup"><span data-stu-id="e0c93-116">This Error/Warning/Information event indicates that a value entered for a property in a row of the Batch Filter dialog box was invalid, because the property required a float value, but the value entered was not a float.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="e0c93-117">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="e0c93-117">User Action</span></span>  
 <span data-ttu-id="e0c93-118">Pour résoudre cette erreur, dans la boîte de dialogue Propriétés EDI, dans la page Paramètres de création de lots d'échange, ouvrez la boîte de dialogue Filtre par lot.</span><span class="sxs-lookup"><span data-stu-id="e0c93-118">To resolve this error, open the Batch Filter dialog box from within the Interchange Batch Creation Settings page of the EDI Properties dialog box.</span></span> <span data-ttu-id="e0c93-119">Vérifiez que la valeur entrée pour une propriété demandant une valeur float est appropriée.</span><span class="sxs-lookup"><span data-stu-id="e0c93-119">Make sure that the value entered for a property that requires a float is in fact a float.</span></span>