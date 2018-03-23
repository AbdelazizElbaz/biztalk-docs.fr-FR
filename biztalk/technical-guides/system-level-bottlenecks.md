---
title: Les goulots d’étranglement au niveau du système | Documents Microsoft
ms.custom: ''
ms.date: 06/29/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0bdff435-76eb-495f-9fb6-1f1acef3921e
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 058fd60e1c38a3045197b4a36bdcc81250ab5be5
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2018
---
# <a name="system-level-bottlenecks"></a>Goulots d’étranglement au niveau du système
Cette rubrique décrit comment adresser courantes goulots d’étranglement au niveau du système qui peuvent affecter les performances d’une solution BizTalk Server.  
  
## <a name="creating-a-snapshot-of-the-baseline-configuration"></a>Création d’un instantané de la configuration de base  
 Collecte les informations suivantes permettre vous fournir un instantané de la configuration de référence que vous pouvez utiliser pour vous aider dans la correction des goulots d’étranglement au niveau du système.  
  
### <a name="gather-documentation"></a>Regroupez les informations  
 Passez en revue la documentation de l’architecture et l’infrastructure de votre scénario.  
  
### <a name="run-the-baseline-security-analyzer"></a>Exécuter la Baseline Security Analyzer  
 Suivez ces étapes pour exécuter l’Analyseur de sécurité de base :  
  
1.  Téléchargez le [Microsoft Baseline Security Analyzer 2.2](http://go.microsoft.com/fwlink/?LinKID=204006) (http://go.microsoft.com/fwlink/?LinkId=204006).  
  
2.  À l’aide d’un compte d’administrateur de domaine, ouvrez une session un ordinateur sur le même réseau que celui qui héberge les ordinateurs BizTalk Server et SQL Server.  
  
3.  Installez Microsoft Baseline Security Analyzer sur l’ordinateur actuel (par exemple, un des ordinateurs BizTalk Server ou un ordinateur distinct).  
  
4.  Exécuter une analyse séparée (**démarrer l’analyse**), en spécifiant en tant que paramètre le nom ou l’adresse IP de chaque ordinateur BizTalk Server et SQL Server.  
  
5.  Copie de chaque rapport de sécurité (fichiers .mbsa) à partir du répertoire %userprofile%\SecurityScans.  
  
### <a name="run-the-biztalk-server-best-practices-analyzer"></a>Exécuter BizTalk Server Best Practices Analyzer  
 Suivez ces étapes pour exécuter BizTalk Server Best Practices Analyzer :  
  
1.  Téléchargez le [BizTalk Server Best Practices Analyzer v1.2](http://go.microsoft.com/fwlink/?LinkID=83317) (http://go.microsoft.com/fwlink/?LinkID=83317).  
  
2.  À l’aide d’un compte d’utilisateur qui fait partie du groupe de sécurité administrateur de BizTalk Server, ouvrez une session un nœud de BizTalk Server.  
  
3.  Installer BizTalk Server Best Practices Analyzer sur l’ordinateur actuel.  
  
4.  Exécutez l’outil et enregistrer le rapport.  
  
### <a name="run-msinfo32-and-save-the-results"></a>Exécutez MSInfo32 et enregistrer les résultats  
 Suivez ces étapes pour exécuter MSInfo32 :  
  
1.  À l’aide d’un domaine ou un compte d’administrateur local, ouvrez une session chaque ordinateur BizTalk Server et SQL Server.  
  
2.  Lancez une invite de commandes et accédez au répertoire %windir%\system32 de l’ordinateur.  
  
3.  À partir de l’invite de commandes, exécutez MSinfo32.exe.  
  
4.  Cliquez sur le **fichier** menu et sélectionnez le **exporter** élément de menu Exporter pour enregistrer la configuration de l’ordinateur.  
  
### <a name="export-the-biztalk-server-and-sql-server-computer-tcpip-registry-setting-"></a>Exporter l’ordinateur BizTalk Server et SQL Server du paramètre du Registre TCP/IP-  
 Suivez ces étapes pour enregistrer les paramètres de Registre de BizTalk Server et SQL Server TCP/IP :  
  
1.  Lancez une invite de commandes et accédez au répertoire %windir%\system32 de l’ordinateur.  
  
2.  À partir de l’invite de commandes, exécutez Regedit.exe.  
  
3.  Accédez à la clé suivante dans le Registre :  
  
    ```  
    [HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Tcpip\Parameters] (network settings)  
    ```  
  
4.  Cette clé d’avec le bouton droit et sélectionnez **exporter** pour exporter la clé de Registre dans un fichier.  
  
### <a name="collect-the-biztalk-configuration-files"></a>Collecter les fichiers de configuration de BizTalk  
 Sur chaque nœud de BizTalk Server, collecter le BizTalk Server configuration fichier, fichier BTSNTSvc.exe.config (ou BTSNTSvc64.exe.config pour les ordinateurs hôtes 64 bits), situé dans le dossier d’installation de BizTalk Server (par exemple, C:\Program Files\Microsoft BizTalk Server 2010).  
  
### <a name="collect-the-net-configuration-files"></a>Collecter les fichiers de configuration .NET  
 Sur chaque nœud de BizTalk Server, collecter les fichiers de configuration .NET Framework 4.0 machine.config et web.config. Vous pouvez trouver les fichiers de configuration à l’emplacement suivant :  
  
-   Pour 32 bits : %windir%\Microsoft.NET\Framework\v4.0.30319\CONFIG dossier  
  
-   64 bits : %windir%\Microsoft.NET\Framework64\v4.0.30319\CONFIG dossier  
  
### <a name="use-the-biztalk-msgboxviewer-tool-to-collect-information-about-the-messagebox-database"></a>Utilisez l’outil de BizTalk MsgBoxViewer pour collecter des informations sur la base de données MessageBox  
 Suivez ces étapes pour collecter des informations sur la base de données MessageBox à l’aide de l’outil BizTalk MsgBoxViewer :  
  
1.  Téléchargez le [BizTalk MsgBoxViewer outil](http://go.microsoft.com/fwlink/?LinkID=117289) (http://go.microsoft.com/fwlink/?LinkID=117289).  
  
2.  Ouvrez une session l’ordinateur BizTalk Server avec un compte d’utilisateur qui fait partie du groupe de sécurité administrateur de BizTalk Server.  
  
3.  Copiez le MsgBoxViewer.exe sur l’ordinateur BizTalk Server.  
  
4.  Lancez l’outil.  
  
5.  Cliquez sur le **facultatif des informations à collecter** onglet, puis cliquez sur **sélectionner toutes les informations**.  
  
6.  Cliquez sur **démarrer à collecter**.  
  
7.  Lorsque l’étiquette de l’état affiche le **fin Collection** de message, basculez vers le dossier contenant le fichier exécutable MsgBoxViewer.exe et copier le rapport obtenu (.htm) et les fichiers journaux.  
  
### <a name="collect-and-store-the-source-code-for-all-components-used-in-the-solution"></a>Collecter et stocker le code source pour tous les composants utilisés dans la solution  
 Stocker le code source pour tous les composants (par exemple d’Orchestration, composant de Pipeline personnalisé et d’assistance composants code) sur un partage de fichiers distincts.  
  
## <a name="initial-troubleshooting"></a>Dépannage initial  
 Il existe certains composants d’une solution BizTalk Server, ce qui, s’il est ne pas activé, provoque des problèmes de performances, quelle que soit la taille globale ou de la conception de la solution BizTalk. Les tâches de dépannage préliminaires suivantes doivent être effectuées pour éliminer des « suspect » avant de s’engager dans une analyse exhaustive de goulot d’étranglement d’une solution BizTalk.  
  
-   **Vérifiez que l’instance d’hôte de suivi est en cours d’exécution -** suivi de l’instance de l’hôte est responsable du déplacement des données BAM et du fonctionnement de la table TrackingData de la base de données MessageBox pour les tables de base de données BizTalkDTADb et/ou BAMPrimaryImport. Si l’instance de l’hôte du suivi n’est pas exécuté, les données de suivi seront s’accumulent dans la base de données MessageBox et nuire aux performances de la solution BizTalk Server.  
  
-   **Vérifiez que le service de l’entreprise Sign-On (ENTSSO) est en cours d’exécution sur tous les ordinateurs BizTalk Server -** instances d’hôte BizTalk conservent une dépendance sur une instance en cours d’exécution locale du service ENTSSO. Si le service d’authentification unique ne fonctionne pas sur le serveur BizTalk Server, les instances d’hôte sur le serveur ne sera pas en mesure d’exécuter le.  
  
-   **Vérifiez que le service SQL Server Agent est en cours d’exécution sur tous les ordinateurs SQL Server -** service de l’Agent SQL Server doit être exécuté dans l’ordre pour les travaux BizTalk SQL Server Agent exécuter. Ces travaux remplissent des fonctions importantes pour conserver vos serveurs de fonctionnement.  
  
-   **Vérifiez que les travaux BizTalk SQL Server Agent sont activés et en cours d’exécution sans exceptions -** même si le service SQL Server Agent est en cours d’exécution, il est impératif que tous les travaux de l’Agent SQL Server BizTalk par défaut sont activés et en cours d’exécution avec succès.  
  
-   **Vérifiez les journaux des événements BizTalk Server et SQL Server -** un examen rapide des journaux d’événements BizTalk Server ou SQL Server peut révéler un problème qui pourrait avoir beaucoup de temps pour diagnostiquer et résoudre.  
  
-   **Exécuter BizTalk Server Best Practices Analyzer -** le BizTalk Server Best Practices Analyzer examine un déploiement de BizTalk Server et génère une liste des problèmes liés aux normes de meilleures pratiques. L’outil effectue une vérification au niveau de la configuration en collectant des données à partir des informations différentes sources, telles que les classes Windows Management Instrumentation (WMI), les bases de données SQL Server et les entrées de Registre. Les données sont ensuite utilisées pour évaluer la configuration de déploiement. L’outil lit les rapports uniquement et ne modifie pas les paramètres système et n’est pas un outil de réglage automatique. Télécharger le serveur BizTalk Server Best Practices Analyzer v1.2 de [BizTalk Server Best Practices Analyzer v1.2](http://go.microsoft.com/fwlink/?LinkID=83317) (http://go.microsoft.com/fwlink/?LinkID=83317).  
  
## <a name="high-level-system-bottlenecks"></a>Goulots d’étranglement du système de niveau supérieur  
 Cette section décrit les goulots d’étranglement au niveau du système qui peuvent être présents dans une solution BizTalk Server et les stratégies d’atténuation possibles.  
  
### <a name="disk-io-bottlenecks"></a>Goulots d’étranglement des e/s disque  
 E/s disque fait référence au nombre de lecture et les opérations d’écriture effectuées par votre application sur un disque physique ou plusieurs disques installés sur votre serveur. Les activités courantes qui peuvent provoquer des e/s disque et les goulots d’étranglement connexes incluent des longues opérations d’e/s de fichier, le chiffrement des données et le déchiffrement, les données inutiles lors de la lecture à partir de tables de base de données et d’une insuffisance de mémoire physique, ce qui peut entraîner une pagination excessive activité. Vitesse du disque est un autre facteur à prendre en compte lors de l’évaluation des goulots d’étranglement d’e/s disque ; disques plus rapides améliorer les performances et réduire les goulots d’étranglement des e/s disque.  
  
 Le tableau ci-dessous fournit des facteurs à prendre en compte lorsque vous planifiez le sous-système de disque pour une solution BizTalk Server.  
  
|Facteur de sous-système de disque|Détails|  
|---------------------------|-------------|  
|Mémoire cache de disque et de mémoire physique disponible|Étant donné que la mémoire est mise en cache sur disque lorsque la mémoire physique devient limitée, assurez-vous que vous avez une quantité suffisante de mémoire disponible. Lorsque la mémoire est rare, davantage de pages est écrites sur le disque, ce qui entraîne une activité du disque accrue. En outre, assurez-vous que définir le fichier d’échange à une taille appropriée. Mémoire cache de disque supplémentaire aidera décalage des pics de demandes d’e/s de disque. Toutefois, il convient de noter qu’une mémoire cache de disque volumineux rarement permet de résoudre le problème de ne pas disposer de suffisamment de piles et ayant suffisamment piles peut refuser la nécessité d’une mémoire cache de disque de grande taille. Pour plus d’informations sur la configuration du fichier de pagination Windows pour des performances optimales, consultez la section « Configurer le fichier d’échange pour optimiser les performances de Windows » dans la rubrique [optimisation des performances de système d’exploitation](~/technical-guides/optimizing-operating-system-performance.md).|  
|Type de contrôleur de stockage|Si vous avez par batterie, activer le cache d’écriture améliorer les performances d’écriture de disque sur les volumes de fichier journal des transactions et sur les volumes de base de données. La mise en cache d’écriture offre un temps de réponse de 2 ms pour une demande d’e/s d’écriture, par opposition à un temps de réponse de 10 à 20 ms sans cache d’écriture. L’activation d’écriture considérablement la mise en cache améliore la réactivité pour les demandes d’écriture client. La mise en cache de lecture n’améliore pas les performances dans un scénario de BizTalk Server, car il n’est utile pour les lectures de disque séquentiel, qui se produisent uniquement dans les fichiers journaux des transactions.<br /><br /> Fichiers journaux de transactions sont lues à partir uniquement lorsqu’ils sont lu, par exemple après une base de données de restauration ou lorsqu’un serveur n’est pas correctement l’arrêt. Les caches plus grands autorisent davantage de données en mémoire tampon, ce qui signifie que des périodes plus longues de saturation est possible. Si votre contrôleur vous permet de configurer la taille de page du cache, vous devez le définir à 4 Ko. Une taille importante, telles que de 8 Ko, aboutit à gaspiller la mémoire cache, car une demande d’e/s de 4 Ko occupe la page de l’intégralité du cache de 8 Ko, ce qui coupe votre cache utilisable dans la moitié.|  
|Piles|Piles de disques sont plus importantes que la capacité et les performances de BizTalk Server sont améliorées si les piles prend en charge un grand nombre de demandes d’e/s aléatoires. Plan pour ne plus de 80 pour cent de l’utilisation pour garantir des e/s suffisante est disponible, même en cas de défaillance d’une pile totale.|  
|RAID|La solution RAID que vous utilisez doit être basée sur les coûts et les performances compromis qui sont appropriées pour votre environnement. Par conséquent, plusieurs types de solution RAID peut vous être recommandé pour une exigence de stockage de données particulier. Recommandations générales sont les suivantes :<br /><br /> -Utilisez Raid-1 + 0 (agrégats par bande dans un jeu en miroir) pour les bases de données BizTalk Server.<br />-Utilisez Raid-1 (jeu de mise en miroir sans parité) pour les volumes de fichier journal des transactions.<br />-En général, Raid 5 (ensemble agrégé par bandes avec parité distribuée) n’est pas recommandé que Raid 5 ne fournit pas de fiabilité optimales, la disponibilité et les performances par rapport aux autres configurations Raid.<br />-En raison de la possibilité de perte définitive des données, une configuration Raid-0 (agrégat sans parité) ne doit jamais être utilisée dans un environnement de production BizTalk Server.|  
|Type de bus|Un débit plus élevé offre de meilleures performances. En général, les bus SCSI fournissent une meilleure débit et extensibilité que les bus IDE ou ATA. Vous pouvez utiliser l’équation suivante pour déterminer la limite de débit théorique pour votre type de bus :<br /><br /> (Vitesse du bus (en bits) / 8 bits par octet) X la vitesse d’exploitation (en MHz) = débit (en Mo/s)<br /><br /> Vous pouvez également améliorer les performances d’e/s de disque en plaçant plusieurs lecteurs sur le bus d’e/s distincts.|  
  
#### <a name="performance-counters-for-measuring-disk-io-bottlenecks"></a>Compteurs de performance pour mesurer les goulots d’étranglement des e/s disque  
  
> [!NOTE]
>  Lorsque vous tentez d’analyser les goulots d’étranglement des performances de disque, vous devez toujours utiliser les compteurs de disque physique. Toutefois, si vous utilisez les volumes RAID logiciels, vous devez utiliser les compteurs de disque logique. Comme pour le disque logique et les compteurs de disque physique, les mêmes compteurs sont disponibles dans chacun de ces objets de compteur. Les données de disque logique sont suivies par le Gestionnaire de volume (ou gestionnaires) et les données du disque physique sont suivies par le Gestionnaire de partition.  
  
 Les compteurs de performances suivants doivent être utilisés pour déterminer si votre système rencontre un goulot d’étranglement connexe d’e/s disque :  
  
-   **Disque Physique\moy. Longueur de file d’attente de disque**  
  
    -   Seuil : Ne doit pas être supérieure au nombre de piles plus deux.  
  
    -   Importance : Ce compteur indique le nombre moyen d’un accès en lecture et écrit les demandes qui ont été mises en attente pour le disque sélectionné pendant l’intervalle échantillon. Ce compteur est utile pour la collecte des données de concurrence, y compris les pics de données et des pics. Ces valeurs représentent le nombre de demandes en vol au-dessous du pilote effectuant les statistiques. Cela signifie que les demandes ne sont pas nécessairement mises en attente, mais peuvent être dans un service ou s’est terminée et sur la façon de sauvegarder le chemin d’accès. Emplacements en vol possibles sont les suivantes :  
  
        -   File d’attente SCSIport ou Storport  
  
        -   File d’attente du pilote OEM  
  
        -   File d’attente du contrôleur de disque  
  
        -   File d’attente du disque dur  
  
        -   Réception active à partir d’un disque dur  
  
-   **Disque Physique\moy. Longueur de file d’attente de lecture du disque**  
  
    -   Le seuil : Doit être inférieur à deux.  
  
    -   Importance : Ce compteur indique le nombre moyen de demandes de lecture ont été mises en attente pour le disque sélectionné pendant l’intervalle échantillon.  
  
-   **Disque Physique\moy. Longueur de file d’attente écriture disque**  
  
    -   Le seuil : Doit être inférieur à deux.  
  
    -   Importance : Ce compteur indique le nombre moyen de demandes d’écriture qui ont été mises en attente pour le disque sélectionné pendant l’intervalle échantillon.  
  
-   **Disque Physique\moy. Disque s/lecture**  
  
    -   Seuil : Aucune valeur spécifique.  
  
        -   Inférieure à 10 millisecondes (ms) = bonne  
  
        -   Entre 15 et 25 ms = juste  
  
        -   Supérieur à 25 ms = médiocre  
  
    -   Importance : Ce compteur indique la durée moyenne, en secondes, d’une opération de lecture à partir du disque de données. Si le nombre est supérieur à 25 millisecondes (ms), cela signifie que le système de disque rencontre latence lors de la lecture à partir du disque. Pour les serveurs critiques de BizTalk Server d’hébergement, le seuil acceptable est beaucoup plus faible, environ 10 ms.  
  
-   **Disque Physique\moy. Disque s/écriture**  
  
    -   Seuil : Aucune valeur spécifique.  
  
        -   Inférieure à 10 millisecondes (ms) = bonne  
  
        -   Entre 15 et 25 ms = juste  
  
        -   Supérieur à 25 ms = médiocre  
  
    -   Importance : Ce compteur indique la durée moyenne, en secondes, d’une donnée de l’opération d’écriture sur le disque. Si le nombre est supérieur à 25 ms, le système de disques des problèmes de latence lors de l’écriture sur le disque. Pour les serveurs critiques de BizTalk Server d’hébergement, le seuil acceptable est beaucoup plus faible, environ 10 ms.  
  
-   **Disque Physique\moy. Disque s/transfert**  
  
    -   Seuil : Ne doit pas être plus de 18 millisecondes.  
  
    -   Importance : Ce compteur indique la durée, en secondes, de transfert sur le disque. Cela peut indiquer une grande quantité de fragmentation du disque, des disques lents ou des défaillances de disque. Multiplier les valeurs de la **physique\Moy. Disque s/transfert** et **Mémoire\Pages/s** compteurs. Si le produit de ces compteurs dépasse 0,1, la pagination prend plus de 10 % de temps d’accès de disque, vous avez besoin de davantage de mémoire physique disponible.  
  
-   **PhysicalDisk\Disk Writes/sec**  
  
    -   Seuil : Dépend du fabricant.  
  
    -   Importance : Ce compteur indique le taux d’opérations d’écriture sur le disque.  
  
-   **Processeur\\% temps DPC, % temps d’interruption et % temps privilégié -** si du temps d’interruption et la durée des appels de procédure différés (DPC) sont une grande partie du temps privilégié, le noyau consacre beaucoup de temps à traiter les demandes d’e/s. Dans certains cas de performances peuvent être améliorées en configurant des interruptions et l’affinité DPC à un petit nombre de processeurs sur un système multiprocesseur, ce qui améliore la localité du cache. Dans d’autres cas, il fonctionne mieux pour distribuer les interruptions et les appels DPC entre plusieurs processeurs, afin de conserver l’interruption et l’activité DPC de devenir un goulot d’étranglement. Pour plus d’informations sur l’utilisation de l’outil de Configuration du filtre d’interruption pour lier des interruptions de carte réseau sur des processeurs spécifiques sur les ordinateurs multiprocesseurs, consultez la section « utiliser l’outil de Configuration du filtre d’interruption à lier à des interruptions de carte réseau spécifique processeurs sur les ordinateurs multiprocesseurs » dans [optimisation des performances de système d’exploitation](~/technical-guides/optimizing-operating-system-performance.md).  
  
-   **Processor\DPCs la file d’attente / s -** mesure comment DPC consomment des ressources de temps et de noyau de processeur.  
  
-   **Processeur Interruptions / s -** une autre mesure de comment interruptions consomment des ressources de temps et de noyau de processeur. Contrôleurs de disque modernes combinent souvent ou interruptions de fusion afin que les résultats d’une interruption unique lors du traitement de plusieurs achèvement d’e/s. Bien entendu, il existe un compromis entre retarder les interruptions (et donc les achèvements) et ainsi réduits le temps de traitement du processeur.  
  
#### <a name="disk-io-tuning-options"></a>Options de paramétrage d’e/s disque  
 Si vous déterminez que les e/s disque est un goulot d’étranglement dans votre environnement, les techniques suivantes peuvent être utilisées afin d’atténuer le goulot d’étranglement :  
  
-   **Défragmentez vos disques -** utiliser les fonctionnalités disponibles à [utilitaire PageDefrag](http://go.microsoft.com/fwlink/?LinkId=108976) (http://go.microsoft.com/fwlink/?LinkId=108976) pour défragmenter le fichier de pagination Windows et allouer à l’avance les Tables de fichiers principal.  
  
-   **Agrégats par bande utiliser pour traiter les demandes d’e/s simultanément sur plusieurs disques -** volumes en miroir permet de fournir une tolérance de panne et d’augmenter les performances d’e/s. Si vous n’avez pas besoin d’une tolérance de panne, implémentez les agrégats de lecture et en écriture et rapidement améliorée de la capacité de stockage. Lorsque les agrégats sont utilisées, par disque utilisation est réduite, car le travail est réparti entre les volumes et le débit global augmente. Si vous l’ajout de disques supplémentaires dans une bande définissez n’augmente pas le débit, puis votre système rencontre peut-être un goulot d’étranglement en raison de conflits entre les disques par le contrôleur de disque. Dans ce cas, ajout d’un contrôleur de disque supplémentaire permet de distribuer la charge et améliorer les performances.  
  
-   **Distribuer la charge de travail entre plusieurs disques -** Clustering Windows et le système de fichiers distribués d’offrir des solutions pour l’équilibrage de charge sur plusieurs lecteurs de disque.  
  
-   **Limitez l’utilisation de la compression de fichiers ou de chiffrement -** le chiffrement et la compression de fichiers sont des opérations d’e/S intensives. Vous devez uniquement utiliser les cas d’absolue nécessité.  
  
-   **Désactiver la création des noms courts -** si vous ne sont pas en charge les clients MS-DOS pour Windows 3.x, désactiver des noms courts pour améliorer les performances. Pour plus d’informations sur la désactivation de la création des noms courts, consultez la section « Désactiver la génération de nom de fichier court (8.3) » dans [optimisation des performances de système d’exploitation](~/technical-guides/optimizing-operating-system-performance.md).  
  
-   **Désactiver la dernière mise à jour de l’accès -** par défaut, NTFS met à jour le cachet de date et heure du dernier accès sur les répertoires lorsqu’il traverse le répertoire. Pour un volume NTFS volumineux, ce processus de mise à jour peut affecter les performances. Pour plus d’informations sur la désactivation des mises à jour de derniers accès, consultez la section « Désactiver les mises à jour de l’accès dernière NTFS » dans [optimisation des performances de système d’exploitation](~/technical-guides/optimizing-operating-system-performance.md).  
  
    > [!CAUTION]
    >  Certaines applications, telles que les utilitaires de sauvegarde incrémentielle, s’appuient sur les informations de mise à jour NTFS et ne fonctionnera pas correctement sans lui.  
  
-   **Réserver l’espace approprié pour la table de fichier maître -** ajouter la **NtfsMftZoneReservation** entrée dans le Registre en fonction du nombre de fichiers qui sont généralement stockés sur les volumes NTFS. Lorsque vous ajoutez cette entrée au Registre, le système réserve l’espace sur le volume pour la table de fichiers principal. Réservation d’espace de cette manière permet à la table de fichier maître de croître de manière optimale. Si vos volumes NTFS stockent généralement relativement peu de fichiers, définissez la valeur de cette entrée de Registre à la valeur par défaut de 1. En règle générale, vous pouvez utiliser une valeur de 2 ou 3 si vos volumes NTFS stocker un nombre modéré de fichiers, utilisent la valeur 4 (maximum) si vos volumes NTFS ont tendance à contenir un nombre relativement important de fichiers. Toutefois, veillez à tester des paramètres supérieurs à 2, car ces valeurs supérieures au système de réserver une plus grande partie du disque pour la table de fichiers principal. Pour plus d’informations sur l’ajout de la **NtfsMftZoneReservation** dans le Registre, consultez la section « augmentation espace disponible pour la table de fichier maître » dans [optimisation des performances de système d’exploitation](~/technical-guides/optimizing-operating-system-performance.md).  
  
-   **Utiliser les systèmes de disque plus efficaces disponibles -** en plus du disque physique qui est utilisé, envisagez le type de contrôleur de disque et le câblage qui sera utilisé. Un sous-système de disque efficace doit également fournir des pilotes qui prennent en charge de modération de l’interruption ou de prévention de l’interruption pour atténuer l’activité d’interruption processeur due à des e/s disque.  
  
-   **Vérifiez que vous utilisez la configuration RAID appropriée -** utilisez RAID 10 (répartition et la mise en miroir) pour optimiser performances et tolérance de panne. L’inconvénient est qu’à l’aide de RAID 10 est onéreux. Évitez d’utiliser des volumes RAID 5 lorsque vous avez des opérations d’écriture complète. Pour plus d’informations sur l’implémentation de RAID dans un environnement BizTalk Server, consultez la section « Disque Infrastructure » dans le [livre blanc de l’optimisation de base de données BizTalk Server](http://go.microsoft.com/fwlink/?LinkID=101578) (http://go.microsoft.com/fwlink/?LinkID=101578).  
  
-   **Envisagez l’utilisation de partitions de base de données -** si vous avez un goulot d’étranglement de la base de données, envisagez d’utiliser des partitions de base de données et de mappage des disques à des tables spécifiques et des journaux de transactions. L’objectif principal de partitions est à surmonter les goulots d’étranglement du disque pour les tables volumineuses. Si vous avez une table avec un grand nombre de lignes et que vous constatez qu’il est la source d’un goulot d’étranglement, envisagez d’utiliser des partitions. Pour SQL Server, vous pouvez utiliser des groupes de fichiers pour améliorer les performances d’e/s. Vous pouvez associer les tables de groupes de fichiers et puis associer les groupes de fichiers avec un disque dur spécifique. Pour plus d’informations sur l’utilisation de groupes de fichiers optimisé pour les bases de données BizTalk Server, consultez [optimisation de groupes de fichiers pour les bases de données](~/technical-guides/optimizing-filegroups-for-the-databases2.md).  
  
-   **Ajout de mémoire physique, si vous avez des erreurs de page excessif -** une valeur élevée pour le **mémoire : Pages/s** compteur de performance peut indiquer une pagination excessive qui augmentera disque I / 0. Si cela se produit, envisagez d’ajouter de la mémoire physique pour réduire les e/s disque et améliorer les performances.  
  
-   **Envisagez d’utiliser un disque avec une vitesse est élevée, évaluation ou à l’aide d’un réseau de zone de stockage (SAN) périphérique -** disques dont le niveau supérieur tpm offrent de meilleures performances par rapport aux disques dont le niveau inférieur tr/min. Périphériques SAN offrent des performances de niveau supérieur mais à un supplément.  
  
-   Suivez les recommandations de [optimisation des performances de base de données](~/technical-guides/optimizing-database-performance.md). Cette rubrique fournit quelques recommandations pour optimiser les performances de base de données avant et après la configuration de BizTalk Server.  
  
### <a name="cpu-bottlenecks"></a>Goulots d’étranglement du processeur  
 Chaque application qui s’exécute sur un serveur obtienne une tranche de temps du processeur. L’UC peut être en mesure de gérer efficacement tous les processus en cours d’exécution sur l’ordinateur, ou il est peut-être surchargé. En examinant l’activité du processeur et l’activité des processus individuels, y compris la création de threads, en basculant de thread et commutation de contexte, vous pouvez obtenir un aperçu de la charge du processeur et les performances.  
  
#### <a name="you-may-have-a-cpu-bottleneck-if"></a>Vous pouvez avoir un goulot d’étranglement du processeur si...  
  
-   La valeur de la **processeur\\% temps processeur** compteur de performances est souvent supérieure à 75 %.  
  
-   La valeur de la **longueur de file d’attente du processeur transcription** compteur de performances est de 2 ou plus pour une période prolongée.  
  
-   La valeur de la **processeur\\% temps privilégié** ou **Système\Changements de contexte/s** les compteurs de performance sont exceptionnellement élevées.  
  
     Si la valeur de **Processor\ % temps processeur** compteur de performances est élevé, puis queuing se produit et dans la plupart des scénarios de la valeur de **longueur de file d’attente du processeur système** peuvent également être élevé.  
  
#### <a name="performance-counters-for-measuring-cpu-bottlenecks"></a>Compteurs de performance pour mesurer les goulots d’étranglement du processeur  
 Les compteurs de performances suivants doivent être utilisés pour déterminer si votre système rencontre un goulot d’étranglement connexe de l’UC :  
  
-   **Processeur\\% temps processeur**  
  
    -   Seuil : Doit être inférieur à 85 %.  
  
    -   Importance : Ce compteur est l’indicateur principal de l’activité du processeur. Haute valeurs nombreux pas nécessairement être incorrect. Toutefois, si les autres compteurs relatifs au processeur augmente proportionnellement au nombre tel que **processeur\\% temps privilégié** ou **Système\longueur de file d’attente**, utilisation élevée du processeur, il peut être intéressant le problème.  
  
-   **Processeur\\% temps privilégié**  
  
    -   Seuil : Un graphique qui est constamment sur 75 pour cent indique un goulot d’étranglement.  
  
    -   Importance : Ce compteur indique le pourcentage de temps qu'un thread s’exécute en mode privilégié. Lorsque votre application appelle les fonctions de système d’exploitation (par exemple pour effectuer des e/s de fichier ou de réseau ou pour allouer de la mémoire), ces fonctions de système d’exploitation sont exécutées en mode privilégié.  
  
-   **Processeur\\% temps d’interruption**  
  
    -   Seuil : Dépend du processeur.  
  
    -   Importance : Ce compteur indique le pourcentage de temps que le processeur consacre à des interruptions matérielles réception et de maintenance. Cette valeur est un indicateur indirect de l’activité des périphériques qui génèrent des interruptions, tels que des cartes réseau. Une augmentation considérable de ce compteur indique des problèmes de matériel.  
  
-   **Système\longueur de file d’attente**  
  
    -   Seuil : Une valeur moyenne constamment supérieure à 2 indique un goulot d’étranglement.  
  
    -   Importance : S’il existe plusieurs tâches prêts à être exécuté qu’il sont a de processeurs, threads de file d’attente. La file d’attente du processeur est la collection de threads qui sont prêts, mais n’a pas pu être exécuté par le processeur, car un autre thread en cours d’exécution. Une file d’attente prolongée ou périodique de plus de deux threads est une indication d’un goulot d’étranglement de processeur. Vous pouvez obtenir plus de débit en réduisant le parallélisme dans ces cas.  
  
         Vous pouvez utiliser ce compteur conjointement avec la **processeur\\% temps processeur** compteur pour déterminer si votre application peut tirer parti des processeurs plus. Il concerne une seule file d’attente de temps processeur, même sur les ordinateurs multiprocesseurs. Par conséquent, sur un ordinateur multiprocesseur, divisez la valeur de longueur de file d’attente de processeur (PQL) par le nombre de processeurs desservant la charge de travail.  
  
         Si l’UC est très occupé (90 pour cent ou une utilisation plus importante) et la moyenne PQL est constamment supérieure à 2 par processeur, vous pouvez avoir un goulot d’étranglement de processeur qui peut tirer parti de l’ajout de processeurs. Ou bien, vous pouvez réduire le nombre de threads et de file d’attente plus au niveau de l’application. Cela provoquera moins de changements de contexte et moins de changements de contexte est valable pour réduire la charge de l’UC. Une raison courante de valeur PQL 2 ou version ultérieure avec utilisation faible du processeur est que pour le temps processeur, les demandes arrivent au hasard et threads demande irrégulières quantités de temps du processeur. Cela signifie que le processeur n’est pas un goulet d’étranglement, mais que l’application de thread doit être améliorée.  
  
-   **System\Context Switches/sec**  
  
    -   Seuil : En règle générale, un changement de contexte du taux de moins de 5 000 par seconde par le processeur n’est pas utile soucier. Si le taux de changement de contexte dépassent 15 000 par seconde par le processeur, ce phénomène peut alors un goulot d’étranglement.  
  
    -   Importance : Changement de contexte se produit lorsqu’un thread de priorité plus élevée prioritaire d’un thread de priorité plus faible qui est en cours d’exécution ou lorsqu’un thread de priorité élevée empêche les autres threads. Les niveaux élevés de changement de contexte peuvent se produire lorsque de nombreux threads partagent le même niveau de priorité. Ceci indique souvent qu’il n’y a trop de threads en concurrence pour les processeurs sur le système. Si l’utilisation du processeur et niveaux de changement de contexte sont faibles, ceci indique souvent que les threads sont bloqués.  
  
#### <a name="resolving-cpu-bottlenecks"></a>Résolution des engorgements du processeur  
 La première étape consiste à identifier le processus qui consomme trop de temps processeur. Utiliser Windows **le Gestionnaire des tâches** pour identifier le processus qui consomme des niveaux élevés de processeur en examinant le **processeur** colonne sur le **processus** page. Vous pouvez également le déterminer en surveillant **processus\\% temps processeur** dans l’Analyseur de performances et en sélectionnant les processus que vous souhaitez surveiller.  
  
 Un autre outil puissant permettant de déterminer les processus qui consomment trop de temps processeur est le profileur Visual Studio Team System qui est inclus dans la suite Visual Studio Team System (VSTS). Pour plus d’informations sur l’utilisation de Visual Studio Team System Profiler, consultez la documentation de Visual Studio Team System.  
  
 Après avoir déterminé que votre processeur est un goulot d’étranglement que vous disposez de plusieurs options, notamment les suivantes :  
  
-   Ajout de plusieurs processeurs si vous avez des applications multithread. Envisagez de mettre à niveau vers un processeur plus puissant si votre application est monothread.  
  
-   Si vous observez un taux élevé de changement de contexte, pensez à réduire le nombre de threads pour votre processus avant d’augmenter le nombre de processeurs.  
  
-   Analyser et paramétrer l’application qui provoque une utilisation élevée du processeur. Vous pouvez vider le processus en cours d’exécution à l’aide de l’utilitaire ADPLUS et analyser la cause à l’aide de Windbg. Ces utilitaires font partie de la boîte à outils de débogage de Windows. Vous pouvez télécharger ces outils à partir de [outils de débogage pour Windows](http://go.microsoft.com/fwlink/?LinkID=106624) (http://go.microsoft.com/fwlink/?LinkID=106624).  
  
-   Analyser le journal d’instrumentation généré par votre application afin d’isoler le sous-système qui est en cours de la durée maximale d’exécution. Déterminer si une révision du code serait préférable que le paramétrage de simplement l’environnement BizTalk Server.  
  
> [!NOTE]
>  Bien que vous pouvez modifier le niveau de priorité de processus d’une application à l’aide de **le Gestionnaire des tâches** ou à partir d’une invite de commandes, vous devez généralement éviter cela.  
  
### <a name="memory-bottlenecks"></a>Goulots d’étranglement de la mémoire  
 Lorsque vous évaluez les goulots d’étranglement liés à la mémoire, envisagez d’allocations inutiles, inefficace de nettoyage et s’avère inapproprié mise en cache et les mécanismes de gestion d’état. Pour résoudre les goulots d’étranglement liés à la mémoire, optimiser votre code pour résoudre ces problèmes et ensuite le paramétrer la quantité de mémoire allouée à vos applications. Si vous déterminez que la contention de mémoire et une pagination excessive sont produisent, vous devrez peut-être ajouter de la mémoire physique sur le serveur pendant le paramétrage. Insuffisance de mémoire entraîne une pagination accrue d’espace d’adressage virtuel d’une application vers et depuis le disque. Si la pagination est excessive, e/s disque augmente et nuire aux performances globales du système.  
  
#### <a name="you-might-have-a-memory-bottleneck-if"></a>Vous pouvez avoir un goulot d’étranglement de la mémoire si...  
  
-   La valeur de la **Memory\Available MBytes** compteur de performances est faible, en raison de limitations de mémoire système ou d’une application qui ne libère pas la mémoire. Analyser la valeur de la **Collecte\** compteur de performance pour chaque processus qui s’exécute. Si la valeur de la **Collecte\** reste élevé même lorsque le processus n’est pas actif, cela peut indiquer que le processus ne libère pas la mémoire comme il le devrait.  
  
-   La valeur de la **Mémoire\Pages/s** compteur de performances est élevé. La moyenne de **Mémoire\Pages en entrée/s** divisée par la moyenne de **Mémoire\Lectures de pages/s** donne le nombre de pages par lecture sur le disque. Cette valeur ne doit généralement pas dépasser cinq pages par seconde. Une valeur supérieure à cinq pages par seconde indique que le système passe trop de pagination de temps et requiert plus de mémoire (en supposant que l’application a été optimisée).  
  
#### <a name="performance-counters-for-measuring-memory-bottlenecks"></a>Compteurs de performance pour mesurer les goulots d’étranglement de la mémoire  
 Les compteurs de performances suivants doivent être utilisés pour déterminer si votre système rencontre un goulot d’étranglement connexes mémoire :  
  
-   **Memory\Available Mbytes**  
  
    -   Seuil : Une valeur cohérente de moins de 20 à 25 pour cent de mémoire vive est une indication de la quantité de mémoire insuffisante.  
  
    -   Importance : Cela indique la quantité de mémoire physique disponible pour les processus en cours d’exécution sur l’ordinateur. Notez que ce compteur affiche la dernière valeur observée. Il n’est pas une moyenne.  
  
-   **Memory\Page Reads/sec**  
  
    -   Seuil : Des valeurs soutenues de plus de cinq indiquent un grand nombre de défauts de page pour les demandes de lecture.  
  
    -   Importance : Ce compteur indique que le jeu de travail d’un processus est trop grand pour la mémoire physique disponible qui est la cause de mémoire à la page sur le disque. Il affiche le nombre d’opérations de lecture, indépendamment du nombre de pages extraites lors de chaque opération. Des valeurs supérieures indiquent un goulot d’étranglement de la mémoire.  
  
         Si un faible taux d’opérations de lecture de page coïncide avec des valeurs pour **disque physique\\% temps du disque** et **physique\Moy. Longueur de file d’attente du disque**, un condition de goulot d’étranglement d’e/s disque peut-être exister. Si une augmentation de la longueur de file d’attente n’est pas accompagnée d’une diminution du taux de lectures de pages, il existe un goulot d’étranglement de la mémoire en raison d’une insuffisance de mémoire physique.  
  
-   **Memory\Pages/sec**  
  
    -   Seuil : Une valeur soutenue de plus de cinq indique un goulot d’étranglement.  
  
    -   Importance : Ce compteur indique le taux auquel les pages sont lues ou écrites sur le disque afin de résoudre des défauts de page. Multiplier les valeurs de la **physique\Moy. Disque s/transfert** et **Mémoire\Pages/s** les compteurs de performance. Si le produit de ces valeurs dépasse **0,1**, la pagination est utilisant plus de 10 % de temps d’accès de disque, ce qui indique que l’insuffisance de mémoire physique est disponible.  
  
-   **Mémoire\Octets octets de réserve non paginées**  
  
    -   Seuil : Examinez la valeur de **Mémoire\octets de réserve non paginée** une augmentation d’au moins 10 pour cent de sa valeur au démarrage du système.  
  
    -   Signification : Une augmentation de 10 pour cent ou plus à partir de la valeur de démarrage peut être une indication d’une fuite de mémoire.  
  
-   **Serveur\Octets échecs de réserve non paginées**  
  
    -   Seuil : Des valeurs différentes de zéro régulières indiquent un goulot d’étranglement.  
  
    -   Importance : Ce compteur indique le nombre de fois où les allocations à partir de la réserve non paginée ont échoué. La réserve non paginée contient des pages à partir de l’espace d’adressage virtuel d’un processus qui ne doivent ne pas être permutée vers le fichier d’échange sur le disque, par exemple un tableau d’objets de processus noyau. La disponibilité de la réserve non paginée détermine le nombre des processus, threads et autres ces objets peuvent être créés. En cas d’échouent d’allocations à partir de la réserve non paginée, cela peut être dû à une fuite de mémoire dans un processus, en particulier si l’utilisation du processeur n’a pas augmenté en conséquence.  
  
-   **Échecs de Serveur\réserve**  
  
    -   Seuil : Aucune valeur spécifique.  
  
    -   Importance : Ce compteur indique le nombre de fois où les allocations à partir de la réserve paginée ont échoué. Une valeur positive pour ce compteur est une indication que l’ordinateur dispose d’une mémoire physique insuffisante ou que le fichier d’échange Windows est trop petit.  
  
-   **Serveur\Octets maxi.**  
  
    -   Seuil : Aucune valeur spécifique.  
  
    -   Importance : Il s’agit du nombre maximal d’octets dans la réserve non paginée que le serveur a réservé pour une utilisation à un point quelconque. Il indique la quantité de mémoire physique l’ordinateur doit avoir. Étant donné que la réserve non paginée doit résider dans la mémoire physique et, car il doit être certains de la mémoire pour d’autres opérations, comme le principe de l’ordinateur doit être installée de mémoire physique qui est de 4 fois la valeur indiquée pour ce compteur.  
  
-   **Memory\Cache Bytes**  
  
    -   Seuil : Aucune valeur spécifique.  
  
    -   Importance : Contrôle la taille du cache dans des conditions de charge différents. Cette valeur de ce compteur de performance indique la taille du cache de fichiers statiques. Par défaut, ce compteur utilise environ 50 % de mémoire disponible, mais diminue si la mémoire disponible est réduit, ce qui affecte les performances du système.  
  
-   **Memory\Cache Faults/sec**  
  
    -   Seuil : Aucune valeur spécifique.  
  
    -   Importance : Ce compteur indique la fréquence à laquelle le système d’exploitation recherche des données dans le cache du système de fichiers, mais ne parvient pas à trouver. Cette valeur doit être aussi faible que possible.  
  
-   **% De correspondances dans Cache\MDL lecture**  
  
    -   Seuil : Plus cette valeur, meilleures sont les performances du cache du système de fichier. Valeurs doivent être aussi proche que possible à 100 pour cent.  
  
    -   Importance : Ce compteur fournit le pourcentage de mémoire descripteur de liste (MDL) demandes de lecture sur le cache du système de fichiers, où le cache retourne l’objet directement au lieu de nécessiter une lecture à partir du disque dur.  
  
-   **Process\Working Set**  
  
    -   Seuil : Aucune valeur spécifique.  
  
    -   Signification : Le jeu de travail est l’ensemble de pages de mémoire actuellement chargée en mémoire (physique + virtuelle). Si le système dispose de suffisamment de mémoire, il ne peut gérer suffisamment d’espace dans le jeu de travail afin qu’il est inutile effectuer des opérations de disque pour la mémoire de pages sur le disque. Toutefois, si la mémoire est insuffisante, le système essaie de réduire la plage de travail en effectuant immédiatement la mémoire de processus, ce qui entraîne une augmentation de défauts de page. Lorsque le taux de défauts de page augmente, le système tente d’augmenter la plage de travail du processus. Si vous observez les fluctuations importantes dans le jeu de travail, il peut indiquer un manque de mémoire. Valeurs supérieures dans la plage de travail peuvent également être dû à plusieurs assemblys dans une application. Vous pouvez améliorer la plage de travail à l’aide des assemblys partagés dans le global assembly cache.  
  
#### <a name="resolving-memory-bottlenecks"></a>Résolution des engorgements de la mémoire  
 Si vous déterminez que la mémoire est un goulot d’étranglement dans votre environnement BizTalk Server, utilisez un ou plusieurs des méthodes suivantes pour résoudre le goulot d’étranglement :  
  
-   Régler la quantité de mémoire allouée si vous pouvez contrôler l’allocation. Par exemple, vous pouvez le paramétrer pour BizTalk Server, ASP.NET et SQL Server.  
  
-   Augmenter la taille du fichier d’échange Windows et suivez les étapes décrites dans la section « Configurer le fichier d’échange Windows pour des performances optimales » de [optimisation des performances de système d’exploitation](~/technical-guides/optimizing-operating-system-performance.md).  
  
-   Désactiver les services qui ne sont pas utilisés. Arrêt des services que vous n’utilisez pas régulièrement économise de la mémoire et améliore les performances système. Pour plus d’informations, consultez la section « Désactiver les services superflus » de [optimisation des performances de système d’exploitation](~/technical-guides/optimizing-operating-system-performance.md).  
  
-   Supprimer des pilotes et les protocoles inutilisés. Protocoles inactifs même utilisent l’espace dans les pools de mémoire paginée et non paginée. Pilotes consomment également la mémoire, vous devez supprimer ceux qui sont inutiles. Pour plus d’informations, consultez la section « Supprimer les protocoles réseau inutiles » de [optimisation des performances de système d’exploitation](~/technical-guides/optimizing-operating-system-performance.md).  
  
-   Installez la mémoire physique supplémentaire sur les ordinateurs dans l’environnement BizTalk Server.  
  
> [!NOTE]
>  Sur un système 32 bits, BizTalk peut utiliser un maximum de 2 Go de mémoire, la limite augmente à 3 Go avec BizTalk Server 2010 et versions ultérieures, si le commutateur/3 GB est utilisé. Pour plus d’informations sur l’utilisation de la mémoire, consultez [limites de mémoire pour les versions Windows](http://go.microsoft.com/fwlink/?LinkId=118349) (http://go.microsoft.com/fwlink/?LinkId=118349).  
  
### <a name="network-io-bottlenecks"></a>Goulots d’étranglement des e/s réseau  
  
#### <a name="you-might-have-a-network-io-bottleneck-if"></a>Vous pouvez avoir un goulot d’étranglement des e/s réseau si...  
  
-   La valeur de la **réseau\Total des octets/s** compteur de performances dépasse 80 % de la bande passante réseau disponible.  
  
-   La valeur de la **nntp\total des octets/s** compteur de performances est supérieur à 50 % de la bande passante réseau disponible.  
  
#### <a name="performance-counters-for-measuring-network-io-bottlenecks"></a>Compteurs de performance pour mesurer les goulots d’étranglement des e/s réseau  
 Les compteurs de performances suivants doivent être utilisés pour mesurer les e/s réseau et de déterminer si votre système rencontre un goulot d’étranglement réseau d’e/s associée :  
  
-   **Network Interface réseau\Total des octets/s**  
  
    -   Seuil : Valeur soutenue de plus de 80 pour cent de la capacité du réseau.  
  
    -   Importance : Ce compteur indique le taux auquel les octets sont envoyés et reçus via chaque carte réseau. Ce compteur permet de déterminer si une carte réseau est saturée, et si vous devez ajouter une ou plusieurs cartes réseau pour augmenter la bande passante réseau disponible.  
  
-   **Network Interface\Bytes Received/sec**  
  
    -   Seuil : Aucune valeur spécifique.  
  
    -   Importance : Ce compteur indique le taux auquel les octets sont reçus via chaque carte réseau. Utilisez la valeur de ce compteur pour calculer le taux de données entrantes sous forme de pourcentage de bande passante disponible totale. Cela permet de déterminer si la bande passante réseau doit être augmentée sur les client envoie des données BizTalk Server ou si la bande passante réseau doit être augmentée sur l’ordinateur BizTalk Server lui-même.  
  
-   **Network Interface\Bytes Sent/sec**  
  
    -   Seuil : Aucune valeur spécifique.  
  
    -   Importance : Ce compteur indique la vitesse à laquelle les octets sont envoyés via chaque carte réseau. Utilisez la valeur de ce compteur pour calculer le taux de données sortantes sous forme de pourcentage de bande passante disponible totale. Cela permet de déterminer si la bande passante réseau doit être augmentée sur les données d’envoi BizTalk Server à un client ou si la bande passante réseau doit être augmentée sur le client ordinateur réception de données à partir de BizTalk Server.  
  
-   **Server\Bytes Total/sec**  
  
    -   Seuil : Valeur soutenue de plus de 50 % de la capacité du réseau.  
  
    -   Importance : Ce compteur indique le nombre d’octets envoyés et reçus sur le réseau. Des valeurs supérieures indiquent un goulot d’étranglement des e/s réseau. Si la somme des **Total des octets/s** pour tous les serveurs est à peu près égale à la vitesse de transfert de votre réseau, envisagez les sous-réseaux du réseau pour améliorer les performances. Pour plus d’informations sur les sous-réseaux d’un réseau pour améliorer les performances, consultez le **sous-réseaux** section de la [livre blanc de l’optimisation de base de données BizTalk Server](http://go.microsoft.com/fwlink/?LinkID=101578) (http://go.microsoft.com/fwlink/?LinkID=101578).  
  
#### <a name="resolving-network-io-bottlenecks"></a>Résoudre les goulots d’étranglement des e/s réseau  
 Si vous déterminez que les e/s réseau est un goulot d’étranglement dans votre environnement, vous devez utiliser une ou plusieurs des méthodes suivantes pour résoudre le goulot d’étranglement :  
  
-   Suivez les recommandations de la section « Instructions générales pour améliorer les performances du réseau » de [optimisation des performances réseau](~/technical-guides/optimizing-network-performance.md).  
  
-   Exécutez le script de l’optimisation du réseau Windows Powershell décrit dans la rubrique [optimisation des performances réseau](~/technical-guides/optimizing-network-performance.md) sur chaque ordinateur dans l’environnement BizTalk Server.  
  
## <a name="see-also"></a>Voir aussi  
 [Recherche et suppression des goulots d’étranglement](~/technical-guides/finding-and-eliminating-bottlenecks.md)