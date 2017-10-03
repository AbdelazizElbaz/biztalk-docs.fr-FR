---
title: "Élément de données obligatoire manquant | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 510d54b3-13de-4735-92ec-04fd4b9d460e
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0b0c2d415b977c069e351d90fa5ad68b430c3f2f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="mandatory-data-element-missing"></a><span data-ttu-id="d6cf8-102">Élément de données obligatoire manquant</span><span class="sxs-lookup"><span data-stu-id="d6cf8-102">Mandatory data element missing</span></span>
## <a name="details"></a><span data-ttu-id="d6cf8-103">Détails</span><span class="sxs-lookup"><span data-stu-id="d6cf8-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d6cf8-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="d6cf8-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="d6cf8-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="d6cf8-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="d6cf8-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="d6cf8-106">Event ID</span></span>|-|  
|<span data-ttu-id="d6cf8-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="d6cf8-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="d6cf8-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="d6cf8-108"> EDI</span></span>|  
|<span data-ttu-id="d6cf8-109">Composant</span><span class="sxs-lookup"><span data-stu-id="d6cf8-109">Component</span></span>|<span data-ttu-id="d6cf8-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="d6cf8-110">EDI Engine</span></span>|  
|<span data-ttu-id="d6cf8-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="d6cf8-111">Symbolic Name</span></span>|<span data-ttu-id="d6cf8-112">X12DeMandatoryDataElementMissingDescription</span><span class="sxs-lookup"><span data-stu-id="d6cf8-112">X12DeMandatoryDataElementMissingDescription</span></span>|  
|<span data-ttu-id="d6cf8-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="d6cf8-113">Message Text</span></span>|<span data-ttu-id="d6cf8-114">Élément de données obligatoire manquant</span><span class="sxs-lookup"><span data-stu-id="d6cf8-114">Mandatory data element missing</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="d6cf8-115">Explication</span><span class="sxs-lookup"><span data-stu-id="d6cf8-115">Explanation</span></span>  
 <span data-ttu-id="d6cf8-116">Cet événement de type erreur/avertissement/information indique que le pipeline de réception n'a pas pu traiter l'échange X12 entrant, car celui-ci ne contenait pas un élément de données requis par le schéma de message (pour lequel minOccurs est supérieur à 0).</span><span class="sxs-lookup"><span data-stu-id="d6cf8-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming X12 interchange because the interchange did not contain a data element that is required by the message schema (for which minOccurs is greater than 0).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="d6cf8-117">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="d6cf8-117">User Action</span></span>  
 <span data-ttu-id="d6cf8-118">Pour résoudre cette erreur, assurez-vous que l'échange contient tous les éléments de données requis par le schéma de message, puis procédez au renvoi du message.</span><span class="sxs-lookup"><span data-stu-id="d6cf8-118">To resolve this error, make sure that the interchange contains all the data elements required by the message schema, and then have the message resent.</span></span>