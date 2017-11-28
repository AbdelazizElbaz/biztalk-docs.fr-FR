---
title: "Numéro de contrôle de groupe dans GS et GE ne correspondent pas | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e2419f61-2717-4347-a4be-54362330c7e3
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 05bb9e879e9a994215ba052fc3549d5bdb28e9fd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="group-control-number-in-gs-and-ge-do-not-match"></a><span data-ttu-id="a8d32-102">Les numéros de contrôle de groupe dans GS et GE sont différents</span><span class="sxs-lookup"><span data-stu-id="a8d32-102">Group control number in GS and GE do not match</span></span>
## <a name="details"></a><span data-ttu-id="a8d32-103">Détails</span><span class="sxs-lookup"><span data-stu-id="a8d32-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a8d32-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="a8d32-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="a8d32-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="a8d32-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="a8d32-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="a8d32-106">Event ID</span></span>|-|  
|<span data-ttu-id="a8d32-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="a8d32-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="a8d32-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="a8d32-108"> EDI</span></span>|  
|<span data-ttu-id="a8d32-109">Composant</span><span class="sxs-lookup"><span data-stu-id="a8d32-109">Component</span></span>|<span data-ttu-id="a8d32-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="a8d32-110">EDI Engine</span></span>|  
|<span data-ttu-id="a8d32-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="a8d32-111">Symbolic Name</span></span>|<span data-ttu-id="a8d32-112">X12FaControlNumberMismatchDescription</span><span class="sxs-lookup"><span data-stu-id="a8d32-112">X12FaControlNumberMismatchDescription</span></span>|  
|<span data-ttu-id="a8d32-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="a8d32-113">Message Text</span></span>|<span data-ttu-id="a8d32-114">Les numéros de contrôle de groupe dans GS et GE sont différents</span><span class="sxs-lookup"><span data-stu-id="a8d32-114">Group control number in GS and GE do not match</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="a8d32-115">Explication</span><span class="sxs-lookup"><span data-stu-id="a8d32-115">Explanation</span></span>  
 <span data-ttu-id="a8d32-116">Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline de réception n'a pas pu traiter l'échange X12 entrant, car les numéros de contrôle contenus dans les champs GS06 et GE02 de l'échange n'ont pas la même valeur.</span><span class="sxs-lookup"><span data-stu-id="a8d32-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming X12 interchange because the control numbers contained in the GS06 and GE02 fields of the  interchange do not have the same value.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="a8d32-117">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="a8d32-117">User Action</span></span>  
 <span data-ttu-id="a8d32-118">Pour résoudre cette erreur, assurez-vous que les numéros de contrôle du groupe contenus dans les champs GS06 et GE02 de l'échange ont la même valeur, puis demandez à l'expéditeur de renvoyer l'échange.</span><span class="sxs-lookup"><span data-stu-id="a8d32-118">To resolve this error, make sure that the group control numbers contained in the GS06 and GE02 fields of the interchange have the same value, and then have the interchange resent.</span></span>