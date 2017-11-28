---
title: Heure non valide | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6942eb77-3ef1-460c-ac4f-8f1339c25d1b
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: aae508a945cc6934e83408b2a9b78c324947e0e8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="invalid-time"></a><span data-ttu-id="c418b-102">Heure non valide</span><span class="sxs-lookup"><span data-stu-id="c418b-102">Invalid Time</span></span>
## <a name="details"></a><span data-ttu-id="c418b-103">Détails</span><span class="sxs-lookup"><span data-stu-id="c418b-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c418b-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="c418b-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="c418b-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="c418b-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="c418b-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="c418b-106">Event ID</span></span>|-|  
|<span data-ttu-id="c418b-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="c418b-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="c418b-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="c418b-108"> EDI</span></span>|  
|<span data-ttu-id="c418b-109">Composant</span><span class="sxs-lookup"><span data-stu-id="c418b-109">Component</span></span>|<span data-ttu-id="c418b-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="c418b-110">EDI Engine</span></span>|  
|<span data-ttu-id="c418b-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="c418b-111">Symbolic Name</span></span>|<span data-ttu-id="c418b-112">X12Ta1InvalidTimeDescription</span><span class="sxs-lookup"><span data-stu-id="c418b-112">X12Ta1InvalidTimeDescription</span></span>|  
|<span data-ttu-id="c418b-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="c418b-113">Message Text</span></span>|<span data-ttu-id="c418b-114">Heure non valide</span><span class="sxs-lookup"><span data-stu-id="c418b-114">Invalid Time</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="c418b-115">Explication</span><span class="sxs-lookup"><span data-stu-id="c418b-115">Explanation</span></span>  
 <span data-ttu-id="c418b-116">Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline de réception n'a pas réussi à traiter l'échange entrant, car une valeur d'heure d'un élément de données n'est pas conforme au type de données spécifié par le schéma EDI, ou une valeur d'heure de l'en-tête de champ GS05 d'un échange X12 n'est pas conforme au schéma de service (X12ServiceSchema dans le fichier BaseArtifacts.dll).</span><span class="sxs-lookup"><span data-stu-id="c418b-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange because a time value in a data element did not conform to the data type specified by the EDI schema or the time value in the GS05 field header in an X12 interchange did not conform to the service schema (X12ServiceSchema in BaseArtifacts.dll).</span></span> <span data-ttu-id="c418b-117">Pour X12, le schéma de service définit une heure dans le champ GS05 du type de données X12_TM et d'une longueur comprise entre 4 et 8 caractères.</span><span class="sxs-lookup"><span data-stu-id="c418b-117">For X12, the service schema defines a time in the GS05 field as of the X12_TM data type and between four and eight characters in length.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="c418b-118">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="c418b-118">User Action</span></span>  
 <span data-ttu-id="c418b-119">Pour résoudre cette erreur, assurez-vous qu'une valeur d'heure contenue dans un élément de données est conforme au type de données spécifié par le schéma EDI ou que la valeur d'heure dans l'en-tête GS05 d'un échange X12 est conforme au schéma de service, puis demandez à l'expéditeur de renvoyer l'échange.</span><span class="sxs-lookup"><span data-stu-id="c418b-119">To resolve this error, make sure that a time value in a data element conforms to the data type specified by the EDI schema or a time value in the GS05 header of an X12 interchange conforms to the service schema, and then have the interchange resent.</span></span>