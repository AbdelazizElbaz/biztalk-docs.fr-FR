---
title: "Vue d’ensemble du modèle de service WCF avec l’adaptateur Oracle E-Business Suite | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aeeac8a4-a4bc-4963-951c-0c806e232f1e
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f40b22865ca45cbd10823f6c514f75e5965f1df5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="overview-of-the-wcf-service-model-with-the-oracle-e-business-suite-adapter"></a>Vue d’ensemble du modèle de service WCF avec l’adaptateur Oracle E-Business Suite
Le [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] expose un système Oracle E-Business Suite comme service WCF. Pour effectuer des opérations sur les artefacts d’Oracle E-Business Suite, par exemple, pour appeler une procédure stockée, vous appelez une opération sur la carte, qui, à son tour, exécute l’opération sur Oracle E-Business Suite. Votre code agit comme un client au service WCF présenté par l’adaptateur.  
  
 Dans la [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] modèle de service, le contrat de service qui existe entre un client et un service est représenté sous la forme d’une interface .NET et les opérations sont représentées en tant que méthodes sur cette interface. Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] et WCF fournissent des outils qui vous permettent de générer cette interface pour les opérations ciblées à partir des métadonnées qui expose de l’adaptateur. Ces outils créent également une classe de client WCF qui peut être utilisée pour appeler les opérations exposées dans l’interface de service. Une application cliente peut appeler les méthodes de la classe de client WCF pour appeler des opérations sur la carte.  
  
 La section suivante explique comment utiliser le modèle de service WCF pour appeler des opérations avec un client WCF.  
  
## <a name="invoking-operations-on-the-oracle-e-business-suite-with-a-wcf-client"></a>Appel d’opérations sur Oracle E-Business Suite avec un Client WCF  
 Pour utiliser le modèle de service WCF pour appeler des opérations sur le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], vous devez commencer par générer une classe de client WCF pour les opérations de la cible. Vous pouvez ensuite créer une instance de cette classe, un client WCF et appeler ses méthodes pour effectuer ces opérations sur Oracle E-Business Suite.  
  
#### <a name="to-invoke-operations-on-the-oracle-e-business-adapter"></a>Pour appeler des opérations sur l’adaptateur Oracle E-Business  
  
1.  Générer un code de classe et d’assistance de client WCF. Utilisez le [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] ou le service Model Metadata Utility Tool (svcutil.exe) pour générer une classe de client WCF ciblée sur les artefacts d’Oracle E-Business Suite avec lequel vous souhaitez travailler. Pour plus d’informations sur la façon de générer un client WCF, consultez [générer un Client WCF ou un contrat de Service WCF pour les artefacts de Solution Oracle E-Business](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-wcf-client-or-wcf-service-contract-for-oracle-ebs-solution-artifacts.md).  
  
2.  Créer une instance de client WCF et configurer le client WCF. Configuration du client WCF implique la spécification de la liaison et l’adresse de point de terminaison (URI de connexion) utilisé par le client. Ce faire, vous pouvez soit impérativement dans du code ou de façon déclarative dans la configuration. Le code suivant crée un client WCF qui cible le **Interface client** simultanées du programme dans le **des comptes clients** application dans Oracle E-Business Suite. Il définit également les informations d’identification pour Oracle E-Business Suite. Le client WCF est initialisé à partir de la configuration.  
  
    ```  
    ConcurrentPrograms_ARClient client = new ConcurrentPrograms_ARClient("OracleEBSBinding_ConcurrentPrograms_AR"); //picking the binding and address from app.config  
  
    client.ClientCredentials.UserName.UserName = "myuser";  
    client.ClientCredentials.UserName.Password = "mypassword";  
    ```  
  
    > [!NOTE]
    >  Vous pouvez spécifier l’adresse de liaison et le point de terminaison client dans le code ou déclarer dans le fichier de configuration app.config. L’extrait de code précédent utilise ce dernier. Pour plus d’informations sur l’utilisation des deux approches, consultez [configurer une liaison de Client d’Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-a-client-binding-for-the-oracle-e-business-suite.md).  
  
3.  Ouvrez le client WCF.  
  
    ```  
    client.Open();  
    ```  
  
4.  Appeler des méthodes sur le client WCF créé à l’étape 2 pour effectuer des opérations sur Oracle E-Business Suite. Le code suivant appelle la **Interface client** simultanées du programme dans le **des comptes clients** application dans Oracle E-Business Suite.  
  
    ```  
    string Result = client.RACUST(null, null, null, description, null, recipro_cust, org_id);  
    ```  
  
     **RACUST** est le nom réel du programme client Interface simultané. **Interface client** est le nom convivial du programme simultané.  
  
5.  Fermez le client WCF.  
  
    ```  
    client.Close();  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Développer à l’aide du modèle de canal WCF les Applications Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/develop-oracle-e-business-suite-applications-using-the-wcf-service-model.md)