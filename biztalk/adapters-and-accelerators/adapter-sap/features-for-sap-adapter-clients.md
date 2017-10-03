---
title: "Fonctionnalités pour les clients de l’adaptateur SAP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dynamic ports
- adapters, features
- XML data streaming
- performance counters
- adapters, support for dynamic ports in BizTalk Server
- adapters, support for message versioning
- adapters, support for XML data streaming
- adapters, support for performance counters
- adapters, support for configuring adapters using binding properties
ms.assetid: 9003c2c1-931d-405e-9a58-660032195af7
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6516ff99f599d02cdf27aa7c0c07752747749021
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="features-for-sap-adapter-clients"></a><span data-ttu-id="d06be-102">Fonctionnalités pour les clients de l’adaptateur SAP</span><span class="sxs-lookup"><span data-stu-id="d06be-102">Features for SAP adapter clients</span></span>
<span data-ttu-id="d06be-103">Outre les fonctionnalités présentées dans toutes les rubriques de [présentation de l’Architecture de l’adaptateur BizTalk pour mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/architecture-overview-of-the-biztalk-adapter-for-mysap-business-suite.md), le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] fournit également les fonctionnalités suivantes qui sont utiles pour les clients de la carte.</span><span class="sxs-lookup"><span data-stu-id="d06be-103">In addition to the features discussed throughout the topics of [Architecture overview of BizTalk Adapter for mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/architecture-overview-of-the-biztalk-adapter-for-mysap-business-suite.md), the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] also provides the following features that are useful for adapter clients.</span></span>  
  
-   <span data-ttu-id="d06be-104">**Prise en charge de la configuration des cartes à l’aide des propriétés de liaison**.</span><span class="sxs-lookup"><span data-stu-id="d06be-104">**Support for configuring adapters using binding properties**.</span></span> <span data-ttu-id="d06be-105">Les clients de l’adaptateur peuvent configurer le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] en spécifiant certaines propriétés de liaison.</span><span class="sxs-lookup"><span data-stu-id="d06be-105">Adapter clients can configure the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] by specifying certain binding properties.</span></span> <span data-ttu-id="d06be-106">Par exemple, les clients peuvent configurer l’adaptateur pour spécifier le nombre maximal de connexions dans le pool de connexions de la carte en spécifiant une valeur pour le **MaxConnectionsPerSystem** propriété de liaison.</span><span class="sxs-lookup"><span data-stu-id="d06be-106">For example, clients can configure the adapter to specify the maximum number of connections in the adapter's connection pool by specifying a value for the **MaxConnectionsPerSystem** binding property.</span></span> <span data-ttu-id="d06be-107">Pour plus d’informations, consultez [en savoir plus sur l’adaptateur BizTalk pour mySAP Business Suite liaison propriétés](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md).</span><span class="sxs-lookup"><span data-stu-id="d06be-107">For more information, see [Read about BizTalk Adapter for mySAP Business Suite Binding Properties](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md).</span></span>  
  
-   <span data-ttu-id="d06be-108">**Prise en charge pour les ports dynamiques dans BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="d06be-108">**Support for dynamic ports in BizTalk Server**.</span></span> <span data-ttu-id="d06be-109">Via BizTalk [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)], le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] prend en charge un port dynamique qui active le routage dynamique de messages de [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] basée sur les propriétés de contexte de message.</span><span class="sxs-lookup"><span data-stu-id="d06be-109">Through the BizTalk [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)], the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] supports a dynamic port that enables dynamic routing of messages from [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] based on the message context properties.</span></span> <span data-ttu-id="d06be-110">Pour plus d’informations, consultez [configurer des ports dynamiques](../../adapters-and-accelerators/adapter-sap/configure-dynamic-ports-in-the-sap-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="d06be-110">For more information, see [Configure dynamic ports](../../adapters-and-accelerators/adapter-sap/configure-dynamic-ports-in-the-sap-adapter.md).</span></span>
  
-   <span data-ttu-id="d06be-111">**Prise en charge pour le versioning de messages**.</span><span class="sxs-lookup"><span data-stu-id="d06be-111">**Support for message versioning**.</span></span> <span data-ttu-id="d06be-112">Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] prend en charge message contrôle de version pour prendre en charge pour les schémas de message différent dans les versions futures de la [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d06be-112">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] supports message versioning to enable support for different message schemas in future releases of the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span></span> <span data-ttu-id="d06be-113">Pour plus d’informations, consultez [prise en charge du Versioning de Message](../../adapters-and-accelerators/adapter-sap/message-versioning-support1.md).</span><span class="sxs-lookup"><span data-stu-id="d06be-113">For more information, see [Message Versioning Support](../../adapters-and-accelerators/adapter-sap/message-versioning-support1.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d06be-114">Cette fonctionnalité ne fournit pas de compatibilité descendante avec les versions précédentes de la carte.</span><span class="sxs-lookup"><span data-stu-id="d06be-114">This feature does not provide backward compatibility with the earlier versions of the adapter.</span></span>  
  
-   <span data-ttu-id="d06be-115">**Prise en charge pour les compteurs de performance**.</span><span class="sxs-lookup"><span data-stu-id="d06be-115">**Support for performance counters**.</span></span> <span data-ttu-id="d06be-116">Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] prend en charge les compteurs de performances basée sur WCF pour une utilisation par les clients de la carte.</span><span class="sxs-lookup"><span data-stu-id="d06be-116">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] supports WCF-based performance counters for use by adapter clients.</span></span> <span data-ttu-id="d06be-117">Pour plus d’informations sur les compteurs de performance, consultez [utiliser des compteurs de performances avec l’adaptateur SAP](../../adapters-and-accelerators/adapter-sap/use-performance-counters-with-the-sap-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="d06be-117">For more information about performance counters, see [Use Performance Counters with the SAP adapter](../../adapters-and-accelerators/adapter-sap/use-performance-counters-with-the-sap-adapter.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d06be-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d06be-118">See Also</span></span>  
 [<span data-ttu-id="d06be-119">Présentation de l’architecture de l’adaptateur BizTalk pour mySAP Business Suite</span><span class="sxs-lookup"><span data-stu-id="d06be-119">Architecture overview of BizTalk Adapter for mySAP Business Suite</span></span>](../../adapters-and-accelerators/adapter-sap/architecture-overview-of-the-biztalk-adapter-for-mysap-business-suite.md)