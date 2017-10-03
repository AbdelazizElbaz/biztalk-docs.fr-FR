---
title: "Qualificateur de sécurité non valide | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dce36f4b-ab59-41c0-8b92-3020f6393db9
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3f4d16b4295bd8d01f93db964d4e45e8363205ee
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="invalid-security-qualifier"></a><span data-ttu-id="effa0-102">Qualificateur de sécurité non valide</span><span class="sxs-lookup"><span data-stu-id="effa0-102">Invalid Security Qualifier</span></span>
## <a name="details"></a><span data-ttu-id="effa0-103">Détails</span><span class="sxs-lookup"><span data-stu-id="effa0-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="effa0-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="effa0-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="effa0-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="effa0-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="effa0-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="effa0-106">Event ID</span></span>|-|  
|<span data-ttu-id="effa0-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="effa0-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="effa0-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="effa0-108"> EDI</span></span>|  
|<span data-ttu-id="effa0-109">Composant</span><span class="sxs-lookup"><span data-stu-id="effa0-109">Component</span></span>|<span data-ttu-id="effa0-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="effa0-110">EDI Engine</span></span>|  
|<span data-ttu-id="effa0-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="effa0-111">Symbolic Name</span></span>|<span data-ttu-id="effa0-112">X12Ta1InvalidSecurityQualifierDescription</span><span class="sxs-lookup"><span data-stu-id="effa0-112">X12Ta1InvalidSecurityQualifierDescription</span></span>|  
|<span data-ttu-id="effa0-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="effa0-113">Message Text</span></span>|<span data-ttu-id="effa0-114">Qualificateur de sécurité non valide</span><span class="sxs-lookup"><span data-stu-id="effa0-114">Invalid Security Qualifier</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="effa0-115">Explication</span><span class="sxs-lookup"><span data-stu-id="effa0-115">Explanation</span></span>  
 <span data-ttu-id="effa0-116">Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline de réception n'a pas pu traiter l'échange entrant, car le qualificateur de sécurité dans le champ ISA03 ou le qualificateur du mot de passe du destinataire dans le champ UNB6.2 ne correspond à aucune valeur de l'énumération établie par le schéma de service (X12ServiceSchema ou EdifactServiceSchema dans BaseArtifacts.dll).</span><span class="sxs-lookup"><span data-stu-id="effa0-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange because the Security Qualifier in the ISA03 field or the Recipient Reference Password Qualifier in the UNB6.2 field did not match a value in the enumeration established by the service schema (X12ServiceSchema or the EdifactServiceSchema in BaseArtifacts.dll).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="effa0-117">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="effa0-117">User Action</span></span>  
 <span data-ttu-id="effa0-118">Pour résoudre cette erreur, assurez-vous que le champ ISA03 ou UNB6.2 correspond à l'une des valeurs de l'énumération établie par le schéma de service.</span><span class="sxs-lookup"><span data-stu-id="effa0-118">To resolve this error, make sure that the ISA03 field or the UNB6.2 field matches one of the values in the enumeration established by the service schema.</span></span> <span data-ttu-id="effa0-119">Demandez à l'expéditeur de renvoyer l'échange.</span><span class="sxs-lookup"><span data-stu-id="effa0-119">Have the interchange resent.</span></span>