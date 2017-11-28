---
title: "Configuration des Ports d’envoi dynamiques à l’aide des propriétés de contexte des adaptateurs WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF services, send ports
- send ports, WCF services
- dynamic send ports, WCF services
- send ports, dynamic
ms.assetid: 2a7e2cd2-fa2d-45da-bb8e-eb8bab21bfa3
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2bca34afa85c8764215f47d1272c115354889fa5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-dynamic-send-ports-using-wcf-adapters-context-properties"></a><span data-ttu-id="2a681-102">Configuration des ports d'envoi dynamiques à l'aide des propriétés de contexte des adaptateurs WCF</span><span class="sxs-lookup"><span data-stu-id="2a681-102">Configuring Dynamic Send Ports Using WCF Adapters Context Properties</span></span>
<span data-ttu-id="2a681-103">Vous pouvez configurer des ports d'envoi dynamiques pour les adaptateurs WCF.</span><span class="sxs-lookup"><span data-stu-id="2a681-103">You can configure dynamic send ports for WCF adapters.</span></span> <span data-ttu-id="2a681-104">L’URI, une action et une liaison peuvent être déterminées à partir d’une propriété d’un message entrant et ensuite spécifiés dans le **Expression** mettre en forme, comme indiqué dans l’adaptateur WCF-NetTcp suivant :</span><span class="sxs-lookup"><span data-stu-id="2a681-104">The URI, action, and binding might be determined from a property on an incoming message, and then specified in the **Expression** shape, as shown in the following WCF-NetTcp adapter:</span></span>  
  
```  
MessageOut=MessageIn;  
MessageOut(WCF.Action)="http://tempuri.org/IReceiveMessage/ReceiveMessage";  
MessageOut(WCF.SecurityMode)="Transport";  
MessageOut(WCF.TransportClientCredentialType)="Windows";  
DynamicSendPort(Microsoft.XLANGs.BaseTypes.Address)="net.tcp://localhost:8001/netTcp";  
DynamicSendPort(Microsoft.XLANGs.BaseTypes.TransportType)="WCF-NetTcp";  
```  
  
 <span data-ttu-id="2a681-105">Le code suivant montre comment spécifier les propriétés de contexte WCF dans le **Expression** forme pour un adaptateur WCF-Custom :</span><span class="sxs-lookup"><span data-stu-id="2a681-105">The following code shows an example of how to specify the WCF context properties in the **Expression** shape for a WCF-Custom adapter:</span></span>  
  
```  
MessageOut=MessageIn;  
MessageOut(WCF.BindingType)="customBinding";  
MessageOut(WCF.Action)="http://tempuri.org/IReceiveMessage/ReceiveMessage";  
MessageOut(WCF.BindingConfiguration)=@"<binding name=""customBinding""><binaryMessageEncoding /><tcpTransport /></binding>";  
DynamicSendPort(Microsoft.XLANGs.BaseTypes.Address)="net.tcp://localhost:8001/customNetTcp";  
DynamicSendPort(Microsoft.XLANGs.BaseTypes.TransportType)="WCF-Custom";  
```  
  
 <span data-ttu-id="2a681-106">Lors de la configuration des propriétés de contexte WCF, les éléments à prendre en compte sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="2a681-106">Considerations when specifying WCF context properties are as follows:</span></span>  
  
-   <span data-ttu-id="2a681-107">Certaines adresses peuvent être mappées vers plusieurs adaptateurs.</span><span class="sxs-lookup"><span data-stu-id="2a681-107">There are addresses that can be mapped to multiple adapters.</span></span> <span data-ttu-id="2a681-108">Par exemple, une adresse commençant par http:// ou https:// peut être traitée par l'adaptateur HTTP comme par les adaptateurs WCF-BasicHttp, WCF-WsHttp ou WCF-Custom.</span><span class="sxs-lookup"><span data-stu-id="2a681-108">For example, an address that starts with http:// or https:// can be handled by the HTTP adapter as well as by the WCF-BasicHttp, WCF-WsHttp, or WCF-Custom adapters.</span></span> <span data-ttu-id="2a681-109">Un autre exemple réside dans l'utilisation du début d'adresse net.tcp:// dans les deux exemples de code précédents ; toutefois, étant donné que le deuxième exemple de code fait appel à une liaison personnalisée, il est recommandé d'utiliser l'adaptateur WCF-Custom pour traiter cette adresse.</span><span class="sxs-lookup"><span data-stu-id="2a681-109">For another example, in the above sample code, both of them are using the address starts with net.tcp://, yet because the second sample code uses custom binding, WCF-Custom adapter should be used to handle the address.</span></span> <span data-ttu-id="2a681-110">Par conséquent, pour identifier l’adaptateur adéquat, vous devez configurer le paramètre facultatif **Microsoft.XLANGs.BaseTypes.TransportType** champ dans un **Expression** forme avec la carte que vous souhaitez utiliser.</span><span class="sxs-lookup"><span data-stu-id="2a681-110">Therefore, to identify the correct adapter, you must configure the optional **Microsoft.XLANGs.BaseTypes.TransportType** field in an **Expression** shape with the adapter that you want to use.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2a681-111">Si l’adresse commence par http:// ou https:// et si vous ne spécifiez pas le **Microsoft.XLANGs.BaseTypes.TransportType** champ, par défaut, le moteur BizTalk utilise l’adaptateur HTTP.</span><span class="sxs-lookup"><span data-stu-id="2a681-111">If the address starts with http:// or https://, and if you do not specify the **Microsoft.XLANGs.BaseTypes.TransportType** field, by default, the BizTalk engine will use the HTTP adapter.</span></span>  
  
-   <span data-ttu-id="2a681-112">Le **WCF. BindingType** identifie la liaison par nom.</span><span class="sxs-lookup"><span data-stu-id="2a681-112">The **WCF.BindingType** identifies the binding by name.</span></span> <span data-ttu-id="2a681-113">Les valeurs possibles sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="2a681-113">It can be one of the following:</span></span>  
  
    -   <span data-ttu-id="2a681-114">basicHttpBinding</span><span class="sxs-lookup"><span data-stu-id="2a681-114">basicHttpBinding</span></span>  
  
    -   <span data-ttu-id="2a681-115">customBinding</span><span class="sxs-lookup"><span data-stu-id="2a681-115">customBinding</span></span>  
  
    -   <span data-ttu-id="2a681-116">netMsmqBinding</span><span class="sxs-lookup"><span data-stu-id="2a681-116">netMsmqBinding</span></span>  
  
    -   <span data-ttu-id="2a681-117">netNamedPipeBinding</span><span class="sxs-lookup"><span data-stu-id="2a681-117">netNamedPipeBinding</span></span>  
  
    -   <span data-ttu-id="2a681-118">netTcpBinding</span><span class="sxs-lookup"><span data-stu-id="2a681-118">netTcpBinding</span></span>  
  
    -   <span data-ttu-id="2a681-119">wsFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="2a681-119">wsFederationHttpBinding</span></span>  
  
    -   <span data-ttu-id="2a681-120">wsHttpBinding</span><span class="sxs-lookup"><span data-stu-id="2a681-120">wsHttpBinding</span></span>  
  
     <span data-ttu-id="2a681-121">La liste ci-dessus peut être étendue.</span><span class="sxs-lookup"><span data-stu-id="2a681-121">The above list can be extended.</span></span> <span data-ttu-id="2a681-122">Vous pouvez y ajouter votre propre liaison, par exemple FtpBinding.</span><span class="sxs-lookup"><span data-stu-id="2a681-122">For example, you can add your own binding to it such as FtpBinding.</span></span>  
  
-   <span data-ttu-id="2a681-123">Le **WCF. BindingConfiguration** spécifie la configuration de liaison pour le type de liaison.</span><span class="sxs-lookup"><span data-stu-id="2a681-123">The **WCF.BindingConfiguration** specifies the binding configuration for the binding type.</span></span> <span data-ttu-id="2a681-124">Elle récupère toute liaison inscrite dans le fichier de configuration de l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="2a681-124">It takes any binding that are registered in the machine configuration file.</span></span> <span data-ttu-id="2a681-125">Elle récupère également la configuration XML dans un format identique à celui utilisé dans la configuration des liaisons du fichier de configuration WCF.</span><span class="sxs-lookup"><span data-stu-id="2a681-125">It also takes the XML configuration in the same format as used in the binding configuration in the WCF configuration file.</span></span>  
  
-   <span data-ttu-id="2a681-126">Vous devrez peut-être spécifier des propriétés WCF supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="2a681-126">You may need to specify additional WCF properties.</span></span> <span data-ttu-id="2a681-127">Vous pouvez taper **WCF** dans l’éditeur d’Expression et IntelliSense fonctionnalité doit répertorier toutes les propriétés de contexte disponibles.</span><span class="sxs-lookup"><span data-stu-id="2a681-127">You can type **WCF** in the Expression Editor, and the IntelliSense feature should list all the available context properties.</span></span> <span data-ttu-id="2a681-128">Pour plus d’informations sur les propriétés de contexte WCF, consultez [propriétés et schéma de propriété des adaptateurs WCF](../core/wcf-adapters-property-schema-and-properties.md).</span><span class="sxs-lookup"><span data-stu-id="2a681-128">For more information about WCF context properties, see [WCF Adapters Property Schema and Properties](../core/wcf-adapters-property-schema-and-properties.md).</span></span>  
  
 <span data-ttu-id="2a681-129">Les exemples précédents montrent comment configurer **WCF. Action** en une seule action.</span><span class="sxs-lookup"><span data-stu-id="2a681-129">The preceding examples show how to configure **WCF.Action** with a single action.</span></span> <span data-ttu-id="2a681-130">Pour les scénarios de mappage à plusieurs actions, l'adaptateur WCF ne prend pas en charge l'utilisation du mappage à plusieurs actions avec les ports d'envoi dynamiques.</span><span class="sxs-lookup"><span data-stu-id="2a681-130">For multiple actions mapping scenarios, WCF adapter do not support using multiple actions mapping with dynamic send ports.</span></span> <span data-ttu-id="2a681-131">Vous pouvez définir l’action réelle le **WCF. Action** propriété de contexte comme décrit ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="2a681-131">You can just set the actual action in the **WCF.Action** context property as showing in above.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a681-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2a681-132">See Also</span></span>  
 <span data-ttu-id="2a681-133">[Spécification des Actions SOAP pour WCF des adaptateurs d’envoi](../core/specifying-soap-actions-for-wcf-send-adapters.md) </span><span class="sxs-lookup"><span data-stu-id="2a681-133">[Specifying SOAP Actions for WCF Send Adapters](../core/specifying-soap-actions-for-wcf-send-adapters.md) </span></span>  
 <span data-ttu-id="2a681-134">[Comment utiliser des Expressions pour affecter des valeurs à des Ports dynamiques](../core/how-to-use-expressions-to-assign-values-to-dynamic-ports.md) </span><span class="sxs-lookup"><span data-stu-id="2a681-134">[How to Use Expressions to Assign Values to Dynamic Ports](../core/how-to-use-expressions-to-assign-values-to-dynamic-ports.md) </span></span>  
 [<span data-ttu-id="2a681-135">Liaisons de port</span><span class="sxs-lookup"><span data-stu-id="2a681-135">Port Bindings</span></span>](../core/port-bindings.md)