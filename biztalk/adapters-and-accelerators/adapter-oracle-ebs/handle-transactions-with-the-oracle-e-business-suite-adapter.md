---
title: "Gérer des transactions avec l’adaptateur Oracle E-Business Suite | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b443be9d-a93d-4836-8717-5ee9dad4442f
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7d3d9946db7ea9ec1e9d035aa34081c1a11c113e
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="handle-transactions-with-the-oracle-e-business-suite-adapter"></a>Gérer des transactions avec l’adaptateur Oracle E-Business Suite
[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]ne lance pas une transaction lors d’une opération dans Oracle E-Business Suite. Au lieu de cela, l’adaptateur effectue les opérations à l’aide du contexte de transaction fourni par les clients de la carte. Afin d’effectuer des opérations dans une transaction à l’aide de la [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], vous devez :  
  
-   Activer les transactions dans les clients de la carte. Par exemple, pour activer les transactions dans BizTalk Server, vous devez sélectionner le **utiliser une Transaction** case à cocher dans la **Transactions** zone de la **Messages** onglet pour WCF-Custom ou WCF-OracleEBS port.  
  
-   Définir la valeur de la **UseAmbientTransaction** liaison de propriété **True** dans l’adaptateur. Pour plus d’informations sur la propriété de liaison, consultez [en savoir plus sur l’adaptateur BizTalk pour Oracle E-Business Suite liaison propriétés](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md).  
  
> [!IMPORTANT]
>  Pour utiliser l’adaptateur pour effectuer des transactions dans Oracle E-Business Suite, vous devez avoir installé le **Oracle Services pour Microsoft Transaction Server** composant lors de l’installation du client Oracle, sur l’ordinateur qui exécute l’adaptateur client.  
  
## <a name="transactions-in-the-outbound-operations"></a>Transactions dans les opérations sortantes  
 Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] effectue une opération sortante dans une transaction unique. Pour les opérations de composites, toutes les opérations sont effectuées dans une seule transaction, mais à l’aide de différentes connexions ODP.NET. Pour plus d’informations sur les opérations sortantes exposés par le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], consultez [en quoi les métadonnées de l’adaptateur Surface Oracle E-Business Suite ?](https://msdn.microsoft.com/library/dd788431.aspx).  
  
## <a name="transactions-in-the-inbound-operations"></a>Transactions dans les opérations entrantes  
 Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] expose les deux opérations entrantes suivantes :  
  
-   **L’interrogation**: l’instruction d’interrogation et l’instruction après interrogation (si spécifié) sont exécutées dans une transaction, tandis que l’instruction disponibles des données interrogées est exécutée dans une autre transaction. De même, l’instruction d’interrogation et l’instruction après interrogation sont exécutés à l’aide de la même connexion ODP.NET, tandis que les données interrogées disponibles instruction à l’aide d’une autre connexion ODP.NET.  
  
-   **Notification**: l’opération de notification est effectuée dans une transaction à l’aide d’une seule connexion ODP.NET.  
  
 Pour plus d’informations sur les opérations entrantes exposés par le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], consultez [en quoi les métadonnées de l’adaptateur Surface Oracle E-Business Suite ?](https://msdn.microsoft.com/library/dd788431.aspx).  
  
## <a name="see-also"></a>Voir aussi  
[Présentation de l’adaptateur BizTalk pour Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/understand-biztalk-adapter-for-oracle-e-business-suite.md)