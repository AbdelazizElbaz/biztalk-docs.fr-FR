---
title: "Compteurs de performances de l’adaptateur SOAP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 40b54d4e-0a2e-483f-982a-97ab9fb59202
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 870a3333ce638200c92125f08a4f048150584b51
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="soap-adapter-performance-counters"></a>Compteurs de performances de l'adaptateur SOAP
Les compteurs de performance permettent d'analyser des aspects spécifiques du travail effectué sur le site ou le système par un service. Ils peuvent vous aider à identifier et à résoudre des problèmes de performances de serveur.  
  
 Les compteurs de performances suivants sont accessibles pour chaque instance d’hôte sous le **adaptateur de réception SOAP** et **adaptateur d’envoi SOAP** catégories d’objet de performances :  
  
|**Catégorie**|**Compteur**|**Description**|  
|------------------|-----------------|---------------------|  
|BizTalk:adaptateur de réception SOAP|Messages reçus|Nombre total de messages reçus par l'adaptateur de réception SOAP. Le compteur est incrémenté après qu'un message de requête a été lu dans son intégralité par l'adaptateur dans le client SOAP.|  
||Messages reçus/s|Nombre total de messages reçus par l'adaptateur de réception SOAP à chaque seconde. Le compteur prend uniquement en compte les messages de requête lus dans leur intégralité par l'adaptateur dans le client SOAP.|  
|BizTalk:adaptateur d'envoi SOAP|Messages envoyés|Nombre total de messages envoyés par l'adaptateur d'envoi SOAP. Le compteur est augmenté uniquement pour les messages ayant atteint l'URL de destination.|  
||Messages envoyés/s|Nombre total de messages envoyés par l'adaptateur d'envoi SOAP à chaque seconde. Le compteur prend uniquement en compte les messages qui ont atteint l'URL de destination.|  
  
## <a name="to-access-performance-counters"></a>Pour accéder aux compteurs de performance  
 Utilisez la procédure suivante pour accéder aux compteurs de performances.  
  
#### <a name="if-you-are-using-windows-server-2008"></a>Si vous utilisez Windows Server 2008  
  
1.  Cliquez sur **Démarrer**, pointez sur **outils d’administration**, puis cliquez sur **l’Analyseur de performances**.  
  
2.  Dans le **l’Analyseur de performances** boîte de dialogue, développez **outils d’analyse**, sélectionnez **l’Analyseur de performances**, puis cliquez sur **ajouter**.  
  
3.  Dans le **ajouter des compteurs** boîte de dialogue, à partir de la **compteurs disponibles** liste, développez le **SOAP** objet compteur de performance et sélectionnez les compteurs à surveiller  
  
4.  Dans le **Instances de l’objet sélectionné** , sélectionnez les instances spécifiques à surveiller pour les compteurs sélectionnés, puis cliquez sur **ajouter**. Pour sélectionner toutes les instances de compteur disponibles, sélectionnez \< **toutes les instances**>.  
  
5.  Après avoir ajouté les compteurs, cliquez sur **OK**.  
  
     Les compteurs de performances sélectionnés s’affichent sur le **l’Analyseur de performances** écran.