---
title: "Compteurs de Performance de l’adaptateur SMTP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0c7aa7dd-1674-4bbb-b22f-92204d55c4b8
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a3503b5a37a7b2ab48be2478879cc61187895029
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="smtp-adapter-performance-counters"></a>Compteurs de performances de l'adaptateur SMTP
Les compteurs de performance permettent d'analyser des aspects spécifiques du travail effectué sur le site ou le système par un service. Ils peuvent vous aider à identifier et à résoudre des problèmes de performances de serveur.  
  
 Les compteurs de performances suivants sont accessibles pour chaque instance d’hôte sous le **adaptateur d’envoi SMTP** catégorie d’objet de performances :  
  
|**Catégorie**|**Compteur**|**Description**|  
|------------------|-----------------|---------------------|  
|BizTalk:adaptateur d'envoi SMTP|Messages envoyés|Nombre total de messages envoyés par l'adaptateur SMTP. Le compteur prend en compte uniquement les messages qui ont été transmis au serveur SMTP.|  
||Messages envoyés/s|Nombre de messages envoyés par l'adaptateur SMTP à chaque seconde. Le compteur s'applique uniquement aux messages qui ont été transmis au serveur SMTP.|  
  
## <a name="to-access-performance-counters"></a>Pour accéder aux compteurs de performance  
 Utilisez la procédure suivante pour accéder aux compteurs de performances.  
  
#### <a name="if-you-are-using-windows-2008"></a>Si vous exécutez Windows 2008  
  
1.  Cliquez sur **Démarrer**, pointez sur **outils d’administration**, puis cliquez sur **l’Analyseur de performances**.  
  
2.  Dans le **l’Analyseur de performances** boîte de dialogue, développez **outils d’analyse**, sélectionnez **l’Analyseur de performances**, puis cliquez sur **ajouter**.  
  
3.  Dans le **ajouter des compteurs** boîte de dialogue, à partir de la **compteurs disponibles** liste, développez le **adaptateur d’envoi SMTP**objet compteur de performances et sélectionnez les compteurs à être analysé  
  
4.  Dans le **Instances de l’objet sélectionné** , sélectionnez les instances spécifiques à surveiller pour les compteurs sélectionnés, puis cliquez sur **ajouter**.  Pour sélectionner toutes les instances de compteur disponibles, sélectionnez \< **toutes les instances**\>.  
  
5.  Après avoir ajouté les compteurs, cliquez sur **OK**.  
  
     Les compteurs de performances sélectionnés s’affichent sur le **l’Analyseur de performances** écran.