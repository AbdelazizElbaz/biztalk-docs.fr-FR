---
title: "Développer des applications SQL à l’aide du modèle de canal WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 11df5cc2-b532-45a8-9055-d05f4704a6e5
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7b503b0766a4848e05c9361fb151196ee43afd81
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="develop-sql-applications-using-the-wcf-channel-model"></a>Développer des applications SQL à l’aide du modèle de canal WCF
Vous pouvez utiliser la [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] modèle de canal pour consommer le [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] en envoyant des messages XML directement sur une instance de canal créée avec la liaison de SQL Server.  
  
 Un avantage de l’utilisation du modèle de canal WCF en utilisant les classes fortement typées et les méthodes que le modèle de service WCF expose est que le modèle de canal fournit un contrôle plus précis sur les opérations que vous effectuez sur la base de données SQL. Ce contrôle vient du fait que dans le modèle de canal WCF, vous contrôlez directement le contenu des messages que vous envoyez sur le canal.  
  
 Dans certains scénarios, ce niveau supplémentaire de contrôle peut être utile. Par exemple, lorsque vous utilisez le modèle de canal WCF pour effectuer une opération de mise à jour sur une table, vous pouvez sélectivement mettre à jour colonnes dans les lignes de la cible en omettant les colonnes à partir du modèle de mise à jour que vous passez dans le message. Seules les colonnes qui sont nécessaires sont celles avec « nillable = false » dans le WSDL. La méthode de mise à jour exposée par un [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] client utilise un paramètre d’enregistrement de fortement typé pour le modèle qui inclut toutes les colonnes dans le schéma de table.  
  
 Les sections de cette rubrique expliquent comment effectuer les opérations sur les [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] en utilisant le modèle de canal WCF.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Vue d’ensemble du modèle de canal WCF avec l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/overview-of-the-wcf-channel-model-with-the-sql-adapter.md)  
  
-   [Créer un canal à l’aide de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/create-a-channel-using-the-sql-adapter.md)  
  
-   [Exécuter une opération Insert sur une Table dans SQL à l’aide du modèle de canal WCF](../../adapters-and-accelerators/adapter-sql/run-an-insert-operation-on-a-table-in-sql-using-the-wcf-channel-model.md)  
  
-   [Recevoir des Messages d’interrogation de données modifiées à partir de SQL Server à l’aide du modèle de canal WCF](../../adapters-and-accelerators/adapter-sql/receive-polling-based-data-changed-messages-from-sql-server-using-a-wcf-channel.md)  
  
## <a name="see-also"></a>Voir aussi  
[Développer vos applications SQL](../../adapters-and-accelerators/adapter-sql/develop-your-sql-applications.md)