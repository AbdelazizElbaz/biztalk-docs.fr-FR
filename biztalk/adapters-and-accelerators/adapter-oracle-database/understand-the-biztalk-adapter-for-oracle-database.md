---
title: "Comprendre l’adaptateur BizTalk pour base de données Oracle | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF LOB Adapter SDK
- features of Oracle database adapter
- table
- adapter client
- service model
- WCF
- artifacts
- database tables
- adapters, features
- Windows Communication Foundation
- adapter features
- channel model
ms.assetid: a8691957-0430-4cba-83f8-b60c21a86849
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bb2d3603bb6d7c64d355c88420167344f564ddd8
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="understand-the-biztalk-adapter-for-oracle-database"></a>Comprendre l’adaptateur BizTalk pour base de données Oracle
Le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] permet un accès par programmation orientée service pour pouvoir interagir avec un système externe. Les cartes présentent les avantages suivants aux clients :  
  
-   **Expérience de conception cohérente**. Les adaptateurs fournissent une expérience au moment du design commune et conviviale pour parcourir, rechercher et récupérer les métadonnées des artefacts LOB.  
  
-   **Diverses options de programmation**. Les adaptateurs fournissent un choix de modèle de programmation y compris le modèle de canal de Windows Communication Foundation (WCF), WCF service services Web de modèle, ADO.NET, ou BizTalk pris en charge les modèles.  
  
-   **Uniforme d’expérience sur LOB**. Les adaptateurs de normaliser l’utilisation de WCF et [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]et donc fournir une expérience uniforme d’accéder à n’importe quel système LOB.  
  
 Comme indiqué, les adaptateurs sont générés sur le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]. Le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] fournit une base commune pour la création d’adaptateurs d’intégration qui consommable une variété d’applications clientes telles que BizTalk Server et Microsoft Office. Le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] aligne la stratégie de carte avec la stratégie de Services Microsoft en exposant des adaptateurs d’intégration en tant que les canaux de Windows Communication Foundation (WCF). Pour plus d’informations sur la [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], consultez la [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] documentation. Le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] documentation est installée avec le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], généralement sous \<lecteur d’installation\>: \Program Files\\[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]\Documents.  
  
 Pour effectuer des opérations sur une base de données Oracle, les clients de l’adaptateur doivent avoir accès aux tables appropriées, les fonctions et procédures. Les tables de base de données sont l’unité de stockage dans la base de données Oracle. Des applications externes peuvent ajouter ou supprimer des données d’une table à l’aide d’instructions SQL. Les applications peuvent également accéder aux données dans les tables à l’aide de vues, fonctions et procédures. Avec [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)], les clients de l’adaptateur peuvent parcourir les artefacts tels que des tables, des procédures, des packages, des vues et des autres éléments de ce type dans une base de données Oracle. Les clients de l’adaptateur peuvent sélectionner les artefacts qu’ils requièrent pour leur solution et récupérer des métadonnées pour ces artefacts. Cela permet aux utilisateurs d’accéder et d’exécuter les opérations sur les artefacts dans la base de données Oracle.  
  
 Cette section répertorie les fonctionnalités de la [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Vue d’ensemble de l’adaptateur BizTalk pour Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/overview-of-biztalk-adapter-for-oracle-database.md)  
  
-   [Principales fonctionnalités de l’adaptateur BizTalk pour base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/key-features-in-biztalk-adapter-for-oracle-database.md)  
  
-   [Limitations de l’adaptateur BizTalk pour base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/limitations-of-biztalk-adapter-for-oracle-database.md)  
  
## <a name="see-also"></a>Voir aussi  
[Prise en main de BizTalk Server](../../core/getting-started-with-biztalk-server.md)