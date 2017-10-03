---
title: Consolider les Databases2 de BizTalk Server | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d7fc4fe6-3fc2-4164-9f16-90b6f473ba8c
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 56a8f594298569caaa4842a5f754ba991e9e5f51
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="consolidate-the-biztalk-server-databases2"></a>Consolidation des bases de données BizTalk Server2
Une installation de Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] peut nécessiter la création de 13 bases de données distinctes maximum dans Microsoft [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)], qui seront utilisées comme banques de données pour les différentes fonctionnalités de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. En raison de la charge de travail que constituent la gestion et la maintenance de ces bases de données, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] permet de consolider plusieurs d'entre elles dans une base de données unique. Cette section décrit comment réaliser la consolidation des bases de données [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et présente les observations relatives à l’implémentation de la consolidation des bases de données [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
> [!NOTE]
>  Pour obtenir la liste complète de toutes les bases de données requises lors de l’installation de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], consultez [Bases de données dans BizTalk Server](../core/databases-in-biztalk-server.md).  
  
## <a name="implementing-biztalk-database-consolidation"></a>Implémentation de la consolidation des bases de données BizTalk  
 La consolidation des bases de données [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est effectuée après l'installation de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], au cours de la configuration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Pour implémenter la consolidation des bases de données [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], procédez comme suit :  
  
1.  Cliquez sur **Démarrer**, pointez sur **Tous les programmes** et sur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], puis cliquez sur **Configuration de BizTalk Server**. Si vous êtes invité à sélectionner un type de configuration, cliquez sur **Configuration personnalisée**.  
  
2.  Entrez les mêmes **nom de serveur** et **nom de base de données** [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] (par exemple, *BizTalkConsolidatedDb*) pour plusieurs des banques de données suivantes :  
  
    |Nom de la fonctionnalité|Nom de la banque de données|  
    |------------------|---------------------|  
    |Microsoft Enterprise Single Sign-On|Base de données SSO|  
    |Groupe|Base de données de gestion BizTalk|  
    |Groupe|Base de données MessageBox BizTalk|  
    |Groupe|Base de données de suivi BizTalk|  
    |Business Rules Engine|Base de données du moteur de règles|  
  
     Notez que les banques de données suivantes ne doivent **pas** être configurées pour partager une base de données [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] :  
  
    |Nom de la fonctionnalité|Nom de la banque de données|  
    |------------------|---------------------|  
    |Outils BAM|Base de données d’importation principale BAM|  
    |Outils BAM|Base de données des archives BAM|  
  
3.  Définissez les options de configuration restantes, puis appliquez la configuration. L’outil de configuration va créer des tables dans la base de données [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] partagée pour les banques de données pour lesquelles vous avez spécifié les mêmes **nom de serveur** et **nom de base de données** [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)].  
  
## <a name="considerations-for-implementing-biztalk-database-consolidation"></a>Considérations relatives à l'implémentation d'une consolidation des bases de données BizTalk  
 Lors de la consolidation d'une base de données BizTalk, prenez en compte les éléments suivants :  
  
1.  La consolidation réduit la surcharge découlant de la gestion et de la maintenance des bases de données [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. C'est pourquoi elle doit uniquement être implémentée dans un environnement approprié. Avant l'implémentation de la consolidation des bases de données [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dans un environnement de production, les effets sur les performances soutenues de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] doivent être calculés dans un environnement intermédiaire. Envisagez d'implémenter la consolidation des bases de données [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour simplifier leur administration et leur maintenance dans les scénarios suivants :  
  
    -   Environnements de production [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] à échelle réduite, peu volumineux, où les performances des bases de données ne risquent pas de provoquer un goulot d'étranglement.  
  
    -   Environnements de production [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] d'échelle et de volume moyens, si la base de données des suivis BizTalk n'est pas incluse dans la consolidation, et est créée sur un disque physique distinct de celui de la base de données consolidée.  
  
    -   Environnements de production [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] à grande échelle, très volumineux, si la base de données [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] partagée est située physiquement sur un périphérique réseau SAN (Storage Area Network) à très hautes performances, où la probabilité que les performances des bases de données génèrent un goulot d'étranglement est très faible.  
  
    -   Environnements de test de validation ou de développement où les performances des bases de données sont un problème secondaire.  
  
2.  Les performances globales de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dépendent généralement des performances des bases de données [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. C'est pourquoi, la consolidation des bases de données ne doit pas être implémentée dans un environnement de production [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] très volumineux. La seule exception à cet état de fait se produit lorsque les bases de données [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sont situées sur un périphérique réseau SAN à très hautes performances, où la probabilité que les performances des bases de données génèrent un goulot d'étranglement est très faible. Si tel n'est pas le cas, les bases de données distribuées offrent de meilleures performances que les bases de données consolidées, notamment sous charge.  
  
3.  Si la base de données de gestion [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est incluse dans la consolidation des bases de données et que la base de données de consolidation n’est pas nommée **BizTalkMgmtDb**, la console Administration de BizTalk doit être configurée pour pointer sur la base de données de consolidation. Procédez de la manière décrite dans la rubrique [Connexion à un groupe existant](../core/how-to-connect-to-an-existing-group.md) et configurez la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour pointer sur la base de données de consolidation afin de gérer le groupe [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
4.  Pour plus d’informations sur les performances soutenues de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], consultez la rubrique [Planification en vue de performances soutenues](../core/planning-for-sustained-performance.md).  
  
 Pour plus d’informations sur les activités associées à la maintenance des bases de données [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], consultez la rubrique [Maintenance de BizTalk Server1](../core/maintaining-biztalk-server1.md).