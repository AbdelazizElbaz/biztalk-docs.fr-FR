---
title: "Créer une connexion à SQL Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 44a03b2c-55b5-49a0-92cc-6f017720d34a
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c3b87b4141c9e14c680d8100a7c505dda0a0093c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="create-a-connection-to-sql-server"></a><span data-ttu-id="2db04-102">Créer une connexion à SQL Server</span><span class="sxs-lookup"><span data-stu-id="2db04-102">Create a connection to SQL Server</span></span>
<span data-ttu-id="2db04-103">Le [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] est un [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="2db04-103">The [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] is a [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] custom binding.</span></span> <span data-ttu-id="2db04-104">Par conséquent, il permet la communication à une base de données SQL Server via une adresse de point de terminaison WCF.</span><span class="sxs-lookup"><span data-stu-id="2db04-104">As such, it enables communication to a SQL Server database through a WCF endpoint address.</span></span> <span data-ttu-id="2db04-105">Dans WCF, l’adresse de point de terminaison identifie l’emplacement réseau d’un service et est généralement exprimée comme une ressource identificateur URI (Uniform).</span><span class="sxs-lookup"><span data-stu-id="2db04-105">In WCF, the endpoint address identifies the network location of a service and is typically expressed as a Uniform Resource Identifier (URI).</span></span> <span data-ttu-id="2db04-106">Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] exprime cet emplacement en tant qu’URI qui contient des propriétés de connexion qui le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] utilise pour établir une connexion à la base de données SQL Server.</span><span class="sxs-lookup"><span data-stu-id="2db04-106">The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] expresses this location as a connection URI, which contains properties that the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] uses to establish a connection to the SQL Server database.</span></span> <span data-ttu-id="2db04-107">Vous devez spécifier un URI de connexion lorsque vous :</span><span class="sxs-lookup"><span data-stu-id="2db04-107">You must specify a connection URI when you:</span></span>  
  
-   <span data-ttu-id="2db04-108">Créer une fabrique de canaux ou d’un écouteur de canal à l’aide du modèle de canal WCF ou lorsque vous créez un hôte de service ou client WCF à l’aide du modèle de service WCF.</span><span class="sxs-lookup"><span data-stu-id="2db04-108">Create a channel factory or a channel listener using the WCF channel model or when you create a WCF client or service host using the WCF service model.</span></span>  
  
-   <span data-ttu-id="2db04-109">Créer une liaison de port physique dans un [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] solution.</span><span class="sxs-lookup"><span data-stu-id="2db04-109">Create a physical port binding in a [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] solution.</span></span>  
  
-   <span data-ttu-id="2db04-110">Utilisez le [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] pour générer une classe de client WCF ou l’interface de service WCF pour une solution de modèle de service WCF.</span><span class="sxs-lookup"><span data-stu-id="2db04-110">Use the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] to generate a WCF client class or WCF service interface for a WCF service model solution.</span></span>  
  
-   <span data-ttu-id="2db04-111">Utilisez le [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] pour extraire les schémas de message à partir de la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] pour une solution BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="2db04-111">Use the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] to retrieve message schemas from the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] for a BizTalk Server solution.</span></span>  
  
-   <span data-ttu-id="2db04-112">Utilisez l’outil Service Model Metadata Utility (svcutil.exe) pour générer une classe de client WCF ou l’interface de service WCF pour une solution de modèle de service WCF.</span><span class="sxs-lookup"><span data-stu-id="2db04-112">Use the ServiceModel Metadata Utility tool (svcutil.exe) to generate a WCF client class or WCF service interface for a WCF service model solution.</span></span>  
  
 <span data-ttu-id="2db04-113">Les rubriques de cette section décrivent comment établir une connexion entre le [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] et la base de données SQL Server en vous fournissant :</span><span class="sxs-lookup"><span data-stu-id="2db04-113">The topics in this section describe how to establish a connection between the [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] and the SQL Server database by providing you with:</span></span>  
  
-   <span data-ttu-id="2db04-114">Informations sur les propriétés de connexion et la structure de l’URI de connexion SQL Server.</span><span class="sxs-lookup"><span data-stu-id="2db04-114">Information about the connection properties and the structure of the SQL Server connection URI.</span></span>  
  
-   <span data-ttu-id="2db04-115">Liens vers des rubriques qui montrent comment spécifier un URI de connexion à l’aide de la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2db04-115">Links to topics that show how to specify a connection URI by using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span>  
  
-   <span data-ttu-id="2db04-116">Informations sur la connexion à SQL Server à l’aide de l’authentification Windows.</span><span class="sxs-lookup"><span data-stu-id="2db04-116">Information about connecting to SQL Server using Windows Authentication.</span></span>  
  
  
  
## <a name="see-also"></a><span data-ttu-id="2db04-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2db04-117">See Also</span></span>  
[<span data-ttu-id="2db04-118">Développer vos applications SQL</span><span class="sxs-lookup"><span data-stu-id="2db04-118">Develop your SQL applications</span></span>](../../adapters-and-accelerators/adapter-sql/develop-your-sql-applications.md)