---
title: Configuration des adaptateurs WCF | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- NetTcpBinding [WCF adapters]
- configuring [WCF adapters]
- WCF adapters, pre-defined bindings
- configuring [WCF adapters], about configuring WCF adapters
- WsHttpBinding [WCF adapters]
- BasicHttpBinding [WCF adapters]
- NetNamedPipeBinding [WCF adapters]
- NetMsmqBinding [WCF adapters]
- bindings, pre-defined [WCF adapters]
- WCF adapters, configuring
ms.assetid: af01e2d4-303d-407a-b853-dd90b0246a8a
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dde69bb5b2014a20509778e27230840e47c0b36d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-the-wcf-adapters"></a><span data-ttu-id="ee576-102">Configuration des adaptateurs WCF</span><span class="sxs-lookup"><span data-stu-id="ee576-102">Configuring the WCF Adapters</span></span>
<span data-ttu-id="ee576-103">Les adaptateurs BizTalk pour Windows Communication Foundation (WCF) permettent à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] de communiquer avec les applications WCF.</span><span class="sxs-lookup"><span data-stu-id="ee576-103">The BizTalk Adapters for Windows Communication Foundation (WCF) allow  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to communicate with WCF-based applications.</span></span> <span data-ttu-id="ee576-104">Les adaptateurs WCF BizTalk incluent cinq adaptateurs physiques qui représentent les liaisons prédéfinies WCF :**BasicHttpBinding**, **WsHttpBinding**, **NetTcpBinding**,  **NetNamedPipeBinding**, et **NetMsmqBinding**.</span><span class="sxs-lookup"><span data-stu-id="ee576-104">The BizTalk WCF adapters include five physical adapters that represent the WCF predefined bindings—**BasicHttpBinding**, **WsHttpBinding**, **NetTcpBinding**, **NetNamedPipeBinding**, and **NetMsmqBinding**.</span></span> <span data-ttu-id="ee576-105">Les adaptateurs WCF pour les liaisons prédéfinies simplifient la définition des informations nécessaires pour la plupart des configurations d'application.</span><span class="sxs-lookup"><span data-stu-id="ee576-105">The WCF adapters for the predefined bindings are provided to enable you to easily configure necessary information for most application requirements.</span></span>  
  
 <span data-ttu-id="ee576-106">Les adaptateurs WCF BizTalk incluent également deux adaptateurs qui vous permettent de configurer librement les informations de liaison et de comportement WCF de l'emplacement de réception et du port d'envoi.</span><span class="sxs-lookup"><span data-stu-id="ee576-106">The BizTalk WCF adapters also include two adapters that enable you to freely configure WCF binding and behavior information for the receive location and send port.</span></span>  
  
 <span data-ttu-id="ee576-107">Tous les adaptateurs WCF possèdent des boîtes de dialogue de propriétés de transport similaires pour les ports d'envoi et les emplacements de réception.</span><span class="sxs-lookup"><span data-stu-id="ee576-107">All the WCF adapters provide similar transport properties dialog boxes for send ports and receive locations.</span></span> <span data-ttu-id="ee576-108">Toutefois, les tâches de configuration des adaptateurs WCF dépendent de l'adaptateur physique.</span><span class="sxs-lookup"><span data-stu-id="ee576-108">However, the detailed tasks to configure the WCF adapters vary depending on the physical adapter.</span></span> <span data-ttu-id="ee576-109">Les tâches qui ne sont pas directement liées aux liaisons de l'adaptateur (telles que l'installation de certificats) sont identiques pour tous les adaptateurs WCF.</span><span class="sxs-lookup"><span data-stu-id="ee576-109">Tasks not directly related to the adapter bindings, such as installing certificates, are the same for all the WCF adapters.</span></span> <span data-ttu-id="ee576-110">Cette section présente les tâches communes à tous les adaptateurs WCF.</span><span class="sxs-lookup"><span data-stu-id="ee576-110">This section discusses the tasks that are common to all the WCF adapters.</span></span> <span data-ttu-id="ee576-111">Pour plus d’informations sur les tâches qui diffèrent pour chaque carte, consultez les rubriques correspondantes de l’adaptateur dans [adaptateurs WCF](../core/wcf-adapters.md).</span><span class="sxs-lookup"><span data-stu-id="ee576-111">For information about tasks that differ for each adapter, see the appropriate topics for the adapter in [WCF Adapters](../core/wcf-adapters.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ee576-112">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="ee576-112">In This Section</span></span>  
  
-   [<span data-ttu-id="ee576-113">Propriétés et schéma de propriété des adaptateurs WCF</span><span class="sxs-lookup"><span data-stu-id="ee576-113">WCF Adapters Property Schema and Properties</span></span>](../core/wcf-adapters-property-schema-and-properties.md)  
  
-   [<span data-ttu-id="ee576-114">Recommandations de sécurité pour les adaptateurs WCF</span><span class="sxs-lookup"><span data-stu-id="ee576-114">WCF Adapters Security Recommendations</span></span>](../core/wcf-adapters-security-recommendations.md)  
  
-   [<span data-ttu-id="ee576-115">Installation des certificats pour les adaptateurs WCF</span><span class="sxs-lookup"><span data-stu-id="ee576-115">Installing Certificates for the WCF Adapters</span></span>](../core/installing-certificates-for-the-wcf-adapters.md)  
  
-   [<span data-ttu-id="ee576-116">En spécifiant le corps du Message pour les adaptateurs WCF</span><span class="sxs-lookup"><span data-stu-id="ee576-116">Specifying the Message Body for the WCF Adapters</span></span>](../core/specifying-the-message-body-for-the-wcf-adapters.md)  
  
-   [<span data-ttu-id="ee576-117">Comment activer les Points d’extensibilité WCF avec les adaptateurs WCF</span><span class="sxs-lookup"><span data-stu-id="ee576-117">How to Enable the WCF Extensibility Points with the WCF Adapters</span></span>](../core/how-to-enable-the-wcf-extensibility-points-with-the-wcf-adapters.md)  
  
-   [<span data-ttu-id="ee576-118">Compteurs de Performance des adaptateurs WCF</span><span class="sxs-lookup"><span data-stu-id="ee576-118">WCF Adapters Performance Counters</span></span>](../core/wcf-adapters-performance-counters.md)  
  
-   [<span data-ttu-id="ee576-119">Seule l’authentification prise en charge pour les adaptateurs WCF</span><span class="sxs-lookup"><span data-stu-id="ee576-119">Single Sign-On Support for the WCF Adapters</span></span>](../core/single-sign-on-support-for-the-wcf-adapters.md)  
  
## <a name="see-also"></a><span data-ttu-id="ee576-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ee576-120">See Also</span></span>  
 [<span data-ttu-id="ee576-121">Adaptateurs WCF</span><span class="sxs-lookup"><span data-stu-id="ee576-121">WCF Adapters</span></span>](../core/wcf-adapters.md)