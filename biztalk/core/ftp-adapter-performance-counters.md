---
title: "Compteurs de performances de l’adaptateur FTP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ca5cbe67-9aa3-4194-816e-fab4eb551c07
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5dad67f24f37f661e26f4cb56895c6bcad6b0782
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="ftp-adapter-performance-counters"></a>Compteurs de performances de l'adaptateur FTP
Les compteurs de performance permettent d'analyser des aspects spécifiques du travail effectué sur le site ou le système par un service. Ils peuvent vous aider à identifier et à résoudre des problèmes de performances de serveur.  
  
 Les compteurs de performances suivants sont accessibles pour chaque instance d’hôte sous le **adaptateur de réception FTP** et **adaptateur d’envoi FTP** catégories d’objet de performances :  
  
|**Catégorie**|**Compteur**|**Description**|  
|------------------|-----------------|---------------------|  
|BizTalk:adaptateur de réception FTP|Octets reçus|Nombre total d'octets reçus par l'adaptateur de réception FTP. Le compteur est incrémenté après qu'un message est lu dans son intégralité par l'adaptateur de réception FTP sur le serveur FTP.|  
||Octets reçus/s|Nombre total d'octets reçus par l'adaptateur de réception FTP à chaque seconde. Le compteur prend uniquement en compte les messages lus dans leur intégralité par l'adaptateur de réception FTP sur le serveur FTP.|  
||Messages reçus|Nombre total de messages reçus par l'adaptateur de réception FTP. Le compteur est incrémenté après qu'un message est lu dans son intégralité par l'adaptateur de réception FTP sur le serveur FTP.|  
||Messages reçus/s|Nombre total de messages reçus par l'adaptateur de réception FTP à chaque seconde. Le compteur prend uniquement en compte les messages lus dans leur intégralité par l'adaptateur de réception FTP sur le serveur FTP.|  
|BizTalk:adaptateur d'envoi FTP|Octets envoyés|Nombre total d'octets envoyés par l'adaptateur d'envoi FTP. Le compteur est incrémenté uniquement pour les messages qui ont été écrits sur le serveur FTP de destination.|  
||Octets envoyés/s|Nombre total d'octets envoyés par l'adaptateur d'envoi FTP à chaque seconde. Le compteur s’applique uniquement aux messages qui ont été écrits sur le serveur FTP de destination.|  
||Messages envoyés|Nombre total de messages envoyés par le protocole FTP l’adaptateur d’envoi. Le compteur est incrémenté uniquement pour les messages qui ont été écrits sur le serveur FTP de destination.|  
||Messages envoyés/s|Nombre total de messages envoyés par l'adaptateur d'envoi FTP à chaque seconde. Le compteur prend en compte uniquement les messages qui ont été écrits sur le serveur FTP de destination.|  
  
## <a name="to-access-performance-counters"></a>Pour accéder aux compteurs de performance  
 Utilisez la procédure suivante pour accéder aux compteurs de performances.  
  
#### <a name="if-you-are-using-windows-2008"></a>Si vous exécutez Windows 2008  
  
1.  Cliquez sur **Démarrer**, pointez sur **outils d’administration**, puis cliquez sur **l’Analyseur de performances**.  
  
2.  Dans le **l’Analyseur de performances** boîte de dialogue, développez **outils d’analyse**, sélectionnez **l’Analyseur de performances**, puis cliquez sur **ajouter**.  
  
3.  Dans le **ajouter des compteurs** boîte de dialogue, à partir de la **compteurs disponibles** liste, développez le **FTP** objet compteur de performance et sélectionnez les compteurs à surveiller  
  
4.  Dans le **Instances de l’objet sélectionné** , sélectionnez les instances spécifiques à surveiller pour les compteurs sélectionnés, puis cliquez sur **ajouter**.  Pour sélectionner toutes les instances de compteur disponibles, sélectionnez \< **toutes les instances**\>.  
  
5.  Après avoir ajouté les compteurs, cliquez sur **OK**.  
  
     Les compteurs de performances sélectionnés s’affichent sur le **l’Analyseur de performances** écran.  
  
## <a name="see-also"></a>Voir aussi  
 [Analyse de BizTalk Server](../core/monitoring-biztalk-server.md) [considérations pour l’exécution des gestionnaires d’adaptateur au sein d’un hôte en cluster](../core/considerations-for-running-adapter-handlers-within-a-clustered-host1.md)