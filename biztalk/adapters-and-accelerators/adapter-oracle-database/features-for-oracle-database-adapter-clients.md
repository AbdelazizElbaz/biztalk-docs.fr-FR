---
title: "Fonctionnalités pour les clients de carte de base de données Oracle | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data streaming, support for
- binding properties
- adapter, features
- adapters, configuring
- message versioning, support for
- XML data streaming
- performance counters, support for
- dynamic ports in BizTalk, support for
- data streaming
ms.assetid: 63b52573-80a5-4206-95c3-478b86718fee
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b120c948ef3d9821af0a79e91fd718e3a1f33137
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="features-for-oracle-database-adapter-clients"></a><span data-ttu-id="e224f-102">Fonctionnalités pour les clients de carte de base de données Oracle</span><span class="sxs-lookup"><span data-stu-id="e224f-102">Features for Oracle Database adapter clients</span></span>
<span data-ttu-id="e224f-103">Outre les fonctionnalités présentées dans toutes les rubriques de [vue d’ensemble de l’adaptateur BizTalk pour base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/overview-of-biztalk-adapter-for-oracle-database.md), le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] fournit également les fonctionnalités suivantes qui sont utiles pour les clients de la carte :</span><span class="sxs-lookup"><span data-stu-id="e224f-103">In addition to the features discussed throughout the topics of [Overview of BizTalk Adapter for Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/overview-of-biztalk-adapter-for-oracle-database.md), the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] also provides the following features that are useful for adapter clients:</span></span>  
  
-   <span data-ttu-id="e224f-104">**Prise en charge de la configuration des cartes à l’aide des propriétés de liaison**.</span><span class="sxs-lookup"><span data-stu-id="e224f-104">**Support for configuring adapters using binding properties**.</span></span> <span data-ttu-id="e224f-105">Les clients de l’adaptateur peuvent configurer le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] en spécifiant certaines propriétés de liaison.</span><span class="sxs-lookup"><span data-stu-id="e224f-105">Adapter clients can configure the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] by specifying certain binding properties.</span></span> <span data-ttu-id="e224f-106">Par exemple, les clients peuvent configurer l’adaptateur pour utiliser le pool de connexions ODP.NET en définissant le **UseOracleConnectionPool** propriété de liaison.</span><span class="sxs-lookup"><span data-stu-id="e224f-106">For example, clients can configure the adapter to use the ODP.NET connection pool by setting the **UseOracleConnectionPool** binding property.</span></span> <span data-ttu-id="e224f-107">Pour plus d’informations, consultez [configurer les propriétés de liaison pour la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/configure-the-binding-properties-for-oracle-database.md).</span><span class="sxs-lookup"><span data-stu-id="e224f-107">For more information, see [Configure the binding properties for Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/configure-the-binding-properties-for-oracle-database.md).</span></span>  
  
-   <span data-ttu-id="e224f-108">**Prise en charge des valeurs null pour les paramètres de l’opération**.</span><span class="sxs-lookup"><span data-stu-id="e224f-108">**Support for null values for operation parameters**.</span></span> <span data-ttu-id="e224f-109">Les clients de l’adaptateur peuvent fournir des valeurs null pour les paramètres de l’opération à l’aide de l’attribut « nil » dans le code XML d’entrée.</span><span class="sxs-lookup"><span data-stu-id="e224f-109">Adapter clients can provide null values for operation parameters using the “nil” attribute in the input XML.</span></span>  
  
-   <span data-ttu-id="e224f-110">**Prise en charge pour les ports dynamiques dans BizTalk**.</span><span class="sxs-lookup"><span data-stu-id="e224f-110">**Support for dynamic ports in BizTalk**.</span></span> <span data-ttu-id="e224f-111">Via BizTalk [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)], le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] prend en charge un port dynamique qui active le routage dynamique de messages de [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] basée sur les propriétés de contexte de message.</span><span class="sxs-lookup"><span data-stu-id="e224f-111">Through the BizTalk [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)], the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] supports a dynamic port that enables dynamic routing of messages from [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] based on the message context properties.</span></span> <span data-ttu-id="e224f-112">Pour plus d’informations, consultez [configurer des ports dynamiques](../../adapters-and-accelerators/adapter-oracle-database/configure-dynamic-ports-in-the-oracle-database-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="e224f-112">For more information, see [Configure dynamic ports](../../adapters-and-accelerators/adapter-oracle-database/configure-dynamic-ports-in-the-oracle-database-adapter.md).</span></span>  
  
-   <span data-ttu-id="e224f-113">**Prise en charge pour les compteurs de performance**.</span><span class="sxs-lookup"><span data-stu-id="e224f-113">**Support for performance counters**.</span></span> <span data-ttu-id="e224f-114">Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] prend en charge les compteurs de performances basée sur WCF pour une utilisation par les clients de la carte.</span><span class="sxs-lookup"><span data-stu-id="e224f-114">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] supports WCF-based performance counters for use by adapter clients.</span></span> <span data-ttu-id="e224f-115">Pour plus d’informations sur les compteurs de performance, consultez [les compteurs de Performance](../../core/performance-counters.md).</span><span class="sxs-lookup"><span data-stu-id="e224f-115">For more information about performance counters, see [Performance Counters](../../core/performance-counters.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e224f-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e224f-116">See Also</span></span>  
 [<span data-ttu-id="e224f-117">Vue d’ensemble de l’adaptateur BizTalk pour base de données Oracle</span><span class="sxs-lookup"><span data-stu-id="e224f-117">Overview of BizTalk Adapter for Oracle Database</span></span>](../../adapters-and-accelerators/adapter-oracle-database/overview-of-biztalk-adapter-for-oracle-database.md)