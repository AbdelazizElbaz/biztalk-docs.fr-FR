---
title: "OutboundCustomHeaders n’a pas le format correct | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6097762b-01c9-48b8-8cee-ccd6b11d28d4
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b3b81a8c9c605f646a8ac0b6df2045af05eb58e5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="outboundcustomheaders-does-not-have-correct-format"></a><span data-ttu-id="cfa38-102">OutboundCustomHeaders n’a pas le format correct</span><span class="sxs-lookup"><span data-stu-id="cfa38-102">OutboundCustomHeaders does not have correct format</span></span>
## <a name="details"></a><span data-ttu-id="cfa38-103">Détails</span><span class="sxs-lookup"><span data-stu-id="cfa38-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="cfa38-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="cfa38-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="cfa38-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="cfa38-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="cfa38-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="cfa38-106">Event ID</span></span>|<span data-ttu-id="cfa38-107">0</span><span class="sxs-lookup"><span data-stu-id="cfa38-107">0</span></span>|  
|<span data-ttu-id="cfa38-108">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="cfa38-108">Event Source</span></span>|<span data-ttu-id="cfa38-109">0</span><span class="sxs-lookup"><span data-stu-id="cfa38-109">0</span></span>|  
|<span data-ttu-id="cfa38-110">Composant</span><span class="sxs-lookup"><span data-stu-id="cfa38-110">Component</span></span>|<span data-ttu-id="cfa38-111">0</span><span class="sxs-lookup"><span data-stu-id="cfa38-111">0</span></span>|  
|<span data-ttu-id="cfa38-112">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="cfa38-112">Symbolic Name</span></span>|<span data-ttu-id="cfa38-113">0</span><span class="sxs-lookup"><span data-stu-id="cfa38-113">0</span></span>|  
|<span data-ttu-id="cfa38-114">Texte du message</span><span class="sxs-lookup"><span data-stu-id="cfa38-114">Message Text</span></span>|<span data-ttu-id="cfa38-115">OutboundCustomHeaders n'a pas le format correct</span><span class="sxs-lookup"><span data-stu-id="cfa38-115">OutboundCustomHeaders does not have a correct format</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="cfa38-116">Explication</span><span class="sxs-lookup"><span data-stu-id="cfa38-116">Explanation</span></span>  
 <span data-ttu-id="cfa38-117">La valeur de WCF. InboundHeaders ou WCF. OutboundCustomHeaders n’est pas dans le format suivant : \<en-têtes >...\</headers >.</span><span class="sxs-lookup"><span data-stu-id="cfa38-117">The value of WCF.InboundHeaders or WCF.OutboundCustomHeaders  is not in the following format: \<headers>….\</headers>.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="cfa38-118">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="cfa38-118">User Action</span></span>  
 <span data-ttu-id="cfa38-119">Retour à la ligne avec les valeurs de propriété \<en-têtes > élément.</span><span class="sxs-lookup"><span data-stu-id="cfa38-119">Wrap the property values with \<headers> element.</span></span>  
  
 <span data-ttu-id="cfa38-120">Pour plus d'informations, consultez la ressource suivante dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="cfa38-120">For further information, see the following resource in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="cfa38-121">Utilisation des en-têtes SOAP des Messages WCF avec les composants de Pipeline</span><span class="sxs-lookup"><span data-stu-id="cfa38-121">Using SOAP Headers in WCF Messages with Pipeline Components</span></span>](../core/using-soap-headers-in-wcf-messages-with-pipeline-components.md)