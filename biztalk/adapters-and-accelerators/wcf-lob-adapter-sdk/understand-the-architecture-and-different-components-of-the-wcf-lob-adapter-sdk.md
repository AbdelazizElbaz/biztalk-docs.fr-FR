---
title: "Comprendre l’architecture et les différents composants du SDK adaptateur LOB WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 293189be-61d7-44f4-8ba6-e5550516d9b4
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: feea57176512bb42306feb8b60a10a887a020145
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="understand-the-architecture-and-different-components-of-the-wcf-lob-adapter-sdk"></a><span data-ttu-id="a52e9-102">Comprendre l’architecture et les différents composants du SDK adaptateur LOB WCF</span><span class="sxs-lookup"><span data-stu-id="a52e9-102">Understand the architecture and different components of the WCF LOB Adapter SDK</span></span>
<span data-ttu-id="a52e9-103">En savoir plus sur les [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] pour aider à comprendre les différents composants et le rôle de WCF.</span><span class="sxs-lookup"><span data-stu-id="a52e9-103">Read about the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] to help understand the different components, and the role of WCF.</span></span>  

<span data-ttu-id="a52e9-104">Le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] est une collection d’outils et composants qui fournissent un cadre cohérent pour le développement d’adaptateurs réutilisables et riches en métadonnées pour les systèmes de line-of-business.</span><span class="sxs-lookup"><span data-stu-id="a52e9-104">The [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] is a collection of tools and components that provide a consistent framework for developing reusable, metadata-rich adapters for line-of-business systems.</span></span> <span data-ttu-id="a52e9-105">Adaptateurs écrits à l’aide de la [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] sont signalées en tant que liaisons WCF personnalisées et peuvent être utilisés par un client compatible WCF.</span><span class="sxs-lookup"><span data-stu-id="a52e9-105">Adapters written using the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] are surfaced as custom WCF bindings and can be consumed by a WCF-capable client.</span></span>  
  
## <a name="features-and-components-overview"></a><span data-ttu-id="a52e9-106">Vue d’ensemble des composants et fonctionnalités</span><span class="sxs-lookup"><span data-stu-id="a52e9-106">Features and components overview</span></span>
<span data-ttu-id="a52e9-107">[Quel est le Windows Communication Foundation ligne de Business Adapter SDK](what-is-the-windows-communication-foundation-line-of-business-adapter-sdk.md) fournit une vue d’ensemble des fonctionnalités et des composants qui composent le Kit de développement et décrit les métadonnées et la gestion des connexions et décrit les termes du contrat WCF courantes.</span><span class="sxs-lookup"><span data-stu-id="a52e9-107">[What Is the Windows Communication Foundation Line of Business Adapter SDK](what-is-the-windows-communication-foundation-line-of-business-adapter-sdk.md) provides an overview of the features and components that make up the SDK, and describes the metadata, connection management, and describes the common WCF terms.</span></span>

## <a name="role-of-wcf"></a><span data-ttu-id="a52e9-108">Rôle de WCF</span><span class="sxs-lookup"><span data-stu-id="a52e9-108">Role of WCF</span></span>  
<span data-ttu-id="a52e9-109">[Lisez comment WCF est utilisé par WCF LOB Adapter SDK](read-how-wcf-is-used-by-the-wcf-lob-adapter-sdk.md) explique la relation avec le Kit de développement logiciel et WCF.</span><span class="sxs-lookup"><span data-stu-id="a52e9-109">[Read how WCF is used by the WCF LOB Adapter SDK](read-how-wcf-is-used-by-the-wcf-lob-adapter-sdk.md) explains the relationship with the SDK and WCF.</span></span>

## <a name="architecture-overview"></a><span data-ttu-id="a52e9-110">Vue d'ensemble de l'architecture</span><span class="sxs-lookup"><span data-stu-id="a52e9-110">Architecture Overview</span></span>  
<span data-ttu-id="a52e9-111">[Présentation de l’architecture ](architecture-overview-of-the-wcf-lob-adapter-sdk.md) descrbied l’architecture interne et les principaux composants de WCF LOB Adapter SDK.</span><span class="sxs-lookup"><span data-stu-id="a52e9-111">[Architecture overview ](architecture-overview-of-the-wcf-lob-adapter-sdk.md) descrbied the internal architecture and the main components of WCF LOB Adapter SDK.</span></span>
 
## <a name="connection-handler-metadata-custom-and-core-components"></a><span data-ttu-id="a52e9-112">Connexion, gestionnaire, métadonnées, personnalisée et composants de base</span><span class="sxs-lookup"><span data-stu-id="a52e9-112">Connection, handler, metadata, custom, and core components</span></span>
<span data-ttu-id="a52e9-113">[Les composants clés de WCF LOB Adapter SDK](key-components-of-the-wcf-lob-adapter-sdk.md) décrit ces différents composants.</span><span class="sxs-lookup"><span data-stu-id="a52e9-113">[Key Components of the WCF LOB Adapter SDK](key-components-of-the-wcf-lob-adapter-sdk.md) describes these different components.</span></span>

## <a name="biztalk-server-and-the-sdk"></a><span data-ttu-id="a52e9-114">BizTalk Server et le Kit de développement</span><span class="sxs-lookup"><span data-stu-id="a52e9-114">BizTalk Server and the SDK</span></span>  
[<span data-ttu-id="a52e9-115">Adaptateur BizTalk pour base de données Oracle et le Kit de développement logiciel de l’adaptateur LOB WCF</span><span class="sxs-lookup"><span data-stu-id="a52e9-115">BizTalk Adapter for Oracle Database and the WCF LOB Adapter SDK</span></span>](../adapter-oracle-database/architecture-overview-of-the-biztalk-adapter-for-oracle-database.md)   
  
## <a name="see-also"></a><span data-ttu-id="a52e9-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a52e9-116">See Also</span></span>  
 [<span data-ttu-id="a52e9-117">Prise en main de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="a52e9-117">Getting started with BizTalk Server</span></span>](../../core/getting-started-with-biztalk-server.md)