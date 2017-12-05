---
title: "Comprendre l’adaptateur BizTalk pour Oracle E-Business Suite | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 77a3f0a8-fc64-42cd-bb7c-0a6f527622e4
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 342ffbd77434a470e3afdd10ae1c708c8734e85c
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="understand-biztalk-adapter-for-oracle-e-business-suite"></a>Comprendre l’adaptateur BizTalk pour Oracle E-Business Suite
## <a name="biztalk-adapter-pack-features"></a>Fonctionnalités du Pack d’adaptateurs BizTalk
Le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] permet un accès par programmation orientée service pour pouvoir interagir avec un système externe. Les cartes présentent les avantages suivants aux clients :  
  
-   **Expérience de conception cohérente**. Les adaptateurs fournissent une expérience au moment du design commune et conviviale pour parcourir, rechercher et récupérer les métadonnées des artefacts LOB.  
  
-   **Diverses options de programmation**. Les adaptateurs fournissent un choix de modèle de programmation y compris le modèle de canal de Windows Communication Foundation (WCF), WCF service services Web de modèle, ADO.NET, ou BizTalk Server pris en charge les modèles.  
  
-   **Uniforme d’expérience sur LOB**. Les adaptateurs de normaliser l’utilisation de WCF et [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]et donc fournir une expérience uniforme d’accéder à n’importe quel système LOB.  
  
 Comme indiqué, les adaptateurs sont générés sur le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]. Ce kit fournit une base commune pour la création d’adaptateurs d’intégration qui consommable une variété d’applications clientes telles que BizTalk Server et Microsoft Office. Le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] aligne la stratégie de carte avec la stratégie de services Microsoft en exposant des adaptateurs d’intégration en tant que les canaux WCF. Pour plus d’informations sur la [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], consultez la [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] documentation. Le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] documentation est installée avec le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], généralement sous \< *lecteur d’installation*\>: \Program Files\\[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]\Documents.  

## <a name="overview-of-the-oracle-ebs-adapter"></a>Vue d’ensemble de l’adaptateur Oracle eBusiness Suite
Le [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] expose Oracle E-Business Suite comme service WCF. Les clients de l’adaptateur peuvent effectuer des opérations sur Oracle E-Business Suite en échangeant des messages SOAP avec l’adaptateur. L’adaptateur utilise le message SOAP et effectue des appels ODP.NET appropriés pour effectuer l’opération. L’adaptateur renvoie la réponse à partir d’Oracle E-Business Suite au client sous la forme des messages SOAP.  
  
 Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]affiche les métadonnées des artefacts de base de données Oracle sous-jacent (par exemple, les tables, les fonctions et procédures) qui décrivent les artefacts d’Oracle E-Business Suite (API PL/SQL, interface tables/vues, des programmes simultanés et ensembles de requêtes) la structure d’un message SOAP dans le formulaire de Web Services Description Language (WSDL). Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] utilise le [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)], [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], et [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] pour permettre aux clients d’adaptateur récupérer des métadonnées pour les opérations. L’adaptateur génère également des artefacts de programmation qui peuvent être utilisés dans votre solution de programmation. Pour plus d’informations sur [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)], [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], et [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)], consultez [se connecter à Oracle E-Business Suite dans Visual Studio](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-the-oracle-e-business-suite-in-visual-studio.md).  
  
 Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] utilise le fournisseur de données Oracle pour .NET (ODP.NET) 11.1.0.7 pour communiquer avec Oracle E-Business Suite. ODP.NET 11.1.0.7 est un des composants d’Oracle données accès composants (ODAC). Vous pouvez utiliser la [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] pour communiquer avec Oracle E-Business Suite comme suit :  
  
-   En développant des applications BizTalk. Pour plus d’informations, consultez [développement d’Applications BizTalk Server](../../core/developing-biztalk-server-applications.md).  
  
-   À l’aide de la [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] modèle de service. Pour plus d’informations, consultez [développer Oracle de base de données Applications à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-service-model.md).  
  
-   À l’aide du modèle de canal WCF. Pour plus d’informations, consultez [développer des Applications SQL à l’aide du modèle de canal WCF](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-channel-model.md).  

## <a name="access-to-oracle-e-business-suite"></a>Accès à Oracle E-Business Suite
 Pour effectuer des opérations dans Oracle E-Business Suite, les clients de l’adaptateur doivent avoir accès aux artefacts pertinentes dans Oracle E-Business Suite. Des applications externes peuvent ajouter ou supprimer des données dans les tables de base de données et les tables d’interface Oracle E-Business Suite à l’aide d’instructions SQL. Les applications peuvent également accéder aux données dans les tables d’interface et les tables de base de données à l’aide de vues, fonctions et procédures. Avec [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)], les clients de l’adaptateur peuvent parcourir les artefacts dans Oracle E-Business Suite, ainsi que dans la base de données sous-jacente. Dans Oracle E-Business Suite, les clients de l’adaptateur peuvent parcourir les tables d’interface, les vues de l’interface, les programmes simultanés et requête définit lors de la base de données Oracle, les clients de l’adaptateur peuvent parcourir les tables, vues, procédures stockées, fonctions, les API PL/SQL et les packages. Les clients de l’adaptateur peuvent sélectionner les artefacts qu’ils requièrent pour leur solution et récupérer des métadonnées pour ces artefacts. Cela permet aux utilisateurs d’accéder et d’exécuter les opérations sur les artefacts dans Oracle E-Business Suite et de la base de données Oracle.  
  
 Cette section répertorie les fonctionnalités de la [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)].  
  
## <a name="more-good-stuff"></a>Autre contenu intéressant  
  
-    [Connexion à Oracle E-Business Suite à l’aide de l’adaptateur](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-oracle-e-business-suite-using-the-adapter.md)

- [Parcourir, rechercher et obtenir des métadonnées d’Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/browse-search-and-get-oracle-e-business-suite-metadata.md)

- [Les opérations sont prises en charge par l’adaptateur Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/what-operations-are-supported-by-the-oracle-e-business-suite-adapter.md)

- [Gérer des transactions avec l’adaptateur de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/handle-transactions-with-the-oracle-database-adapter.md) 

- [Fonctionnalités pour les clients de l’adaptateur Oracle EBS](../../adapters-and-accelerators/adapter-oracle-ebs/features-for-oracle-ebs-adapter-clients.md) 

-   [Principales fonctionnalités de l’adaptateur BizTalk pour Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/key-features-in-biztalk-adapter-for-oracle-e-business-suite.md)  
  
-   [Limitations de l’adaptateur BizTalk pour Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/limitations-of-biztalk-adapter-for-oracle-e-business-suite.md)  
  
## <a name="see-also"></a>Voir aussi  
[Prise en main](../../adapters-and-accelerators/adapter-oracle-ebs/get-started-with-the-biztalk-adapter-for-oracle-e-business-suite.md)