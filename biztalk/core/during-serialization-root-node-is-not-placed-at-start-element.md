---
title: "Pendant la sérialisation nœud racine n’est pas placé au début de l’élément | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9ea4aa6f-0f9c-4b7b-b7f6-24a5ce954048
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b3dced7e36802dd9d9ec9620272fc8a96bd6b590
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="during-serialization-root-node-is-not-placed-at-start-element"></a><span data-ttu-id="c5da9-102">Lors de la sérialisation, le nœud racine n'est pas placé au niveau de l'élément de départ</span><span class="sxs-lookup"><span data-stu-id="c5da9-102">During serialization root node is not placed at start element</span></span>
## <a name="details"></a><span data-ttu-id="c5da9-103">Détails</span><span class="sxs-lookup"><span data-stu-id="c5da9-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c5da9-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="c5da9-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="c5da9-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="c5da9-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="c5da9-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="c5da9-106">Event ID</span></span>|-|  
|<span data-ttu-id="c5da9-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="c5da9-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="c5da9-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="c5da9-108"> EDI</span></span>|  
|<span data-ttu-id="c5da9-109">Composant</span><span class="sxs-lookup"><span data-stu-id="c5da9-109">Component</span></span>|<span data-ttu-id="c5da9-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="c5da9-110">EDI Engine</span></span>|  
|<span data-ttu-id="c5da9-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="c5da9-111">Symbolic Name</span></span>|-|  
|<span data-ttu-id="c5da9-112">Texte du message</span><span class="sxs-lookup"><span data-stu-id="c5da9-112">Message Text</span></span>|<span data-ttu-id="c5da9-113">Lors de la sérialisation, le nœud racine n'est pas placé au niveau de l'élément de départ</span><span class="sxs-lookup"><span data-stu-id="c5da9-113">During serialization root node is not placed at start element</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="c5da9-114">Explication</span><span class="sxs-lookup"><span data-stu-id="c5da9-114">Explanation</span></span>  
 <span data-ttu-id="c5da9-115">Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline de réception n'a pas pu traiter un échange entrant car le document informatisé ne commence pas par un en-tête ST ou UNH.</span><span class="sxs-lookup"><span data-stu-id="c5da9-115">This Error/Warning/Information event indicates that the receive pipeline could not process an incoming interchange because the transaction set does not start with an ST or UNH header.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="c5da9-116">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="c5da9-116">User Action</span></span>  
 <span data-ttu-id="c5da9-117">Pour résoudre cette erreur, assurez-vous que chaque document informatisé d'un échange commence par un segment ST (échanges X12) ou un segment UNH (échanges EDIFACT), puis renvoyez l'échange.</span><span class="sxs-lookup"><span data-stu-id="c5da9-117">To resolve this error, ensure that each of the transaction sets in an interchange starts with an ST segment (for X12 interchanges) or an UNH segment (for EDIFACT interchanges), and then resubmit the interchange.</span></span>