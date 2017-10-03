---
title: "Limitations de l’Infrastructure BAM | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BAM, limitations
- infrastructure, BAM
- BAM, objects
- BAM, infrastructure
- BAM, naming conventions
ms.assetid: e33d2f6c-8d26-4a76-810e-85d810cfdbee
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bfb8751e42918a64f13d35685d7d73b4f2406ff8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="bam-infrastructure-limitations"></a>Limitations de l'infrastructure BAM
L'infrastructure BAM comporte les limitations de conception suivantes pour cette version de [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] :  
  
-   Les agrégations RTA ne prennent en charge ni la fonction MIN ni la fonction MAX.  
  
-   Dans une même vue RTA, il est impossible de référencer un alias à niveau unique à l'aide de plus d'une dimension de données.  
  
-   Ni le cube régulier ni les agrégations RTA ne prennent en charge les mesures de compte distinct. L'utilitaire de gestion de l'analyse BAM crée une même mesure de compte par défaut pour le cube régulier et les agrégations RTA. Le compte par défaut correspond au compte total des faits (également appelés « instances d'activité ») et non pas au compte distinct.  
  
-   Ne définissez pas plusieurs RTA utilisant une même activité BAM. Si vous le faites, les données RTA seront incorrectes lors de l'archivage des données BAM.  
  
## <a name="bam-maximum-number-of-objects"></a>Nombre maximum d'objets dans l'analyse BAM  
 Le tableau suivant répertorie le nombre maximum des objets pouvant figurer dans l'infrastructure BAM.  
  
|Objet|Limite d'implémentation|Reason|  
|------------|--------------------------|------------|  
|Points de contrôle dans l'activité|1,000|SQL Server prend en charge 1 024 arguments de procédure stockée et BizTalk Server utilise 3 procédures système.|  
|Index dans l'activité|245|SQL Server prend en charge 245 index non cluster par table. BizTalk Server crée toujours un index sur ActivityID.|  
|DataLength|4000 caractères Unicode|Des variables SQL de type NVARCHAR sont utilisées.|  
|ActivityRef|128|Vous pouvez obtenir la vue en joignant la base de données d'importation principale à des tables Relation (deux par activité). SQL Server prend en charge 256 tables dans l'instruction SELECT.|  
|Colonnes de la vue<br /><br /> (alias, durées et niveaux de dimension)|150|SQL Server limite la table intermédiaire à 1024 colonnes, dont 24 colonnes système réservées par l'analyse BAM.|  
|Dimensions dans le cube OLAP|128|Limitation OLAP - 128 dimensions par cube|  
|Mesures dans OLAP|1,024|Limitation OLAP - 1024 mesures par cube. La mesure de compte est toujours créée.|  
|Niveaux de dimension dans OLAP|64|Limitation OLAP avec une limite supplémentaire de 256 niveaux par cube.|  
|Niveaux de dimension dans la vue RTA|14 niveaux de dimension|L'analyse BAM crée un index à tous les niveaux de dimension ; un index SQL Server peut être créé sur 16 colonnes maximum et l'analyse BAM en réserve deux pour les colonnes système.|  
|Mesures, mesures masquées (compte par défaut, mesures SUM masquées pour AVG) et niveaux de dimension dans la vue RTA.|1,024|1024 colonnes maximum dans la table/vue SQL.|  
|ActivityViews|63|Lorsque vous configurez une alerte, vous êtes limité à 63 ActivityViews dans [!INCLUDE[btsSQLServer2005](../includes/btssqlserver2005-md.md)].|  
  
## <a name="bam-object-names"></a>Noms d'objets de l'analyse BAM  
 Le tableau suivant répertorie les limitations qui s'appliquent aux noms d'objets dans le schéma de définition BAM et la feuille de calcul Microsoft Excel.  
  
|Noms d'objets|Limitation XSD|Limitation Excel|  
|------------------|--------------------|----------------------|  
|Nom de point de contrôle|50 caractères|50 caractères|  
|Nom de l'index|100 caractères|100 caractères|  
|Nom de la durée|100 caractères|100 caractères|  
|Nom d’alias|50 caractères|50 caractères|  
|Nom de l'activité|48 caractères|20 caractères|  
|Nom de la vue|18 caractères|18 caractères|  
|Nom ActivityView|52 caractères (Le nom est composé du préfixe « View » et du nom de la vue en 48 caractères.)|Non applicable (dérivé du nom d'activité)|  
|Nom de cube|20 caractères|Non applicable (dérivé du nom de vue)|  
|Nom RealTimeAggregation|48 caractères|Non applicable (dérivé du nom de cube)|  
|Nom de la dimension|20 caractères|20 caractères|  
|Nom de niveau|20 caractères|20 caractères|  
|Nom de la mesure|20 caractères|20 caractères|  
|Nom de l’alerte|128 caractères|Néant|  
|Message d’alerte|1024 caractères|Néant|  
|Nom de la règle d'événement|255 caractères|Néant|  
|Nom du fournisseur d'événements|255 caractères|Néant|  
  
## <a name="see-also"></a>Voir aussi  
 [Schéma de Configuration BAM](../core/bam-configuration-schema.md)   
 [Infrastructure dynamique BAM](../core/bam-dynamic-infrastructure.md)