---
title: "Valeur d’indicateur de Test non valide | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5d81d501-4020-4ff9-955c-5674a99d250b
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 166ab446831243c58b1c12881393be1466399e0c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="invalid-test-indicator-value"></a><span data-ttu-id="99cf1-102">Valeur de l'indicateur de test non valide</span><span class="sxs-lookup"><span data-stu-id="99cf1-102">Invalid Test Indicator Value</span></span>
## <a name="details"></a><span data-ttu-id="99cf1-103">Détails</span><span class="sxs-lookup"><span data-stu-id="99cf1-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="99cf1-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="99cf1-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="99cf1-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="99cf1-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="99cf1-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="99cf1-106">Event ID</span></span>|-|  
|<span data-ttu-id="99cf1-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="99cf1-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="99cf1-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="99cf1-108"> EDI</span></span>|  
|<span data-ttu-id="99cf1-109">Composant</span><span class="sxs-lookup"><span data-stu-id="99cf1-109">Component</span></span>|<span data-ttu-id="99cf1-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="99cf1-110">EDI Engine</span></span>|  
|<span data-ttu-id="99cf1-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="99cf1-111">Symbolic Name</span></span>|<span data-ttu-id="99cf1-112">X12Ta1InvalidTestIndicatorValueDescription</span><span class="sxs-lookup"><span data-stu-id="99cf1-112">X12Ta1InvalidTestIndicatorValueDescription</span></span>|  
|<span data-ttu-id="99cf1-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="99cf1-113">Message Text</span></span>|<span data-ttu-id="99cf1-114">Valeur de l'indicateur de test non valide</span><span class="sxs-lookup"><span data-stu-id="99cf1-114">Invalid Test Indicator Value</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="99cf1-115">Explication</span><span class="sxs-lookup"><span data-stu-id="99cf1-115">Explanation</span></span>  
 <span data-ttu-id="99cf1-116">Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline de réception n'a pas réussi à traiter l'échange entrant, car l'indicateur de test dans le champ UNB11 n'est pas conforme au type de données et au nombre de chiffres qui ont été définis par le schéma de service (X12ServiceSchema ou le EdifactServiceSchema dans le fichier BaseArtifacts.dll).</span><span class="sxs-lookup"><span data-stu-id="99cf1-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange because the Test Indicator in the UNB11 field did not conform to the data type and number of digits established by the service schema (X12ServiceSchema or the EdifactServiceSchema in BaseArtifacts.dll).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="99cf1-117">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="99cf1-117">User Action</span></span>  
 <span data-ttu-id="99cf1-118">Pour résoudre cette erreur, vérifiez que le champ UNB11 est du type de données EDIFACT_N et que sa longueur est de 1 caractère.</span><span class="sxs-lookup"><span data-stu-id="99cf1-118">To resolve this error, make sure that the UNB11 field is of the EDIFACT_N data type and is 1 character in length.</span></span> <span data-ttu-id="99cf1-119">Demandez à l'expéditeur de renvoyer l'échange.</span><span class="sxs-lookup"><span data-stu-id="99cf1-119">Have the interchange resent.</span></span>