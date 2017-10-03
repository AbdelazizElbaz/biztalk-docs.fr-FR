---
title: "Schéma non trouvé pour CLR Namespace et rootName | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: db283d81-1cb0-460d-ace4-49a91ceb4a02
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 06db4a89803b8386ccbb45372b72423e83c6ff7c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="schema-not-found-for-clr-namespace-and-rootname"></a><span data-ttu-id="738e2-102">Schéma non trouvé pour CLR Namespace et rootName</span><span class="sxs-lookup"><span data-stu-id="738e2-102">Schema not found for CLR Namespace and rootName</span></span>
## <a name="details"></a><span data-ttu-id="738e2-103">Détails</span><span class="sxs-lookup"><span data-stu-id="738e2-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="738e2-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="738e2-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="738e2-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="738e2-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="738e2-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="738e2-106">Event ID</span></span>|-|  
|<span data-ttu-id="738e2-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="738e2-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="738e2-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="738e2-108"> EDI</span></span>|  
|<span data-ttu-id="738e2-109">Composant</span><span class="sxs-lookup"><span data-stu-id="738e2-109">Component</span></span>|<span data-ttu-id="738e2-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="738e2-110">EDI Engine</span></span>|  
|<span data-ttu-id="738e2-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="738e2-111">Symbolic Name</span></span>|<span data-ttu-id="738e2-112">SchemaNotFoundForCLRAndRN</span><span class="sxs-lookup"><span data-stu-id="738e2-112">SchemaNotFoundForCLRAndRN</span></span>|  
|<span data-ttu-id="738e2-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="738e2-113">Message Text</span></span>|<span data-ttu-id="738e2-114">Schéma non trouvé pour CLR Namespace = {0} et rootName = {{1}</span><span class="sxs-lookup"><span data-stu-id="738e2-114">Schema not found for CLR Namespace = {0} and rootName = {1}</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="738e2-115">Explication</span><span class="sxs-lookup"><span data-stu-id="738e2-115">Explanation</span></span>  
 <span data-ttu-id="738e2-116">Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline de réception n'a pas pu détecter le schéma de document à l'aide du nom racine associé à l'échange et à l'aide de l'espace de noms associé au tiers qui a été résolu pour l'échange.</span><span class="sxs-lookup"><span data-stu-id="738e2-116">This Error/Warning/Information event indicates that the receive pipeline could not find the document schema using the root name associated with the interchange and the namespace associated with the party that was resolved for the interchange.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="738e2-117">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="738e2-117">User Action</span></span>  
 <span data-ttu-id="738e2-118">Pour résoudre cette erreur, assurez-vous que le nom racine issu de l'échange et que l'espace de noms déterminé d'après les propriétés du tiers résolu correspondent tous deux au schéma déployé.</span><span class="sxs-lookup"><span data-stu-id="738e2-118">To resolve this error, ensure that the root name taken from the interchange and the namespace determined from the properties of the resolved party correspond together to a deployed schema.</span></span> <span data-ttu-id="738e2-119">BizTalk détermine le nom racine à partir du type et de la version du document de l'échange.</span><span class="sxs-lookup"><span data-stu-id="738e2-119">BizTalk determines the root name from the document type and version in the interchange.</span></span> <span data-ttu-id="738e2-120">Il identifie le schéma à partir du champ Espace de noms cible par défaut (pour les schémas par défaut) ou d'après la grille « Activer les définitions des documents informatisés personnalisés » (pour les schémas personnalisé) des propriétés de traitement de l'échange.</span><span class="sxs-lookup"><span data-stu-id="738e2-120">BizTalk determines the schema from the Default Target Namespace field (for default schemas) or the "Enable custom transaction set definitions" grid (for custom schemas) in the Interchange Processing Properties.</span></span>