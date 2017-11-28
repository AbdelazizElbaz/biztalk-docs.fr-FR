---
title: "Contenu de l’échange non valide | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6b2352c3-d233-4d79-be31-b32dde29c8ee
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d03dc518406083cda1b070a3358cc4d8967f5f07
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="invalid-interchange-content"></a><span data-ttu-id="84d78-102">Contenu de l'échange non valide</span><span class="sxs-lookup"><span data-stu-id="84d78-102">Invalid Interchange Content</span></span>
## <a name="details"></a><span data-ttu-id="84d78-103">Détails</span><span class="sxs-lookup"><span data-stu-id="84d78-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="84d78-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="84d78-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="84d78-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="84d78-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="84d78-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="84d78-106">Event ID</span></span>|-|  
|<span data-ttu-id="84d78-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="84d78-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="84d78-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="84d78-108"> EDI</span></span>|  
|<span data-ttu-id="84d78-109">Composant</span><span class="sxs-lookup"><span data-stu-id="84d78-109">Component</span></span>|<span data-ttu-id="84d78-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="84d78-110">EDI Engine</span></span>|  
|<span data-ttu-id="84d78-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="84d78-111">Symbolic Name</span></span>|<span data-ttu-id="84d78-112">X12Ta1InvalidInterchangeContentDescription</span><span class="sxs-lookup"><span data-stu-id="84d78-112">X12Ta1InvalidInterchangeContentDescription</span></span>|  
|<span data-ttu-id="84d78-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="84d78-113">Message Text</span></span>|<span data-ttu-id="84d78-114">Contenu de l'échange non valide</span><span class="sxs-lookup"><span data-stu-id="84d78-114">Invalid Interchange Content</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="84d78-115">Explication</span><span class="sxs-lookup"><span data-stu-id="84d78-115">Explanation</span></span>  
 <span data-ttu-id="84d78-116">Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline de réception n'a pas pu traiter l'échange entrant ou que le pipeline d'envoi n'a pas pu traiter l'échange sortant, car la validation de message réalisée par BizTalk Server sur les données contenues dans l'échange a échoué.</span><span class="sxs-lookup"><span data-stu-id="84d78-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange or the send pipeline could not process the outgoing interchange because the data in the interchange did not pass message validation performed by BizTalk Server.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="84d78-117">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="84d78-117">User Action</span></span>  
 <span data-ttu-id="84d78-118">Pour résoudre cette erreur, identifiez les parties de l'échange pour lesquelles la validation a échoué ainsi que le type de validation qu'elles n'ont pas réussi.</span><span class="sxs-lookup"><span data-stu-id="84d78-118">To resolve this error, identify which part of the interchange failed validation, and which validation it failed.</span></span> <span data-ttu-id="84d78-119">Résolvez le problème qui a provoqué l'échec de la validation, puis demandez à l'expéditeur de renvoyer l'échange.</span><span class="sxs-lookup"><span data-stu-id="84d78-119">Resolve the issue that caused validation to fail, and then have the interchange resent.</span></span>