---
title: "Vue d’ensemble du modèle de service WCF avec l’adaptateur de base de données Oracle | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF service model, overview
- invoking operations
- WCF service, creating and implementing
ms.assetid: 8ed765e5-b5e6-46bd-bcd6-282219caf75d
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 100bacfeaf2e06d7ff491ec77f88e00980a96fa1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="overview-of-the-wcf-service-model-with-the-oracle-database-adapter"></a>Vue d’ensemble du modèle de service WCF avec l’adaptateur de base de données Oracle
Lorsque vous consommez des opérations qui les [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] surfaces, votre code agit comme un client ou un service à l’adaptateur. Pour presque toutes les opérations qui les [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] surfaces, votre code est le client. Autrement dit, votre application appelle l’opération sur la carte ; par exemple insérer des enregistrements dans une table Oracle. La seule opération pour laquelle votre code fonctionne comme un service à le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] est pour l’opération POLLINGSMT. Dans ce cas, l’adaptateur envoie les résultats de l’opération de requête d’interrogation à votre application.  
  
 Dans la [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] modèle de service, le contrat de service qui existe entre un client et un service est représenté sous la forme d’une interface .NET et les opérations sont représentées en tant que méthodes sur cette interface. Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] et WCF fournissent des outils qui vous permettent de générer cette interface pour les opérations ciblées à partir des métadonnées qui expose de l’adaptateur. Ces outils créent également une classe de client WCF qui peut être utilisée pour appeler les opérations exposées dans l’interface de service. Une application cliente peut appeler les méthodes de la classe de client WCF pour appeler des opérations sur la carte. Pour implémenter un service pour la réception de l’opération POLLINGSTMT le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], vous implémentez l’interface générée pour l’opération POLLINGSTMT.  
  
 Les sections suivantes expliquent comment utiliser le modèle de service WCF pour créer un code client et le service pour le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].  
  
## <a name="creating-and-invoking-operations-on-a-wcf-client-by-using-the-oracle-database-adapter"></a>Création et l’appel d’opérations sur un Client WCF à l’aide de l’adaptateur de base de données Oracle  
 Pour utiliser le modèle de service WCF pour appeler des opérations sur le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], vous devez commencer par générer une classe de client WCF pour les opérations de la cible. Vous pouvez ensuite créer une instance de cette classe, un client WCF et appeler ses méthodes pour effectuer des opérations sur la base de données Oracle.  
  
#### <a name="to-invoke-operations-on-the-oracle-database-adapter"></a>Pour appeler des opérations sur la carte de base de données Oracle  
  
1.  Générer un code de classe et d’assistance de client WCF. Utilisez le [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] ou le service Model Metadata Utility Tool (svcutil.exe) pour générer une classe de client WCF ciblée sur les artefacts de base de données Oracle avec lequel vous souhaitez travailler. Pour plus d’informations sur la façon de générer un client WCF, consultez [génération d’un Client WCF ou un contrat de Service WCF pour les artefacts de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/create-a-wcf-client-or-wcf-service-contract-for-oracle-db-solution-artifacts.md).  
  
2.  Créez une instance du client WCF en spécifiant une liaison de client. Spécification d’une liaison de client implique la spécification de la liaison et l’adresse de point de terminaison utilisé par le client WCF. Ce faire, vous pouvez soit impérativement dans du code ou de façon déclarative dans la configuration. Pour plus d’informations sur la façon de spécifier une liaison de client, consultez [configurer un client de liaison pour la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/configure-a-client-binding-for-the-oracle-database.md). Le code suivant crée un client WCF qui peut être utilisé pour effectuer des opérations de data manipulation language (DML) sur une table de base de données Oracle (/ SCOTT/ACCOUNTACTIVITY). Il définit également les informations d’identification pour la base de données Oracle. Le client WCF est initialisé à partir de la configuration.  
  
    ```  
    SCOTTTableACCOUNTACTIVITYClient aaTableClient =   
        new SCOTTTableACCOUNTACTIVITYClient("OracleDBBinding_SCOTT.Table.ACCOUNTACTIVITY");  
  
    aaTableClient.ClientCredentials.UserName.UserName = "SCOTT";  
    aaTableClient.ClientCredentials.UserName.Password = "TIGER";  
    ```  
  
3.  Ouvrez le client WCF.  
  
    ```  
    aaTableClient.Open();  
    ```  
  
4.  Appeler des méthodes sur le client WCF créé à l’étape 2 pour effectuer des opérations sur la base de données Oracle. Le code suivant appelle la **sélectionnez** méthode du client WCF pour effectuer la requête SQL SELECT suivante sur la table ACCOUNTACTIVITY : `SELECT * FROM ACCOUNTACTIVITY`.  
  
    ```  
    // create a record set parameter to hold the SELECT query result set and invoke the Select operation;  
    microsoft.lobservices.oracledb._2007._03.SCOTT.Table.ACCOUNTACTIVITY.ACCOUNTACTIVITYRECORDSELECT[] selectRecords;  
    selectRecords = aaTableClient.Select("*", null);  
    ```  
  
5.  Fermez le client WCF.  
  
    ```  
    aaTableClient.Close();  
    ```  
  
 Pour plus d’informations sur l’exécution d’opérations DML sur les tables et vues, y compris l’opération Select ci-dessus, consultez [effectuant base opérations d’insertion, mise à jour, supprimer et sélectionnez à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-oracle-database/insert-update-delete-select-operations-in-oracle-db-using-a-wcf-service.md).  
  
## <a name="creating-and-implementing-a-wcf-service-by-using-the-oracle-database-adapter"></a>Création et implémentation d’un Service WCF à l’aide de l’adaptateur de base de données Oracle  
 Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] peut effectuer d’interrogation sur une table de base de données Oracle ou la vue. Cette fonctionnalité vous permet de spécifier une requête SQL SELECT que l’adaptateur doit s’exécuter régulièrement par rapport à la base de données Oracle. Les résultats de cette requête sont retournés à votre application via une opération particulière, l’opération POLLINGSTMT. Pour recevoir les résultats de la requête d’interrogation, votre application doit implémenter le service de contrat qui la [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] expose pour l’opération POLLINGSTMT.  
  
 Pour implémenter un service pour l’opération POLLINGSTMT de réception, vous devez tout d’abord générer l’interface .NET (également appelé le contrat de service WCF) qui représente le contrat de service exposé par le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] pour l’opération POLLINGSTMT. Pour plus d’informations, consultez [génération d’un Client WCF ou un contrat de Service WCF pour les artefacts de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/create-a-wcf-client-or-wcf-service-contract-for-oracle-db-solution-artifacts.md).  
  
 Ensuite, vous implémentez un service WCF en implémentant l’interface générée. Cette classe contient la logique métier pour traiter le message POLLINGSTMT et renvoyer une réponse à la carte. Puis vous utilisez un hôte de service (**System.ServiceModel.ServiceHost**) pour héberger une instance de ce service. Pour plus d’informations, consultez [Messages basés sur la réception d’interrogation de données modifiées à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-oracle-database/receive-polling-based-data-changed-messages-in-oracle-db-using-a-wcf-service.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Développer des Applications de base de données Oracle à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-service-model.md)