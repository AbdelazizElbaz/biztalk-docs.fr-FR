---
title: "Instructions générales pour améliorer les performances du système d’exploitation | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bc9ca38e-1feb-4f34-a64b-d04566e85db9
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e7be3f8060bba20bc0ba127443095c228f954bba
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="general-guidelines-for-improving-operating-system-performance"></a>Instructions générales pour améliorer les performances du système d’exploitation
Les directives générales suivantes doivent être suivies pour améliorer les performances du système d’exploitation :  
  
## <a name="install-the-latest-bios-storage-area-network-san-drivers-network-adapter-firmware-and-network-adapter-drivers"></a>Installez la dernière version du BIOS, les pilotes de réseau SAN de zone de stockage, les microprogramme de la carte réseau et les pilotes de carte réseau  
 Fabricants de matériel libérer régulièrement des mises à jour du BIOS, de microprogramme et de pilote qui peuvent améliorer les performances et disponibilité pour le matériel associé. Reportez-vous au site Web de fabricant de matériel pour télécharger et appliquer des mises à jour pour les composants matériels suivants sur chaque ordinateur dans l’environnement BizTalk Server :  
  
1.  Mises à jour du BIOS  
  
2.  Pilotes réseau SAN (si vous utilisez un réseau SAN)  
  
3.  Microprogramme de cartes réseau  
  
4.  Pilotes de carte réseau  
  
## <a name="enable-the-high-performance-power-plan-on-all-biztalk-server-and-sql-server-computers"></a>Activer « hautes performances » gestion de l’alimentation sur tous les ordinateurs BizTalk Server et SQL Server.  
 Par défaut, Windows Server 2008/2008 R2 définit l’équilibre (recommandé) alimentation, ce qui permet des économies d’énergie, mais peut provoquer une latence accrue (temps de réponse plus lent pour certaines tâches) et provoquer des problèmes de performances avec les applications sollicitant beaucoup le processeur.  
  
 Afin de réduire la latence, vous devez vous assurer que les fenêtres de tous les serveurs qui exécutent BizTalk Server et SQL Server **de l’alimentation** la valeur **hautes performances**. Pour plus d’informations sur la façon de basculer vers le **hautes performances** de l’alimentation, consultez l’article : 2207548 [une dégradation des performances globales sur Windows Server 2008 R2](http://go.microsoft.com/fwlink/?LinkID=219677) (http://go.microsoft.com/fwlink/?LinkID=219677).  
  
## <a name="evaluate-the-usage-of-intel-hyper-threading-on-biztalk-server-and-sql-server-computers"></a>Évaluer l’utilisation de Intel Hyper-Threading sur les ordinateurs BizTalk Server et SQL Server  
  
-   **Pre-Nehalem Hyper-Threading**:  
  
    -   La technologie Hyper-threading doit être désactivée sur les ordinateurs BizTalk Server. Il s’agit d’un paramètre du BIOS, que se trouve généralement dans les paramètres de processeur de la configuration du BIOS. La technologie Hyper-threading rend le serveur à semble avoir davantage de cœurs de processeurs/processeur qu’il le fait ; Toutefois, multithread de processeurs fournissent en général entre 20 à 30 % des performances d’un cœur de processeur/processeur physique. Lorsque BizTalk Server compte le nombre de processeurs pour ajuster ses algorithmes de réglage automatique, les processeurs HyperThreaded provoquent ces réglages pour être dévié, ce qui peuvent entraîner une diminution des performances globales.  
  
    -   La technologie Hyper-threading doit être désactivée sur les ordinateurs SQL Server, car les applications qui peuvent provoquer des niveaux élevés de contention (par exemple, BizTalk Server) peuvent provoquer une diminution des performances dans un environnement multithread sur un ordinateur SQL Server.  
  
-   **Hyper-Threading Nehalem**: contrairement à dans les architectures plus anciens, l’activation de hyper-threading dans les processeurs Intel une micro-architecture « Nehalem » peut fournir jusqu'à une augmentation de capacité quasi linéaire. Pour de meilleurs résultats, lorsque vous déployez les processeurs « Nehalem », nous vous recommandons de configurer le BIOS de l’ordinateur en activant la technologie Intel Hyper-Threading (H-T) pour une augmentation du débit marquée.  
  
-   **La virtualisation matérielle**: lorsque vous utilisez la virtualisation de matériel, l’ordinateur virtuel à l’aide de processeurs virtuels. Le nombre de processeurs disponibles est basé sur les paramètres choisis lors de la configuration de l’ordinateur virtuel. Si le matériel est multithread, l’ordinateur virtuel ne sauriez, qu'il est multithread.  
  
## <a name="assign-the-msdtc-log-file-directory-to-a-separate-dedicated-drive"></a>Affecter le répertoire du fichier journal MSDTC vers un autre lecteur dédié  
 Dans un environnement BizTalk Server avec plusieurs bases de données MessageBox sur des ordinateurs distincts de SQL Server, une surcharge supplémentaire associée avec Microsoft Distributed Transaction Coordinator (MSDTC) est générée. Par défaut, le journal MSDTC fichiers se trouvent dans le répertoire %systemdrive%\windows\system32\msdtc des ordinateurs exécutant le service DTC. Pour limiter le risque que la journalisation DTC peut devenir un goulot d’étranglement, déplacez le répertoire du fichier journal MSDTC vers un lecteur de disque rapide.  
  
 Pour modifier le répertoire du fichier journal MSDTC, consultez [configurer la journalisation DTC](http://go.microsoft.com/fwlink/?LinkID=204107) (http://go.microsoft.com/fwlink/?LinkID=204107).  
  
## <a name="configure-antivirus-software-to-avoid-real-time-scanning-of-biztalk-server-executables-and-file-drops"></a>Configurez le logiciel antivirus pour éviter l’analyse en temps réel des fichiers exécutables de BizTalk Server et supprime des fichiers  
 Le logiciel antivirus analyse en temps réel des fichiers exécutables de BizTalk Server et les dossiers ou le fichier partages surveillés par BizTalk Server des emplacements de réception peut nuire aux performances de BizTalk Server. Si un logiciel antivirus est installé sur l’ordinateur BizTalk Server, désactivez l’analyse en temps réel des types de fichier non exécutable référencés par n’importe quel serveur BizTalk emplacements de réception (en général. XML, mais peut également être .csv, .txt, etc..) et configurez le logiciel antivirus pour exclure l’analyse des fichiers exécutables de BizTalk Server  
  
## <a name="disable-intrusion-detection-network-scanning-between-computers-in-the-biztalk-server-environment"></a>Désactiver le réseau de détection d’intrusion analyse entre les ordinateurs dans l’environnement BizTalk Server  
 Logiciel de détection des intrusions peut ralentir ou même empêcher les communications valides sur le réseau. Si un logiciel de détection des intrusions est installé, désactivez réseau analyse entre les ordinateurs BizTalk Server et les ordinateurs de référentiels (SQL Server) de données externes ou les ordinateurs (par exemple, Message Queuing et WebSphere MQSeries), les services de messagerie.  
  
## <a name="defragment-all-disks-in-the-biztalk-server-environment-on-a-regular-basis"></a>Défragmentez tous les disques de l’environnement BizTalk Server sur une base régulière  
 Fragmentation excessive du disque dans l’environnement BizTalk Server affecte négativement les performances. Suivez ces étapes pour défragmenter des disques dans l’environnement BizTalk Server :  
  
1.  Défragmentez tous les disques (local et SAN/NAS) régulièrement par la planification de la défragmentation de disque heures creuses.  
  
2.  Défragmenter le fichier d’échange Windows et allouer à l’avance les Tables du fichier maître de chaque disque dans l’environnement BizTalk Server pour améliorer les performances globales du système.  
  
    > [!NOTE]  
    >  Pour allouer à l’avance les Tables du fichier maître, consultez l’article de la Base de connaissances 961095, [« Sur la Table de fichiers principale zone de réservation dans Windows Vista et Windows Server 2008 »](http://go.microsoft.com/fwlink/?LinkID=204563) (http://go.microsoft.com/fwlink/?LinkID=204563).  
  
## <a name="if-antivirus-software-is-installed-on-the-sql-server-computer-disable-real-time-scanning-of-data-and-transaction-files"></a>Si un logiciel antivirus est installé sur l’ordinateur SQL Server, désactivez l’analyse en temps réel des fichiers de données et de transactions  
 Analyse en temps réel des fichiers SQL Server transaction et de données (.mdf, .ndf, .ldf, .mdb), vous pouvez augmenter les conflits d’e/s disque et réduire les performances de SQL Server. Notez que les noms des fichiers de données et de transactions de SQL Server peuvent varier entre les environnements de BizTalk Server. Pour plus d’informations sur les fichiers de données et de transactions créés avec une configuration de BizTalk Server par défaut, consultez [optimisation de groupes de fichiers pour le Databases2](../technical-guides/optimizing-filegroups-for-the-databases2.md).  
  
## <a name="configure-msdtc-for-biztalk-server-and-sql-server"></a>Configurer MSDTC pour BizTalk Server et SQL Server  
 Pour faciliter les transactions entre SQL Server et BizTalk Server, vous devez activer Microsoft Distributed Transaction Coordinator (MSDTC).  
  
#### <a name="to-configure-distributed-transaction-coordinator-dtc"></a>Pour configurer le coordinateur de transactions distribuées (DTC, Distributed Transaction Coordinator)  
  
1.  Cliquez sur **Démarrer**, cliquez sur **exécuter**, type **dcomcnfg**, puis cliquez sur **OK** pour ouvrir **Services de composants** .  
  
2.  Dans l’arborescence de la console, développez **Services de composants**, **Ordinateurs**, **Poste de travail**, **Distributed Transaction Coordinator**, puis cliquez sur **DTC local**.  
  
3.  Avec le bouton droit **DTC Local**, puis cliquez sur **propriétés** pour afficher les **propriétés DTC Local** boîte de dialogue.  
  
4.  Sur le **suivi** sous l’onglet sous **Options de sortie** section, désactivez le **sortie de Trace** boîte.  
  
5.  Cliquez sur l’onglet **Sécurité** .  
  
6.  Vérifiez que les quatre options suivantes sont sélectionnées (et que les autres sont désactivées) :  
  
    -   **Accès DTC réseau**  
  
    -   **Autoriser les transactions entrantes**  
  
    -   **Autoriser les transactions sortantes**  
  
    -   **Aucune authentification requise**  
  
7.  Cliquez sur **OK** pour fermer la **propriétés DTC Local** boîte de dialogue. Si vous êtes invité à redémarrer le service MSDTC, cliquez sur **Oui**.  
  
8.  Fermez **Services de composants**.  
  
9. Cliquez sur **Démarrer**, pointez sur **outils d’administration**, puis cliquez sur **pare-feu Windows avec fonctions avancées de sécurité**.  
  
10. Dans le pare-feu Windows avec fonctions avancées de sécurité, cliquez sur **règles de trafic entrant**.  
  
11. Dans le **règles de trafic entrant** volet, avec le bouton droit **Distributed Transaction Coordinator*** (selon le cas), puis cliquez sur **activer la règle**.  
  
12. Dans le pare-feu Windows avec fonctions avancées de sécurité, cliquez sur **règles de trafic sortant**.  
  
13. Dans le **règles de trafic sortant** volet, avec le bouton droit **Distributed Transaction Coordinator*** (selon le cas), puis cliquez sur **activer la règle**.  
  
14. Sur le **le panneau de configuration**, double-cliquez sur **outils d’administration**.  
  
15. Dans le volet droit, double-cliquez sur **Services**.  
  
16. Dans le volet droit de **Services (Local)**, avec le bouton droit **Application système COM +**, cliquez sur **redémarrer**et attendez que le redémarrage du service.  
  
17. Effectuez un clic droit et redémarrez le service **Distributed Transaction Coordinator**.  
  
18. Effectuez un clic droit et redémarrez le service **SQL Server (MSSQLSERVER)**.  
  
19. Fermez la page **Services (local)**, puis la page **Outils d’administration**.  
  
## <a name="configure-firewalls-for-biztalk-server"></a>Configurez l’ou les pare-feu pour BizTalk Server  
  
> [!NOTE]  
>  Cette étape est uniquement requis si un ou plusieurs pare-feu sont en place dans votre environnement BizTalk Server.  
  
 Passez en revue les informations suivantes pour configurer l’ou les pare-feu pour BizTalk Server :  
  
-   [Ports requis pour BizTalk Server](http://go.microsoft.com/fwlink/?LinkID=153238) (http://go.microsoft.com/fwlink/?LinkID=153238).  
  
-   Pour configurer l’allocation de port dynamique RPC avec un pare-feu, consultez l’article de la Base de connaissances 929851, [« la plage de ports dynamiques par défaut pour le protocole TCP/IP a changé dans Windows Vista et Windows Server 2008 »](http://go.microsoft.com/fwlink/?LinkID=204568) (lien hypertexte « http:// go.Microsoft.com/fwlink/ ? LinkID = 204568" http://go.microsoft.com/fwlink/? LinkID = 204568). Pour plus d’informations sur la façon de configurer le pare-feu Windows pour prendre en charge les ports nécessaires, consultez [le pare-feu Windows et Guide pas à pas de déploiement de stratégie IPsec](http://go.microsoft.com/fwlink/?LinkID=204569) (http://go.microsoft.com/fwlink/?LinkID=204569).  
  
## <a name="install-appropriate-com-and-msdtc-hotfix-rollup-packages"></a>Installer approprié MSDTC et COM + correctifs cumulatifs  
 Passez en revue les informations suivantes pour installer les packages MS DTC et COM + correctif cumulatif appropriés :  
  
-   Le correctif logiciel MS DTC sont accessibles dans la Base de connaissances Microsoft article978476 [« Le problème de MS DTC est résolu dans Windows Server 2008 R2 MS DTC Package de correctifs cumulatifs 1 »](http://go.microsoft.com/fwlink/?LinkID=204109) (http://go.microsoft.com/fwlink/?LinkID=204109).  
  
-   Article le plus récent DTC correctif cumulatif Ko de package peut être recherché en [http://support.microsoft.com](http://go.microsoft.com/fwlink/?LinkID=96185) (http://go.microsoft.com/fwlink/?LinkID=96185) pour l’expression (y compris les guillemets) :  
  
    ```  
    "MS DTC Hotfix Rollup Package"  
    ```  
  
     La requête suivante effectue cette recherche pour vous. Choisir la plus récente :   
    [http://support.Microsoft.com/search/default.aspx?Query= « MS + DTC + + Package correctif cumulatif + »](http://support.microsoft.com/search/default.aspx?query="MS+DTC+Hotfix+Rollup+Package")  
  
## <a name="use-the-interrupt-affinity-policy-tool-to-bind-network-adapter-interrupts-to-specific-processors-on-multiprocessor-computers"></a>Utiliser l’outil Stratégie Interrupt Affinity pour lier des interruptions de carte réseau sur des processeurs spécifiques sur les ordinateurs multiprocesseurs  
 La stratégie Interrupt Affinity (IntPolicy) est un outil qui vous permet de « lier » ou de modifier l’affinité du processeur d’interruptions pour un périphérique donné (par exemple, une carte réseau) permet à un processeur spécifique ou de processeurs sur un ordinateur multiprocesseur. Cette liaison est également appelée le partitionnement. La liaison des interruptions à partir d’une carte réseau spécifique sur des processeurs spécifiques sur un ordinateur multiprocesseur applique en cours d’exécution des appels de procédure différés (DPC) et les routines de service d’interruption (ISR) pour la carte réseau sur les processeurs désignés. Notez qu’une affinité ne peut pas être configurée sur les ordinateurs à processeur unique.  
  
> [!NOTE]  
>  Un DPC est défini comme un appel en file d’attente à une fonction en mode noyau qui est généralement exécutée ultérieurement. Une ISR est défini comme une routine qui vise à un périphérique de service lorsqu’il génère une interruption. Pour plus d’informations sur les appels de procédure différés et les routines ISR, consultez le [documentation de Windows Driver Kit](http://go.microsoft.com/fwlink/?LinkId=84418) (http://go.microsoft.com/fwlink/?LinkId=84418).  
  
 ![Interruption &#45; Outil de stratégie d’affinité](../technical-guides/media/interrupt-affinitypolicytool.gif "AffinityPolicyTool de l’interruption")  
Outil Stratégie Interrupt Affinity  
  
 Sur Windows Server 2008 en fonction des ordinateurs multiprocesseurs, le comportement par défaut du contrôleur d’interruption est pour affecter des interruptions de l’appareil à n’importe quel processeur disponible. Lorsque les connexions réseau et les sessions de serveur de fichiers pour une carte réseau donnée sont liés aux/partitionnée pour s’exécuter sur un ensemble spécifique de processeurs, plutôt que n’importe quel processeur disponible, les performances et l’évolutivité du traitement du réseau associée est améliorée. Grandes solutions BizTalk Server utilisent souvent l’utilisation de plusieurs processeurs des ordinateurs de SQL Server avec plusieurs cartes réseau pour lesquels la liaison d’interruption peut être particulièrement utile.   
Liaison de l’interruption à l’aide de IntPolicy doit toujours être évaluée dans un environnement de test avant d’utiliser dans un environnement de production. Le matériel, le système d’exploitation et la configuration de l’application de l’environnement de test doivent être l’environnement de production aussi fidèlement que possible. Cela vous permettra pour tester diverses permutations de liaison de l’interruption et de déterminer l’étendue d’interruption de la liaison de transport seront augmenter les performances.  
 Nous vous conseillons de désactiver hyper-threading avant de configurer IntPolicy sur un ordinateur disposant de processeurs qui prend en charge la technologie hyper-threading. Cela garantit que les interruptions sont attribuées à des processeurs physiques plutôt que de processeurs logiques. Affecter une affinité avec des processeurs logiques qui font référence au même processeur physique pas améliore les performances et peut même dégrader les performances du système.    Lien hypertexte « The » le [outil de stratégie Interrupt Affinity](http://go.microsoft.com/fwlink/?LinkID=204111) (http://go.microsoft.com/fwlink/?LinkID=204111) est disponible en téléchargement depuis le site Web WHDC.  
  
## <a name="use-the-ntfs-file-system-on-all-volumes"></a>Utiliser le système de fichiers NTFS sur tous les volumes  
 Windows Server offre plusieurs types de système de fichiers de mise en forme des lecteurs, y compris NTFS, FAT et FAT32. NTFS doit toujours être le système de fichiers de choix pour les serveurs.  
NTFS offre des gains de performance considérable sur les systèmes de fichiers FAT et FAT32 et doit être utilisé exclusivement sur les serveurs Windows. En outre, NTFS offre de nombreux avantages de sécurité, d’évolutivité, de stabilité et de récupération sur les FAT et FAT32.  
Dans les versions antérieures de Windows, FAT et FAT32 ont souvent implémentées pour petits volumes (par exemple < 500 Mo), car il est souvent plus rapides dans ces situations. Avec relativement peu coûteux aujourd'hui le stockage sur disque et les systèmes d’exploitation et les applications en exécutant un push de capacité de disque à un maximum, il est peu probable que ces volumes de petite taille soit en cours d’utilisation. FAT32 évolue mieux que FAT sur des volumes de grande capacité mais n’est pas toujours un système de fichiers approprié pour les serveurs Windows.  
FAT et FAT32 ont souvent été implémentées dans le passé comme elles ont été considérés comme plus facilement récupérables et gérable à l’aide des outils natifs de déni de service en cas de problème avec un volume. Aujourd'hui, avec la récupération NTFS divers outils intégrés à la fois en mode natif dans le système d’exploitation et disponibles en tant que des utilitaires tiers disponibles, il ne doit plus être un argument valide pour ne pas utiliser NTFS pour les systèmes de fichiers.  
  
## <a name="do-not-use-ntfs-file-compression"></a>N’utilisez pas la compression de fichiers NTFS  
 Si à l’aide de la compression du système de fichiers NTFS est un moyen simple pour réduire l’espace sur les volumes, il n’est pas appropriée pour les serveurs de fichiers d’entreprise. Implémentation de la compression place une surcharge inutile sur l’UC pour toutes les opérations de disque et est évitée. Considérer les options permettant d’ajouter des disques supplémentaires, stockage quasi en ligne ou envisagez de l’archivage des données avant de considérer sérieusement de compression du système de fichiers.  
  
## <a name="review-disk-controller-stripe-size-and-volume-allocation-units"></a>Passez en revue les unités sur disque contrôleur stripe volume et la taille d’allocation  
 Lors de la configuration des baies de lecteurs et les lecteurs logiques au sein de votre contrôleur de disque matériel, vérifiez vous correspond à la taille de répartition de contrôleur avec la taille d’unité d’allocation à formater les volumes avec. Cela vous assurer de lecture de disque et écrire les performances sont optimales et offrent de meilleures performances globales du serveur.  
Configuration d’allocation unité (ou de cluster ou d’un bloc) volumineux entraîne l’espace disque à utiliser moins efficace, mais fournit également des meilleures performances d’e/s disque comme la tête de lecture peut lire davantage de données au cours de chaque activité de lecture.  
Pour déterminer le paramètre optimal pour configurer le contrôleur et de formater les disques avec, vous devez déterminer la taille moyenne du disque de transfert sur le sous-système de disque d’un serveur avec des caractéristiques de système de fichiers similaires. Utilisez l’outil Analyseur de performances Windows pour surveiller les compteurs des objets disque logique de moyenne Disque, octets/lecture et moyenne Disque, octets/écriture sur une période d’activité normale pour aider à déterminer la meilleure valeur à utiliser.  
Bien que la plus petite taille d’unité d’allocation peut se justifier si le système accèdent aux nombreux petits fichiers ou des enregistrements, une taille d’unité d’allocation de 64 Ko offre des performances audio et débit d’e/s dans la plupart des cas. Améliorations des performances avec les tailles d’unité d’allocation analysé peuvent être notées en particulier lors de l’augmentation de la charge de disque.  
  
> [!NOTE]  
>  L’outil de ligne de commande FORMAT ou de l’outil de gestion des disques est requis pour spécifier une taille d’unité d’allocation supérieure à 4 096 octets (4 Ko) lors de la mise en forme des volumes. L’Explorateur Windows ne mettra en forme jusqu'à ce seuil. La commande CHKDSK peut être utilisée pour vérifier la taille d’unité d’allocation actuelle d’un volume, mais qu’il doit analyser l’intégralité du volume avant que les informations souhaitées sont affichées (indiqué en tant qu’octets dans chaque unité d’allocation).  
  
## <a name="monitor-drive-space-utilization"></a>Surveiller l’utilisation de l’espace disque  
 L’a moins de données un disque, rapide, il fonctionnera. Il s’agit, car il est sur un lecteur également défragmenté, les données sont écrites aussi proche du bord extérieur du disque de la mesure du possible, car il s’agit où le disque tourne la plus rapide et produit les meilleures performances.  
Temps de recherche de disque est généralement beaucoup plus de temps à lire ou écrire des activités. Comme indiqué ci-dessus, les données sont initialement écrites à l’extérieur d’un disque. Comme la demande pour le stockage de disque augmente et l’espace libre est réduit, les données sont écrites proche au centre du disque. Recherche de disque temps est augmenté à localiser les données en tant que le principal déplace loin du bord et lorsque trouvé, prend plus de temps à lire, affecter négativement les performances d’e/s disque.  
Cela signifie qu’il est important de surveiller l’utilisation de l’espace disque pas également seulement pour des raisons de capacité, mais pour les performances.  
En règle générale, de parvenir à un objectif est de conserver l’espace disque disponible entre 20 et 25 % d’espace disque total. Si suppressions d’espace disque disponible sous ce seuil, puis les performances d’e/s disque diminues.  
  
## <a name="implement-a-strategy-to-avoid-disk-fragmentation"></a>Implémenter une stratégie pour éviter la fragmentation du disque  
 Exécuter un utilitaire Défragmenteur régulièrement sur vos disques, y compris le lecteur racine, pour éviter une dégradation des performances. Effectuez cette hebdomadaires sur des disques occupés. Le Défragmenteur de disque est installé avec Windows et peut être exécuté à partir d’une tâche planifiée à intervalles réguliers.  
  
## <a name="optimize-windows-server-performance-for-background-services"></a>Optimiser les performances de Windows Server pour les services d’arrière-plan  
 Le processus BizTalk Server (BTSNTSVC.exe) s’exécute comme un service en arrière-plan.   
Windows Server 2008 utilise multitâches préemptifs pour classer par priorité des threads de processus qui participeront à l’UC. Multitâches préemptifs est une méthode par laquelle l’exécution d’un processus est arrêtée et un autre processus est lancé, à la discrétion du système d’exploitation. Ce schéma empêche la dominent le processeur d’un thread unique.  
Basculement de l’UC de l’exécution d’un processus à l’autre est connu en tant que le changement de contexte. Le système d’exploitation Windows inclut un paramètre qui détermine la durée pendant laquelle les threads individuels sont autorisés à exécuter sur l’UC avant un changement de contexte se produit et le thread suivant est traité. Ce délai est appelé un quantum. Ce paramètre vous permet de choisir la façon dont les quanta de processeur est partagés entre les programmes de premier plan et les services d’arrière-plan. En général, pour un serveur qu’il n’est pas souhaitable d’autoriser un programme de premier plan à plus de temps processeur allouée à des services d’arrière-plan. Autrement dit, toutes les applications et leurs processus en cours d’exécution sur le serveur doivent être autorisés égal pas prises en compte pour le temps processeur.  
 Pour améliorer les performances pour le service en arrière-plan, comme des instances d’hôte BizTalk, procédez comme suit :  
  
1.  Cliquez sur **Démarrer**, cliquez sur **le panneau de configuration**, puis cliquez sur **système**.  
  
2.  Cliquez sur le **avancé** onglet, puis cliquez sur **paramètres** sous **performances**.  
  
3.  Cliquez sur le **avancé** , cliquez sur **services d’arrière-plan**, puis cliquez sur **OK** à deux reprises.  
  
## <a name="disable-non-essential-services"></a>Désactiver les services non essentiels  
 Une installation par défaut de Windows Server 2008 permet à plusieurs services qui ne peuvent pas être nécessaire dans un environnement BizTalk Server. Chaque service en cours d’exécution consomme des ressources système et par conséquent, les services doivent être désactivés pour améliorer les performances globales.  
Soyez vigilant lors de la désactivation des services. Avant de désactiver le service, comme Windows Server requiert que certains services s’exécutent des recherches approfondies sur l’objectif d’un service. Si les services requis par Windows Server 2008 sont désactivés, le système d’exploitation peut devenir inutilisable et voire ne peut pas démarrer.  
Pour désactiver les services de Windows Server 2008 qui ne sont pas requis pour un serveur dédié de BizTalk Server, procédez comme suit :  
  
1.  Cliquez sur **Démarrer**, pointez sur **outils d’administration**, puis cliquez sur **gestion de l’ordinateur**.  
  
2.  Sous **gestion de l’ordinateur (Local)**, développez **Services et Applications**, puis cliquez sur **Services**.  
    Dans le **état** colonne, chaque service est en cours d’exécution est étiqueté « Démarré ». Arrêter et désactiver tout service qui est démarré inutilement, par exemple, les services suivants ne sont pas requis sur un serveur dédié de BizTalk :  
  
    -   Avertissement  
  
    -   Album  
  
    -   Serveur DHCP  
  
    -   Service de télécopie  
  
    -   Réplication de fichiers  
  
    -   Moniteur infrarouge  
  
    -   Partage de connexion Internet  
  
    -   Messenger  
  
    -   Le partage de bureau à distance NetMeeting  
  
    -   DDE réseau  
  
    -   DSDM DDE réseau  
  
    -   NWLink NetBIOS  
  
    -   NWLink IPX/SP  
  
    -   Spouleur d’impression  
  
    -   Téléphonie  
  
    -   Telnet  
  
    -   Alimentation non interruptible.  
  
3.  Notez les services qui dépendent de chaque service que vous souhaitez désactiver. Pour cela, procédez comme suit :  
  
    1.  Double-cliquez sur le service que vous souhaitez désactiver.  
  
    2.  Cliquez sur le **dépendances** onglet.  
  
    3.  Dans le **ce service dépend des composants système suivants** list, notez les services de ce service dépend.  
  
    4.  Dans le **les composants système suivants dépendent de ce service** list, notez les services qui ne peut pas démarrer sans ce service, puis cliquez sur **OK**.  
  
4.  À la fois, désactivez chaque service que vous avez sélectionné. Pour cela, procédez comme suit :  
  
    1.  Cliquez sur le service que vous voulez désactiver, puis cliquez sur **propriétés**.  
  
    2.  Dans le **type de démarrage** , cliquez sur **désactivé**.  
  
    3.  Si vous souhaitez arrêter immédiatement le service, cliquez sur **arrêter**.  
  
         Si le **arrêter les autres Services** boîte de dialogue s’affiche, notez les autres services dépendants qui est également arrêter, puis cliquez sur **Oui**, puis cliquez sur **OK**.  
  
5.  Répétez l’étape 4 pour désactiver les autres services non essentiels.  
  
> [!NOTE]  
>  Tester le serveur pour fonctionner correctement après la désactivation de chaque service pour vous assurer que vous ne désactivez pas un service que vous souhaitez continuer à utiliser.   
> Si le serveur est membre d’un domaine Windows Server 2008, qui sont souvent des serveurs BizTalk Server, vous devez disposer du service d’assistance TCP/IP sur votre système pour appliquer correctement la stratégie de groupe à l’ordinateur.   
> Lorsque vous désactivez le client DHCP, le client DHCP arrête l’enregistrement de protocole de mise à jour dynamique DNS et requiert des enregistrements DNS manuelles à ajouter au serveur DNS pour ce client.  
  
## <a name="manually-load-microsoft-certificate-revocation-lists"></a>Charger manuellement les listes de révocation de certificats Microsoft  
 Lorsque vous démarrez une application .NET, le .NET Framework tente de télécharger la liste de révocation de certificats (CRL) pour tous les assemblys signés. Si votre système ne dispose pas d’un accès direct à Internet, ou accéder au domaine Microsoft.com, cela peut retarder le démarrage de BizTalk Server. Pour éviter ce délai au démarrage de l’application, vous pouvez utiliser les étapes suivantes pour télécharger et installer le code de signature de listes de révocation de certificat sur votre système manuellement.  
  
1.  Télécharger les dernières mises à jour de la liste CRL à partir de [http://crl.microsoft.com/pki/crl/products/CodeSignPCA.crl](http://go.microsoft.com/fwlink/?LinkID=117794) (http://go.Microsoft.com/fwlink/?) LinkID = 117794) et [http://crl.microsoft.com/pki/crl/products/CodeSignPCA2.crl](http://go.microsoft.com/fwlink/?LinkId=117795) (http://go.Microsoft.com/fwlink/?) LinkId = 117795).  
  
2.  Déplacer les fichiers CodeSignPCA.crl et CodeSignPCA2.crl vers le système isolé.  
  
3.  À partir d’une invite de commandes, entrez la commande suivante pour utiliser l’utilitaire certutil pour mettre à jour le magasin de certificats avec la liste de révocation téléchargé à l’étape 1 :  
  
     certutil-addstore autorité de certification c:\CodeSignPCA.crl  
  
 Les fichiers de la révocation de certificats sont mis à jour régulièrement, afin que vous envisagez de définir une tâche récurrence de téléchargement et installation de la liste de révocation des mises à jour. Pour afficher la prochaine mise à jour, double-cliquez sur le fichier .crl et la valeur de la **mettre à jour suivant** champ.  
  
## <a name="synchronize-time-on-all-servers"></a>Synchroniser l’heure sur tous les serveurs  
 De nombreuses opérations tickets, accusés de réception et la journalisation s’appuient sur l’horloge système locale exact. Cela est particulièrement vrai dans un environnement distribué, où les différences de temps entre les systèmes peuvent entraîner des journaux de synchronisation ou tickets émis par un seul système pour être rejetés par un autre comme ayant expiré ou pas encore valide.  
  
 Pour plus d’informations sur la configuration d’un serveur pour synchroniser l’heure, consultez [configurer un ordinateur client pour la synchronisation automatique de domaines](http://go.microsoft.com/fwlink/?LinkId=99420) (http://go.microsoft.com/fwlink/?LinkId=99420).  
  
## <a name="configure-the-windows-pagefile-for-optimal-performance"></a>Configurer le fichier d’échange Windows pour des performances optimales  
 Suivez ces instructions pour configurer le fichier d’échange Windows (fichier d’échange) pour optimiser les performances :  
  
1.  **Déplacer le fichier d’échange à un volume physique distinct dans le lecteur de système d’exploitation est installé sur pour réduire la contention de disque et améliorer les performances du disque physique** - sur les ordinateurs BizTalk Server, le gain de performance associé au déplacement le fichier de pagination varie en fonction de la charge de traitement de document. Sur les ordinateurs SQL Server, le déplacement du fichier de pagination vers un volume distinct est considéré comme une meilleure pratique dans tous les scénarios en raison de la nature intensif du disque de SQL Server.  
  
2.  **Isoler le fichier d’échange sur un ou plusieurs physique des lecteurs dédiés qui sont configurés comme RAID-0 (agrégation) ou les tableaux RAID-1 (miroir) ou sur des disques uniques sans RAID** : À l’aide d’une baie de disque ou lecteur dédiée où fichier d’échange. SYS est le seul fichier sur le volume entier, le fichier d’échange ne sera pas fragmenté, ce qui améliore également les performances. Comme avec la plupart des-baies de disques, les performances du tableau sont améliorées en augmentant le nombre de disques physiques dans le tableau. Si le fichier d’échange est répartie entre plusieurs volumes sur plusieurs disques physiques dans une baie de disques, la taille de fichier d’échange doit être la même taille sur chaque lecteur dans le tableau. Lorsque vous configurez une baie de disques, il est également recommandé d’utiliser des disques physiques qui ont la même capacité et la vitesse. Notez que la redondance n’est pas normalement requise pour le fichier d’échange.  
  
3.  **Ne configurez pas le fichier d’échange sur un tableau RAID 5** -Configuration du fichier de pagination sur un tableau RAID 5 n’est pas recommandée, car l’activité du fichier d’échange est en écriture intensif et les tableaux RAID 5 conviennent mieux aux performances de lecture que d’écriture.  
  
4.  **Si vous n’avez pas de ressources à déplacer le fichier d’échange à un volume physique autres que le système d’exploitation est installé sur, configurez le fichier d’échange pour résider sur le même volume logique en tant que le système d’exploitation** -configuration du fichier de pagination pour résider sur un un autre volume logique qui se trouve sur le même disque physique, car le système d’exploitation augmente disque temps de recherche et de réduire les performances du système car les têtes de plateau de disque dur sera continuellement déplacements entre les volumes, vous pouvez également accéder au fichier de page, les fichiers de système d’exploitation, les fichiers d’application et les fichiers de données. En outre, le système d’exploitation est généralement installé sur la première partition d’un disque physique, ce qui est généralement le plus proche du bord extérieur du disque physique et où la vitesse de disque est et performances sont optimales pour le disque.  
  
    > [!IMPORTANT]  
    >  Si vous supprimez le fichier d’échange à partir de la partition de démarrage, Windows ne peut pas créer un fichier de vidage sur incident (mémoire. DMP) dans lequel écrire les informations de débogage dans le cas où un mode noyau arrêter erreur se produit. Si vous devez un fichier de vidage sur incident, vous n’avez aucune possibilité, mais laissez au moins un fichier d’échange taille de mémoire physique + 1 Mo sur la partition de démarrage.  
  
5.  **Définir manuellement la taille du fichier d’échange** – manuellement définissant la taille du fichier d’échange en général plus performant que permettre au serveur pour le redimensionner automatiquement ou n’avoir aucun fichier d’échange du tout. Meilleures pratiques de paramétrage est pour définir les paramètres de taille maximale du fichier d’échange initial (au minimum) à la même valeur. Cela garantit qu’aucune des ressources de traitement ne sont perdus au redimensionnement dynamique du fichier d’échange, qui peut être intensif. Cela est particulièrement vrai étant donné que cette activité redimensionnement se produit généralement lorsque les ressources mémoire sur le système sont déjà devenant limités. Paramètre de temps de recherche de la même minimum et taille de fichier maximale de page valeurs Assurez-vous également de la zone de la pagination sur un disque est un domaine unique et contiguë, améliorer le disque. Windows Server 2008 recommande automatiquement une total taille de fichier d’échange égale à 1,5 fois la quantité de mémoire vive. Sur les serveurs avec un espace disque suffisant, le fichier d’échange sur combinées de tous les disques doit être configuré jusqu'à deux fois la mémoire physique pour des performances optimales.  
  
## <a name="remove-cpu-intensive-screen-savers"></a>Supprimer des économiseurs d’écran gourmande en ressources processeur  
 3D ou des économiseurs d’écran OpenGL sont connus pour être gourmande en ressources processeur et utilisent des ressources système importantes lorsqu’ils sont en cours d’exécution. Il est préférable pour éviter d’installer ces purement et simplement comme une option au moment de la build du serveur ou les supprimer si elles ont été installés. La base « Windows Server 2008 » ou des économiseurs d’écran vide sont une excellente lieu d’utiliser des économiseurs d’écran gourmande en ressources processeur.  
  
## <a name="see-also"></a>Voir aussi  
 [Optimisation des performances du système d’exploitation](../technical-guides/optimizing-operating-system-performance.md)