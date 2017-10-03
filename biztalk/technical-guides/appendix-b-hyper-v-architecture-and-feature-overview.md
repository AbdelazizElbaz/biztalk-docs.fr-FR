---
title: "Annexe b : Architecture Hyper-V et vue d’ensemble de la fonctionnalité | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 87b6b9a0-a470-43f7-b076-36075477cc34
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9e6282b6f5a5784b80d58a1a1737389ee23e01e2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="appendix-b-hyper-v-architecture-and-feature-overview"></a>Annexe b : Architecture Hyper-V et la vue d’ensemble de la fonctionnalité
Cette rubrique fournit une vue d’ensemble de l’architecture de Hyper-V, décrit les avantages et inconvénients de Hyper-V.  
  
## <a name="hyper-v-architecture"></a>Architecture Hyper-V  
  
 Hyper-V est une plateforme de virtualisation basée sur un hyperviseur et une technologie pour l’une des [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]de fonctionnalités de sélection, la Migration dynamique. Avec Hyper-V version 1.0, Windows Server 2008 était en mesure de la Migration rapide, qui peut déplacer des ordinateurs virtuels entre les hôtes physiques que quelques secondes de temps d’arrêt. Avec la Migration en direct, se déplace entre les cibles physiques se produire dans milliseconde, ce qui signifie que les opérations de migration sont invisibles pour les utilisateurs connectés. Pour découvrir les nouvelles fonctionnalités et améliorations dans [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] Hyper-V, consultez [Nouveautés de Hyper-V dans Windows Server 2008 R2](http://go.microsoft.com/fwlink/?LinkID=202427).  
  
 L’hyperviseur est la plateforme de virtualisation de processeur spécifique qui peut héberger plusieurs machines virtuelles (VM) qui sont isolés les uns des autres, mais partagent les ressources matérielles sous-jacentes à la virtualisation les processeurs, la mémoire et les périphériques d’e/s.  
  
 Les systèmes d’exploitation invités s’exécutant dans un ordinateur virtuel Hyper-V fournissent des performances approche les performances du système d’exploitation en cours d’exécution sur un matériel physique *si* les pilotes de clients (VSC) de serveur virtuel nécessaires et les services sont installés sur le système d’exploitation invité. Code de client (VSC) de serveur virtuel Hyper-V, également appelé Hyper-V compatibles avec des e/s, permet un accès direct à la « Bus de l’ordinateur virtuel » de Hyper-V et est disponible avec l’installation des services d’intégration Hyper-V. Les deux [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] et [!INCLUDE[btsWinVista](../includes/btswinvista-md.md)] prise en charge Hyper-V compatibles avec des e/s avec les services d’intégration Hyper-V. Services d’intégration Hyper-V qui fournissent des pilotes VSC sont également disponibles pour les autres systèmes d’exploitation.  
  
 Hyper-V prend en charge d’isolation en termes d’une partition. Une partition est une unité logique d’isolation, pris en charge par l’hyperviseur, dans laquelle s’exécutent les systèmes d’exploitation. L’hyperviseur Microsoft doit avoir au moins une partition parente ou racine, en cours d’exécution [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]. La pile de virtualisation s’exécute dans la partition parente et a un accès direct aux périphériques matériels. La partition racine puis crée les enfants des partitions qui hébergent les systèmes d’exploitation invités. Une partition racine crée des partitions enfants à l’aide de l’interface de programmation d’application (API) hypercall.  
  
 Partitions n’ont pas accès au processeur physique, ni qu’ils gèrent les interruptions processeur. Au lieu de cela, ils ont une vue virtuelle sur le processeur et s’exécuter dans une région de l’adresse mémoire virtuelle qui est privée pour chaque partition de l’invité. L’hyperviseur gère les interruptions au processeur et les redirige vers la partition respectif. Hyper-V peut également matériel accélérer la traduction d’adresses entre les différents espaces d’adressage virtuels invités à l’aide d’une entrée sortie mémoire gestion unité (IOMMU) qui est indépendante du matériel de gestion de mémoire utilisé par le processeur. Un IOMMU est utilisée pour remapper les adresses de mémoire physique pour les adresses qui sont utilisées par la partition enfant.  
  
 Partitions enfants n’ont pas accès direct aux autres ressources matérielles également et sont présentées un affichage virtuel des ressources, comme les périphériques virtuels (VDEV). Les demandes pour les périphériques virtuels sont redirigées via le VMBus ou de l’hyperviseur pour les périphériques dans la partition parente, qui gère les demandes. Le VMBus est un canal de communication entre des partitions logiques. La partition parente héberge les fournisseurs de services de virtualisation (vsp) qui communiquent sur le VMBus pour gérer les demandes d’accès de périphérique à partir des partitions enfants. Hébergent des partitions enfants consommateurs de services de virtualisation (VSC) qui redirigent les demandes de périphérique vers vsp dans la partition parente via le VMBus. Tout ce processus est transparent pour le système d’exploitation invité.  
  
 Périphériques virtuels peuvent également tirer parti d’une fonctionnalité de virtualisation de Windows Server, nommée compatibles avec une e/s de stockage, mise en réseau, des graphiques et des sous-systèmes d’entrée. E/s compatibles est une implémentation de virtualisation prenant en charge spécialisée haut niveau de protocoles de communication (par exemple, SCSI) qui utilisent le VMBus directement, en ignorant toutes les couches d’émulation de périphérique. Cela rend la communication plus efficace mais nécessite un invité compatible hyperviseur et VMBus prenant en charge. Hyper-V compatibles avec des e/s et un noyau de hyperviseur prenant en charge est fourni via l’installation des services d’intégration Hyper-V. Composants d’intégration, y compris des pilotes de clients (VSC) de serveur virtuel, sont également disponibles pour les autres systèmes d’exploitation. Hyper-V nécessite un processeur qui comprend la virtualisation d’assistance matérielle, tels qu’est fourni avec Intel VT ou la technologie de virtualisation d’AMD-V (AMD).  
  
 Le diagramme suivant fournit une vue d’ensemble de l’architecture d’un environnement Hyper-V s’exécutant sur Windows Server 2008.  
  
 ![Hyper &#45; Présentation de l’architecture V](../technical-guides/media/eadd2a84-3936-4b48-a0e2-05b94882d848.gif "eadd2a84-3936-4b48-a0e2-05b94882d848")  
Vue d’ensemble de l’architecture Hyper-V  
  
 Les acronymes et termes utilisés dans le diagramme ci-dessus sont décrits ci-dessous :  
  
-   **APIC** – contrôleur d’interruptions Programmable avancé. Sorties d’un appareil qui permet des niveaux de priorité à attribuer à son interruption.  
  
-   **Partition enfant** – Partition qui héberge un système d’exploitation invité. Tous les accès à la mémoire physique et les périphériques en une partition enfant sont assuré par la Machine virtuelle Bus VMBus ou de l’hyperviseur.  
  
-   **Hypercall** – Interface pour la communication avec l’hyperviseur. L’interface hypercall prend en charge l’accès pour les optimisations fournies par l’hyperviseur.  
  
-   **Hyperviseur** – couche logicielle qui se trouve entre le matériel et un ou plusieurs systèmes d’exploitation. Son rôle principal est de fournir des environnements d’exécution isolés appelées partitions. L’hyperviseur contrôle et détermine l’accès à du matériel sous-jacent.  
  
-   **IC** : composant d’intégration. Composant qui permet des partitions pour la communication avec les autres partitions et de l’hyperviseur enfant.  
  
-   **Pile d’e/s** – pile d’entrée/sortie.  
  
-   **MSR** – mémoire Routine du Service.  
  
-   **La Partition racine** – gère les fonctions de niveau de l’ordinateur telles que les pilotes de périphérique et gestion de l’alimentation à chaud Ajout/Suppression du périphérique. La partition racine (ou parent) est la seule partition qui a un accès direct à la mémoire physique et les appareils.  
  
-   **VID** – pilote d’Infrastructure de virtualisation. Fournit des services de gestion de partition, les services de gestion de processeur virtuel et les services de gestion de mémoire pour les partitions.  
  
-   **VMBus** – mécanisme de communication basée sur le canal utilisé pour l’énumération de communication et d’appareils inter-partition sur les systèmes avec plusieurs partitions virtualisées actives. Le VMBus est installé avec les Services d’intégration Hyper-V.  
  
-   **VMMS** – Service de gestion d’ordinateurs virtuels. Responsable de la gestion de l’état de tous les ordinateurs virtuels dans les partitions enfants.  
  
-   **VMWP** – processus de travail de Machine virtuelle. Un composant de mode utilisateur de la pile de virtualisation. Le processus de travail fournit des services de gestion de machine virtuelle à partir de la [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] instance dans la partition parente pour les systèmes d’exploitation invités dans les partitions enfants. Le Service de gestion d’ordinateurs virtuels génère un processus de travail distinct pour chaque ordinateur virtuel en cours d’exécution.  
  
-   **VSC** – Client du Service de virtualisation. Une instance de périphérique synthétique qui réside dans une partition enfant. VSC utilisent les ressources matérielles qui sont fournis par les fournisseurs de services de virtualisation (vsp) dans la partition parente. Ils communiquent avec le vsp correspondante dans la partition parente sur le VMBus pour satisfaire que les demandes d’e/s des partitions enfant.  
  
-   **VSP** : fournisseur de services de virtualisation. Réside dans la partition racine et prennent en charge les périphériques synthétiques pour des partitions enfants sur l’ordinateur virtuel Bus VMBus.  
  
-   **WinHv** – bibliothèque d’Interface de l’hyperviseur Windows. WinHv est essentiellement un pont entre les pilotes d’un système d’exploitation partitionnées et de l’hyperviseur, ce qui permet d’appeler l’hyperviseur à l’aide des conventions d’appel Windows standards de pilotes  
  
-   **WMI** : le Service de gestion d’ordinateur virtuel expose un ensemble d’API basées sur Windows Management Instrumentation WMI pour gérer et contrôler les ordinateurs virtuels.  
  
 La plupart de ces termes sont définis dans le [Glossary8](../technical-guides/glossary8.md).  
  
> [!NOTE]  
>  Pour plus d’informations sur [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] Hyper-V, consultez [http://go.microsoft.com/fwlink/?LinkID=121187](http://go.microsoft.com/fwlink/?LinkID=121187).  
  
## <a name="advantages-of-hyper-v"></a>Avantages d’Hyper-V  
 Les avantages de l’exécution des solutions au niveau de l’entreprise dans un environnement virtualisé Hyper-V sont les suivants :  
  
1.  **Consolidation des ressources matérielles** -plusieurs serveurs physiques peuvent être facilement consolidées dans relativement moins de serveurs par l’implémentation de la virtualisation avec Hyper-V. Consolidation prend en charge pleinement parti des ressources matérielles déployé. Hyper-V dans Windows Server 2008 R2 peut désormais accéder jusqu'à 64 processeurs logiques sur les ordinateurs hôtes. Cette fonctionnalité ne prend pas uniquement parti des nouveaux systèmes multicœurs, cela signifie également que les ratios de consolidation de machine virtuelle plus élevés chaque hôte physique.  
  
2.  **Facilité d’administration**:  
  
    -   La consolidation et la centralisation des ressources simplifie l’administration.  
  
    -   Implémentation de la montée en puissance parallèle et de montée en puissance parallèle est pris en charge beaucoup plus facilement.  
  
3.  **Réduction des coûts de significatifs**:  
  
    -   Les coûts du matériel sont considérablement réduits, car plusieurs machines virtuelles qui s’exécute sur un seul ordinateur physique, par conséquent, un ordinateur physique distinct n’est pas requis pour chaque ordinateur.  
  
    -   Les coûts de licence Hyper-V sont inclus dans le coût de licence de [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]. Hyper-V peut également être acheté pour une utilisation en tant que produit autonome qui peut être installé sur [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] Server Core.  
  
    -   Alimentation peut être réduite considérablement par la consolidation des applications existantes sur un environnement Hyper-V virtualisé en raison du matériel physique réduit « empreinte » qui est requis.  
  
4.  **Prise en charge de la tolérance de panne via la gestion de clusters Hyper-V d’erreur** – étant donné que Hyper-V est une application prenant en charge de cluster [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] fournit hôte natif clustering prise en charge des ordinateurs virtuels créés dans un environnement virtualisé Hyper-V.  
  
5.  **Facilité de déploiement et de gestion**:  
  
    -   Consolidation des serveurs existants en moins de serveurs physiques simplifie le déploiement.  
  
    -   Une solution complète de gestion Hyper-V est disponible avec System Center Virtual Machine Manager. Pour plus d’informations sur System Center Virtual Machine Manager, consultez [http://go.microsoft.com/fwlink/?LinkID=111303](http://go.microsoft.com/fwlink/?LinkID=111303).  
  
6.  **Caractéristiques de performance clé Hyper-V**:  
  
    -   **Architecture de partage de matériel améliorées** - Hyper-V fournit un accès amélioré et l’utilisation des ressources de base, tels que des disques, le réseau, et des systèmes d’exploitation vidéo lorsqu’il est en cours d’exécution invité avec un noyau hyperviseur prenant en charge et qui sont équipés de code de client (VSC) requise du serveur virtuel (également appelé Hyper-V compatibles avec des e/s). Enlightments sont les améliorations apportées au système d’exploitation afin de réduire le coût de certaines fonctions du système d’exploitation tels que la gestion de la mémoire. Actuellement, les deux [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] et [!INCLUDE[btsWinVista](../includes/btswinvista-md.md)] prise en charge Hyper-V compatibles avec e/s et un noyau de hyperviseur prenant en charge via l’installation des services d’intégration Hyper-V. Composants d’intégration, y compris les pilotes VSC, sont également disponibles pour les autres systèmes d’exploitation.  
  
         Performances du disque sont critiques pour les applications d’entreprise gourmandes en e/s disque telles que Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et en plus de Hyper-V compatibles avec les e/s Hyper-V fournit la prise en charge de disque « Relais » qui fournit des performances du disque similaire à des performances de disques physiques. Notez que prise en charge du disque de « Relais » fournit des performances améliorées à un petit coût pour des raisons de commodité. Les disques de « Relais » sont essentiellement des disques/LUN physiques qui sont attachés à un ordinateur virtuel et ne prennent pas en charge certaines fonctionnalités de disques virtuels, tels que des captures instantanées d’ordinateur virtuel.  
  
    -   **Prise en charge de la virtualisation à assistance matérielle processeur** – Hyper-V tire pleinement parti de processeur assisté matérielle virtualisation prise en charge est disponible avec la technologie de processeur récent.  
  
    -   **Plusieurs noyaux (SMP) invité prise en charge du système d’exploitation** – Hyper-V offre la possibilité de prendre en charge jusqu'à quatre processeurs dans un environnement de machine virtuelle, ce qui permet aux applications de tirer pleinement parti des fonctionnalités de multithreading dans une machine virtuelle ordinateur.  
  
    -   **Invités 32 bits et 64 bits d’exploitation prise en charge système** – Hyper-V prend en charge l’exécution simultanée de différents types de systèmes d’exploitation, y compris les systèmes 32 bits et 64 bits sur des plates-formes de serveur différentes, telles que des fenêtres, Linux® et autres.  
  
7.  **Preuve d’enregistrement de suivi des** -clé les sites Web Microsoft MSDN ([http://msdn.microsoft.com](http://go.microsoft.com/fwlink/?LinkId=122019)) et TechNet ([http://technet.microsoft.com](http://go.microsoft.com/fwlink/?LinkID=64380)) sont hébergés dans les environnements Hyper-V.  
  
8.  **Prise en charge complète de produits** – étant donné que les applications d’entreprise Microsoft (par exemple, Exchange Server et SQL Server) sont entièrement testées en cours d’exécution dans Hyper-V, Microsoft prend en charge de correctif de code pour ces applications lorsque déployé et exécuté dans Hyper-V environnement.  
  
9. **Évolutivité** : plus la capacité de stockage, de la bande passante réseau et de puissance de traitement faire rapidement et facilement, répartition des ressources supplémentaires disponibles à partir de l’ordinateur hôte pour les ordinateurs virtuels invités. Cette opération peut nécessiter que l’ordinateur hôte est mis à niveau ou que les ordinateurs virtuels invités sont déplacés vers un ordinateur hôte plus performante.  
  
 Pour plus d’informations sur les avantages de l’utilisation de la technologie de virtualisation fournie avec Hyper-V, consultez [les avantages de la virtualisation](http://go.microsoft.com/fwlink/?LinkID=202419) de [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)].  
  
## <a name="disadvantages-of-hyper-v"></a>Inconvénients de Hyper-V  
 Certains inconvénients de l’exécution des solutions au niveau de l’entreprise dans un environnement virtualisé Hyper-V peuvent inclure :  
  
-   **Configuration matérielle requise –** en raison d’exigences de consolidation de serveurs, ordinateurs virtuels Hyper-V ont tendance à consommer plus d’UC et mémoire et nécessitent la bande passante d’e/s de disque que les serveurs physiques avec des charges de calcul comparables. Étant donné que le rôle de serveur Hyper-V est disponible seulement pour 64 bits et toutes les éditions de Windows Server 2008 R2 64 bits ne sont, le matériel physique doit prendre en charge la virtualisation d’assistance matérielle. Cela signifie que le processeur doit être compatible avec Intel VT ou la technologie de virtualisation d’AMD-V (AMD), le BIOS doit prendre en charge la prévention de l’exécution des données (PED) et la fonctionnalité doit être activée.  
  
-   **Configuration logicielle requise –** alors que la plupart des logiciels de Microsoft est prise en charge en cours d’exécution sur des ordinateurs virtuels Hyper-V, certains logiciels de Microsoft est toujours en cours en cours de test pour garantir la compatibilité avec un environnement virtualisé Hyper-V. Par exemple, la plupart des applications de niveau entreprise Microsoft prend en charge l’exécution sur Hyper-V ou sont dans le processus qui est testé pour la prise en charge sur Hyper-V. Toutes les versions de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] depuis [!INCLUDE[btsBizTalkServer2004](../includes/btsbiztalkserver2004-md.md)] sont pris en charge sur Hyper-V. Pour plus d’informations sur la prise en charge de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] sur Hyper-V, consultez [annexe c : BizTalk Server et la prise en charge de SQL Server Hyper-V](../technical-guides/appendix-c-biztalk-server-and-sql-server-hyper-v-supportability.md).