---
title: "Le composant d’itinéraire ESB | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 379edc6a-7d53-4338-87a5-47b5238453a4
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 80aa7c1ef4bc53ad2e2821eaf8dc4184777900a3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-esb-itinerary-component"></a><span data-ttu-id="991f3-102">Le composant d’itinéraire ESB</span><span class="sxs-lookup"><span data-stu-id="991f3-102">The ESB Itinerary Component</span></span>
<span data-ttu-id="991f3-103">Le composant de la feuille de route ESB définit les propriétés de contexte à partir de l’en-tête SOAP envoyée avec le message pour un ESB d’itinéraire rampe d’entrée.</span><span class="sxs-lookup"><span data-stu-id="991f3-103">The ESB Itinerary component sets the context properties from the SOAP header sent along with the message to an ESB itinerary on-ramp.</span></span>  
  
## <a name="installation"></a><span data-ttu-id="991f3-104">Installation</span><span class="sxs-lookup"><span data-stu-id="991f3-104">Installation</span></span>  
 <span data-ttu-id="991f3-105">L’installation du noyau ESB installe automatiquement le **itinéraire** composant de pipeline dans le dossier composants de Pipeline BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="991f3-105">Installing the ESB Core automatically installs the **Itinerary** pipeline component in the BizTalk Server Pipeline Components folder.</span></span>  
  
## <a name="how-it-works"></a><span data-ttu-id="991f3-106">Fonctionnement</span><span class="sxs-lookup"><span data-stu-id="991f3-106">How It Works</span></span>  
 <span data-ttu-id="991f3-107">Le composant de la feuille de route ESB est un composant de pipeline Microsoft BizTalk qui peut résider que dans un pipeline de réception.</span><span class="sxs-lookup"><span data-stu-id="991f3-107">The ESB Itinerary component is a Microsoft BizTalk pipeline component that can reside only in a receive pipeline.</span></span> <span data-ttu-id="991f3-108">Il promeut les valeurs à partir des en-têtes de message SOAP ou des paramètres de composant dans le contexte du message en tant que propriétés.</span><span class="sxs-lookup"><span data-stu-id="991f3-108">It promotes values from either SOAP message headers or component settings into the message context as properties.</span></span> <span data-ttu-id="991f3-109">Vous trouverez un exemple de promouvoir des en-têtes SOAP dans les services Web de rampe d’entrée d’itinéraire fournis avec [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)].</span><span class="sxs-lookup"><span data-stu-id="991f3-109">You can find an example of promoting SOAP headers in the Itinerary On-Ramp Web services provided with [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)].</span></span> <span data-ttu-id="991f3-110">Ces services Web exposent des en-têtes SOAP dans le cadre de leur contrat, et les applications clientes doivent définir les en-têtes.</span><span class="sxs-lookup"><span data-stu-id="991f3-110">These Web services expose SOAP headers as part of their contracts, and client applications must set the headers.</span></span> <span data-ttu-id="991f3-111">Comme le message passe par le composant dans un pipeline de réception, le composant lit les valeurs de l’en-tête SOAP et promeut (écritures) vers les propriétés de contexte de message.</span><span class="sxs-lookup"><span data-stu-id="991f3-111">As the message passes through the component in a receive pipeline, the component reads the SOAP header values and promotes (writes) them to the message context properties.</span></span>  
  
## <a name="using-the-esb-itinerary-component"></a><span data-ttu-id="991f3-112">À l’aide du composant d’itinéraire ESB</span><span class="sxs-lookup"><span data-stu-id="991f3-112">Using the ESB Itinerary Component</span></span>  
 <span data-ttu-id="991f3-113">Vous pouvez ajouter le composant de la feuille de route ESB à un pipeline de réception et ensuite utiliser le pipeline dans un emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="991f3-113">You can add the ESB Itinerary component to a receive pipeline and then use the pipeline in a receive location.</span></span> <span data-ttu-id="991f3-114">Le composant promeut automatiquement les valeurs d’en-tête SOAP ou des paramètres du composant dans les propriétés de contexte du message entrant.</span><span class="sxs-lookup"><span data-stu-id="991f3-114">The component automatically promotes SOAP header values or component settings into the context properties of the incoming message.</span></span>  
  
 <span data-ttu-id="991f3-115">Pour obtenir un exemple d’utilisation de ce composant, consultez [l’installation et l’exécution de l’exemple de rampe d’entrée d’itinéraire](../esb-toolkit/installing-and-running-the-itinerary-on-ramp-sample.md).</span><span class="sxs-lookup"><span data-stu-id="991f3-115">For an example of how to use this component, see [Installing and Running the Itinerary On-Ramp Sample](../esb-toolkit/installing-and-running-the-itinerary-on-ramp-sample.md).</span></span>