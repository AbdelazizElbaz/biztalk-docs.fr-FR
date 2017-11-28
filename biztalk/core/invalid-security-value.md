---
title: "Valeur non valide de sécurité | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ee380da7-c05e-4b9b-84ee-f7ffee90eb0e
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e41315400ee2b0eae099439237356b61676b26cb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="invalid-security-value"></a><span data-ttu-id="b9d46-102">Valeur Sécurité non valide</span><span class="sxs-lookup"><span data-stu-id="b9d46-102">Invalid Security Value</span></span>
## <a name="details"></a><span data-ttu-id="b9d46-103">Détails</span><span class="sxs-lookup"><span data-stu-id="b9d46-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b9d46-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="b9d46-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="b9d46-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="b9d46-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="b9d46-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="b9d46-106">Event ID</span></span>|-|  
|<span data-ttu-id="b9d46-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="b9d46-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="b9d46-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="b9d46-108"> EDI</span></span>|  
|<span data-ttu-id="b9d46-109">Composant</span><span class="sxs-lookup"><span data-stu-id="b9d46-109">Component</span></span>|<span data-ttu-id="b9d46-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="b9d46-110">EDI Engine</span></span>|  
|<span data-ttu-id="b9d46-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="b9d46-111">Symbolic Name</span></span>|<span data-ttu-id="b9d46-112">X12Ta1InvalidSecurityValueDescription</span><span class="sxs-lookup"><span data-stu-id="b9d46-112">X12Ta1InvalidSecurityValueDescription</span></span>|  
|<span data-ttu-id="b9d46-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="b9d46-113">Message Text</span></span>|<span data-ttu-id="b9d46-114">Valeur Sécurité non valide</span><span class="sxs-lookup"><span data-stu-id="b9d46-114">Invalid Security Value</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="b9d46-115">Explication</span><span class="sxs-lookup"><span data-stu-id="b9d46-115">Explanation</span></span>  
 <span data-ttu-id="b9d46-116">Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline de réception n'a pas réussi à traiter l'échange entrant, car les informations de sécurité dans le champ ISA04 ou la valeur du mot de passe de référence du destinataire dans le champ UNB6.1 n'est pas conforme au type de données et au nombre de chiffres qui ont été définis par le schéma de service (X12ServiceSchema ou EdifactServiceSchema dans le fichier BaseArtifacts.dll).</span><span class="sxs-lookup"><span data-stu-id="b9d46-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange because the Security Information in the ISA04 field or the Recipient Reference Password Value in the UNB6.1 field did not conform to the data type and number of digits established by the service schema (X12ServiceSchema or the EdifactServiceSchema in BaseArtifacts.dll).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="b9d46-117">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="b9d46-117">User Action</span></span>  
 <span data-ttu-id="b9d46-118">Pour résoudre cette erreur, veillez à ce que le champ ISA04 soit défini sur le type de données X12_AN et comporte 10 caractères (avec ou sans espace de fin) ou que le champ UNB6.1 soit défini sur le type de données EDIFACT_AN et comporte entre 1 et 14 caractères.</span><span class="sxs-lookup"><span data-stu-id="b9d46-118">To resolve this error, make sure that the ISA04 field is of the X12_AN data type and is 10 characters long (with or without trailing spaces) or that the UNB6.1 field is of the EDIFACT_AN data type and is between 1 and 14 characters long.</span></span> <span data-ttu-id="b9d46-119">Demandez à l'expéditeur de renvoyer l'échange.</span><span class="sxs-lookup"><span data-stu-id="b9d46-119">Have the interchange resent.</span></span>