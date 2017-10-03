---
title: "Séparateur de champs introuvable après l’id de balise de segment | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5f6f0a74-3560-4d6d-9893-85e8426e6b17
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 818a061cd723c0d8f8c58570c9e6df94a670942b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="field-separator-not-found-after-segment-tag-id"></a><span data-ttu-id="7e730-102">Séparateur de champs non trouvé avec l'ID de balise de segment</span><span class="sxs-lookup"><span data-stu-id="7e730-102">Field separator not found after segment tag id</span></span>
## <a name="details"></a><span data-ttu-id="7e730-103">Détails</span><span class="sxs-lookup"><span data-stu-id="7e730-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7e730-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="7e730-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="7e730-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="7e730-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="7e730-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="7e730-106">Event ID</span></span>|-|  
|<span data-ttu-id="7e730-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="7e730-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="7e730-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="7e730-108"> EDI</span></span>|  
|<span data-ttu-id="7e730-109">Composant</span><span class="sxs-lookup"><span data-stu-id="7e730-109">Component</span></span>|<span data-ttu-id="7e730-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="7e730-110">EDI Engine</span></span>|  
|<span data-ttu-id="7e730-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="7e730-111">Symbolic Name</span></span>|<span data-ttu-id="7e730-112">X12SeFsNotFoundAfterTagIdDescription</span><span class="sxs-lookup"><span data-stu-id="7e730-112">X12SeFsNotFoundAfterTagIdDescription</span></span>|  
|<span data-ttu-id="7e730-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="7e730-113">Message Text</span></span>|<span data-ttu-id="7e730-114">Séparateur de champs non trouvé avec l'ID de balise de segment</span><span class="sxs-lookup"><span data-stu-id="7e730-114">Field separator not found after segment tag id</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="7e730-115">Explication</span><span class="sxs-lookup"><span data-stu-id="7e730-115">Explanation</span></span>  
 <span data-ttu-id="7e730-116">Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline de réception n'a pas pu traiter l'échange, car ce dernier contient un segment dans lequel un identificateur de segment n'est pas immédiatement suivi d'un séparateur d'éléments de données.</span><span class="sxs-lookup"><span data-stu-id="7e730-116">This Error/Warning/Information event indicates that the receive pipeline could not process the interchange because the interchange contained a segment that had a segment identifier without a data element separator immediately following it.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="7e730-117">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="7e730-117">User Action</span></span>  
 <span data-ttu-id="7e730-118">Pour résoudre cette erreur, assurez-vous que tous les identificateurs de segment d'un échange soient immédiatement suivis de séparateurs d'éléments de données, puis demandez à l'expéditeur de renvoyer l'échange.</span><span class="sxs-lookup"><span data-stu-id="7e730-118">To resolve this error, ensure that all segment identifiers in the interchange have data element separators immediately following them, and then have the interchange resent.</span></span>