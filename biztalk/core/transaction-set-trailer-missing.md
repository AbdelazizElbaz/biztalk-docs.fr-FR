---
title: Code de fin manquante du jeu de transactions | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 07753300-fe47-47a6-a947-6abec10c1c90
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b7f1c153aa0bb62b6c62f4eeebf9d1fb9bea004b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="transaction-set-trailer-missing"></a><span data-ttu-id="51c44-102">Code de fin de document informatisé manquant</span><span class="sxs-lookup"><span data-stu-id="51c44-102">Transaction Set Trailer Missing</span></span>
## <a name="details"></a><span data-ttu-id="51c44-103">Détails</span><span class="sxs-lookup"><span data-stu-id="51c44-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="51c44-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="51c44-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="51c44-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="51c44-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="51c44-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="51c44-106">Event ID</span></span>|-|  
|<span data-ttu-id="51c44-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="51c44-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="51c44-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="51c44-108"> EDI</span></span>|  
|<span data-ttu-id="51c44-109">Composant</span><span class="sxs-lookup"><span data-stu-id="51c44-109">Component</span></span>|<span data-ttu-id="51c44-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="51c44-110">EDI Engine</span></span>|  
|<span data-ttu-id="51c44-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="51c44-111">Symbolic Name</span></span>|<span data-ttu-id="51c44-112">X12TsTrailerMissingDescription</span><span class="sxs-lookup"><span data-stu-id="51c44-112">X12TsTrailerMissingDescription</span></span>|  
|<span data-ttu-id="51c44-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="51c44-113">Message Text</span></span>|<span data-ttu-id="51c44-114">Code de fin de document informatisé manquant</span><span class="sxs-lookup"><span data-stu-id="51c44-114">Transaction Set Trailer Missing</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="51c44-115">Explication</span><span class="sxs-lookup"><span data-stu-id="51c44-115">Explanation</span></span>  
 <span data-ttu-id="51c44-116">Cet événement de type erreur/avertissement/information indique que le pipeline de réception n'a pas pu traiter le document informatisé entrant ou que le pipeline d'envoi n'a pas pu traiter le document informatisé sortant, car celui-ci n'incluait pas le code de fin de document informatisé SE (pour les documents informatisés X12) ou le code de fin de message UNT (pour les documents informatisés EDIFACT).</span><span class="sxs-lookup"><span data-stu-id="51c44-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming transaction set or the send pipeline could not process the outgoing transaction set because the transaction set did not include the SE transaction set trailer (for X12 transaction sets) or the UNT message trailer (for EDIFACT transaction sets).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="51c44-117">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="51c44-117">User Action</span></span>  
 <span data-ttu-id="51c44-118">Pour résoudre cette erreur, assurez-vous que l'expéditeur du document informatisé ajoute à celui-ci un code de fin de document informatisé SE (pour les documents informatisés X12) ou le code de fin de message UNT (pour les documents informatisés EDIFACT), puis renvoyez le document informatisé.</span><span class="sxs-lookup"><span data-stu-id="51c44-118">To resolve this error, have the sender of the transaction set add to the transaction set an SE transaction set trailer (for X12 transaction sets) or the UNT message trailer (for EDIFACT transaction sets), and then resend the transaction set.</span></span>