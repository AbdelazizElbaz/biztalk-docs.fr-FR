---
title: Date non valide | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a41da9c5-9dcf-44cd-be5b-922e6c267ec3
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 259456e781f5f5255f9fed8a51c8eb0569dd57b4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="invalid-date"></a><span data-ttu-id="8b4ce-102">Date non valide</span><span class="sxs-lookup"><span data-stu-id="8b4ce-102">Invalid Date</span></span>
## <a name="details"></a><span data-ttu-id="8b4ce-103">Détails</span><span class="sxs-lookup"><span data-stu-id="8b4ce-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8b4ce-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="8b4ce-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="8b4ce-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="8b4ce-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="8b4ce-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="8b4ce-106">Event ID</span></span>|-|  
|<span data-ttu-id="8b4ce-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="8b4ce-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="8b4ce-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="8b4ce-108"> EDI</span></span>|  
|<span data-ttu-id="8b4ce-109">Composant</span><span class="sxs-lookup"><span data-stu-id="8b4ce-109">Component</span></span>|<span data-ttu-id="8b4ce-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="8b4ce-110">EDI Engine</span></span>|  
|<span data-ttu-id="8b4ce-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="8b4ce-111">Symbolic Name</span></span>|<span data-ttu-id="8b4ce-112">X12DeInvalidDateDescription</span><span class="sxs-lookup"><span data-stu-id="8b4ce-112">X12DeInvalidDateDescription</span></span>|  
|<span data-ttu-id="8b4ce-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="8b4ce-113">Message Text</span></span>|<span data-ttu-id="8b4ce-114">Date non valide</span><span class="sxs-lookup"><span data-stu-id="8b4ce-114">Invalid Date</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="8b4ce-115">Explication</span><span class="sxs-lookup"><span data-stu-id="8b4ce-115">Explanation</span></span>  
 <span data-ttu-id="8b4ce-116">Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline de réception n'a pas pu traiter l'échange entrant ou que le pipeline d'envoi n'a pas pu traiter l'échange sortant, car une valeur de date de l'élément de données n'est pas conforme au type de données spécifié par le schéma EDI, ou la valeur de date de l'en-tête de champ GS04 d'un échange X12 n'est pas conforme au schéma de service (X12ServiceSchema dans le fichier BaseArtifacts.dll).</span><span class="sxs-lookup"><span data-stu-id="8b4ce-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange or the send pipeline could not process the outgoing interchange because a date value in a data element did not conform to the data type specified by the EDI schema or the date value in the GS04 field header in an X12 interchange did not conform to the service schema (X12ServiceSchema in BaseArtifacts.dll).</span></span> <span data-ttu-id="8b4ce-117">Pour X12, le schéma de service définit une date dans le champ GS04 du type de données X12_DT et d'une longueur comprise entre 6 et 8 caractères.</span><span class="sxs-lookup"><span data-stu-id="8b4ce-117">For X12, the service schema defines a date in the GS04 field as of the X12_DT data type and between six and eight characters in length.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="8b4ce-118">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="8b4ce-118">User Action</span></span>  
 <span data-ttu-id="8b4ce-119">Pour résoudre cette erreur, assurez-vous que la valeur d'heure contenue dans un élément de données est conforme au type de données spécifié par le schéma EDI, ou que la valeur de date dans l'en-tête GS04 d'un échange X12 est conforme au schéma de service, puis demandez à l'expéditeur de renvoyer l'échange.</span><span class="sxs-lookup"><span data-stu-id="8b4ce-119">To resolve this error, make sure that the time value in a data element conforms to the data type specified by the EDI schema or the date value in the GS04 header of an X12 interchange conforms to the service schema, and then have the interchange resent.</span></span>