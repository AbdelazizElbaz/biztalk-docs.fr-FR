---
title: "Optimisations de système d’exploitation | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: af2e77d0-d69b-4ae4-b689-96831fc4deed
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2ede5ad9dd3affba3ce132ab4c4415e8dba4f3cb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="operating-system-optimizations"></a>Optimisations de système d’exploitation
Cette rubrique fournit des recommandations pour optimiser les performances de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ordinateurs utilisés dans une production [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnement. Ces optimisations sont appliquées après [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] a été installé et configuré.  
  
## <a name="general-guidelines-for-improving-operating-system-performance"></a>Recommandations générales pour améliorer les performances du système d’exploitation  
 Les recommandations suivantes peuvent être utilisées pour augmenter les performances du système d’exploitation :  
  
### <a name="install-the-latest-bios-storage-area-network-san-drivers-network-adapter-firmware-and-network-adapter-drivers"></a>Installez la dernière version du BIOS, les pilotes de réseau SAN de zone de stockage, les microprogramme de la carte réseau et les pilotes de carte réseau  
 Fabricants de matériel libérer régulièrement des mises à jour du BIOS, de microprogramme et de pilote qui peuvent améliorer les performances et disponibilité pour le matériel associé. Reportez-vous au site Web de fabricant de matériel pour télécharger et appliquer des mises à jour pour les composants matériels suivants sur chaque ordinateur dans l’environnement BizTalk Server :  
  
1.  Mises à jour du BIOS  
  
2.  Pilotes réseau SAN (si vous utilisez un réseau SAN)  
  
3.  Microprogramme de cartes réseau  
  
4.  Pilotes de carte réseau  
  
### <a name="assign-the-msdtc-log-file-directory-to-a-separate-dedicated-drive"></a>Affecter le répertoire du fichier journal MSDTC vers un autre lecteur dédié  
 Dans un environnement BizTalk Server avec plusieurs bases de données MessageBox sur des ordinateurs distincts de SQL Server, une surcharge supplémentaire associée avec Microsoft Distributed Transaction Coordinator (MSDTC) est générée. Par défaut, les fichiers de journal MSDTC sont situés dans le répertoire %systemdrive%\windows\system32\msdtc des ordinateurs exécutant le service DTC. Pour limiter le risque que la journalisation DTC peut devenir un goulot d’étranglement, déplacez le répertoire du fichier journal MSDTC vers un lecteur de disque rapide. Pour modifier le répertoire du fichier journal MSDTC, procédez comme suit :  
  
1.  Cliquez sur **Démarrer**, cliquez sur **exécuter**et le type **dcomcnfg** pour lancer le **Services de composants** console de gestion.  
  
2.  Développez **Services de composants**, développez **ordinateurs**, avec le bouton droit **poste**, puis cliquez sur **propriétés**.  
  
3.  Dans le **propriétés Poste de travail** boîte de dialogue, cliquez sur le **MSDTC** onglet.  
  
4.  Dans le **emplacement** modifier la zone sous **informations du journal**, tapez le chemin d’accès où vous souhaitez que le nouveau journal doit être créé (par exemple, G:\Logs\DTCLog).  
  
5.  Cliquez sur **réinitialiser le journal**, et vous serez invité pour le redémarrage du service. Cliquez sur **OK** à redémarrer le service DTC, puis cliquez sur **OK** pour confirmer le service MSDTC a été redémarré.  
  
### <a name="configure-antivirus-software-to-avoid-real-time-scanning-of-biztalk-server-executables-and-file-drops"></a>Configurez le logiciel antivirus pour éviter l’analyse en temps réel des fichiers exécutables de BizTalk Server et supprime des fichiers  
 Le logiciel antivirus analyse en temps réel des fichiers exécutables de BizTalk Server et les dossiers ou le fichier partages surveillés par BizTalk Server des emplacements de réception peut nuire aux performances de BizTalk Server. Si un logiciel antivirus est installé sur les ordinateurs BizTalk Server, désactivez l’analyse en temps réel des types de fichier non exécutable référencés par n’importe quel serveur BizTalk emplacements de réception (en général. XML, mais peut également être .csv, .txt, etc..) et configurez le logiciel antivirus pour exclure l’analyse des fichiers exécutables de BizTalk Server  
  
### <a name="disable-intrusion-detection-network-scanning-between-computers-in-the-biztalk-server-environment"></a>Désactiver le réseau de détection d’intrusion analyse entre les ordinateurs dans l’environnement BizTalk Server  
 Logiciel de détection des intrusions peut ralentir ou même empêcher les communications valides sur le réseau. Si un logiciel de détection des intrusions est installé, désactivez réseau analyse entre les ordinateurs BizTalk Server et les ordinateurs de référentiels (SQL Server) de données externes ou les ordinateurs (Message Queuing, WebSphere MQSeries, etc.) de services de messagerie.  
  
### <a name="defragment-all-disks-in-the-biztalk-server-environment-on-a-regular-basis"></a>Défragmentez tous les disques de l’environnement BizTalk Server sur une base régulière  
 Fragmentation excessive du disque dans l’environnement BizTalk Server affecte négativement les performances. Suivez ces étapes pour défragmenter des disques dans l’environnement BizTalk Server :  
  
1.  Défragmentez tous les disques (local et SAN/NAS) régulièrement par la planification de la défragmentation de disque heures creuses.  
  
2.  Défragmenter le fichier d’échange Windows et allouer à l’avance les Tables du fichier maître de chaque disque dans l’environnement BizTalk Server pour améliorer les performances globales du système.  
  
    > [!NOTE]  
    >  Utilisez l’utilitaire PageDefrag disponible à l’adresse [http://go.microsoft.com/fwlink/?LinkId=108976](http://go.microsoft.com/fwlink/?LinkId=108976) pour défragmenter le fichier d’échange Windows et allouer à l’avance les Tables de fichiers principal.  
  
### <a name="if-antivirus-software-is-installed-on-the-sql-server-computers-disable-real-time-scanning-of-data-and-transaction-files"></a>Si un logiciel antivirus est installé sur l’ordinateur SQL Server, désactivez l’analyse en temps réel des fichiers de données et de transactions  
 Analyse en temps réel des fichiers SQL Server transaction et de données (.mdf, .ndf, .ldf, .mdb), vous pouvez augmenter les conflits d’e/s disque et réduire les performances de SQL Server. Notez que les noms des fichiers de données et de transactions de SQL Server peuvent varier entre les environnements de BizTalk Server. Pour plus d’informations sur les fichiers de données et de transactions créés avec une configuration de BizTalk Server par défaut, consultez[optimisation de groupes de fichiers pour les bases de données](http://msdn.microsoft.com/library/ee377060\(v=bts.70\).aspx).  
  
### <a name="configure-msdtc-for-biztalk-server"></a>Configurer MSDTC pour BizTalk Server  
 Passez en revue les informations suivantes pour configurer MSDTC pour BizTalk Server :  
  
-   Pour configurer MSDTC sur BizTalk Server, consultez guide de la section « Activer DTC sur le serveur hôte Local » de l’installation de BizTalk Server 2010 [http://go.microsoft.com/fwlink/?LinkID=191321](http://go.microsoft.com/fwlink/?LinkID=191321).  
  
-   « Dépannage des problèmes liés à MSDTC » à [http://go.microsoft.com/fwlink/?LinkID=202142](http://go.microsoft.com/fwlink/?LinkID=202142).  
  
### <a name="configure-firewalls-for-biztalk-server"></a>Configurez l’ou les pare-feu pour BizTalk Server  
  
> [!NOTE]  
>  Cette étape est uniquement requis si un ou plusieurs pare-feu sont en place dans votre environnement BizTalk Server.  
  
 Passez en revue les informations suivantes pour configurer l’ou les pare-feu pour BizTalk Server :  
  
-   « Ports requis pour BizTalk Server » à [http://go.microsoft.com/fwlink/?LinkId=101607](http://go.microsoft.com/fwlink/?LinkId=101607).  
  
-   « Comment configurer l’allocation de port dynamique RPC avec les pare-feu » à [http://go.microsoft.com/fwlink/?LinkID=76145](http://go.microsoft.com/fwlink/?LinkID=76145).  
  
### <a name="use-the-ntfs-file-system-on-all-volumes"></a>Utiliser le système de fichiers NTFS sur tous les volumes  
 [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)]offre plusieurs types de système pour mettre en forme des lecteurs, y compris NTFS, FAT et FAT32. NTFS doit toujours être le système de fichiers de choix pour les serveurs.[!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)]  
  
 NTFS offre des gains de performance considérable sur les systèmes de fichiers FAT et FAT32 et doit être utilisé exclusivement sur les serveurs Windows. En outre, NTFS offre de nombreux avantages de sécurité, d’évolutivité, de stabilité et de récupération sur les FAT et FAT32.  
  
 Dans les versions antérieures de Windows, FAT et FAT32 ont souvent implémentées pour petits volumes (par exemple \<500 Mo), car il est souvent plus rapides dans ces situations. Avec relativement peu coûteux aujourd'hui le stockage sur disque et les systèmes d’exploitation et les applications en exécutant un push de capacité de disque à un maximum, il est peu probable que ces volumes de petite taille soit en cours d’utilisation. FAT32 évolue mieux que FAT sur des volumes de grande capacité mais n’est pas toujours un système de fichiers approprié pour les serveurs Windows.  
  
 FAT et FAT32 ont souvent été implémentées dans le passé comme elles ont été considérés comme plus facilement récupérables et gérable à l’aide des outils natifs de déni de service en cas de problème avec un volume. Aujourd'hui, avec la récupération NTFS divers outils intégrés à la fois en mode natif dans le système d’exploitation et disponibles en tant que des utilitaires tiers disponibles, il ne doit plus être un argument valide pour ne pas utiliser NTFS pour les systèmes de fichiers.  
  
### <a name="do-not-use-ntfs-file-compression"></a>N’utilisez pas la compression de fichiers NTFS  
 Si à l’aide de la compression du système de fichiers NTFS est un moyen simple pour réduire l’espace sur les volumes, il n’est pas appropriée pour les serveurs de fichiers d’entreprise. Implémentation de la compression place une surcharge inutile sur l’UC pour toutes les opérations de disque et est évitée. Considérer les options permettant d’ajouter des disques supplémentaires, stockage quasi en ligne ou envisagez de l’archivage des données avant de considérer sérieusement de compression du système de fichiers.  
  
### <a name="review-disk-controller-stripe-size-and-volume-allocation-units"></a>Passez en revue les unités sur disque contrôleur stripe volume et la taille d’allocation  
 Lors de la configuration des baies de lecteurs et les lecteurs logiques au sein de votre contrôleur de disque matériel, vérifiez vous correspond à la taille de répartition de contrôleur avec la taille d’unité d’allocation à formater les volumes avec. Cela vous assurer de lecture de disque et écrire les performances sont optimales et offrent de meilleures performances globales du serveur.  
  
 Configuration d’allocation unité (ou de cluster ou d’un bloc) volumineux entraîne l’espace disque à utiliser moins efficace, mais fournit également des meilleures performances d’e/s disque comme la tête de lecture peut lire davantage de données au cours de chaque activité de lecture.  
  
 Pour déterminer le paramètre optimal pour configurer le contrôleur et de formater les disques avec, vous devez déterminer la taille moyenne du disque de transfert sur le sous-système de disque d’un serveur avec des caractéristiques de système de fichiers similaires. Utilisez le [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)] outil Analyseur de performances pour surveiller les compteurs des objets disque logique de moyenne Disque, octets/lecture et moyenne Disque, octets/écriture sur une période d’activité normale pour aider à déterminer la meilleure valeur à utiliser.  
  
 Bien que la plus petite taille d’unité d’allocation peut se justifier si le système accèdent aux nombreux petits fichiers ou des enregistrements, une taille d’unité d’allocation de 64 Ko offre des performances audio et débit d’e/s dans la plupart des cas. Améliorations des performances avec les tailles d’unité d’allocation analysé peuvent être notées en particulier lors de l’augmentation de la charge de disque.  
  
> [!NOTE]  
>  L’outil de ligne de commande FORMAT ou de l’outil de gestion des disques est requis pour spécifier une taille d’unité d’allocation supérieure à 4 096 octets (4 Ko) lors de la mise en forme des volumes. L’Explorateur Windows ne mettra en forme jusqu'à ce seuil. La commande CHKDSK peut être utilisée pour vérifier la taille d’unité d’allocation actuelle d’un volume, mais qu’il doit analyser l’intégralité du volume avant que les informations souhaitées sont affichées (indiqué en tant qu’octets dans chaque unité d’allocation).  
  
### <a name="monitor-drive-space-utilization"></a>Surveiller l’utilisation de l’espace disque  
 Les moins de données sur un disque, plus il va s’exécuter. Il s’agit, car il est sur un lecteur également défragmenté, les données sont écrites aussi proche du bord extérieur du disque que possible, car c’est là le disque tourne la plus rapide et produit les meilleures performances.  
  
 Temps de recherche de disque est généralement beaucoup plus de temps à lire ou écrire des activités. Comme indiqué ci-dessus, les données sont initialement écrites à l’extérieur d’un disque. Comme la demande pour le stockage de disque augmente et l’espace libre est réduit, les données sont écrites proche au centre du disque. Recherche de disque temps est augmenté à localiser les données en tant que le principal déplace loin du bord et lorsque trouvé, prend plus de temps à lire, affecter négativement les performances d’e/s disque.  
  
 Cela signifie qu’il est important de surveiller l’utilisation de l’espace disque pas également seulement pour des raisons de capacité, mais pour les performances.  
  
 En règle générale, de parvenir à un objectif est de conserver l’espace disque disponible entre 20 et 25 % d’espace disque total. Si suppressions d’espace disque disponible sous ce seuil, puis les performances d’e/s disque diminues.  
  
### <a name="implement-a-strategy-to-avoid-disk-fragmentation"></a>Implémenter une stratégie pour éviter la fragmentation du disque  
 Exécuter un utilitaire Défragmenteur régulièrement sur vos disques, y compris le lecteur racine, pour éviter une dégradation des performances. Effectuez cette hebdomadaires sur des disques occupés. Le Défragmenteur de disque est installé avec Windows Server et peut être exécuté à partir d’une tâche planifiée à intervalles réguliers.  
  
### <a name="optimize-windows-server-performance-for-background-services"></a>Optimiser les performances de Windows Server pour les services d’arrière-plan  
 Le processus BizTalk Server (BTSNTSVC.exe) s’exécute comme un service en arrière-plan. Par défaut, [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)] est configuré pour l’ajuster pour de meilleures performances des programmes d’application et pas pour les services d’arrière-plan.  
  
 [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)]utilise multitâches préemptifs pour classer par priorité des threads de processus qui participeront à l’UC. Multitâches préemptifs est une méthode par laquelle l’exécution d’un processus est arrêtée et un autre processus est lancé, à la discrétion du système d’exploitation. Ce schéma empêche la dominent le processeur d’un thread unique.  
  
 Basculement de l’UC de l’exécution d’un processus à l’autre est connu en tant que le changement de contexte. Le système d’exploitation Windows inclut un paramètre qui détermine la durée pendant laquelle les threads individuels sont autorisés à exécuter sur l’UC avant un changement de contexte se produit et le thread suivant est traité. Ce délai est appelé un quantum. Ce paramètre vous permet de choisir la façon dont les quanta de processeur est partagés entre les programmes de premier plan et les services d’arrière-plan. En général, pour un serveur qu’il n’est pas souhaitable d’autoriser un programme de premier plan à plus de temps processeur allouée à des services d’arrière-plan. Autrement dit, toutes les applications et leurs processus en cours d’exécution sur le serveur doivent être autorisés égal pas prises en compte pour le temps processeur.  
  
 Pour améliorer les performances pour le service en arrière-plan, comme des instances d’hôte BizTalk, procédez comme suit :  
  
1.  Cliquez sur **Démarrer**, cliquez sur **le panneau de configuration**, puis cliquez sur **système**.  
  
2.  Cliquez sur le **avancé** onglet, puis cliquez sur **paramètres** sous **performances**.  
  
3.  Cliquez sur le **avancé** , cliquez sur **services d’arrière-plan**, puis cliquez sur **OK** à deux reprises.  
  
### <a name="manually-load-microsoft-certificate-revocation-lists"></a>Charger manuellement les listes de révocation de certificats Microsoft  
 Lorsque vous démarrez une application .NET, le .NET Framework tente de télécharger la liste de révocation de certificats (CRL) pour tous les assemblys signés. Si votre système ne dispose pas d’un accès direct à Internet, ou accéder au domaine Microsoft.com, cela peut retarder le démarrage de BizTalk Server. Pour éviter ce délai au démarrage de l’application, vous pouvez utiliser les étapes suivantes pour télécharger et installer le code de signature de listes de révocation de certificat sur votre système manuellement.  
  
1.  Télécharger les dernières mises à jour de la liste CRL à partir de [http://crl.microsoft.com/pki/crl/products/CodeSignPCA.crl](http://go.microsoft.com/fwlink/?LinkID=117794) et [http://crl.microsoft.com/pki/crl/products/CodeSignPCA2.crl](http://go.microsoft.com/fwlink/?LinkId=117795).  
  
2.  Déplacer les fichiers CodeSignPCA.crl et CodeSignPCA2.crl vers le système isolé.  
  
3.  À partir d’une invite de commandes, entrez la commande suivante pour utiliser l’utilitaire certutil pour mettre à jour le magasin de certificats avec la liste de révocation téléchargé à l’étape 1 :  
  
     certutil-addstore autorité de certification c:\CodeSignPCA.crl  
  
 Les fichiers de la révocation de certificats sont mis à jour régulièrement, afin que vous envisagez de définir une tâche récurrence de téléchargement et installation de la liste de révocation des mises à jour. Pour afficher la prochaine mise à jour, double-cliquez sur le fichier .crl et la valeur de la **mettre à jour suivant** champ.  
  
### <a name="synchronize-time-on-all-servers"></a>Synchroniser l’heure sur tous les serveurs  
 De nombreuses opérations tickets, accusés de réception et la journalisation s’appuient sur l’horloge système locale exact. Cela est particulièrement vrai dans un environnement distribué, où les différences de temps entre les systèmes peuvent entraîner des journaux de synchronisation ou tickets émis par un seul système pour être rejetés par un autre comme ayant expiré ou pas encore valide.  
  
 Pour plus d’informations sur la configuration d’un serveur pour synchroniser l’heure, consultez [http://go.microsoft.com/fwlink/?LinkId=99420](http://go.microsoft.com/fwlink/?LinkId=99420).  
  
### <a name="configure-the-windows-pagefile-for-optimal-performance"></a>Configurer le fichier d’échange Windows pour des performances optimales  
 Suivez ces instructions pour configurer le fichier d’échange Windows (fichier d’échange) pour optimiser les performances :  
  
1.  **Déplacer le fichier d’échange à un volume physique distinct dans le lecteur de système d’exploitation est installé sur pour réduire la contention de disque et améliorer les performances du disque physique** - sur les ordinateurs BizTalk Server, le gain de performance associé au déplacement le fichier de pagination varie en fonction de la charge de traitement de document. Sur les ordinateurs SQL Server, le déplacement du fichier de pagination vers un volume distinct est considéré comme une meilleure pratique dans tous les scénarios en raison de la nature intensif du disque de SQL Server.  
  
2.  **Isoler le fichier d’échange sur un ou plusieurs physique des lecteurs dédiés qui sont configurés comme RAID-0 (agrégation) ou les tableaux RAID-1 (miroir) ou sur des disques uniques sans RAID** : À l’aide d’une baie de disque ou lecteur dédiée où fichier d’échange. SYS est le seul fichier sur le volume entier, le fichier d’échange ne sera pas fragmenté, ce qui améliore également les performances. Comme avec la plupart des-baies de disques, les performances du tableau sont améliorées en augmentant le nombre de disques physiques dans le tableau. Si le fichier d’échange est répartie entre plusieurs volumes sur plusieurs disques physiques dans une baie de disques, la taille de fichier d’échange doit être la même taille sur chaque lecteur dans le tableau. Lorsque vous configurez une baie de disques, il est également recommandé d’utiliser des disques physiques qui ont la même capacité et la vitesse. Notez que la redondance n’est pas normalement requise pour le fichier d’échange.  
  
3.  **Ne configurez pas le fichier d’échange sur un tableau RAID 5** -Configuration du fichier de pagination sur un tableau RAID 5 n’est pas recommandée, car l’activité du fichier d’échange est en écriture intensif et les tableaux RAID 5 conviennent mieux aux performances de lecture que d’écriture.  
  
4.  **Si vous n’avez pas de ressources à déplacer le fichier d’échange à un volume physique autres que le système d’exploitation est installé sur, configurez le fichier d’échange pour résider sur le même volume logique en tant que le système d’exploitation** -configuration du fichier de pagination pour résider sur un un autre volume logique qui se trouve sur le même disque physique, car le système d’exploitation augmente disque temps de recherche et de réduire les performances du système car les têtes de plateau de disque dur sera continuellement déplacements entre les volumes, vous pouvez également accéder au fichier de page, les fichiers de système d’exploitation, les fichiers d’application et les fichiers de données. En outre, le système d’exploitation est généralement installé sur la première partition d’un disque physique, ce qui est généralement le plus proche du bord extérieur du disque physique et où la vitesse de disque est et performances sont optimales pour le disque.  
  
    > [!IMPORTANT]  
    >  Si vous supprimez le fichier d’échange à partir de la partition de démarrage, Windows ne peut pas créer un fichier de vidage sur incident (mémoire. DMP) dans lequel écrire les informations de débogage dans le cas où un mode noyau arrêter erreur se produit. Si vous devez un fichier de vidage sur incident, vous n’avez aucune possibilité, mais laissez au moins un fichier d’échange taille de mémoire physique + 1 Mo sur la partition de démarrage.  
  
5.  **Définir manuellement la taille du fichier d’échange** – manuellement définissant la taille du fichier d’échange en général plus performant que permettre au serveur pour le redimensionner automatiquement ou n’avoir aucun fichier d’échange du tout. Meilleures pratiques de paramétrage est pour définir les paramètres de taille maximale du fichier d’échange initial (au minimum) à la même valeur. Cela garantit qu’aucune des ressources de traitement ne sont perdus au redimensionnement dynamique du fichier d’échange, qui peut être intensif. Cela est particulièrement vrai étant donné que cette activité redimensionnement se produit généralement lorsque les ressources mémoire sur le système sont déjà devenant limités. Définition de la même minimale et la valeur de taille de fichier maximale de page garantit également la zone de la pagination sur un disque est un domaine unique et contigu, améliorer le disque des temps de recherche.