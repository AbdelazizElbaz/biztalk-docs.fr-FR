---
title: "Créer une connexion au système SAP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SAP system, connecting to
- connection URI
- URI
- Uniform Resource Identifier
ms.assetid: 25d1eaa7-d02a-4fd0-8adf-83505cdb1ab8
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c9835047fd32556e6bd9f42adb768ce62f4536ff
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="create-a-connection-to-the-sap-system"></a><span data-ttu-id="c373c-102">Créer une connexion au système SAP</span><span class="sxs-lookup"><span data-stu-id="c373c-102">Create a connection to the SAP system</span></span>
<span data-ttu-id="c373c-103">Le [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] est un [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="c373c-103">The [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] is a [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] custom binding.</span></span> <span data-ttu-id="c373c-104">Par conséquent, il permet la communication sur un système SAP via une adresse de point de terminaison WCF.</span><span class="sxs-lookup"><span data-stu-id="c373c-104">As such, it enables communication to an SAP system through a WCF endpoint address.</span></span> <span data-ttu-id="c373c-105">Dans WCF, l’adresse de point de terminaison identifie l’emplacement réseau d’un service et est généralement exprimée comme une ressource identificateur URI (Uniform).</span><span class="sxs-lookup"><span data-stu-id="c373c-105">In WCF the endpoint address identifies the network location of a service and is typically expressed as a Uniform Resource Identifier (URI).</span></span> <span data-ttu-id="c373c-106">Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] exprime cet emplacement en tant qu’URI qui contient des propriétés de connexion qui le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] utilise pour établir une connexion au système SAP.</span><span class="sxs-lookup"><span data-stu-id="c373c-106">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] expresses this location as a connection URI, which contains properties that the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] uses to establish a connection to the SAP system.</span></span> <span data-ttu-id="c373c-107">Vous devez spécifier un URI de connexion lorsque vous :</span><span class="sxs-lookup"><span data-stu-id="c373c-107">You must specify a connection URI when you:</span></span>  
  
-   <span data-ttu-id="c373c-108">Lorsque vous créez une fabrication de canal ou un écouteur de canal à l’aide de la [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] modèle de canal ou lorsque vous créez un hôte de service ou client WCF à l’aide de la [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] modèle de service.</span><span class="sxs-lookup"><span data-stu-id="c373c-108">When you create a channel factory or a channel listener using the [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] channel model or when you create a WCF client or service host using the [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] service model.</span></span>  
  
-   <span data-ttu-id="c373c-109">Créer une liaison de port physique dans un [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] solution.</span><span class="sxs-lookup"><span data-stu-id="c373c-109">Create a physical port binding in a [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] solution.</span></span>  
  
-   <span data-ttu-id="c373c-110">Utilisez le [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] pour générer une classe de client WCF ou l’interface de service WCF pour un [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] solution de modèle de service.</span><span class="sxs-lookup"><span data-stu-id="c373c-110">Use the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] to generate a WCF client class or WCF service interface for a [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] service model solution.</span></span>  
  
-   <span data-ttu-id="c373c-111">Utilisez le [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] pour extraire les schémas de message à partir de la [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] pour un [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] solution.</span><span class="sxs-lookup"><span data-stu-id="c373c-111">Use the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] to retrieve message schemas from the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] for a [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] solution.</span></span>  
  
-   <span data-ttu-id="c373c-112">Utilisez l’outil Service Model Metadata Utility (svcutil.exe) pour générer une classe de client WCF ou l’interface de service WCF pour une solution de modèle de service WCF.</span><span class="sxs-lookup"><span data-stu-id="c373c-112">Use the ServiceModel Metadata Utility tool (svcutil.exe) to generate a WCF client class or WCF service interface for a WCF service model solution.</span></span>  
  
 <span data-ttu-id="c373c-113">Les rubriques de cette section décrivent comment établir une connexion entre le [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] et le système SAP en fournissant des :</span><span class="sxs-lookup"><span data-stu-id="c373c-113">The topics in this section describe how to establish a connection between the [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] and the SAP system by providing you with:</span></span>  
  
-   <span data-ttu-id="c373c-114">Informations sur les propriétés de connexion et la structure de l’URI de connexion SAP.</span><span class="sxs-lookup"><span data-stu-id="c373c-114">Information about the connection properties and the structure of the SAP connection URI.</span></span>  
  
-   <span data-ttu-id="c373c-115">Liens vers des rubriques qui montrent comment établir une connexion à l’aide de la [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c373c-115">Links to topics that show how to establish a connection by using the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c373c-116">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="c373c-116">In This Section</span></span>  
  
-   [<span data-ttu-id="c373c-117">Créer l’URI de connexion au système SAP</span><span class="sxs-lookup"><span data-stu-id="c373c-117">Create the SAP system connection URI</span></span>](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md)