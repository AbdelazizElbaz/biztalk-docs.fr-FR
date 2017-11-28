---
title: "Valeur non valide d’autorisation | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 70d0dd75-b045-4b67-ba23-78551493f074
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b4e83d35e379babeedca783fa8eb00774ccf05ea
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="invalid-authorization-value"></a><span data-ttu-id="bb8b1-102">Valeur Autorisation non valide</span><span class="sxs-lookup"><span data-stu-id="bb8b1-102">Invalid Authorization Value</span></span>
## <a name="details"></a><span data-ttu-id="bb8b1-103">Détails</span><span class="sxs-lookup"><span data-stu-id="bb8b1-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="bb8b1-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="bb8b1-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="bb8b1-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="bb8b1-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="bb8b1-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="bb8b1-106">Event ID</span></span>|-|  
|<span data-ttu-id="bb8b1-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="bb8b1-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="bb8b1-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="bb8b1-108"> EDI</span></span>|  
|<span data-ttu-id="bb8b1-109">Composant</span><span class="sxs-lookup"><span data-stu-id="bb8b1-109">Component</span></span>|<span data-ttu-id="bb8b1-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="bb8b1-110">EDI Engine</span></span>|  
|<span data-ttu-id="bb8b1-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="bb8b1-111">Symbolic Name</span></span>|<span data-ttu-id="bb8b1-112">X12Ta1InvalidAuthorizationValueDescription</span><span class="sxs-lookup"><span data-stu-id="bb8b1-112">X12Ta1InvalidAuthorizationValueDescription</span></span>|  
|<span data-ttu-id="bb8b1-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="bb8b1-113">Message Text</span></span>|<span data-ttu-id="bb8b1-114">Valeur Autorisation non valide</span><span class="sxs-lookup"><span data-stu-id="bb8b1-114">Invalid Authorization Value</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="bb8b1-115">Explication</span><span class="sxs-lookup"><span data-stu-id="bb8b1-115">Explanation</span></span>  
 <span data-ttu-id="bb8b1-116">Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline de réception n'a pas pu traiter l'échange entrant, car les valeurs des informations d'autorisation dans ISA02 ne sont pas conformes au type de données spécifié par le schéma (X12_AN) ou que ces données ne comportent pas le même nombre de chiffres requis par le schéma (10).</span><span class="sxs-lookup"><span data-stu-id="bb8b1-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange because the value of the Authorization Information in ISA02 did not conform to the data type specified by the schema (X12_AN), or did not have the number of digits required by the schema (10).</span></span> <span data-ttu-id="bb8b1-117">Le schéma est le X12ServiceSchema dans BaseArtifacts.dll.</span><span class="sxs-lookup"><span data-stu-id="bb8b1-117">The schema is the X12ServiceSchema in BaseArtifacts.dll.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="bb8b1-118">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="bb8b1-118">User Action</span></span>  
 <span data-ttu-id="bb8b1-119">Pour résoudre cette erreur, assurez-vous que la valeur de l'en-tête ISA02 est conforme au type de données X12:AN et qu'elle comporte 10 chiffres (espaces de fin compris), puis demandez à l'expéditeur de renvoyer l'échange.</span><span class="sxs-lookup"><span data-stu-id="bb8b1-119">To resolve this error, make sure that the value in the ISA02 header conforms to the X12:AN data type and has 10 digits (with trailing spaces), and then have the interchange resent.</span></span>