---
title: "Identificateur du jeu de transactions manquante ou non valide ou dupliquée | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8580aab2-9fa4-43fb-b643-10621926591e
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 75251d0210be4ed34a74ba0f3f5cadf84d9941b8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="missing-or-invalid-or-duplicate-transaction-set-identifier"></a><span data-ttu-id="c8c95-102">Identificateur du jeu de transactions manquante ou non valide ou en double</span><span class="sxs-lookup"><span data-stu-id="c8c95-102">Missing or invalid or duplicate Transaction set identifier</span></span>
## <a name="details"></a><span data-ttu-id="c8c95-103">Détails</span><span class="sxs-lookup"><span data-stu-id="c8c95-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c8c95-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="c8c95-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="c8c95-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="c8c95-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="c8c95-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="c8c95-106">Event ID</span></span>|-|  
|<span data-ttu-id="c8c95-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="c8c95-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="c8c95-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="c8c95-108"> EDI</span></span>|  
|<span data-ttu-id="c8c95-109">Composant</span><span class="sxs-lookup"><span data-stu-id="c8c95-109">Component</span></span>|<span data-ttu-id="c8c95-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="c8c95-110">EDI Engine</span></span>|  
|<span data-ttu-id="c8c95-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="c8c95-111">Symbolic Name</span></span>|<span data-ttu-id="c8c95-112">X12TsMissingOrInvalidTsIdentiferDescription2</span><span class="sxs-lookup"><span data-stu-id="c8c95-112">X12TsMissingOrInvalidTsIdentiferDescription2</span></span>|  
|<span data-ttu-id="c8c95-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="c8c95-113">Message Text</span></span>|<span data-ttu-id="c8c95-114">Identificateur de document informatisé « {0} » manquant, non valide ou dupliqué</span><span class="sxs-lookup"><span data-stu-id="c8c95-114">Missing or invalid or duplicate Transaction set identifier '{0}'</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="c8c95-115">Explication</span><span class="sxs-lookup"><span data-stu-id="c8c95-115">Explanation</span></span>  
 <span data-ttu-id="c8c95-116">Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline de réception ou d'envoi n'a pas réussi à traiter l'échange X12 car la valeur de l'identificateur de document informatisé (champ ST01) était manquante, dupliquée ou non valide.</span><span class="sxs-lookup"><span data-stu-id="c8c95-116">This Error/Warning/Information event indicates that the receive or send pipeline could not process the X12 interchange because the value of the transaction set identifier (in the ST01 field) was missing, a duplicate, or had an invalid value.</span></span> <span data-ttu-id="c8c95-117">Cette erreur se produit si le schéma de document ne possède pas d'en-tête ST ni de code de fin SE.</span><span class="sxs-lookup"><span data-stu-id="c8c95-117">This can occur if the document schema does not have an ST header and an SE trailer.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="c8c95-118">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="c8c95-118">User Action</span></span>  
 <span data-ttu-id="c8c95-119">Pour résoudre cette erreur, assurez-vous que le champ ST01 de l'échange possède une valeur et que le schéma dispose d'une entrée pour l'en-tête ST et le code de fin SE.</span><span class="sxs-lookup"><span data-stu-id="c8c95-119">To resolve this error, make sure that the interchange has a value for the ST01 field and that the schema has an entry for the ST header and SE trailer.</span></span> <span data-ttu-id="c8c95-120">Vérifiez que la valeur de ST01 est un indicateur de type de document à trois chiffres valide.</span><span class="sxs-lookup"><span data-stu-id="c8c95-120">Verify that the value of ST01 is a valid three-digit document-type designator.</span></span> <span data-ttu-id="c8c95-121">Vérifiez que le champ ST01 n'est pas un doublon du champ ST01 d'un autre document informatisé.</span><span class="sxs-lookup"><span data-stu-id="c8c95-121">Verify that the ST01 field is not a duplicate with the ST01 field of another transaction set.</span></span>