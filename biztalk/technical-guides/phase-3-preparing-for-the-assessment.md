---
title: "Phase 3 : Préparation de l’évaluation | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d153ed62-f2cc-4080-8912-c98ecdd329f5
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 890047f6a13352d89d33d9514883dc20eacd4001
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="phase-3-preparing-for-the-assessment"></a>Phase 3 : Préparation de l’évaluation
La phase d’une évaluation des performances peut être considéré comme « comment » à la phase de portée « que se passe-t-il » et la phase de planification de préparation 's « lorsque. » À ce stade dans l’évaluation des performances, toutes les parties prenantes doivent ont convenu l’étendue de l’engagement et les plans d’effectuer le laboratoire. Il est dans la phase de préparation de l’évaluation des performances où les plans sont exécutées et les étapes pour préparer l’exécution des procédures du laboratoire de performances.  
  
 Cette rubrique décrit les différents aspects de la phase de préparation d’une évaluation de performances de BizTalk Server.  
  
## <a name="detailed-design-of-the-solution-platform"></a>Conception détaillée de la plateforme de solution  
 Conception d’une solution détaillées facilite les communications et évite les hypothèses, afin d’amélioreront la flexibilité et l’efficacité de toutes les activités. Vous devez entièrement documenter les éléments suivants :  
  
-   **Bases de données BizTalk Server et comment elles seront distribuées sur plusieurs ordinateurs** -performances de SQL Server sont un des principaux facteurs de performances globales de BizTalk Server. Si SQL Server rencontre des contraintes de ressources, cela aura un impact sur la capacité de BizTalk Server pour traiter les messages. Le principal facteur qui influencent les performances de base de données BizTalk est la vitesse de qu’ils sont hébergés sur des disques. Séparer les fichiers de base de données et du journal des transactions pour chaque BizTalk base de données sur des lecteurs distincts ou l’unité logique de réseau SAN a démontré considérablement améliorer les performances globales de BizTalk Server. Par conséquent, il est important que ces informations soient enregistrés de façon facilement accessible. Les valeurs qui seront utilisés dans l’environnement de production doivent être documentées dans la conception de solution détaillées. Le tableau suivant fournit un exemple de la manière dont cela est possible.  
  
    |Base de données BizTalk|Nom de volume|Fichiers|Numéro d’unité logique # ou ML_ #|Taille LUN physique (Go)|  
    |----------------------|-----------------|-----------|---------------------|------------------------------|  
    |MessageBox|Data_TempDb_1|Fichiers de données TEMPDB, MASTER et MSDB|1|134|  
    ||Logs_TempDb_1|Fichiers journaux des transactions TEMPDB, MASTER et MSDB|2|134|  
    ||Data_BtsMsgBox|Fichier de données BizTalkMsgBoxDb|3|134|  
    ||Logs_BtsMsgBox|Fichier journal des transactions BizTalkMsgBoxDb|4|134|  
    |BAM|Data_TempDb_2|Fichiers de données TEMPDB, MASTER et MSDB|5|67|  
    ||Logs_TempDb_2|Fichiers journaux des transactions TEMPDB, MASTER et MSDB|6|67|  
    ||Data_BAM|Fichier de données BAMPrimaryImport|7|134|  
    ||Logs_BAM|Fichier journal des transactions BAMPrimaryImport|8|134|  
    |Bases de données des suivis BizTalk, la gestion, l’authentification unique et du moteur de règles|Data_TempDb_3|Fichiers de données TEMPDB, MASTER, MSDB, BizTalkDTADb, BizTalkMgmtDb, ENTSSO et BizTalkRuleEngineDb|9|67|  
    ||Logs_TempDb_3|Fichiers journaux des transactions TEMPDB, MASTER, MSDB, BizTalkDTADb, BizTalkMgmtDb, ENTSSO et BizTalkRuleEngineDb|10|67|  
  
-   **Conception de l’hôte BizTalk et les descriptions de chaque ordinateur hôte et leurs instances.**  
  
-   **Description de chaque orchestration.**  
  
-   **Description de chaque pipeline.**  
  
-   **Description des composants personnalisés tels que des assemblys .NET et des composants COM +.**  
  
## <a name="detailed-architecture-diagram"></a>Diagramme d’architecture détaillée  
 Le diagramme suivant illustre un diagramme d’architecture qui peut être utilisé pour une évaluation des performances.  
  
 ![Diagramme d’Architecture BizTalk](../technical-guides/media/architecturediagram.gif "ArchitectureDiagram")  
Diagramme de l'architecture BizTalk  
  
## <a name="message-flow-diagrams"></a>Diagrammes de flux de message  
 Créer des diagrammes de flux de message détaillé pour éviter toute confusion ou false hypothèses concernant ce qui doit pour se produire pour les messages au cours du traitement.  
  
 En matière de guidage une solution BizTalk, nous avons tendance à considérer que le flux de messages via le système. Cette perspective de flux de messages est particulièrement importante lors de la tester les performances car toutes les parties du flux doivent être considérées comme des goulots d’étranglement potentiels. Avoir un diagramme de flux de message empêche toute confusion ou fausses hypothèses concernant ce qui doit pour se produire pour les messages au cours de chaque test exécuté.  
  
 Dans l’exemple suivant, créé à l’aide de formes Visio, tout le monde sur le projet, quelle que soit l’arrière-plan peut comprendre rapidement comment un message atteint dans le système, quelles parties des solutions interagissent avec le message, et enfin sur lequel le message arrive après lors du traitement.  
  
 ![Diagramme de flux de message](../technical-guides/media/11c5afac-5c1b-42a5-8947-7c6d0ca4e2df.gif "11c5afac-5c1b-42a5-8947-7c6d0ca4e2df")  
Diagramme du flux de message  
  
 Les détails suivants doivent être pris en compte lors de la création de diagrammes de flux de message :  
  
-   Décrire le cycle de vie de chaque type de message à partir du moment qu’il arrive à un emplacement de réception jusqu'à ce que tous les messages résultants sont envoyés et toutes les liés au traitement est terminé.  
  
-   Décrire le traitement des modifications des conditions d’erreur.  
  
-   Inclure des détails sur la corrélation, les accusés de réception et les accusés de réception.  
  
-   Inclure des détails sur la dépendance sur des systèmes externes.  
  
-   Incluent des informations de condition de performances concernant la latence et le débit.  
  
## <a name="third-party-software-details"></a>Détails des logiciels tiers  
 Tous les logiciels non Microsoft sont utilisé doivent être entièrement documentée dans le cadre de la conception de solution détaillées.  
  
## <a name="detailed-lab-hardware-stack"></a>Pile de matériel de laboratoire détaillées  
 S’appuyant sur le diagramme de matériel de niveau supérieur créé précédemment, les informations matérielles suivantes doivent être entièrement documentées :  
  
-   Processeurs  
  
    -   Type  
  
    -   Vitesse  
  
    -   Nombre de cœurs  
  
    -   Hyperthreading  
  
-   Mémoire  
  
    -   Montant  
  
    -   Vitesse  
  
    -   Parité  
  
-   Réseau  
  
    -   Nombre de cartes d’interface réseau (NIC)  
  
    -   Vitesse du réseau  
  
-   RÉSEAU SAN  
  
    -   Nombre de cartes réseau SAN de chaque ordinateur  
  
    -   Nombre de numéros d’unité logique (LUN) pour chaque ordinateur et l’objectif de chaque numéro d’unité logique  
  
    -   Vitesse de zone de stockage (SAN) cartes du réseau  
  
    -   Détails de configuration de carte réseau SAN  
  
    -   Allocation de disque SAN, mise en forme et le partitionnement  
  
-   Disque  
  
    -   Détails du disque local pour chaque ordinateur  
  
    -   Mise en forme utilisée pour les disques locaux  
  
    -   Partitionnement des détails pour les disques locaux  
  
-   Cache  
  
    -   Quantité de mémoire Cache L2  
  
    -   Quantité de mémoire Cache L3  
  
## <a name="detailed-lab-software-stack"></a>Pile de logiciels détaillées de laboratoire  
 Les logiciels suivants doivent être documentées :  
  
-   Architecture, les éditions et versions de système d’exploitation spécifique  
  
-   Fonctionnalités du système d’exploitation spécifique  
  
-   Logiciel spécifique installé sur chaque ordinateur  
  
-   Pilotes spécifiques  
  
-   Service Packs et autres mises à jour  
  
-   Valeurs de configuration pour toutes les fonctionnalités de système d’exploitation et les logiciels utilisées si elles diffèrent des valeurs par défaut  
  
## <a name="see-also"></a>Voir aussi  
 [Phases d’une évaluation des performances](../technical-guides/phases-of-a-performance-assessment.md)