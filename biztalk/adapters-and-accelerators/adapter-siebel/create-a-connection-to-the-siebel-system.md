---
title: "Créer une connexion au système Siebel | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: connecting, to the Siebel system
ms.assetid: 5810eeb1-6e26-4620-a731-fb352eebea2e
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a108335263e85db832f4db144d27b64b92429683
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="create-a-connection-to-the-siebel-system"></a><span data-ttu-id="8c93a-102">Créer une connexion au système Siebel</span><span class="sxs-lookup"><span data-stu-id="8c93a-102">Create a connection to the Siebel system</span></span>
<span data-ttu-id="8c93a-103">Le [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)] est un [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="8c93a-103">The [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)] is a [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] custom binding.</span></span> <span data-ttu-id="8c93a-104">Par conséquent, il permet la communication à un système Siebel via une adresse de point de terminaison WCF.</span><span class="sxs-lookup"><span data-stu-id="8c93a-104">As such, it enables communication to a Siebel system through a WCF endpoint address.</span></span> <span data-ttu-id="8c93a-105">Dans WCF, l’adresse de point de terminaison identifie l’emplacement réseau d’un service et est généralement exprimée comme une ressource identificateur URI (Uniform).</span><span class="sxs-lookup"><span data-stu-id="8c93a-105">In WCF the endpoint address identifies the network location of a service and is typically expressed as a Uniform Resource Identifier (URI).</span></span> <span data-ttu-id="8c93a-106">Le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] exprime cet emplacement en tant qu’URI qui contient des propriétés de connexion qui le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] utilise pour établir une connexion au système Siebel.</span><span class="sxs-lookup"><span data-stu-id="8c93a-106">The [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] expresses this location as a connection URI, which contains properties that the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] uses to establish a connection to the Siebel system.</span></span> <span data-ttu-id="8c93a-107">Vous devez spécifier un URI de connexion lorsque vous :</span><span class="sxs-lookup"><span data-stu-id="8c93a-107">You must specify a connection URI when you:</span></span>  
  
-   <span data-ttu-id="8c93a-108">Créer une fabrique de canaux ou d’un écouteur de canal à l’aide de la [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] modèle de canal, ou créer un hôte de service ou client WCF à l’aide de la [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] modèle de service.</span><span class="sxs-lookup"><span data-stu-id="8c93a-108">Create a channel factory or a channel listener using the [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] channel model, or create a WCF client or service host using the [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] service model.</span></span>  
  
-   <span data-ttu-id="8c93a-109">Créer une liaison de port physique dans un [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] solution.</span><span class="sxs-lookup"><span data-stu-id="8c93a-109">Create a physical port binding in a [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] solution.</span></span>  
  
-   <span data-ttu-id="8c93a-110">Utilisez le [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] pour générer une classe de client WCF ou une interface de service WCF pour un [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] solution de modèle de service.</span><span class="sxs-lookup"><span data-stu-id="8c93a-110">Use the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] to generate a WCF client class, or WCF service interface for a [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] service model solution.</span></span>  
  
-   <span data-ttu-id="8c93a-111">Utilisez le [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] pour extraire les schémas de message à partir de la [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] pour un [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] solution.</span><span class="sxs-lookup"><span data-stu-id="8c93a-111">Use the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] to retrieve message schemas from the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] for a [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] solution.</span></span>  
  
-   <span data-ttu-id="8c93a-112">Utilisez l’outil Service Model Metadata Utility (svcutil.exe) pour générer une classe de client WCF, ou une interface de service WCF pour une solution de modèle de service WCF.</span><span class="sxs-lookup"><span data-stu-id="8c93a-112">Use the ServiceModel Metadata Utility tool (svcutil.exe) to generate a WCF client class, or WCF service interface for a WCF service model solution.</span></span>  
  
 <span data-ttu-id="8c93a-113">Les rubriques de cette section décrivent comment établir une connexion entre le [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)] et le système Siebel en fournissant des :</span><span class="sxs-lookup"><span data-stu-id="8c93a-113">The topics in this section describe how to establish a connection between the [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)] and the Siebel system by providing you with:</span></span>  
  
-   <span data-ttu-id="8c93a-114">Informations sur les propriétés de connexion et la structure de l’URI de connexion Siebel.</span><span class="sxs-lookup"><span data-stu-id="8c93a-114">Information about the connection properties and the structure of the Siebel connection URI.</span></span>  
  
-   <span data-ttu-id="8c93a-115">Liens vers des rubriques qui montrent comment établir une connexion à l’aide de la [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8c93a-115">Links to topics that show how to establish a connection by using the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].</span></span>  
  

  
## <a name="see-also"></a><span data-ttu-id="8c93a-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8c93a-116">See Also</span></span>  
[<span data-ttu-id="8c93a-117">Développer vos applications Siebel</span><span class="sxs-lookup"><span data-stu-id="8c93a-117">Develop your Siebel applications</span></span>](../../adapters-and-accelerators/adapter-siebel/develop-your-siebel-applications.md)