---
title: "Vue d’ensemble de l’architecture de l’adaptateur BizTalk pour base de données Oracle | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- adapter, and WCF
- architecture of the Oracle Database adapter
- ODAC
- Oracle Data Access Components
- endpoint
- adapter, architecture
- endpoint address
- ODP.NET
- Oracle Data Provider for .NET
- architecture
ms.assetid: cc59beb5-327a-4b00-a45c-82cc9d505167
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3f5d4a23b9802c04af37716f8bef07735d8f80bd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="architecture-overview-of-the-biztalk-adapter-for-oracle-database"></a>Vue d’ensemble de l’architecture de l’adaptateur BizTalk pour base de données Oracle
Décrit l’architecture de le [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]. 

Comprendre les [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] architecture peut vous aider à :  
  
-   Comprendre la relation entre la [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] et [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)].  
  
-   Comprendre les limites de sécurité, afin que vous pouvez mieux sécuriser des données dans votre solution.  
  
-   Comprendre les [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] propriétés de liaison.  
  
-   Résoudre les problèmes d’installation.  
  
Cette rubrique décrit l’architecture des solutions de bout en bout qui utilisent la [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] pour fonctionner sur une base de données Oracle et décrit également l’architecture interne de la [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].  
 
## <a name="adapter-architecture-overview"></a>Présentation de l’architecture adaptateur
Le [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] est un [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] liaison personnalisée. Cette liaison contient un élément de liaison de transport personnalisé unique qui permet la communication avec une base de données Oracle. Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] est encapsulée par la [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)] runtime et est exposé à des applications via le [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] architecture de canal. Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] communique avec la base de données Oracle par le biais du fournisseur de données Oracle pour .NET (ODP.NET) et le client Oracle, qui font partie d’Oracle données accès composants (ODAC) pour Windows.  
  
 La figure suivante illustre l’architecture de bout en bout pour les solutions sont développées à l’aide de la [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].  
  
 ![Diagramme d’architecture de carte de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/media/bts-oracledb-architecturec.gif "bts_OracleDB_Architecturec")  
  
## <a name="consuming-the-adapter"></a>Utilisation de l’adaptateur  
 Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] expose la base de données Oracle en tant qu’un [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] service pour les applications clientes. Pour effectuer des opérations et accéder aux données sur la base de données Oracle, les applications clientes échangent des messages SOAP avec le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] via [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] canaux. L’illustration précédente montre quatre façons dans lequel le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] peuvent être utilisés. Celles-ci sont les suivantes :  
  
-   Via un [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]application du modèle de canal. A [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] application de modèle de canal effectue des opérations sur la base de données Oracle à l’aide de la [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] modèle de canal pour échanger SOAP des messages directement avec le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]. Pour plus d’informations sur le développement de solutions pour le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] à l’aide de la [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] modèle de canal, consultez [application de développement de la base de données Oracle à l’aide du modèle de canal WCF](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-channel-model.md).  
  
-   Via un [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] application du modèle de service. A [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] application de modèle de service appelle des méthodes sur un [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] client pour effectuer des opérations sur la base de données Oracle. A [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] client modélise les opérations exposées par le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] en tant que méthodes de .NET. Vous pouvez utiliser la [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)] ou le WCF Service Model Metadata Utility Tool (svcutil.exe) pour créer un [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] classe de client à partir des métadonnées exposées par le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]. Pour plus d’informations sur la [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] modèle de service et le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], consultez [développer les Applications base de données Oracle à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-service-model.md).  
  
-   Via un BizTalk emplacement de réception ou port d’envoi qui est configuré pour utiliser l’adaptateur Microsoft BizTalk WCF-Custom. L’adaptateur WCF-Custom permet d’utiliser [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] fonctionnalités d’extensibilité. À l’aide de l’adaptateur WCF-Custom, vous pouvez sélectionner et configurer la liaison de base de données Oracle et le comportement de l’emplacement de réception ou port d’envoi. Pour plus d’informations sur l’utilisation de la [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] dans [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] solutions, consultez [développer vos applications BizTalk](../../core/develop-your-biztalk-applications.md).  
  
-   Grâce à un service Web hébergé par IIS. Dans ce scénario, un proxy de service WCF généré à l’aide de l’adaptateur est hébergé dans IIS à l’aide de la liaison de Http de WCF standard. Cela expose le contrat de service comme service Web aux utilisateurs externes. IIS héberge automatiquement l’adaptateur lors de l’exécution, ce qui, à son tour, communique avec la base de données Oracle.  
  
 Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] et ODAC se trouvent toujours in-process avec l’application ou le service qui utilise l’adaptateur.  
  
## <a name="oracle-database-adapter-and-wcf"></a>WCF et l’adaptateur de base de données oracle  
 [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]présente un modèle de programmation basé sur l’échange de messages SOAP sur les canaux entre les clients et services. Ces messages sont envoyés entre les points de terminaison exposés par un client et un service de communication. Un point de terminaison se compose de :  
  
-   Un *adresse de point de terminaison*, qui spécifie l’emplacement de réception des messages  
  
-   A *liaison*, qui spécifie les protocoles de communication utilisés pour échanger des messages  
  
-   A *contrat*, qui spécifie les types d’opérations et les données exposées par le point de terminaison.  
  
 Une liaison se compose d’un ou plusieurs éléments de liaison s’empilent autres pour définir la manière dont les messages sont échangés avec le point de terminaison. Au minimum, une liaison doit spécifier le transport et encodage qui sont utilisés pour échanger des messages avec le point de terminaison. Échange de messages entre points de terminaison se produit sur une pile de canaux qui se compose d’un ou plusieurs canaux. Chaque canal est une implémentation concrète de l’un des éléments de liaison dans la liaison configurée pour le point de terminaison. Le [documentation WCF](http://go.microsoft.com/fwlink/?LinkID=196850) comprend plus de détails sur [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]et le [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] modèle de programmation.  
  
 Le [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] expose un [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] liaison personnalisée, la liaison de base de données Oracle (**Microsoft.Adapters.OracleDB.OracleDBBinding**). Par défaut, cette liaison contient un élément de liaison de transport personnalisé unique, l’élément de liaison de carte de base de données Oracle (**Microsoft.Adapters.OracleDB.OracleDBAdapter**), ce qui permet des opérations sur une base de données Oracle.  
  
 **Microsoft.Adapters.OracleDB.OracleDBBinding** (le Oracle DB liaison) et **Microsoft.Adapters.OracleDB.OracleDBAdapter** (l’Oracle DB adaptateur élément de liaison) sont des classes publiques et sont également exposées à la système de configuration. Étant donné que l’élément de liaison Oracle DB carte est exposée publiquement, vous pouvez créer vos propres [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] liaisons permettant d’étendre les fonctionnalités de la [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]. Par exemple, vous pouvez implémenter une liaison personnalisée pour prendre en charge Enterprise Single Sign-on (SSO) dans un [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] solution de modèle de canal ou de service. Les raisons de cette opération serait d’opérations d’agrégation de la base de données en une seule opération multifonction ou pour effectuer la transformation de schéma entre les opérations sur la base de données Oracle et des opérations implémentées par une application personnalisée.  
  
 Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] repose sur le [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)] et s’exécute sur le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] runtime. Le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] fournit une infrastructure de framework et les outils logiciels qui le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] utilise pour fournir un ensemble complet de fonctionnalités aux utilisateurs et aux clients de la carte.  

## <a name="oracle-database-adapter-and-wcf-lob-adapter-sdk"></a>Adaptateur de base de données Oracle et le Kit de développement logiciel de l’adaptateur WCF LOB
Le [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] implémente un ensemble de composants qui tirent parti des fonctionnalités fournies par le [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)] et fournir la connectivité à la base de données Oracle par le biais du fournisseur de données Oracle pour .NET (ODP.NET).  
  
 Le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] sert de la couche du logiciel par le biais duquel le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] interagissant avec le [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]. ODP.NET sert de la couche par le biais duquel le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] interfaces avec la base de données Oracle. 
 
L’illustration suivante montre les relations entre les composants internes de la [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]et ODP.NET.  
  
 ![Architecture interne de l’adaptateur de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/media/fa730561-9db7-40d1-bfcd-bc4eb119eea8.gif "fa730561-9db7-40d1-bfcd-bc4eb119eea8")  
 
   
## <a name="odpnet"></a>ODP.NET  
 Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] se connecte à la base de données Oracle par le biais du ODP.NET et le client Oracle. Deux de ces composants font partie d’Oracle données accès composants (ODAC).  
  
 ODP.NET implémente un fournisseur de données pour la base de données Oracle qui est cohérente avec l’interface ADO.NET. Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] utilise les classes exposées par ODP.NET pour fonctionner sur la base de données Oracle.  
  
 Le client Oracle fournit la connectivité à la base de données Oracle. Vous établissez une connexion à une base de données Oracle en fournissant un URI de connexion à la [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]. Vous pouvez spécifier l’URI de connexion de deux manières :  
  
-   **À l’aide de tnsnames.ora**. Dans cette approche, l’URI fourni par le client de l’adaptateur de connexion contient uniquement le nom de service réseau spécifié dans le fichier tnsnames.ora. L’adaptateur extrait les paramètres de connexion telles que le nom du serveur, nom du service, numéro de port, etc. à partir de l’entrée de nom de service réseau dans le fichier. Pour utiliser cette approche, l’ordinateur qui exécute le client Oracle doit être configuré pour inclure le nom de service réseau pour la base de données Oracle dans le fichier tnsnames.ora.  
  
-   **Sans utiliser de tnsnames.ora**. Dans cette approche, les clients de l’adaptateur spécifient les paramètres de connexion directement dans l’URI de connexion. Cela ne nécessite pas le nom de service réseau d’être présents dans le fichier tnsnames.ora sur l’ordinateur client. Cette approche ne nécessite pas le fichier tnsnames.ora se trouvent sur l’ordinateur client.  
  
 Pour plus d’informations sur l’URI de connexion, consultez [créer une connexion à la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/create-a-connection-to-the-oracle-database.md).
  
## <a name="next"></a>Suivant
[Sécuriser vos applications de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/secure-your-oracle-database-applications.md)