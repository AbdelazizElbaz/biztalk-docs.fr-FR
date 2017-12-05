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
ms.openlocfilehash: df751526661ddef455be45c4258c331c940fdd47
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="outboundcustomheaders-does-not-have-correct-format"></a><span data-ttu-id="5edc0-102">OutboundCustomHeaders n’a pas le format correct</span><span class="sxs-lookup"><span data-stu-id="5edc0-102">OutboundCustomHeaders does not have correct format</span></span>
## <a name="details"></a><span data-ttu-id="5edc0-103">Détails</span><span class="sxs-lookup"><span data-stu-id="5edc0-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5edc0-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="5edc0-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="5edc0-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="5edc0-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="5edc0-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="5edc0-106">Event ID</span></span>|<span data-ttu-id="5edc0-107">0</span><span class="sxs-lookup"><span data-stu-id="5edc0-107">0</span></span>|  
|<span data-ttu-id="5edc0-108">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="5edc0-108">Event Source</span></span>|<span data-ttu-id="5edc0-109">0</span><span class="sxs-lookup"><span data-stu-id="5edc0-109">0</span></span>|  
|<span data-ttu-id="5edc0-110">Composant</span><span class="sxs-lookup"><span data-stu-id="5edc0-110">Component</span></span>|<span data-ttu-id="5edc0-111">0</span><span class="sxs-lookup"><span data-stu-id="5edc0-111">0</span></span>|  
|<span data-ttu-id="5edc0-112">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="5edc0-112">Symbolic Name</span></span>|<span data-ttu-id="5edc0-113">0</span><span class="sxs-lookup"><span data-stu-id="5edc0-113">0</span></span>|  
|<span data-ttu-id="5edc0-114">Texte du message</span><span class="sxs-lookup"><span data-stu-id="5edc0-114">Message Text</span></span>|<span data-ttu-id="5edc0-115">OutboundCustomHeaders n'a pas le format correct</span><span class="sxs-lookup"><span data-stu-id="5edc0-115">OutboundCustomHeaders does not have a correct format</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="5edc0-116">Explication</span><span class="sxs-lookup"><span data-stu-id="5edc0-116">Explanation</span></span>  
 <span data-ttu-id="5edc0-117">La valeur de WCF. InboundHeaders ou WCF. OutboundCustomHeaders n’est pas dans le format suivant : \<en-têtes\>...\</headers\>.</span><span class="sxs-lookup"><span data-stu-id="5edc0-117">The value of WCF.InboundHeaders or WCF.OutboundCustomHeaders  is not in the following format: \<headers\>….\</headers\>.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="5edc0-118">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="5edc0-118">User Action</span></span>  
 <span data-ttu-id="5edc0-119">Retour à la ligne avec les valeurs de propriété \<en-têtes\> élément.</span><span class="sxs-lookup"><span data-stu-id="5edc0-119">Wrap the property values with \<headers\> element.</span></span>  
  
 <span data-ttu-id="5edc0-120">Pour plus d'informations, consultez la ressource suivante dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="5edc0-120">For further information, see the following resource in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="5edc0-121">Utilisation des en-têtes SOAP dans les messages WCF avec des composants de pipeline</span><span class="sxs-lookup"><span data-stu-id="5edc0-121">Using SOAP Headers in WCF Messages with Pipeline Components</span></span>](../core/using-soap-headers-in-wcf-messages-with-pipeline-components.md)