---
title: "Recherches d’activité dans le portail BAM | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- activities [BAM], searching
- queries [BAM], field descriptions
- Query Builder [BAM portal], creating queries
- queries [BAM], activity searches
- Query Builder [BAM portal], about Query Builder
- Query Builder [BAM portal], activity searches
- Query Builder [BAM portal]
- Query Builder [BAM portal], field descriptions
- BAM portal, Query Builder
- BAM portal, activity searches
ms.assetid: 60ab8deb-ebe2-4959-97fd-261ff64d500c
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 617461b104f3188c14bb7c5b6eb5eb0bd329693f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="activity-searches-in-the-bam-portal"></a>Recherches d'activités dans le portail BAM
Une recherche d'activité vous permet de lancer des recherches sur des données BAM pour extraire les activités répondant aux critères spécifiés, sur la base des valeurs et des éléments suivis disponibles dans une vue BAM, ou pour afficher des activités à modifier ou créer des alertes relatives à ces activités.  
  
## <a name="parts-of-the-query-builder"></a>Composants du Générateur de requête  
 Pour générer des requêtes dans le cadre de votre recherche d'activité, vous devez sélectionner des éléments de données d'entreprise contre lesquels vous créez des comparaisons booléennes pour extraire des données d'intérêt. Vous commencez par sélectionner une vue BAM à partir de la **Mes vues** frame du portail. A partir de la vue sélectionnée, vous choisissez l'activité sur laquelle vous voulez générer la requête.  
  
 ![](../core/media/bamportalviewschooser.gif "BAMPortalViewsChooser")  
  
 Une fois l'activité sélectionnée, le frame de contenu du portail affiche les zones Générateur de requête, Sélecteur de colonne et Résultats. Vous pouvez ouvrir une requête existante ou en créer une nouvelle.  
  
 ![](../core/media/activitysearchquerybuilder.gif "ActivitySearchQueryBuilder")  
  
 Pour créer une nouvelle requête, vous commencez par sélectionner un élément de données d’entreprise à partir de la **données d’entreprise** liste déroulante.  
  
 ![](../core/media/activitysearchquerybuilderbusinessdatadropdown.gif "ActivitySearchQueryBuilderBusinessDataDropdown")  
  
 Vous sélectionnez ensuite un opérateur de comparaison dans la liste déroulante Opérateur. Cet opérateur vous permet d'affiner les résultats de la requête.  
  
 ![](../core/media/activitysearchcomparisonoperatordropdown.gif "ActivitySearchComparisonOperatorDropDown")  
  
 La liste déroulante Valeur dépend du type de données représentées par l'élément de données d'entreprise. L'interface utilisateur change en fonction du type de données autorisées.  
  
 Vous pouvez joindre des clauses de la requête avec et ou opérateurs OR pour former des requêtes plus complexes en cliquant sur le **ajouter** bouton.  
  
 ![](../core/media/activitysearchjoiningclauses.gif "ActivitySearchJoiningClauses")  
  
> [!NOTE]
>  Vous ne pouvez pas regrouper des clauses. Une requête est une simple chaîne de clauses individuelles jointes par les opérateurs AND et OR.  
  
 Le tableau suivant décrit les champs de date et d'heure.  
  
|Opérateur| Description|  
|--------------|-----------------|  
|**AT**|Indique une correspondance exacte. Équivaut à une opération booléenne de type Égal (=). **Remarque :** si vous sélectionnez le **à** opérateur et spécifiez une date sans la partie heure, le portail utilise minuit comme valeur par défaut. Si ce n’est pas votre intention, utilisez le **à ou avant** ou **à ou après** opérateurs pour obtenir les résultats souhaités.|  
|**L’ou avant**|Indique que seules les transactions ayant lieu à la date spécifiée ou avant sont mises en correspondance. Équivaut à une opération booléenne de type Inférieur ou égal à (=).|  
|**Sur ou après**|Indique que seules les transactions ayant lieu à la date spécifiée ou après sont mises en correspondance. Équivaut à une opération booléenne de type Supérieur ou égal à (=).|  
|**Avant**|Indique que seules les transactions ayant lieu avant la date spécifiée sont mises en correspondance. Équivalent à une valeur booléenne inférieur à (\<) opération.|  
|**After**|Indique que seules les transactions ayant lieu après la date spécifiée sont mises en correspondance. Équivalent à une opération booléenne de supérieure à (>).|  
|**Dans le dernier**|Indique que seules les transactions qui ont eu lieu au cours de la dernière période spécifiée sont mises en correspondances. Cette période peut être indiquée en secondes, minutes, heures ou jours.|  
|**Avant le dernier**|Indique que seules les transactions qui ont eu lieu avant la période spécifiée sont mises en correspondances. Cette période peut être indiquée en secondes, minutes, heures ou jours.|  
|**Est vide**|Indique que seules les transactions pour lesquelles l'élément de données d'entreprise ne contient aucunes données (valeur du champ de données définie sur NULL) sont retournées.|  
|**N’est pas vide**|Indique que seules les transactions pour lesquelles l'élément de données d'entreprise contient des données (valeur du champ de données non définie sur NULL) sont retournées.|  
  
 Le tableau suivant décrit les champs numériques et de durée. Les champs numériques contiennent des données telles que des quantités ou des montants en devises. Les champs de durée indiquent des périodes.  
  
|Opérateur| Description|  
|--------------|-----------------|  
|**Égal à**|Indique une correspondance exacte. Équivaut à une opération booléenne de type Égal (=).|  
|**Supérieur à**|Indique une correspondance exacte. Équivaut à une opération booléenne de type Supérieur à (>).|  
|**Supérieur ou égal à**|Indique une correspondance exacte. Équivaut à une opération booléenne supérieur ou égal à (≥).|  
|**Inférieur à**|Indique une correspondance exacte. Équivaut à une opération booléenne inférieure à (<).|  
|**Inférieur ou égal à**|Indique une correspondance exacte. Équivalent à un inférieur à ou égal à (<) opération.|  
|**Non égal**|Indique une correspondance exacte. Équivaut à une opération Différent de (?).|  
|**Est vide**|Indique que seules les transactions pour lesquelles l'élément de données d'entreprise ne contient aucunes données (valeur du champ de données définie sur NULL) sont retournées.|  
|**N’est pas vide**|Indique que seules les transactions pour lesquelles l'élément de données d'entreprise contient des données (valeur du champ de données non définie sur NULL) sont retournées.|  
  
 Le tableau suivant décrit les champs de texte.  
  
|Opérateur| Description|  
|--------------|-----------------|  
|**Correspond exactement à**|Indique une correspondance exacte. Équivaut à une opération booléenne de type Égal (=).|  
|**Contient**|Indique que le texte de l'élément de données d'entreprise contient la valeur spécifiée. Cela vous permet d'effectuer des correspondances partielles sur les données.|  
|**Ne contient pas**|Indique que le texte de l'élément de données d'entreprise ne contient pas la valeur spécifiée.|  
|**Est vide**|Indique que seules les transactions pour lesquelles l'élément de données d'entreprise ne contient aucunes données (valeur du champ de données définie sur NULL) sont retournées.|  
|**N’est pas vide**|Indique que seules les transactions pour lesquelles l'élément de données d'entreprise contient des données (valeur du champ de données non définie sur NULL) sont retournées.|  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Comment créer une requête de recherche d’activité](../core/how-to-create-a-query-in-activity-search.md)  
  
-   [Comment définir une alerte](../core/how-to-set-an-alert.md)  
  
-   [Comment afficher les résultats d’une recherche d’activité](../core/how-to-view-the-results-of-an-activity-search.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Portail BAM](../core/bam-portal.md)