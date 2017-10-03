---
title: "Instructions générales pour l’amélioration des performances réseau | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 286c10d2-9262-4e3c-adde-f7b5780c2736
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 67b76a7e488610a72952832d2a84526ca60d6989
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="general-guidelines-for-improving-network-performance"></a>Instructions générales pour améliorer les performances du réseau
Réglage des paramètres de réseau pour les valeurs optimales a été indiqué pour résoudre les goulots d’étranglement du réseau et améliorer les performances du réseau dans les solutions BizTalk Server efficacement. Cela doit être effectuée sur tous les ordinateurs impliqués dans la solution, y compris les ordinateurs BizTalk Server, les ordinateurs SQL Server et tous les autres ordinateurs du serveur.  
  
> [!NOTE]  
>  Le symptôme le plus courant que les e/s réseau est un goulot d’étranglement dans un environnement BizTalk Server est le compteur « Attentes de SQL Server : attente Statistics\Network e/s ». Lorsque la valeur de **le temps d’attente moyen** ce compteur est supérieure à zéro sur un ou plusieurs de vos ordinateurs SQL Server, puis les e/s réseau est un goulot d’étranglement.  
  
 La recommandation suivante peut servir à améliorer les performances du réseau :  
  
## <a name="add-additional-network-cards-to-computers-in-the-biztalk-server-environment"></a>Ajouter des cartes réseau supplémentaires sur les ordinateurs dans l’environnement BizTalk Server  
 Que comme l’ajout de disques durs supplémentaires peuvent améliorer les performances du disque, les cartes réseau supplémentaires Ajout peuvent améliorer les performances réseau. Si les cartes réseau sur les ordinateurs de votre environnement BizTalk Server sont saturés et que la carte est un goulot d’étranglement, envisagez d’ajouter une ou plusieurs cartes réseau supplémentaires pour améliorer les performances.  
  
## <a name="implement-network-segmentation"></a>Implémentez la segmentation du réseau  
 Suivez les recommandations de la **sous-réseaux** section de la [livre blanc des « Optimisation de base de données BizTalk Server »](http://go.microsoft.com/fwlink/?LinkID=101578) (http://go.microsoft.com/fwlink/?LinkID=101578).  
  
## <a name="where-possible-replace-hubs-with-switches"></a>Si possible, remplacez les concentrateurs avec les commutateurs  
 Commutateurs contiennent une logique pour acheminer directement le trafic entre la source et de destination, tandis que les concentrateurs utilisent un modèle d’acheminer le trafic de diffusion. Par conséquent, les commutateurs sont plus efficaces et offrent de meilleures performances.  
  
## <a name="remove-unnecessary-network-protocols"></a>Supprimer les protocoles réseau inutiles  
 Ordinateurs Windows Server ont parfois plusieurs services et protocoles réseau installés que réellement nécessaire. Chaque client réseau supplémentaire, le service ou le protocole place supplémentaire surcharge des ressources système.  
En outre, chaque protocole installé génère un trafic réseau. En supprimant les protocoles, les services et les clients du réseau inutile, les ressources système sont disponibles pour d’autres processus, accroît le trafic réseau est évité et le nombre de liaisons de réseau qui doit être négociée est réduit au minimum.  
Pour afficher les clients du réseau actuellement installé, protocoles et les services, procédez comme suit :  
  
1.  Cliquez sur **Démarrer**, puis cliquez sur **le panneau de configuration**.  
  
2.  Dans le panneau de configuration, effectuez l’une des opérations suivantes  
  
    1.  Dans **ajuster les paramètres de votre ordinateur**, définissez **afficher par** à **catégorie**, cliquez sur **réseau et Internet**, puis cliquez sur  **Centre réseau et partage**.  
  
    2.  Dans **ajuster les paramètres de votre ordinateur**, définissez **afficher par** soit **grandes icônes** ou **petites icônes**, puis cliquez sur  **Centre réseau et partage**.  
  
3.  Dans le volet de tâches, cliquez sur **modifier les paramètres de la carte**.  
  
4.  Avec le bouton droit **connexion au réseau Local** (ou l’entrée pour votre connexion réseau), puis cliquez sur **propriétés** pour afficher la boîte de dialogue Propriétés de la connexion réseau.  
  
5.  Pour supprimer un élément inutile, sélectionnez-la, puis cliquez sur **désinstallation**. Pour désactiver un élément, désactivez simplement la case à cocher associée à l’élément.  
  
 Si vous ne savez pas sur les effets de la désinstallation d’un élément pour la connexion, puis désactivez l’élément plutôt que de le désinstaller. Désactiver les éléments vous permet de déterminer quels services, les protocoles et les clients sont réellement nécessaire sur un système. Lorsqu’il a été déterminé que la désactivation d’un élément n’a aucune incidence sur le serveur, l’élément peut ensuite être désinstallé.  
Dans de nombreux cas, uniquement les trois composants suivants sont requis pour l’opération sur un réseau TCP/IP de base standard :  
  
-   Client pour les réseaux Microsoft  
  
-   Partage de fichiers et imprimantes pour les réseaux Microsoft  
  
-   Protocole Internet (TCP/IP)  
  
## <a name="network-adapter-drivers-on-all-computers-in-the-biztalk-server-environment-should-be-tuned-for-performance"></a>Les pilotes de cartes réseau sur tous les ordinateurs dans l’environnement BizTalk Server doivent être réglées pour des performances  
  
> [!IMPORTANT]  
>  Avant d’appliquer le paramétrage à des pilotes de carte réseau toujours installer les pilotes de périphérique de carte réseau plus récentes pour les cartes réseau dans l’environnement.  
  
 Ajustez les pilotes de périphérique de carte réseau pour optimiser la quantité de mémoire disponible pour la mise en mémoire tampon de paquet, entrante et sortante. Aussi optimiser le nombre de mémoires tampons, en particulier tampons de transmission et fusionner les tampons. La valeur par défaut les valeurs pour ces paramètres et si elles sont encore fournies, varier entre les versions de pilotes et les fabricants. L’objectif est d’optimiser le travail effectué par la carte réseau et pour permettre l’espace de mémoire tampon possible plus grande pour les opérations de réseau atténuer les pics de trafic réseau et de congestion associée.  
  
> [!NOTE]  
>  Étapes pour paramétrer les pilotes de cartes réseau varient selon le fabricant.  
  
 Suivez ces étapes pour accéder aux paramètres des cartes réseau :  
  
1.  Cliquez sur **Démarrer** puis cliquez sur **le panneau de configuration**.  
  
2.  Dans le panneau de configuration, effectuez l’une des opérations suivantes :  
  
    1.  Dans **ajuster les paramètres de votre ordinateur**, définissez **afficher par** à **catégorie**, cliquez sur **réseau et Internet**, puis cliquez sur  **Centre réseau et partage**.  
  
    2.  Dans **ajuster les paramètres de votre ordinateur**, définissez **afficher par** soit **grandes icônes** ou **petites icônes**, puis cliquez sur  **Centre réseau et partage**.  
  
3.  Dans le volet de tâches, cliquez sur **modifier les paramètres de la carte**.  
  
4.  Avec le bouton droit **connexion au réseau Local** (ou le nom de votre connexion réseau), puis cliquez sur **propriétés**.  
  
5.  Sur le **réseau** , cliquez sur **configurer**.  
  
6.  Cliquez sur le **avancé** onglet pour accéder aux propriétés qui peuvent être configurés pour la carte réseau.  
  
 Les propriétés suivantes doivent être configurées pour chaque carte réseau dans l’environnement BizTalk Server :  
  
> [!NOTE]  
>  Vous appliquez ces paramètres pour chaque carte réseau physique, y compris les cartes réseau individuelles au sein d’un ensemble de cartes réseau qui sont configurées pour l’agrégation, l’équilibrage de charge ou la tolérance de panne. Avec certains logiciels de l’association de cartes, vous devrez peut-être également appliquer ces paramètres à l’équipe. Notez que certaines cartes réseau sont réglage automatique et ne proposent pas l’option pour configurer les paramètres manuellement.  
  
-   **Option d’alimentation** – configurer le pilote de carte réseau pour éviter les fonctionnalités de gestion d’alimentation à partir de la désactivation de la carte réseau à économiser de l’énergie. Cette fonctionnalité peut être utile pour les ordinateurs clients, mais doit rarement, voire jamais, utilisée sur un ordinateur BizTalk Server ou SQL Server.  
  
-   **Fixe vitesse/Duplex (n’utilisez pas AUTO)** -il est très important que la vitesse du réseau, duplex et les paramètres de contrôle de flux sont définies pour correspondre aux paramètres du commutateur à laquelle ils sont connectés. Cela limite l’occurrence de « auto-synchronisation périodique « cette opération peut être temporairement hors connexion des connexions.  
  
-   **Tampons de fusion max** -registres de mappage sont utilisés pour convertir les adresses physiques des adresses virtuelles pour les cartes réseau qui prennent en charge le contrôle du bus de ressources système. Fusionner les mémoires tampons sont disponibles pour le pilote de réseau si le pilote suffisamment de registres de mappage. Définissez cette valeur plus élevée possible pour des performances maximales. Sur les serveurs avec peu de mémoire physique, cela peut avoir une valeur négative impact que les tampons de fusion consomme de mémoire système. Sur la plupart des systèmes, toutefois, la valeur maximale peut être appliquée sans réduire considérablement la mémoire disponible.  
  
-   **Tampons d’envoi et les descripteurs de transmission/envoi max** -ce paramètre spécifie combien de transmettre des tampons de contrôle du pilote alloue pour une utilisation par l’interface réseau. Cela reflète directement le nombre de paquets en attente, que le pilote peut avoir dans sa file d’attente « envoyer ». Définissez cette valeur plus élevée possible pour des performances maximales. Sur les serveurs avec peu de mémoire physique, cela peut avoir un impact négatif en tant que les mémoires tampons d’envoi à consommer de mémoire système. Sur la plupart des systèmes, toutefois, la valeur maximale peut être appliquée sans réduire considérablement la mémoire disponible.  
  
-   **Tampons de réception max** -ce paramètre spécifie la quantité de mémoire tampon utilisée par le pilote d’interface réseau lors de la copie des données à la mémoire de protocole. Il est normalement défini par défaut sur une valeur relativement faible. Définissez cette valeur plus élevée possible pour des performances maximales. Sur les serveurs avec peu de mémoire physique, cela peut avoir une valeur négative impact que les tampons de réception consommer de mémoire système. Sur la plupart des systèmes, toutefois, la valeur maximale peut être appliquée sans réduire considérablement la mémoire disponible.  
  
-   **Toutes les options de déchargement sur** - dans presque tous les cas, les performances sont améliorées lors de l’activation des fonctionnalités de déchargement de l’interface réseau. Certaines cartes réseau fournissent des paramètres distincts pour activer ou désactiver le déchargement pour envoyer et recevoir le trafic. Déchargement des tâches à partir de l’UC à la carte réseau peut aider à faible utilisation du processeur sur le serveur afin d’améliore les performances globales du système. Le transport TCP/IP de Microsoft peut décharger une ou plusieurs des tâches suivantes pour une carte réseau qui a les fonctionnalités appropriées :  
  
    -   **Tâches de somme de contrôle** - transport TCP/IP le peut décharger le calcul et la validation de sommes de contrôle IP et TCP pour envoie et reçoit à la carte réseau ; Activez cette option si le pilote de carte réseau offre cette possibilité.  
  
    -   **Tâches de sécurité IP** -transport TCP/IP le peut décharger le calcul et la validation de sommes de contrôle chiffré pour les en-têtes d’authentification (AH) et en encapsulant des charges utiles de sécurité (ESP) à la carte réseau. Le transport TCP/IP peut également décharger le chiffrement et déchiffrement de charges utiles de ESP à la carte réseau. Activer ces options si le pilote de carte réseau fournit cette fonctionnalité.  
  
    -   **Segmentation des paquets TCP volumineux** -transport TCP/IP le prend en charge le déchargement d’envoi important (LSO). Avec LSO, le transport TCP/IP peut décharger la segmentation des paquets TCP volumineux.  
  
    -   **Déchargement de la pile** – la pile réseau peut être déchargée sur une carte réseau qui a les fonctionnalités appropriées. Activez cette option si le pilote de carte réseau fournit cette fonctionnalité.  
  
-   **Wake On LAN désactivé (sauf s’il est utilisé)** : configurer le pilote de carte réseau pour désactiver la fonctionnalité d’éveil par appel réseau. Cette fonctionnalité peut être utile pour les ordinateurs clients, mais doit rarement, voire jamais être utilisée sur un ordinateur BizTalk Server ou SQL Server.  
  
 Pour plus d’informations sur le réglage des cartes réseau pour les performances, consultez le **paramètres des périphériques réseau** section de la [livre blanc des « Optimisation de base de données BizTalk Server »](http://go.microsoft.com/fwlink/?LinkID=101578) (http://go.microsoft.com/fwlink/?LinkID=101578).  
  
## <a name="see-also"></a>Voir aussi  
 [Paramètres qui peuvent être modifiées pour améliorer les performances réseau](../technical-guides/settings-that-can-be-modified-to-improve-network-performance.md)