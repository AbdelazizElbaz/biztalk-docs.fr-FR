---
title: "Document informatisé non pris en charge | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5ffe8528-f34f-4189-8ee6-4ae1afb50c92
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 751b4bdff008a191a2367faea62fa92b6c15011b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="transaction-set-not-supported"></a><span data-ttu-id="404b4-102">Document informatisé non pris en charge</span><span class="sxs-lookup"><span data-stu-id="404b4-102">Transaction Set Not Supported</span></span>
## <a name="details"></a><span data-ttu-id="404b4-103">Détails</span><span class="sxs-lookup"><span data-stu-id="404b4-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="404b4-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="404b4-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="404b4-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="404b4-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="404b4-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="404b4-106">Event ID</span></span>|-|  
|<span data-ttu-id="404b4-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="404b4-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="404b4-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="404b4-108"> EDI</span></span>|  
|<span data-ttu-id="404b4-109">Composant</span><span class="sxs-lookup"><span data-stu-id="404b4-109">Component</span></span>|<span data-ttu-id="404b4-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="404b4-110">EDI Engine</span></span>|  
|<span data-ttu-id="404b4-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="404b4-111">Symbolic Name</span></span>|<span data-ttu-id="404b4-112">X12TsNotSupportedDescription</span><span class="sxs-lookup"><span data-stu-id="404b4-112">X12TsNotSupportedDescription</span></span>|  
|<span data-ttu-id="404b4-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="404b4-113">Message Text</span></span>|<span data-ttu-id="404b4-114">Document informatisé non pris en charge</span><span class="sxs-lookup"><span data-stu-id="404b4-114">Transaction Set Not Supported</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="404b4-115">Explication</span><span class="sxs-lookup"><span data-stu-id="404b4-115">Explanation</span></span>  
 <span data-ttu-id="404b4-116">Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline de réception n'a pas pu traiter l'échange entrant, car un schéma de document n'a pas été déployé pour le type du document informatisé.</span><span class="sxs-lookup"><span data-stu-id="404b4-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange because a document schema has not been deployed for the document type of that transaction set.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="404b4-117">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="404b4-117">User Action</span></span>  
 <span data-ttu-id="404b4-118">Pour résoudre cette erreur, dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], déployez un schéma de document pour le type du document informatisé.</span><span class="sxs-lookup"><span data-stu-id="404b4-118">To resolve this error, in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] deploy a document schema for the document type of the transaction set.</span></span>