---
title: "Stockage des données d’activité | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- performance, BAM
- databases [BAM], performance
- activities [BAM], peformance
- databases [BAM], partitioning
- BAM, performance
ms.assetid: 1f736599-3d16-496e-a459-8b0507d57fcb
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0139e76512eb9ca60089cb3c5f1e71b4f5524690
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="activity-data-storage"></a>Stockage des données d'activité
Cette rubrique décrit le stockage des données d'activité, les problèmes de performances engendrés par l'augmentation progressive de la taille des tables de l'activité et la manière dont le composant BAM permet de résoudre ces difficultés en séparant les tables des activités en cours de celles des activités terminées. Cette rubrique traite également des fenêtres en ligne permettant d'interroger les données et de l'utilisation du partitionnement dans les analyses BAM pour augmenter les performances.  
  
 Le principe fondamental du stockage des données d'activité consiste à disposer d'une table par type d'activité, où chaque enregistrement représente une instance d'activité différente (par exemple, une instance en cours ou terminée).  
  
 Dans l'exemple développé ci-après, l'activité considérée est le traitement d'un bon de commande. La table se présente alors de la manière suivante :  
  
|Bon de cmde n°|Heure réception|Ville|Quantité|Heure expédition|Heure livraison|  
|----------|--------------|----------|--------------|--------------|------------------|  
|123|8:00 am|Seattle|150|8:24 heures|12h45|  
|124|8 h 30|Seattle|234|8:45 am|1:20 pm|  
|125|8:35 am|Redmond|87|9:05 am|2 h 30|  
|126|8:45 am|Seattle|450|9 h 20|3:10 pm|  
|127|8:55:00|Redmond|200|9 h 30|\<NULL\>|  
|128|8:57 am|Seattle|340|9 h 20|15:05:00|  
|129|9 h 12|Seattle|120|9 h 45|\<NULL\>|  
|130|9 h 30|Redmond|25|10:15:00|\<NULL\>|  
|131|9:45|Seattle|250|10:35:00|\<NULL\>|  
|132|10:00 am|Redmond|100|\<NULL\>|\<NULL\>|  
|133|10:15:00|Seattle|230|\<NULL\>|\<NULL\>|  
|134|10:25:00|Redmond|45|\<NULL\>|\<NULL\>|  
  
 Dans cette table, lorsque le composant BAM reçoit un nouveau bon de commande, une nouvelle ligne est insérée et des valeurs autres que « null » sont attribuées à certaines colonnes (heure de réception, ville, quantité, etc.). Ensuite, une fois que vous avez validé l'expédition du bon de commande, l'analyse BAM définit une valeur non « null » dans la colonne correspondant à l'heure d'expédition. Enfin, lorsque la commande a été livrée, l'analyse BAM attribue une valeur autre que « null » pour l'heure de livraison.  
  
 Les performances de cette implémentation simplifiée se détériorent rapidement au fil du temps. Au départ, le nombre de transactions pouvant être effectuées par le serveur SQL étant limité (restriction principalement due au processeur), l'impact sur les performances est réduit. En revanche, au bout d'un certain temps, les performances diminuent considérablement. Dans le même temps, la longueur moyenne de la file d'attente pour les E/S du disque augmente jusqu'à dépasser les capacités :  
  
 ![](../core/media/ebiz-prog-bam-data-maint-fig4.gif "ebiz_prog_bam_data_maint_fig4")  
Rapport performances de l'analyse BAM en écriture / longueur de la file d'attente du disque  
  
 Cette évolution est due à l'augmentation de la taille de la table au fur et à mesure que de nouvelles instances du processus d'entreprise prennent fin. Par exemple, un premier appel à la procédure stockée (instruction UPDATE) entraîne une recherche sur les numéros de bon de commande dans l'index mis en cluster ainsi qu'une lecture de certaines pages en mémoire. Les instances du processus de bon de commande étant indépendantes les unes des autres (certaines sont longues, d'autres très brèves), l'appel à la procédure stockée suivant peut concerner une autre instance de bon de commande et donc nécessiter la lecture de pages de données en mémoire différentes. Tant que le nombre total d'enregistrements de bon de commande est réduit, le serveur SQL met en mémoire cache toutes les pages de données. Lorsque le nombre de ces enregistrements devient trop important, la fréquence d'accès au cache diminue et chaque opération requiert une lecture sur le disque physique. Il semble que dans une telle situation, aucune activité d'interrogation de la table ne soit possible.  
  
## <a name="bam-tables"></a>Tables BAM  
 Pour contourner ce problème, l'analyse BAM utilise deux tables distinctes : dans le schéma ci-après, une table est consacrée aux activités en cours et une autre aux activités terminées.  
  
 ![](../core/media/ebiz-prog-bam-data-maint-fig5.gif "ebiz_prog_bam_data_maint_fig5")  
Tables BAM  
  
 Dans ce schéma, l'objectif est d'obtenir, d'une part, une table dont la taille reste raisonnable et où ont lieu les mises à jour et, d'autre part, une table dont la taille peut augmenter et qui est accessible de façon incrémentielle (instructions INSERT uniquement). Dans l'exemple présenté ici, seules les commandes en cours de traitement sont placées dans la table active tandis que celles qui ont déjà été livrées sont placées dans la table des activités terminées.  
  
 Au départ, cette structure à tables multiples est plus lente qu'une table unique fonctionnant à l'aide d'instructions INSERT/UPDATE en raison du système de déclenchement utilisé, mais à long terme, ses performances en écriture restent stables.  
  
## <a name="online-window-for-activity-data"></a>Fenêtre en ligne et données d'activité  
 Dans un premier temps, le stockage d'activité gère les requêtes relatives aux activités en cours ou venant de se terminer. L'analyse BAM se charge ensuite d'archiver et de supprimer de la base de données d'importation principale BAM les activités terminées depuis un certain temps. Les données d'activité transitent par le composant BAM et sont disponibles pour d'éventuelles requêtes pendant une période définie par la fenêtre en ligne.  
  
## <a name="bam-partitioning"></a>Partitionnement BAM  
 Pour obtenir des performances élevées et éviter les temps d'arrêt, le stockage d'activité utilise un partitionnement en fonction de la date et de l'heure de fin de l'activité. Le composant BAM réalise cette opération en remplaçant régulièrement la table des activités terminées par une table vide de format identique. Les nouvelles activités terminées sont ensuite placées dans la table vide tandis que l'analyse BAM conserve l'ancienne table pour d'éventuelles requêtes, comme indiqué dans le schéma ci-dessous :  
  
 ![](../core/media/ebiz-prog-bam-data-maint-fig8.gif "ebiz_prog_bam_data_maint_fig8")  
Remplacement de partition BAM  
  
 Une fois qu'une partition se trouve en dehors de la fenêtre en ligne spécifiée, le composant BAM l'archive puis la supprime. Afin de rendre cette opération moins complexe pour l'utilisateur, l'analyse BAM gère également une vue partitionnée du formulaire :  
  
```  
SELECT * FROM Active   
UNION ALL   
SELECT * FROM Completed   
UNION ALL  
  
```  
  
 Cette vue est automatiquement régénérée à chaque création ou suppression d'une partition.  
  
 Notez les remarques suivantes concernant le partitionnement de l'analyse BAM :  
  
-   Le nom de la vue partitionnée est **bam_\<Nomactivité\>_AllInstances**. Cette vue n'est pas destinée à des interrogations directes mais peut être utile lors du dépannage des outils BAM. Pour effectuer des requêtes sur les données provenant des vues que vous avez créées pour chaque catégorie d'utilisateurs d'activités, utilisez une nouvelle vue. Pour plus d’informations, consultez [Querying Instance Data](../core/querying-instance-data.md).  
  
-   Vous définissez la fenêtre en ligne en modifiant les valeurs de **OnlineWindowTimeUnit** et **OnlineWindowLength** dans l’enregistrement de l’activité actuelle dans la table **bam_Metadata_Activities** dans la base de données d’importation principale.  
  
-   Le package DTS, **BAM_DM_\<Nomactivité\>**, effectue le partitionnement et l’archivage/purge. À chaque exécution, ce lot tronque une nouvelle partition et archive et supprime toutes les partitions se trouvant en dehors de la fenêtre en ligne spécifiée.  
  
-   Si vous n'avez pas configuré de base de données pour archiver les partitions, le composant BAM supprime les anciennes données d'activité sans les archiver au préalable.  
  
## <a name="see-also"></a>Voir aussi  
 [Infrastructure dynamique de l’analyse BAM](../core/bam-dynamic-infrastructure.md)