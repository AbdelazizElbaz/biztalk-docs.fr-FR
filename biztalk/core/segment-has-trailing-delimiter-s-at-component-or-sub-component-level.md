---
title: "Segment possède un ou plusieurs délimiteurs fin au composant ou sous-composant | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 517f1cfc-66c1-47e6-be94-2c76c1f89230
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3eede2923da1ed206a897b879b7b6be589800e4c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="segment-has-trailing-delimiters-at-component-or-sub-component-level"></a><span data-ttu-id="127f8-102">Un segment possède un ou plusieurs délimiteurs de fin au niveau du composant ou du sous-composant</span><span class="sxs-lookup"><span data-stu-id="127f8-102">Segment has trailing delimiter(s) at component or sub-component level</span></span>
## <a name="details"></a><span data-ttu-id="127f8-103">Détails</span><span class="sxs-lookup"><span data-stu-id="127f8-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="127f8-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="127f8-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="127f8-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="127f8-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="127f8-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="127f8-106">Event ID</span></span>|-|  
|<span data-ttu-id="127f8-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="127f8-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="127f8-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="127f8-108"> EDI</span></span>|  
|<span data-ttu-id="127f8-109">Composant</span><span class="sxs-lookup"><span data-stu-id="127f8-109">Component</span></span>|<span data-ttu-id="127f8-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="127f8-110">EDI Engine</span></span>|  
|<span data-ttu-id="127f8-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="127f8-111">Symbolic Name</span></span>|<span data-ttu-id="127f8-112">X12SeSegmentHasTrailingDelimiterDescription</span><span class="sxs-lookup"><span data-stu-id="127f8-112">X12SeSegmentHasTrailingDelimiterDescription</span></span>|  
|<span data-ttu-id="127f8-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="127f8-113">Message Text</span></span>|<span data-ttu-id="127f8-114">Un segment possède un ou plusieurs délimiteurs de fin au niveau du composant ou du sous-composant</span><span class="sxs-lookup"><span data-stu-id="127f8-114">Segment has trailing delimiter(s) at component or sub-component level</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="127f8-115">Explication</span><span class="sxs-lookup"><span data-stu-id="127f8-115">Explanation</span></span>  
 <span data-ttu-id="127f8-116">Cet événement de type erreur/avertissement/information indique que le pipeline de réception n'a pas pu traiter l'échange entrant, car celui-ci contenait des délimiteurs de fin, mais ces derniers n'étaient pas activés pour le tiers jouant le rôle d'expéditeur des échanges.</span><span class="sxs-lookup"><span data-stu-id="127f8-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange because the interchange contained trailing delimiters, but trailing delimiters were not enabled for the party as interchange sender.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="127f8-117">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="127f8-117">User Action</span></span>  
 <span data-ttu-id="127f8-118">Pour résoudre cette erreur, activez les séparateurs de fin de la façon suivante :</span><span class="sxs-lookup"><span data-stu-id="127f8-118">To resolve this error, enable trailing separators as follows:</span></span>  
  
1.  <span data-ttu-id="127f8-119">Ouvrez la console Administration de BizTalk Server, déplacez le dossier Tiers et ouvrez les propriétés EDI du tiers.</span><span class="sxs-lookup"><span data-stu-id="127f8-119">Open the BizTalk Server Administration Console, move to the Parties folder, and open the EDI Properties for the party.</span></span>  
  
2.  <span data-ttu-id="127f8-120">Déplacez la page Génération d'accusés de réception et paramètres de validation pour X12 ou EDIFACT, selon les besoins.</span><span class="sxs-lookup"><span data-stu-id="127f8-120">Move to the Validation and ACK Generation page for X12 or EDIFACT, as appropriate.</span></span>  
  
3.  <span data-ttu-id="127f8-121">Cliquez sur Autoriser les séparateurs de fin.</span><span class="sxs-lookup"><span data-stu-id="127f8-121">Click "Allow trailing separators".</span></span>