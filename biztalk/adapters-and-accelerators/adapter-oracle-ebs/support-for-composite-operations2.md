---
title: Prise en charge de Composite Operations2 | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3f65cf10-4e27-4872-bc6a-defe6cbab198
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5766adec70c1a1fe7eaabe4ffaf07499e33d210c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="support-for-composite-operations"></a>Prise en charge des opérations composites
Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] permet aux clients d’adaptateur effectuer des opérations composites qui peuvent inclure plusieurs des opérations suivantes et dans n’importe quel ordre :  
  
-   Sélectionnez, Insert, Update et les opérations Delete sur une table d’interface et une table de base de données.  
  
-   Sélectionner une opération sur une vue de l’interface et l’affichage de la base de données.  
  
-   Procédures stockées, fonctions et procédures dans des packages qui sont signalées en tant qu’opérations dans l’adaptateur.  
  
 Les opérations dans une opération composite peuvent cibler des tables et des vues dans la même base de données ou les bases de données différentes. Toutefois, les données ne peut pas être partagées ou réutilisées dans plusieurs opérations dans une opération composite. Par exemple, dans une opération composite, le jeu de résultats d’une opération de sélection ne peut pas être utilisé comme paramètre d’entrée pour une procédure stockée.  
  
 Chaque opération dans une opération composite est effectuée à l’aide d’une connexion distincte. Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] consomme autant de connexions à partir du pool de connexions ODP.NET en tant que le nombre d’opérations dans une opération composite et libère les connexions que les opérations sont exécutées. Toutefois, si une opération dans l’opération composite renvoie un jeu de résultats, la connexion est libérée uniquement après que le message est utilisé.  
  
> [!IMPORTANT]
>  Si vous rencontrez des problèmes de délai d’attente lors de l’exécution d’une opération composite ce peut être, car le nombre de connexions est inférieur au nombre d’opérations dans une opération composite impliquant :  
>   
>  -   Les procédures stockées contenant des BFILE, BLOB, CLOB, NCLOB et REF CURSOR comme OUT ou IN OUT.  
> -   Sélectionnez l’opération.  
>   
>  Pour résoudre ce problème, vous devez vous assurer que s’il existe le nombre de « n » de ces opérations dans une opération composite, la valeur spécifiée pour le **MinPoolSize** propriété de liaison est « n + 1 » ou supérieur. Pour plus d’informations sur la **MinPoolSize** liaison de propriété, consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison d’Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md).  
  
 Pour plus d’informations sur :  
  
-   Comment effectuer des opérations composites dans [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] à l’aide de [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], consultez [exécuter des opérations composites sur la base de données Oracle à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/run-composite-operations-on-oracle-database-using-biztalk-server.md).  
  
-   Schémas pour l’opération composite de messages, consultez [des schémas de Message pour l’opération Composite](../../adapters-and-accelerators/adapter-oracle-ebs/message-schemas-for-the-composite-operation1.md).  
  
> [!NOTE]
>  Vous pouvez également définir le contexte des applications pour des opérations composites dans le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]. Il est obligatoire de définir le contexte des applications pour les opérations composites si une des opérations dans une opération composite est exécutée sur une vue de table ou une interface d’interface. Pour plus d’informations sur le contexte des applications et comment le configurer, consultez [définir le contexte application](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Les opérations sont prises en charge par l’adaptateur Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/what-operations-are-supported-by-the-oracle-e-business-suite-adapter.md)