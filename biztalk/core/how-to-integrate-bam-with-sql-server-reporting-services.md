---
title: "L’intégration BAM avec SQL Server Reporting Services | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6e2d66b7-c8eb-4871-8a47-544955ccd51e
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8a55d0fa09267cc23d54533427da326e5028d3f0
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-integrate-bam-with-sql-server-reporting-services"></a>Intégration de l'analyse BAM avec SQL Server Reporting Services
La création d'un rapport basé sur les données de l'infrastructure BAM fait appel aux même tâches que la création d'un rapport pour n'importe quelle autre source de données SQL Server. Pour plus d’informations sur la création d’un rapport avec le Concepteur de rapports, consultez [http://go.microsoft.com/fwlink/?LinkId=82437](http://go.microsoft.com/fwlink/?LinkId=82437).  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez détenir les autorisations d'accès aux données nécessaires pour créer le rapport.  
  
### <a name="how-to-create-a-report-in-bam-by-using-sql-server-reporting-service"></a>Création d'un rapport dans BAM à l'aide de SQL Server Reporting Services  
  
1.  Sélectionnez la source de données à partir de laquelle créer le rapport.  
  
     BAM propose deux sources de données vers lesquelles pointe Reporting Services.  
  
    |Source de données| Description|  
    |-----------------|-----------------|  
    |Base de données d'importation principale BAM|Contient les vues sur les instances d'activité et les agrégations en temps réel. Sélectionnez Type = « Microsoft SQL Server » et la chaîne de connexion = « Source de données =\<*nom du serveur*\>; Catalogue initial =\<*nom de la base de données*\>», où \< *nom du serveur* \> et \< *base de données nom* \> sont les noms de serveur et de base de données de votre base de données d’importation principale Bam.|  
    |Base de données d'analyse BAM|Contient les données utilisées pour interroger le cube d'analyse. Sélectionnez Type = « Microsoft SQL Server Analysis Server » et la chaîne de connexion = « Source de données =\<*nom du serveur*\>; Catalogue initial =\<*nom de la base de données*\>», où \< *nom du serveur* \> et \< *base de données nom* \> sont les noms de serveur et de base de données de votre base de données analyse BAM.|  
  
2.  Concevez la requête. Pour la base de données d'importation principale BAM, il existe deux types de vues :  
  
    |Nom de la vue| Description|  
    |---------------|-----------------|  
    |dbo.bam_\<*nom de la vue*\>_\<*nom de l’activité*\>View_View.|Cette vue contient les données d'instance.|  
    |dbo.bam_\<*nom de la vue*\>_\<*nom de table de tableau croisé dynamique d’agrégation en temps réel*\>_RTAView|Cette vue contient les données utilisées dans les agrégations en temps réel.|  
  
    > [!NOTE]
    >  Vous pouvez taper **sélectionnez \* à partir de la vue** pour retourner le résultat souhaité. Pour la base de données analyse BAM, cliquez sur le Générateur de requêtes et faites glisser les dimensions et mesures du cube nommé \< *nom de la vue* \> pour retourner le résultat souhaité.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Exécutez les étapes décrites dans l'Assistant Rapport afin de spécifier les données à présenter et la manière dont elles doivent être présentées.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des bases de données BAM](../core/managing-bam-databases.md)