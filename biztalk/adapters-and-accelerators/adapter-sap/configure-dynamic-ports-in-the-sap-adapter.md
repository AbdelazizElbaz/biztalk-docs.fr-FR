---
title: "Configurer des ports dynamiques dans l’adaptateur SAP | Documents Microsoft"
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
ms.assetid: 4d6569f9-e513-47f3-b2c1-4c21bafb2bf2
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ea1a63bf66cd798656f1303513b5200a49243138
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configure-dynamic-ports-in-the-sap-adapter"></a><span data-ttu-id="cd530-102">Configurer des ports dynamiques dans l’adaptateur SAP</span><span class="sxs-lookup"><span data-stu-id="cd530-102">Configure dynamic ports in the SAP adapter</span></span>
## <a name="use-message-context-properties"></a><span data-ttu-id="cd530-103">Utilisez les propriétés de contexte de message</span><span class="sxs-lookup"><span data-stu-id="cd530-103">Use message context properties</span></span>
<span data-ttu-id="cd530-104">Dans [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], vous pouvez configurer des ports dynamiques pour un [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cd530-104">In [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], you can configure dynamic ports for a [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)].</span></span> <span data-ttu-id="cd530-105">Étant donné que [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] est un adaptateur WCF, vous pouvez configurer dynamiquement un port pour le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] à l’aide des propriétés de contexte de message.</span><span class="sxs-lookup"><span data-stu-id="cd530-105">Because [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] is a WCF-based adapter, you can dynamically configure a port for the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] by using message context properties.</span></span>  
  
 <span data-ttu-id="cd530-106">Pour le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], l’URI, une action et une liaison peuvent être déterminées à partir d’une propriété d’un message entrant et ensuite spécifiés dans la forme Expression, comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="cd530-106">For the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], the URI, action, and binding might be determined from a property on an incoming message, and then specified in the Expression shape, as shown in the following example:</span></span>  
  
```  
Request2=Request1;  
Request2(WCF.Action)="http://Microsoft.LobServices.Sap/2007/03/Rfc/RFC_CUSTOMER_GET";  
Request2(WCF.BindingType)="sapBinding";  
Request2(WCF.UserName)="YourUserName";  
Request2(WCF.Password)="YourPassword";  
SendPort(Microsoft.XLANGs.BaseTypes.Address)="sap://CLIENT=800;LANG=EN;@A/YourSAPHost/00";  
SendPort(Microsoft.XLANGs.BaseTypes.TransportType)="WCF-Custom";  
  
```  
  
> [!NOTE]
>  <span data-ttu-id="cd530-107">Si vous utilisez un adaptateur WCF-SAP dans [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration, vous pouvez également spécifier le type de transport en tant que `SendPort(Microsoft.XLANGs.BaseTypes.TransportType)="SAPAdapter"`, où **SAPAdapter** est celui avec lequel vous avez ajouté l’adaptateur WCF-SAP dans [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Console d’administration.</span><span class="sxs-lookup"><span data-stu-id="cd530-107">If you are using a WCF-SAP adapter in [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console, you can also specify the transport type as `SendPort(Microsoft.XLANGs.BaseTypes.TransportType)="SAPAdapter"`, where **SAPAdapter** is the name with which you added the WCF-SAP adapter in [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
 <span data-ttu-id="cd530-108">Dans l’exemple précédent :</span><span class="sxs-lookup"><span data-stu-id="cd530-108">In the preceding example:</span></span>  
  
-   <span data-ttu-id="cd530-109">MAX2 message est créé à partir du message de Request1.</span><span class="sxs-lookup"><span data-stu-id="cd530-109">Request2 message is being created from Request1 message.</span></span> <span data-ttu-id="cd530-110">Les messages de la mappent à un schéma de l’opération, qui est généré à l’aide de la [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cd530-110">Both the messages map to an operation schema, which is generated using the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)].</span></span>  
  
-   <span data-ttu-id="cd530-111">Le port d’envoi est le nom du port d’envoi logique dans l’orchestration BizTalk.</span><span class="sxs-lookup"><span data-stu-id="cd530-111">SendPort is the name of the logical send port in the BizTalk orchestration.</span></span>  
  
 <span data-ttu-id="cd530-112">La forme Expression fait partie de l’orchestration BizTalk.</span><span class="sxs-lookup"><span data-stu-id="cd530-112">The Expression shape is part of the BizTalk orchestration.</span></span> <span data-ttu-id="cd530-113">Lorsque vous déployez l’orchestration, le port d’envoi WCF-Custom est également créé.</span><span class="sxs-lookup"><span data-stu-id="cd530-113">When you deploy the orchestration, the WCF-Custom send port is also created.</span></span>  
  
 <span data-ttu-id="cd530-114">Pour plus d’informations sur la configuration des ports dynamiques, consultez [configuration dynamique envoyer des Ports à l’aide de cartes propriétés de contexte WCF](../../core/configuring-dynamic-send-ports-using-wcf-adapters-context-properties.md).</span><span class="sxs-lookup"><span data-stu-id="cd530-114">For more information on configuring dynamic ports, see [Configuring Dynamic Send Ports Using WCF Adapters Context Properties](../../core/configuring-dynamic-send-ports-using-wcf-adapters-context-properties.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="cd530-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cd530-115">See Also</span></span>  
[<span data-ttu-id="cd530-116">Blocs de construction pour créer des applications SAP</span><span class="sxs-lookup"><span data-stu-id="cd530-116">Building blocks to create SAP applications</span></span>](../../adapters-and-accelerators/adapter-sap/building-blocks-to-create-sap-applications.md)