---
title: "Qualificateur de l’ID d’expéditeur non valide | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cfe9c51c-d569-4f14-a690-f145ef1bf6a4
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7b3192a21965360f6e10d7eb9a0a2ec7755d71e7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="invalid-senderid-qualifier"></a><span data-ttu-id="f3d06-102">Qualificateur d'ID d'expéditeur non valide</span><span class="sxs-lookup"><span data-stu-id="f3d06-102">Invalid SenderId Qualifier</span></span>
## <a name="details"></a><span data-ttu-id="f3d06-103">Détails</span><span class="sxs-lookup"><span data-stu-id="f3d06-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f3d06-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="f3d06-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="f3d06-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="f3d06-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="f3d06-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="f3d06-106">Event ID</span></span>|-|  
|<span data-ttu-id="f3d06-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="f3d06-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="f3d06-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="f3d06-108"> EDI</span></span>|  
|<span data-ttu-id="f3d06-109">Composant</span><span class="sxs-lookup"><span data-stu-id="f3d06-109">Component</span></span>|<span data-ttu-id="f3d06-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="f3d06-110">EDI Engine</span></span>|  
|<span data-ttu-id="f3d06-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="f3d06-111">Symbolic Name</span></span>|<span data-ttu-id="f3d06-112">X12Ta1InvalidSenderIdQualifierDescription</span><span class="sxs-lookup"><span data-stu-id="f3d06-112">X12Ta1InvalidSenderIdQualifierDescription</span></span>|  
|<span data-ttu-id="f3d06-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="f3d06-113">Message Text</span></span>|<span data-ttu-id="f3d06-114">Qualificateur d'ID d'expéditeur non valide</span><span class="sxs-lookup"><span data-stu-id="f3d06-114">Invalid SenderId Qualifier</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="f3d06-115">Explication</span><span class="sxs-lookup"><span data-stu-id="f3d06-115">Explanation</span></span>  
 <span data-ttu-id="f3d06-116">Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline de réception n'a pas pu traiter l'échange entrant, car le qualificateur d'expéditeur dans le champ ISA05 (pour un échange X12) ou le qualificateur d'expéditeur des échanges dans le champ UNB2.2 (pour un échange EDIFACT) ne correspond à aucune valeur de l'énumération établie par le schéma de service (X12ServiceSchema ou le EdifactServiceSchema dans BaseArtifacts.dll).</span><span class="sxs-lookup"><span data-stu-id="f3d06-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange because the Sender Qualifier in the ISA05 field (for an X12 interchange) or the Sender Code Qualifier in the UNB2.2 field (for an EDIFACT interchange) did not match a value in the enumeration established by the service schema (X12ServiceSchema or the EdifactServiceSchema in BaseArtifacts.dll).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="f3d06-117">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="f3d06-117">User Action</span></span>  
 <span data-ttu-id="f3d06-118">Pour résoudre cette erreur, assurez-vous que le champ ISA07 ou UNB3.2 correspond à l'une des valeurs de l'énumération établie par le schéma de service.</span><span class="sxs-lookup"><span data-stu-id="f3d06-118">To resolve this error, make sure that the ISA07 field or the UNB3.2 field matches one of the values in the enumeration established by the service schema.</span></span> <span data-ttu-id="f3d06-119">Demandez à l'expéditeur de renvoyer l'échange.</span><span class="sxs-lookup"><span data-stu-id="f3d06-119">Have the interchange resent.</span></span>