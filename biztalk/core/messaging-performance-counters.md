---
title: Les compteurs de Performance de la messagerie | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 162d761a-fe69-45b0-a6af-c5d9f714e0ca
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0baa0e38a27bde7ba2331681a1b0ba103c938258
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="messaging-performance-counters"></a>Compteurs de performances de la messagerie
Les compteurs de performance permettent d'analyser des aspects spécifiques du travail effectué sur le site ou le système par un service. Ils peuvent vous aider à identifier et à résoudre des problèmes de performances de serveur.  
  
 Les compteurs de performances suivants sont accessibles pour chaque instance d’hôte sous le **BizTalk : messagerie** et **BizTalk : latence de messagerie** catégories d’objet de performances :  
  
|**Catégorie**|**Compteur**|**Description**|  
|------------------|-----------------|---------------------|  
|BizTalk:messagerie|Emplacements de réception actifs|Nombre d'emplacements de réception actuellement activés dans cette instance d'hôte.|  
||Threads de réception actifs|Dans le moteur de messagerie, nombre de threads qui traitent actuellement les messages reçus des adaptateurs s'exécutant dans cette instance de l'hôte. Ces messages comprennent les messages traités de manière asynchrone par les adaptateurs d'envoi.|  
||Messages d'envoi actifs|Nombre de messages en cours d'envoi dans le moteur de messagerie. Ces messages comprennent les messages en cours de traitement dans le pipeline d'envoi ainsi que les messages de réponse destinés aux adaptateurs de réception.|  
||Threads d'envoi actifs|Dans le moteur de messagerie, nombre de threads qui traitent actuellement des messages à envoyer vers les adaptateurs. Ces messages comprennent les messages de réponse destinés aux adaptateurs de réception.|  
||Documents traités|Documents en cours de traitement.|  
||Documents traités par seconde|Nombre des documents traités par seconde.|  
||Documents reçus|Documents ayant été reçus.|  
||Documents reçus/s|Nombre des documents reçus par seconde.|  
||Documents retransmis|Nombre total de documents de nouveau transmis par les adaptateurs d'envoi.|  
||Documents envoyés/lot|Nombre moyen de documents transmis par lot.|  
||Documents suspendus|Documents dont la transmission a été interrompue.|  
||Nombre de documents suspendus par seconde.|Nombre de documents par seconde pour lesquels la transmission a été interrompue.|  
||Documents transmis/lot|Nombre moyen de messages transmis par lot.|  
||ID Process (Traitement ID)|Identificateur du traitement pour cette instance d'hôte.|  
||Lots de réception en attente|Nombre de lots reçus par le moteur de messagerie mais pour lesquels le traitement n'est pas terminé. Ces lots comprennent les lots traités de manière asynchrone par les adaptateurs d'envoi.|  
||Messages transmis en attente|Nombre de messages transmis aux adaptateurs d'envoi par le moteur de messagerie mais pour lesquels le traitement n'est pas terminé. Cela inclut la réponse pour les messages des adaptateurs de réception.|  
||Expirations du délai des messages de requête|Nombre de messages de requête n'ayant pas reçu de message de réponse dans le délai indiqué par l'adaptateur.|  
||Lots de réception restreints|Nombre de lots dont la réception a été bloquée par le moteur de messagerie en raison d'une charge élevée au niveau du service. Ces lots contiennent des nouveaux messages à traiter.|  
|BizTalk:latence de messagerie|Latence entrante (s)|Latence moyenne, en millisecondes, entre le moment où le moteur de messagerie reçoit un document de l'adaptateur et le moment où ce document est publié vers MessageBox.|  
||Latence sortante de l'adaptateur (s)|Latence moyenne, en millisecondes, entre le moment où l'adaptateur reçoit un document du moteur de messagerie et le moment où il l'envoie.|  
||Latence sortante (s)|Latence moyenne, en millisecondes, entre le moment où le moteur de messagerie reçoit un document de MessageBox et le moment où ce document est envoyé par l'adaptateur.|  
||Latence requête-réponse (s)|Latence moyenne, en millisecondes, entre le moment où le moteur de messagerie reçoit un document de requête de l'adaptateur et le moment où un document de réponse est renvoyé vers l'adaptateur.|  
  
## <a name="to-access-performance-counters"></a>Pour accéder aux compteurs de performance  
 Utilisez la procédure suivante pour accéder aux compteurs de performances.  
  
#### <a name="if-you-are-using-windows-2008"></a>Si vous exécutez Windows 2008  
  
1.  Cliquez sur **Démarrer**, pointez sur **outils d’administration**, puis cliquez sur **l’Analyseur de performances**.  
  
2.  Dans le **l’Analyseur de performances** boîte de dialogue, développez **outils d’analyse**, sélectionnez **l’Analyseur de performances**, puis cliquez sur **ajouter**.  
  
3.  Dans le **ajouter des compteurs** boîte de dialogue, à partir de la **compteurs disponibles** liste, développez le **BizTalk : messagerie** objet compteur de performance et sélectionnez les compteurs à surveiller  
  
4.  Dans le **Instances de l’objet sélectionné** , sélectionnez les instances spécifiques à surveiller pour les compteurs sélectionnés, puis cliquez sur **ajouter**.  Pour sélectionner toutes les instances de compteur disponibles, sélectionnez \< **toutes les instances**>.  
  
5.  Après avoir ajouté les compteurs, cliquez sur **OK**.  
  
     Les compteurs de performances sélectionnés s’affichent sur le **l’Analyseur de performances** écran.  
  
## <a name="see-also"></a>Voir aussi  
 [Trucs et astuces](../core/performance-tips-and-tricks.md)   
 [Mesurer le débit de moteur maximal acceptable](../core/measuring-maximum-sustainable-engine-throughput.md)   
 [Mesurer le débit de suivi maximal acceptable](../core/measuring-maximum-sustainable-tracking-throughput.md)   
 [Optimisation de l’utilisation des ressources via la limitation de l’hôte](../core/optimizing-resource-usage-through-host-throttling.md)