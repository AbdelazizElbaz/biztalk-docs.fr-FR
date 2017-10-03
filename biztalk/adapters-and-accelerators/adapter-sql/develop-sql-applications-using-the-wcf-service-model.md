---
title: "Développer des applications SQL à l’aide du modèle de Service WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d3ecfd6f-9144-4e41-a4b8-0c768a6ac254
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 645b783ad23d79b4f6be177f6d38287e62abab1a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="develop-sql-applications-using-the-wcf-service-model"></a>Développer des applications SQL à l’aide du modèle de Service WCF
[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]fournit un modèle de programmation appelé le modèle de service WCF, comme alternative au modèle de programmation canal WCF.  
  
 Le modèle de service WCF utilise des paradigmes .NET familiers pour masquer la complexité de l’échange de messages SOAP sur un canal. Le modèle de service accomplit cette simplification en lisant l’intégralité du message SOAP dans la mémoire avant de copier les informations dans les structures de données .NET. Le chargement de longs messages en mémoire, toutefois, peut-être pas pratique pour certaines applications. Dans ces cas, les développeurs doivent utiliser le modèle de canal WCF. Pour plus d’informations sur l’utilisation du modèle de canal WCF, consultez [applications SQL de développer à l’aide du modèle de canal WCF](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-channel-model.md).  
  
 Niveau le plus bas, [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] présente le modèle de canal WCF, dans laquelle les clients pour appeler les opérations sur un service en échangeant des messages SOAP sur un canal établi entre les points de terminaison de client et le service. Le modèle de canal WCF expose les types de données et des méthodes qui permettent d’agir directement sur l’architecture de canal WCF. Le modèle de canal WCF vous offre un contrôle direct sur le contenu des messages SOAP que vous créez et de façon à la fois votre application et le [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] les utiliser. Toutefois, des messages SOAP correct à envoyer via un canal de création et valider les messages de réponse retournés peuvent s’avérer détaillées et précises.  
  
 Le modèle de service WCF utilise des classes proxy pour appeler des opérations sur un service cible ou pour les opérations de réception à partir d’un client. Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] expose la base de données SQL Server sous la forme d’un service WCF sur lequel vous pouvez appeler des opérations.  
  
-   La classe proxy qui est utilisée pour appeler des opérations sur un service cible est appelée une classe de client WCF. Cette classe modélise les opérations exposées par un service en tant que méthodes .NET avec des paramètres fortement typés. À l’aide du modèle de service WCF, vous pouvez appeler les opérations exposées par le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] en tant que méthodes .NET sur le client WCF. Pour plus d’informations sur les clients WCF, consultez [vue d’ensemble du Client WCF](https://msdn.microsoft.com/library/ms735103.aspx).
  
 Vous pouvez utiliser un des outils suivants pour générer une classe de client WCF et le code d’application d’assistance à partir des métadonnées de service associé qui le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] expose :  
  
-   **Le service Model Metadata Utility Tool (svcutil.exe)**, qui est fourni avec WCF.  
  
-   **Le [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]** , qui est livré avec [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] et est intégré à la [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] expérience de conception. Cet outil présente une interface standard de Microsoft Windows qui fournit de puissantes de navigation et de recherche avancées sur les opérations qui expose de l’adaptateur. Pour plus d’informations sur la façon de générer une application cliente WCF, consultez [générer un Client WCF ou le contrat de Service WCF pour les artefacts de SQL Server](../../adapters-and-accelerators/adapter-sql/generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md).  
  
     Les rubriques de cette section contiennent des informations, des procédures et des exemples pour vous aider à créer et utiliser le modèle de service WCF pour développer des applications à l’aide de la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Vue d’ensemble du modèle de service WCF avec l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/overview-of-the-wcf-service-model-with-the-sql-adapter.md)  
  
-   [Métadonnées et le modèle de Service WCF avec l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/metadata-and-the-wcf-service-model-with-the-sql-adapter.md)  
  
-   [Générer un Client WCF ou le contrat de Service WCF pour les artefacts SQL Server](../../adapters-and-accelerators/adapter-sql/generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md)  
  
-   [Configurer une liaison de Client de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/configure-a-client-binding-for-the-sql-adapter.md)  
  
-   [Insérer, mettre à jour, supprimer ou sélectionner des opérations sur les tables d’interface et les vues à l’aide du modèle de service WCF](../../adapters-and-accelerators/adapter-oracle-ebs/insert-update-delete-select-on-interface-tables-and-views-with-a-wcf-service.md)  
  
-   [Exécuter des opérations sur les Tables et vues avec des Types de données volumineux dans SQL à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-sql/read-or-update-tables-and-views-with-large-data-types-in-sql-with-a-wcf-service.md)  
  
-   [Appeler les procédures stockées de SQL à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-sql/invoke-stored-procedures-in-sql-using-the-wcf-service-model.md)  
  
-   [Appeler des fonctions scalaires dans SQL Server à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-sql/invoke-scalar-functions-in-sql-server-by-using-the-wcf-service-model.md)  
  
-   [Appeler des fonctions table dans SQL Server à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-sql/invoke-table-valued-functions-in-sql-server-by-using-the-wcf-service-model.md)  
  
-   [Opérations ExecuteReader, ExecuteScalar ou ExecuteNonQuery dans SQL à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-sql/executereader-executescalar-executenonquery-in-sql-using-wcf-service-model.md)  
  
-   [Interrogation SQL Server à l’aide de l’adaptateur SQL avec le modèle de Service WCF](../../adapters-and-accelerators/adapter-sql/poll-sql-server-using-the-sql-adapter-with-wcf-service-model.md)  
  
-   [Recevoir des Notifications de requête SQL à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-sql/receive-query-notifications-from-sql-using-the-wcf-service-model.md)  
  
## <a name="see-also"></a>Voir aussi  
[Développer vos applications SQL](../../adapters-and-accelerators/adapter-sql/develop-your-sql-applications.md)