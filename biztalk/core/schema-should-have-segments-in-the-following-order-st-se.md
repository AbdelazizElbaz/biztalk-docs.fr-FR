---
title: "Les segments du schéma doivent être placés dans l'ordre suivant ST ... SE | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8f4d1c6a-7d48-413a-9ef5-a0c49773dc16
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2563247dc6fc4c092fe2867c6b4d03239c4be7e1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="schema-should-have-segments-in-the-following-order-st--se"></a><span data-ttu-id="d534a-102">Les segments du schéma doivent être placés dans l'ordre suivant ST ... SE</span><span class="sxs-lookup"><span data-stu-id="d534a-102">Schema should have segments in the following order ST .... SE</span></span>
## <a name="details"></a><span data-ttu-id="d534a-103">Détails</span><span class="sxs-lookup"><span data-stu-id="d534a-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d534a-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="d534a-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="d534a-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="d534a-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="d534a-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="d534a-106">Event ID</span></span>|-|  
|<span data-ttu-id="d534a-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="d534a-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="d534a-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="d534a-108"> EDI</span></span>|  
|<span data-ttu-id="d534a-109">Composant</span><span class="sxs-lookup"><span data-stu-id="d534a-109">Component</span></span>|<span data-ttu-id="d534a-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="d534a-110">EDI Engine</span></span>|  
|<span data-ttu-id="d534a-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="d534a-111">Symbolic Name</span></span>|<span data-ttu-id="d534a-112">SchemaCode116ETransactionSetSchemaStSeOutOfOrder</span><span class="sxs-lookup"><span data-stu-id="d534a-112">SchemaCode116ETransactionSetSchemaStSeOutOfOrder</span></span>|  
|<span data-ttu-id="d534a-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="d534a-113">Message Text</span></span>|<span data-ttu-id="d534a-114">Les segments du schéma doivent être placés dans l'ordre suivant ST ... SE</span><span class="sxs-lookup"><span data-stu-id="d534a-114">Schema should have segments in the following order ST .... SE</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="d534a-115">Explication</span><span class="sxs-lookup"><span data-stu-id="d534a-115">Explanation</span></span>  
 <span data-ttu-id="d534a-116">Cet événement d'erreur/d'avertissement/d'informations indique qu'un schéma de document personnalisé n'est pas valide car les en-têtes et codes de fin n'étaient pas placés dans l'ordre approprié.</span><span class="sxs-lookup"><span data-stu-id="d534a-116">This Error/Warning/Information event indicates that a custom document schema is invalid because the headers and trailers were not in the correct order.</span></span> <span data-ttu-id="d534a-117">BizTalk Server effectue cette validation lorsque le schéma est déployé.</span><span class="sxs-lookup"><span data-stu-id="d534a-117">BizTalk Server performs this validation when the schema is deployed.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="d534a-118">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="d534a-118">User Action</span></span>  
 <span data-ttu-id="d534a-119">Pour résoudre cette erreur, modifiez le schéma de document personnalisé afin que les en-têtes et codes de fin soient placés dans l'ordre approprié, puis redéployez le schéma.</span><span class="sxs-lookup"><span data-stu-id="d534a-119">To resolve this error, change the customized document schema so that the headers and trailers are in the correct order, and then redeploy the schema.</span></span>