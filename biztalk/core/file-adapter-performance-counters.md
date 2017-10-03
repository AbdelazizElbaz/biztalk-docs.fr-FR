---
title: "Compteurs de performances de l’adaptateur de fichier | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 343465b4-6b20-4a24-b4b1-138548c572cc
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 617c3fc2821c9b9aa1aba690d27a9b48dc1116c4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="file-adapter-performance-counters"></a>Compteurs de performances de l'adaptateur FILE
Les compteurs de performance permettent d'analyser des aspects spécifiques du travail effectué sur le site ou le système par un service. Ils peuvent vous aider à identifier et à résoudre des problèmes de performances de serveur.  
  
 Les compteurs de performances suivants sont accessibles pour chaque instance d’hôte sous le **BizTalk : adaptateur de réception** et **BizTalk : adaptateur d’envoi** catégories d’objet de performances :  
  
|**Catégorie**|**Compteur**|**Description**|  
|------------------|-----------------|---------------------|  
|BizTalk : adaptateur de réception|Octets reçus|Nombre total d'octets reçus par l'adaptateur de réception FILE. Le compteur est incrémenté après qu'un message est lu dans son intégralité par l'adaptateur dans le système de fichiers.|  
||Octets reçus/s|Nombre total d'octets reçus par l'adaptateur de réception FILE à chaque seconde. Le compteur prend uniquement en compte les messages lus dans leur intégralité par l'adaptateur FILE dans le système de fichiers.|  
||Tentatives de suppression|Nombre de fois où l'adaptateur de réception FILE tente de supprimer un fichier lu.|  
||Échecs de verrouillage|Nombre de fois où l'adaptateur de réception FILE n'a pas réussi à verrouiller le fichier.|  
||Échecs de verrouillage/s|Nombre de fois, par seconde, où l'adaptateur de réception FILE n'a pas réussi à verrouiller le fichier.|  
||Messages reçus|Nombre total de messages reçus par l'adaptateur de réception FILE. Le compteur est incrémenté après qu'un message est lu dans son intégralité par l'adaptateur de réception FILE dans le système de fichiers.|  
||Messages reçus/s|Nombre total de messages reçus par l'adaptateur de réception FILE à chaque seconde. Le compteur prend uniquement en compte les messages lus dans leur intégralité par l'adaptateur de réception FILE dans le système de fichiers.|  
||Durée de construction de lot|Temps moyen nécessaire à l'adaptateur de réception FILE pour créer un lot.|  
|BizTalk : adaptateur d’envoi|Octets envoyés|Nombre total d'octets envoyés par l'adaptateur d'envoi FILE. Le compteur est incrémenté uniquement pour les messages qui ont été écrits complètement au système de fichiers.|  
||Octets envoyés/s|Nombre total d'octets envoyés par l'adaptateur d'envoi FILE à chaque seconde. Le compteur prend uniquement en compte les messages entièrement écrits dans le système de fichiers.|  
||Messages envoyés|Nombre total de messages envoyés par l'adaptateur d'envoi FILE. Le compteur est incrémenté uniquement pour les messages qui ont été écrits complètement au système de fichiers.|  
||Messages envoyés/s|Nombre total de messages envoyés par l'adaptateur d'envoi FILE à chaque seconde. Le compteur prend uniquement en compte les messages entièrement écrits dans le système de fichiers.|  
  
## <a name="to-access-performance-counters"></a>Pour accéder aux compteurs de performance  
 Utilisez la procédure suivante pour accéder aux compteurs de performances.  
  
#### <a name="if-you-are-using-windows-2008"></a>Si vous exécutez Windows 2008  
  
1.  Cliquez sur **Démarrer**, pointez sur **outils d’administration**, puis cliquez sur **l’Analyseur de performances**.  
  
2.  Dans le **l’Analyseur de performances** boîte de dialogue, développez **outils d’analyse**, sélectionnez **l’Analyseur de performances**, puis cliquez sur **ajouter**.  
  
3.  Dans le **ajouter des compteurs** boîte de dialogue, à partir de la **compteurs disponibles** liste, développez le **BizTalk** objet compteur de performance et sélectionnez les compteurs à surveiller  
  
4.  Dans le **Instances de l’objet sélectionné** , sélectionnez les instances spécifiques à surveiller pour les compteurs sélectionnés, puis cliquez sur **ajouter**.  Pour sélectionner toutes les instances de compteur disponibles, sélectionnez \< **toutes les instances**>.  
  
5.  Après avoir ajouté les compteurs, cliquez sur **OK**.  
  
     Les compteurs de performances sélectionnés s’affichent sur le **l’Analyseur de performances** écran.  
  
## <a name="see-also"></a>Voir aussi  
 [Planification des performances soutenues](../core/planning-for-sustained-performance.md)