---
title: "Résultats des tests : Indicateurs de Performance clés SQL Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2459ee6d-7a75-4338-ba5c-f42ab673ab87
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 93e1f1bdef55ad726c308902062dccff67eeb170
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="test-results-sql-server-key-performance-indicators"></a>Résultats des tests : Indicateurs de Performance clés SQL Server
Cette rubrique résume SQL Server Performance indicateurs clés (KPI) observé sur les scénarios de test. Ces tests évalué les KPI SQL Server suivantes :  
  
-   L’utilisation du processeur SQL telle que mesurée par le **\SQL\Processor(_Total)\\% temps processeur** compteur Perfmon.  
  
-   Le nombre de lots de commandes Transact-SQL reçus par seconde, telle que mesurée par le **\SQL Server:SQL Statistics\Batch demandes par seconde** compteur Perfmon.  
  
## <a name="summary-of-sql-server-key-performance-indicators"></a>Résumé des indicateurs de Performance clés SQL Server  
 Pour chaque scénario, les machines physiques étaient limités afin que le nombre de processeurs logiques et les processeurs virtuels était équivalent. Cela a été effectuée à l’aide des commutateurs /maxmem et/NUMPROC du fichier boot.ini. Pour plus d’informations sur l’utilisation de ces commutateurs, consultez « Démarrage INI Options référence » à [http://go.microsoft.com/fwlink/?LinkId=122139](http://go.microsoft.com/fwlink/?LinkId=122139).  
  
 **Comparaison des indicateurs de Performance clés SQL Server –** [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] d’utilisation du processeur, mesurée avec **\SQL\Processor(_Total)\\% temps processeur** compteur était environ le même sur tous les test des environnements, allant de faible niveau de 88 % et 90.1 %.   Il existe toutefois une différence significative entre les **\SQL Server:SQL Statistics\Batch demandes par seconde** mesuré sur l’environnement consolidé (4520) et le **\SQL Server:SQL Statistics\Batchdedemandes/s** mesuré sur l’environnement physique (6350). Le **\SQL Server:SQL Statistics\Batch demandes par seconde** compteur Perfmon constitue un bon indicateur de la quantité de travail est effectuée par SQL Server. La réduction de requêtes de lots/s lorsque SQL Server est en cours d’exécution dans un environnement Hyper-V peut être attribuée à la surcharge du processeur requise par Hyper-V.  
  
 Il existe, toutefois, une différence significative entre les **\SQL Server:SQL Statistics\Batch demandes par seconde** mesuré sur l’environnement consolidé (4520) et le **\SQL Server:SQL Statistics\Batch demandes par seconde**  mesuré sur l’environnement physique (6350). Le **\SQL Server:SQL Statistics\Batch demandes par seconde** compteur Perfmon constitue un bon indicateur de la quantité de travail est effectuée par SQL Server. La réduction de requêtes de lots/s lorsque SQL Server est en cours d’exécution dans un environnement Hyper-V peut être attribuée à la surcharge du processeur requise par Hyper-V.  
  
 Suivez ces étapes pour augmenter les performances de SQL Server est en cours d’exécution sur un ordinateur virtuel de Hyper-V telle que mesurée par le **\SQL Server:SQL Statistics\Batch demandes par seconde** compteur Analyseur de performances :  
  
1.  **Allouer des disques de disque dur virtuel fixes supplémentaires avec des contrôleurs virtuels dédiés et les canaux –** dédiée de l’Allocation de disques de disque dur virtuel fixes supplémentaires à l’aide de contrôleurs virtuels et de canaux augmente le débit de disque par rapport à un seul disque du disque dur virtuel.  
  
2.  **Optimiser les performances du réseau –** suivez les étapes décrites dans la section « Optimiser les performances du réseau » de [liste de vérification : optimisation des performances sur Hyper-V](~/technical-guides/checklist-optimizing-performance-on-hyper-v.md). Lors de l’exécution de plusieurs machines virtuelles de Hyper-V sur le même hôte Hyper-V, il est particulièrement importante pour suivre les recommandations de la section « Configurer Hyper-V virtuels qui s’exécutent sur le même Hyper-V hôte de l’ordinateur à utiliser un un réseau privé virtuel » de [optimisations du réseau](../technical-guides/network-optimizations.md).  
  
 En raison de la nature sans état de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]supplémentaires [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] machines virtuelles peuvent être facilement ajoutés à l’environnement comme requis pour fournir la montée en puissance parallèle et améliorer les performances générales du système.  
  
 Le graphique ci-dessous illustre les performances de SQL Server sur les différentes plateformes de test :  
  
 ![Indicateurs de Performance clés SQL](../technical-guides/media/sqlkpi.gif "SQLKPI")  
indicateurs de performance clés SQL  
  
 Le tableau ci-dessous illustre les performances relatives de l’indicateur collectées pour chaque configuration. Chaque jeu de résultats est calculée en pourcentage de la configuration de base indicateur de performance clé  
  
|Indicateur de performance clé|Virtuel BizTalk/physiques SQL|Virtuel BizTalk/virtuel SQL sur des hôtes distincts|Virtuel SQL BizTalk/virtuel dans l’environnement de consolidé|  
|---------|-----------------------------------|----------------------------------------------------|--------------------------------------------------------------|  
|\SQL\Processor(_Total)\\% temps processeur|97.7%|98.4%|99.9%|  
|\SQL server : SQL SQL\nombre demandes par seconde|97.1%|83.3%|71.2%|  
  
 Pour plus d’informations sur la façon d’évaluer les performances d’e/s disque, consultez le **performances d’e/s du disque mesure** section de la rubrique [liste de vérification : mesure des performances sur Hyper-V](../technical-guides/checklist-measuring-performance-on-hyper-v.md).  
  
 Pour plus d’informations sur les meilleures pratiques lors de l’exécution de SQL Server 2008 dans un environnement Hyper-V, consultez le livre blanc « En cours d’exécution SQL Server 2008 in a Hyper-V environnement – et performances recommandations » disponible en téléchargement à [http : / / go.microsoft.com/fwlink/ ? LinkId = 144622](http://go.microsoft.com/fwlink/?LinkId=144622).