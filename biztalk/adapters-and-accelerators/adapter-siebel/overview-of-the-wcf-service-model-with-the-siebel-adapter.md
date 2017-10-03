---
title: "Vue d’ensemble du modèle de service WCF avec l’adaptateur Siebel | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- how to, invoke operations on the Siebel system with a WCF client
- WCF service model, overview of
ms.assetid: 0e812473-0f50-4972-8b07-ec8edc2ef000
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3c638255b103a9c588f22d6ddcb2a75b81619b73
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="overview-of-the-wcf-service-model-with-the-siebel-adapter"></a>Vue d’ensemble du modèle de service WCF avec l’adaptateur Siebel
Le [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)] expose un système Siebel comme service WCF. Pour effectuer des opérations sur les artefacts du système Siebel, par exemple, pour appeler une méthode d’un service d’entreprise Siebel, vous appelez une opération sur la carte, qui, à son tour, exécute l’opération sur le système Siebel. Votre code est par conséquent agit comme un client au service WCF présenté par l’adaptateur.  
  
 Dans la [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] modèle de service, le contrat de service qui existe entre un client et un service est représenté sous la forme d’une interface .NET et les opérations sont représentées en tant que méthodes sur cette interface. Le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] et WCF fournissent des outils qui vous permettent de générer cette interface pour les opérations ciblées à partir des métadonnées qui expose de l’adaptateur. Ces outils créent également une classe de client WCF qui peut être utilisée pour appeler les opérations exposées dans l’interface de service. Une application cliente peut appeler les méthodes de la classe de client WCF pour appeler des opérations sur la carte.  
  
 La section suivante explique comment utiliser le modèle de service WCF pour appeler des opérations avec un client WCF.  
  
## <a name="invoking-operations-on-the-siebel-system-with-a-wcf-client"></a>Appel d’opérations sur le système Siebel avec un Client WCF  
 Pour utiliser le modèle de service WCF pour appeler des opérations sur le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)], vous devez commencer par générer une classe de client WCF pour les opérations de la cible. Vous pouvez ensuite créer une instance de cette classe, un client WCF et appeler ses méthodes pour effectuer ces opérations sur le système Siebel.  
  
#### <a name="to-invoke-operations-on-the-siebel-adapter"></a>Pour appeler des opérations sur l’adaptateur Siebel  
  
1.  Générer un code de classe et d’assistance de client WCF. Utilisez le [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] ou le service Model Metadata Utility Tool (svcutil.exe) pour générer une classe de client WCF ciblée sur les artefacts du système Siebel avec lequel vous souhaitez travailler. Pour plus d’informations sur la façon de générer un client WCF, consultez [générer un Client WCF ou un contrat de service WCF pour les artefacts de Solution Siebel](../../adapters-and-accelerators/adapter-siebel/generate-a-wcf-client-or-a-wcf-service-contract-for-siebel-solution-artifacts.md).  
  
2.  Créer une instance de client WCF et configurer le client WCF. Configuration du client WCF implique la spécification de la liaison et l’adresse de point de terminaison (URI de connexion) utilisé par le client. Ce faire, vous pouvez soit impérativement dans du code ou de façon déclarative dans la configuration. Pour plus d’informations sur la façon de configurer le client WCF, consultez [configurer un Client WCF pour un système Siebel](../../adapters-and-accelerators/adapter-siebel/configure-a-wcf-client-for-a-siebel-system.md). Le code suivant crée un client WCF qui cible le service d’entreprise Siebel TimeStamp. Il définit également les informations d’identification pour le système Siebel. Le client WCF est initialisé à partir de la configuration.  
  
    ```  
    BusinessServices_TimeStamp_OperationClient client =  
        new BusinessServices_TimeStamp_OperationClient("SiebelBinding_BusinessServices_TimeStamp_Operation");  
  
    client.ClientCredentials.UserName.UserName = "YourUserName";  
    client.ClientCredentials.UserName.Password = "YourPassword";  
    ```  
  
3.  Ouvrez le client WCF.  
  
    ```  
    client.Open();  
    ```  
  
4.  Appeler des méthodes sur le client WCF créé à l’étape 2 pour effectuer des opérations sur le système Siebel. Le code suivant appelle la **Execute** méthode du client WCF pour appeler le **Execute** méthode du service métier TimeStamp sur le système Siebel.  
  
    ```  
    // Create a parameter to hold the results and then invoke the Execute method of the TimeStamp business service.  
    microsoft.lobservices.siebel._2007._03.BusinessServices.TimeStamp.ExecuteResponseRecord er;  
    er = client.Execute();  
    ```  
  
5.  Fermez le client WCF.  
  
    ```  
    client.Close();  
    ```  
  
 Pour plus d’informations sur l’appel des méthodes de service d’entreprise Siebel, consultez [appeler des méthodes de Service métier avec l’adaptateur Siebel à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-siebel/run-business-service-methods-with-the-siebel-adapter-using-a-wcf-service.md) 
  
## <a name="see-also"></a>Voir aussi  
 [Développer des Applications Siebel à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-siebel/develop-siebel-applications-using-the-wcf-service-model.md)