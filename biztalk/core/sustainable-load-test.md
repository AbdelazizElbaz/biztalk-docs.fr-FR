---
title: Test de charge maximale | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- sustainable load test
- LoadGen tool, sustainable load test
ms.assetid: a9d752ff-aff1-4445-8af5-8f84609880e2
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0a32f7ab31435cb81bee9e4ed52afc1f7d5194e8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="sustainable-load-test"></a>Test de charge maximale
Les informations contenues dans cette rubrique fait référence aux tests décrits dans [des scénarios de Test pour mesurer le débit maximal acceptable du moteur de](../core/test-scenarios-for-measuring-mst-of-the-engine.md).  
  
 Pour le premier test, le système a fonctionné à son débit maximal acceptable, de façon à effectuer des observations sur un système sain.  
  
 Le graphique suivant montre les indicateurs clés après l'utilisation de cette approche pour identifier le débit maximal acceptable du système de test.  
  
 **Profil de charge du test de charge maximale**  
  
 ![L’Analyseur de performances mesure charge maximale](../core/media/bts06-sustainable-load.gif "BTS06_Sustainable_Load")  
  
 Ce graphique montre que, pendant la durée du test, la profondeur du spouleur est restée stable et n'a pas augmenté :  
  
-   Les lignes noires en haut du graphique indiquent le nombre total de messages reçus par seconde par le système (pour les deux serveurs de réception, par exemple).  
  
-   Les lignes au bas du graphique indiquent la profondeur du spouleur MessageBox sur chaque serveur SQL Server.  
  
 Une fois que le système fonctionne à la profondeur de spouleur stable maximale, le débit maximal acceptable est déterminé par le nombre de messages reçus par seconde. Pour ce scénario et avec le matériel décrit, un débit maximal acceptable de 290 messages par seconde a été atteint.  
  
> [!NOTE]
>  Une fois que le système fonctionne à une profondeur de spouleur dont la stabilité ne peut plus être garantie, le débit maximal acceptable est dépassé. Plusieurs exécution du test avec des charges différentes peuvent être nécessaires pour évaluer la charge maximale à laquelle la profondeur du spouleur reste stable et à laquelle le système peut gérer les messages accumulés sans risque de saturation.  
  
 Toute analyse des performances d'un déploiement BizTalk doit passer par la vérification de certains indicateurs clés permettant d'anticiper les engorgements de ressources. Les mesures clés et les valeurs correspondantes suivantes ont été utilisées pour ce déploiement fonctionnant au débit maximal acceptables :  
  
 **Utilisation du processeur**  
  
|Server|Utilisation moyenne de l'UC|  
|------------|-----------------------------|  
|Serveurs BizTalk|55%|  
|Serveur SQL Server (serveur MessageBox maître)|76%|  
|Serveur SQL Server (autres serveurs MessageBox)|83%|  
  
 **Durée d’inactivité disque physique**  
  
|Server|Durée d'inactivité moyenne du disque|  
|------------|----------------------------|  
|Moyenne pour tous les serveurs SQL Server|69%|  
  
 **Verrous SQL sur SQL Server**  
  
|Paramètre|Valeur|  
|---------------|-----------|  
|Nombre total moyen de dépassements de délai de verrouillage par seconde (par serveur SQL Server)|1980|  
|Temps d'attente total moyen pour les verrouillages (ms)|495|  
  
 Au cours de ce test, aucune erreur n'a été consignée dans le journal de l'application BizTalk ou SQL Server.  
  
 Ces données permettent de tirer les conclusions suivantes :  
  
-   Notre système ne génère aucun engorgement de ressources évident.  
  
-   Tous ces indicateurs se situent dans les limites acceptables.  
  
-   L'utilisation de l'UC et les durées d'inactivité du disque montrent même que le système dispose encore d'une marge importante.  
  
-   Les indicateurs de verrouillage SQL bonnes **des délais d’attente de verrous/s** ne commence à devenir un problème jusqu'à ce qu’autour de 5000 ou (selon votre serveur SQL Server) et les temps inférieurs à 1 seconde d’attente de verrou sont également acceptables.  
  
 Maintenant que nous avons indiqué comment déterminer le débit maximal acceptable et identifié les indicateurs clés d'un système sain, étudions le comportement d'un système dont les capacités de traitement et de garbage collection sont dépassées. Passez à [dépassement de Test de charge](../core/overdrive-load-test.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Scénarios de test pour mesurer le débit maximal acceptable du moteur](../core/test-scenarios-for-measuring-mst-of-the-engine.md)   
 [Test de surcharge](../core/overdrive-load-test.md)