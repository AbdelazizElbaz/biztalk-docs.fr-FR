---
title: "Valeur de numéro de contrôle non valide | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8ac762e2-2d48-45e8-b4c4-2df246b7568c
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1ce9df9724d85a3b4a2d6ebf28f94e4b9c05db05
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="invalid-control-number-value"></a><span data-ttu-id="4863a-102">Valeur du numéro de contrôle non valide</span><span class="sxs-lookup"><span data-stu-id="4863a-102">Invalid Control Number Value</span></span>
## <a name="details"></a><span data-ttu-id="4863a-103">Détails</span><span class="sxs-lookup"><span data-stu-id="4863a-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4863a-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="4863a-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="4863a-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="4863a-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="4863a-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="4863a-106">Event ID</span></span>|-|  
|<span data-ttu-id="4863a-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="4863a-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="4863a-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="4863a-108"> EDI</span></span>|  
|<span data-ttu-id="4863a-109">Composant</span><span class="sxs-lookup"><span data-stu-id="4863a-109">Component</span></span>|<span data-ttu-id="4863a-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="4863a-110">EDI Engine</span></span>|  
|<span data-ttu-id="4863a-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="4863a-111">Symbolic Name</span></span>|<span data-ttu-id="4863a-112">X12Ta1InvalidControlNumberValueDescription</span><span class="sxs-lookup"><span data-stu-id="4863a-112">X12Ta1InvalidControlNumberValueDescription</span></span>|  
|<span data-ttu-id="4863a-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="4863a-113">Message Text</span></span>|<span data-ttu-id="4863a-114">Valeur du numéro de contrôle non valide</span><span class="sxs-lookup"><span data-stu-id="4863a-114">Invalid Control Number Value</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="4863a-115">Explication</span><span class="sxs-lookup"><span data-stu-id="4863a-115">Explanation</span></span>  
 <span data-ttu-id="4863a-116">Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline de réception n'a pas pu traiter l'échange entrant car la valeur d'un numéro de contrôle (échange, groupe ou document informatisé) dans l'échange n'est pas conforme au type de données ou ne possède pas le nombre correct de chiffres spécifié par le schéma.</span><span class="sxs-lookup"><span data-stu-id="4863a-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange because the value of a control number (interchange, group, or transaction set) in the interchange did not conform to the data type or did not have the correct number of digits specified by the schema.</span></span> <span data-ttu-id="4863a-117">Le schéma est X12ServiceSchema ou EdifactServiceSchema dans BaseArtifacts.dll.</span><span class="sxs-lookup"><span data-stu-id="4863a-117">The schema is the X12ServiceSchema or the EdifactServiceSchema in BaseArtifacts.dll.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="4863a-118">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="4863a-118">User Action</span></span>  
 <span data-ttu-id="4863a-119">Pour résoudre cette erreur, assurez-vous que le numéro de contrôle est conforme au type de données et au nombre de chiffres spécifiés par le schéma, puis renvoyez l'échange.</span><span class="sxs-lookup"><span data-stu-id="4863a-119">To resolve this error, make sure that the control number conforms to the data type and number of digits specified by the schema, and then have the interchange resent.</span></span>