---
title: "Comprendre l’adaptateur BizTalk pour SQL Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 302a7f20-ffa2-49f1-a4c4-dd713adc23e1
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ce5fdb7f3bcc6f0ef87a021db4375a90ce3be16d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="understand-biztalk-adapter-for-sql-server"></a>Comprendre l’adaptateur BizTalk pour SQL Server
Le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] permet d’accéder par programmation orientée service permettant d’interagir avec un système externe. Les cartes présentent les avantages suivants aux clients :  
  
-   **Expérience de conception cohérente**. Les adaptateurs fournissent une expérience au moment du design commune et conviviale pour parcourir, rechercher et récupérer les métadonnées des artefacts LOB.  
  
-   **Diverses options de programmation**. Les adaptateurs fournissent un choix de modèle de programmation y compris le modèle de canal de Windows Communication Foundation (WCF), WCF service services Web de modèle, ADO.NET, ou BizTalk pris en charge les modèles.  
  
-   **Uniforme d’expérience sur LOB**. Les adaptateurs de normaliser l’utilisation de WCF et [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]et donc fournir une expérience uniforme d’accéder à n’importe quel système LOB.  
  
 Comme indiqué, les adaptateurs sont générés sur le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]. Le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] fournit une base commune pour la création d’adaptateurs d’intégration qui consommable une variété d’applications clientes telles que BizTalk Server et Microsoft Office. Le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] aligne la stratégie de carte avec la stratégie de Services Microsoft en exposant des adaptateurs d’intégration en tant que les canaux de Windows Communication Foundation (WCF). Pour plus d’informations sur la [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], consultez la [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] documentation. Le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] documentation est installée avec le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], généralement sous \<lecteur d’installation > : \Program Files\\[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]\Documents.  
  
 Pour effectuer des opérations sur une base de données SQL Server, les clients de l’adaptateur doivent accéder aux tables appropriées, procédures, vues, fonctions scalaires et fonctions table. Les tables de base de données sont l’unité de stockage dans la base de données SQL Server. Des applications externes peuvent sélectionner, insérer, supprimer et mettre à jour des données à partir d’une table à l’aide d’instructions SQL. Les applications peuvent également accéder aux données dans les tables à l’aide de procédures, vues, fonctions scalaires et fonctions table. Avec [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)], les clients de l’adaptateur peuvent parcourir les artefacts, tels que des tables, des procédures, des vues et des autres éléments de ce type dans une base de données SQL Server. Les clients de l’adaptateur peuvent sélectionner les artefacts qu’ils requièrent pour leur solution et récupérer des métadonnées pour ces artefacts. Cela permet aux utilisateurs d’accéder et d’exécuter les opérations sur les artefacts dans la base de données SQL Server.  
  
 Cette section répertorie les fonctionnalités de la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Vue d’ensemble de l’adaptateur BizTalk pour SQL Server](../../adapters-and-accelerators/adapter-sql/overview-of-biztalk-adapter-for-sql-server.md)  
  
-   [Principales fonctionnalités de l’adaptateur BizTalk pour SQL Server](../../adapters-and-accelerators/adapter-sql/key-features-in-biztalk-adapter-for-sql-server.md) 
  
-   [Limitations de l’adaptateur BizTalk pour SQL Server](../../adapters-and-accelerators/adapter-sql/limitations-of-biztalk-adapter-for-sql-server.md)  
  
## <a name="see-also"></a>Voir aussi  
[Prise en main l’adaptateur BizTalk pour SQL](../../adapters-and-accelerators/adapter-sql/get-started-with-the-biztalk-adapter-for-sql.md)