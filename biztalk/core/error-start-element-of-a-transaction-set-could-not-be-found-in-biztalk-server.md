---
title: "Erreur rencontrée après le traitement de Transaction Set(s), car il est impossible de trouver l’élément de début d’un document informatisé | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d5380aee-1632-4cdf-98a1-aff87574ce4f
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 224b08046d1733aa8426909d7dddac4b10e48c8e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error-encountered-after-processing-transaction-sets-because-the-start-element-of-a-transaction-set-could-not-be-found"></a><span data-ttu-id="1a8d6-102">Erreur rencontrée après le traitement de document(s) informatisé(s) car l'élément de départ d'un document informatisé n'a pas pu être trouvé</span><span class="sxs-lookup"><span data-stu-id="1a8d6-102">Error encountered after processing Transaction Set(s) because the Start element of a Transaction set could not be found</span></span>
## <a name="details"></a><span data-ttu-id="1a8d6-103">Détails</span><span class="sxs-lookup"><span data-stu-id="1a8d6-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1a8d6-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="1a8d6-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="1a8d6-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="1a8d6-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="1a8d6-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="1a8d6-106">Event ID</span></span>|-|  
|<span data-ttu-id="1a8d6-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="1a8d6-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="1a8d6-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="1a8d6-108"> EDI</span></span>|  
|<span data-ttu-id="1a8d6-109">Composant</span><span class="sxs-lookup"><span data-stu-id="1a8d6-109">Component</span></span>|<span data-ttu-id="1a8d6-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="1a8d6-110">EDI Engine</span></span>|  
|<span data-ttu-id="1a8d6-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="1a8d6-111">Symbolic Name</span></span>|<span data-ttu-id="1a8d6-112">InvalidEfactBiboXmlFormat</span><span class="sxs-lookup"><span data-stu-id="1a8d6-112">InvalidEfactBiboXmlFormat</span></span>|  
|<span data-ttu-id="1a8d6-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="1a8d6-113">Message Text</span></span>|<span data-ttu-id="1a8d6-114">Erreur rencontrée après le traitement de {0} document(s) informatisé(s).</span><span class="sxs-lookup"><span data-stu-id="1a8d6-114">Error encountered after processing {0} Transaction Set(s).</span></span> <span data-ttu-id="1a8d6-115">L'élément de départ d'un document informatisé n'a pas pu être trouvé.</span><span class="sxs-lookup"><span data-stu-id="1a8d6-115">Start element of a Transaction set could not be found.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="1a8d6-116">Explication</span><span class="sxs-lookup"><span data-stu-id="1a8d6-116">Explanation</span></span>  
 <span data-ttu-id="1a8d6-117">Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline de réception EDI n'a pas pu traiter un document informatisé entrant, car le pipeline de réception n'a pas réussi à trouver l'en-tête ST ou UNH.</span><span class="sxs-lookup"><span data-stu-id="1a8d6-117">This Error/Warning/Information event indicates that the EDI receive pipeline could not process an incoming transaction set because the receive pipeline could not find the ST or UNH header.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="1a8d6-118">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="1a8d6-118">User Action</span></span>  
 <span data-ttu-id="1a8d6-119">Pour résoudre cette erreur, contactez l'expéditeur de l'échange et demandez-lui de s'assurer que le document informatisé erroné commence par un segment ST01 ou UNH1.</span><span class="sxs-lookup"><span data-stu-id="1a8d6-119">To resolve this error, contact the sender of the interchange, and have them ensure that the transaction set in error begins with an ST01 or UNH1 segment.</span></span>