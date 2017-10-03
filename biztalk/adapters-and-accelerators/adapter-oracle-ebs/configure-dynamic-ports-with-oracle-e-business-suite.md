---
title: Configurer des ports dynamiques avec Oracle E-Business Suite | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 75a150ea-d957-4a37-81cf-c043a0a7d5cb
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b02dc0cd4a4cf1d031acaf6d5a0e1c905ee225b8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configure-dynamic-ports-with-oracle-e-business-suite"></a><span data-ttu-id="5fcea-102">Configurer des ports dynamiques avec Oracle E-Business Suite</span><span class="sxs-lookup"><span data-stu-id="5fcea-102">Configure dynamic ports with Oracle E-Business Suite</span></span>
<span data-ttu-id="5fcea-103">Dans [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], vous pouvez configurer des ports dynamiques pour un [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5fcea-103">In [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], you can configure dynamic ports for a [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)].</span></span> <span data-ttu-id="5fcea-104">Étant donné que la [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] est un adaptateur WCF, vous pouvez configurer dynamiquement un port pour le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] à l’aide des propriétés de contexte de message.</span><span class="sxs-lookup"><span data-stu-id="5fcea-104">Because the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] is a WCF-based adapter, you can dynamically configure a port for the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] by using message context properties.</span></span>  
  
 <span data-ttu-id="5fcea-105">Pour le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], l’URI, une action et une liaison peuvent être déterminées à partir d’une propriété d’un message entrant et ensuite spécifiés dans le **Expression** mettre en forme, comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="5fcea-105">For the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], the URI, action, and binding may be determined from a property on an incoming message, and then specified in the **Expression** shape, as shown in the following example:</span></span>  
  
```  
Request2=Request1;  
Request2(WCF.Action)="InterfaceTables/Insert/OFA/FA/FA_BOOKS";  
Request2(WCF.BindingType)="oracleEBSBinding";  
Request2(WCF.UserName)="myuser";  
Request2(WCF.Password)="mypass";  
SendPort(Microsoft.XLANGs.BaseTypes.Address)="oracleebs://ebs_instance";  
SendPort(Microsoft.XLANGs.BaseTypes.TransportType)="WCF-Custom";  
```  
  
> [!NOTE]
>  <span data-ttu-id="5fcea-106">Si vous utilisez un adaptateur WCF-OracleEBS dans [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration, vous pouvez également spécifier le type de transport en tant que `SendPort(Microsoft.XLANGs.BaseTypes.TransportType)="OracleEBSAdapter"`, où **OracleEBSAdapter** est celui avec lequel vous avez ajouté l’adaptateur WCF-OracleEBS dans [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Console d’administration.</span><span class="sxs-lookup"><span data-stu-id="5fcea-106">If you are using a WCF-OracleEBS adapter in [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console, you can also specify the transport type as `SendPort(Microsoft.XLANGs.BaseTypes.TransportType)="OracleEBSAdapter"`, where **OracleEBSAdapter** is the name with which you added the WCF-OracleEBS adapter in [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
 <span data-ttu-id="5fcea-107">Dans l’exemple précédent,</span><span class="sxs-lookup"><span data-stu-id="5fcea-107">In the preceding example,</span></span>  
  
-   <span data-ttu-id="5fcea-108">MAX2 message est créé à partir du message de Request1.</span><span class="sxs-lookup"><span data-stu-id="5fcea-108">Request2 message is being created from Request1 message.</span></span> <span data-ttu-id="5fcea-109">Les deux messages mappent à un schéma de l’opération, qui est généré à l’aide de la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5fcea-109">Both messages map to an operation schema, which is generated using the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)].</span></span>  
  
-   <span data-ttu-id="5fcea-110">Le port d’envoi est le nom du port d’envoi logique dans l’orchestration BizTalk.</span><span class="sxs-lookup"><span data-stu-id="5fcea-110">SendPort is the name of the logical send port in the BizTalk orchestration.</span></span>  
  
 <span data-ttu-id="5fcea-111">Le **Expression** forme fait partie de l’orchestration BizTalk.</span><span class="sxs-lookup"><span data-stu-id="5fcea-111">The **Expression** shape is part of the BizTalk orchestration.</span></span> <span data-ttu-id="5fcea-112">Déploiement de l’orchestration crée également un port d’envoi WCF-Custom.</span><span class="sxs-lookup"><span data-stu-id="5fcea-112">Deploying the orchestration also creates a WCF-Custom send port.</span></span>  
  
 <span data-ttu-id="5fcea-113">Pour plus d’informations sur la configuration des ports dynamiques, consultez [configuration dynamique envoyer des Ports à l’aide de cartes propriétés de contexte WCF](../../core/configuring-dynamic-send-ports-using-wcf-adapters-context-properties.md).</span><span class="sxs-lookup"><span data-stu-id="5fcea-113">For more information about configuring dynamic ports, see [Configuring Dynamic Send Ports Using WCF Adapters Context Properties](../../core/configuring-dynamic-send-ports-using-wcf-adapters-context-properties.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="5fcea-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5fcea-114">See Also</span></span>  
[<span data-ttu-id="5fcea-115">Blocs de construction pour créer des applications d’Oracle E-Business Suite</span><span class="sxs-lookup"><span data-stu-id="5fcea-115">Building blocks to create Oracle E-Business Suite applications</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/building-blocks-to-create-oracle-e-business-suite-applications.md)