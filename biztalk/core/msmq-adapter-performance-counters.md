---
title: "Compteurs de performances de l’adaptateur MSMQ | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ab8b0342-c6c2-4113-ae54-359df28e5d30
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: be7580ae6551fca18ee0a3b9b14b194006efd62e
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="msmq-adapter-performance-counters"></a>Compteurs de performances de l'adaptateur MSMQ
Les compteurs de performance permettent d'analyser des aspects spécifiques du travail effectué sur le site ou le système par un service. Ils peuvent vous aider à identifier et à résoudre des problèmes de performances de serveur.  
  
 Les compteurs de performances suivants sont accessibles pour chaque instance d’hôte sous le **adaptateur de réception MSMQ** et **adaptateur d’envoi MSMQ** catégories d’objet de performances :  
  
|**Catégorie**|**Compteur**|**Description**|  
|------------------|-----------------|---------------------|  
|BizTalk:adaptateur de réception MSMQ|Octets reçus|Nombre total d'octets reçus par l'adaptateur de réception MSMQ. Le compteur est incrémenté après qu'un message est lu dans son intégralité par l'adaptateur de réception MSMQ dans la file d'attente source.|  
||Octets reçus/s|Nombre total d'octets reçus par l'adaptateur de réception MSMQ à chaque seconde. Le compteur prend uniquement en compte les messages lus dans leur intégralité par l'adaptateur de réception MSMQ dans la file d'attente source.|  
||Messages reçus|Nombre total de messages reçus par l'adaptateur de réception MSMQ. Le compteur est incrémenté après qu'un message est lu dans son intégralité par l'adaptateur de réception MSMQ dans la file d'attente source.|  
||Messages reçus/s|Nombre total de messages reçus par l'adaptateur de réception MSMQ à chaque seconde. Le compteur prend uniquement en compte les messages lus dans leur intégralité par l'adaptateur de réception MSMQ dans la file d'attente source.|  
|BizTalk:adaptateur d'envoi MSMQ|Octets envoyés|Nombre total d'octets envoyés par l'adaptateur d'envoi MSMQ. Le compteur est augmenté uniquement pour les messages ayant atteint la file d'attente de destination.|  
||Octets envoyés/s|Nombre total d'octets envoyés par l'adaptateur d'envoi MSMQ à chaque seconde. Le compteur prend uniquement en compte les messages ayant atteint la file d'attente de destination.|  
||Messages envoyés|Nombre total de messages envoyés par l'adaptateur d'envoi MSMQ. Le compteur est augmenté uniquement pour les messages ayant atteint la file d'attente de destination.|  
||Messages envoyés/s|Nombre total de messages envoyés par l'adaptateur d'envoi MSMQ à chaque seconde. Le compteur prend uniquement en compte les messages ayant atteint la file d'attente de destination.|  
  
## <a name="to-access-performance-counters"></a>Pour accéder aux compteurs de performance  
 Utilisez la procédure suivante pour accéder aux compteurs de performances.  
  
#### <a name="if-you-are-using-windows-2008"></a>Si vous exécutez Windows 2008  
  
1.  Cliquez sur **Démarrer**, pointez sur **outils d’administration**, puis cliquez sur **l’Analyseur de performances**.  
  
2.  Dans le **l’Analyseur de performances** boîte de dialogue, développez **outils d’analyse**, sélectionnez **l’Analyseur de performances**, puis cliquez sur **ajouter**.  
  
3.  Dans le **ajouter des compteurs** boîte de dialogue, à partir de la **compteurs disponibles** liste, développez le **MSMQ** objet compteur de performance et sélectionnez les compteurs à surveiller  
  
4.  Dans le **Instances de l’objet sélectionné** , sélectionnez les instances spécifiques à surveiller pour les compteurs sélectionnés, puis cliquez sur **ajouter**.  Pour sélectionner toutes les instances de compteur disponibles, sélectionnez \< **toutes les instances**\>.  
  
5.  Après avoir ajouté les compteurs, cliquez sur **OK**.  
  
     Les compteurs de performances sélectionnés s’affichent sur le **l’Analyseur de performances** écran.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de LoadGen 2007 avec MSMQ](../core/using-loadgen-2007-with-msmq.md)   
 [Optimisation des performances de l’adaptateur MSMQ](../core/optimizing-performance-of-the-msmq-adapter.md)