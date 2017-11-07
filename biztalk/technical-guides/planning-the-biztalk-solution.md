---
title: Planification de la Solution BizTalk | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 30d56a04-966a-46b1-861d-f5be4e58b7d2
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 337883ce2ca3b7f28def19898930d872928a8ce4
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="plan-for-your-biztalk-solution"></a>Planifier votre Solution BizTalk
Un des principaux objectifs de création de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est d’offrir une flexibilité maximale pour la prise en charge des scénarios de traitement autant que possible. En raison de cette avec une grande souplesse, un des principaux défis aux développeurs d’une solution BizTalk est pour déterminer comment exploiter les fonctionnalités disponibles dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour mieux répondre à leurs besoins. Planification de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] peut être décomposée en plusieurs phases distinctes qui sont résumés ci-dessous.  
  
## <a name="scoping-the-solution"></a>L’étendue de la Solution  
  
### <a name="performance-considerations"></a>Considérations relatives aux performances  
 Considérez les éléments suivants lorsque la portée de votre solution BizTalk :  
  
-   Les adaptateurs et/ou les accélérateurs sont nécessaires ?  
  
-   Quelles sont les conditions requises pour implémenter des orchestrations dans la solution ?  
  
-   Documenter les exigences de débit : quelles sont les exigences de débit maximal acceptable pour la solution ?  
  
-   Conditions de latence : la réactivité la solution doit-elle être pour les scénarios de sollicitation-réponse et requête-réponse ?  
  
-   Comment la solution permet de récupérer des périodes de pic de charge de document ?  
  
-   Quelles sont les exigences de haute disponibilité de la solution ?  
  
-   Quelles sont les exigences de suivi de document de la solution ?  
  
-   Quelles sont les caractéristiques de performances de toutes les applications dépendantes telles que l’autre système ou d’un service Web à distance ? Si les applications dépendantes ne conservez pas la charge requise les performances globales du système seront altérée en conséquence.  
  
-   Est l’application BizTalk consomme ne pas liées à des bases de données [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]? Par exemple, si l’application BizTalk consomme des tables dans une base de données SQL Server à l’aide de l’adaptateur SQL, sont les tables efficacement configurés ?  
  
### <a name="hardware-considerations"></a>Configuration matérielle requise  
 Lorsque la portée de la solution, créez un diagramme de matériel qui inclut les éléments suivants :  
  
-   Architecture de l’ordinateur (par exemple, x86, x64 et IA64)  
  
-   Configuration requise du processeur (par exemple, le type, la vitesse, nombre, cœurs et utilisation de l’hyperthreading)  
  
-   Mémoire RAM requise pour chaque ordinateur  
  
-   Stockage de disque local (type, taille, vitesse)  
  
-   Réseau SAN (exigences de stockage : nombre de numéros d’unités logiques ; Type de carte réseau SAN)  
  
-   Cartes réseau (numéro de chaque ordinateur, 100 mégabits (Mbit/s) et 1 Gigabit (1 Gbit/s).)  
  
-   Comment les pare-feux être déployé dans la solution ?  
  
-   Matériel d’équilibrage de charge réseau servira ?  
  
-   Sont des ordinateurs spécifiques à mettre en cluster ?  
  
-   Vous utilisent un environnement virtuel impliquant Microsoft Hyper-V Server ou autres produits de virtualisation ?  
  
## <a name="planning-the-solution"></a>Planification de la Solution  
  
### <a name="solution-milestones-timeline"></a>Chronologie des jalons de solution  
 Créer une planification avec étapes majeures pour l’achèvement des aspects spécifiques de votre solution BizTalk. Définition des étapes majeures spécifiques augmente la probabilité que la solution sera effectuée en temps voulu.  
  
### <a name="non-microsoft-software-considerations"></a>Considérations relatives à des logiciels non Microsoft  
 Considérez les éléments suivants lors de logiciels non Microsoft seront utilisé avec la solution :  
  
-   Déterminer comment le logiciel ou matériel requis être obtenu.  
  
-   Planifier la capacité et de dimensionnement pour vous assurer que des logiciels non Microsoft n’est pas un goulet d’étranglement dans votre solution.  
  
-   Déterminer un plan d’action pour l’installation de logiciels non Microsoft requis.  
  
-   Créer un plan d’action pour la configuration et l’optimisation des logiciels non Microsoft requis.  
  
## <a name="preparing-for-the-solution"></a>Préparation de la Solution  
 Inclure les éléments suivants dans la phase de préparation :  
  
### <a name="detailed-design-of-the-solution-platform"></a>Conception détaillée de la plateforme de Solution  
 Conception d’une solution détaillées facilite les communications et évite les hypothèses, afin d’amélioreront la flexibilité et l’efficacité de toutes les activités. Vous devez entièrement documenter les éléments suivants :  
  
-   Bases de données BizTalk Server et comment elles seront distribuées sur plusieurs ordinateurs.  
  
-   Conception de l’hôte BizTalk et les descriptions de chaque ordinateur hôte et leurs instances.  
  
-   Description de chaque orchestration.  
  
-   Description de chaque pipeline.  
  
-   Description des composants personnalisés tels que des assemblys .NET et des composants COM +.  
  
 **Diagrammes de flux de message**  
  
 Créer des diagrammes de flux de message détaillé pour aider à éviter des hypothèses de confusion ou false sur ce qui doit pour se produire pour les messages au cours du traitement. Les détails suivants doivent être pris en compte lors de la création de diagrammes de flux de message :  
  
-   Décrire le cycle de vie de chaque type de message à partir du moment qu’il arrive à un emplacement de réception jusqu'à ce que tous les messages résultants sont envoyés et toutes les liés au traitement est terminé.  
  
-   Décrire le traitement des modifications des conditions d’erreur.  
  
-   Inclure des détails sur la corrélation, les accusés de réception et les accusés de réception.  
  
-   Incluent des informations de condition de performances concernant la latence et le débit.  
  
 **Détails des logiciels non Microsoft**  
  
 Tous les logiciels non Microsoft sont utilisé doivent être entièrement documentée dans le cadre de la conception de solution détaillées.  
  
 **Pile de matérielles détaillées**  
  
 S’appuyant sur le diagramme de matériel de haut niveau créé précédemment, les informations matérielles suivantes doivent être entièrement documentées :  
  
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
  
 **Pile logicielle détaillées**  
  
 Les logiciels suivants doivent être documentées :  
  
-   Architecture, les éditions et versions de système d’exploitation spécifique  
  
-   Fonctionnalités du système d’exploitation spécifique  
  
-   Logiciel spécifique installé sur chaque ordinateur  
  
-   Pilotes spécifiques  
  
-   Service Packs et autres mises à jour  
  
-   Valeurs de configuration pour toutes les fonctionnalités de système d’exploitation et les logiciels utilisées si elles diffèrent des valeurs par défaut  
  
## <a name="building-out-the-environment-for-the-solution"></a>Création de l’environnement de la Solution  
 Instructions détaillées pour l’installation de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et la configuration logicielle requise est dans le [Guides d’Installation de BizTalk Server](../install-and-config-guides/biztalk-server-what-s-new-installation-configuration-and-upgrade.md).
  
## <a name="see-also"></a>Voir aussi  
 [Planification du niveau BizTalk Server](../technical-guides/planning-the-biztalk-server-tier.md)
