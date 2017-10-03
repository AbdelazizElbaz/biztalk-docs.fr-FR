---
title: "La valeur de propriété octet n’est pas valide | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e8599688-9f05-4983-8850-9ac1479ce9cc
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5789ae17b5127b58de45e5c4764b4ef490c43f1f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-byte-property-value-is-not-valid"></a><span data-ttu-id="dcb1a-102">La valeur de propriété octet n'est pas valide</span><span class="sxs-lookup"><span data-stu-id="dcb1a-102">The byte property value is not valid</span></span>
## <a name="details"></a><span data-ttu-id="dcb1a-103">Détails</span><span class="sxs-lookup"><span data-stu-id="dcb1a-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="dcb1a-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="dcb1a-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="dcb1a-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="dcb1a-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="dcb1a-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="dcb1a-106">Event ID</span></span>|-|  
|<span data-ttu-id="dcb1a-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="dcb1a-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="dcb1a-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="dcb1a-108"> EDI</span></span>|  
|<span data-ttu-id="dcb1a-109">Composant</span><span class="sxs-lookup"><span data-stu-id="dcb1a-109">Component</span></span>|<span data-ttu-id="dcb1a-110">Moteur de traitement par lot</span><span class="sxs-lookup"><span data-stu-id="dcb1a-110">Batching Engine</span></span>|  
|<span data-ttu-id="dcb1a-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="dcb1a-111">Symbolic Name</span></span>|<span data-ttu-id="dcb1a-112">InvalidBytePropertyValue</span><span class="sxs-lookup"><span data-stu-id="dcb1a-112">InvalidBytePropertyValue</span></span>|  
|<span data-ttu-id="dcb1a-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="dcb1a-113">Message Text</span></span>|<span data-ttu-id="dcb1a-114">La valeur de propriété octet n'est pas valide</span><span class="sxs-lookup"><span data-stu-id="dcb1a-114">The byte property value is not valid</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="dcb1a-115">Explication</span><span class="sxs-lookup"><span data-stu-id="dcb1a-115">Explanation</span></span>  
 <span data-ttu-id="dcb1a-116">Cet événement d'erreur/d'avertissement/d'informations indique qu'une valeur entrée pour une propriété d'une ligne dans la boîte de dialogue Filtre par lot est non valide, car la propriété requiert une valeur en octet et la valeur qui a été entrée n'est pas de ce type.</span><span class="sxs-lookup"><span data-stu-id="dcb1a-116">This Error/Warning/Information event indicates that a value entered for a property in a row of the Batch Filter dialog box was invalid, because the property required a byte value, but the value entered was not a byte.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="dcb1a-117">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="dcb1a-117">User Action</span></span>  
 <span data-ttu-id="dcb1a-118">Pour résoudre cette erreur, dans la boîte de dialogue Propriétés EDI, dans la page Paramètres de création de lots d'échange, ouvrez la boîte de dialogue Filtre par lot.</span><span class="sxs-lookup"><span data-stu-id="dcb1a-118">To resolve this error, open the Batch Filter dialog box from within the Interchange Batch Creation Settings page of the EDI Properties dialog box.</span></span> <span data-ttu-id="dcb1a-119">Vérifiez que la valeur entrée pour une propriété demandant une valeur en octet est appropriée.</span><span class="sxs-lookup"><span data-stu-id="dcb1a-119">Make sure that the value entered for a property that requires a byte value is in fact a byte.</span></span>