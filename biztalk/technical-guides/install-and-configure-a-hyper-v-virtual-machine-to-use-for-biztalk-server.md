---
title: "Installation et configuration d’un ordinateur virtuel de Hyper-V pour une utilisation avec BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 86add392-3cde-432d-95d6-c81d68716537
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b973053d3afa9c6d0b61de111d9da1c4fb7a0fb1
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="installing-and-configuring-a-hyper-v-virtual-machine-for-use-with-biztalk-server"></a>Installation et configuration d’un ordinateur virtuel de Hyper-V pour une utilisation avec BizTalk Server
Cette rubrique fournit des recommandations pour l’installation et la configuration de BizTalk Server dans un environnement Hyper-V, y compris des recommandations pour l’installation et configuration de l’ordinateur virtuel Hyper-V et des recommandations pour l’installation de BizTalk Server sur un Machine virtuelle de Hyper-V.  
  
## <a name="installing-and-configuring-hyper-v"></a>Installation et configuration d’Hyper-V  
 Avant d’installer Hyper-V, consultez [Nouveautés de Hyper-V dans Windows Server 2008 R2](http://go.microsoft.com/fwlink/?LinkID=202427). Le guide « Microsoft Hyper-V Server 2008 R2 Getting Started » fournit des détails sur la façon d’installer et configurer [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] Hyper-V. Le guide est disponible à l’adresse [http://go.microsoft.com/fwlink/?LinkID=202431](http://go.microsoft.com/fwlink/?LinkID=202431).  
  
 Document de « Instructions de réglage de performances pour Windows Server 2008 R2 » fournit des détails sur le réglage [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] et inclut une section se concentre spécifiquement sur Hyper-V. Le document est disponible à l’adresse [http://go.microsoft.com/fwlink/?LinkID=202087](http://go.microsoft.com/fwlink/?LinkID=202087).  
  
### <a name="hyper-v-platform-prerequisites"></a>Configuration requise pour Hyper-V plateforme  
 Hyper-V est un rôle de serveur disponible pour toutes les éditions d’et 64 bits [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] sont 64 bits uniquement. En outre, le matériel physique doit prendre en charge la virtualisation d’assistance matérielle. Cela signifie que le processeur doit être compatible avec la technologie de virtualisation Intel (VT Intel) ou la technologie de virtualisation d’AMD-V (AMD), le BIOS doit prendre en charge la prévention de l’exécution des données (PED) et la fonctionnalité doit être activée. Plus précisément, vous devez activer le bit Intel XD (execute disable bit) ou le bit AMD NX (aucun bit execute).  
  
> [!NOTE]  
>  Après l’activation de ces options dans le BIOS du système, désactiver l’ordinateur, puis redémarrez l’ordinateur pour vous assurer que ces paramètres sont appliqués.  
  
#### <a name="determining-hardware-requirements"></a>Déterminer la configuration matérielle requise  
 En raison d’exigences de consolidation de serveurs, serveurs Hyper-V ont tendance à consommer plus d’UC et mémoire et nécessitent la bande passante d’e/s de disque que les serveurs physiques avec des charges de calcul comparables. Pour déployer un environnement qui répond aux attentes, tenez compte des facteurs ci-dessous pour déterminer la configuration matérielle requise exacte de votre serveur.  
  
##### <a name="storage-configuration-options"></a>Options de Configuration de stockage  
 Le matériel de stockage doit fournir d’e/s de bande passante et de stockage une capacité suffisante pour répondre aux besoins actuels et futurs des ordinateurs virtuels que vous prévoyez d’héberger. Il existe un compromis lors du choix entre l’utilisation des capacités et les performances, qu'il peut fournir la configuration du stockage pour Hyper-V.  
  
 Lorsque vous planifiez la configuration de stockage, tenir compte des besoins de l’environnement que vous configurez. La configuration requise pour la production, de préproduction et environnements de développement peut varier considérablement.  
  
 Si vous déployez un environnement BizTalk Server sur Hyper-V de production, les performances seront une condition essentielle. Pour éviter la contention d’e/s sur les systèmes de production occupé de disque, installez les services d’intégration sur les système d’exploitation hôte et invité et configurer les disques pour les volumes de données avec le contrôleur SCSI synthétique. Pour les charges d’e/s de stockage très importantes qui s’étendent sur plusieurs lecteurs de données, chaque disque dur virtuel doit être attaché à un contrôleur SCSI synthétique distinct pour meilleures performances globales. En outre, chaque disque dur virtuel doit être stocké sur des disques physiques distincts. Pour plus d’informations sur la configuration des disques pour les données des volumes avec le contrôleur SCSI synthétique consultez la section « Optimiser les performances de disque » de la rubrique [liste de vérification : optimisation des performances sur Hyper-V](~/technical-guides/checklist-optimizing-performance-on-hyper-v.md).  
  
 En règle générale, les environnements de développement ont des exigences de performances strictes étant donné que l’utilisation des ressources a tendance à être la principale priorité. Pour les environnements de développement, les performances fournies lors de l’hébergement de plusieurs fichiers de disque dur virtuel sur un seul lecteur physique sont généralement acceptable.  
  
 Hyper-V prend en charge différents types de disques de stockage. Chacune des options de stockage peut être attaché via un contrôleur IDE ou SCSI à l’ordinateur. Un avantage potentiel de l’utilisation du contrôleur SCSI sur le contrôleur IDE est qu’il ne fonctionneront correctement si les versions correctes du système d’exploitation des composants d’intégration ont été installées sur l’ordinateur virtuel invité. Il s’agit d’une méthode simple pour s’assurer que les composants d’intégration de système d’exploitation sont installés sur le système d’exploitation invité.  
  
> [!NOTE]  
>  Contrairement aux versions précédentes de la technologie de virtualisation Microsoft, il n’existe aucune différence de performances entre l’utilisation d’un contrôleur IDE virtuel ou un contrôleur SCSI virtuel lors de l’accès aux disques durs virtuels.  
  
 Pour les activités en lecture-écriture intensives, telles que l’hébergement [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] bases de données, l’option de disque relais fournit de meilleures performances incrémentielles fixes du disque dur virtuel des disques (VHD). L’option de relais permet à l’ordinateur virtuel d’accéder directement au disque physique et contourne le système de fichiers NTFS de la partition racine, mais ne prend pas en charge certaines fonctionnalités de disques virtuels, tels que des captures instantanées d’ordinateur virtuel et le clustering prise en charge. Par conséquent, l’utilisation de la fonctionnalité de disque direct n’est pas recommandée dans un environnement BizTalk ou SQL Server, car les avantages de performance marginaux sont plus que par les fonctionnalités manquantes.  
  
 Le tableau suivant récapitule les avantages et inconvénients des options de stockage disponibles Hyper-V :.  
  
|**Type de stockage d’Hyper-V**|**Professionnels de l'**|**Inconvénients**|**Considérations pour BizTalk Server**|  
|-------------------------------|--------------|--------------|-------------------------------------------|  
|**Disques de taille fixe**|Plus performant qu’un disque dur virtuel dynamique, car le fichier de disque dur virtuel est initialisé à sa taille maximale possible lorsqu’il est créé sur le disque dur physique.<br /><br /> Cela rend la fragmentation inférieure probablement et, par conséquent, permet d’atténuer les scénarios où une seule e/s est fractionnée en plusieurs e/s. Cela a la surcharge du processeur la plus faible des types de disque dur virtuel, car les lectures et écritures en n’avez pas besoin rechercher le mappage du bloc.|Exige l’allocation du montant total d’espace disque initial.|Utiliser des volumes de système d’exploitation sur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]. **Important :** le disque de démarrage d’une partition d’invité Hyper-V doit être attaché à un contrôleur IDE.|  
|**Disques à extension dynamique**|La taille du fichier de disque dur virtuel augmente à la taille spécifiée lors de la création du disque, en plus de données sont stockés sur l’ordinateur virtuel lui-même. Cela permet d’optimiser l’utilisation du stockage disponible.|N’effectue pas ainsi que d’un disque dur virtuel de taille fixe. Il s’agit, car les blocs dans le disque démarrer en tant que blocs réinitialisés mais ne sont pas sauvegardés par n’importe quel espace réel dans le fichier de disque dur virtuel. Lit un bloc de zéros non significatifs à partir de ces blocs de retournés. Lorsqu’un bloc est d’abord écrites dans, la pile de virtualisation doit allouer de l’espace dans le fichier de disque dur virtuel pour le bloc et ensuite mettre à jour les métadonnées correspondantes. En outre chaque fois qu’un bloc existant est référencé le mappage de bloc doive être recherché dans les métadonnées. Cela augmente le nombre de lectures et les activités d’écriture qui provoque à son tour augmente l’utilisation du processeur.<br /><br /> La croissance dynamique requiert également que l’administrateur du serveur analyser la capacité de disque pour vous assurer qu’il existe suffisamment de stockage de disque en tant que l’augmentation de la configuration requise du stockage.|N’effectue pas ainsi que d’un disque dur virtuel de taille fixe.<br /><br /> Si les performances ne sont pas un critère important, par exemple dans un environnement de développement, cette option peut être une approprié pour les disques durs du système d’exploitation.<br /><br /> Entraîne un temps processeur supplémentaire en raison d’une recherche de mappage de bloc.|  
|**Disques de différenciation**|Cela une configuration parent-enfant où le disque de différenciation stocke toutes les modifications apportées par rapport à un disque dur virtuel de base et le disque dur virtuel de base reste statique. Par conséquent, uniquement les blocs qui sont différents du parent doivent être stockées dans les enfants de disque dur virtuel de différenciation.|Peuvent dégrader les performances, car il est en lecture/écriture devoir accéder au disque dur virtuel fixe/dynamique parent, ainsi que le disque de différenciation. Cela augmente l’utilisation du processeur et la charge d’e/s de disque.|Une grande quantité de configuration spécifique de l’ordinateur est requise pour les installations de BizTalk Server et les fichiers de disque dur virtuel enfant peuvent augmenter considérablement ce qui réduirait les avantages de l’utilisation de cette configuration de disque. La lecture à partir de plusieurs disques durs virtuels dans ce scénario implique la surcharge d’e/s de disque et des UC supplémentaires.|  
|**Disques relais**|Il s’agit des disques physiques qui sont définies sur *hors connexion* dans la partition racine et activer Hyper-V pour avoir un accès exclusif en lecture-écriture sur le disque physique.|Nécessite un disque entièrement dédié ou un numéro d’unité logique pour pouvoir être allouée à une machine virtuelle.<br /><br /> Un disque physique est plus difficile de déplacer entre des ordinateurs que les fichiers de disque dur virtuel.|Si votre [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instance s’exécute sur Hyper-V, vous pouvez obtenir des améliorations de performances incrémentielles à l’aide de disques relais principal à l’aide de disques durs virtuels (VHD) fixes pour les volumes de données BizTalk Server.<br /><br /> Si vous hébergez le fichier local emplacements de réception sur BizTalk Server ou la diffusion en continu sur le disque au cours du traitement des messages volumineux, vous pouvez obtenir des améliorations de performances incrémentielles à l’aide de disques relais à l’utilisation des disques durs virtuels (VHD).|  
  
 Pour plus d’informations sur l’implémentation de disques et stockage avec Hyper-V, consultez [implémentation de disques et de stockage](http://go.microsoft.com/fwlink/?LinkID=142362) (http://go.microsoft.com/fwlink/?LinkID=142362).  
  
##### <a name="networking"></a>Réseau  
 BizTalk Server a tendance à présenter l’utilisation du réseau élevé. Par conséquent, lorsque les performances du réseau sont un problème, envisagez d’allouer une carte réseau physique distinct pour chaque ordinateur virtuel.  
  
 Lorsque vous configurez un ordinateur virtuel, assurez-vous d’utiliser la carte réseau au lieu de la carte réseau virtuelle héritée. La carte réseau héritée est destinée aux systèmes d’exploitation qui ne prennent pas en charge les composants d’intégration.  
  
 Pour mesurer les performances réseau, utilisez le **« \Network Interface \Bytes/s »** et **\Network Interface (\*) \Output longueur de file d’attente** compteurs d’analyseur de performances sur l’ordinateur hôte d’exploitation système pour mesurer les performances globales de la carte réseau. Si un réseau physique a été identifié comme étant occupé, utilisez le **» \Hyper-V carte de réseau virtuel (\*) \Bytes/sec «** se trouvent le compteur sur le système d’exploitation hôte pour identifier les cartes réseau de machine virtuelle génération d’une charge élevée.  
  
 Pour plus d’informations sur l’évaluation des performances du réseau sur un environnement Hyper-V, consultez le **mesure les performances réseau** section de [liste de vérification : mesure des performances sur Hyper-V](../technical-guides/checklist-measuring-performance-on-hyper-v.md).  
  
##### <a name="cpu"></a>Unité centrale  
 Hyper-V prend en charge différents nombres de processeurs virtuels pour les systèmes d’exploitation invités différents ; comme indiqué dans le tableau ci-dessous. Pour allouer les ressources de processeur maximales pour BizTalk Server, installez-le sur un [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] système d’exploitation invité, qui prend en charge quatre processeurs virtuels par machine virtuelle.  
  
 Configurer une allocation de 1-1 de processeurs virtuels dans les systèmes d’exploitation invité avec des processeurs logiques disponibles pour le système d’exploitation hôte afin d’éviter les basculements excessifs de contexte. Entre les processeurs de contexte excessifs entraîne une dégradation des performances. Pour plus d’informations sur l’allocation de processeurs virtuels pour les processeurs logiques, consultez la section « Optimiser les performances du processeur » de la rubrique [liste de vérification : optimisation des performances sur Hyper-V](~/technical-guides/checklist-optimizing-performance-on-hyper-v.md).  
  
 Le « \Hyper-V processeur (_Total) logique de l’hyperviseur\\% Total exécution « compteur Analyseur de performances mesure l’utilisation des ressources globale de tous les ordinateurs invités et de l’hyperviseur sur l’ordinateur hôte Hyper-V. Si cette valeur est supérieure à 90 %, le serveur est en cours d’exécution atteint sa capacité maximale ; allocation de processeurs virtuels supplémentaires pour les machines virtuelles dans ce scénario peuvent dégrader les performances globales du système et doivent être évitées. Pour plus d’informations sur l’utilisation des compteurs de performance Hyper-v, consultez le [évaluation des performances du serveur BizTalk sur Hyper-V](../technical-guides/evaluating-biztalk-server-performance-on-hyper-v.md) section de ce guide.  
  
|Système d'exploitation|Limite du processeur virtuel|  
|----------------------|-----------------------------|  
|[!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]. Toutes les éditions de [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] sont 64 bits uniquement.|4|  
|[!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]64 bits|4|  
|[!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]32 bits|4|  
|Windows 7 64 bits|4|  
|Windows 7 32 bits|4|  
|Windows Vista 64 bits|2|  
|Windows Vista 32 bits|2|  
  
> [!NOTE]  
>  Pour plus d’informations sur les systèmes d’exploitation invités pris en charge sur Hyper-V, consultez [http://go.microsoft.com/fwlink/?LinkID=118347](http://go.microsoft.com/fwlink/?LinkID=118347).  
  
##### <a name="memory"></a>Mémoire  
 Le serveur physique requiert une mémoire suffisante pour la partition racine et toutes les machines virtuelles en cours d’exécution sur le serveur. Pendant le test, un minimum de 2 Go de mémoire a été alloué à la partition racine et le **Memory/Available Mbytes** compteur Analyseur de performances a été contrôlé afin de garantir aucune sollicitation de la mémoire a été rencontrée.  
  
 La quantité de mémoire qui doit être allouée à chaque ordinateur virtuel dans un environnement BizTalk Server dépend de la charge de travail et le type de traitement qui sera effectuée. Il existe de nombreux facteurs qui affectent les besoins en mémoire de BizTalk Server, notamment :  
  
-   Taille des messages traités  
  
-   Débit de messages  
  
-   Conception de l’orchestration  
  
-   Traitement du pipeline  
  
-   Nombre d’hôtes BizTalk que vous projetez d’exécuter sur l’ordinateur virtuel  
  
 Pour obtenir une liste complète des facteurs qui affectent la mémoire, consultez la section « Les facteurs de performances » de ce Guide d’optimisations de performances BizTalk Server à [http://go.microsoft.com/fwlink/?LinkId=122587](http://go.microsoft.com/fwlink/?LinkId=122587).  
  
 Analyse de façon proactive les **Memory/Available Mbytes** compteur à partir de chaque ordinateur virtuel et la partition racine lui-même. Les instructions suivantes à partir de [liste de vérification : mesure des performances sur Hyper-V](../technical-guides/checklist-measuring-performance-on-hyper-v.md) doit être utilisé pour déterminer s’il existe suffisamment de mémoire physique disponible pour la machine virtuelle et de la partition racine :  
  
-   50 % de mémoire disponible ou plus = sain  
  
-   25 % de mémoire disponible = analyse  
  
-   10 % de mémoire disponible = avertissement  
  
-   Inférieure à 5 % de mémoire disponible = critique, performances seront affectées  
  
#### <a name="choosing-root-operating-system-version"></a>En choisissant l’option Version de système d’exploitation racine  
 Hyper-V est pris en charge sur un Server Core, ainsi que d’une installation complète de [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]. Pour réduire la charge de la partition racine, installez Hyper-V sur une installation Server Core de [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]. Le rôle Hyper-V peut être géré à distance à partir du Gestionnaire Hyper-V sur un autre système. Server Core fournit un plus petit disque et mémoire un profil, par conséquent, en laissant davantage de ressources disponibles pour les ordinateurs virtuels. Pour plus d’informations sur l’option d’installation Server Core disponible pour [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)], consultez [http://go.microsoft.com/fwlink/?LinkID=202439](http://go.microsoft.com/fwlink/?LinkID=202439).  
  
 Si vous choisissez d’utiliser une installation complète de [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)], assurez-vous que la partition racine dédiée uniquement au rôle de serveur Hyper-V. Rôles serveur supplémentaires en cours d’exécution consomme les ressources réseau, processeur, mémoire et disque et dégrader les performances.  
  
#### <a name="creating-your-virtual-machines"></a>Création de vos Machines virtuelles  
 Après avoir installé et configuré le rôle de serveur Hyper-V, vous devez créer les ordinateurs virtuels. Avant cela, il est utile répondre aux questions suivantes :  
  
-   Quelle configuration de stockage va utiliser ?  
  
-   Le nombre de processeurs virtuel prises en charge par le système d’exploitation invité ?  
  
-   La quantité de mémoire est allouée à la machine virtuelle ?  
  
-   Nombre d’ordinateurs virtuels puis-je exécuter sur mon serveur Hyper-V ?  
  
-   Comment s’installer le système d’exploitation sur l’ordinateur ?  
  
 Pour plus d’informations sur la façon de créer et configurer des machines virtuelles, consultez [créer des ordinateurs virtuels](http://go.microsoft.com/fwlink/?LinkID=202440).  
  
##### <a name="installing-the-base-operating-system"></a>L’installation du système d’exploitation de Base  
 Toutes les options disponibles pour une installation de serveur physique sont disponibles dans Hyper-V. Un média CD/DVD-ROM de démarrage ou d’une image ISO peut être utilisée pour effectuer une installation manuelle. Une installation réseau peut être effectuée si l’ordinateur virtuel a été configuré avec une carte réseau connectée au même réseau en tant que serveur qui héberge les images ISO.  
  
> [!IMPORTANT]  
>  Quelle que soit la méthode d’installation choisie, pour des performances optimales, qu'il est essentiel que les composants d’intégration de système d’exploitation est installé pour chaque ordinateur virtuel en cours d’exécution sous Hyper-V. Les composants d’intégration fournissent un ensemble de pilotes et de services d’activation de l’ordinateur invité pour effectuer à l’aide de périphériques synthétiques. Les périphériques synthétiques évitez la nécessité de périphériques émulés, qui sont utilisés sur les systèmes d’exploitation qui ne prennent pas en charge les composants d’intégration. Périphériques émulés peser supérieure système par rapport aux périphériques synthétiques.  
  
 Pour installer et configurer les ordinateurs utilisés dans cet atelier, une image de base initiale a été créée sur un disque dur virtuel de taille fixe. Cela impliqué une installation manuelle de [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]. Une fois que toutes les mises à jour appropriées ont été installés l’ordinateur virtuel de base a été mis en image à l’aide de sysprep utilitaire qui est installé avec Windows Server 2008, dans le répertoire %WINDIR%\system32\sysprep.  
  
> [!NOTE]  
>  Exécution de Sysprep une fois que BizTalk Server a été installé et configuré sur le serveur peut être effectuée via l’utilisation d’un fichier de réponses Sysprep et les scripts fournis avec BizTalk Server. Ces exemples de scripts sont conçus pour une utilisation avec BizTalk Server est installé sur [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]. Pour plus d’informations, consultez la documentation en ligne de BizTalk Server.  
  
## <a name="installing-and-configuring-biztalk-server"></a>Installation et configuration de BizTalk Server  
  
-   Pour réduire le temps nécessaire pour installer des ordinateurs virtuels, créer une image de base comprenant uniquement le système d’exploitation invité et les logiciels requis. Utiliser SysPrep pour préparer l’image de disque dur virtuel pour une réutilisation et puis baser toutes vos machines virtuelles (VM) sur ce disque dur virtuel.  
  
    > [!NOTE]  
    >  Avec BizTalk Server, il est possible d’exécuter Sysprep sur une image de base *après*BizTalk Server a été installé et configuré sur le serveur. Cela peut être accompli à l’aide d’un fichier de réponses Sysprep et les scripts fournis avec BizTalk Server. Ces exemples de scripts sont conçus pour une utilisation avec BizTalk Server est installé sur [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] . Pour plus d’informations, consultez la documentation en ligne de BizTalk Server.  
    >   
    >  La référence de l’installation Windows sans assistance est disponible à l’adresse [http://go.microsoft.com/fwlink/?LinkId=142364](http://go.microsoft.com/fwlink/?LinkId=142364).  
  
-   Suivez les recommandations de la « lors de l’installation et configuration de BizTalk Server... » section de la rubrique [liste de vérification : meilleures pratiques pour l’installation et configuration de BizTalk Server sur Hyper-V](../technical-guides/checklist-best-practices-to-install-and-configure-biztalk-server-on-hyper-v.md).  
  
-   Pour plus d’informations sur la prise en charge de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] dans un environnement Hyper-V, voir [annexe c : BizTalk Server et la prise en charge de SQL Server Hyper-V](../technical-guides/appendix-c-biztalk-server-and-sql-server-hyper-v-supportability.md).