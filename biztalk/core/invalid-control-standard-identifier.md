---
title: "Identificateur Standard de contrôle non valide | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3d2b5a54-7f29-49c9-8bcf-a5b4b6d07ad3
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 94975e63d5781200ee1bfd9d14896c1e5fe722a5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="invalid-control-standard-identifier"></a><span data-ttu-id="9e333-102">Identificateur standard de contrôle non valide</span><span class="sxs-lookup"><span data-stu-id="9e333-102">Invalid Control Standard Identifier</span></span>
## <a name="details"></a><span data-ttu-id="9e333-103">Détails</span><span class="sxs-lookup"><span data-stu-id="9e333-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9e333-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="9e333-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="9e333-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="9e333-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="9e333-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="9e333-106">Event ID</span></span>|-|  
|<span data-ttu-id="9e333-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="9e333-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="9e333-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="9e333-108"> EDI</span></span>|  
|<span data-ttu-id="9e333-109">Composant</span><span class="sxs-lookup"><span data-stu-id="9e333-109">Component</span></span>|<span data-ttu-id="9e333-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="9e333-110">EDI Engine</span></span>|  
|<span data-ttu-id="9e333-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="9e333-111">Symbolic Name</span></span>|<span data-ttu-id="9e333-112">X12Ta1InvalidControlStandardIdentifierDescription</span><span class="sxs-lookup"><span data-stu-id="9e333-112">X12Ta1InvalidControlStandardIdentifierDescription</span></span>|  
|<span data-ttu-id="9e333-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="9e333-113">Message Text</span></span>|<span data-ttu-id="9e333-114">Identificateur standard de contrôle non valide</span><span class="sxs-lookup"><span data-stu-id="9e333-114">Invalid Control Standard Identifier</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="9e333-115">Explication</span><span class="sxs-lookup"><span data-stu-id="9e333-115">Explanation</span></span>  
 <span data-ttu-id="9e333-116">Cet événement de type erreur/avertissement/information indique que le pipeline de réception n'a pas pu traiter l'échange entrant, car la valeur de l'identificateur de normes de contrôle d'échange (champ ISA11) dans l'échange ne correspondait pas à une entrée de l'énumération spécifiée par le schéma.</span><span class="sxs-lookup"><span data-stu-id="9e333-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange because the value of the interchange control standards identifier (field ISA11) in the interchange did not match an entry in the enumeration specified by the schema.</span></span> <span data-ttu-id="9e333-117">Le schéma est X12ServiceSchema ou EdifactServiceSchema dans BaseArtifacts.dll.</span><span class="sxs-lookup"><span data-stu-id="9e333-117">The schema is the X12ServiceSchema or the EdifactServiceSchema in BaseArtifacts.dll.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="9e333-118">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="9e333-118">User Action</span></span>  
 <span data-ttu-id="9e333-119">Pour résoudre cette erreur, assurez-vous que l'identificateur de normes de contrôle d'échange utilisé dans l'échange correspond à une entrée de l'énumération pour le champ ISA11, puis procédez à un nouvel envoi de l'échange.</span><span class="sxs-lookup"><span data-stu-id="9e333-119">To resolve this error, make sure that the interchange control standards identifier used in the interchange matches an entry in the enumeration for the ISA11 field, and then have the interchange resent.</span></span>