---
title: "POP3 Compteurs de performances de l’adaptateur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f799175e-e9e7-4937-93bd-aaec1c43b75a
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b0f48879fcc00041ce0fa1cf842a066c6da59804
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="pop3-adapter-performance-counters"></a>Compteurs de performances de l'adaptateur POP3
Les compteurs de performance permettent d'analyser des aspects spécifiques du travail effectué sur le site ou le système par un service. Ils peuvent vous aider à identifier et à résoudre des problèmes de performances de serveur.  
  
 Les compteurs de performances suivants sont accessibles pour chaque instance d’hôte sous le **adaptateur de réception POP3** catégorie d’objet de performances :  
  
|**Catégorie**|**Compteur**|**Description**|  
|------------------|-----------------|---------------------|  
|BizTalk:adaptateur de réception POP3|Sessions actives|Nombre de connexions POP3 actives que l'adaptateur POP3 gère en même temps.|  
||Octets reçus|Nombre total d'octets téléchargés par l'adaptateur POP3 depuis un serveur de messagerie.|  
||Octets reçus/s|Nombre d'octets téléchargés par l'adaptateur POP3 depuis un serveur de messagerie par seconde.|  
||Messages reçus|Nombre total de messages électroniques téléchargés par l'adaptateur POP3 depuis un serveur de messagerie.|  
||Messages reçus/s|Nombre de messages électroniques téléchargés par l'adaptateur POP3 depuis un serveur de messagerie par seconde.|  
  
## <a name="to-access-performance-counters"></a>Pour accéder aux compteurs de performance  
 Pour accéder aux compteurs de performance de l'adaptateur POP3, procédez comme indiqué ci-dessous :  
  
#### <a name="if-you-are-using-windows-2008"></a>Si vous exécutez Windows 2008  
  
1.  Cliquez sur **Démarrer**, pointez sur **outils d’administration**, puis cliquez sur **l’Analyseur de performances**.  
  
2.  Dans le **l’Analyseur de performances** boîte de dialogue, développez **outils d’analyse**, sélectionnez **l’Analyseur de performances**, puis cliquez sur **ajouter**.  
  
3.  Dans le **ajouter des compteurs** boîte de dialogue, à partir de la **compteurs disponibles** liste, développez le **adaptateur de réception POP3** objet compteur de performances et sélectionnez les compteurs à être analysé  
  
4.  Dans le **Instances de l’objet sélectionné** , sélectionnez les instances spécifiques à surveiller pour les compteurs sélectionnés, puis cliquez sur **ajouter**.  Pour sélectionner toutes les instances de compteur disponibles, sélectionnez \< **toutes les instances**>.  
  
5.  Après avoir ajouté les compteurs, cliquez sur **OK**.  
  
     Les compteurs de performances sélectionnés s’affichent sur le **l’Analyseur de performances** écran.  
  
## <a name="see-also"></a>Voir aussi  
 [Analyse de BizTalk Server](../core/monitoring-biztalk-server.md)  
 [Traitement des Messages à parties multiples avec l’adaptateur POP3](../core/processing-multi-part-messages-with-the-pop3-adapter.md)   
 [Considérations pour l’exécution des gestionnaires d’adaptateur au sein d’un hôte en cluster](../core/considerations-for-running-adapter-handlers-within-a-clustered-host1.md)