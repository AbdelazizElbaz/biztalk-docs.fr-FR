---
title: "Comment configurer l’Interception WCF BAM | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d85aa130-3219-4df1-8974-a44a51a15002
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e90577a73abc0291635bf4b7d9bad34a11d1f806
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-the-bam-wcf-interception"></a><span data-ttu-id="651b2-102">Configuration de l'interception WCF BAM</span><span class="sxs-lookup"><span data-stu-id="651b2-102">How to Configure the BAM WCF Interception</span></span>
<span data-ttu-id="651b2-103">Pour configurer l'analyse BAM pour l'interception WCF, vous devez modifier le fichier de configuration de l'intercepteur de manière à ce qu'il puisse accéder au manifeste d'assembly correspondant à vos sources d'événements.</span><span class="sxs-lookup"><span data-stu-id="651b2-103">To configure BAM for WCF interception, you must modify the interceptor configuration file to access the proper assembly manifest for your event sources.</span></span>  
  
 <span data-ttu-id="651b2-104">Lorsque vous configurez les événements, vous devez spécifier correctement mis en forme [XPath](../core/xpath.md) expressions pour les actions.</span><span class="sxs-lookup"><span data-stu-id="651b2-104">When you are configuring the events you must specify properly formatted [XPath](../core/xpath.md) expressions for the actions.</span></span>  
  
 <span data-ttu-id="651b2-105">Vous pouvez créer correctement mis en forme [XPath](../core/xpath.md) expressions à utiliser dans la configuration de l’intercepteur en activant le suivi WCF et l’application en cours d’exécution pour générer un exemple de journal WCF qui contient le message.</span><span class="sxs-lookup"><span data-stu-id="651b2-105">You can create properly formatted [XPath](../core/xpath.md) expressions to use in the interceptor configuration by enabling WCF tracing and running the application to produce a sample WCF log which contains the message.</span></span> <span data-ttu-id="651b2-106">Vous pouvez utiliser la **Microsoft Service Trace Viewer** (SvcTraceViewer.exe) pour afficher le journal et extraire le message.</span><span class="sxs-lookup"><span data-stu-id="651b2-106">You can use the **Microsoft Service Trace Viewer** (SvcTraceViewer.exe) to view the log and extract the message.</span></span> <span data-ttu-id="651b2-107">Cet outil est inclus dans le Kit de développement WCF SDK.</span><span class="sxs-lookup"><span data-stu-id="651b2-107">The viewer is included with the WCF SDK.</span></span> <span data-ttu-id="651b2-108">L’élément [XPath](../core/xpath.md) expression peut être formée en fonction du message et appliquée à la configuration de l’intercepteur.</span><span class="sxs-lookup"><span data-stu-id="651b2-108">The desired [XPath](../core/xpath.md) expression can then be formed based on the message and applied to the interceptor configuration.</span></span>  
  
 <span data-ttu-id="651b2-109">Lors de la configuration de l'interception WCF de l'analyse BAM, il est essentiel que l'extension de comportement utilisée dans le fichier machine.config corresponde à celle utilisée dans la configuration de comportement personnalisée de l'emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="651b2-109">When configuring the BAM WCF interception, it is essential that the behavior extension used in the machine.config file matches the extension used in the custom behavior configuration of the receive location.</span></span> <span data-ttu-id="651b2-110">La modification du nom d'extension d'un emplacement de réception configuré dans le fichier machine.config provoque l'échec du chargement du comportement.</span><span class="sxs-lookup"><span data-stu-id="651b2-110">Changing the extension name of a configured receive location in the machine.config file causes the behavior to fail to load.</span></span> <span data-ttu-id="651b2-111">En outre, l'interface utilisateur de configuration de l'emplacement de réception échouera également.</span><span class="sxs-lookup"><span data-stu-id="651b2-111">In addition, the configuration UI of the receive location will fail.</span></span>  
  
 <span data-ttu-id="651b2-112">Dans un scénario de mise en cluster, le comportement personnalisé n'est configuré qu'une seule fois. Vous devez alors veiller à ce que tous les fichiers machine.config sur les ordinateurs du cluster indiquent une extension de nom de fichier identique.</span><span class="sxs-lookup"><span data-stu-id="651b2-112">In case of a clustered scenario, since the custom behavior is configured only once, you must ensure that all the machine.config files on the computers in the cluster specify the same file name extension.</span></span>  
  
### <a name="to-set-the-manifest"></a><span data-ttu-id="651b2-113">Pour définir le manifeste</span><span class="sxs-lookup"><span data-stu-id="651b2-113">To set the manifest</span></span>  
  
1.  <span data-ttu-id="651b2-114">Pour la propriété EventSource de la configuration de l'interception, définissez le manifeste comme suit : « Microsoft.BizTalk.Adapter.Wcf.Runtime.ITwoWayAsyncVoid, Microsoft.BizTalk.Adapter.Wcf.Runtime, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35 ».</span><span class="sxs-lookup"><span data-stu-id="651b2-114">Set the manifest in the EventSource in the Interception Configuration to 'Microsoft.BizTalk.Adapter.Wcf.Runtime.ITwoWayAsyncVoid, Microsoft.BizTalk.Adapter.Wcf.Runtime, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35'</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="651b2-115">L'interface est alors modifiée en fonction du type de service/port de réception utilisé.</span><span class="sxs-lookup"><span data-stu-id="651b2-115">The interface changes based on the type of service/receive port used.</span></span> <span data-ttu-id="651b2-116">D'après le tableau suivant, modifiez la ligne concernant le manifeste de manière à refléter le type de port que vous utilisez :</span><span class="sxs-lookup"><span data-stu-id="651b2-116">Change the manifest line to reflect the type of port you are using according to the table below.</span></span>  
  
    |<span data-ttu-id="651b2-117">Type de port</span><span class="sxs-lookup"><span data-stu-id="651b2-117">Port Type</span></span>|<span data-ttu-id="651b2-118">Utiliser</span><span class="sxs-lookup"><span data-stu-id="651b2-118">Use</span></span>|  
    |---------------|---------|  
    |<span data-ttu-id="651b2-119">Ports bidirectionnels</span><span class="sxs-lookup"><span data-stu-id="651b2-119">Two-way ports</span></span>|<span data-ttu-id="651b2-120">ITwoWayAsync</span><span class="sxs-lookup"><span data-stu-id="651b2-120">ITwoWayAsync</span></span>|  
    |<span data-ttu-id="651b2-121">Ports unidirectionnels avec une liaison qui est, par nature, bidirectionnelle (par exemple, HTTP).</span><span class="sxs-lookup"><span data-stu-id="651b2-121">One-way ports with binding that are inherently two 2 way (for example, HTTP).</span></span>|<span data-ttu-id="651b2-122">ITwoWayAsyncVoid</span><span class="sxs-lookup"><span data-stu-id="651b2-122">ITwoWayAsyncVoid</span></span>|  
    |<span data-ttu-id="651b2-123">Ports unidirectionnels avec une liaison qui est, par nature, bidirectionnelle avec transactions.</span><span class="sxs-lookup"><span data-stu-id="651b2-123">One-way ports with binding that are inherently two two-way with transactions.</span></span>|<span data-ttu-id="651b2-124">ITwoWayAsyncVoidTxn</span><span class="sxs-lookup"><span data-stu-id="651b2-124">ITwoWayAsyncVoidTxn</span></span>|  
    |<span data-ttu-id="651b2-125">Liaisons unidirectionnelles (par exemple, MSMQ).</span><span class="sxs-lookup"><span data-stu-id="651b2-125">Bindings that are one way (for example, MSMQ).</span></span>|<span data-ttu-id="651b2-126">IOneWayAsync</span><span class="sxs-lookup"><span data-stu-id="651b2-126">IOneWayAsync</span></span>|  
    |<span data-ttu-id="651b2-127">Liaisons unidirectionnelles avec transactions.</span><span class="sxs-lookup"><span data-stu-id="651b2-127">Bindings that are one way with transactions.</span></span>|<span data-ttu-id="651b2-128">IOneWayAsyncTxn</span><span class="sxs-lookup"><span data-stu-id="651b2-128">IOneWayAsyncTxn</span></span>|  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="651b2-129">Dans le filtre, au lieu d’utiliser le [GetOperationName](../core/getoperationname.md) opération, utilisez l’opération XPath en surbrillance dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="651b2-129">In the filter, instead of using the [GetOperationName](../core/getoperationname.md) operation, use XPath operation as highlighted in the following sample.</span></span> <span data-ttu-id="651b2-130">Pour les contrats génériques, tous les messages parviennent à une opération générique, à partir de laquelle ils sont acheminés vers des opérations particulières sur la base du message lui-même (attribut Action).</span><span class="sxs-lookup"><span data-stu-id="651b2-130">For generic contracts all messages arrive at some generic operation, at which point they get routed to specific operations based on the message itself (Action attribute).</span></span>  
  
2.  <span data-ttu-id="651b2-131">À ce stade, le nom de l'opération est toujours le même.</span><span class="sxs-lookup"><span data-stu-id="651b2-131">The operation name will always be the same at this point.</span></span> <span data-ttu-id="651b2-132">Pour les adaptateurs WCF (lesquels utilisent des contrats génériques), la méthode utilisée est BizTalkSubmit.</span><span class="sxs-lookup"><span data-stu-id="651b2-132">In case of WCF adapters (which uses generic contracts) the method used is BizTalkSubmit.</span></span> <span data-ttu-id="651b2-133">Pour extraire le nom de l'opération, vous pouvez utiliser une opération XPath pour le nœud Action au lieu d'employer l'opération GetOperationName.</span><span class="sxs-lookup"><span data-stu-id="651b2-133">You can use an XPath for the Action node instead of GetOperationName to retrieve the operation name.</span></span> <span data-ttu-id="651b2-134">Vous pouvez ensuite filtrer sur le nom de l'opération.</span><span class="sxs-lookup"><span data-stu-id="651b2-134">You can then filter on the operation name.</span></span>  
  
## <a name="sample-interceptor-configurations"></a><span data-ttu-id="651b2-135">Exemple de configurations de l'intercepteur</span><span class="sxs-lookup"><span data-stu-id="651b2-135">Sample Interceptor Configurations</span></span>  
 <span data-ttu-id="651b2-136">Cet exemple illustre l'utilisation de ServiceRequest et de ServiceReply pour l'adaptateur WCF.</span><span class="sxs-lookup"><span data-stu-id="651b2-136">This sample shows the usage of ServiceRequest and ServiceReply for the WCF adapter.</span></span> <span data-ttu-id="651b2-137">Dans la section en surbrillance une [XPath](../core/xpath.md) expression de l’Action est utilisée pour filtrer sur l’opération au lieu d’utiliser [GetOperationName](../core/getoperationname.md).</span><span class="sxs-lookup"><span data-stu-id="651b2-137">In the highlighted section an [XPath](../core/xpath.md) expression on the Action is used to filter on the operation instead of using [GetOperationName](../core/getoperationname.md).</span></span> <span data-ttu-id="651b2-138">Vous pouvez également filtrer sur la réponse, mais uniquement pour ITwoWayAsync.</span><span class="sxs-lookup"><span data-stu-id="651b2-138">You can filter on the reply as well, but only in the case of ITwoWayAsync.</span></span> <span data-ttu-id="651b2-139">Toutes les autres interfaces ne renvoient rien ou renvoient void.</span><span class="sxs-lookup"><span data-stu-id="651b2-139">All other interfaces return nothing or void.</span></span>  
  
### <a name="servicerequest"></a><span data-ttu-id="651b2-140">ServiceRequest</span><span class="sxs-lookup"><span data-stu-id="651b2-140">ServiceRequest</span></span>  
  
```  
<ic:OnEvent IsBegin="true" IsEnd ="false" Name ="WCFServiceRequest" Source="WCFService">  
      <ic:Filter>  
        <ic:Expression>  
          <wcf:Operation Name="GetServiceContractCallPoint"/>  
          <ic:Operation Name ="Constant">  
            <ic:Argument>ServiceRequest</ic:Argument>  
          </ic:Operation>  
          <ic:Operation Name ="Equals" />  
          <wcf:Operation Name ="XPath">  
            <wcf:Argument>//s:Header/a:Action</wcf:Argument>  
          </wcf:Operation>  
          <ic:Operation Name ="Constant">  
            <ic:Argument>Operation1</ic:Argument>  
          </ic:Operation>  
          <ic:Operation Name ="Equals" />  
          <ic:Operation Name ="And" />  
        </ic:Expression>  
      </ic:Filter>  
  
      <ic:CorrelationID>  
        <ic:Expression>  
          <wcf:Operation Name="AutoGenerateCorrelationToken"/>  
        </ic:Expression>  
      </ic:CorrelationID>  
  
      <ic:Update DataItemName ="Activity Date" Type ="DATETIME">  
        <ic:Expression>  
          <wcf:Operation Name ="GetContextProperty">  
            <wcf:Argument>EventTime</wcf:Argument>  
          </wcf:Operation>  
        </ic:Expression>  
      </ic:Update>  
  
      <ic:Update DataItemName ="Source" Type ="NVARCHAR">  
        <ic:Expression>  
          <ic:Operation Name="Constant">  
            <ic:Argument>WcfAdapter_ServiceRequest</ic:Argument>  
          </ic:Operation>  
        </ic:Expression>  
      </ic:Update>  
  
    </ic:OnEvent>  
```  
  
### <a name="servicereply"></a><span data-ttu-id="651b2-141">ServiceReply</span><span class="sxs-lookup"><span data-stu-id="651b2-141">ServiceReply</span></span>  
  
```  
<ic:OnEvent IsBegin="true" IsEnd ="false" Name ="WCFServiceReply" Source="WCFService">  
      <ic:Filter>  
        <ic:Expression>  
          <wcf:Operation Name="GetServiceContractCallPoint"/>  
          <ic:Operation Name ="Constant">  
            <ic:Argument>ServiceReply</ic:Argument>  
          </ic:Operation>  
          <ic:Operation Name ="Equals" />  
        </ic:Expression>  
      </ic:Filter>  
  
      <ic:CorrelationID>  
        <ic:Expression>  
          <wcf:Operation Name="AutoGenerateCorrelationToken"/>  
        </ic:Expression>  
      </ic:CorrelationID>  
  
      <ic:Update DataItemName ="Activity Date" Type ="DATETIME">  
        <ic:Expression>  
          <wcf:Operation Name ="GetContextProperty">  
            <wcf:Argument>EventTime</wcf:Argument>  
          </wcf:Operation>  
        </ic:Expression>  
      </ic:Update>  
  
      <ic:Update DataItemName ="Name" Type ="NVARCHAR">  
        <ic:Expression>  
          <ic:Operation Name="Constant">  
            <ic:Argument>WcfAdapter_ServiceReply</ic:Argument>  
          </ic:Operation>  
        </ic:Expression>  
      </ic:Update>  
  
    </ic:OnEvent>  
```  
  
## <a name="see-also"></a><span data-ttu-id="651b2-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="651b2-142">See Also</span></span>  
 [<span data-ttu-id="651b2-143">Configuration de l’adaptateur WCF pour intercepter les données BAM</span><span class="sxs-lookup"><span data-stu-id="651b2-143">Configuring the WCF Adapter to Intercept BAM Data</span></span>](../core/configuring-the-wcf-adapter-to-intercept-bam-data.md)