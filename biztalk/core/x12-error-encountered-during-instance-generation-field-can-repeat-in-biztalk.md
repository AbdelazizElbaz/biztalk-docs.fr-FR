---
title: "Erreur rencontrée lors de la génération de l’instance : champ peut se répéter mais le délimiteur de répétition n’a pas été défini. | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c7a6783c-cb35-4ce8-9164-ec34ae500de1
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 366caec69fd84b91cf815a58e4975e8e5d7b4d06
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error-encountered-during-instance-generation--field-can-repeat-but-repetition-delimiter-has-not-been-defined"></a><span data-ttu-id="952ff-102">Erreur rencontrée lors de la création de l'instance. Le champ peut se répéter mais le délimiteur de répétition n'a pas été défini</span><span class="sxs-lookup"><span data-stu-id="952ff-102">Error encountered during instance generation--field can repeat but repetition delimiter has not been defined</span></span>
## <a name="details"></a><span data-ttu-id="952ff-103">Détails</span><span class="sxs-lookup"><span data-stu-id="952ff-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="952ff-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="952ff-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="952ff-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="952ff-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="952ff-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="952ff-106">Event ID</span></span>|-|  
|<span data-ttu-id="952ff-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="952ff-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="952ff-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="952ff-108"> EDI</span></span>|  
|<span data-ttu-id="952ff-109">Composant</span><span class="sxs-lookup"><span data-stu-id="952ff-109">Component</span></span>|<span data-ttu-id="952ff-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="952ff-110">EDI Engine</span></span>|  
|<span data-ttu-id="952ff-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="952ff-111">Symbolic Name</span></span>|-|  
|<span data-ttu-id="952ff-112">Texte du message</span><span class="sxs-lookup"><span data-stu-id="952ff-112">Message Text</span></span>|<span data-ttu-id="952ff-113">Erreur rencontrée lors de la création de l'instance.</span><span class="sxs-lookup"><span data-stu-id="952ff-113">Error encountered during instance generation.</span></span> <span data-ttu-id="952ff-114">Le champ {0} peut se répéter mais le délimiteur de répétition n'a pas été défini.</span><span class="sxs-lookup"><span data-stu-id="952ff-114">The field {0} can repeat but repetition delimiter has not been defined.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="952ff-115">Explication</span><span class="sxs-lookup"><span data-stu-id="952ff-115">Explanation</span></span>  
 <span data-ttu-id="952ff-116">Cet événement d'erreur/d'avertissement/d'informations indique que BizTalk Server n'a pas pu générer une instance du message X12, car le champ spécifié peut se répéter (comme indiqué par le schéma), mais aucun séparateur de répétition n'a été défini.</span><span class="sxs-lookup"><span data-stu-id="952ff-116">This Error/Warning/Information event indicates that BizTalk Server could not generate an X12 message instance because the indicated field can repeat (as specified by the schema), but no repetition separator has been defined.</span></span> <span data-ttu-id="952ff-117">Cette situation se produit lorsque la valeur du paramètre minOccurs d'un champ de schéma est supérieure à 1, mais qu'un identificateur standard a été défini à la place d'un séparateur de répétition.</span><span class="sxs-lookup"><span data-stu-id="952ff-117">This occurs when a field in the schema has minOccurs equal to more than 1, but a Standard identifier has been defined, rather than a Repetition separator.</span></span> <span data-ttu-id="952ff-118">(Pour les échanges EDIFACT, un séparateur de répétition est défini par défaut).</span><span class="sxs-lookup"><span data-stu-id="952ff-118">(For EDIFACT interchanges, a repetition separator is defined by default.)</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="952ff-119">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="952ff-119">User Action</span></span>  
 <span data-ttu-id="952ff-120">Pour résoudre cette erreur, dans la page Définition des segments ISA pour le tiers en tant que récepteur d'échanges, sélectionnez un séparateur de répétition au lieu d'un identificateur standard pour ISA11, puis entrez un caractère pour le séparateur.</span><span class="sxs-lookup"><span data-stu-id="952ff-120">To resolve this error, select Repetition separator rather than Standard identifier for ISA11 in the ISA Segment Definition page for the party as interchange receiver, and enter a character for the separator.</span></span> <span data-ttu-id="952ff-121">Si aucun tiers n'a été résolu pour l'échange, définissez le séparateur de répétition dans la page Définition des segments ISA des propriétés globales (pour les échanges X12).</span><span class="sxs-lookup"><span data-stu-id="952ff-121">If no party has been resolved for the interchange, define the repetition separator in the ISA Segment Definition page of the global properties (for X12 interchanges).</span></span>