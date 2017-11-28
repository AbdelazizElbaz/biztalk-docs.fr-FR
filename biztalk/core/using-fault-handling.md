---
title: "À l’aide de la gestion des erreurs | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dc793386-d2ec-4e02-9283-3237f65c9e01
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 00547917da65253123cb2067715a09633547eb4d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-fault-handling"></a><span data-ttu-id="76dc8-102">Utilisation de la gestion des erreurs</span><span class="sxs-lookup"><span data-stu-id="76dc8-102">Using Fault Handling</span></span>
<span data-ttu-id="76dc8-103">Au cours de [!INCLUDE[firstref_btsWinCommFoundation](../includes/firstref-btswincommfoundation-md.md)] un message d’exception de gestion d’erreurs n’est pas retournée au client, sauf si un **FaultException** (ou un sous-type) est levée ou un **FaultContract** est implémentée.</span><span class="sxs-lookup"><span data-stu-id="76dc8-103">During [!INCLUDE[firstref_btsWinCommFoundation](../includes/firstref-btswincommfoundation-md.md)] fault handling an exception message is not returned to the client unless a **FaultException** (or a subtype) is thrown or a **FaultContract** is implemented.</span></span> <span data-ttu-id="76dc8-104">Dans de tels scénarios, vous pouvez donc assurer le suivi des données uniquement à partir du message d'erreur.</span><span class="sxs-lookup"><span data-stu-id="76dc8-104">So you can only track data from the fault message itself in these scenarios.</span></span> <span data-ttu-id="76dc8-105">Une exception dans les implémentations de rappel automatiquement se présente comme un message d’erreur pour les deux **ServerFault** et **ClientFault** points de suivi.</span><span class="sxs-lookup"><span data-stu-id="76dc8-105">An exception in callback implementations automatically comes back as a fault message for both **ServerFault** and **ClientFault** track points.</span></span> <span data-ttu-id="76dc8-106">Toutefois, une erreur générique est toujours renvoyée avec un message générique.</span><span class="sxs-lookup"><span data-stu-id="76dc8-106">However, it will always return a generic fault with a generic message.</span></span> <span data-ttu-id="76dc8-107">Pour plus d’informations sur les contrats d’erreur WCF, consultez [http://go.microsoft.com/fwlink/?LinkId=83132](http://go.microsoft.com/fwlink/?LinkId=83132).</span><span class="sxs-lookup"><span data-stu-id="76dc8-107">For more information about WCF fault contracts, see [http://go.microsoft.com/fwlink/?LinkId=83132](http://go.microsoft.com/fwlink/?LinkId=83132).</span></span>  
  
 <span data-ttu-id="76dc8-108">Vous pouvez également suivre les constantes et les propriétés de contexte via les trackpoints d'erreur.</span><span class="sxs-lookup"><span data-stu-id="76dc8-108">You can also track constants and context properties through the fault track points.</span></span>  
  
 <span data-ttu-id="76dc8-109">Si les détails de l’exception sont renvoyés dans les erreurs à l’aide de la **IncludeExceptionDetailInFaults** attribut, vous extrayez le message d’exception réel via XPath.</span><span class="sxs-lookup"><span data-stu-id="76dc8-109">If exception details are returned in faults using the **IncludeExceptionDetailInFaults** attribute, you extract the actual exception message through the XPath.</span></span>  
  
 <span data-ttu-id="76dc8-110">Gestion d’erreurs est fournie par les trackpoints d’erreur définis dans [GetServiceContractCallPoint](../core/getservicecontractcallpoint.md):</span><span class="sxs-lookup"><span data-stu-id="76dc8-110">Fault handling is provided by the fault track points defined in [GetServiceContractCallPoint](../core/getservicecontractcallpoint.md):</span></span>  
  
-   <span data-ttu-id="76dc8-111">ServiceFault</span><span class="sxs-lookup"><span data-stu-id="76dc8-111">ServiceFault</span></span>  
  
-   <span data-ttu-id="76dc8-112">ClientFault</span><span class="sxs-lookup"><span data-stu-id="76dc8-112">ClientFault</span></span>  
  
-   <span data-ttu-id="76dc8-113">CallbackFault</span><span class="sxs-lookup"><span data-stu-id="76dc8-113">CallbackFault</span></span>  
  
 <span data-ttu-id="76dc8-114">À l'aide de ces trackpoints d'erreur, les données de l'erreur sont toujours rendues persistantes, même dans un scénario basé sur une transaction.</span><span class="sxs-lookup"><span data-stu-id="76dc8-114">When using these fault track points, fault data is always persisted, even when operating in a transaction-based scenario.</span></span> <span data-ttu-id="76dc8-115">L'intégrité transactionnelle est conservée sur toutes les données suivies non erronées, qui sont restaurées sous forme de réponse à l'erreur.</span><span class="sxs-lookup"><span data-stu-id="76dc8-115">Transactional integrity is maintained on all non-fault tracked data and non-fault tracked data is rolled back as a response to the fault.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="76dc8-116">Ces suivi points sont appliquées pour le chemin d’accès de la réponse et s’appliquent uniquement aux ServiceReply, ClientReply et CallbackReply contrat appel de points de service fournis par [GetServiceContractCallPoint](../core/getservicecontractcallpoint.md).</span><span class="sxs-lookup"><span data-stu-id="76dc8-116">These track points are applied to the reply path and apply only to the ServiceReply, ClientReply and CallbackReply service contract call points provided by [GetServiceContractCallPoint](../core/getservicecontractcallpoint.md).</span></span>  
  
## <a name="fault-configuration-sample"></a><span data-ttu-id="76dc8-117">Exemple de configuration d'erreur</span><span class="sxs-lookup"><span data-stu-id="76dc8-117">Fault Configuration Sample</span></span>  
 <span data-ttu-id="76dc8-118">L’exemple suivant illustre le suivi de message d’exception sur une **ServiceFault** lorsque le service lève une **FaultException** dans les **AuthorizationServiceFault** événement ; Sinon, il effectue le suivi de l’expression booléenne renvoyée par l’opération dans le **AuthorizationServiceReply** événement.</span><span class="sxs-lookup"><span data-stu-id="76dc8-118">The following sample demonstrates tracking the exception message on a **ServiceFault** when the service throws a **FaultException** in the **AuthorizationServiceFault** event; otherwise it tracks the Boolean expression returned by the operation in the **AuthorizationServiceReply** event.</span></span> <span data-ttu-id="76dc8-119">Soit le **AuthorizationServiceReply** OnEvent ou **AuthorizationServiceFault** OnEvent est rendu persistant.</span><span class="sxs-lookup"><span data-stu-id="76dc8-119">Either the **AuthorizationServiceReply** OnEvent or the **AuthorizationServiceFault** OnEvent is persisted.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="76dc8-120">L'implémentation de cet exemple illustre le fait que les trackpoints ServiceReply et ServiceFault s'excluent mutuellement.</span><span class="sxs-lookup"><span data-stu-id="76dc8-120">The implementation of this sample demonstrates the mutual exclusivity of the ServiceReply and ServiceFault trackpoints.</span></span>  
  
```  
<ic:OnEvent IsBegin ="true" IsEnd="false" Name="AuthorizationServiceReply" Source="ESCreditCardService">  
  
  <ic:Filter>  
    <ic:Expression>  
      <wcf:Operation Name="GetServiceContractCallPoint"/>  
      <ic:Operation Name ="Constant">  
        <ic:Argument>ServiceReply</ic:Argument>  
      </ic:Operation>  
      <ic:Operation Name ="Equals"/>  
      <wcf:Operation Name="GetOperationName" />  
      <ic:Operation Name="Constant">  
        <ic:Argument>AuthorizeWithDataContract</ic:Argument>  
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
  
  <ic:Update DataItemName="Status" Type="NVARCHAR">  
    <ic:Expression>  
      <ic:Operation Name="Constant">  
        <ic:Argument>Success</ic:Argument>  
      </ic:Operation>  
    </ic:Expression>  
  </ic:Update>  
  
  <ic:Update DataItemName="Result" Type="NVARCHAR">  
    <ic:Expression>  
      <wcf:Operation Name ="XPath">  
        <wcf:Argument>//s:Body/ccservice:*/ccservice:AuthorizeWithDataContractResult</wcf:Argument>  
      </wcf:Operation>  
    </ic:Expression>  
  </ic:Update>  
  
  <ic:Update DataItemName ="Service Call Date" Type ="DATETIME">  
    <ic:Expression>  
      <wcf:Operation Name ="GetContextProperty">  
        <wcf:Argument>EventTime</wcf:Argument>  
      </wcf:Operation>  
    </ic:Expression>  
  </ic:Update>  
  
</ic:OnEvent>  
  
<ic:OnEvent IsBegin ="true" IsEnd="false" Name="AuthorizationServiceFault" Source="ESCreditCardService">  
  
  <ic:Filter>  
    <ic:Expression>  
      <wcf:Operation Name="GetServiceContractCallPoint"/>  
      <ic:Operation Name ="Constant">  
        <ic:Argument>ServiceFault</ic:Argument>  
      </ic:Operation>  
      <ic:Operation Name ="Equals"/>  
      <wcf:Operation Name="GetOperationName" />  
      <ic:Operation Name="Constant">  
        <ic:Argument>AuthorizeWithDataContract</ic:Argument>  
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
  
  <ic:Update DataItemName="Status" Type="NVARCHAR">  
    <ic:Expression>  
      <ic:Operation Name="Constant">  
        <ic:Argument>Fault</ic:Argument>  
      </ic:Operation>  
    </ic:Expression>  
  </ic:Update>  
  
      <ic:Update DataItemName="Source" Type="NVARCHAR">  
        <ic:Expression>  
          <wcf:Operation Name ="XPath">  
            <wcf:Argument>//s:Body/Fault/Reason/Text</wcf:Argument>  
          </wcf:Operation>  
        </ic:Expression>  
      </ic:Update>  
  
  <ic:Update DataItemName ="Service Call Date" Type ="DATETIME">  
    <ic:Expression>  
      <wcf:Operation Name ="GetContextProperty">  
        <wcf:Argument>EventTime</wcf:Argument>  
      </wcf:Operation>  
    </ic:Expression>  
  </ic:Update>  
  
</ic:OnEvent>  
```  
  
## <a name="see-also"></a><span data-ttu-id="76dc8-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="76dc8-121">See Also</span></span>  
 [<span data-ttu-id="76dc8-122">Configuration de l’adaptateur WCF pour intercepter les données BAM</span><span class="sxs-lookup"><span data-stu-id="76dc8-122">Configuring the WCF Adapter to Intercept BAM Data</span></span>](../core/configuring-the-wcf-adapter-to-intercept-bam-data.md)