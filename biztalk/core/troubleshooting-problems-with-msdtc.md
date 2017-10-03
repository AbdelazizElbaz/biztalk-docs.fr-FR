---
title: "Dépannage des problèmes liés à MSDTC | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f39cde52-da8f-4cc1-bdc5-e4b828891a79
caps.latest.revision: "36"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c244ec27cd3e584f7fb22a34effeaf0033c3e78a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshooting-problems-with-msdtc"></a>Résolution des problèmes liés à MSDTC
La plupart des opérations du moteur d'exécution BizTalk Server requièrent une prise en charge du service MSDTC (Microsoft Distributed Transaction Coordinator) afin de garantir la cohérence transactionnelle des opérations. Si la prise en charge des transactions MSDTC n'est pas disponible, alors les opérations d'exécution de BizTalk Server associées ne peuvent pas se poursuivre. Les composants de BizTalk généralement affectés par la configuration incorrecte de la prise en charge des transactions MSDTC sont, entre autres, le service de l'authentification unique, les instances d'hôte BizTalk et toutes les instances SQL Server connectées par BizTalk Server. Cette rubrique contient des informations décrivant les problèmes liés au service MSDTC, ainsi que les procédures à suivre pour diagnostiquer et résoudre ces problèmes.  
  
## <a name="errors-that-can-occur-if-msdtc-transaction-support-is-not-configured-correctly"></a>Erreurs susceptibles de survenir si la prise en charge des transactions MSDTC n'est pas correctement configurée  
 Des erreurs telles que celles présentées ci-dessous sont susceptibles de se produire sur BizTalk Server lorsque la prise en charge des transactions MSDTC n'est pas correctement configurée sur les ordinateurs d'un environnement BizTalk :  
  
-   « Un problème MSDTC (Microsoft Distributed Transaction Coordinator) a empêché la connexion à la base de données de configuration. Le gestionnaire de transactions a désactivé sa prise en charge de transactions à distance/réseau. »  
  
-   « Un problème MSDTC (Microsoft Distributed Transaction Coordinator) a empêché la connexion à la base de données de configuration. La transaction a déjà été validée ou annulée de manière implicite ou explicite. »  
  
-   « Code d'erreur : 0x8004d00a, La nouvelle transaction ne peut pas s'inscrire dans le coordinateur de transactions spécifié. »  
  
-   « Impossible d'extraire de la banque de configuration les données du type de transport de l'emplacement de réception 'MySample ReceiveLocation'. Échec du serveur SSO principal 'MyServer'. Le serveur RPC n'est pas disponible. »  
  
-   « Code d'erreur : 0x8004d025, Le partenaire du gestionnaire de transactions a désactivé la prise en charge des transactions à distance/par réseau. »  
  
-   « Code d'erreur : 0xc0002a24. Impossible d'importer une transaction DTC. Vérifiez que MSDTC est correctement configuré pour l'opération distante. »  
  
-   « 0x8004d01c  
  
     [0x1705] Échec lors de la création de l'élément de travail interne.  
  
     Assurez-vous que le serveur SQL Server est en cours d'exécution. »  
  
 Pour résoudre les problèmes de configuration du service MSDTC, suivez les instructions ci-dessous.  
  
## <a name="ensure-netbios-name-resolution-between-the-biztalk-server-and-remote-servers-is-successful"></a>Vérifiez que la résolution de noms NetBIOS entre le serveur BizTalk et les serveurs distants s'effectue correctement.  
 Pour une transaction MSDTC réussie entre différents ordinateurs, l'ordinateur client doit être en mesure de convertir le nom NetBIOS de l'ordinateur du serveur en une adresse IP correcte et l'ordinateur du serveur doit également être en mesure de convertir le nom NetBIOS de l'ordinateur client en une adresse IP correcte. Pour vous assurer que la résolution de noms NetBIOS fonctionne dans les deux sens (client vers serveur et serveur vers client), procédez comme indiqué ci-dessous :  
  
> [!NOTE]
>  Le nom NetBIOS est généralement appelé nom du **réseau** .  
  
1.  Déterminez le nom NetBIOS de chaque ordinateur :  
  
    1.  Cliquez avec le bouton droit sur **Poste de travail** pour afficher la boîte de dialogue **Propriétés système** , puis cliquez sur l'onglet **Nom de l'ordinateur** pour afficher le **Nom complet de l'ordinateur** affecté à l'ordinateur en question.  
  
    2.  Le nom NetBIOS est la première partie du nom désigné en tant que **Nom complet de l'ordinateur** . Par exemple, si le **Nom complet de l'ordinateur** est monserveur.société.domaine.fr, alors le nom NetBIOS de l'ordinateur est **monserveur**.  
  
2.  Déterminez la ou les adresses IP associées à chaque ordinateur.  
  
    1.  Lancez une invite de commandes sur l'ordinateur client, entrez la commande suivante, puis appuyez sur la touche ENTRÉE :  
  
        ```  
        ipconfig /all  
        ```  
  
    2.  La ou les adresses IP associées à l'ordinateur client sont répertoriées dans la fenêtre d'invite de commandes.  
  
    3.  Lancez une invite de commandes sur l'ordinateur du serveur, entrez la commande suivante, puis appuyez sur la touche ENTRÉE :  
  
        ```  
        ipconfig /all  
        ```  
  
    4.  La ou les adresses IP associées à l'ordinateur du serveur sont répertoriées dans la fenêtre d'invite de commandes.  
  
3.  Assurez-vous que le nom NetBIOS de chaque ordinateur correspond à l'une des adresses IP associées à l'ordinateur :  
  
    1.  Lancez une invite de commandes sur l'ordinateur client, entrez la commande suivante, puis appuyez sur la touche ENTRÉE :  
  
        ```  
        ping <NetBIOS name of server computer>  
        ```  
  
         Les résultats de la commande ping doivent renvoyer une adresse IP associée à l'ordinateur du serveur.  
  
    2.  Lancez une invite de commandes sur l'ordinateur du serveur, entrez la commande suivante, puis appuyez sur la touche ENTRÉE :  
  
        ```  
        ping <NetBIOS name of client computer>  
        ```  
  
         Les résultats de la commande ping doivent renvoyer une adresse IP associée à l'ordinateur client.  
  
4.  Assurez-vous que la recherche de nom inversée de l'adresse IP associée au nom NetBIOS de chaque ordinateur correspond au nom correct de l'ordinateur.  
  
    1.  Lancez une invite de commandes sur l'ordinateur client, entrez la commande suivante, puis appuyez sur la touche ENTRÉE :  
  
        ```  
        ping -a <IP Address associated with client computer NetBIOS name>  
        ```  
  
         Le résultat de la commande ping doit retourner un nom NetBIOS ou un nom de domaine complet correspondant au nom NetBIOS utilisé à l'étape 3a. Si le nom retourné ne correspond pas au nom NetBIOS utilisé à l'étape 3a, la recherche inversée de l'adresse IP échoue, ce qui peut entraîner l'échec des transactions MSDTC.  
  
    2.  Lancez une invite de commandes sur l'ordinateur du serveur, entrez la commande suivante, puis appuyez sur la touche ENTRÉE :  
  
        ```  
        ping -a <IP Address associated with server computer NetBIOS name>  
        ```  
  
         Le résultat de la commande ping doit retourner un nom NetBIOS ou un nom de domaine complet correspondant au nom NetBIOS utilisé à l'étape 3b. Si le nom retourné ne correspond pas au nom NetBIOS utilisé à l'étape 3b, la recherche inversée de l'adresse IP échoue, ce qui peut entraîner l'échec des transactions MSDTC.  
  
 Si la résolution de noms NetBIOS échoue dans un sens ou dans l'autre, ou si la recherche de nom inversée n'aboutit pas, créez les entrées appropriées dans le serveur DNS, le serveur de nom NetBIOS, le fichier HOSTS ou le fichier LMHOSTS pour résoudre le problème.  
  
> [!NOTE]
>  La méthode de résolution de noms utilisée par l'ordinateur varie en fonction du type de nœud NetBIOS de l'ordinateur. Pour plus d’informations sur les types de nœuds NetBIOS, consultez la rubrique [Résolution de noms NetBIOS](http://go.microsoft.com/fwlink/?LinkId=201638).  
  
## <a name="ensure-that-a-firewall-between-the-biztalk-server-and-remote-servers-is-not-blocking-ports-required-for-rpc-dynamic-port-allocation"></a>Assurez-vous qu'aucun pare-feu entre BizTalk Server et les serveurs distants ne bloque les ports nécessaires à l'allocation de port dynamique RPC.  
 La fonctionnalité MSDTC sur le réseau dépend de la fonctionnalité RPC sur le réseau. L'utilisation de la fonctionnalité RPC à travers un pare-feu nécessite l'ouverture de ports spécifiques pour prendre en compte une allocation de port dynamique RPC. Si un pare-feu a été placé entre le serveur BizTalk et les serveurs distants, effectuez la procédure détaillée dans la rubrique [Configuration de l'allocation de port dynamique RPC avec un pare-feu](http://go.microsoft.com/fwlink/?LinkId=66831) pour pouvoir prendre en compte une allocation de port dynamique RPC.  
  
## <a name="set-the-appropriate-msdtc-security-configuration-options"></a>Définition des options de configuration de la sécurité MSDTC appropriées  
 Windows fournit des améliorations de sécurité qui régissent l'accès à MSDTC sur un réseau. En modifiant les paramètres de sécurité MSDTC, vous contrôlez la façon dont MSDTC communique avec les ordinateurs distants sur le réseau. Ce tableau répertorie les valeurs d'options recommandées disponibles lors de la configuration des paramètres de sécurité MSDTC :  
  
|Option de configuration|Valeur par défaut|Valeur recommandée|  
|--------------------------|-------------------|-----------------------|  
|Accès DTC réseau|Désactivé|Activé|  
|**Client et Administration**|||  
|Autoriser les clients distants|Désactivé|Désactivé|  
|Autoriser l'administration distante|Désactivé|Désactivé|  
|**Communication du Gestionnaire de transactions**|||  
|Autoriser les transactions entrantes|Désactivé|Activé|  
|Autoriser les transactions sortantes|Désactivé|Activé|  
|Authentification mutuelle requise|Activé|Activé si tous les ordinateurs distants exécutent Windows Server 2003 SP1 ou Windows XP SP2 ou une version ultérieure, et sont configurés avec l'option « Authentification mutuelle requise ».|  
|Autorisation de l'appelant entrant requise|Désactivé|Activé si MSDTC s'exécute sur un cluster.|  
|Aucune authentification requise|Désactivé|Activé si tous les ordinateurs distants exécutent des versions antérieures à Windows Server 2003 ou à Windows XP SP2.|  
|Activer la fonctionnalité TIP.|Désactivé|Activé si le portail BAM s'exécute.|  
|Activer les transactions XA.|Désactivé|Activé en cas de communication avec un système transactionnel XA ou avec IBM WebSphere MQ à l'aide de l'adaptateur MQSeries.|  
  
 Une fois ces changements appliqués, le service MSDTC est redémarré.  
  
 Pour accéder aux options de configuration de la sécurité MSDTC, procédez comme suit :  
  
1.  Cliquez sur **Démarrer**, sur **Exécuter**, puis tapez **dcomcnfg** pour lancer la console de gestion **Services de composants**.  
  
2.  Développez **Services de composants** , puis **Ordinateurs**.  
  
3.  Développez **Poste de travail**, **Distributed Transaction Coordinator**, cliquez avec le bouton droit sur **DTC local**, puis cliquez sur **Propriétés**.  
  
4.  Dans la boîte de dialogue **Propriétés DTC locales** , cliquez sur l'onglet **Sécurité** .  
  
> [!NOTE]
>  En fonction des changements effectués, il se peut que vous ayez à redémarrer l'ordinateur. Si vous rencontrez toujours des problèmes après avoir appliqué les changements et relancé le service MSDTC, redémarrez l'ordinateur sur lequel les changements ont été apportés pour que ceux-ci entrent en vigueur.  
  
 Si l'option de configuration **Authentification mutuelle requise** ou **Autorisation de l'appelant entrant requise** est activée, le compte de l'ordinateur client doit se voir accorder le droit utilisateur **Accéder à cet ordinateur à partir du réseau** . Si le compte d'un ordinateur client ne dispose pas du droit utilisateur **Accéder à cet ordinateur à partir du réseau** ou est inclus dans le droit **Interdire l'accès à cet ordinateur à partir du réseau** , la communication DTC entre le client et le serveur échoue.  
  
 Par défaut, le droit utilisateur **Accéder à cet ordinateur à partir du réseau** est accordé au groupe Tout le monde. Par conséquent, il n'a pas besoin d'être changé, sauf si le paramètre par défaut a été modifié. Si l'option de configuration **Aucune authentification requise** est activée, le droit utilisateur **Accéder à cet ordinateur à partir du réseau** ne s'applique pas au compte de l'ordinateur client.  
  
 Pour changer les utilisateurs ou groupes disposant du droit Accéder à cet ordinateur à partir du réseau, procédez comme suit :  
  
1.  Cliquez sur **Démarrer**, puis **Exécuter**, tapez **Gpedit.msc**et cliquez sur **OK**.  
  
2.  Développez les éléments suivants dans la liste Stratégie de l'ordinateur local :  
  
    -   Configuration ordinateur  
  
    -   Paramètres Windows  
  
    -   Paramètres de sécurité  
  
    -   Stratégies locales  
  
3.  Cliquez sur **Attribution des droits utilisateur**.  
  
4.  Double-cliquez sur **Accéder à cet ordinateur à partir du réseau**, puis cliquez sur **Ajouter un utilisateur ou un groupe**.  
  
5.  Cliquez sur **Types d'objet**, sélectionnez **Ordinateurs** , puis cliquez sur **OK**.  
  
6.  Ajoutez le nom de l'ordinateur ou du groupe dans la zone **Entrez les noms des objets à sélectionner** .  
  
7.  Cliquez sur **Vérifier les noms** pour vérifier l'entrée.  
  
8.  Cliquez deux fois sur **OK** .  
  
 Pour changer les utilisateurs ou les groupes inclus dans le droit **Interdire l'accès à cet ordinateur à partir du réseau** , procédez comme suit :  
  
1.  Développez les éléments suivants dans la liste Stratégie de l'ordinateur local :  
  
    -   Configuration ordinateur  
  
    -   Paramètres Windows  
  
    -   Paramètres de sécurité  
  
    -   Stratégies locales  
  
2.  Cliquez sur **Attribution des droits utilisateur**.  
  
3.  Double-cliquez sur **Interdire l'accès à cet ordinateur à partir du réseau**, puis cliquez sur le nom de l'ordinateur ou du groupe à supprimer de ce droit.  
  
4.  Cliquez sur **Supprimer** , puis sur **OK**.  
  
## <a name="set-the-appropriate-values-for-the-enableauthepresolution-and-restrictremoteclients-options"></a>Définition des valeurs appropriées pour les options EnableAuthEpResolution et RestrictRemoteClients  
 Windows améliore la sécurité en exigeant que les appels passés à l'interface RPC soient authentifiés. Vous pouvez configurer cette fonctionnalité par l'intermédiaire des clés de Registre **EnableAuthEpResolution** et **RestrictRemoteClients** . Pour vous assurer que les ordinateurs distants sont en mesure d'accéder à l'interface RPC, procédez comme suit :  
  
> [!WARNING]
>  Une utilisation incorrecte de l'Éditeur du Registre peut causer des problèmes vous obligeant à réinstaller votre système d'exploitation. Son utilisation est sous votre entière responsabilité. Pour plus d'informations sur la procédure de sauvegarde, de restauration et de modification du Registre, voir l'article de la Base de connaissances Microsoft « Description du Registre de Microsoft Windows » disponible à l'adresse [Description du Registre de Microsoft Windows](http://go.microsoft.com/fwlink/?LinkId=62729).  
  
1.  Cliquez sur **Démarrer**, **Exécuter**, tapez **regedit.exe**, puis cliquez sur **OK** pour démarrer l'Éditeur du Registre.  
  
     Accédez à **HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows NT**.  
  
2.  Sous la clé **RPC** , créez les entrées DWORD suivantes avec les valeurs indiquées. Si la clé **RPC** n'existe pas, créez-la.  
  
    |Entrée DWORD|Valeur par défaut|Valeur recommandée|  
    |-----------------|-------------------|-----------------------|  
    |EnableAuthEpResolution|0 (désactivé)|1|  
    |RestrictRemoteClients|1 (activé)|0|  
  
3.  Fermez l'Éditeur de Registre.  
  
4.  Redémarrez le service MSDTC.  
  
> [!NOTE]
>  En fonction des changements effectués, il se peut que vous ayez à redémarrer l'ordinateur. Si vous rencontrez toujours des problèmes après avoir appliqué les changements et relancé le service MSDTC, redémarrez l'ordinateur sur lequel les changements ont été apportés pour que ceux-ci entrent en vigueur.  
  
## <a name="if-windows-firewall-is-running-add-an-exception-for-the-msdtc-service"></a>Si le Pare-feu Windows fonctionne, ajoutez une exception pour le service MSDTC.  
 Le service Pare-feu Windows peut bloquer les communications MSDTC entre ordinateurs. Pour que ces communications ne soient pas bloquées, ajoutez msdtc.exe à la liste des exceptions du Pare-feu Windows, si ce service est exécuté.  
  
1.  Cliquez sur **Démarrer**, puis **Exécuter**, tapez **firewall.cpl**, puis cliquez sur **OK** pour afficher la boîte de dialogue **Pare-feu Windows** .  
  
2.  Cliquez sur **Autoriser un programme via le Pare-feu Windows** pour afficher la boîte de dialogue **Paramètres du Pare-feu Windows** .  
  
3.  Cliquez sur l'onglet **Exceptions** de la boîte de dialogue **Paramètres du Pare-feu Windows** .  
  
4.  Cliquez sur **Ajouter un programme** pour afficher la boîte de dialogue **Ajouter un programme** .  
  
5.  Cliquez sur **Parcourir** et recherchez le fichier *%system32%*\msdtc.exe.  
  
    > [!NOTE]
    >  Lancez une invite de commandes, tapez **echo %system32%** et appuyez sur la touche **Entrée** pour déterminer l'emplacement du répertoire \System32 sur l'ordinateur.  
  
6.  Cliquez sur **msdtc.exe** , puis sur **Ouvrir**.  
  
7.  Cliquez sur **Modifier l'étendue** pour spécifier le jeu d'ordinateurs pour lequel les communications MSDTC doivent être autorisées, puis cliquez sur **OK**.  
  
8.  Cliquez sur **OK** dans la boîte de dialogue **Ajouter un programme** , puis sur **OK** dans la boîte de dialogue **Paramètres du Pare-feu Windows** .  
  
9. Fermez la boîte de dialogue **Pare-feu Windows** .  
  
10. Arrêtez et redémarrez le service Distributed Transaction Coordinator.  
  
    -   Lancez une invite de commandes, tapez **net stop msdtc** et appuyez sur la touche **Entrée**.  
  
    -   Une fois le service Distributed Transaction Coordinator arrêté, tapez **net start msdtc** , puis appuyez sur **Entrée**.  
  
## <a name="use-dtctester-or-dtcping-to-verify-msdtc-functionality-over-the-network"></a>Les utilitaires DTCTester et DTCPing permettent de vérifier que la fonctionnalité MSDTC s'exécute correctement sur le réseau.  
 L'utilitaire DTCTester permet de vérifier la prise en charge des transactions entre deux ordinateurs si SQL Server est installé sur l'un des deux au moins. L'utilitaire DTCTester fait appel à ODBC pour vérifier la prise en charge des transactions par rapport à une base de données SQL Server. Pour plus d'informations sur l'utilitaire DTCTester, voir [Utilisation de l'outil DTCTester](http://go.microsoft.com/fwlink/?LinkId=66232).  
  
 L'utilitaire DTCPing permet de vérifier la prise en charge des transactions entre deux ordinateurs si SQL Server n'est installé sur aucun des deux. L'utilitaire DTCPing doit être exécuté à la fois sur l'ordinateur client et sur l'ordinateur du serveur et constitue une alternative à l'utilitaire DTCTester lorsque SQL Server n'est installé sur aucun des deux ordinateurs. Pour plus d'informations sur l'utilitaire DTCPing, consultez la page [Résolution des problèmes liés à l'utilisation d'un pare-feu MS DTC (page éventuellement en anglais)](http://go.microsoft.com/fwlink/?LinkId=61915).  
  
> [!IMPORTANT]
>  Si l'utilitaire DTCPing renvoie l'avertissement « AVERTISSEMENT : les valeurs CID des deux ordinateurs de test sont identiques », veuillez suivre la procédure décrite dans la section **S'assurer qu'une valeur CID unique a été attribuée à MSDTC** pour garantir l'interopérabilité de la fonctionnalité MSDTC entre les ordinateurs de test.  
  
## <a name="ensure-that-msdtc-is-assigned-a-unique-cid-value"></a>S'assurer qu'une valeur CID unique a été attribuée à MSDTC  
 Pour garantir le bon fonctionnement entre ordinateurs de la fonctionnalité MSDTC du système d'exploitation Windows, des valeurs CID uniques doivent avoir été attribuées. Les images dupliquées du disque des installations Windows doivent avoir reçu des valeurs CID uniques, sinon la fonctionnalité MSDTC risque d'être altérée. Cela peut se produire lors de l'utilisation de disques durs virtuels pour le déploiement d'un système d'exploitation sur un ordinateur virtuel.  
  
 Pour déterminer si les valeurs CID de MSDTC attribuées aux ordinateurs exécutant le système d'exploitation Windows sont uniques, vérifiez les valeurs des entrées sous la clé de Registre HKEY_CLASSES_ROOT\CID pour les deux ordinateurs. Si ces valeurs ne sont pas uniques pour chaque ordinateur, suivez la procédure décrite dans la section **Réinstallation du service DTC si les autres instructions de dépannage échouent** pour réinstaller MSDTC sur l'un des ordinateurs, ce qui aura pour effet de générer des valeurs CID MSDTC uniques pour cet ordinateur et de garantir le bon fonctionnement des opérations MSDTC.  
  
## <a name="error-new-transaction-cannot-enlist-in-the-specified-transaction-coordinator-0x8004d00a-occurs-if-the-msdtc-connection-between-a-client-computer-and-a-server-computer-is-closed"></a>L'erreur « La nouvelle transaction ne peut pas s'inscrire dans le coordinateur de transactions spécifié (0x8004d00a) » survient si la connexion MSDTC entre un ordinateur client et un ordinateur serveur est fermée.  
 Dans certains scénarios, il est possible qu’une connexion MSDTC existante entre un client et un serveur soit fermée, et que les tentatives suivantes d’utilisation de cette connexion provoquent l’affichage du message d’erreur suivant :  
La nouvelle transaction ne peut pas s’inscrire dans le coordinateur de transactions spécifié (0x8004d00a)  
Pour plus d’informations, consultez [Message d’erreur lorsque vous essayez de démarrer une transaction dans MS DTC : « La nouvelle transaction ne peut pas s’inscrire dans le coordinateur de transactions spécifié. »](http://support.microsoft.com/kb/922430).  
  
## <a name="consider-reinstalling-the-distributed-transaction-coordinator-service-if-other-troubleshooting-steps-are-not-successful"></a>Réinstallation du service DTC si les autres instructions de dépannage échouent  
 Si d'autres tentatives de dépannage de MSDTC échouent, désinstallez et réinstallez MSDTC. Pour ce faire, procédez comme suit :  
  
1.  Ouvrez une invite de commandes en tant qu'administrateur.  
  
2.  À l’invite de commandes, tapez la commande suivante pour désinstaller le service Distributed Transaction Coordinator :  
    `msdtc -uninstall`  
  
3.  À l’invite de commandes, tapez la commande suivante pour installer le service Distributed Transaction Coordinator :  
    `msdtc –install`  
  
> [!IMPORTANT]
>  La réinstallation de MSDTC peut modifier le comportement par défaut du service Distributed Transaction Coordinator. Suivez ces étapes après la réinstallation de MSDTC pour vous assurer que le service Distributed Transaction Coordinator fonctionne correctement :  
>   
>  -   La réinstallation de MSDTC peut rétablir les valeurs par défaut des options de configuration de la sécurité MSDTC. Après la réinstallation de MSDTC, vérifiez que les options de configuration de la sécurité MSDTC sont définies sur les valeurs appropriées.  
> -   La réinstallation de MSDTC peut modifier la valeur **Type de démarrage** du service Distributed Transaction Coordinator. Après la réinstallation de MSDTC, vérifiez que la valeur **Type de démarrage** du service Distributed Transaction Coordinator est définie sur **Automatique** .  
> -   La réinstallation de MSDTC peut nécessiter un redémarrage de l'ordinateur. Pour vérifier que le service Distributed Transaction Coordinator fonctionne correctement, redémarrez l'ordinateur après la réinstallation de MSDTC.  
  
## <a name="see-also"></a>Voir aussi  
 [Outils et utilitaires à utiliser pour la résolution des problèmes](../core/tools-and-utilities-to-use-for-troubleshooting.md)   
 [Résolution des problèmes d’un Cluster Windows Server](../core/troubleshooting-a-windows-server-cluster.md)