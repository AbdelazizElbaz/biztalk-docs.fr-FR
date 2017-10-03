---
title: "Rapport d’état du lot | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 04dad016-e7bb-45cd-b36a-a9c83d073501
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7c033f58432c8ae5a2d87b87b56223b8f64a7201
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="batch-status-report"></a>Rapport État du lot
Ce rapport affiche l'activité des instances de l'orchestration de traitement par lot. Chaque ligne du rapport indique l'état des lots en cours de traitement par une instance de l'orchestration de traitement par lot.  
  
 L'état des lots conservés n'est pas signalé dans le rapport État du lot, mais dans le rapport État de l'échange/de l'accusé de réception.  
  
## <a name="fields-in-the-status-report"></a>Champs du rapport État  
 Le rapport État du lot affiche les informations suivantes pour les échanges reçus par lot :  
  
-   état du lot ;  
  
-   Nom du lot  
  
-   nom du tiers de destination ;  
  
-   heure de l'activation ;  
  
-   nombre d'occurrences dans le lot ;  
  
-   type de codage EDI ;  
  
-   type de lot ;  
  
-   cible du lot ;  
  
-   Nombre d’éléments de lot : le nombre d’éléments par lots ont été accumulé par l’instance d’orchestration de traitement par lot  
  
-   nombre d'éléments rejetés ;  
  
-   Action la plus récente : Peut être lot activé, déclenchement planifié, déclenchement basé sur le nombre, déclenchement du remplacement manuel, lot terminé/arrêter version, élément ajouté ou déclenchement externe  
  
-   Numéro de contrôle d’échange  
  
-   date/heure de l'échange ;  
  
-   taille du lot (en nombre de caractères) (n'est pas affichée par défaut).  
  
## <a name="view-related-interchanges-status-reports"></a>Affichage des rapports État de l'échange associés  
 Si vous cliquez avec le bouton droit sur un échange ou un accusé de réception répertorié dans le rapport État du lot, vous pouvez afficher les détails des échanges associés au lot.  
  
## <a name="fields-in-the-query-expression-for-the-status-report"></a>Champs de l'expression de requête du rapport d'état  
 Vous pouvez personnaliser le rapport État du lot en modifiant les champs de l'expression de requête qui détermine les données affichées. Les champs suivants sont disponibles :  
  
|||||  
|-|-|-|-|  
|Champ de l'expression de requête|Opérateurs potentiels|Valeurs potentielles|Inclus par défaut ?|  
|Rechercher|Égal à|état du lot ;|Oui (requis)|  
|état du lot ;|Égal à<br /><br /> Différent de|Défini par : L’instance de lot est configurée mais heure de début est postérieur à l’heure de la date actuelle.<br /><br /> Actif (par défaut) : l’instance du lot est configurée et collecte des jeux de transactions pour un lot. L'heure de début est antérieure à l'heure actuelle.<br /><br /> Publié : Les critères de déclenchement ont été satisfaits et le lot a été envoyé, ou que l’orchestration de traitement par lots a été arrêtée avant que les messages soient traités.<br /><br /> Terminé : Les critères de déclenchement a été remplie, mais le lot n’a pas été envoyé.<br /><br /> All : Afficher n’importe quelle instance de lot dans un de ces États.|Oui|  
|Résultats (nb maximal)|Égal à|Entier (valeur par défaut 50)|Oui|  
|Date et heure d'activation|Inférieur ou égal à<br /><br /> Supérieur ou égal à|Date heure<br /><br /> aujourd'hui<br /><br /> Aujourd'hui - 5|Non<br /><br /> Remarque : peut être inclus plusieurs fois dans l'expression de requête.|  
|Nom du lot|Égal à|Tous (valeur par défaut)<br /><br /> Nom de lot spécifique|Non|  
|Tiers de destination|Égal à|Tous (par défaut)<br /><br /> Nom de tiers spécifique|Non|  
|Type de codage EDI|Égal à|X12<br /><br /> EDIFACT<br /><br /> Tous (par défaut)|Non|  
  
