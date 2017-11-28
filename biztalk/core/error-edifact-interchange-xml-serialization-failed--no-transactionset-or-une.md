---
title: "Échec de la sérialisation Xml de l’échange EDIFACT en raison d’une structure non valide, aucun transactionSet ou de UNE | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3ce1c219-f2ed-46c1-ae4b-8a4206f7cd01
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f5c6aae4bc3ed16afffadec774eaeac9ed64808d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="edifact-interchange-xml-serialization-failed-due-to-invalid-structure-no-transactionset-or-une"></a><span data-ttu-id="5db17-102">Échec de la sérialisation XML de l'échange EDIFACT dû à une structure non valide, absence de transactionSet ou UNE.</span><span class="sxs-lookup"><span data-stu-id="5db17-102">Edifact interchange Xml serialization failed due to invalid structure, no transactionSet or UNE</span></span>
## <a name="details"></a><span data-ttu-id="5db17-103">Détails</span><span class="sxs-lookup"><span data-stu-id="5db17-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5db17-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="5db17-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="5db17-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="5db17-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="5db17-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="5db17-106">Event ID</span></span>|-|  
|<span data-ttu-id="5db17-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="5db17-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="5db17-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="5db17-108"> EDI</span></span>|  
|<span data-ttu-id="5db17-109">Composant</span><span class="sxs-lookup"><span data-stu-id="5db17-109">Component</span></span>|<span data-ttu-id="5db17-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="5db17-110">EDI Engine</span></span>|  
|<span data-ttu-id="5db17-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="5db17-111">Symbolic Name</span></span>|<span data-ttu-id="5db17-112">EfactTransactionSetOrUneNotFound</span><span class="sxs-lookup"><span data-stu-id="5db17-112">EfactTransactionSetOrUneNotFound</span></span>|  
|<span data-ttu-id="5db17-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="5db17-113">Message Text</span></span>|<span data-ttu-id="5db17-114">Échec de la sérialisation XML de l'échange EDIFACT dû à une structure non valide.</span><span class="sxs-lookup"><span data-stu-id="5db17-114">Edifact interchange Xml serialization failed due to invalid structure.</span></span> <span data-ttu-id="5db17-115">Recherche de TransactionSet ou de UNE infructueuse.</span><span class="sxs-lookup"><span data-stu-id="5db17-115">Looking for TransactionSet or UNE, but not found</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="5db17-116">Explication</span><span class="sxs-lookup"><span data-stu-id="5db17-116">Explanation</span></span>  
 <span data-ttu-id="5db17-117">Cet événement de type erreur/avertissement/information indique que le pipeline de réception EDI n'a pas pu traiter l'échange EDIFACT entrant, car le premier segment n'était ni de type UNA, ni de type UNB.</span><span class="sxs-lookup"><span data-stu-id="5db17-117">This Error/Warning/Information event indicates that the EDI receive pipeline could not process the incoming EDIFACT interchange because the first segment was neither a UNA or a UNB segment.</span></span> <span data-ttu-id="5db17-118">Le segment UNA est facultatif ; le segment UNB est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="5db17-118">The UNA segment is optional; the UNB segment is mandatory.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="5db17-119">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="5db17-119">User Action</span></span>  
 <span data-ttu-id="5db17-120">Pour résoudre cette erreur, assurez-vous que l'expéditeur de l'échange structure le message de telle manière qu'un document informatisé dans un groupe soit suivi d'un autre document informatisé ou d'un segment UNE.</span><span class="sxs-lookup"><span data-stu-id="5db17-120">To resolve this error, ensure that the sender of the interchange structures the message such that a transaction set in a group is either followed by another transaction set or a UNE segment.</span></span> <span data-ttu-id="5db17-121">Demandez ensuite à l'expéditeur de renvoyer l'échange.</span><span class="sxs-lookup"><span data-stu-id="5db17-121">Have the sender then resend the interchange.</span></span>