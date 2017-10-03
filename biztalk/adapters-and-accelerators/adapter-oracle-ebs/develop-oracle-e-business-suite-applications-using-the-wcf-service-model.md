---
title: "Développer des applications d’Oracle E-Business Suite à l’aide du modèle de Service WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1cf3430d-12e9-437c-b398-d978faa4da2b
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 103a5f8c84b57693dd8f19d47d2b94d5e26256d9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="develop-oracle-e-business-suite-applications-using-the-wcf-service-model"></a>Développer des applications d’Oracle E-Business Suite à l’aide du modèle de Service WCF
[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]fournit un modèle de programmation appelé le modèle de service WCF pour se connecter à la [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]. Le modèle de service a été ajouté à WCF à résoudre en partie, certaines des limitations du modèle de programmation de canal WCF.  
  
 Le modèle de service WCF utilise des paradigmes .NET familiers pour masquer la complexité de l’échange de message SOAP sur un canal. Le modèle de service accomplit cette simplification en lisant l’intégralité du message SOAP dans la mémoire avant de copier les informations dans les structures de données .NET. Le chargement de longs messages en mémoire ne peut pas être pratique pour certaines applications. Dans ces cas, les développeurs doivent utiliser le modèle de canal WCF. Pour plus d’informations sur l’utilisation du modèle de canal WCF, consultez [développer des Applications Oracle E-Business Suite à l’aide du modèle de canal WCF](../../adapters-and-accelerators/adapter-oracle-ebs/develop-oracle-e-business-suite-applications-using-the-wcf-channel-model.md).  
  
 Niveau le plus bas, le [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] présente le modèle de canal WCF dans lequel les clients pour appeler les opérations sur un service en échangeant des messages SOAP sur un canal établi entre les points de terminaison de client et le service. Le modèle de canal WCF expose les types de données et des méthodes qui permettent d’agir directement sur l’architecture de canal WCF. Le modèle de canal WCF vous offre un contrôle direct sur le contenu des messages SOAP que vous créez et de façon à la fois votre application et le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] les utiliser. Toutefois, des messages SOAP correct à envoyer via un canal de création et valider les messages de réponse retournés peuvent s’avérer détaillées et précises.  
  
 Le modèle de service WCF utilise des classes proxy pour appeler des opérations sur un service cible ou pour les opérations de réception à partir d’un client. Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] expose Oracle E-Business Suite comme service WCF sur lequel vous pouvez appeler des opérations.  
  
-   La classe proxy utilisée pour appeler des opérations sur un service cible est appelée une classe de client WCF. Cette classe modélise les opérations exposées par un service en tant que méthodes .NET avec des paramètres fortement typés. À l’aide du modèle de service WCF, vous pouvez appeler les opérations exposées par le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] en tant que méthodes .NET sur le client WCF. Pour plus d’informations sur les clients WCF, consultez [vue d’ensemble du Client WCF](https://msdn.microsoft.com/library/ms735103.aspx).
  
 Vous pouvez utiliser un des outils suivants pour générer une classe de client WCF et le code d’application d’assistance à partir des métadonnées de service associé qui le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] expose :  
  
-   **Le service Model Metadata Utility Tool (svcutil.exe)**, qui est fourni avec WCF.  
  
-   **Le [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]** , qui est fourni avec le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] et est intégré à la [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] expérience de conception. Cet outil présente une interface standard de Microsoft Windows qui fournit de puissantes de navigation et de recherche avancées sur les opérations qui expose de l’adaptateur. Pour plus d’informations sur la façon de générer un client WCF, consultez [générer un Client WCF ou un contrat de Service WCF pour Oracle E-Business Suite des artefacts de Solution](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-wcf-client-or-wcf-service-contract-for-oracle-ebs-solution-artifacts.md).  
  
## <a name="in-this-section"></a>Dans cette section  
 Les rubriques suivantes fournissent des informations sur la façon de développer des applications qui utilisent le modèle de service WCF :  
  
-   [Vue d’ensemble du modèle de Service WCF avec l’adaptateur Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/overview-of-the-wcf-service-model-with-the-oracle-e-business-suite-adapter.md)  
  
-   [Métadonnées et le modèle de Service WCF avec Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/metadata-and-the-wcf-service-model-with-oracle-e-business-suite.md)  
  
-   [Générer un Client WCF ou un contrat de Service WCF pour les artefacts de Solution Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-wcf-client-or-wcf-service-contract-for-oracle-ebs-solution-artifacts.md)  
  
-   [Configurer une liaison de Client d’Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-a-client-binding-for-the-oracle-e-business-suite.md)  
  
-   [Exécution d’Insert, Update, Delete ou opérations Select sur les Tables d’Interface et les vues à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-oracle-ebs/insert-update-delete-select-on-interface-tables-and-views-with-a-wcf-service.md)  
  
-   [Effectuer des opérations sur les Tables avec des Types de données de grande taille dans Oracle E-Business Suite à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-oracle-ebs/run-table-operations-with-large-data-types-in-oracle-ebs-using-a-wcf-service.md)  
  
-   [Appeler des programmes simultanés dans Oracle E-Business Suite à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-oracle-ebs/run-concurrent-programs-in-oracle-e-business-suite-using-the-wcf-service-model.md)  
  
-   [Appeler des ensembles de requêtes dans Oracle E-Business Suite à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-oracle-ebs/invoke-request-sets-in-oracle-e-business-suite-using-the-wcf-service-model.md)  
  
-   [Réalisation d’opérations ExecuteReader, ExecuteScalar ou ExecuteNonQuery opérations dans Oracle E-Business Suite à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-oracle-ebs/executereader-executescalar-executenonquery-in-oracle-ebs-with-a-wcf-service.md)  
  
-   [Interrogation Oracle E-Business Suite à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-oracle-ebs/poll-oracle-e-business-suite-using-the-wcf-service-model.md)  
  
-   [Recevoir des Notifications de modification de base de données Oracle E-Business Suite à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-oracle-ebs/receive-oracle-ebs-database-change-notifications-using-the-wcf-service-model.md)  
  
## <a name="see-also"></a>Voir aussi  
[Développer vos applications Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/develop-your-oracle-e-business-suite-applications.md)