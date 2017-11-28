---
title: "Qualificateur d’autorisation non valide | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bc2a9f83-833f-4ea0-9421-7382ee1b1a54
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dbf33e8bd42b18134bd31f02f791b306ece97272
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="invalid-authorization-qualifier"></a><span data-ttu-id="b5977-102">Qualificateur d'autorisation non valide</span><span class="sxs-lookup"><span data-stu-id="b5977-102">Invalid Authorization Qualifier</span></span>
## <a name="details"></a><span data-ttu-id="b5977-103">Détails</span><span class="sxs-lookup"><span data-stu-id="b5977-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b5977-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="b5977-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="b5977-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="b5977-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="b5977-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="b5977-106">Event ID</span></span>|-|  
|<span data-ttu-id="b5977-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="b5977-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="b5977-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="b5977-108"> EDI</span></span>|  
|<span data-ttu-id="b5977-109">Composant</span><span class="sxs-lookup"><span data-stu-id="b5977-109">Component</span></span>|<span data-ttu-id="b5977-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="b5977-110">EDI Engine</span></span>|  
|<span data-ttu-id="b5977-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="b5977-111">Symbolic Name</span></span>|<span data-ttu-id="b5977-112">X12Ta1InvalidAuthorizationQualifierDescription</span><span class="sxs-lookup"><span data-stu-id="b5977-112">X12Ta1InvalidAuthorizationQualifierDescription</span></span>|  
|<span data-ttu-id="b5977-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="b5977-113">Message Text</span></span>|<span data-ttu-id="b5977-114">Qualificateur d'autorisation non valide</span><span class="sxs-lookup"><span data-stu-id="b5977-114">Invalid Authorization Qualifier</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="b5977-115">Explication</span><span class="sxs-lookup"><span data-stu-id="b5977-115">Explanation</span></span>  
 <span data-ttu-id="b5977-116">Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline de réception n'a pas pu traiter l'échange entrant car la valeur du qualificateur d'autorisation dans ISA01 ne correspond à aucune des valeurs d'énumération spécifiées par le schéma.</span><span class="sxs-lookup"><span data-stu-id="b5977-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange because the value of the Authorization Qualifier in ISA01 did not match any of the enumeration values specified by the schema.</span></span> <span data-ttu-id="b5977-117">Le schéma est le X12ServiceSchema dans BaseArtifacts.dll.</span><span class="sxs-lookup"><span data-stu-id="b5977-117">The schema is the X12ServiceSchema in BaseArtifacts.dll.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="b5977-118">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="b5977-118">User Action</span></span>  
 <span data-ttu-id="b5977-119">Pour résoudre cette erreur, assurez-vous que la valeur de l'en-tête ISA02 est conforme à l'une des valeurs d'énumération spécifiées par le schéma X12ServiceSchema, puis demandez à l'expéditeur de renvoyer l'échange.</span><span class="sxs-lookup"><span data-stu-id="b5977-119">To resolve this error, make sure that the value in the ISA01 header matches one of the enumeration values specified by the X12ServiceSchema, and then have the interchange resent.</span></span>