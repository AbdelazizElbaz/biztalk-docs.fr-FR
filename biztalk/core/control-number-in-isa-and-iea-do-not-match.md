---
title: "Numéro de contrôle dans ISA et IEA ne correspondent pas | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6f9091ea-460b-464b-acd5-8dc0488b61e5
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cd2f86d767b6065a6aeaa02f887dc8b6bd056fbb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="control-number-in-isa-and-iea-do-not-match"></a><span data-ttu-id="14490-102">Les numéros de contrôle dans ISA et IEA ne correspondent pas</span><span class="sxs-lookup"><span data-stu-id="14490-102">Control Number in ISA and IEA do not match</span></span>
## <a name="details"></a><span data-ttu-id="14490-103">Détails</span><span class="sxs-lookup"><span data-stu-id="14490-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="14490-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="14490-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="14490-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="14490-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="14490-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="14490-106">Event ID</span></span>|-|  
|<span data-ttu-id="14490-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="14490-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="14490-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="14490-108"> EDI</span></span>|  
|<span data-ttu-id="14490-109">Composant</span><span class="sxs-lookup"><span data-stu-id="14490-109">Component</span></span>|<span data-ttu-id="14490-110">Moteur AS2</span><span class="sxs-lookup"><span data-stu-id="14490-110">AS2 Engine</span></span>|  
|<span data-ttu-id="14490-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="14490-111">Symbolic Name</span></span>|-|  
|<span data-ttu-id="14490-112">Texte du message</span><span class="sxs-lookup"><span data-stu-id="14490-112">Message Text</span></span>|<span data-ttu-id="14490-113">Les numéros de contrôle dans ISA et IEA ne correspondent pas</span><span class="sxs-lookup"><span data-stu-id="14490-113">Control Number in ISA and IEA do not match</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="14490-114">Explication</span><span class="sxs-lookup"><span data-stu-id="14490-114">Explanation</span></span>  
 <span data-ttu-id="14490-115">Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline de réception AS2 n'a pas pu traiter l'échange entrant, car les numéros de contrôle de l'échange contenus dans les champs ISA13 et IEA02 de l'échange ne possèdent pas les mêmes valeurs.</span><span class="sxs-lookup"><span data-stu-id="14490-115">This Error/Warning/Information event indicates that the AS2 receive pipeline could not process the incoming interchange because the interchange control numbers contained in the ISA13 and IEA02 fields of the interchange do not have the same value.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="14490-116">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="14490-116">User Action</span></span>  
 <span data-ttu-id="14490-117">Pour résoudre cette erreur, assurez-vous que les numéros de contrôle de l'échange contenus dans les champs ISA13 et IEA02 de l'échange ont les mêmes valeurs, puis demandez à l'expéditeur de renvoyer l'échange.</span><span class="sxs-lookup"><span data-stu-id="14490-117">To resolve this error, make sure that the interchange control numbers contained in the ISA13 and IEA02 fields of the interchange have the same value, and then have the interchange resent.</span></span>