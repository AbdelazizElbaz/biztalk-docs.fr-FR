---
title: "Rapport d’agrégation du document informatisé | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a6e1417e-e0c6-4d30-aab5-d9bfe14cd4b8
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 960fe64eb61504cb07b71be3e1870007b46c5fa9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="transaction-set-aggregation-report"></a>Rapport d'agrégation du document informatisé
Ce rapport fournit un enregistrement unique qui indique le nombre de documents informatisés EDI partageant les mêmes ID de document informatisé, type de codage EDI, tiers expéditeur, tiers récepteur et direction. Il ne fournit aucune information sur les documents informatisés individuels.  
  
 Pour afficher ce rapport d'état, cliquez sur le lien Rapport d'agrégation du document informatisé au bas de la page Hub du groupe dans la console Administration de BizTalk Server.  
  
## <a name="fields-in-the-status-report"></a>Champs du rapport État  
 Le Rapport d'agrégation du document informatisé affiche les informations suivantes pour les échanges reçus ou envoyés :  
  
-   nombre de documents informatisés partageant les mêmes ID de document informatisé, type de codage EDI, tiers expéditeur, tiers récepteur et direction ;  
  
-   le tiers expéditeur pour chaque transaction définie dans l'enregistrement ;  
  
-   le tiers récepteur pour chaque transaction définie dans l'enregistrement ;  
  
-   la direction (réception ou envoi) de chaque document informatisé dans l'enregistrement ;  
  
-   date et heure auxquelles le document informatisé le plus ancien dans la plage horaire a été envoyé ou reçu (Date/heure du début le plus ancien) ;  
  
    > [!NOTE]
    >  Pour les documents reçus, si la date spécifiée dans l'échange est au format AAMMJJ et que AA est supérieur ou égal à 75, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] affiche l'année sous la forme 19AA. Si la date est antérieure à 75, l'année est affichée sous la forme 20AA.  
    >   
    >  Par exemple, si vous recevez un échange contenant la valeur 991113 dans ISA09, la date/heure du début le plus ancien est affichée dans le rapport sous la forme 13/11/1999.  
  
-   date et heure auxquelles le document informatisé le plus récent dans la plage horaire a été envoyé ou reçu (Date/heure de la fin la plus récente).  
  
## <a name="fields-in-the-query-expression-for-the-status-report"></a>Champs de l'expression de requête du rapport d'état  
 Vous pouvez personnaliser le rapport d'agrégation de l'échange en modifiant les champs de l'expression de requête qui détermine les données affichées. Les champs suivants sont disponibles :  
  
|||||  
|-|-|-|-|  
|Champ de l'expression de requête|Opérateurs potentiels|Valeurs potentielles|Inclus par défaut ?|  
|Rechercher|Égal à|Rapport d'agrégation du document informatisé|Oui (requis)|  
|date/heure de l'échange ;|Inférieur ou égal à<br /><br /> Supérieur ou égal à|Date/heure spécifique<br /><br /> aujourd'hui<br /><br /> Aujourd'hui - 1|Oui<br /><br /> Remarque : Peut être inclus deux fois dans l’expression de requête, une fois avec un inférieur-que l’opérateur et une autre fois avec un-à (opérateur), pour indiquer une plage|  
|Résultats (nb maximal)|Égal à|Entier (valeur par défaut 50)|Oui|  
|Sens|Égal à|Tous (par défaut)<br /><br /> Recevoir<br /><br /> Send|Non|  
|Nom du tiers récepteur|Égal à|Tous (par défaut)<br /><br /> Nom de tiers spécifique (chaîne AN)|Non|  
|Nom du tiers expéditeur|Égal à|Tous (par défaut)<br /><br /> Nom de tiers spécifique (chaîne AN)|Non|  
|État|Égal à<br /><br /> Différent de|Accepté<br /><br /> Accepté avec erreurs<br /><br /> Envoyé<br /><br /> Tous<br /><br /> Accusé de réception attendu<br /><br /> Accusé de réception non attendu<br /><br /> Rejeté|Non|  
|ID du jeu de transactions|Égal à|Tous (par défaut)<br /><br /> ID de document informatisé spécifique|Non|  
  
