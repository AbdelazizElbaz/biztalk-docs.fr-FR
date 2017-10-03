---
title: "Présentation de l’architecture de l’adaptateur BizTalk pour SQL Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d31eb73f-b73e-4cd3-8b62-207b806175ee
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 841f07bfb8c027ab2bfc1b98e23b225af42b449c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="architecture-overview-of-biztalk-adapter-for-sql-server"></a>Présentation de l’architecture de l’adaptateur BizTalk pour SQL Server
Le [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] est un [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] liaison personnalisée. Cette liaison contient un élément de liaison de transport personnalisé unique qui permet la communication avec une base de données SQL Server. Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] est encapsulée par la [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)] temps d’exécution et est exposé à des applications via le [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] architecture de canal. Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] communique avec la base de données SQL Server via ADO.NET.  


 La figure suivante illustre l’architecture de bout en bout pour les solutions sont développées à l’aide de la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].  
  
 ![](../../adapters-and-accelerators/adapter-sql/media/05e2a88c-a3cc-42a7-9c06-cfdb7c071e70.gif "05e2a88c-a3cc-42a7-9c06-cfdb7c071e70")  

  
## <a name="consuming-the-adapter"></a>Utilisation de l’adaptateur  
 Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] expose la base de données SQL Server en tant qu’un [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] service pour les applications clientes. Pour effectuer des opérations et accéder aux données sur la base de données SQL Server, les applications clientes échangent des messages SOAP avec le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] via [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] canaux. L’illustration précédente montre quatre façons dans lequel le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] peuvent être utilisés.  
  
-   **Via un [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] application du modèle de canal**. A [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] application de modèle de canal effectue des opérations sur la base de données SQL Server à l’aide de la [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] modèle de canal pour échanger SOAP des messages directement avec le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]. Consultez [applications SQL de développer à l’aide du modèle de canal WCF](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-channel-model.md).
  
-   **Via un [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] application du modèle de service**. A [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] application de modèle de service appelle des méthodes sur un [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] client pour effectuer des opérations sur la base de données SQL Server. A [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] client modélise les opérations exposées par le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] en tant que méthodes de .NET. Vous pouvez utiliser la [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)] ou le WCF Service Model Metadata Utility Tool (svcutil.exe) pour créer un [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] classe de client à partir des métadonnées exposées par le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].  Consultez [applications SQL de développer à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-service-model.md).
  
-   **Via un BizTalk emplacement de réception ou port d’envoi qui est configuré pour utiliser l’adaptateur Microsoft BizTalk WCF-Custom**. L’adaptateur WCF-Custom permet d’utiliser [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] fonctionnalités d’extensibilité. À l’aide de l’adaptateur WCF-Custom, vous pouvez sélectionner et configurer la liaison de base de données SQL et le comportement de l’emplacement de réception ou port d’envoi. Pour plus d’informations sur l’utilisation de la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] dans [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] solutions, consultez [développement d’Applications BizTalk Server](../../core/developing-biztalk-server-applications.md). 
  
-   **Grâce à un service Web hébergé par IIS**. Dans ce scénario, un proxy de service WCF généré à l’aide de l’adaptateur est hébergé dans IIS à l’aide de la liaison de Http de WCF standard. Cela expose le contrat de service comme service Web aux utilisateurs externes. IIS héberge automatiquement l’adaptateur au moment de l’exécution, ce qui, à son tour, communique avec la base de données SQL Server.  
  
## <a name="the-sql-adapter-and-wcf"></a>L’adaptateur SQL et WCF  
 [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]présente un modèle de programmation basé sur l’échange de messages SOAP sur les canaux entre les clients et services. Ces messages sont envoyés entre les points de terminaison exposés par un client et un service de communication. Un point de terminaison se compose de :  
  
-   Un *adresse de point de terminaison*, qui spécifie l’emplacement auquel les messages sont reçus.  
  
-   A *liaison*, qui spécifie les protocoles de communication utilisés pour échanger des messages.  
  
-   A *contrat*, qui spécifie les types d’opérations et les données exposées par le point de terminaison.  
  
 Une liaison se compose d’un ou plusieurs éléments de liaison s’empilent autres pour définir la manière dont les messages sont échangés avec le point de terminaison. Au minimum, une liaison doit spécifier le transport et encodage qui sont utilisés pour échanger des messages avec le point de terminaison. Échange de messages entre points de terminaison se produit sur une pile de canaux qui se compose d’un ou plusieurs canaux. Chaque canal est une implémentation concrète de l’un des éléments de liaison dans la liaison configurée pour le point de terminaison. 

Le [documentation WCF](http://go.microsoft.com/fwlink/?LinkID=196850) comprend plus de détails sur [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]et le [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] modèle de programmation.  
  
 Le [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] expose un [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] liaison personnalisée, la liaison de base de données SQL (**Microsoft.Adapters.SQLDB.SQLDBBinding**). Par défaut, cette liaison contient un élément de liaison de transport personnalisé unique, l’élément de liaison de carte de base de données SQL (**Microsoft.Adapters.SQLDB.SQLDBAdapter**), ce qui permet des opérations sur une base de données SQL Server.  
  
 **Microsoft.Adapters.SQLDB.SQLDBBinding** (le SQL DB liaison) et **Microsoft.Adapters.SQLDB.SQLDBAdapter** (le SQL DB adaptateur élément de liaison) sont des classes publiques et sont également exposées au système de configuration. Étant donné que l’élément de liaison SQL DB carte est exposée publiquement, vous pouvez créer vos propres [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] liaisons permettant d’étendre les fonctionnalités de la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]. Par exemple, vous pouvez implémenter une liaison personnalisée pour prendre en charge Enterprise Single Sign-on (SSO) dans un [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] solution de modèle de canal ou de service. Les raisons de cette opération serait d’opérations d’agrégation de la base de données en une seule opération multifonction ou pour effectuer la transformation de schéma entre les opérations implémentées par une application personnalisée et les opérations sur la base de données SQL Server.  
  
 Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] repose sur le [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]et s’exécute sur le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] moment de l’exécution. Le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] fournit une infrastructure de framework et les outils logiciels qui le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] utilise pour fournir un ensemble complet de fonctionnalités aux utilisateurs et aux clients de la carte.  

## <a name="sql-adapter-and-the-wcf-lob-adapter-sdk"></a>Adaptateur SQL et WCF LOB Adapter SDK
Le [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] implémente un ensemble de composants qui tirent parti des fonctionnalités fournies par le [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)] et fournir la connectivité à la base de données SQL Server via ADO.NET.  
  
 Le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] sert de la couche du logiciel par le biais duquel le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] interagissant avec le [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]; ADO.NET sert de la couche par le biais duquel le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] interfaces avec la base de données SQL Server. L’illustration suivante montre les relations entre les composants internes de le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] et entre ces composants et d’ADO.NET.  
  
 ![](../../adapters-and-accelerators/adapter-sql/media/0b15e33b-7f59-4228-bb50-0455f7ed3d85.gif "0b15e33b-7f59-4228-bb50-0455f7ed3d85")  
 
   
## <a name="adonet"></a>ADO.NET  
 Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] se connecte à la base de données SQL Server via ADO.NET. ADO.NET propose un accès cohérent aux sources de données telles que SQL Server et facilite la récupération, la gestion et la modification des données dans les sources de données. En savoir plus sur [ADO.NET](https://msdn.microsoft.com/library/e80y5yhx.aspx).
  
 Le client SQL fournit la connectivité à la base de données SQL Server. Vous établissez une connexion à une base de données SQL Server en fournissant un URI de connexion à la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]. Cet URI de connexion contient le nom de l’ordinateur sur lequel est installé le serveur SQL Server et le nom de la base de données. Pour plus d’informations sur l’URI de connexion, consultez [créer une connexion à SQL Server](../../adapters-and-accelerators/adapter-sql/create-a-connection-to-sql-server.md).  
  
## <a name="see-also"></a>Voir aussi  

 [Comprendre l’adaptateur BizTalk pour SQL Server](../../adapters-and-accelerators/adapter-sql/understand-biztalk-adapter-for-sql-server.md)