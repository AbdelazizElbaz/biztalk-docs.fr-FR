---
title: "Erreur rencontrée après le traitement de Transaction Set(s) car DocType n’a pas été définie. | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a323658c-77d8-4059-aa15-d88c08e5450d
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 874b0229eecdd5fe9c046f69789c4708b9280031
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error-encountered-after-processing-transaction-sets-because-doctype-was-not-set"></a><span data-ttu-id="5c914-102">Erreur rencontrée après le traitement de document(s) informatisé(s) car DocType n'a pas été défini</span><span class="sxs-lookup"><span data-stu-id="5c914-102">Error encountered after processing Transaction Set(s) because DocType was not set</span></span>
## <a name="details"></a><span data-ttu-id="5c914-103">Détails</span><span class="sxs-lookup"><span data-stu-id="5c914-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5c914-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="5c914-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="5c914-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="5c914-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="5c914-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="5c914-106">Event ID</span></span>|-|  
|<span data-ttu-id="5c914-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="5c914-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="5c914-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="5c914-108"> EDI</span></span>|  
|<span data-ttu-id="5c914-109">Composant</span><span class="sxs-lookup"><span data-stu-id="5c914-109">Component</span></span>|<span data-ttu-id="5c914-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="5c914-110">EDI Engine</span></span>|  
|<span data-ttu-id="5c914-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="5c914-111">Symbolic Name</span></span>|<span data-ttu-id="5c914-112">DocTypeNotSet</span><span class="sxs-lookup"><span data-stu-id="5c914-112">DocTypeNotSet</span></span>|  
|<span data-ttu-id="5c914-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="5c914-113">Message Text</span></span>|<span data-ttu-id="5c914-114">Erreur rencontrée après le traitement de {0} document(s) informatisé(s).</span><span class="sxs-lookup"><span data-stu-id="5c914-114">Error encountered after processing {0} Transaction Set(s).</span></span> <span data-ttu-id="5c914-115">Le type de document n'a pas été défini</span><span class="sxs-lookup"><span data-stu-id="5c914-115">DocType was not set</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="5c914-116">Explication</span><span class="sxs-lookup"><span data-stu-id="5c914-116">Explanation</span></span>  
 <span data-ttu-id="5c914-117">Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline de réception EDI n'a pas pu traiter un document informatisé entrant car STO1 (pour un échange X12) ou UNH2.1 (pour un échange EDIFACT) n'est pas défini pour le document informatisé.</span><span class="sxs-lookup"><span data-stu-id="5c914-117">This Error/Warning/Information event indicates that the EDI receive pipeline could not process an incoming transaction set because ST01 (for an X12 interchange) or UNH2.1 (for an EDIFACT interchange) was not set for the transaction set.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="5c914-118">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="5c914-118">User Action</span></span>  
 <span data-ttu-id="5c914-119">Pour résoudre cette erreur, vérifiez que le segment ST01 ou UNH1 pour le document informatisé indiqué dans l'erreur est défini sur un type de document valide.</span><span class="sxs-lookup"><span data-stu-id="5c914-119">To resolve this error, verify that the ST01 or UNH1 segment for the transaction set in error is set to a valid document type.</span></span>