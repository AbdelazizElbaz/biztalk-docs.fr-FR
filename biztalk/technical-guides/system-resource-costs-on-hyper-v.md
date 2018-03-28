---
title: Les coûts des ressources système sur Hyper-V | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9f25a76c-1c41-41c0-b28d-d7473dbe1cd1
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 491c71a446829ddddfc4d7c55053b94dcf7fc9d1
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="system-resource-costs-on-hyper-v"></a>Coûts des ressources système sur Hyper-V
## <a name="system-resource-costs-associated-with-running-a-guest-operating-system-on-hyper-v"></a>Coûts des ressources système associées à l’exécution d’un système d’exploitation invité sur Hyper-V  
 Comme avec n’importe quel logiciel de virtualisation de serveur, il existe une certaine surcharge liée à l’exécution du code de virtualisation doit prendre en charge les systèmes d’exploitation invités s’exécutant sur Hyper-V. La liste suivante résume la surcharge liée à des ressources spécifiques lors de l’exécution de systèmes d’exploitation invités sur les ordinateurs virtuels Hyper-V :  
  
### <a name="cpu-overhead"></a>Surcharge du processeur  
 Le processeur surcharge associé au système d’exploitation invité en cours d’exécution dans un ordinateur virtuel Hyper-V a été trouvé à la plage comprise entre 9 et 12 %.  Par exemple, un système d’exploitation invité exécute généralement sur un ordinateur virtuel Hyper-V est disponible 88-91 % des ressources processeur disponibles pour un système d’exploitation équivalent en cours d’exécution sur un matériel physique.  
  
### <a name="memory-overhead"></a>Surcharge de mémoire  
 Pour l’ordinateur hôte Hyper-V, le coût de mémoire associé à un système d’exploitation invité en cours d’exécution sur un ordinateur virtuel Hyper-V a été observé, soit environ 300 Mo pour l’hyperviseur, ainsi que 32 Mo pour la première Go de mémoire RAM allouée à chaque ordinateur virtuel et un autre 8 Mo pour chaque Go de RAM supplémentaire allouée à chaque ordinateur virtuel. Pour plus d’informations sur l’allocation de mémoire pour les systèmes d’exploitation invités s’exécutant sur un ordinateur virtuel Hyper-V, consultez la section « Optimisation des performances mémoire » dans [liste de vérification : optimisation des performances sur Hyper-V](~/technical-guides/checklist-optimizing-performance-on-hyper-v.md).  
  
### <a name="network-overhead"></a>Surcharge du réseau  
 Latence du réseau directement attribuables à l’exécution d’un système d’exploitation invité dans un ordinateur virtuel Hyper-V a été observée est inférieur à 1 ms et le système d’exploitation invité généralement conserver une longueur de file d’attente de sortie de réseau de moins d’une. Pour plus d’informations sur la mesure de la longueur de file d’attente de sortie de réseau, consultez la section « Mesurer les performances réseau » dans [liste de vérification : mesure des performances sur Hyper-V](../technical-guides/checklist-measuring-performance-on-hyper-v.md).  
  
### <a name="disk-overhead"></a>Surcharge de disque  
 Lorsque vous utilisez la fonctionnalité de disque direct dans Hyper-V, disque surcharge d’e/s associé à un système d’exploitation invité dans un ordinateur virtuel Hyper-V a été trouvé à la plage comprise entre 6 et 8 %. Par exemple, un système de d’exploitation invité s’exécutant sur Hyper-V de généralement avait disponible 94-92 % du disque disponibles pour un système d’exploitation équivalent en cours d’exécution sur un matériel physique, mesurée par les performances du disque source ouvert outil IOMeter des tests de performances d’e/s.  
  
 Pour plus d’informations sur la mesure de la latence de disque sur un système Hyper-V hôte ou invité d’exploitation à l’aide de l’Analyseur de performances, consultez la section « Mesure les performances de d’e/s disque » dans [liste de vérification : mesure des performances sur Hyper-V](../technical-guides/checklist-measuring-performance-on-hyper-v.md).  
  
 Le reste de cette section fournit des informations générales sur le serveur BizTalk les performances de disque, décrit les paramètres de configuration de test utilisées et fournit un résumé des résultats de test obtenus.  
  
#### <a name="disk-performance-when-running-a-biztalk-server-solution-on-hyper-v"></a>Performances du disque lors de l’exécution d’une Solution BizTalk Server sur Hyper-V  
 BizTalk Server est extrêmement de base de données applications exigeantes qui peuvent nécessiter la création de bases de données jusqu'à 13 dans SQL Server. BizTalk Server conserve les données sur le disque avec une fréquence élevée et en outre, le fait dans le contexte d’une transaction MSDTC. Par conséquent, les performances de la base de données est primordiale pour les performances globales d’une solution BizTalk Server. Hyper-V fournit un contrôleur SCSI synthétique et un pilote de filtre IDE qui les deux fournissent des gains de performance significatifs à l’aide d’un périphérique IDE émulé comme est fourni avec Virtual Server 2005.  
  
 Configurer les disques pour les volumes de données à l’aide du contrôleur SCSI. Cela garantit que les services d’intégration sont installés, car le contrôleur SCSI ne peut être installé que si les services d’intégration Hyper-V sont installés alors que le contrôleur IDE émulé est disponible sans avoir à installer les services d’intégration Hyper-V. E/s de disque effectuées à l’aide du contrôleur SCSI, soit le pilote du filtre IDE fourni avec les services d’intégration est considérablement plus performants que les performances d’e/s fourni avec le contrôleur IDE émulé sur disque. Par conséquent, pour vous assurer de disque optimiser les performances d’e/s pour les fichiers de données dans un environnement virtualisé Hyper-V, installez les services d’intégration sur les système d’exploitation hôte et invité et configurer les disques pour les volumes de données avec le contrôleur SCSI synthétique. Pour les charges d’e/s de stockage très importantes qui s’étendent sur plusieurs lecteurs de données, chaque disque dur virtuel doit être attaché à un contrôleur SCSI synthétique distinct pour meilleures performances globales. En outre, chaque disque dur virtuel doit être stockée sur des disques physiques distincts ou des numéros d’unités logiques.  
  
#### <a name="measuring-passthrough-disk-performance"></a>Mesurer les performances de disque direct  
 Pendant un exercice de consolidation, il est important de veiller à une utilisation maximale des ressources disponibles. Comme indiqué précédemment, le stockage d’e/s sur les volumes de données SQL joue un rôle significatif dans les performances globales d’une solution BizTalk Server. Par conséquent, dans le cadre de ce guide, les performances relatives d’un disque physique sur les performances d’un disque direct dans Hyper-V a été testé. Les performances relatives de données MessageBox de lecteur dans Physical_SQL01 et Virtual_SQL01 a été mesuré à l’aide de la IOMeter outil open source initialement développé par Intel Corporation et maintenant gérés par l’open Source Development Lab (OSDL). Pour plus d’informations sur IOMeter, consultez [ http://go.microsoft.com/fwlink/?LinkId=122412 ](http://go.microsoft.com/fwlink/?LinkId=122412).  
  
 Les tableaux suivants décrivent la configuration de matériel physique et virtuel utilisée dans l’environnement de test, les options de configuration IOMeter qui ont été utilisées, une description du test qui a été exécuté et un résumé des résultats.  
  
#### <a name="configuration-used-for-testing"></a>Utilisé pour le test de configuration  
  
### <a name="physicalsql01"></a>Physical_SQL01  
  
|||  
|-|-|  
|**Modèle**|HP DL580|  
|**Processor**|Processeur quadruple, cœurs Intel Xeon 2,4 Ghz|  
|**Mémoire**|8 GO|  
|**Mise en réseau**|Carte HP NC3T3i multifonction Gigabit Server|  
|**Configuration du réseau SAN**|SAN stockage en attachement direct (voir tableau ci-dessous)|  
  
### <a name="physicalsql01--san-configuration"></a>Physical_SQL01 – Configuration du réseau SAN  
  
|Lettre de lecteur| Description|Taille des unités logiques|Configuration RAID|  
|------------------|-----------------|--------------|------------------------|  
|G :|Data_Sys|10|RAID 0 + 1|  
|H :|Logs_Sys|10|RAID 0 + 1|  
|FAIRE :|Data_TempDb|50|RAID 0 + 1|  
|J :|Logs_TempDb|50|RAID 0 + 1|  
|K :|Data_BtsMsgBox|300|RAID 0 + 1|  
|L :|Logs_BtsMsgBox|100|RAID 0 + 1|  
|M :|MSDTC|5|RAID 0 + 1|  
  
### <a name="hyper-vhostsql01"></a>Hyper-V_Host_SQL01  
  
|||  
|-|-|  
|**Modèle**|HP DL580|  
|**Processor**|Processeur quadruple, cœurs Intel Xeon 2,4 Ghz|  
|**Mémoire**|32 Go|  
|**Mise en réseau**|Broadcom BCM5708C NetXtreme II GigEHP DL380 G5|  
  
### <a name="virtualsql01---virtual-machine-configuration"></a>Virtual_SQL01 - Configuration d’ordinateur virtuel  
  
|||  
|-|-|  
|**Processeurs virtuels**|4 allouée|  
|**Mémoire**|8 GO|  
|**Mise en réseau**|Mise en réseau de l’ordinateur virtuel connecté à :<br />Broadcom BCM5708C NetXtreme II GigE|  
|**Configuration de disque dur**|**Contrôleur IDE** – 30 Go, disque dur virtuel fixé pour le système d’exploitation<br />**Contrôleur SCSI** -7 directement attaché LUN de réseau SAN de relais (voir tableau ci-dessous)|  
  
### <a name="virtualsql01--san-configuration"></a>Virtual_SQL01 – Configuration du réseau SAN  
  
|Lettre de lecteur| Description|Taille des unités logiques|Configuration RAID|  
|------------------|-----------------|--------------|------------------------|  
|G :|Data_Sys|10|RAID 0 + 1|  
|H :|Logs_Sys|10|RAID 0 + 1|  
|FAIRE :|Data_TempDb|50|RAID 0 + 1|  
|J :|Logs_TempDb|50|RAID 0 + 1|  
|K :|Data_BtsMsgBox|300|RAID 0 + 1|  
|L :|Logs_BtsMsgBox|100|RAID 0 + 1|  
|M :|MSDTC|5|RAID 0 + 1|  
  
#### <a name="iometer-configuration"></a>Configuration de IOMeter  
 L’outil IOMeter peut être utilisé comme un test d’évaluation et l’outil de résolution des problèmes en répliquant les performances en lecture/écriture d’applications. IOMeter est un outil configurable qui peut être utilisé pour simuler des différents types de performances. Pour des raisons de ce scénario de test, les paramètres de configuration de IOMeter ont été définis comme décrit dans le tableau ci-dessous sur les deux physique [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] ordinateur qui a été testé et sur le système d’exploitation invité qui s’exécutait [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] dans un ordinateur virtuel Hyper-V :  
  
### <a name="iometer--passthrough-disk-comparison-test-configuration"></a>IOMeter – Configuration de Test de comparaison de disque direct  
  
|||  
|-|-|  
|**Longueur du test**|10 minutes|  
|**Temps d’accélération**|30 secondes|  
|**Nombre de threads de travail**|4|  
|**Taille de la demande de transfert**|2 KO|  
|**Distribution de lecture/écriture**|66 % de lecture, écriture de 33 %|  
|**Longueur de rafale**|E/s 1|  
|**Lecteur cible**|K:\|  
  
#### <a name="test-description"></a>Description du test  
 Le [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] service a été arrêté sur les deux serveurs pour vérifier que IOMeter a le processus uniquement effectuer d’e/s sur le disque. Le numéro d’unité logique d’utilisé dans ce test étaient tous deux situés sur le même réseau SAN qui était dédié à cet environnement de laboratoire. Aucune autre activité d’e/s a été effectuée sur le réseau SAN pendant le test pour vous assurer que les résultats ont été pas inégale. L’exécution du test puis en exécutant l’outil IOMeter localement à partir de chaque [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] et compteurs du moniteur de performances suivantes ont été collectés :  
  
 **Collectées à partir de Virtual_SQL01 et Physical_SQL01**:  
  
-   \LogicalDisk(*)\\\*  
  
-   \PhysicalDisk(*)\\\*  
  
 **Collectées à partir de l’ordinateur virtuel Hyper-V_02**:  
  
-   Dispositif de stockage virtuel \Hyper-V\\*  
  
### <a name="results"></a>Résultats  
 Le disque direct n’a pas pu atteindre plus de 90 % du débit de la LUN SAN connecté directement à Physical_SQL01.  Total, lecture et écriture e/s par seconde ont été intégralement dans 10 % comme était le total de Mo transféré par seconde.  Temps de réponse des disques sains doivent être entre ms 15-1 pour la lecture et écriture. Temps de réponse moyens d’e/s étaient inférieure à 4 ms sur les deux disques. Temps de réponse des lectures aléatoires était 5,4 ms sur physique et 5.7 ms sur le disque direct. Temps de réponse d’écriture était inférieure à 0,5 ms dans les environnements physiques et virtuels.  
  
 Les résultats indiquent qu’un disque direct à l’aide du contrôleur SCSI compatible peut fournir plus 90 % des performances d’un disque physique connecté directement. Performances du sous-système d’e/s sont essentielle pour le bon fonctionnement de BizTalk Server, en fournissant une excellente heures de débit et de réponse Hyper-V est un excellent candidat pour la consolidation d’un environnement BizTalk Server. Le tableau ci-dessous fournit qu'un résumé des résultats du test de disque observées lors de la comparaison des performances d’un disque de transfert direct vers un disque physique :  
  
|Mesure|Physical_SQL01 (Physical Disk)|Virtual_SQL01 (passthrough)|Performances relatives de disques directs vers les disques physiques|  
|-----------------|---------------------------------------|------------------------------------|-----------------------------------------------------------------|  
|Total e/s par seconde|269.73|250.47|92.86%|  
|E/s de lecture par seconde|180.73|167.60|92.74%|  
|Écriture d’e/s par seconde|89.00|82.87|93.11%|  
|Nombre total de Mo par seconde|0.53|0.49|92.45%|  
|Moyenne de lecture des temps de réponse (ms)|5.4066|5.7797|93.54%|  
|Temps de réponse moyen d’écriture (ms)|0.2544|0.3716|% De 68.42 **Remarque :** bien que les performances relatives des disques pass-through pour le temps de réponse moyen d’écriture a été % 68.42 des performances de disques physiques, le temps de réponse moyen d’écriture des disques relais était toujours bien compris Permet d’établir des limites acceptables de 10 ms.|  
|Temps de réponse moyen d’e/s (ms)|3.7066|3.9904|93.89%|  
  
> [!NOTE]  
>  Les valeurs en pourcentage pour le Total des e/s par seconde, e/s de lecture par seconde, écrire des e/s par seconde et nombre Total de Mo par seconde ont été calculées en divisant les valeurs de disque direct par les valeurs correspondantes de disque physique.  
>   
>  Les valeurs en pourcentage pour la moyenne de lecture des temps de réponse (ms), le temps de réponse (ms) d’écriture moyenne et temps de réponse d’e/s moyenne (ms) ont été calculées en divisant les valeurs de disque physique par les valeurs de disque direct correspondantes.