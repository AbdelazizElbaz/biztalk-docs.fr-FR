---
title: "ID d’expéditeur non valide | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: be8055ab-8aba-49ac-ad33-fb33d4ff3e8b
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 150be7faef15efd033cf87759a8390c09e38e249
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="invalid-senderid"></a><span data-ttu-id="85d1a-102">ID d'expéditeur non valide</span><span class="sxs-lookup"><span data-stu-id="85d1a-102">Invalid SenderId</span></span>
## <a name="details"></a><span data-ttu-id="85d1a-103">Détails</span><span class="sxs-lookup"><span data-stu-id="85d1a-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="85d1a-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="85d1a-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="85d1a-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="85d1a-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="85d1a-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="85d1a-106">Event ID</span></span>|-|  
|<span data-ttu-id="85d1a-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="85d1a-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="85d1a-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="85d1a-108"> EDI</span></span>|  
|<span data-ttu-id="85d1a-109">Composant</span><span class="sxs-lookup"><span data-stu-id="85d1a-109">Component</span></span>|<span data-ttu-id="85d1a-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="85d1a-110">EDI Engine</span></span>|  
|<span data-ttu-id="85d1a-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="85d1a-111">Symbolic Name</span></span>|<span data-ttu-id="85d1a-112">X12Ta1InvalidSenderIdDescription</span><span class="sxs-lookup"><span data-stu-id="85d1a-112">X12Ta1InvalidSenderIdDescription</span></span>|  
|<span data-ttu-id="85d1a-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="85d1a-113">Message Text</span></span>|<span data-ttu-id="85d1a-114">ID d'expéditeur non valide</span><span class="sxs-lookup"><span data-stu-id="85d1a-114">Invalid SenderId</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="85d1a-115">Explication</span><span class="sxs-lookup"><span data-stu-id="85d1a-115">Explanation</span></span>  
 <span data-ttu-id="85d1a-116">Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline de réception n'a pas réussi à traiter l'échange entrant, car l'ID d'expéditeur dans le champ ISA06 ou l'identification de l'expéditeur dans le champs UNB2.1 n'est pas conforme au type de données et au nombre de chiffres qui ont été définis par le schéma de service (X12ServiceSchema ou EdifactServiceSchema dans le fichier BaseArtifacts.dll).</span><span class="sxs-lookup"><span data-stu-id="85d1a-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange because the Sender ID in the ISA06 field or the Sender Identification in the UNB2.1 field did not conform to the data type and number of digits established by the service schema (X12ServiceSchema or the EdifactServiceSchema in BaseArtifacts.dll).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="85d1a-117">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="85d1a-117">User Action</span></span>  
 <span data-ttu-id="85d1a-118">Pour résoudre cette erreur, veillez à ce que le champ ISA06 soit défini sur le type de données X12_AN et comporte 15 caractères (avec ou sans espace de fin) ou que le champ UNB2.1 soit défini sur le type de données EDIFACT_AN et comporte entre 1 et 35 caractères.</span><span class="sxs-lookup"><span data-stu-id="85d1a-118">To resolve this error, make sure that the ISA06 field is of the X12_AN data type and is 15 characters long (with or without trailing spaces) or that the UNB2.1 field is of the EDIFACT_AN data type and is between 1 and 35 characters.</span></span> <span data-ttu-id="85d1a-119">Demandez à l'expéditeur de renvoyer l'échange.</span><span class="sxs-lookup"><span data-stu-id="85d1a-119">Have the interchange resent.</span></span>