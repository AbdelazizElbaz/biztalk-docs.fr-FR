---
title: "Données de suivi décoder des compteurs de Performance Services | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 733450b1-71b5-48a4-9ac3-cd880324440c
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 99ec03138e455c671e9ccb69aa8bc4c5588d287c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="tracking-data-decode-services-performance-counters"></a>Compteurs de performance du service de décodage des données de suivi
Les compteurs de performance permettent d'analyser des aspects spécifiques du travail effectué sur le site ou le système par un service. Ils peuvent vous aider à identifier et à résoudre des problèmes de performances de serveur.  
  
 Les compteurs de performances suivants sont accessibles pour chaque instance d’hôte sous le **TDDS** catégorie d’objet de performances :  
  
|**Catégorie**|**Compteur**|**Description**|  
|------------------|-----------------|---------------------|  
|BizTalk:TDDS|Lots traités|Nombre de lots en cours de traitement dans la transaction SQL actuelle.|  
||Lots validés|Nombre de lots validés dans la base de données de destination.|  
||Événements traités|Nombre d'événements en cours de traitement dans la transaction SQL actuelle.|  
||Événements validés|Nombre d'événements validés dans la base de données de destination durant la seconde écoulée.|  
||Enregistrements traités|Nombre d'enregistrements en cours de traitement dans la transaction SQL actuelle.|  
||Enregistrements validés|Nombre d'enregistrements validés dans la base de données de destination durant la seconde écoulée.|  
||Nombre total de lots|Nombre total de lots traités par le service TDDS.|  
||Nombre total d'événements|Nombre total d'événements traités par le service TDDS.|  
||Nombre total échec de lots|Nombre total de lots que le service TDDS n'a pas pu exécuter.|  
||Nombre total échec d'événements|Nombre total d'événements que le service TDDS n'a pas pu exécuter.|  
||Nombre total d'enregistrements|Nombre total d'enregistrements traités par le service TDDS.|  
  
## <a name="to-access-performance-counters"></a>Pour accéder aux compteurs de performance  
 Utilisez la procédure suivante pour accéder aux compteurs de performances.  
  
#### <a name="if-you-are-using-windows-2008"></a>Si vous exécutez Windows 2008  
  
1.  Cliquez sur **Démarrer**, pointez sur **outils d’administration**, puis cliquez sur **l’Analyseur de performances**.  
  
2.  Dans le **l’Analyseur de performances** boîte de dialogue, développez **outils d’analyse**, sélectionnez **l’Analyseur de performances**, puis cliquez sur **ajouter**.  
  
3.  Dans le **ajouter des compteurs** boîte de dialogue, à partir de la **compteurs disponibles** liste, développez le **TDDS** objet compteur de performance et sélectionnez les compteurs à surveiller  
  
4.  Dans le **Instances de l’objet sélectionné** , sélectionnez les instances spécifiques à surveiller pour les compteurs sélectionnés, puis cliquez sur **ajouter**.  Pour sélectionner toutes les instances de compteur disponibles, sélectionnez \< **toutes les instances**>.  
  
5.  Après avoir ajouté les compteurs, cliquez sur **OK**.  
  
     Les compteurs de performances sélectionnés s’affichent sur le **l’Analyseur de performances** écran.  
  
## <a name="see-also"></a>Voir aussi  
 [Trucs et astuces](../core/performance-tips-and-tricks.md)   
 [Mesurer le débit de moteur maximal acceptable](../core/measuring-maximum-sustainable-engine-throughput.md)   
 [Mesurer le débit de suivi maximal acceptable](../core/measuring-maximum-sustainable-tracking-throughput.md)   
 [Optimisation de l’utilisation des ressources via la limitation de l’hôte](../core/optimizing-resource-usage-through-host-throttling.md)