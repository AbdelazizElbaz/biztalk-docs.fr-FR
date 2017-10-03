---
title: "Optimisations du réseau | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9ff0392f-37ae-4ca6-8cc6-d53065de64c5
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bbf4b0e8df9d8baa81a91576dc37fd89413714f9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="network-optimizations"></a>Optimisations du réseau
Dans un environnement BizTalk Server où l’ou les ordinateurs BizTalk Server sont distinct de l’ordinateur SQL Server, chaque message traité par BizTalk Server requiert la communication sur le réseau. Cette communication comprend un trafic important entre les ordinateurs BizTalk Server et les bases de données MessageBox de BizTalk, les bases de données de gestion BizTalk, les bases de données BAM et autres bases de données. Dans les scénarios de charge élevée, cette communication peut entraîner un trafic réseau considérable et peut devenir un goulot d’étranglement, en particulier lorsque les paramètres réseau n’ont pas été optimisées, n’est pas suffisant cartes d’interface réseau sont installés ou de bande passante réseau insuffisantes disponible.  
  
 Cette rubrique explique comment améliorer les performances réseau entre les machines virtuelles de Hyper-V en cours d’exécution sur le même ordinateur hôte Hyper-V et fournit quelques recommandations générales pour améliorer les performances du réseau.  
  
> [!NOTE]  
>  Le symptôme le plus courant que les e/s réseau est un goulot d’étranglement est le compteur « Attentes de SQL Server : attente Statistics\Network e/s ». Lorsque la valeur de **le temps d’attente moyen** ce compteur est supérieure à zéro sur un ou plusieurs de vos ordinateurs SQL Server, puis les e/s réseau est un goulot d’étranglement.  
  
## <a name="improving-network-performance-of-biztalk-server-on-hyper-v"></a>Amélioration des performances du réseau de BizTalk Server sur Hyper-V  
  
### <a name="configure-hyper-v-virtual-machines-that-are-running-on-the-same-hyper-v-host-computer-to-use-a-private-virtual-network"></a>Configurer des ordinateurs virtuels Hyper-V qui s’exécutent sur le même ordinateur hôte Hyper-V pour utiliser un un réseau privé virtuel  
 Pour améliorer les performances réseau entre des ordinateurs virtuels Hyper-V qui s’exécutent sur le même ordinateur hôte Hyper-V, créez un privée réseau et router le trafic réseau virtuel entre des machines virtuelles via le réseau virtuel privé.  
  
##### <a name="create-a-private-virtual-network"></a>Créer un réseau virtuel privé  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**. Cliquez sur **outils d’administration**, puis cliquez sur **Gestionnaire Hyper-V**.  
  
2.  Dans le volet gauche du Gestionnaire Hyper-V, cliquez sur **Gestionnaire Hyper-V**, puis cliquez sur **se connecter au serveur**.  
  
3.  Dans le **sélectionner un ordinateur** boîte de dialogue, entrez le nom de l’ordinateur hôte Hyper-V, puis cliquez sur **OK**.  
  
4.  Dans le volet gauche du Gestionnaire Hyper-V, cliquez sur l’hôte Hyper-V, puis cliquez sur **Gestionnaire de réseau virtuel**.  
  
5.  Dans le Gestionnaire de réseau virtuel, sous **le type de réseau virtuel voulez-vous créer ?**, cliquez sur **privé**, puis cliquez sur **ajouter**.  
  
6.  Entrez un nom pour le nouveau réseau virtuel, puis cliquez sur **OK**. Le réseau virtuel est maintenant disponible pour chaque ordinateur virtuel Hyper-V qui est exécuté sur cet ordinateur hôte Hyper-V.  
  
##### <a name="add-the-private-virtual-network-to-hyper-v-virtual-machines-running-on-the-hyper-v-host"></a>Ajouter le réseau virtuel privé pour ordinateurs virtuels Hyper-V en cours d’exécution sur l’ordinateur hôte Hyper-V  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**. Cliquez sur **outils d’administration**, puis cliquez sur **Gestionnaire Hyper-V**.  
  
2.  Dans le volet gauche du Gestionnaire Hyper-V, cliquez sur **Gestionnaire Hyper-V**, puis cliquez sur **se connecter au serveur**.  
  
3.  Dans le **sélectionner un ordinateur** boîte de dialogue, entrez le nom de l’ordinateur hôte Hyper-V, puis cliquez sur **OK**.  
  
4.  Arrêtez toutes les machines virtuelles en cours d’exécution pour lequel vous souhaitez ajouter le réseau virtuel privé en cliquant sur l’ordinateur virtuel, puis en cliquant sur **arrêter**.  
  
5.  Après l’arrêt des machines virtuelles, cliquez sur un ordinateur virtuel, puis cliquez sur **paramètres** pour modifier les paramètres pour un ordinateur virtuel.  
  
6.  Dans le **paramètres pour < nom_ordinateur >** boîte de dialogue **ajouter un matériel**, sélectionnez **carte réseau**, puis cliquez sur **ajouter**.  
  
7.  Sur le **carte réseau** page de configuration, sous **réseau :**, sélectionnez le réseau virtuel privé que vous avez créé précédemment, puis cliquez sur **OK**. Vous avez maintenant effectué le réseau virtuel privé disponibles pour l’ordinateur virtuel Hyper-V qui sera accessible au prochain démarrage de l’ordinateur virtuel.  
  
8.  Répétez les étapes ci-dessus pour chaque ordinateur virtuel pour lequel vous souhaitez router le trafic réseau via le réseau virtuel privé.  
  
9. Démarrer les ordinateurs virtuels que vous avez ajouté le réseau virtuel privé. Cliquez avec le bouton droit sur chaque ordinateur virtuel et cliquez sur **Démarrer**.  
  
##### <a name="configure-each-virtual-machine-to-use-the-private-virtual-network"></a>Configurez chaque ordinateur virtuel pour utiliser le réseau virtuel privé  
  
1.  Une fois que chaque ordinateur virtuel a été démarré, le réseau virtuel privé est accessible à l’ordinateur virtuel en tant qu’une connexion réseau. Configurer la connexion réseau sur chaque ordinateur virtuel à utiliser TCP/IPv4 et spécifiez les paramètres pour le protocole TCP/IPv4.  
  
    1.  Accéder à la page de propriétés de connexion réseau, sélectionnez **4(TCP/IPv4) du protocole Internet Version**, puis cliquez sur **propriétés**.  
  
    2.  Cliquez sur le bouton radio en regard **utiliser l’adresse IP suivante**.  
  
2.  Entrez une valeur pour le **adresse IP** identifié dans « RFC 1918, l’Allocation d’adresses pour les adresses IP privées » des adresses à partir de la plage de l’adresse IP privée à [http://go.microsoft.com/fwlink/?LinkID=31904](http://go.microsoft.com/fwlink/?LinkID=31904).  
  
3.  Prenez note de l’adresse IP que vous avez spécifié ; Vous devez associer cette valeur avec le nom NetBIOS de cet ordinateur dans une entrée de fichier d’hôtes plus tard.  
  
4.  Entrez une valeur appropriée pour le **masque de sous-réseau** champ.  
  
    > [!NOTE]  
    >  Windows doit remplir les **masque de sous-réseau** champ avec une valeur appropriée en fonction de la valeur que vous avez entré dans le **adresse IP** champ.  
  
5.  Laissez le **passerelle par défaut** champ, vide, cliquez sur **OK**, puis cliquez sur **fermer**.  
  
6.  Après avoir configuré chaque ordinateur virtuel avec une adresse IP privée unique, vous devez mettre à jour le fichier HOSTS sur chaque ordinateur virtuel avec l’adresse IP et le nom NetBIOS des autres ordinateurs virtuels en cours d’exécution sur l’ordinateur hôte Hyper-V. Le fichier HOSTS mis à jour doit être enregistré dans le dossier %systemroot%\drivers\etc\ sur chaque ordinateur virtuel.  
  
    > [!NOTE]  
    >  Étant donné que par défaut, Windows vérifie le fichier HOSTS local pour résoudre les noms NetBIOS, en mettant à jour le fichier HOSTS sur chaque ordinateur virtuel avec les adresses IP privées uniques des autres ordinateurs virtuels, le trafic réseau entre ces ordinateurs est routé via le réseau virtuel privé.  
  
### <a name="disable-tcp-offloading-for-the-virtual-machine-network-cards"></a>Désactiver le déchargement TCP pour les cartes réseau de Machine virtuelle  
 Modifier le Registre comme décrit dans la rubrique « Utilisation des valeurs du Registre pour activer et désactiver la tâche délestage (NDIS 5.1) » à la [http://go.microsoft.com/fwlink/?LinkId=147619](http://go.microsoft.com/fwlink/?LinkId=147619) pour désactiver le déchargement TCP pour les cartes réseau sur chaque ordinateur virtuel.  
  
> [!IMPORTANT]  
>  Une utilisation incorrecte de l'Éditeur du Registre peut causer des problèmes vous obligeant à réinstaller votre système d'exploitation. Son utilisation est sous votre entière responsabilité. Pour plus d’informations sur la façon de sauvegarder, restaurer et modifier le Registre, consultez l’article de la Base de connaissances Microsoft « Description du Registre de Microsoft Windows » à [http://go.microsoft.com/fwlink/?LinkId=62729](http://go.microsoft.com/fwlink/?LinkId=62729).  
  
## <a name="general-guidelines-for-improving-network-performance"></a>Recommandations générales pour améliorer les performances du réseau  
 Les recommandations suivantes peuvent être utilisées pour augmenter les performances du réseau :  
  
### <a name="add-additional-network-cards-to-computers-in-the-biztalk-server-environment"></a>Ajouter des cartes réseau supplémentaires sur les ordinateurs dans l’environnement BizTalk Server  
 Que comme l’ajout de disques durs supplémentaires peuvent améliorer les performances du disque, les cartes réseau supplémentaires Ajout peuvent améliorer les performances réseau. Si les cartes réseau sur les ordinateurs de votre environnement BizTalk Server sont saturés et que la carte est un goulot d’étranglement, envisagez d’ajouter une ou plusieurs cartes réseau supplémentaires pour améliorer les performances.  
  
### <a name="implement-network-segmentation"></a>Implémentez la segmentation du réseau  
 Suivez les recommandations de la **sous-réseaux** section du livre blanc « Optimisation de base de données BizTalk Server » à [http://go.microsoft.com/fwlink/?LinkID=101578](http://go.microsoft.com/fwlink/?LinkID=101578).  
  
### <a name="where-possible-replace-hubs-with-switches"></a>Si possible, remplacez les concentrateurs avec les commutateurs  
 Commutateurs contiennent une logique pour acheminer directement le trafic entre la source et de destination, tandis que les concentrateurs utilisent un modèle d’acheminer le trafic de diffusion. Par conséquent, les commutateurs sont plus efficaces et offrent de meilleures performances.  
  
### <a name="remove-unnecessary-network-protocols"></a>Supprimer les protocoles réseau inutiles  
 Ordinateurs Windows Server ont parfois plusieurs services et protocoles réseau installés que réellement nécessaire. Chaque client réseau supplémentaire, le service ou le protocole place supplémentaire surcharge des ressources système.  
  
 En outre, chaque protocole installé génère un trafic réseau. En supprimant les protocoles, les services et les clients du réseau inutile, les ressources système sont disponibles pour d’autres processus, accroît le trafic réseau est évité et le nombre de liaisons de réseau qui doit être négociée est réduit au minimum.  
  
 Pour afficher les clients du réseau actuellement installé, protocoles et les services, procédez comme suit :  
  
1.  Cliquez sur **Démarrer**, pointez sur **paramètres**, puis cliquez sur **le panneau de configuration**.  
  
2.  Double-cliquez sur **connexions réseau** pour afficher les connexions réseau sur l’ordinateur.  
  
3.  Avec le bouton droit **connexion au réseau Local** (ou l’entrée pour votre connexion réseau), puis cliquez sur **propriétés** pour afficher la boîte de dialogue Propriétés de la connexion réseau.  
  
4.  Pour supprimer un élément inutile, sélectionnez-la, puis cliquez sur **désinstallation**. Pour désactiver un élément, désactivez simplement la case à cocher associée à l’élément.  
  
 Si vous ne savez pas sur les effets de la désinstallation d’un élément pour la connexion, puis désactivez l’élément plutôt que de le désinstaller. Désactiver les éléments vous permet de déterminer quels services, les protocoles et les clients sont réellement nécessaire sur un système. Lorsqu’il a été déterminé que la désactivation d’un élément n’a aucune incidence sur le serveur, l’élément peut ensuite être désinstallé.  
  
 Dans de nombreux cas, uniquement les trois composants suivants sont requis pour l’opération sur un réseau TCP/IP de base standard :  
  
-   Client pour les réseaux Microsoft  
  
-   Partage de fichiers et imprimantes pour les réseaux Microsoft  
  
-   Protocole Internet (TCP/IP)  
  
### <a name="network-adapter-drivers-on-all-computers-in-the-biztalk-server-environment-should-be-tuned-for-performance"></a>Les pilotes de cartes réseau sur tous les ordinateurs dans l’environnement BizTalk Server doivent être réglées pour des performances  
  
> [!IMPORTANT]  
>  Avant d’appliquer sur les pilotes de carte réseau du paramétrage, vous devez toujours installer les pilotes de périphérique de carte réseau plus récentes pour les cartes réseau dans l’environnement.  
  
 Ajustez les pilotes de périphérique de carte réseau pour optimiser la quantité de mémoire disponible pour la mise en mémoire tampon de paquet, entrante et sortante. Aussi optimiser le nombre de mémoires tampons, en particulier tampons de transmission et fusionner les tampons. La valeur par défaut les valeurs pour ces paramètres et si elles sont encore fournies, varier entre les versions de pilotes et les fabricants. L’objectif est d’optimiser le travail effectué par la carte réseau et pour permettre l’espace de mémoire tampon possible plus grande pour les opérations de réseau atténuer les pics de trafic réseau et de congestion associée.  
  
> [!NOTE]  
>  Étapes pour paramétrer les pilotes de cartes réseau varient selon le fabricant.  
  
 Suivez ces étapes pour accéder aux paramètres des cartes réseau dans[!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]:  
  
1.  Cliquez sur **Démarrer**, puis cliquez sur **le panneau de configuration**.  
  
2.  Cliquez sur **réseau et Internet**, puis cliquez sur **Centre réseau et partage**.  
  
3.  Cliquez sur **modifier les paramètres de la carte**, avec le bouton droit **connexion au réseau Local** (ou le nom de votre connexion réseau), puis cliquez sur **propriétés**.  
  
4.  Sur le **général** , cliquez sur **configurer**.  
  
5.  Cliquez sur le **avancé** onglet pour accéder aux propriétés qui peuvent être configurés pour la carte réseau.  
  
 Les propriétés suivantes doivent être configurées pour chaque carte réseau dans l’environnement BizTalk Server :  
  
> [!NOTE]  
>  Vous appliquez ces paramètres pour chaque carte réseau physique, y compris les cartes réseau individuelles au sein d’un ensemble de cartes réseau qui sont configurées pour l’agrégation, l’équilibrage de charge ou la tolérance de panne. Avec certains logiciels de l’association de cartes, vous devrez peut-être également appliquer ces paramètres à l’équipe. Notez que certaines cartes réseau sont réglage automatique et ne proposent pas l’option pour configurer les paramètres manuellement.  
  
-   **Option d’alimentation** – configurer le pilote de carte réseau pour éviter les fonctionnalités de gestion d’alimentation à partir de la désactivation de la carte réseau à économiser de l’énergie. Cette fonctionnalité peut être utile pour les ordinateurs clients, mais doit rarement, voire jamais, utilisée sur un ordinateur BizTalk Server ou SQL Server.  
  
-   **Fixe vitesse/Duplex (n’utilisez pas AUTO)** -il est très important que la vitesse du réseau, duplex et les paramètres de contrôle de flux sont définies pour correspondre aux paramètres du commutateur à laquelle ils sont connectés. Cela limite l’occurrence de « auto-synchronisation périodique « cette opération peut être temporairement hors connexion des connexions.  
  
-   **Tampons de fusion max** -registres de mappage sont utilisés pour convertir les adresses physiques des adresses virtuelles pour les cartes réseau qui prennent en charge le contrôle du bus de ressources système. Fusionner les mémoires tampons sont disponibles pour le pilote de réseau si le pilote suffisamment de registres de mappage. Définissez cette valeur plus élevée possible pour des performances maximales. Sur les serveurs avec peu de mémoire physique, cela peut avoir une valeur négative impact que les tampons de fusion consomme de mémoire système. Sur la plupart des systèmes, toutefois, la valeur maximale peut être appliquée sans réduire considérablement la mémoire disponible.  
  
-   **Tampons d’envoi et les descripteurs de transmission/envoi max** -ce paramètre spécifie combien de transmettre des tampons de contrôle du pilote alloue pour une utilisation par l’interface réseau. Cela reflète directement le nombre de paquets en attente, que le pilote peut avoir dans sa file d’attente « envoyer ». Définissez cette valeur plus élevée possible pour des performances maximales. Sur les serveurs avec peu de mémoire physique, cela peut avoir un impact négatif en tant que les mémoires tampons d’envoi à consommer de mémoire système. Sur la plupart des systèmes, toutefois, la valeur maximale peut être appliquée sans réduire considérablement la mémoire disponible.  
  
-   **Tampons de réception max** -ce paramètre spécifie la quantité de mémoire tampon utilisée par le pilote d’interface réseau lors de la copie des données à la mémoire de protocole. Il est normalement défini par défaut sur une valeur relativement faible. Définissez cette valeur plus élevée possible pour des performances maximales. Sur les serveurs avec peu de mémoire physique, cela peut avoir une valeur négative impact que les tampons de réception consommer de mémoire système. Sur la plupart des systèmes, toutefois, la valeur maximale peut être appliquée sans réduire considérablement la mémoire disponible.  
  
-   **Toutes les options de déchargement sur** - dans presque tous les cas, les performances sont améliorées lors de l’activation des fonctionnalités de déchargement de l’interface réseau. Certaines cartes réseau fournissent des paramètres distincts pour activer ou désactiver le déchargement pour envoyer et recevoir le trafic. Déchargement des tâches à partir de l’UC à la carte réseau peut aider à faible utilisation du processeur sur le serveur afin d’améliore les performances globales du système. Le transport TCP/IP de Microsoft peut décharger une ou plusieurs des tâches suivantes pour une carte réseau qui a les fonctionnalités appropriées :  
  
    -   **Tâches de somme de contrôle** - transport TCP/IP le peut décharger le calcul et la validation de sommes de contrôle IP et TCP pour envoie et reçoit à la carte réseau, activez cette option si le pilote de carte réseau offre cette possibilité.  
  
    -   **Tâches de sécurité IP** -transport TCP/IP le peut décharger le calcul et la validation de sommes de contrôle chiffré pour les en-têtes d’authentification (AH) et en encapsulant des charges utiles de sécurité (ESP) à la carte réseau. Le transport TCP/IP peut également décharger le chiffrement et déchiffrement de charges utiles de ESP à la carte réseau. Activer ces options si le pilote de carte réseau fournit cette fonctionnalité.  
  
    -   **Segmentation des paquets TCP volumineux** -transport TCP/IP le prend en charge le déchargement d’envoi important (LSO). Avec LSO, le transport TCP/IP peut décharger la segmentation des paquets TCP volumineux.  
  
    -   **Déchargement de la pile** – la pile réseau peut être déchargée sur une carte réseau qui a les fonctionnalités appropriées. Activez cette option si le pilote de carte réseau fournit cette fonctionnalité.  
  
-   **Wake On LAN désactivé (sauf s’il est utilisé)** : configurer le pilote de carte réseau pour désactiver la fonctionnalité d’éveil par appel réseau. Cette fonctionnalité peut être utile pour les ordinateurs clients, mais doit rarement, voire jamais être utilisée sur un ordinateur BizTalk Server ou SQL Server.  
  
 Pour plus d’informations sur le réglage des cartes réseau pour les performances, consultez le **paramètres des périphériques réseau** section du livre blanc « Optimisation de base de données BizTalk Server » à [http://go.microsoft.com/fwlink/?LinkID=101578](http://go.microsoft.com/fwlink/?LinkID=101578).