---
title: "Compteurs de performances de l’adaptateur HTTP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d85473f1-1d67-4990-8d2f-fc7fe0e80108
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ff9fcc2530484abd7c5bdbf1997e3d294afdb3dc
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="http-adapter-performance-counters"></a>Compteurs de performances de l'adaptateur HTTP
Les compteurs de performance permettent d'analyser des aspects spécifiques du travail effectué sur le site ou le système par un service. Ils peuvent vous aider à identifier et à résoudre des problèmes de performances de serveur.  
  
 Les compteurs de performances suivants sont accessibles pour chaque instance d’hôte sous le **BizTalk : adaptateur de réception HTTP** et **: adaptateur d’envoi HTTP** catégories d’objet de performance :  
  
|**Catégorie**|**Compteur**|**Description**|  
|------------------|-----------------|---------------------|  
|BizTalk:adaptateur de réception HTTP|Taille de file d'attente mémoire|Nombre de messages entrants dans la file d'attente mémoire interne de l'adaptateur de réception HTTP.|  
||Messages reçus|Nombre total de requêtes HTTP reçues par l'adaptateur de réception HTTP. Le compteur est incrémenté après qu'un message de requête a été lu dans son intégralité par l'adaptateur de réception HTTP dans le client HTTP.|  
||Messages reçus/s|Nombre de requêtes HTTP reçues par l'adaptateur de réception HTTP par seconde. Le compteur prend uniquement en compte les messages de requête lus dans leur intégralité par l'adaptateur de réception HTTP dans le client HTTP.|  
||Messages envoyés|Nombre total de réponses HTTP envoyées par l'adaptateur de réception HTTP. Le compteur est incrémenté uniquement lorsque les messages de réponse ont été envoyés avec succès vers les clients HTTP.|  
||Messages envoyés/s|Nombre de réponses HTTP envoyées par l'adaptateur de réception HTTP par seconde. Le compteur tient compte uniquement des messages de réponse envoyés avec succès aux clients HTTP.|  
||Durée d'ajout de message au lot|Durée moyenne entre la remise d'un message par IIS à l'adaptateur de réception HTTP et son ajout à un lot.|  
||Durée de construction de lot|Temps moyen nécessaire à l'adaptateur de réception HTTP pour créer un lot de messages.|  
|BizTalk:adaptateur d'envoi HTTP|Taille de file d'attente mémoire|Nombre de messages sortants dans la file d'attente mémoire interne de l'adaptateur d'envoi HTTP.|  
||Messages reçus|Nombre total de messages de réponse HTTP reçus par l'adaptateur d'envoi HTTP. Le compteur est incrémenté après qu'un message de réponse a été lu dans son intégralité par l'adaptateur d'envoi HTTP sur les serveurs HTTP.|  
||Messages reçus/s|Nombre de réponses HTTP reçues par l'adaptateur d'envoi HTTP par seconde. Le compteur prend uniquement en compte les messages de réponse lus dans leur intégralité par l'adaptateur d'envoi HTTP sur les serveurs HTTP.|  
||Messages envoyés|Nombre total de requêtes HTTP envoyées par l'adaptateur d'envoi HTTP. Le compteur est incrémenté uniquement pour les messages de requête ayant atteint l'URL de destination.|  
||Messages envoyés/s|Nombre de requêtes HTTP envoyées par l'adaptateur d'envoi HTTP par seconde. Le compteur prend uniquement en compte les messages de requête ayant atteint l'URL de destination.|  
  
## <a name="to-access-performance-counters"></a>Pour accéder aux compteurs de performance  
 Utilisez la procédure suivante pour accéder aux compteurs de performances.  
  
#### <a name="if-you-are-using-windows-2008"></a>Si vous exécutez Windows 2008  
  
1.  Cliquez sur **Démarrer**, pointez sur **outils d’administration**, puis cliquez sur **l’Analyseur de performances**.  
  
2.  Dans le **l’Analyseur de performances** boîte de dialogue, développez **outils d’analyse**, sélectionnez **l’Analyseur de performances**, puis cliquez sur **ajouter**.  
  
3.  Dans le **ajouter des compteurs** boîte de dialogue, à partir de la **compteurs disponibles** liste, développez le **HTTP** objet compteur de performance et sélectionnez les compteurs à surveiller  
  
4.  Dans le **Instances de l’objet sélectionné** , sélectionnez les instances spécifiques à surveiller pour les compteurs sélectionnés, puis cliquez sur **ajouter**.  Pour sélectionner toutes les instances de compteur disponibles, sélectionnez \< **toutes les instances**\>.  
  
5.  Après avoir ajouté les compteurs, cliquez sur **OK**.  
  
     Les compteurs de performances sélectionnés s’affichent sur le **l’Analyseur de performances** écran.  
  
## <a name="see-also"></a>Voir aussi  
 [Analyse de BizTalk Server](../core/monitoring-biztalk-server.md)   
 [Paramètres de réglage et de Configuration de l’adaptateur HTTP](../core/http-adapter-configuration-and-tuning-parameters.md)   
 [Éléments à prendre en compte pour l’exécution des gestionnaires d’adaptateur au sein d’un hôte en cluster](../core/considerations-for-running-adapter-handlers-within-a-clustered-host1.md)