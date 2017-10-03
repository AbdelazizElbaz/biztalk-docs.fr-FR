---
title: "Générales de BizTalk Server Optimizations2 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 41b452e9-d94c-4bcb-8ef6-e9cea28fc0ab
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3d4777545d7522a1f8ca61e9209669b489ebcb30
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="general-biztalk-server-optimizations"></a>Optimisations générales de BizTalk Server
Les recommandations suivantes peuvent être utilisées pour augmenter [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] performances. Les optimisations répertoriées dans cette rubrique sont appliquées après [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] a été installé et configuré.  
  
## <a name="create-multiple-biztalk-server-hosts-and-separate-host-instances-by-functionality"></a>Créer plusieurs hôtes BizTalk Server et les instances d’hôte distinctes par fonctionnalité  
 Des hôtes distincts doivent être créés pour envoyer, recevoir, traiter et fonctionnalités de suivi. Création de plusieurs hôtes BizTalk offre une grande souplesse lors de la configuration de la charge de travail dans votre groupe BizTalk et constitue le principal moyen de distribuer le traitement entre les serveurs BizTalk Server dans un groupe BizTalk. Plusieurs ordinateurs hôtes vous permettent également d’arrêter un ordinateur hôte sans affecter les autres hôtes. Pouvez par exemple, si vous souhaitez arrêter l’envoi de messages pour leur permettre de file d’attente dans la base de données Messagebox, tout en autorisant la trafic entrante réception de messages se produise. Séparation des instances d’hôte par la fonctionnalité fournit également les avantages suivants :  
  
-   Chaque instance d’hôte possède son propre ensemble de ressources, telles que la mémoire, les poignées et les threads dans le pool de threads .NET.  
  
-   Plusieurs hôtes BizTalk permet également de réduire la contention sur les tables de file d’attente de hôte de base de données Messagebox, car chaque hôte possède ses propres tables de file d’attente de travail dans la base de données Messagebox.  
  
-   La limitation est implémentée dans BizTalk Server au niveau de l’hôte. Cela vous permet de définir différentes caractéristiques de limitation pour chaque hôte.  
  
-   La sécurité est implémentée au niveau de l’hôte ; chaque hôte s’exécute sous une identité Windows discrète. Cela vous permettrait, par exemple, pour accorder l’accès de Host_A à FileShare_B, tout en autorisant ne pas un des autres ordinateurs hôtes à accéder au partage de fichiers.  
  
> [!NOTE]  
>  Bien qu’il existe des avantages à la création des instances d’hôte supplémentaires, il existe également des inconvénients potentiels si trop d’instances d’hôte sont créées. Chaque instance d’hôte est un service Windows (BTSNTSvc.exe), qui génère une charge supplémentaire par rapport à la base de données MessageBox et consomme des ressources de l’ordinateur (par exemple, UC, mémoire, les threads).  
  
 Pour plus d’informations sur la modification des propriétés de l’hôte BizTalk Server, consultez « Modification des propriétés de hôte » dans le [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] à l’adresse [http://go.microsoft.com/fwlink/?LinkId=101588](http://go.microsoft.com/fwlink/?LinkId=101588).  
  
## <a name="configure-a-dedicated-tracking-host"></a>Configurer un hôte de suivi dédié  
 BizTalk Server est optimisé pour le débit, afin de l’orchestration principale et les moteurs de messagerie ne pas réellement déplacent les messages directement aux bases de données des suivis BizTalk ou BAM, comme ce serait transférer ces moteurs à partir de leur travail principal de l’exécution des processus d’entreprise. Au lieu de cela, BizTalk Server conserve les messages dans la base de données MessageBox et les marque comme nécessitant un déplacement vers la base de données des suivis BizTalk. Un processus en arrière-plan (l’hôte de suivi), puis se déplace les messages vers les bases de données des suivis BizTalk et l’analyse BAM. Étant donné que le suivi des modifications est une opération gourmande en ressources, un hôte distinct doit être créé qui est dédié au suivi, réduisant ainsi l’impact suivi sur les ordinateurs hôtes dédiés au traitement des messages.  
  
 À l’aide d’un hôte de suivi dédié vous permet également d’arrêter les autres hôtes BizTalk sans interférer avec le suivi de BizTalk Server. Le déplacement des données en dehors de la base de données de suivi est essentiel pour un système BizTalk Server intègre. Si l’hôte BizTalk responsable du déplacement des données de suivi dans le groupe BizTalk est arrêté, le service de décodage de données de suivi ne fonctionnera pas. L’impact de ce est comme suit :  
  
-   HAT des données de suivi n’est pas déplacé à partir de la base de données Messagebox à la base de données des suivis BizTalk.  
  
-   Données de suivi BAM n’est pas déplacé à partir de la base de données Messagebox à la base de données d’importation principale BAM.  
  
-   Étant donné que les données ne sont pas déplacées, il ne peut pas être supprimé à partir de la base de données Messagebox.  
  
-   Lorsque le service de décodage de données de suivi est arrêté, le suivi des intercepteurs toujours déclenche, écrire des données de suivi dans la base de données Messagebox. Si les données ne sont pas déplacées, cela entraîne la base de données Messagebox à être saturé, ce qui aura un impact sur les performances au fil du temps. Même si les propriétés personnalisées ne sont pas suivies ou les profils de l’analyse BAM ne sont pas définies, par défaut des données de suivi sont effectuées (telles que le pipeline de réception / envoyer des événements et des événements de l’orchestration). Si vous ne souhaitez pas exécuter le service de décodage de données de suivi, désactivez tous les suivi afin qu’aucun des intercepteurs d’enregistrement des données dans la base de données. Pour désactiver le suivi global, voir « Comment de désactivation du suivi Global » dans le [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] à l’adresse [http://go.microsoft.com/fwlink/?LinkId=101589](http://go.microsoft.com/fwlink/?LinkId=101589). La console Administration de BizTalk Server permet de désactiver le suivi des événements de manière sélective.  
  
 L’hôte de suivi doit être exécuté sur au moins deux ordinateurs exécutant BizTalk Server (pour assurer la redondance dans les cas de défaillance d’un). Pour des performances optimales, vous devez avoir suivi au moins une instance de l’hôte par base de données Messagebox. Le nombre réel de suivi des instances d’hôte doit être (N + 1), où N = nombre de bases de données Messagebox. Le « + 1 » est pour la redondance, en cas de défaillance d’un des ordinateurs hébergeant le suivi.  
  
 Un suivi instance d’hôte déplace les données de suivi pour les bases de données Messagebox spécifiques, mais il y aura jamais l’hôte de suivi plus d’une instance de déplacer les données d’une base de données Messagebox spécifique. Par exemple, si vous avez trois bases de données Messagebox et que deux instances de l’hôte de suivi, une des instances de l’hôte doit déplacer les données de deux bases de données Messagebox. Ajout d’une troisième instance de l’hôte de suivi distribue le suivi des hôtes de travail vers un autre ordinateur exécutant BizTalk Server. Dans ce scénario, ajout d’une quatrième instance de l’hôte de suivi ne serait pas distribuer n’importe quel hôte de suivi plus de travail, mais cela permet de fournir un fichier extra suivi d’instance d’hôte pour la tolérance de panne.  
  
 Pour plus d’informations sur le service Bus d’événements BAM, consultez les rubriques suivantes dans le [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] aide :  
  
-   « Gestion de Service Bus d’événements BAM » au [http://go.microsoft.com/fwlink/?LinkId=101590](http://go.microsoft.com/fwlink/?LinkId=101590).  
  
-   « Création d’Instances de Service Bus d’événements BAM » à [http://go.microsoft.com/fwlink/?LinkId=101591](http://go.microsoft.com/fwlink/?LinkId=101591).  
  
## <a name="manage-aspnet-thread-usage-or-concurrently-executing-requests-for-web-applications-that-host-orchestrations-published-as-a-web-or-wcf-service"></a>Gérer l’utilisation de thread ASP.NET ou de manière simultanée des demandes pour les applications Web que les orchestrations de l’hôte publié en tant qu’un site ou un Service WCF  
 Le nombre de processus de travail et les threads d’e/s (IIS 6.0 et IIS 7.0 en mode classique) ou le nombre de demandes (IIS 7.0 en mode intégré) pour une application Web ASP.NET qui héberge une orchestration de manière simultanée publié comme un service Web doit être modifié sous le conditions suivantes :  
  
-   Utilisation du processeur n’est pas un goulot d’étranglement sur le serveur d’hébergement Web.  
  
-   La valeur de la **les applications ASP.NET v2.0.50727\Request du temps d’attente** ou **les applications ASP.NET v2.0.50727\Request temps d’exécution** les compteurs de performance est anormalement élevée.  
  
-   Une erreur semblable au suivant généré dans le journal des applications de l’ordinateur qui héberge l’application Web :  
  
    ```  
    Event Type: Warning  
    Event Source: W3SVC Event Category: None  
    Event ID: 1013  
    Date: 6/4/2009  
    Time: 1:03:47 PM  
    User: N/A  
    Computer: <ComputerName>  
    Description: A process serving application pool 'DefaultAppPool' exceeded time limits during shut down. The process id was '<xxxx>'  
    ```  
  
### <a name="manage-aspnet-thread-usage-for-web-applications-that-host-orchestrations-on-iis-60-and-on-iis-70-running-in-classic-mode"></a>Gérer l’utilisation de thread ASP.NET pour les applications Web qui hébergent les orchestrations sur IIS 6.0 et IIS 7.0 en mode classique  
 Lorsque le **autoConfig** dans le fichier machine.config, d’un serveur d’IIS 6.0 ou IIS 7.0 en mode classique a la valeur **true**, ASP.NET 2.0 gère le nombre de threads de travail et de threads e/s qui sont alloué à n’importe quel processus de travail IIS associés :  
  
```  
<processModel autoConfig="true" />  
```  
  
 Pour modifier manuellement le nombre de threads d’e/s pour une application Web ASP.NET 2.0 et de travail, ouvrez le fichier machine.config associée, puis entrez les nouvelles valeurs pour le **maxWorkerThreads** et **maxIoThreads**paramètres :  
  
```  
<!-- <processModel autoConfig="true" /> -->  
    <processModel maxWorkerThreads="200" maxIoThreads="200" />  
```  
  
> [!NOTE]  
>  Ces valeurs sont à titre indicatif uniquement. Assurez-vous de que tester les modifications à ces paramètres.  
  
 Pour plus d’informations sur le réglage des paramètres dans le fichier machine.config pour une application Web ASP.NET 2.0, consultez l’article de la Base de connaissances Microsoft [821268 « Contention, des performances médiocres et blocages lorsque vous effectuez des demandes de service Web à partir d’ASP.NET applications »](http://go.microsoft.com/fwlink/?LinkID=66483) (http://go.microsoft.com/fwlink/?LinkID=66483).  
  
### <a name="manage-the-number-of-concurrently-executing-requests-for-web-applications-that-host-orchestrations-on-iis-70-running-in-integrated-mode"></a>Gérer le nombre de demandes pour les applications Web qui hébergent les orchestrations sur IIS 7.0 en mode intégré de manière simultanée  
 Lorsque ASP.NET 2.0 est hébergé sur IIS 7.0 en mode intégré, l’utilisation de threads est gérée différemment que sur IIS 6.0 ou IIS 7.0 en mode classique. Lorsque ASP.NET 2.0 est hébergé sur IIS 7.0 en mode intégré, ASP.NET 2.0 limite le nombre de manière simultanée **demandes** plutôt que le nombre de **threads** demandes de manière simultanée. Pour les scénarios synchrones cette limite indirectement le nombre de threads, mais pour les scénarios asynchrones le nombre de demandes et les threads seront probablement très différent. Lors de l’exécution d’ASP.NET 2.0 sur IIS 7.0 en mode intégré, le **maxWorkerThreads** et **maxIoThreads** paramètres dans le fichier machine.config ne sont pas utilisés pour régir le nombre de threads en cours d’exécution. Au lieu de cela, le nombre de demandes de manière simultanée peut être modifié à partir de la valeur par défaut de 12 par UC en modifiant la valeur spécifiée pour **maxConcurrentThreadsPerCPU**. Le **maxConcurrentThreadsPerCPU** valeur peut être spécifiée dans le reqistry ou dans la section de configuration d’un fichier aspnet.config. Procédez comme suit pour modifier la valeur par défaut **maxConcurrentThreadsPerCPU** pour indiquer le nombre de demandes de manière simultanée :  
  
 **Pour définir la valeur maxConcurrentThreadsPerCPU dans le Registre**  
  
> [!WARNING]  
>  Une utilisation incorrecte de l'Éditeur du Registre peut causer des problèmes vous obligeant à réinstaller votre système d'exploitation. Son utilisation est sous votre entière responsabilité. Pour plus d’informations sur la façon de sauvegarder, restaurer et modifier le Registre, consultez l’article de la Base de connaissances Microsoft « Description du Registre de Microsoft Windows » à [http://go.microsoft.com/fwlink/?LinkId=62729](http://go.microsoft.com/fwlink/?LinkId=62729).  
  
> [!NOTE]  
>  Ce paramètre est global et ne peut pas être modifié pour les applications ou les pools d’applications individuels.  
  
1.  Cliquez sur **Démarrer**, **Exécuter**, tapez **regedit.exe**, puis cliquez sur **OK** pour démarrer l'Éditeur du Registre.  
  
2.  Accédez à **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ASP.NET\2.0.50727.0**  
  
3.  Créez la clé en suivant ces étapes :  
  
    1.  Sur le **modifier** menu, cliquez sur **nouveau**, puis cliquez sur **clé**.  
  
    2.  Type **maxConcurrentThreadsPerCPU**, puis appuyez sur **entrée**.  
  
    3.  Sous le **maxConcurrentThreadsPerCPU** clé, créez une entrée DWORD avec la nouvelle valeur pour maxConcurrentThreadsPerCPU.  
  
    4.  Fermez l'Éditeur de Registre.  
  
 **La valeur maxConcurrentThreadsPerCPU pour un pool d’applications dans la section de configuration d’un fichier aspnet.config**  
  
> [!NOTE]  
>  Microsoft .NET Framework 3.5 Service Pack 1 doit être installé pour prendre en charge la définition des valeurs ci-dessous via le fichier de configuration. Vous pouvez télécharger Microsoft .NET Framework 3.5 Service Pack 1 à partir de [http://go.microsoft.com/fwlink/?LinkID=136345](http://go.microsoft.com/fwlink/?LinkID=136345).  
  
-   Ouvrez le fichier aspnet.config du pool d’applications, puis entrez les nouvelles valeurs pour le **maxConcurrentRequestsPerCPU** et **requestQueueLimit** paramètres :  
  
```  
<system.web>  
    <applicationPool maxConcurrentRequestsPerCPU="12" requestQueueLimit="5000"/>  
</system.web>  
```  
  
> [!NOTE]  
>  Cette valeur remplace la valeur spécifiée pour **maxConcurrentThreadsPerCPU** dans le Registre. Le paramètre requestQueueLimit est le même que processModel/requestQueueLimit, sauf que le paramètre dans le fichier aspnet.config remplace le paramètre dans le fichier machine.config.  
  
## <a name="define-clr-hosting-thread-values-for-biztalk-host-instances"></a>Définir les valeurs de thread pour les instances d’hôte BizTalk d’hébergement du CLR  
 Un thread Windows étant l'unité exécutable la plus basique disponible pour un processus Windows, il est important d'en allouer suffisamment au pool de threads .NET associé à une instance d'un hôte BizTalk pour prévenir la pénurie de threads. Pareil cas, il ne sont pas suffisamment de threads disponibles pour effectuer le travail demandé qui affecte négativement les performances. En même temps, veillez à n’allouer plus de threads au pool de threads.NET associé à un hôte qu’il n’est nécessaire. L'allocation d'un nombre trop important de threads au pool de threads .NET associé à un hôte peut favoriser le basculement de contexte. Ce phénomène survient lorsque le noyau Windows bascule à partir de l’exécution d’un thread à un autre thread, ce qui entraîne une baisse des performances. Allocation de threads excessive peut entraîner le basculement de contexte excessifs, susceptible d’affecter les performances globales.  
  
 Modifier le nombre de threads Windows disponibles dans le pool de threads .NET associé à une instance d’un hôte BizTalk en créant les valeurs d’hébergement CLR appropriées dans le Registre de BizTalk Server.  
  
> [!WARNING]  
>  Une utilisation incorrecte de l'Éditeur du Registre peut causer des problèmes vous obligeant à réinstaller votre système d'exploitation. Son utilisation est sous votre entière responsabilité. Pour plus d’informations sur la façon de sauvegarder, restaurer et modifier le Registre, consultez l’article de la Base de connaissances Microsoft « Description du Registre de Microsoft Windows » à [http://go.microsoft.com/fwlink/?LinkId=62729](http://go.microsoft.com/fwlink/?LinkId=62729).  
  
> [!NOTE]  
>  **Threads de travail** sont utilisés pour traiter les éléments de travail en file d’attente et **les threads d’e/s** sont des threads de rappel dédiés associés à un port de terminaison d’e/s pour traiter une demande d’e/s asynchrone terminée.  
  
 **Pour modifier le nombre de threads disponibles dans le pool de threads .NET associé à chaque instance d’un hôte BizTalk, procédez comme suit :**  
  
1.  Arrêtez l’instance d’hôte BizTalk.  
  
2.  Cliquez sur **Démarrer**, **Exécuter**, tapez **regedit.exe**, puis cliquez sur **OK** pour démarrer l'Éditeur du Registre.  
    Accédez à **HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\BTSSvc$***nom d’hôte*] où *nom d’hôte* est le nom de l’hôte associé à l’hôte instance.  
  
    > [!NOTE]  
    >  Si vous avez mis à niveau votre installation de BizTalk Server 2006 de BizTalk Server 2004, cette clé de Registre peut être représentée en tant que **HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\BTSSvc***guid*] où *guid* est un GUID unique pour chaque instance d’un hôte BizTalk Server.  
  
3.  Recherchez le **CLR Hosting** clé. Si cette clé n’existe pas, créez la clé en suivant ces étapes :  
  
    1.  Sur le **modifier** menu, cliquez sur **nouveau**, puis cliquez sur **clé**.  
  
    2.  Type **CLR Hosting**, puis appuyez sur **entrée**.  
  
4.  Sous le **CLR Hosting** clé, créez les entrées DWORD suivantes avec les valeurs indiquées.  
  
    |Entrée DWORD|Valeur par défaut|Valeur recommandée|  
    |-----------------|-------------------|-----------------------|  
    |MaxIOThreads|20|100|  
    |MaxWorkerThreads|25|100 **Important :** valeur supérieure à 100 peut avoir un effet néfaste sur les performances de l’ordinateur SQL Server hébergeant la base de données MessageBox de BizTalk Server. Lorsque ce problème se produit, SQL Server peut rencontrer une situation de blocage. Il est recommandé de que ce paramètre n’est pas augmenté au-delà de la valeur 100.|  
    |MinIOThreads|1|25|  
    |MinWorkerThreads|1|25|  
  
    > [!NOTE]  
    >  Ces recommandé de valeurs seront suffisants pour la plupart des scénarios mais doivent être augmentées en fonction du nombre de gestionnaires d’adaptateur ou orchestrations en cours d’exécution dans chaque instance d’hôte.  
  
    > [!NOTE]  
    >  Ces valeurs sont implicitement multipliées par le nombre de processeurs sur le serveur. Par exemple, définissez l’entrée de MaxWorkerThreads sur une valeur de 100 efficacement définiriez une valeur de 400 sur un serveur de l’UC de 4.  
  
5.  Fermez l'Éditeur de Registre.  
  
6.  Redémarrez l’instance d’hôte BizTalk.  
  
## <a name="disable-tracking-for-orchestrations-send-ports-receive-ports-and-pipelines-when-tracking-is-not-required"></a>Désactiver le suivi des orchestrations, ports d’envoi, ports de réception et pipelines lorsque le suivi n’est pas obligatoire  
 Suivi entraîne des performances de traitement dans BizTalk Server donnée ne doit être écrite dans la base de données MessageBox et ensuite asynchrone vers la base de données des suivis BizTalk. Si le suivi n’est pas une exigence, puis désactivez le suivi pour réduire la surcharge et augmenter les performances. Pour plus d’informations sur la configuration de suivi, consultez « Configuration de suivi à l’aide de la Console Administration BizTalk Server » dans le [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] à l’adresse [http://go.microsoft.com/fwlink/?LinkID=106742](http://go.microsoft.com/fwlink/?LinkID=106742).  
  
## <a name="decrease-the-purging-period-for-the-dta-purge-and-archive-job-from-7-days-to-2-days-in-high-throughput-scenarios"></a>Réduisez la période de purge de la tâche d’archivage de 7 jours à 2 jours dans les scénarios de débits élevés et DTA Purge  
 Par défaut, l’intervalle de vidage pour le suivi des données dans BizTalk Server est défini sur 7 jours. Dans un scénario d’un débit élevé, cela peut entraîner une accumulation excessive de données dans la base de données de suivi qui finalement affectera les performances de la MessageBox et à son tour négativement débit de traitement des messages impact.  
  
 Dans les scénarios de débits élevés, réduire les matériels et logiciels purge intervalle à partir de la valeur par défaut de 7 jours à 2 jours. Pour plus d’informations sur la configuration de l’intervalle de vidage, consultez « Comment pour configurer le DTA Purge et Archive la tâche » dans le [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] à l’adresse [http://go.microsoft.com/fwlink/?LinkID=104908](http://go.microsoft.com/fwlink/?LinkID=104908).  
  
## <a name="install-the-latest-service-packs"></a>Installer les derniers service packs  
 Les derniers service packs pour BizTalk Server et le .NET Framework doivent être installés, car ils contiennent les correctifs qui peuvent corriger les problèmes de performances que vous pouvez rencontrer.  
  
## <a name="do-not-cluster-biztalk-hosts-unless-absolutely-necessary"></a>Pas de cluster hôtes BizTalk, sauf si c’est absolument nécessaire.  
 Alors que [!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)] et ses versions ultérieures [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] vous permettent de configurer un hôte BizTalk en tant que ressource de cluster, vous n’envisagez cette opération si vous avez besoin fournir une haute disponibilité à une ressource qui ne peut pas être hébergée sur plusieurs BizTalk ordinateurs. Comme un exemple, les ports à l’aide de l’adaptateur FTP doit résider uniquement sur une instance d’un ordinateur hôte, comme le protocole FTP ne fournit pas de verrouillage de fichier, toutefois, elle présente un seul point de défaillance qui pourraient tirer parti de la gestion de clusters. Hôtes qui contiennent des adaptateurs, tels que le fichier, SQL, HTTP ou de traiter uniquement les ordinateurs hôtes, peuvent être en interne à charge équilibrée entre ordinateurs et ne bénéficient pas de clustering.  
  
## <a name="performance-optimizations-in-the-biztalk-server-documentation"></a>Optimiser les performances dans la documentation de BizTalk Server  
 Appliquer les recommandations suivantes à partir de la documentation de BizTalk Server comme il convient :  
  
-   « Dépannage des problèmes de latence de MessageBox » à [http://go.microsoft.com/fwlink/?LinkId=114747](http://go.microsoft.com/fwlink/?LinkId=114747)  
  
-   « Identifier les goulots d’étranglement de performances » [http://go.microsoft.com/fwlink/?LinkID=104418](http://go.microsoft.com/fwlink/?LinkID=104418)  
  
-   « Ce qui évite d’Exceptions DBNETLIB » à [http://go.microsoft.com/fwlink/?LinkID=108787](http://go.microsoft.com/fwlink/?LinkID=108787)  
  
-   « Ce qui évite d’épuisement du Port TCP/IP » à [http://go.microsoft.com/fwlink/?LinkID=101610](http://go.microsoft.com/fwlink/?LinkID=101610)  
  
-   « Configuration de la taille de pool de threads de terminaison » à [http://go.microsoft.com/fwlink/?LinkId=114748](http://go.microsoft.com/fwlink/?LinkId=114748)