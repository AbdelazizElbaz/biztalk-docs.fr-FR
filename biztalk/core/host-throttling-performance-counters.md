---
title: Limitation des compteurs de performances de l’hôte | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- host throttling, performance counters
ms.assetid: b9090d1c-86be-40db-b814-cc116a426d95
caps.latest.revision: 22
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2ca80f44b9f1244a340e9a9892593ae42ba4b4e9
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="host-throttling-performance-counters"></a>Compteurs de performances des limitations des hôtes
Cette section décrit les compteurs de performance qui mesurent les paramètres système ayant un impact sur les limitations des hôtes. Les compteurs de performances suivants sont accessibles pour chaque instance d’hôte sous le **BizTalk : Agent** catégorie d’objet de performances :  
  
|Compteur| Description|  
|-------------|-----------------|  
|Nombre d'instances actives|Nombre d'instances de service actives en mémoire. Pour le moteur d'orchestration, une instance de service est une instance en cours d'exécution d'une planification d'orchestration. Pour le Gestionnaire des points de terminaison, une instance de service peut correspondre soit à un message sans état, soit à un ensemble de messages avec état. **Remarque :** instances avec état sont ceux qui gèrent certaines informations d’état sur les messages associés à l’instance. Les messages appartenant à une instance avec état sont liés les uns aux autres d'une manière ou d'une autre. Par exemple, un port d'envoi chronologique qui tient à jour des informations sur la commande est considéré comme une instance avec état. La plupart des scénarios de messagerie impliquent des instances sans état dans lesquelles les messages sont traités indépendamment les uns des autres. Chaque instance de ce type correspond à un seul message dans le Gestionnaire des points de terminaison.|  
|Session de base de données|Nombre de connexions simultanées à la base de données MessageBox utilisées.|  
|Seuil de session de base de données|Nombre maximal de sessions de base de données simultanées en vigueur. Ce paramètre est initialement défini la **les connexions de base de données** valeur sur le **limitation basée sur une ressource** onglet **Panneau de configuration**. Cette valeur est réglée automatiquement en fonction de l'utilisation des sessions de base de données faite par le processus. Si le nombre de sessions de base de données simultanées dépasse ce seuil, les limitations des hôtes sont implémentées.|  
|Taille de la base de données|Nombre de messages publiés par ce processus se trouvant dans les files d'attente de base de données. Cette valeur est déterminée par le nombre d'éléments dans les tables de file d'attente pour tous les hôtes et le nombre d'éléments dans les tables du spouleur et de suivi. Si un processus publie vers plusieurs files d'attente, ce compteur représente la moyenne pondérée de toutes les files d'attente. **Remarque :** si l’hôte est redémarré, les statistiques stockées en mémoire sont perdues. Étant donné qu'une certaine surcharge est impliquée, BizTalk Server ne recommence à rassembler les statistiques que lorsque au moins 100 publications et 5 % du nombre total de publications s'exécutent dans le processus hôte redémarré.|  
|Nombre de sessions de bases de données élevé|-0 : Normal<br />-1 : nombre de sessions de base de données dépasse le seuil|  
|Taille importante de bases de données|-0 : Normal<br />-1 : taille de la base de données a été augmenté de manière supérieur au seuil<br /><br /> Ce compteur ne sera défini à une valeur d’une des conditions indiquées pour le **nombre dans la base de données de messages** seuil se produit. [Comment modifier les ressources de limitation paramètres](../core/how-to-modify-resource-based-throttling-settings.md) fournit des informations sur ce seuil de limitation.|  
|Nombre élevé de messages en cours de traitement|-0 : Normal<br />-1 : messages in-process nombre dépasse la limite|  
|Vitesse élevée de remise de messages|-0 : Normal<br />-1 : taux de livraison dépasse le taux de traitement des messages de message|  
|Vitesse élevée de publication des messages|-0 : Normal<br />-1 : demande taux dépasse le taux d’achèvement de publication|  
|Mémoire de processus élevée|-0 : Normal<br />-1 : mémoire de processus dépasse le seuil|  
|Mémoire système élevée|-0 : Normal<br />-1 : la mémoire système dépasse le seuil|  
|Nombre de threads élevé|-0 : Normal<br />-1 : nombre de threads dépasse le seuil|  
|Nombre de messages en cours de traitement|Nombre de messages en mémoire transmis au moteur XLANG ou au moteur de messagerie en sortie, qui n'ont pas encore été traités.|  
|Seuil du nombre de messages en cours de traitement|Nombre maximal de messages en cours de traitement en vigueur.|  
|Délai de remise de messages (ms)|Délai en millisecondes actuellement imposé à chaque lot de remise de messages (applicable si la remise de messages est soumise à limitation).|  
|Vitesse d'entrée de remise de messages|Nombre de messages remis par seconde au moteur d'orchestration ou au moteur de messagerie dans l'intervalle type indiqué.|  
|Vitesse de sortie de remise de messages|Nombre de messages traités par seconde par le moteur d'orchestration ou le moteur de messagerie dans l'intervalle type indiqué.|  
|État de limitation de remise de messages|Indicateur précisant si le système limite la remise de messages (ce qui affecte le traitement des messages XLANG et les transports en sortie).<br /><br /> -0 : ne pas de limitation<br />-1 : limitation due à des taux de remise de messages déséquilibrées (vitesse en entrée dépasse la vitesse de sortie)<br />-3 : limitation due à haute intra-processus nombre de messages<br />-4 : limitation due à la mémoire de processus<br />-5 : limitation due à une sollicitation de la mémoire système<br />-9 : limitation due à un nombre élevé de threads<br />-10 : limitation due à un utilisateur de remplacement sur la remise|  
|Durée de l'état de limitation de remise de messages|Nombre de secondes écoulées depuis que le système se trouve dans cet état. Si des limitations d'hôte sont définies, depuis quand et, sinon, à quand remonte la dernière application de limitations.|  
|Remplacement d'utilisateur pour limitation de remise de messages|Ce compteur représente le remplacement d'utilisateur géré par le moteur et interprété comme suit :<br /><br /> -0 : aucune substitution<br />-1 : toujours limiter la remise de messages<br />-2 : ne pas limiter la remise de messages<br /><br /> Ce remplacement est configurable dans le **basé sur le taux de limitation** onglet **Panneau de configuration**.|  
|Délai de publication de messages (ms)|Délai en millisecondes actuellement imposé à chaque lot de publication de messages (applicable si la publication de messages est soumise à des limitations et si celles-ci s'appliquent au lot).|  
|Vitesse d'entrée de publication de messages|Nombre de messages envoyés par seconde à la base de données pour publication, dans l'intervalle type donné.|  
|Vitesse de sortie de publication de messages|Nombre de messages par seconde effectivement publiés dans la base de données, dans l'intervalle type donné.|  
|État de limitation de publication de messages|Indicateur précisant si le système limite la publication de messages (ce qui affecte le traitement des messages XLANG et les transports en entrée).<br /><br /> -0 : ne pas de limitation<br />-2 : limitation due à des taux de publication de messages déséquilibrées (vitesse en entrée dépasse la vitesse de sortie)<br />-4 : limitation due à la mémoire de processus<br />-5 : limitation due à une sollicitation de la mémoire système<br />-6 : limitation en raison d’une croissance de la base de données<br />-8 : limitation due à un nombre élevé de sessions<br />-9 : limitation due à un nombre élevé de threads<br />-11 : limitation due à un utilisateur de remplacement sur la publication|  
|Durée de limitation de publication de messages|Nombre de secondes écoulées depuis que le système se trouve dans cet état. Si des limitations d'hôte sont définies, depuis quand et, sinon, à quand remonte la dernière application de limitations.|  
|Remplacement d'utilisateur pour limitation de publication de messages|Ce compteur représente le remplacement d'utilisateur géré par le moteur et interprété comme suit :<br /><br /> -0 : aucune substitution<br />-1 : toujours limiter la publication de messages<br />-2 : ne pas limiter la publication de messages<br /><br /> Ce remplacement est configurable dans le **basé sur le taux de limitation** onglet **Panneau de configuration**.|  
|Utilisation de la mémoire physique (Mo)|Quantité de mémoire physique en Mo utilisée par les tous processus sur l'ordinateur.|  
|Utilisation de la mémoire de processus (Mo)|Consommation de mémoire de processus en Mo. Il s'agit de la taille maximale de la plage de travail du processus et de l'espace total alloué au fichier d'échange du processus.|  
|Seuil d'utilisation de la mémoire de processus (Mo)|Seuil de consommation de mémoire de processus en Mo en vigueur. Ce paramètre est initialement défini la **virtuelle de processus** valeur **Panneau de configuration**. Si une valeur en pourcentage est spécifiée, elle est calculée sur la base de la mémoire disponible à valider.|  
|ID de la classe du service|Valeur décimale de la partie initiale du GUID de la classe de service à laquelle cette instance de compteur de performance correspond. Un processus peut héberger plusieurs classes de service ; les compteurs de performance de l'agent des messages affichent les données associées à la classe de service la plus active.|  
|Nombre de threads|Nombre de threads utilisés dans le processus.|  
|Seuil de nombre de threads|Nombre maximal de threads dans le processus en vigueur. Ce paramètre est initialement défini la **Threads** valeur sur le **limitation basée sur une ressource** onglet **Panneau de configuration**. Cette valeur est réglée automatiquement en fonction des besoins du processus en termes de threads. Si le nombre de threads dans le processus dépasse ce seuil, les limitations des hôtes sont implémentées.|  
|Nombre total de lots validés|Nombre de lots de base de données validés par la classe de service.|  
|Nombre total de messages remis|Nombre de messages sortants remis au moteur d'orchestration ou au Gestionnaire de points de terminaison.|  
|Nombre total de messages publiés|Nombre de messages publiés|  
  
> [!NOTE]
>  Le **BizTalk : Agent** les compteurs de performance sont fournis à des fins d’analyse du comportement de limitation d’un ordinateur hôte et par conséquent ne capture pas données, sauf si l’ordinateur hôte spécifié traite activement des documents. Ce comportement est destiné à éviter la consommation de threads système avec l'analyseur de performances, lorsqu'aucune activité de limitation n'est en cours.  
  
## <a name="to-access-performance-counters"></a>Pour accéder aux compteurs de performance  
 Utilisez la procédure suivante pour accéder aux compteurs de performances.  
  
#### <a name="if-you-are-using-windows-2008"></a>Si vous exécutez Windows 2008  
  
1.  Cliquez sur **Démarrer**, pointez sur **outils d’administration**, puis cliquez sur **l’Analyseur de performances**.  
  
2.  Dans le **l’Analyseur de performances** boîte de dialogue, développez **outils d’analyse**, sélectionnez **l’Analyseur de performances**, puis cliquez sur **ajouter**.  
  
3.  Dans le **ajouter des compteurs** boîte de dialogue, à partir de la **compteurs disponibles** liste, développez le **BizTalk : Agent** objet compteur de performances et sélectionnez les compteurs à être analysé.  
  
4.  Dans le **Instances de l’objet sélectionné** , sélectionnez les instances spécifiques à surveiller pour les compteurs sélectionnés, puis cliquez sur **ajouter**.  Pour sélectionner toutes les instances de compteur disponibles, sélectionnez \< **toutes les instances**\>.  
  
5.  Après avoir ajouté les compteurs, cliquez sur **OK**.  
  
     Les compteurs de performances sélectionnés s’affichent sur le **l’Analyseur de performances** écran.  
  
## <a name="see-also"></a>Voir aussi  
 [Limitation des recommandations sur la conception](../core/throttling-design-recommendations.md)   
 [Comment BizTalk Server implémente la limitation de l’hôte](../core/how-biztalk-server-implements-host-throttling.md)   
 [Utilisation du panneau de configuration pour le réglage des performances de BizTalk Server](../core/using-settings-dashboard-for-biztalk-server-performance-tuning.md)