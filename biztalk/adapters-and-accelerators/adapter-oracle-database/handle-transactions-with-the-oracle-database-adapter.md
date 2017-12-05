---
title: "Gérer des Transactions avec l’adaptateur de base de données Oracle | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 971c2fba-640c-4ae5-9ab3-2d8227c1627d
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5072a49c9edc5dc8ce03ec819d6042b640b94a47
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="handle-transactions-with-the-oracle-database-adapter"></a>Gérer des Transactions avec l’adaptateur de base de données Oracle
[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]ne lance pas une transaction lors d’une opération sur la base de données Oracle. Au lieu de cela, l’adaptateur effectue les opérations à l’aide du contexte de transaction fourni par les clients de la carte. Afin d’effectuer des opérations dans une transaction à l’aide de la [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], vous devez :  
  
-   Activer les transactions dans les clients de la carte. Par exemple, pour activer les transactions dans BizTalk Server, vous devez sélectionner le **utiliser une Transaction** case à cocher dans la **Transactions** zone de la **Messages** onglet pour WCF-Custom ou WCF-OracleDB port.  
  
-   Définir la valeur de la **UseAmbientTransaction** liaison de propriété **True** dans l’adaptateur. Pour plus d’informations sur la propriété de liaison, consultez [configurer les propriétés de liaison pour la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/configure-the-binding-properties-for-oracle-database.md).  
  
> [!IMPORTANT]
>  Pour utiliser l’adaptateur pour effectuer des transactions sur la base de données Oracle, vous devez avoir installé le **Oracle Services pour Microsoft Transaction Server** composant lors de l’installation du client Oracle, sur l’ordinateur qui exécute l’adaptateur client.  
  
## <a name="transactions-in-the-outbound-operations"></a>Transactions dans les opérations sortantes  
 Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] effectue une opération sortante dans une transaction unique. Pour les opérations de composites, toutes les opérations sont effectuées dans une seule transaction, mais à l’aide de différentes connexions ODP.NET. Pour plus d’informations sur les opérations sortantes exposés par le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], consultez [en quoi les métadonnées d’Oracle Surface adaptateur ?](https://msdn.microsoft.com/library/cc185310(v=bts.10).aspx).  
  
## <a name="transactions-in-the-inbound-operations"></a>Transactions dans les opérations entrantes  
 Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] expose les deux opérations entrantes suivantes :  
  
-   **L’interrogation**: l’instruction d’interrogation et l’instruction après interrogation (si spécifié) sont exécutées dans une transaction, tandis que l’instruction disponibles des données interrogées est exécutée dans une autre transaction. De même, l’instruction d’interrogation et l’instruction après interrogation sont exécutés à l’aide de la même connexion ODP.NET, tandis que les données interrogées disponibles instruction à l’aide d’une autre connexion ODP.NET.  
  
-   **Notification**: l’opération de notification est effectuée dans une transaction à l’aide d’une seule connexion ODP.NET.  
  
 Pour plus d’informations sur les opérations entrantes exposés par le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], consultez [en quoi les métadonnées d’Oracle Surface adaptateur ?](https://msdn.microsoft.com/library/cc185310(v=bts.10).aspx).  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de l’adaptateur BizTalk pour Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/overview-of-biztalk-adapter-for-oracle-database.md)