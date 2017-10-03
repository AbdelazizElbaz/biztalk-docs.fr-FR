---
title: "Définition des mesures et des dimensions | Microsoft Docs"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e6b12a4c-9be5-4cac-b5b9-ece376d28cb1
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bdbbd270b5241d25e7ba227c2db886c112f3f4c4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="what-are-measures-and-dimensions"></a>Définition des mesures et des dimensions
Les dimensions et les mesures sont les aspects physiques de l'agrégation de données. Cette rubrique décrit les mesures et les dimensions à l'aide d'un scénario d'analyse BAM faisant office de contexte.  
  
## <a name="measures"></a>mesures  
 Supposons qu'une activité BAM soit définie pour un processus de gestion des commandes en termes extrêmement simples se composant de trois éléments :  
  
1.  heure de début du processus (événement du monde réel) ;  
  
2.  heure de fin du processus (également événement du monde réel) ;  
  
3.  durée du processus (deuxième élément - premier élément).  
  
 L'agrégation des données, dans ce cas, consiste simplement à appliquer une fonction d'agrégation (par exemple, moyenne, minimum, maximum, etc.) à une série de valeurs de durée individuelles (c'est-à-dire, la durée du traitement de chaque commande).  
  
 Le concept de « durée moyenne » est une mesure. Il s'agit en outre d'une valeur unique. Cette mesure seule génère des informations relatives à la gestion des processus, car elle indique si, globalement, le processus se comporte comme prévu (en termes d'opportunité ou de débit). Toutefois, en l'absence d'autres données (la « durée moyenne » étant une valeur unique), l'interprétation du sens de la valeur réelle de cette mesure est plus difficile. Par exemple, pourquoi la durée moyenne a-t-elle enregistré un pic au cours de la semaine ? Était-ce dû à un partenaire, à un programme ou à un produit particulier ?  
  
## <a name="dimensions"></a>Dimensions  
 Les dimensions constituent le contexte qui aide l'utilisateur des mesures à comprendre la signification de ces dernières.  
  
 À la suite de l'exemple ci-dessus, supposons que trois éléments supplémentaires sont ajoutés à l'activité BAM pour le processus de gestion des commandes :  
  
1.  nom du partenaire commercial (qui a envoyé la commande) ;  
  
2.  nom du gestionnaire de compte (qui est le contact commercial) ;  
  
3.  région de vente.  
  
 L'activité incluant maintenant trois tableaux croisés dynamiques de données possibles (partenaire, gestionnaire de compte, région), l'agrégation de ces données résulte littéralement en la création d'un cube tridimensionnel lors de l'exécution.  
  
 Elle commence toujours par la première tâche, résultant en la création d'une mesure de « durée moyenne » unique. Lorsque la prochaine tâche (lancée par l'arrivée d'un autre bon de commande) est exécutée, si le partenaire commercial, le gestionnaire de compte et la région sont inchangés par rapport à la première tâche, la mesure de « durée moyenne » est recalculée sur la base de deux tâches (par exemple, la moyenne des deux durées) pour produire une valeur de mesure de « durée moyenne » unique.  
  
 Si, dans une tâche, le partenaire commercial, le gestionnaire de compte ou la région sont différents des valeurs rencontrées jusqu'à présent, une nouvelle valeur de mesure de « durée moyenne » est créée et mise à jour séparément de la première.  
  
 Par exemple, si le partenaire commercial pour la troisième tâche est différent de celui des deux premières tâches, une seconde valeur de mesure de « durée moyenne » est créée avec la dimension de partenaire commercial. Il est maintenant possible de consulter les valeurs de « durée moyenne » avec la dimension de partenaire commercial et de constater, par exemple que « cela prend presque deux fois plus de temps en moyenne de traiter les commandes émanant du PartenaireCommercialX que du PartenaireCommercialY. » Les dimensions peuvent en outre être réduites de sorte qu'il reste possible de voir la « durée moyenne » globale pour le processus, indépendamment d'une dimension de partenaire commercial ou autre.  
  
 Enfin, si les dimensions de partenaire commercial, de gestionnaire de compte et de région sont dotées chacune de trois, et seulement de trois, valeurs distinctes, une fois les permutations effectuées, il en résulte un « Rubik® Cube » de données, où les utilisateurs peuvent afficher chacune des 27 valeurs de « durée moyenne » mises à jour de façon indépendante, les dimensions étant représentées par trois côtés du cube.  
  
 Pour plus d'informations sur les dimensions et les mesures, consultez la rubrique « À propos des données source OLAP dans les rapports de tableau ou de graphique croisé dynamique » de l'Aide d'Excel.