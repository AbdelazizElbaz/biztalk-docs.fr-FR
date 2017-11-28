---
title: "Schéma du document informatisé contient un ou plusieurs des contrôle les segments ISA, IEA, GS, GE | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7589d8f0-c727-47df-afbc-77b0f190f3e2
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ff90a7ea80208f0a69ee8aca5c7593c7b6253c53
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="transaction-set-schema-contains-one-or-more-of-control-segments-isa-iea-gs-ge"></a><span data-ttu-id="7b680-102">Le schéma du document informatisé contient un ou plusieurs segments de contrôle ISA, IEA, GS, GE</span><span class="sxs-lookup"><span data-stu-id="7b680-102">Transaction set schema contains one or more of control segments ISA, IEA, GS, GE</span></span>
## <a name="details"></a><span data-ttu-id="7b680-103">Détails</span><span class="sxs-lookup"><span data-stu-id="7b680-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7b680-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="7b680-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="7b680-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="7b680-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="7b680-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="7b680-106">Event ID</span></span>|-|  
|<span data-ttu-id="7b680-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="7b680-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="7b680-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="7b680-108"> EDI</span></span>|  
|<span data-ttu-id="7b680-109">Composant</span><span class="sxs-lookup"><span data-stu-id="7b680-109">Component</span></span>|<span data-ttu-id="7b680-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="7b680-110">EDI Engine</span></span>|  
|<span data-ttu-id="7b680-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="7b680-111">Symbolic Name</span></span>|<span data-ttu-id="7b680-112">SchemaCode114EOtherControlSegmentsPresent</span><span class="sxs-lookup"><span data-stu-id="7b680-112">SchemaCode114EOtherControlSegmentsPresent</span></span>|  
|<span data-ttu-id="7b680-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="7b680-113">Message Text</span></span>|<span data-ttu-id="7b680-114">Le schéma du document informatisé contient un ou plusieurs segments de contrôle ISA, IEA, GS, GE</span><span class="sxs-lookup"><span data-stu-id="7b680-114">Transaction set schema contains one or more of control segments ISA, IEA, GS, GE</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="7b680-115">Explication</span><span class="sxs-lookup"><span data-stu-id="7b680-115">Explanation</span></span>  
 <span data-ttu-id="7b680-116">Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline de réception n'a pas pu traiter le document informatisé entrant ou que le pipeline d'envoi n'a pas pu traiter le document informatisé sortant, car le schéma du document informatisé impose la présence d'au moins un segment ISA, IEA, GS ou GE.</span><span class="sxs-lookup"><span data-stu-id="7b680-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming transaction set or the send pipeline could not process the outgoing transaction set because the document schema for the transaction set defined at least one ISA, IEA, GS, or GE segment.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="7b680-117">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="7b680-117">User Action</span></span>  
 <span data-ttu-id="7b680-118">Pour résoudre cette erreur, annulez le déploiement du schéma de document, supprimez le segment ISA, IEA, GS ou GE du schéma, puis redéployez-le.</span><span class="sxs-lookup"><span data-stu-id="7b680-118">To resolve this error, undeploy the document schema, remove the ISA, IEA, GS, or GE segment from the schema, and then redeploy the schema.</span></span>