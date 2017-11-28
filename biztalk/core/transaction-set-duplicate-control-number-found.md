---
title: "Numéro de contrôle dupliqué transaction trouvée | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1b2779a0-b365-4c4b-81c7-8f9284748b6e
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fe63d3814bcce178164054ab8dcf673eeb4f395a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="transaction-set-duplicate-control-number-found"></a><span data-ttu-id="5dd43-102">Numéro de contrôle dupliqué du document informatisé trouvé</span><span class="sxs-lookup"><span data-stu-id="5dd43-102">Transaction Set duplicate control number found</span></span>
## <a name="details"></a><span data-ttu-id="5dd43-103">Détails</span><span class="sxs-lookup"><span data-stu-id="5dd43-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5dd43-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="5dd43-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="5dd43-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="5dd43-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="5dd43-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="5dd43-106">Event ID</span></span>|-|  
|<span data-ttu-id="5dd43-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="5dd43-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="5dd43-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="5dd43-108"> EDI</span></span>|  
|<span data-ttu-id="5dd43-109">Composant</span><span class="sxs-lookup"><span data-stu-id="5dd43-109">Component</span></span>|<span data-ttu-id="5dd43-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="5dd43-110">EDI Engine</span></span>|  
|<span data-ttu-id="5dd43-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="5dd43-111">Symbolic Name</span></span>|<span data-ttu-id="5dd43-112">X12TsDuplicateNumberFoundDescription</span><span class="sxs-lookup"><span data-stu-id="5dd43-112">X12TsDuplicateNumberFoundDescription</span></span>|  
|<span data-ttu-id="5dd43-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="5dd43-113">Message Text</span></span>|<span data-ttu-id="5dd43-114">Numéro de contrôle dupliqué du document informatisé trouvé</span><span class="sxs-lookup"><span data-stu-id="5dd43-114">Transaction Set duplicate control number found</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="5dd43-115">Explication</span><span class="sxs-lookup"><span data-stu-id="5dd43-115">Explanation</span></span>  
 <span data-ttu-id="5dd43-116">Cet événement de type erreur/avertissement/information indique que le pipeline de réception n'a pas pu traiter l'échange X12 entrant, car le numéro de contrôle d'un document informatisé d'un groupe de cet échange était le même que celui d'un autre document informatisé de ce groupe.</span><span class="sxs-lookup"><span data-stu-id="5dd43-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming X12 interchange because the transaction set control number for a transaction set in a group of that interchange was the same as the control number for another transaction set in that group.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="5dd43-117">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="5dd43-117">User Action</span></span>  
 <span data-ttu-id="5dd43-118">Pour résoudre cette erreur, effectuez l’une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="5dd43-118">To resolve this error, do one of the following:</span></span>  
  
-   <span data-ttu-id="5dd43-119">Modifiez les numéros de contrôle des documents informatisés dans l'échange entrant de sorte qu'il n'y ait plus de numéros de contrôle en double pour les documents informatisés dans un groupe.</span><span class="sxs-lookup"><span data-stu-id="5dd43-119">Change the transaction set control numbers of transaction sets in incoming interchange so there are no duplicate control numbers for transaction sets in a group.</span></span>  
  
-   <span data-ttu-id="5dd43-120">Désactivez la vérification de numéros de contrôle de documents informatisés en double, comme suit :</span><span class="sxs-lookup"><span data-stu-id="5dd43-120">Disable the check for duplicate transaction set control numbers as follows:</span></span>  
  
    1.  <span data-ttu-id="5dd43-121">Ouvrez la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="5dd43-121">Open the BizTalk Server Administration Console.</span></span>  
  
    2.  <span data-ttu-id="5dd43-122">Ouvrez la boîte de dialogue Propriétés EDI du tiers qui a envoyé l'échange.</span><span class="sxs-lookup"><span data-stu-id="5dd43-122">Open the EDI Properties dialog box for the party that sent the interchange.</span></span>  
  
    3.  <span data-ttu-id="5dd43-123">Pour les échanges X12, désactivez « Vérifiez qu'aucun doublon n'existe pour ST2 (numéro de contrôle du document informatisé) dans le groupe » dans la page Propriétés du processus d'échange X12 de la boîte de dialogue Propriétés EDI.</span><span class="sxs-lookup"><span data-stu-id="5dd43-123">For X12 interchanges, clear the "Check for duplicate ST2 (Transaction set control number) in group" in the X12 Interchange Processing Properties Page of the EDI Properties dialog box.</span></span>  
  
    4.  <span data-ttu-id="5dd43-124">Pour les échanges EDIFACT, désactivez « Vérifiez qu'aucun doublon n'existe pour UNH1 (numéro de contrôle du document informatisé) dans le groupe » dans la page Propriétés du traitement de l'échange EDIFACT de la boîte de dialogue Propriétés EDI.</span><span class="sxs-lookup"><span data-stu-id="5dd43-124">For EDIFACT interchanges, clear the "Check for duplicate UNH1 (Transaction set reference number) in group" property in the EDIFACT Interchange Processing Properties Page of the EDI Properties dialog box.</span></span>