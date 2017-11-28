---
title: "Développer des applications BizTalk à l’aide de l’adaptateur SAP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BizTalk applications, developing
- developing, BizTalk applications
ms.assetid: 4aa10897-a08e-4fc3-9c1f-40485d204273
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 75e70a52f12227b1bde3a43f9330c6fe373ac5a3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="develop-biztalk-applications-using-the-sap-adapter"></a><span data-ttu-id="9be8a-102">Développer des applications BizTalk à l’aide de l’adaptateur SAP</span><span class="sxs-lookup"><span data-stu-id="9be8a-102">Develop BizTalk applications using the SAP adapter</span></span>
<span data-ttu-id="9be8a-103">Développement d’applications BizTalk implique la création d’un projet BizTalk dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] et à l’aide de la [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] ou [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] pour générer le schéma XML.</span><span class="sxs-lookup"><span data-stu-id="9be8a-103">Developing BizTalk applications involves creating a BizTalk project in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] and using the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] or [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] to generate XML schema.</span></span> <span data-ttu-id="9be8a-104">Une fois que vous avez généré le schéma, vous pouvez utiliser le routage basé sur le contenu (CBR) ou créer des orchestrations BizTalk pour envoyer et recevoir des messages conformes au schéma généré.</span><span class="sxs-lookup"><span data-stu-id="9be8a-104">Once you have generated the schema, you can either use Content-Based Routing (CBR) or create BizTalk orchestrations to send and receive messages that conform to the generated schema.</span></span>  
  
 <span data-ttu-id="9be8a-105">CBR peut être utilisé dans les scénarios où les messages envoyés au système SAP nécessitent un traitement intensif.</span><span class="sxs-lookup"><span data-stu-id="9be8a-105">CBR can be used in scenarios where the messages being sent to the SAP system do not require any intensive processing.</span></span> <span data-ttu-id="9be8a-106">Par exemple, si vous savez que le port de réception recevra les messages uniquement d’un certain type, vous pouvez ajouter un filtre au port d’envoi pour acheminer les messages correspondant à l’expression de filtre pour le port d’envoi.</span><span class="sxs-lookup"><span data-stu-id="9be8a-106">For example, if you know that the receive port will be receiving messages only of a certain type, you can add a filter to the send port to route the messages matching the filter expression to the send port.</span></span>  
  
 <span data-ttu-id="9be8a-107">Dans les orchestrations BizTalk, vous créez envoi et ports de réception pour envoyer et recevoir des messages vers et depuis le [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)], qui à son tour envoie des messages à [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9be8a-107">In BizTalk orchestrations, you create send and receive ports to send and receive messages to and from the [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)], which in turn sends the messages to [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="9be8a-108">Cette section fournit des informations sur l’utilisation des orchestrations BizTalk pour effectuer des opérations sur le système SAP en utilisant le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9be8a-108">This section provides information about using BizTalk orchestrations to perform operations on the SAP system using the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span> <span data-ttu-id="9be8a-109">Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] à son tour utilise le [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)] adaptateur qui peut interagir avec une liaison WCF.</span><span class="sxs-lookup"><span data-stu-id="9be8a-109">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] in turn uses the [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)] adapter that can interact with a WCF binding.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9be8a-110">Pour utiliser le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] avec Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], vous devez toujours définir la **EnableBizTalkCompatibilityMode** liaison de propriété **True**.</span><span class="sxs-lookup"><span data-stu-id="9be8a-110">To use the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] with Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], you must always set the **EnableBizTalkCompatibilityMode** binding property to **True**.</span></span> <span data-ttu-id="9be8a-111">Pour plus d’informations sur la définition des propriétés de liaison, consultez [configurer les propriétés de liaison de l’adaptateur SAP](../../adapters-and-accelerators/adapter-sap/configure-the-binding-properties-for-the-sap-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="9be8a-111">For information about how to set binding properties, see [Configure the binding properties for the SAP adapter](../../adapters-and-accelerators/adapter-sap/configure-the-binding-properties-for-the-sap-adapter.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9be8a-112">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="9be8a-112">In This Section</span></span>  
  
-   [<span data-ttu-id="9be8a-113">Conditions préalables pour créer des applications SAP</span><span class="sxs-lookup"><span data-stu-id="9be8a-113">Prerequisites to create SAP applications</span></span>](../../adapters-and-accelerators/adapter-sap/prerequisites-to-create-sap-applications.md)
  
-   [<span data-ttu-id="9be8a-114">Blocs de construction pour créer des applications SAP</span><span class="sxs-lookup"><span data-stu-id="9be8a-114">Building blocks to create SAP applications</span></span>](../../adapters-and-accelerators/adapter-sap/building-blocks-to-create-sap-applications.md)
  
-   [<span data-ttu-id="9be8a-115">Appeler les RFC dans SAP à l’aide de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="9be8a-115">Invoke RFCs in SAP using BizTalk Server</span></span>](../../adapters-and-accelerators/adapter-sap/invoke-rfcs-in-sap-using-biztalk-server.md)  
  
-   [<span data-ttu-id="9be8a-116">Recevoir des appels de RFC entrants à partir de SAP à l’aide de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="9be8a-116">Receive Inbound RFC Calls from SAP using BizTalk Server</span></span>](../../adapters-and-accelerators/adapter-sap/receive-inbound-rfc-calls-from-sap-using-biztalk-server.md)  
  
-   [<span data-ttu-id="9be8a-117">Appeler tRFCs dans SAP à l’aide de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="9be8a-117">Invoke tRFCs in SAP using BizTalk Server</span></span>](../../adapters-and-accelerators/adapter-sap/invoke-trfcs-in-sap-using-biztalk-server.md)  
  
-   [<span data-ttu-id="9be8a-118">Réception entrant tRFC appelle à partir de SAP à l’aide de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="9be8a-118">Receive Inbound tRFC Calls from SAP using BizTalk Server</span></span>](../../adapters-and-accelerators/adapter-sap/receive-inbound-trfc-calls-from-sap-using-biztalk-server.md)  
  
-   [<span data-ttu-id="9be8a-119">Exécutez BAPI Transactions dans SAP à l’aide de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="9be8a-119">Run BAPI Transactions in SAP using BizTalk Server</span></span>](../../adapters-and-accelerators/adapter-sap/run-bapi-transactions-in-sap-using-biztalk-server.md)  
  
-   [<span data-ttu-id="9be8a-120">Envoyer des IDOC à SAP à l’aide de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="9be8a-120">Send IDOCs to SAP using BizTalk Server</span></span>](../../adapters-and-accelerators/adapter-sap/send-idocs-to-sap-using-biztalk-server.md)  
  
-   [<span data-ttu-id="9be8a-121">Recevoir des IDOC SAP à l’aide de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="9be8a-121">Receive IDOCs from SAP using BizTalk Server</span></span>](../../adapters-and-accelerators/adapter-sap/receive-idocs-from-sap-using-biztalk-server.md)  
  
-   [<span data-ttu-id="9be8a-122">Recevoir des IDOC de SAP dans un contexte transactionnel à l’aide de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="9be8a-122">Receive IDOCs from SAP in a Transactional Context using BizTalk Server</span></span>](../../adapters-and-accelerators/adapter-sap/receive-idocs-from-sap-in-a-transactional-context-using-biztalk-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="9be8a-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9be8a-123">See Also</span></span>  
[<span data-ttu-id="9be8a-124">Développer vos applications SAP</span><span class="sxs-lookup"><span data-stu-id="9be8a-124">Develop your SAP applications</span></span>](../../adapters-and-accelerators/adapter-sap/develop-your-sap-applications.md)