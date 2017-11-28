---
title: "Un comportement de service permet d’entrer les informations d’identification avec WCF LOB Adapter SDK | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9b203cfa-6331-4498-b656-8cd8339f8613
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3cc494e55aee70a9a441eccbe056f4651448752d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="use-a-service-behavior-to-enter-credentials-with-the-wcf-lob-adapter-sdk"></a><span data-ttu-id="0e35c-102">Un comportement de service permet d’entrer les informations d’identification avec WCF LOB Adapter SDK</span><span class="sxs-lookup"><span data-stu-id="0e35c-102">Use a service behavior to enter credentials with the WCF LOB Adapter SDK</span></span>
<span data-ttu-id="0e35c-103">De nombreux cas, les consommateurs de carte devront transmettre des informations d’identification à la ligne de la cible du système de l’entreprise.</span><span class="sxs-lookup"><span data-stu-id="0e35c-103">Many times, adapter consumers will be required to pass credentials to the target line of business system.</span></span> <span data-ttu-id="0e35c-104">Pour fournir cette fonctionnalité, vous devez fournir un comportement de service WCF.</span><span class="sxs-lookup"><span data-stu-id="0e35c-104">To provide this functionality, you will need to provide a WCF service behavior.</span></span>  
  
 <span data-ttu-id="0e35c-105">L’exemple de code suivant montre comment dériver un comportement de service.</span><span class="sxs-lookup"><span data-stu-id="0e35c-105">The following example code demonstrates how to derive a service behavior.</span></span> <span data-ttu-id="0e35c-106">Elle délègue les informations d’identification obtenues du consommateur de l’adaptateur à l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="0e35c-106">It delegates the credentials obtained from the consumer of the adapter to the adapter.</span></span> <span data-ttu-id="0e35c-107">L’adaptateur doit ensuite utiliser les protocoles line-of-business pour authentifier les informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="0e35c-107">The adapter then must use line-of-business protocols to authenticate the credentials.</span></span> <span data-ttu-id="0e35c-108">Une fois que les informations d’identification sont authentifiées, le service peut démarrer l’écoute des événements entrants à partir de la ligne de l’application d’entreprise.</span><span class="sxs-lookup"><span data-stu-id="0e35c-108">Once the credentials are authenticated, the service can start listening for incoming events from the line of business application.</span></span>  
  
```  
/// <summary>  
/// This class derives from a WCF service behavior.  It is used in the inbound scenario  
/// for the Inbound Service to pass the line-of-business credentials to the adapter using  
/// WCF ClientCredentials class.  
/// </summary>  
public class InboundClientCredentialsServiceBehavior : ClientCredentials, IServiceBehavior  
{  
    public InboundClientCredentialsServiceBehavior() { }  
  
    public InboundClientCredentialsServiceBehavior(InboundClientCredentialsServiceBehavior other)  
         : base(other)  
    {  
    }  
  
    #region IServiceBehavior Members  
  
    public void AddBindingParameters(ServiceDescription serviceDescription, System.ServiceModel.ServiceHostBase serviceHostBase, System.Collections.ObjectModel.Collection<ServiceEndpoint> endpoints, System.ServiceModel.Channels.BindingParameterCollection bindingParameters)  
    {  
        bindingParameters.Add(this);  
    }  
  
    public void ApplyDispatchBehavior(ServiceDescription serviceDescription, System.ServiceModel.ServiceHostBase serviceHostBase)  
    {  
    }  
  
    public void Validate(ServiceDescription serviceDescription, System.ServiceModel.ServiceHostBase serviceHostBase)  
    {  
    }  
  
    #endregion  
  
    protected override ClientCredentials CloneCore()  
    {  
        return new InboundClientCredentialsServiceBehavior(this);  
    }  
}  
```  
  
 <span data-ttu-id="0e35c-109">L’exemple de code suivant montre comment le comportement de service permet de transmettre des informations d’identification à l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="0e35c-109">The following example code shows how to use the service behavior to pass credentials to the adapter.</span></span>  
  
```  
// Create a ServiceHost for the EchoServiceImpl type  
// and use the base address from app.config  
ServiceHost host = new ServiceHost(typeof(EchoServiceImpl));  
  
// Set service behavior to pass the line-of-business credentials.  
InboundClientCredentialsServiceBehavior credentialsBehavior = new InboundClientCredentialsServiceBehavior();  
credentialsBehavior.UserName.UserName = "username";  
credentialsBehavior.UserName.Password = "****";  
host.Description.Behaviors.Add(credentialsBehavior);  
  
// Open the ServiceHost to start listening for messages  
host.Open();  
  
Console.WriteLine("The service is ready.");  
Console.WriteLine("Press <ENTER> to terminate service.");  
Console.ReadLine();  
  
// Close the ServiceHost  
host.Close();  
```  
  
## <a name="see-also"></a><span data-ttu-id="0e35c-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0e35c-110">See Also</span></span>  
 [<span data-ttu-id="0e35c-111">Recommandées de développement à l’aide de WCF LOB Adapter SDK</span><span class="sxs-lookup"><span data-stu-id="0e35c-111">Development best practices using the WCF LOB Adapter SDK</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/development-best-practices-using-the-wcf-lob-adapter-sdk.md)