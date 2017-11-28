---
title: "Set non pris en charge, car les informations de codage en UNB1.1 ne correspondent pas au codage réel de caractères | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 085ea8e3-e0d8-45bd-9985-6787b00e4d5a
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 41a6eafbb0e71de5f13e792361cdc0d1fc338088
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="character-set-not-supported-because-the-encoding-information-in-unb11-does-not-match-the-actual-encoding"></a><span data-ttu-id="8acc6-102">Jeu de caractères non pris en charge car les informations de codage en UNB1.1 ne correspondent pas au codage réel.</span><span class="sxs-lookup"><span data-stu-id="8acc6-102">Character set not supported because the encoding information in UNB1.1 does not match the actual encoding</span></span>
## <a name="details"></a><span data-ttu-id="8acc6-103">Détails</span><span class="sxs-lookup"><span data-stu-id="8acc6-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8acc6-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="8acc6-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="8acc6-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="8acc6-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="8acc6-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="8acc6-106">Event ID</span></span>|-|  
|<span data-ttu-id="8acc6-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="8acc6-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="8acc6-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="8acc6-108"> EDI</span></span>|  
|<span data-ttu-id="8acc6-109">Composant</span><span class="sxs-lookup"><span data-stu-id="8acc6-109">Component</span></span>|<span data-ttu-id="8acc6-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="8acc6-110">EDI Engine</span></span>|  
|<span data-ttu-id="8acc6-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="8acc6-111">Symbolic Name</span></span>|-|  
|<span data-ttu-id="8acc6-112">Texte du message</span><span class="sxs-lookup"><span data-stu-id="8acc6-112">Message Text</span></span>|<span data-ttu-id="8acc6-113">Jeu de caractères non pris en charge.</span><span class="sxs-lookup"><span data-stu-id="8acc6-113">Character set not supported.</span></span> <span data-ttu-id="8acc6-114">Ceci peut être dû au fait que les informations de codage en UNB1.1 ne correspondent pas au codage réel de l'échange.</span><span class="sxs-lookup"><span data-stu-id="8acc6-114">It could be due to the fact that encoding information in UNB1.1 does not match the actual encoding of the interchange.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="8acc6-115">Explication</span><span class="sxs-lookup"><span data-stu-id="8acc6-115">Explanation</span></span>  
 <span data-ttu-id="8acc6-116">Cet événement de type erreur/avertissement/information indique que le pipeline de réception EDI n'a pas pu traiter l'échange EDIFACT entrant, car les caractères utilisés dans l'échange n'étaient pas conformes au jeu de caractères identifié dans le champ UNB1.1 de l'échange.</span><span class="sxs-lookup"><span data-stu-id="8acc6-116">This Error/Warning/Information event indicates that the EDI receive pipeline could not process the incoming EDIFACT interchange because the characters used in the interchange did not conform to the character set identified in field UNB1.1 of the interchange.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="8acc6-117">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="8acc6-117">User Action</span></span>  
 <span data-ttu-id="8acc6-118">Pour résoudre cette erreur, effectuez l’une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="8acc6-118">To resolve this error, do one of the following:</span></span>  
  
-   <span data-ttu-id="8acc6-119">Modifiez les caractères utilisés dans l'échange afin qu'ils soient conformes au jeu de caractères défini dans le champ UNB1.1 de l'échange.</span><span class="sxs-lookup"><span data-stu-id="8acc6-119">Change the characters used in the interchange so they conform to the character set specified in field UNB1.1 of the interchange.</span></span>  
  
-   <span data-ttu-id="8acc6-120">Modifiez le jeu de caractères défini dans le champ UNB1.1 de l'échange, afin que tous les caractères de l'échange fassent partie du jeu de caractères.</span><span class="sxs-lookup"><span data-stu-id="8acc6-120">Change the character set specified in field UNB1.1 of the interchange, so all characters in the interchange are part of the character set.</span></span>