---
title: "Les paramètres de destinataire de groupe ne sont pas configurés pour l’accord de lot | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 57b205e9-aaab-43d1-b373-17d206957814
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8ea41ad5c8de88e446a86745b57ff282d5b90af5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-group-receiver-settings-are-not-configured-for-agreement-of-batch"></a><span data-ttu-id="0fcf7-102">Les paramètres de destinataire de groupe ne sont pas configurés pour l'accord de lot.</span><span class="sxs-lookup"><span data-stu-id="0fcf7-102">The group receiver settings are not configured for agreement of batch</span></span>
## <a name="details"></a><span data-ttu-id="0fcf7-103">Détails</span><span class="sxs-lookup"><span data-stu-id="0fcf7-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0fcf7-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="0fcf7-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="0fcf7-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="0fcf7-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="0fcf7-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="0fcf7-106">Event ID</span></span>|-|  
|<span data-ttu-id="0fcf7-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="0fcf7-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="0fcf7-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="0fcf7-108"> EDI</span></span>|  
|<span data-ttu-id="0fcf7-109">Composant</span><span class="sxs-lookup"><span data-stu-id="0fcf7-109">Component</span></span>|<span data-ttu-id="0fcf7-110">Moteur de traitement par lot</span><span class="sxs-lookup"><span data-stu-id="0fcf7-110">Batching Engine</span></span>|  
|<span data-ttu-id="0fcf7-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="0fcf7-111">Symbolic Name</span></span>|<span data-ttu-id="0fcf7-112">GroupReceiverNotSelected</span><span class="sxs-lookup"><span data-stu-id="0fcf7-112">GroupReceiverNotSelected</span></span>|  
|<span data-ttu-id="0fcf7-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="0fcf7-113">Message Text</span></span>|<span data-ttu-id="0fcf7-114">Les paramètres de destinataire de groupe ne sont pas configurés pour l'accord de lot {0}.</span><span class="sxs-lookup"><span data-stu-id="0fcf7-114">The group receiver settings are not configured for agreement of batch {0}.</span></span> <span data-ttu-id="0fcf7-115">Ils doivent être configurés pour permettre le traitement par lot.</span><span class="sxs-lookup"><span data-stu-id="0fcf7-115">This needs to be configured before batching can proceed.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="0fcf7-116">Explication</span><span class="sxs-lookup"><span data-stu-id="0fcf7-116">Explanation</span></span>  
 <span data-ttu-id="0fcf7-117">Cet événement de type erreur/avertissement/information indique qu'une condition sur deux possibles est vérifiée :</span><span class="sxs-lookup"><span data-stu-id="0fcf7-117">This Error/Warning/Information event indicates that one of two conditions has occurred:</span></span>  
  
-   <span data-ttu-id="0fcf7-118">L'orchestration du traitement par lot n'a pas pu valider un élément de lot reçu, car le champ UNB1.1 (pour un échange EDIFACT) qui contient la syntaxe d'encodage n'était pas défini.</span><span class="sxs-lookup"><span data-stu-id="0fcf7-118">The batching orchestration could not validate a batch element that it has received because the UNB1.1 field (for an EDIFACT-encoded interchange) that contains the encoding syntax was not set.</span></span>  
  
-   <span data-ttu-id="0fcf7-119">L'orchestration du traitement par lot n'a pas pu créer les paramètres d'enveloppe de l'élément de lot, car les propriétés de l'en-tête n'étaient pas complètes (propriétés ISA, GS et ST pour un échange X12  ou propriétés UNA, UNB, UNG  et UNH pour un échange EDIFACT).</span><span class="sxs-lookup"><span data-stu-id="0fcf7-119">The batching orchestration could not create the envelope settings for the batch element because the header properties were not complete (ISA, GS, and ST properties for an X12 interchange or UNA, UNB, UNG, and UNH properties for an EDIFACT interchange).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="0fcf7-120">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="0fcf7-120">User Action</span></span>  
 <span data-ttu-id="0fcf7-121">Pour résoudre cette erreur, effectuez l’une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="0fcf7-121">To resolve this error, do one of the following:</span></span>  
  
-   <span data-ttu-id="0fcf7-122">Si l'orchestration du traitement par lot n'a pas pu valider un élément de lot reçu parce que la syntaxe d'encodage n'était pas définie, définissez celle-ci pour le champ UNB1.1 sur la page Définition du segment UNB de la boîte de dialogue Propriétés EDI.</span><span class="sxs-lookup"><span data-stu-id="0fcf7-122">If the batching orchestration could not validate a batch element that it has received because the encoding syntax was not set, set the encoding syntax for the UNB1.1 field in the UNB Segment Definition page of the EDI Properties dialog box.</span></span>  
  
-   <span data-ttu-id="0fcf7-123">Si l'orchestration du traitement par lot n'a pas pu créer les paramètres d'enveloppe de l'élément de lot parce que les propriétés de l'en-tête n'étaient pas complètes, assurez-vous que les propriétés ISA, GS et ST pour un échange X12  (ou les propriétés UNA, UNB, UNG  et UNH pour un échange EDIFACT) sont définies.</span><span class="sxs-lookup"><span data-stu-id="0fcf7-123">If the batching orchestration could not create the envelope settings for the batch element because the header properties were not complete, ensure that the ISA, GS, and ST properties for an X12 interchange are set or that the UNA, UNB, UNG, and UNH properties for an EDIFACT interchange are set.</span></span>