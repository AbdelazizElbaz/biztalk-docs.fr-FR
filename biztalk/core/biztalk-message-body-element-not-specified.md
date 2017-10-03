---
title: "Élément de corps de message BizTalk non spécifié | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: af5d63c0-af96-4e34-828f-d29638cdf46d
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: baf79c8896169a06df66a8484377816c9897531e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="biztalk-message-body-element-not-specified"></a><span data-ttu-id="cc0a3-102">Élément corps de message BizTalk non spécifié</span><span class="sxs-lookup"><span data-stu-id="cc0a3-102">BizTalk message body element not specified</span></span>
## <a name="details"></a><span data-ttu-id="cc0a3-103">Détails</span><span class="sxs-lookup"><span data-stu-id="cc0a3-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="cc0a3-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="cc0a3-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="cc0a3-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="cc0a3-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="cc0a3-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="cc0a3-106">Event ID</span></span>|<span data-ttu-id="cc0a3-107">0</span><span class="sxs-lookup"><span data-stu-id="cc0a3-107">0</span></span>|  
|<span data-ttu-id="cc0a3-108">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="cc0a3-108">Event Source</span></span>|<span data-ttu-id="cc0a3-109">0</span><span class="sxs-lookup"><span data-stu-id="cc0a3-109">0</span></span>|  
|<span data-ttu-id="cc0a3-110">Composant</span><span class="sxs-lookup"><span data-stu-id="cc0a3-110">Component</span></span>|<span data-ttu-id="cc0a3-111">0</span><span class="sxs-lookup"><span data-stu-id="cc0a3-111">0</span></span>|  
|<span data-ttu-id="cc0a3-112">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="cc0a3-112">Symbolic Name</span></span>|<span data-ttu-id="cc0a3-113">0</span><span class="sxs-lookup"><span data-stu-id="cc0a3-113">0</span></span>|  
|<span data-ttu-id="cc0a3-114">Texte du message</span><span class="sxs-lookup"><span data-stu-id="cc0a3-114">Message Text</span></span>|<span data-ttu-id="cc0a3-115">Élément corps de message BizTalk non spécifié</span><span class="sxs-lookup"><span data-stu-id="cc0a3-115">BizTalk message body element not specified</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="cc0a3-116">Explication</span><span class="sxs-lookup"><span data-stu-id="cc0a3-116">Explanation</span></span>  
 <span data-ttu-id="cc0a3-117">Cette erreur indique l'utilisation de l'option de modèle pour le message WCF sortant.</span><span class="sxs-lookup"><span data-stu-id="cc0a3-117">This error indicates the use of the template option for the outbound WCF message.</span></span> <span data-ttu-id="cc0a3-118">Toutefois, l'expression de modèle ne contient pas d'élément de corps de message BizTalk.</span><span class="sxs-lookup"><span data-stu-id="cc0a3-118">However, the template expression doesn’t contain the BizTalk message body element.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="cc0a3-119">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="cc0a3-119">User Action</span></span>  
 <span data-ttu-id="cc0a3-120">Assurez-vous que l’expression de modèle contienne l’élément suivant : \< **bts-msg-body xmlns = « http://www.microsoft.com/schemas/bts2007 » encoding = « [xml &#124; base64 &#124; hex &#124; chaîne] » /** >.</span><span class="sxs-lookup"><span data-stu-id="cc0a3-120">Ensure that the template expression contains the following element: \<**bts-msg-body xmlns="http://www.microsoft.com/schemas/bts2007" encoding="[xml&#124;base64&#124;hex&#124;string]"/**>.</span></span>