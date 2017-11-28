---
title: "L’échange contenait un ISA incorrect ou le schéma de Service n’était pas disponible | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 78d285f6-26fb-4a3b-a959-a17623321b20
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 84aec7600b71d48becfdeb30e34f837292c5ecfa
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-interchange-contained-a-malformed-isa-or-the-service-schema-was-not-available"></a><span data-ttu-id="335ab-102">L'échange contenait un ISA incorrect ou le schéma Service n'était pas disponible</span><span class="sxs-lookup"><span data-stu-id="335ab-102">The interchange contained a malformed ISA or the Service schema was not available</span></span>
## <a name="details"></a><span data-ttu-id="335ab-103">Détails</span><span class="sxs-lookup"><span data-stu-id="335ab-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="335ab-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="335ab-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="335ab-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="335ab-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="335ab-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="335ab-106">Event ID</span></span>|-|  
|<span data-ttu-id="335ab-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="335ab-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="335ab-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="335ab-108"> EDI</span></span>|  
|<span data-ttu-id="335ab-109">Composant</span><span class="sxs-lookup"><span data-stu-id="335ab-109">Component</span></span>|<span data-ttu-id="335ab-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="335ab-110">EDI Engine</span></span>|  
|<span data-ttu-id="335ab-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="335ab-111">Symbolic Name</span></span>|<span data-ttu-id="335ab-112">MalformedIsaError</span><span class="sxs-lookup"><span data-stu-id="335ab-112">MalformedIsaError</span></span>|  
|<span data-ttu-id="335ab-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="335ab-113">Message Text</span></span>|<span data-ttu-id="335ab-114">L'échange contenait un ISA incorrect ou le schéma Service n'était pas disponible, il est entièrement rejeté</span><span class="sxs-lookup"><span data-stu-id="335ab-114">The interchange contained a malformed ISA or the Service schema was not available, it is being rejected completely</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="335ab-115">Explication</span><span class="sxs-lookup"><span data-stu-id="335ab-115">Explanation</span></span>  
 <span data-ttu-id="335ab-116">Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline de réception n'a pas pu traiter l'échange entrant, car le segment ISA ou IEA n'est pas conforme au X12ServiceSchema, ou X12ServiceSchema (dans BaseArtifacts.dll) n'est pas déployé.</span><span class="sxs-lookup"><span data-stu-id="335ab-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange, because the ISA or IEA segments in the interchange did not conform to the X12ServiceSchema, or the X12ServiceSchema (in BaseArtifacts.dll) was not deployed.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="335ab-117">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="335ab-117">User Action</span></span>  
 <span data-ttu-id="335ab-118">Pour résoudre cette erreur, effectuez l’une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="335ab-118">To resolve this error, do one of the following:</span></span>  
  
-   <span data-ttu-id="335ab-119">Demandez à l'expéditeur de l'échange de modifier les segments ISA et IEA de manière à ce qu'ils soient conformes au X12ServiceSchema.</span><span class="sxs-lookup"><span data-stu-id="335ab-119">Have the sender of the interchange change the ISA and IEA segments so that they conform to the X12ServiceSchema.</span></span>  
  
-   <span data-ttu-id="335ab-120">Assurez-vous que le fichier BaseArtifacts.dll inclut le X12ServiceSchema et que ce dernier est déployé.</span><span class="sxs-lookup"><span data-stu-id="335ab-120">Ensure that BaseArtifacts.dll includes the X12ServiceSchema and is deployed.</span></span> <span data-ttu-id="335ab-121">Pour ce faire, ouvrez la console Administration de BizTalk Server, développez successivement le nœud Application BizTalk EDI, le nœud Schémas, puis vérifiez que X12ServiceSchema est bien répertorié.</span><span class="sxs-lookup"><span data-stu-id="335ab-121">You can do so by opening the BizTalk Server Administration Console, opening the BizTalk EDI Application node and then the Schemas node, and verifying that X12ServiceSchema is listed.</span></span>