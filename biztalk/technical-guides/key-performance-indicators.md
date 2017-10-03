---
title: "Indicateurs de Performance clés | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 298d639a-7adf-4f04-b097-a17f4c77ee50
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8a03bf76c725f22567d5e884ca22e3a862b15ce3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="key-performance-indicators"></a>Indicateurs de Performance clés
Cette rubrique fournit des résultats des tests du groupe de produit de BizTalk Server observé lorsque vous utilisez les méthodes suivantes de la montée en puissance parallèle :  
  
-   Indicateurs de performance (KPI) de clé lorsque vous augmentez le nombre de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ordinateurs dans un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] groupe. Pour ces tests, qu’un seul [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] base de données MessageBox a été configuré pour le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] groupe. Ces tests se concentre uniquement sur l’impact de l’ajout de plusieurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ordinateurs à un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] groupe.  
  
-   Indicateurs de performance clés lorsque vous augmentez le nombre de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données MessageBox utilisées par le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] groupe. Ces tests se concentre uniquement sur l’impact de l’ajout de plusieurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données MessageBox pour un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] groupe.  
  
-   Indicateurs de performance clés lorsque vous augmentez le nombre des deux [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ordinateurs et [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données MessageBox utilisées par le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] groupe. Ces tests mesurer l’impact de l’ajout à la fois [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ordinateurs et [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données MessageBox pour un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] groupe.  
  
## <a name="analysis-of-key-performance-indicators"></a>Analyse des indicateurs de performance clés  
  
### <a name="messaging-scenario-biztalk-server-scale-out--biztalk-and-sql-kpi"></a>Scénario de messagerie, BizTalk Server montée en puissance – BizTalk et SQL KPI  
 Ajout d’un deuxième ordinateur exécutant BizTalk Server ne présente pas un impact significatif sur le débit global.  La charge sur l’UC du serveur BizTalk diminue de 25 %. Le processeur pour SQL Server augmente légèrement de 59 % à 59.8 % lorsque le deuxième ordinateur exécutant BizTalk Server est ajouté au groupe BizTalk Server. Au-delà de ce point, aucun gain de performances supplémentaire a été acquise en augmentant le nombre de serveurs de traitement de BizTalk Server.  
  
 Chaque instance d’hôte BizTalk interroge régulièrement la file d’attente appropriée dans la MessageBox. Tout message qui est référencé dans la file d’attente de l’ordinateur hôte est en réalité stocké dans le jeu de tables dans la MessageBox partagé. Si le débit supprime lors de l’ajout de plusieurs ordinateurs exécutant BizTalk Server, une cause courante est une activité trop importante sur les tables partagées au sein de la base de données MessageBox. Un chemin d’e/s dédié pour SQL Server à ces tables peut être créé en affectant ces tables à un groupe de fichiers spécifique.  
  
 [Optimisation des groupes de fichiers pour le Databases2](../technical-guides/optimizing-filegroups-for-the-databases2.md) fournit des conseils sur la façon d’affecter les tables de groupes de fichiers spécifiques. Le script inclus dans [Script SQL des groupes de fichiers de base de données BizTalk Server MessageBox](../technical-guides/biztalk-server-messagebox-database-filegroups-sql-script.md) du guide indique comment procéder. Montée en puissance pour une configuration à plusieurs MessageBox doit être considérée uniquement après la distribution d’objets de MessageBox sur plusieurs groupes de fichiers, et une fois que toutes les autres optimisations de SQL ont été appliquées.  
  
 **Pourcentage d’utilisation du processeur SQL Server et de BizTalk Server**  
  
 ![M &#45; SingleMsgBox](../technical-guides/media/m-singlemsgbox.gif "SingleMsgBox-M")  
  
### <a name="messaging-scenario-biztalk-server-and-sql-server-scale-out--biztalk-and-sql-kpi"></a>Scénario de messagerie BizTalk Server et SQL Server avec montée en charge – BizTalk et SQL KPI  
 Ce test a été effectué pour déterminer l’efficacité de l’évolution horizontale du niveau de SQL Server en ajoutant les quatre bases de données MessageBox. Dans ce scénario, l’ajout de deux ordinateurs exécutant BizTalk Server activé un débit maximal acceptable de 2,790 messages par seconde. Il s’agissait % 118 plus élevé que le débit maximal de peut être obtenu lors de l’utilisation d’un seul élément MessageBox. Au-delà de ce point, l’ajout de davantage de puissance de traitement au niveau de BizTalk Server dégradation des performances de façon similaire au scénario MessageBox unique.  
  
 Les principaux résultats des tests de scénario de messagerie sont que la montée en puissance parallèle BizTalk Server est une technique efficace pour augmenter le débit global si la contention sur SQL Server n’est pas un goulet d’étranglement. Si la base de données MessageBox devient un point de contention, commencez par appliquer les optimisations décrites en détail dans [optimisation des performances de base de données](../technical-guides/optimizing-database-performance.md), en particulier le script de l’optimisation du groupe de fichiers est décrit dans [BizTalk Server Script de SQL de groupes de fichiers de base de données MessageBox](../technical-guides/biztalk-server-messagebox-database-filegroups-sql-script.md) pour distribuer la charge d’e/s. Si vous ne parvenez toujours pas à atteindre le débit souhaité, vous devez envisager de montée en puissance parallèle en ajoutant plusieurs bases de données MessageBox.  
  
 **Pourcentage d’utilisation du processeur SQL Server et de BizTalk Server**  
  
 ![M &#45; MultipleMsgBox](../technical-guides/media/m-multiplemsgbox.gif "MultipleMsgBox-M")  
  
### <a name="orchestration-scenario-biztalk-server-scale-out--sql-server-and-biztalk-server-kpi"></a>Scénario de l’orchestration, BizTalk Server montée en puissance – SQL Server et BizTalk Server KPI  
 Ajout d’un deuxième ordinateur exécutant BizTalk Server ne présente pas un impact significatif sur le débit global. La charge sur l’UC du serveur BizTalk diminue de 23 %. Le processeur pour SQL Server augmente de 66.5 % à 68,5 % lors de l’ajout d’un autre ordinateur exécutant BizTalk Server.  
  
 **Pourcentage d’utilisation du processeur SQL Server et de BizTalk Server**  
  
 ![O &#45; SingleMsgBox](../technical-guides/media/o-singlemsgbox.gif "SingleMsgBox-O")  
  
### <a name="orchestration-scenario-biztalk-server-and-sql-server-scale-out--sql-server-and-biztalk-server-kpi"></a>Scénario d’orchestration, BizTalk Server et SQL Server avec montée en charge – SQL Server et BizTalk Server KPI  
 Ce test a été effectué pour déterminer l’efficacité de la montée en puissance parallèle de niveau de BizTalk Server et de SQL Server en ajoutant d’autres ordinateurs exécutant BizTalk Server et plusieurs bases de données MessageBox pour le scénario d’Orchestration. Dans ce scénario, l’ajout de deux ordinateurs exécutant BizTalk Server activé un débit maximal acceptable de 1,487 orchestrations par seconde. Il s’agissait 116 % dépasse le nombre maximal de résultats peut être obtenu par rapport à un seul élément MessageBox. Montée en puissance parallèle pour les quatre bases de données MessageBox sur des ordinateurs distincts de SQL Server prend en charge un débit accru en raison d’une puissance de traitement supplémentaire et la possibilité de répartir la charge de la base de données sur plusieurs bases de données MessageBox. Cela risquerait évite également la contention sur les tables partagées, ce qui était un goulot d’étranglement dans le même environnement MessageBox. Comme avec le scénario de messagerie, augmenter le nombre de bases de données MessageBox et de distribuer ces entre des instances SQL dédiés permettent l’ajout de plusieurs ordinateurs BizTalk Server pour le groupe BizTalk Server.  
  
 **Pourcentage d’utilisation du processeur SQL Server et de BizTalk Server**  
  
 ![O &#45; MultipleMsgBox](../technical-guides/media/o-multiplemsgbox.gif "MultipleMsgBox-O")  
  
## <a name="see-also"></a>Voir aussi  
 [Mise à l’échelle d’un environnement BizTalk Server de Production](../technical-guides/scaling-a-production-biztalk-server-environment.md)