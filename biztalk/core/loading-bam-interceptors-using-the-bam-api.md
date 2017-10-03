---
title: "Chargement des intercepteurs BAM à l’aide de l’API BAM | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d77ea5fb-a796-48f1-8c77-173e995c5252
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 363c4fc43092e63b664d42bb0420263bd7439dad
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="loading-bam-interceptors-using-the-bam-api"></a>Chargement des intercepteurs BAM à l'aide de l'API BAM
Cette rubrique fournit des informations sur le chargement des intercepteurs WF et WCF à partir de votre code plutôt que par l'utilisation d'un fichier de configuration.  
  
## <a name="loading-the-wf-interceptor-from-code"></a>Chargement de l'intercepteur WF à partir d'un code  
 Pour charger le composant d'exécution de l'intercepteur WF à partir d'un code, vous devez créer une instance de WorkflowRuntime, puis appeler la méthode AddService avec une nouvelle instance de BamTrackingService. Cette opération est illustrée ci-dessous.  
  
```csharp  
string connectionString = "Integrated Security=SSPI;Data Source=.;Initial Catalog=BAMPrimaryImport";  
int PollingIntervalSec = 300;  
  
WorkflowRuntime workflowRuntime = new WorkflowRuntime();  
workflowRuntime.AddService(new BamTrackingService(connectionString, interceptorConfigurationPollingInterval));  
```  
  
## <a name="loading-the-wcf-interceptor-from-code"></a>Chargement de l'intercepteur WCF à partir d'un code  
 Pour charger l'intercepteur WCF, vous devez créer une classe dérivée qui est chargée d'ouvrir le service et qui est accessible à votre implémentation. Cette opération est illustrée ci-dessous.  
  
```csharp  
// Your project must have a reference to Microsoft.BizTalk.BAM.Interceptors.dll.  
// Create a derived class accessible to the implementation that opens the service.  
internal class MyBamBehaviorExtension : BamBehaviorExtension  
{  
    internal MyBamBehaviorExtension(string connectionString, int pollingInterval)  
        : base()  
    {  
        this.ConnectionString = connectionString;  
        this.PollingIntervalSec = pollingInterval.ToString();  
    }  
  
    internal IEndpointBehavior Create()  
    {  
        return (IEndpointBehavior) this.CreateBehavior();  
    }  
}  
  
// Add the endpoint behavior just before the service is opened.   
// In this example the connection string and polling intervals are being read from appSettings in App.config.  
MyBamBehaviorExtension bamBehaviorExtension = new MyBamBehaviorExtension(ConfigurationManager.AppSettings["ConnectionString"], int.Parse(ConfigurationManager.AppSettings["PollingIntervalSec"]));  
IEndpointBehavior bamBehavior = bamBehaviorExtension.Create();  
foreach (System.ServiceModel.Description.ServiceEndpoint endpoint in myServiceHost.Description.Endpoints)  
{  
    if (endpoint.Behaviors.Find<MyBamBehaviorExtension>() == null)  
        endpoint.Behaviors.Add(bamBehavior);  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide de l’analyse BAM intercepteurs WCF et WF](../core/using-the-bam-wcf-and-wf-interceptors.md)