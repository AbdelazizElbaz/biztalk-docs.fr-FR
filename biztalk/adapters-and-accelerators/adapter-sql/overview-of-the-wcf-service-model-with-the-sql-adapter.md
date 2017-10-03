---
title: "Vue d’ensemble du modèle de service WCF avec l’adaptateur SQL | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7641bcc7-3845-4914-9b1b-cb86b998ea6d
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3afbf1822945f0a47b09a93b3ac3cc2f8ac8653d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="overview-of-the-wcf-service-model-with-the-sql-adapter"></a>Vue d’ensemble du modèle de service WCF avec l’adaptateur SQL
Le [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] expose une opération SQL Server comme un service WCF. Pour effectuer des opérations sur les artefacts de SQL Server, par exemple, pour appeler une procédure stockée, vous appelez une opération sur la carte, qui, à son tour, exécute l’opération sur le serveur SQL Server. Votre code est par conséquent agit comme un client au service WCF présenté par l’adaptateur.  
  
 Dans la [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] modèle de service, le contrat de service qui existe entre un client et un service est représenté sous la forme d’une interface .NET et les opérations sont représentées en tant que méthodes sur cette interface. Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] et WCF fournissent des outils qui vous permettent de générer cette interface pour les opérations ciblées à partir des métadonnées qui expose de l’adaptateur. Ces outils créent également une classe de client WCF qui peut être utilisée pour appeler les opérations exposées dans l’interface de service. Une application cliente peut appeler les méthodes de la classe de client WCF pour appeler des opérations sur la carte. Pour implémenter un service pour recevoir les opérations entrantes à partir de la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], vous implémentez l’interface généré pour les opérations entrantes.  
  
 La section suivante explique comment utiliser le modèle de service WCF pour appeler des opérations avec un client WCF.  
  
## <a name="invoking-operations-on-the-sql-server-with-a-wcf-client"></a>Appel d’opérations sur le serveur SQL Server avec un Client WCF  
 Pour utiliser le modèle de service WCF pour appeler des opérations sur le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], vous devez commencer par générer une classe de client WCF pour les opérations de la cible. Vous pouvez ensuite créer une instance de cette classe, un client WCF et appeler ses méthodes pour effectuer ces opérations sur le système SQL Server. Cette section fournit une description de la façon dont une application de client de carte .NET classique ressemble à. Des explications détaillées sur la façon d’effectuer différentes opérations sur la base de données SQL Server à l’aide de l’adaptateur sont fournies dans les rubriques spécifiques.  
  
#### <a name="to-invoke-operations-on-the-sql-adapter"></a>Pour appeler des opérations sur l’adaptateur SQL  
  
1.  Générer un code de classe et d’assistance de client WCF. Utilisez le [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]pour générer une classe de client WCF ciblé sur les artefacts de base de données SQL Server avec lequel vous souhaitez travailler. Pour plus d’informations sur la façon de générer un client WCF, consultez [générer un Client WCF ou le contrat de Service WCF pour les artefacts de SQL Server](../../adapters-and-accelerators/adapter-sql/generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md).  
  
2.  Créer une instance de client WCF et configurer le client WCF. Configuration du client WCF implique la spécification de la liaison et l’adresse de point de terminaison (URI de connexion) utilisé par le client. Ce faire, vous pouvez soit impérativement dans du code ou de façon déclarative dans la configuration. Le code suivant crée un client WCF qui cible le **sélectionnez** opération sur le **employé** table dans une base de données SQL Server. Il définit également les informations d’identification pour la base de données SQL Server. Le client WCF est initialisé à partir de la configuration.  
  
    ```  
    TableOp_dbo_EmployeeClient client = new TableOp_dbo_EmployeeClient("SqlAdapterBinding_TableOp_dbo_Employee"); //picking the binding and address from the app.config  
  
    client.ClientCredentials.UserName.UserName = "myuser";  
    client.ClientCredentials.UserName.Password = "mypassword";  
    ```  
  
    > [!NOTE]
    >  Vous pouvez spécifier l’adresse de liaison et le point de terminaison client dans le code ou déclarer dans le fichier de configuration app.config. L’extrait de code précédent utilise ce dernier. Pour plus d’informations sur l’utilisation des deux approches, consultez [configurer une liaison de Client de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/configure-a-client-binding-for-the-sql-adapter.md).  
  
3.  Ouvrez le client WCF.  
  
    ```  
    client.Open();  
    ```  
  
4.  Appeler des méthodes sur le client WCF créé à l’étape précédente pour effectuer une opération Select sur la base de données SQL server. Le code suivant appelle la méthode de sélection du client WCF pour appeler l’instruction SELECT sur une table de base de données SQL Server.  
  
    ```  
    client.Select("*", "where [Name] = ‘John Smith’");  
    ```  
  
5.  Fermez le client WCF.  
  
    ```  
    client.Close();  
    ```  
  
## <a name="see-also"></a>Voir aussi  
[Développer des applications SQL à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-service-model.md)