---
title: Conversion de type du message sortant non reconnu | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e675112b-12f3-47ff-95f7-ce1a05db120e
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3928bde0d81a4fe22b7c16af41c3a4b6d5c7121c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="unrecognized-outbound-message-marshalling-type"></a><span data-ttu-id="cc2b0-102">Type de conversion du message sortant non reconnu</span><span class="sxs-lookup"><span data-stu-id="cc2b0-102">Unrecognized outbound message marshalling type</span></span>
## <a name="details"></a><span data-ttu-id="cc2b0-103">Détails</span><span class="sxs-lookup"><span data-stu-id="cc2b0-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="cc2b0-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="cc2b0-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="cc2b0-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="cc2b0-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="cc2b0-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="cc2b0-106">Event ID</span></span>|<span data-ttu-id="cc2b0-107">0</span><span class="sxs-lookup"><span data-stu-id="cc2b0-107">0</span></span>|  
|<span data-ttu-id="cc2b0-108">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="cc2b0-108">Event Source</span></span>|<span data-ttu-id="cc2b0-109">0</span><span class="sxs-lookup"><span data-stu-id="cc2b0-109">0</span></span>|  
|<span data-ttu-id="cc2b0-110">Composant</span><span class="sxs-lookup"><span data-stu-id="cc2b0-110">Component</span></span>|<span data-ttu-id="cc2b0-111">0</span><span class="sxs-lookup"><span data-stu-id="cc2b0-111">0</span></span>|  
|<span data-ttu-id="cc2b0-112">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="cc2b0-112">Symbolic Name</span></span>|<span data-ttu-id="cc2b0-113">0</span><span class="sxs-lookup"><span data-stu-id="cc2b0-113">0</span></span>|  
|<span data-ttu-id="cc2b0-114">Texte du message</span><span class="sxs-lookup"><span data-stu-id="cc2b0-114">Message Text</span></span>|<span data-ttu-id="cc2b0-115">Type de conversion du message sortant non reconnu ; UseBodyElement ou UseTemplate attendu</span><span class="sxs-lookup"><span data-stu-id="cc2b0-115">Unrecognized outbound message marshalling type; expected UseBodyElement or UseTemplate</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="cc2b0-116">Explication</span><span class="sxs-lookup"><span data-stu-id="cc2b0-116">Explanation</span></span>  
 <span data-ttu-id="cc2b0-117">La propriété .OutboundBodyLocation WCF est définie sur une autre valeur que UseBodyElement ou UseTemplate, dans un composant de pipeline personnalisé ou une orchestration.</span><span class="sxs-lookup"><span data-stu-id="cc2b0-117">The WCF.OutboundBodyLocation property is set to a value different than UseBodyElement or UseTemplate, in a custom pipeline component or orchestration.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="cc2b0-118">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="cc2b0-118">User Action</span></span>  
 <span data-ttu-id="cc2b0-119">Définissez la propriété WCF.OutboundBodyLocation sur une valeur valide.</span><span class="sxs-lookup"><span data-stu-id="cc2b0-119">Set the WCF.OutboundBodyLocation property to a valid value.</span></span> <span data-ttu-id="cc2b0-120">Les valeurs valides sont « UseBodyElement » ou « UseTemplate ». Vous devez les modifier dans le code.</span><span class="sxs-lookup"><span data-stu-id="cc2b0-120">Valid values are "UseBodyElement" or "UseTemplate" This is a code change.</span></span>   
<span data-ttu-id="cc2b0-121">Pour plus d’informations sur les messages sortants, consultez les ressources suivantes dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] aide :</span><span class="sxs-lookup"><span data-stu-id="cc2b0-121">For further information about outbound messaging, see the following resources in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="cc2b0-122">Configuration des Ports d’envoi dynamiques à l’aide des propriétés de contexte des adaptateurs WCF</span><span class="sxs-lookup"><span data-stu-id="cc2b0-122">Configuring Dynamic Send Ports Using WCF Adapters Context Properties</span></span>](../core/configuring-dynamic-send-ports-using-wcf-adapters-context-properties.md)  
  
-   [<span data-ttu-id="cc2b0-123">Configuration des adaptateurs WCF</span><span class="sxs-lookup"><span data-stu-id="cc2b0-123">Configuring the WCF Adapters</span></span>](../core/configuring-the-wcf-adapters.md)