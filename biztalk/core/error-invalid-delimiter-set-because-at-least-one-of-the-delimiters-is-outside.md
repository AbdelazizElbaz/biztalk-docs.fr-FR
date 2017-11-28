---
title: "Délimiteur non valide défini, car au moins un des délimiteurs est en dehors de la plage autorisée | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c1286559-765b-4728-945d-cf3386e1ba06
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c70722adc1a099d340b862d38574b44391954aa4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="invalid-delimiter-set-because-at-least-one-of-the-delimiters-is-outside-the-allowed-range"></a><span data-ttu-id="8f98c-102">Ensemble de délimiteurs non valide car au moins l'un des délimiteurs est en dehors de la plage autorisée</span><span class="sxs-lookup"><span data-stu-id="8f98c-102">Invalid delimiter set because at least one of the delimiters is outside the allowed range</span></span>
## <a name="details"></a><span data-ttu-id="8f98c-103">Détails</span><span class="sxs-lookup"><span data-stu-id="8f98c-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8f98c-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="8f98c-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="8f98c-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="8f98c-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="8f98c-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="8f98c-106">Event ID</span></span>|-|  
|<span data-ttu-id="8f98c-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="8f98c-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="8f98c-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="8f98c-108"> EDI</span></span>|  
|<span data-ttu-id="8f98c-109">Composant</span><span class="sxs-lookup"><span data-stu-id="8f98c-109">Component</span></span>|<span data-ttu-id="8f98c-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="8f98c-110">EDI Engine</span></span>|  
|<span data-ttu-id="8f98c-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="8f98c-111">Symbolic Name</span></span>|<span data-ttu-id="8f98c-112">DelimiterOutOfRange</span><span class="sxs-lookup"><span data-stu-id="8f98c-112">DelimiterOutOfRange</span></span>|  
|<span data-ttu-id="8f98c-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="8f98c-113">Message Text</span></span>|<span data-ttu-id="8f98c-114">Ensemble de délimiteurs {0} non valide, l'un au moins des délimiteurs est en dehors de la plage autorisée de 0 à 127</span><span class="sxs-lookup"><span data-stu-id="8f98c-114">Invalid delimiter set {0}, atleast one of the delimiters is outside the allowed range of 0 through 127</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="8f98c-115">Explication</span><span class="sxs-lookup"><span data-stu-id="8f98c-115">Explanation</span></span>  
 <span data-ttu-id="8f98c-116">Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline de réception n'a pas pu traiter l'échange entrant, car un ou plusieurs séparateurs de l'échange sont en dehors de la plage de valeurs du jeu de caractères ASCII.</span><span class="sxs-lookup"><span data-stu-id="8f98c-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange because one or more separators in the interchange was outside the range of values in the ASCII character set.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="8f98c-117">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="8f98c-117">User Action</span></span>  
 <span data-ttu-id="8f98c-118">Pour résoudre cette erreur, assurez-vous que chaque séparateur de l'échange fait partie du jeu de caractères ASCII, puis demandez à l'expéditeur de renvoyer l'échange.</span><span class="sxs-lookup"><span data-stu-id="8f98c-118">To resolve this error, make sure that each separator in the interchange is in the ASCII character set, and then have the interchange resent.</span></span>