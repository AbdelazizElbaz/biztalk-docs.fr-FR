---
title: "Configurer des ports dynamiques avec l’adaptateur Siebel | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dynamic ports, configuring
- configuring, dynamic ports
ms.assetid: a3516c2c-d40e-426b-bf3f-f9dc3de105ef
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b036bf772e3e9580c84616f74786d4908aca7515
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configure-dynamic-ports-with-the-siebel-adapter"></a><span data-ttu-id="3071c-102">Configurer des ports dynamiques avec l’adaptateur Siebel</span><span class="sxs-lookup"><span data-stu-id="3071c-102">Configure dynamic ports with the Siebel adapter</span></span>
<span data-ttu-id="3071c-103">Dans [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], vous pouvez configurer des ports dynamiques pour un [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3071c-103">In [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], you can configure dynamic ports for a [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)].</span></span> <span data-ttu-id="3071c-104">Étant donné que [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] est un adaptateur WCF, vous pouvez configurer dynamiquement un port pour le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] à l’aide des propriétés de contexte de message.</span><span class="sxs-lookup"><span data-stu-id="3071c-104">Because [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] is a WCF-based adapter, you can dynamically configure a port for the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] by using message context properties.</span></span>  
  
 <span data-ttu-id="3071c-105">Pour le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)], l’URI, une action et une liaison peuvent être déterminées à partir d’une propriété d’un message entrant et ensuite spécifiés dans le **Expression** mettre en forme, comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="3071c-105">For the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)], the URI, action, and binding might be determined from a property on an incoming message, and then specified in the **Expression** shape, as shown in the following example:</span></span>  
  
```  
Request2=Request1;  
Request2(WCF.Action)="http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Insert";  
Request2(WCF.BindingType)="siebelBinding";  
Request2(WCF.UserName)="YourUserName";  
Request2(WCF.Password)="YourPassword";  
SendPort(Microsoft.XLANGs.BaseTypes.Address)="siebel://mySiebelServer:1234?SiebelObjectManager=SSEObjMgr&SiebelEnterpriseServer=myEnterpriseServer&Language=enu";  
SendPort(Microsoft.XLANGs.BaseTypes.TransportType)="WCF-Custom";  
  
```  
  
> [!NOTE]
>  <span data-ttu-id="3071c-106">Si vous utilisez un adaptateur WCF-Siebel dans [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration, vous pouvez également spécifier le type de transport en tant que `SendPort(Microsoft.XLANGs.BaseTypes.TransportType)="SiebelAdapter"`, où **SiebelAdapter** est celui avec lequel vous avez ajouté l’adaptateur WCF-Siebel dans [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]Console d’administration.</span><span class="sxs-lookup"><span data-stu-id="3071c-106">If you are using a WCF-Siebel adapter in [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console, you can also specify the transport type as `SendPort(Microsoft.XLANGs.BaseTypes.TransportType)="SiebelAdapter"`, where **SiebelAdapter** is the name with which you added the WCF-Siebel adapter in [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
 <span data-ttu-id="3071c-107">Dans l’exemple précédent :</span><span class="sxs-lookup"><span data-stu-id="3071c-107">In the preceding example:</span></span>  
  
-   <span data-ttu-id="3071c-108">MAX2 message est créé à partir du message de Request1.</span><span class="sxs-lookup"><span data-stu-id="3071c-108">Request2 message is being created from Request1 message.</span></span> <span data-ttu-id="3071c-109">Les messages de la mappent à un schéma de l’opération, qui est généré à l’aide de la [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3071c-109">Both the messages map to an operation schema, which is generated using the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)].</span></span>  
  
-   <span data-ttu-id="3071c-110">Le port d’envoi est le nom du port d’envoi logique dans l’orchestration BizTalk.</span><span class="sxs-lookup"><span data-stu-id="3071c-110">SendPort is the name of the logical send port in the BizTalk orchestration.</span></span>  
  
 <span data-ttu-id="3071c-111">La forme Expression fait partie de l’orchestration BizTalk.</span><span class="sxs-lookup"><span data-stu-id="3071c-111">The Expression shape is part of the BizTalk orchestration.</span></span> <span data-ttu-id="3071c-112">Lorsque vous déployez l’orchestration, le port d’envoi WCF-Custom est également créé.</span><span class="sxs-lookup"><span data-stu-id="3071c-112">When you deploy the orchestration, the WCF-Custom send port is also created.</span></span>  
  
 <span data-ttu-id="3071c-113">Pour plus d’informations sur la configuration des ports dynamiques, consultez [configuration dynamique envoyer des Ports à l’aide de cartes propriétés de contexte WCF](../../core/configuring-dynamic-send-ports-using-wcf-adapters-context-properties.md).</span><span class="sxs-lookup"><span data-stu-id="3071c-113">For more information on configuring dynamic ports, see [Configuring Dynamic Send Ports Using WCF Adapters Context Properties](../../core/configuring-dynamic-send-ports-using-wcf-adapters-context-properties.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="3071c-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3071c-114">See Also</span></span>  
[<span data-ttu-id="3071c-115">Blocs de construction pour créer des applications BizTalk avec l’adaptateur Siebel</span><span class="sxs-lookup"><span data-stu-id="3071c-115">Building blocks to create BizTalk applications with the Siebel adapter</span></span>](../../adapters-and-accelerators/adapter-siebel/building-blocks-to-create-biztalk-applications-with-the-siebel-adapter.md)