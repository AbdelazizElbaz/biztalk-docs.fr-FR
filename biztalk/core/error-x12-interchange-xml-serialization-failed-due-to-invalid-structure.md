---
title: "Échec de la sérialisation XML de l'échange X12 dû à une structure incorrecte. Recherche de TransactionSet ou GE, mais introuvable | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d058fdbb-6be5-499f-86f7-0eb8a85c5fb2
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b3d4081c901e95dbd1b9911b2cd957dbe7319761
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="x12-interchange-xml-serialization-failed-due-to-invalid-structure-looking-for-transactionset-or-ge-but-not-found"></a><span data-ttu-id="91d1c-103">Échec de la sérialisation XML de l'échange X12 dû à une structure incorrecte.</span><span class="sxs-lookup"><span data-stu-id="91d1c-103">X12 interchange Xml serialization failed due to invalid structure.</span></span> <span data-ttu-id="91d1c-104">TransactionSet ou GE recherchés mais non trouvés</span><span class="sxs-lookup"><span data-stu-id="91d1c-104">Looking for TransactionSet or GE, but not found</span></span>
## <a name="details"></a><span data-ttu-id="91d1c-105">Détails</span><span class="sxs-lookup"><span data-stu-id="91d1c-105">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="91d1c-106">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="91d1c-106">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="91d1c-107">Version du produit</span><span class="sxs-lookup"><span data-stu-id="91d1c-107">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="91d1c-108">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="91d1c-108">Event ID</span></span>|-|  
|<span data-ttu-id="91d1c-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="91d1c-109">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="91d1c-110"> EDI</span><span class="sxs-lookup"><span data-stu-id="91d1c-110"> EDI</span></span>|  
|<span data-ttu-id="91d1c-111">Composant</span><span class="sxs-lookup"><span data-stu-id="91d1c-111">Component</span></span>|<span data-ttu-id="91d1c-112">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="91d1c-112">EDI Engine</span></span>|  
|<span data-ttu-id="91d1c-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="91d1c-113">Symbolic Name</span></span>|<span data-ttu-id="91d1c-114">X12TransactionSetOrGeNotFound</span><span class="sxs-lookup"><span data-stu-id="91d1c-114">X12TransactionSetOrGeNotFound</span></span>|  
|<span data-ttu-id="91d1c-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="91d1c-115">Message Text</span></span>|<span data-ttu-id="91d1c-116">Échec de la sérialisation XML de l'échange X12 dû à une structure incorrecte.</span><span class="sxs-lookup"><span data-stu-id="91d1c-116">X12 interchange Xml serialization failed due to invalid structure.</span></span> <span data-ttu-id="91d1c-117">TransactionSet ou GE recherchés mais non trouvés</span><span class="sxs-lookup"><span data-stu-id="91d1c-117">Looking for TransactionSet or GE, but not found</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="91d1c-118">Explication</span><span class="sxs-lookup"><span data-stu-id="91d1c-118">Explanation</span></span>  
 <span data-ttu-id="91d1c-119">Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline d'envoi n'a pas pu sérialiser l'échange sortant, car la structure de l'échange est non valide.</span><span class="sxs-lookup"><span data-stu-id="91d1c-119">This Error/Warning/Information event indicates that the send pipeline could not serialize the outgoing interchange because the structure of the interchange was invalid.</span></span> <span data-ttu-id="91d1c-120">Cela peut être dû au fait que les en-têtes ou les codes de fin requis ne sont pas présents ou valides.</span><span class="sxs-lookup"><span data-stu-id="91d1c-120">The reason could be that the required headers or trailers are not present or are invalid.</span></span> <span data-ttu-id="91d1c-121">Cette erreur peut se produire si un document informatisé de groupe n'est pas suivi par un autre document informatisé ou par le code de fin de groupe.</span><span class="sxs-lookup"><span data-stu-id="91d1c-121">It could occur if a transaction set in a group is not followed by another transaction set or the group trailer.</span></span> <span data-ttu-id="91d1c-122">Elle peut également survenir si les vérifications au niveau de l'intégrité de la structure échouent.</span><span class="sxs-lookup"><span data-stu-id="91d1c-122">It could also occur if structural integrity checks failed.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="91d1c-123">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="91d1c-123">User Action</span></span>  
 <span data-ttu-id="91d1c-124">Pour résoudre cette erreur, vérifiez la structure de l'échange en vous assurant que les en-têtes et les codes de fin du groupe ou du document informatisé sont valides, puis renvoyez l'échange.</span><span class="sxs-lookup"><span data-stu-id="91d1c-124">To resolve this error, verify the structure of the interchange, ensuring that the group or transaction set headers and trailers are valid, and then resend the interchange.</span></span>