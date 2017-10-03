---
title: "Qualificateur d’ID de destinataire non valide | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 52d60f7e-6f16-424d-91b8-dc8181206249
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 86c9adc1fa20f244d1061b67878e433d73dfa72d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="invalid-receiverid-qualifier"></a><span data-ttu-id="97284-102">Qualificateur d'ID de destinataire non valide</span><span class="sxs-lookup"><span data-stu-id="97284-102">Invalid ReceiverId Qualifier</span></span>
## <a name="details"></a><span data-ttu-id="97284-103">Détails</span><span class="sxs-lookup"><span data-stu-id="97284-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="97284-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="97284-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="97284-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="97284-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="97284-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="97284-106">Event ID</span></span>|-|  
|<span data-ttu-id="97284-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="97284-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="97284-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="97284-108"> EDI</span></span>|  
|<span data-ttu-id="97284-109">Composant</span><span class="sxs-lookup"><span data-stu-id="97284-109">Component</span></span>|<span data-ttu-id="97284-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="97284-110">EDI Engine</span></span>|  
|<span data-ttu-id="97284-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="97284-111">Symbolic Name</span></span>|<span data-ttu-id="97284-112">X12Ta1InvalidReceiverIdQualifierDescription</span><span class="sxs-lookup"><span data-stu-id="97284-112">X12Ta1InvalidReceiverIdQualifierDescription</span></span>|  
|<span data-ttu-id="97284-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="97284-113">Message Text</span></span>|<span data-ttu-id="97284-114">Qualificateur d'ID de destinataire non valide</span><span class="sxs-lookup"><span data-stu-id="97284-114">Invalid ReceiverId Qualifier</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="97284-115">Explication</span><span class="sxs-lookup"><span data-stu-id="97284-115">Explanation</span></span>  
 <span data-ttu-id="97284-116">Cet événement de type erreur/avertissement/information indique que le pipeline de réception n'a pas pu traiter l'échange entrant, car le qualificateur du récepteur du champ ISA07 (pour un échange X12) ou le qualificateur de code du récepteur dans le champ UNB3.2 (pour un échange EDIFACT) n'était pas conforme à une valeur dans l'énumération établie par le schéma de service (X12ServiceSchema ou EdifactServiceSchema dans BaseArtifacts.dll).</span><span class="sxs-lookup"><span data-stu-id="97284-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange because the Receiver Qualifier in the ISA07 field (for an X12 interchange) or the Recipient Code Qualifier in the UNB3.2 field (for an EDIFACT interchange) did not match a value in the enumeration established by the service schema (X12ServiceSchema or the EdifactServiceSchema in BaseArtifacts.dll).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="97284-117">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="97284-117">User Action</span></span>  
 <span data-ttu-id="97284-118">Pour résoudre cette erreur, assurez-vous que le champ ISA07 ou UNB3.2 correspond à l'une des valeurs de l'énumération établie par le schéma de service.</span><span class="sxs-lookup"><span data-stu-id="97284-118">To resolve this error, make sure that the ISA07 field or the UNB3.2 field matches one of the values in the enumeration established by the service schema.</span></span> <span data-ttu-id="97284-119">Demandez à l'expéditeur de renvoyer l'échange.</span><span class="sxs-lookup"><span data-stu-id="97284-119">Have the interchange resent.</span></span>