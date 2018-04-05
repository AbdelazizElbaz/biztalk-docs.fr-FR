---
title: Configurer des ports dynamiques dans l’adaptateur de base de données Oracle | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- dynamic ports, configuring
ms.assetid: c4f67707-76a0-4d72-913f-03219b412e2a
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6c58243ba2c953000cbccd7dc9d6c1da34889058
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configure-dynamic-ports-in-the-oracle-database-adapter"></a><span data-ttu-id="119df-102">Configurer des ports dynamiques dans l’adaptateur de base de données Oracle</span><span class="sxs-lookup"><span data-stu-id="119df-102">Configure dynamic ports in the Oracle Database Adapter</span></span>
<span data-ttu-id="119df-103">Dans [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], vous pouvez configurer des ports dynamiques pour un [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="119df-103">In [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], you can configure dynamic ports for a [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)].</span></span> <span data-ttu-id="119df-104">Étant donné que la [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] est un adaptateur WCF, vous pouvez configurer dynamiquement un port pour le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] à l’aide des propriétés de contexte de message.</span><span class="sxs-lookup"><span data-stu-id="119df-104">Because the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] is a WCF-based adapter, you can dynamically configure a port for the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] by using message context properties.</span></span>  
  
 <span data-ttu-id="119df-105">Pour le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], l’URI, une action et une liaison peuvent être déterminées à partir d’une propriété d’un message entrant et ensuite spécifiés dans le **Expression** mettre en forme, comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="119df-105">For the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], the URI, action, and binding may be determined from a property on an incoming message, and then specified in the **Expression** shape, as shown in the following example:</span></span>  
  
```  
Request2=Request1;  
Request2(WCF.Action)="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/ACCOUNTACTIVITY/Select";  
Request2(WCF.BindingType)="oracleDBBinding";  
Request2(WCF.UserName)="SCOTT";  
Request2(WCF.Password)="TIGER";  
SendPort(Microsoft.XLANGs.BaseTypes.Address)="oracledb://adapdoc/";  
SendPort(Microsoft.XLANGs.BaseTypes.TransportType)="WCF-Custom";  
  
```  
  
> [!NOTE]
>  <span data-ttu-id="119df-106">Si vous utilisez un adaptateur WCF-OracleDB dans [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration, vous pouvez également spécifier le type de transport en tant que `SendPort(Microsoft.XLANGs.BaseTypes.TransportType)="OracleDatabaseAdapter"`, où **OracleDatabaseAdapter** est celui avec lequel vous avez ajouté l’adaptateur WCF-OracleDB dans [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Console d’administration.</span><span class="sxs-lookup"><span data-stu-id="119df-106">If you are using a WCF-OracleDB adapter in [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console, you can also specify the transport type as `SendPort(Microsoft.XLANGs.BaseTypes.TransportType)="OracleDatabaseAdapter"`, where **OracleDatabaseAdapter** is the name with which you added the WCF-OracleDB adapter in [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
 <span data-ttu-id="119df-107">Dans l’exemple ci-dessus,</span><span class="sxs-lookup"><span data-stu-id="119df-107">In the above example,</span></span>  
  
-   <span data-ttu-id="119df-108">MAX2 message est créé à partir du message de Request1.</span><span class="sxs-lookup"><span data-stu-id="119df-108">Request2 message is being created from Request1 message.</span></span> <span data-ttu-id="119df-109">Les messages de la mappent à un schéma de l’opération, qui est généré à l’aide de la [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="119df-109">Both the messages map to an operation schema, which is generated using the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)].</span></span>  
  
-   <span data-ttu-id="119df-110">Le port d’envoi est le nom du port d’envoi logique dans l’orchestration BizTalk.</span><span class="sxs-lookup"><span data-stu-id="119df-110">SendPort is the name of the logical send port in the BizTalk orchestration.</span></span>  
  
 <span data-ttu-id="119df-111">Le **Expression** forme fait partie de l’orchestration BizTalk.</span><span class="sxs-lookup"><span data-stu-id="119df-111">The **Expression** shape is part of the BizTalk orchestration.</span></span> <span data-ttu-id="119df-112">Lorsque vous déployez l’orchestration, le port d’envoi WCF-custom est également créé.</span><span class="sxs-lookup"><span data-stu-id="119df-112">When you deploy the orchestration, the WCF-custom send port is also created.</span></span>  
  
 <span data-ttu-id="119df-113">Pour plus d’informations sur la configuration des ports dynamiques, consultez [configuration dynamique envoyer des Ports à l’aide de cartes propriétés de contexte WCF](../../core/configuring-dynamic-send-ports-using-wcf-adapters-context-properties.md).</span><span class="sxs-lookup"><span data-stu-id="119df-113">For more information on configuring dynamic ports, see [Configuring Dynamic Send Ports Using WCF Adapters Context Properties](../../core/configuring-dynamic-send-ports-using-wcf-adapters-context-properties.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="119df-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="119df-114">See Also</span></span>  
[<span data-ttu-id="119df-115">Blocs de construction pour développer des Applications BizTalk avec la base de données Oracle</span><span class="sxs-lookup"><span data-stu-id="119df-115">Building Blocks to develop BizTalk Applications with Oracle Database</span></span>](../../adapters-and-accelerators/adapter-oracle-database/building-blocks-to-develop-biztalk-applications-with-oracle-database.md)