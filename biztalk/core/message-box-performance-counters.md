---
title: "Compteurs de Performance de boîte de message | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5eafbd7b-f5fc-4942-a975-18154e6a7ee2
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 584cad0c850b85ef7c920da1611adbdc464d7250
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="message-box-performance-counters"></a>Compteurs de performances de MessageBox
Les compteurs de performance permettent d'analyser des aspects spécifiques du travail effectué sur le site ou le système par un service. Ils peuvent vous aider à identifier et à résoudre des problèmes de performances de serveur.  
  
 Les compteurs de performances suivants sont accessibles pour chaque instance d’hôte sous le **BizTalk : MessageBox : compteurs généraux** et **BizTalk : zone : hôte compteurs** catégories d’objet de performance :  
  
> [!NOTE]
>  Pour activer les compteurs qui font référence à un travail d'agent SQL, vous devez inclure le rôle SQLAgentUserRole au compte de service utilisé pour exécuter l'hôte BizTalk/Service NT. Vous pouvez également accorder une autorisation d'accès à l'aide des autres rôles ou accorder explicitement un accès en lecture à la base de données MSDB.  
  
> [!NOTE]
>  Si vous avez ajouté une base de données MessageBox à votre groupe BizTalk Server, les compteurs répertoriés ci-dessous ne seront pas disponibles pour cette MessageBox jusqu'à ce que la configuration **actualisation du Cache** intervalle pour le groupe BizTalk Server a expiré (la valeur par défaut de 60 secondes).  
  
|Catégorie|Compteur| Description|  
|--------------|-------------|-----------------|  
|Compteurs généraux|Instances - Nombre total|Calcule, pour chaque hôte, la somme de toutes les instances existant dans une base MessageBox en particulier.|  
|Compteurs généraux|Nettoyage des processus obsolètes MsgBox (travaux de purge)|Durée en secondes de la dernière exécution de la fonction d'agent SQL qui libère les lignes de la base de données associées aux processus BizTalk obsolètes.|  
|Compteurs généraux|Nettoyage des msg MsgBox (travaux de purge)|Durée en secondes de la dernière exécution de la fonction d'agent SQL qui nettoie les tables MessageBox associées aux messages supprimés.|  
|Compteurs généraux|Nettoyage parties MsgBox (travaux de purge)|Durée en secondes de la dernière exécution de la fonction d'agent SQL qui nettoie les tables MessageBox associées aux parties de messages supprimées.|  
|Compteurs généraux|Travail MsgBox d'abonnements de purge (travaux de purge)|Durée en secondes de la dernière exécution de la fonction d'agent SQL qui purge les abonnements qui ne sont plus utilisés.|  
|Compteurs généraux|Taille mise en file d'attente|Effectue le suivi de la taille de la file d'attente pour une MessageBox donnée sur un serveur donné.|  
|Compteurs généraux|Copie msg suivis (travaux de purge)|Durée en secondes de la dernière exécution de la fonction d'agent SQL qui copie le corps des messages suivis.|  
|Compteurs généraux|Taille données de suivi|Effectue le suivi de la taille de la table des données de suivi pour une MessageBox donnée sur un serveur donné.|  
|Compteurs généraux|Nettoyage du spouleur de suivi (travaux de purge)|Durée en secondes de la dernière exécution de la fonction d'agent SQL qui purge les tables du spouleur de suivi inactives.|  
|Compteurs de l'hôte|File d'attente hôte - Réf msg état instance - Longueur|Effectue le suivi du nombre de références de message dans la file d'attente d'état d'instance de cet hôte.|  
|Compteurs de l'hôte|File d'attente hôte - Longueur|Effectue le suivi du nombre total de messages d'une file d'attente particulière.|  
|Compteurs de l'hôte|File d'attente hôte - Nombre d'instances|Effectue le suivi du nombre d'instances de cet hôte.|  
|Compteurs de l'hôte|File d'attente hôte - Msgs suspendus - Longueur|Effectue le suivi du nombre total de messages suspendus pour cet hôte.|  
  
## <a name="to-access-performance-counters"></a>Pour accéder aux compteurs de performance  
 Utilisez la procédure suivante pour accéder aux compteurs de performances.  
  
#### <a name="if-you-are-using-windows-2008"></a>Si vous exécutez Windows 2008  
  
1.  Cliquez sur **Démarrer**, pointez sur **outils d’administration**, puis cliquez sur **l’Analyseur de performances**.  
  
2.  Dans le **l’Analyseur de performances** boîte de dialogue, développez **outils d’analyse**, sélectionnez **l’Analyseur de performances**, puis cliquez sur **ajouter**.  
  
3.  Dans le **ajouter des compteurs** boîte de dialogue, à partir de la **compteurs disponibles** liste, sélectionnez **BizTalk : MessageBox : compteurs généraux** ou **boîte de BizTalk : Héberger des compteurs**. Développez l'objet compteur de performance sélectionné et sélectionnez les compteurs à suivre.  
  
4.  Dans le **Instances de l’objet sélectionné** , sélectionnez les instances spécifiques à surveiller pour les compteurs sélectionnés, puis cliquez sur **ajouter**.  Pour sélectionner toutes les instances de compteur disponibles, sélectionnez \< **toutes les instances**\>.  
  
5.  Après avoir ajouté les compteurs, cliquez sur **OK**.  
  
     Les compteurs de performances sélectionnés s’affichent sur le **l’Analyseur de performances** écran.  
  
## <a name="see-also"></a>Voir aussi  
 [Trucs et astuces](../core/performance-tips-and-tricks.md)   
 [Mesurer le débit de moteur maximal acceptable](../core/measuring-maximum-sustainable-engine-throughput.md)   
 [Mesurer le débit de suivi maximal acceptable](../core/measuring-maximum-sustainable-tracking-throughput.md)   
 [Optimisation de l’utilisation des ressources via la limitation de l’hôte](../core/optimizing-resource-usage-through-host-throttling.md)