---
title: "Appeler des méthodes de Service d’entreprise avec l’adaptateur Siebel à l’aide du modèle de Service WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF service model, invoking business service methods
- business service methods, invoking by using the WCF service model
ms.assetid: b41cf944-efdc-453f-824b-70581e7143e7
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 27eafcbfadc353e8aed9430e2d1bed3ef9e16017
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="invoke-business-service-methods-with-the-siebel-adapter-using-the-wcf-service-model"></a>Appeler des méthodes de Service d’entreprise avec l’adaptateur Siebel à l’aide du modèle de Service WCF
Vous pouvez créer un client WCF que les méthodes de services d’entreprise Siebel cibles. Vous pouvez ensuite utiliser le client WCF pour appeler ces méthodes sur le système Siebel. Services d’entreprise Siebel sont signalées sous le nœud Services professionnels dans le [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]. Les méthodes exposées par chaque service de l’entreprise sont signalées sous le nœud correspondant à ce service. Vous pouvez suivre les étapes de [vue d’ensemble du modèle de Service WCF avec l’adaptateur Siebel](../../adapters-and-accelerators/adapter-siebel/overview-of-the-wcf-service-model-with-the-siebel-adapter.md) pour générer un client WCF pour un service d’entreprise et l’utiliser pour appeler les méthodes du service.  
  
 Le code suivant utilise un client WCF pour appeler le **Execute** méthode du service métier TimeStamp. L’horodatage, qui est retourné dans l’heure locale du serveur Siebel, est ensuite écrites dans la console. Le client WCF dans cet exemple est initialisé à partir d’un fichier de configuration généré par le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]. Pour obtenir un exemple de fichier de configuration généré, consultez [configurer un Client WCF pour un système Siebel](../../adapters-and-accelerators/adapter-siebel/configure-a-wcf-client-for-a-siebel-system.md).  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
  
using System.ServiceModel;  
using microsoft.lobservices.siebel._2007._03.BusinessServices.TimeStamp;  
  
namespace Business_Service  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            BusinessServices_TimeStamp_OperationClient client = null;  
  
            try  
            {  
                client =  
                     new BusinessServices_TimeStamp_OperationClient("SiebelBinding_BusinessServices_TimeStamp_Operation");  
  
                client.ClientCredentials.UserName.UserName = "YourUserName";  
                client.ClientCredentials.UserName.Password = "YourPassword";  
                client.Open();  
  
                ExecuteResponseRecord er = client.Execute();  
                Console.WriteLine(er.Time);  
  
                Console.WriteLine("\nHit <RETURN> to finish");  
                Console.ReadLine();  
            }  
            catch (Exception e)  
            {  
                Console.WriteLine(e.Message);  
            }  
            finally  
            {  
                // Close the client.  
                if (client != null)  
                {  
                    if (client.State == CommunicationState.Opened)  
                        client.Close();  
                    else  
                        client.Abort();  
                }  
            }  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Développer des Applications Siebel à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-siebel/develop-siebel-applications-using-the-wcf-service-model.md)