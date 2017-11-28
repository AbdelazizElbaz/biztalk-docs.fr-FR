---
title: "La valeur ne peut pas être vide ou null pour un opérateur autre qu’Exists. | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 44de42c8-eab7-4b13-b55a-d33eabe75c52
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5b5e257b78df8bf872764542d711637d33714349
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-value-cannot-be-empty-or-null-for-an-operator-other-than-exists"></a><span data-ttu-id="fe978-102">Cette valeur ne peut pas être vide ou null pour un opérateur autre qu'Exists.</span><span class="sxs-lookup"><span data-stu-id="fe978-102">The value cannot be empty or null for an operator other than Exists</span></span>
## <a name="details"></a><span data-ttu-id="fe978-103">Détails</span><span class="sxs-lookup"><span data-stu-id="fe978-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="fe978-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="fe978-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="fe978-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="fe978-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="fe978-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="fe978-106">Event ID</span></span>|-|  
|<span data-ttu-id="fe978-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="fe978-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="fe978-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="fe978-108"> EDI</span></span>|  
|<span data-ttu-id="fe978-109">Composant</span><span class="sxs-lookup"><span data-stu-id="fe978-109">Component</span></span>|<span data-ttu-id="fe978-110">Moteur de traitement par lot</span><span class="sxs-lookup"><span data-stu-id="fe978-110">Batching Engine</span></span>|  
|<span data-ttu-id="fe978-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="fe978-111">Symbolic Name</span></span>|<span data-ttu-id="fe978-112">ValueCannotBeNullOrEmpty</span><span class="sxs-lookup"><span data-stu-id="fe978-112">ValueCannotBeNullOrEmpty</span></span>|  
|<span data-ttu-id="fe978-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="fe978-113">Message Text</span></span>|<span data-ttu-id="fe978-114">Cette valeur ne peut pas être vide ou null pour un opérateur autre qu'Exists.</span><span class="sxs-lookup"><span data-stu-id="fe978-114">The value cannot be empty or null for an operator other than Exists</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="fe978-115">Explication</span><span class="sxs-lookup"><span data-stu-id="fe978-115">Explanation</span></span>  
 <span data-ttu-id="fe978-116">Cet événement de type erreur/avertissement/information indique qu'une valeur entrée pour une propriété sur une ligne de la boîte de dialogue Filtre par lot n'était pas valide, car l'opérateur n'était pas Exists, mais la valeur entrée était vide ou nulle.</span><span class="sxs-lookup"><span data-stu-id="fe978-116">This Error/Warning/Information event indicates that a value entered for a property in a row of the Batch Filter dialog box was invalid, because the operator was not Exists, but the value entered was either empty or null.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="fe978-117">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="fe978-117">User Action</span></span>  
 <span data-ttu-id="fe978-118">Pour résoudre cette erreur, dans la boîte de dialogue Propriétés EDI, dans la page Paramètres de création de lots d'échange, ouvrez la boîte de dialogue Filtre par lot.</span><span class="sxs-lookup"><span data-stu-id="fe978-118">To resolve this error, open the Batch Filter dialog box from within the Interchange Batch Creation Settings page of the EDI Properties dialog box.</span></span> <span data-ttu-id="fe978-119">Si l'opérateur d'une ligne n'est pas Exists, faites en sorte que la valeur entrée ne soit ni vide ni nulle.</span><span class="sxs-lookup"><span data-stu-id="fe978-119">Make sure that if the operator for a row is not Exists, the value entered is neither empty nor null.</span></span>