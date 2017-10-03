---
title: ID de version non valide | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 563af6e8-f496-46c9-8b5f-7b941b2d08a5
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f5edd2dddc5df19d99c434ec60cad46664ba378e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="invalid-versionid"></a><span data-ttu-id="75f72-102">ID de version non valide</span><span class="sxs-lookup"><span data-stu-id="75f72-102">Invalid VersionId</span></span>
## <a name="details"></a><span data-ttu-id="75f72-103">Détails</span><span class="sxs-lookup"><span data-stu-id="75f72-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="75f72-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="75f72-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="75f72-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="75f72-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="75f72-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="75f72-106">Event ID</span></span>|-|  
|<span data-ttu-id="75f72-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="75f72-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="75f72-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="75f72-108"> EDI</span></span>|  
|<span data-ttu-id="75f72-109">Composant</span><span class="sxs-lookup"><span data-stu-id="75f72-109">Component</span></span>|<span data-ttu-id="75f72-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="75f72-110">EDI Engine</span></span>|  
|<span data-ttu-id="75f72-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="75f72-111">Symbolic Name</span></span>|<span data-ttu-id="75f72-112">X12Ta1InvalidVersionIdDescription</span><span class="sxs-lookup"><span data-stu-id="75f72-112">X12Ta1InvalidVersionIdDescription</span></span>|  
|<span data-ttu-id="75f72-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="75f72-113">Message Text</span></span>|<span data-ttu-id="75f72-114">ID de version non valide</span><span class="sxs-lookup"><span data-stu-id="75f72-114">Invalid VersionId</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="75f72-115">Explication</span><span class="sxs-lookup"><span data-stu-id="75f72-115">Explanation</span></span>  
 <span data-ttu-id="75f72-116">Cet événement de type erreur/avertissement/information indique que le pipeline de réception n'a pas pu traiter l'échange entrant, car l'identificateur de version de l'échange (le champ GS08 dans un échange X12 ou le champ UNG7 dans un échange EDIFACT) n'était pas conforme au type de données et au nombre de chiffres définis par le schéma de service (X12ServiceSchema ou le EdifactServiceSchema dans BaseArtifacts.dll).</span><span class="sxs-lookup"><span data-stu-id="75f72-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange because the version identifier in the interchange (the GS08 field in an X12 interchange or the UNG7 field in an EDIFACT interchange) did not conform to the data type and number of digits established by the service schema (X12ServiceSchema or the EdifactServiceSchema in BaseArtifacts.dll).</span></span> <span data-ttu-id="75f72-117">Les données du champ GS08 doivent être de type X12_AN. Ce champ peut contenir de 1 à 12 chiffres.</span><span class="sxs-lookup"><span data-stu-id="75f72-117">The GS08 field must be of the X12_AN data type and between 1 and 12 digits.</span></span> <span data-ttu-id="75f72-118">La version d'origine dans UNG7.1 doit être spécifiée via le type de données EDIFACT_AN. Ce champ peut contenir de 1 à 3 chiffres.</span><span class="sxs-lookup"><span data-stu-id="75f72-118">The version in UNG7.1 must be of the EDIFACT_AN data type and between 1 and 3 digits.</span></span> <span data-ttu-id="75f72-119">La version finale dans UNG7.2 doit être spécifiée via le type de données EDIFACT_AN. Ce champ peut contenir de 1 à 3 chiffres.</span><span class="sxs-lookup"><span data-stu-id="75f72-119">The release in UNG7.2 must be of the EDIFACT_AN data type and between 1 and 3 digits.</span></span> <span data-ttu-id="75f72-120">Le code d'association assigné dans UNG7.3 doit être spécifié via le type de données EDIFACT_AN. Ce champ peut contenir de 1 à 6 chiffres.</span><span class="sxs-lookup"><span data-stu-id="75f72-120">The Association assigned code in UNG7.3 must be of the EDIFACT_AN data type and between 1 and 6 digits.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="75f72-121">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="75f72-121">User Action</span></span>  
 <span data-ttu-id="75f72-122">Pour résoudre cette erreur, vérifiez que la version du champ GS08 ou UNG7 est spécifiée via le type de données et conformément au nombre de chiffres indiqués par le schéma de service, puis faites renvoyer l'échange.</span><span class="sxs-lookup"><span data-stu-id="75f72-122">To resolve this error, make sure that the version in GS08 or UNG7 conforms to the data type and number of digits specified by the service schema, and then have the interchange resent.</span></span>