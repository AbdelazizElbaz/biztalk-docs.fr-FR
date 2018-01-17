---
title: "Générales de BizTalk Server Optimizations1 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e8032553-bae3-440d-9197-b926160b0bdf
caps.latest.revision: "28"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2e9e799822c63cb78eda1b989cb157c71fd357d8
ms.sourcegitcommit: 3fd1c85d9dc2ce7b77da75a5c2087cc48cfcbe50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="general-biztalk-server-optimizations"></a>Optimisations générales de BizTalk Server
Les recommandations suivantes peuvent être utilisées pour augmenter les performances de BizTalk Server. Les optimisations répertoriées dans cette rubrique sont appliquées après que BizTalk Server a été installé et configuré.  
  
## <a name="configure-msdtc"></a>Configurer MSDTC  
 Pour faciliter les transactions entre SQL Server et BizTalk Server, vous devez activer Microsoft Distributed Transaction Coordinator (MS DTC). Pour configurer MSDTC sur BizTalk Server, consultez la rubrique [recommandations générales pour améliorer les performances de système d’exploitation](../technical-guides/general-guidelines-for-improving-operating-system-performance.md).  
  
## <a name="recommendations-for-configuring-biztalk-server-hosts"></a>Recommandations pour la configuration des hôtes BizTalk Server  
 Cette section fournit des recommandations pour la configuration des hôtes BizTalk Server.  
  
### <a name="create-multiple-biztalk-server-hosts-and-separate-host-instances-by-functionality"></a>Créer plusieurs hôtes BizTalk Server et les instances d’hôte distinctes par fonctionnalité  
 Suivez ces instructions pour créer plusieurs hôtes BizTalk Server et d’allouer de la charge de travail entre les hôtes :  
  
-   Créez des hôtes distincts pour l’envoi, réception, traitement et fonctionnalités de suivi. Création de plusieurs hôtes BizTalk offre une grande souplesse lors de la configuration de la charge de travail dans votre groupe BizTalk et constitue le principal moyen de distribuer le traitement sur tous les ordinateurs exécutant BizTalk Server dans un groupe BizTalk. À l’aide de plusieurs ordinateurs hôtes vous permet d’arrêter un ordinateur hôte sans affecter les autres hôtes. Pouvez par exemple, si vous souhaitez arrêter l’envoi de messages pour leur permettre de file d’attente dans la base de données MessageBox tout en permettant à un adaptateur de réception en cours d’exécution dans une instance d’hôte différents recevoir des messages entrants. Séparation des instances d’hôte par la fonctionnalité fournit également les avantages suivants :  
  
    -   Plusieurs hôtes BizTalk en cours d’exécution de réduit la contention sur les tables de file d’attente de hôte de base de données MessageBox, car chaque hôte possède ses propres tables de file d’attente de travail dans la base de données MessageBox.  
  
    -   La limitation est implémentée dans BizTalk Server au niveau de l’hôte. Cela vous permet de définir différentes caractéristiques de limitation pour chaque hôte.  
  
    -   La sécurité est implémentée au niveau de l’hôte ; chaque hôte s’exécute sous une identité Windows discrète. Cela vous permet, par exemple, permettent d’Host_A FileShare_B, tout en autorisant ne pas un des autres ordinateurs hôtes à accéder au partage de fichiers.  
  
-   Chaque instance d’hôte possède son propre ensemble de ressources, telles que la mémoire, les poignées et les threads dans le pool de threads .NET. Lors de l’allocation de la charge de travail sur tous les hôtes envisager de placer les ressources de mise à l’échelle ensemble dans le même hôte.  
  
-   Des cartes distinctes et les orchestrations qui ont des priorités différentes pour les ressources dans des hôtes différents. Cette technique permet la sélection élective des ordinateurs hôtes exécutant des applications de haute priorité sur les ordinateurs BizTalk Server dédiés.  
  
> [!NOTE]  
>  Bien qu’il existe des avantages à la création des instances d’hôte supplémentaires, il existe également des inconvénients potentiels si trop d’instances d’hôte sont créées. Chaque instance d’hôte est un service Windows (BTSNTSvc.exe), qui génère une charge supplémentaire par rapport à la base de données MessageBox et consomme des ressources de l’ordinateur (par exemple, UC, mémoire, les threads).  
  
 Pour plus d’informations sur la modification de BizTalk Server propriétés d’hôte, consultez [comment modifier les propriétés de l’hôte](http://go.microsoft.com/fwlink/?LinkID=154359) (http://go.microsoft.com/fwlink/?LinkID=154359) dans l’aide de BizTalk Server 2010.  
  
### <a name="configure-a-dedicated-tracking-host"></a>Configurer un hôte de suivi dédié  
 BizTalk Server est optimisé pour le débit, afin de l’orchestration principale et les moteurs de messagerie ne pas réellement déplacent les messages directement aux bases de données des suivis BizTalk ou BAM, comme ce serait transférer ces moteurs à partir de leur travail principal de l’exécution des processus d’entreprise. Au lieu de cela, BizTalk Server conserve les messages dans la base de données MessageBox et les marque comme nécessitant un déplacement vers la base de données des suivis BizTalk. Un processus en arrière-plan (l’hôte de suivi), puis se déplace les messages vers les bases de données des suivis BizTalk et l’analyse BAM. Étant donné que le suivi des modifications est une opération gourmande en ressources, un hôte distinct doit être créé qui est dédié au suivi, réduisant ainsi l’impact suivi sur les ordinateurs hôtes dédiés au traitement des messages. Pour des performances optimales, il doit y avoir moins d’une suivi instance de l’hôte par base de données MessageBox. Le nombre réel de suivi des instances d’hôte doit être N + 1, où N = nombre de bases de données MessageBox. Le « + 1 » est pour la redondance, en cas de défaillance d’un des ordinateurs hébergeant le suivi.  
  
 À l’aide d’un hôte de suivi dédié vous permet également d’arrêter les autres hôtes BizTalk sans interférer avec le suivi de BizTalk Server. Le déplacement des données en dehors de la base de données de suivi est essentiel pour un système BizTalk Server intègre. Si l’hôte BizTalk responsable du déplacement des données de suivi dans le groupe BizTalk est arrêté, le service de décodage de données de suivi ne fonctionnera pas. L’impact de ce est comme suit :  
  
-   HAT des données de suivi n’est pas déplacé à partir de la base de données MessageBox à la base de données des suivis BizTalk.  
  
-   Données de suivi BAM n’est pas déplacé à partir de la base de données MessageBox à la base de données d’importation principale BAM.  
  
-   Étant donné que les données ne sont pas déplacées, il ne peut pas être supprimé à partir de la base de données MessageBox.  
  
-   Lorsque le service de décodage de données de suivi est arrêté, le suivi des intercepteurs toujours déclenche, écrire des données de suivi dans la base de données MessageBox. Si les données ne sont pas déplacées, cela entraîne la base de données MessageBox à être saturé, ce qui aura un impact sur les performances au fil du temps. Même si les propriétés personnalisées ne sont pas suivies ou les profils de l’analyse BAM ne sont pas définies, par défaut des données de suivi sont effectuées (telles que le pipeline de réception / envoyer des événements et des événements de l’orchestration). Si vous ne souhaitez pas exécuter le service de décodage de données de suivi, désactivez tous les suivi afin qu’aucun des intercepteurs d’enregistrement des données dans la base de données. Pour désactiver le suivi global, consultez [la désactivation du suivi Global](http://go.microsoft.com/fwlink/?LinkID=154193) (http://go.microsoft.com/fwlink/?LinkID=154193) dans l’aide de BizTalk Server 2010. La console Administration de BizTalk Server permet de désactiver le suivi des événements de manière sélective.  
  
 L’hôte de suivi doit être exécuté sur au moins deux ordinateurs exécutant BizTalk Server (pour assurer la redondance dans les cas de défaillance d’un). Pour des performances optimales, vous devez avoir suivi au moins une instance de l’hôte par base de données MessageBox. Le nombre réel de suivi des instances d’hôte doit être (N + 1), où N = nombre de bases de données MessageBox. Le « + 1 » est pour la redondance, en cas de défaillance d’un des ordinateurs hébergeant le suivi.  
  
 Un suivi instance d’hôte déplace les données de suivi pour les bases de données MessageBox spécifiques, mais il y aura jamais l’hôte de suivi plus d’une instance de déplacer les données d’une base de données MessageBox spécifique. Par exemple, si vous avez trois bases de données MessageBox et que deux instances de l’hôte de suivi, une des instances de l’hôte doit déplacer les données de deux bases de données MessageBox. Ajout d’une troisième instance de l’hôte de suivi distribue le suivi des hôtes de travail vers un autre ordinateur exécutant BizTalk Server. Dans ce scénario, ajout d’une quatrième instance de l’hôte de suivi ne serait pas distribuer n’importe quel hôte de suivi plus de travail, mais cela permet de fournir un fichier extra suivi d’instance d’hôte pour la tolérance de panne.  
  
 Pour plus d’informations sur le service Bus d’événements BAM, consultez les rubriques suivantes dans l’aide de BizTalk Server 2010 :  
  
-   [La gestion de Service Bus d’événements BAM](http://go.microsoft.com/fwlink/?LinkID=154194) (http://go.microsoft.com/fwlink/?LinkID=154194).  
  
-   [Création d’Instances de Service Bus d’événements BAM](http://go.microsoft.com/fwlink/?LinkID=154195) (http://go.microsoft.com/fwlink/?LinkID=154195).  
  
### <a name="do-not-cluster-biztalk-hosts-unless-absolutely-necessary"></a>Pas de cluster hôtes BizTalk, sauf si c’est absolument nécessaire.  
 Lorsque BizTalk Server 2010 vous permet de configurer un hôte BizTalk en tant que ressource de cluster, vous n’envisagez cette opération si vous avez besoin fournir une haute disponibilité à une ressource qui ne peut pas être hébergée sur plusieurs ordinateurs BizTalk. Par exemple, les ports à l’aide de l’adaptateur FTP doivent résider uniquement sur une instance d’un ordinateur hôte, comme le protocole FTP ne fournit pas de verrouillage de fichier. Toutefois, elle présente un point de défaillance, ce qui pourraient tirer parti de la mise en cluster unique. Hôtes qui contiennent des adaptateurs, tels que le fichier, SQL, HTTP ou de traiter uniquement les ordinateurs hôtes, peuvent être en interne à charge équilibrée sur plusieurs ordinateurs et ne bénéficient pas de clustering.  
  
## <a name="increase-the-number-of--http-concurrent-connections-allowed-by-changing-the-value-for-the-maxconnection-parameter"></a>Augmenter le nombre de connexions HTTP autorisées en modifiant la valeur pour le paramètre maxconnection  
 Par défaut, les adaptateurs HTTP (y compris les adaptateurs HTTP basé sur WCF) ouvrent uniquement deux connexions HTTP simultanées à partir de chaque ordinateur exécutant BizTalk Server à n’importe quel serveur de destination spécifique.  
  
 Ce paramètre est conforme à la RFC de l’IETF pour la spécification HTTP 1.1, et bien qu’il soit adapté aux scénarios utilisateur, il n’est pas optimisée pour un débit élevé. Le paramètre de limite efficacement les appels HTTP sortants pour chaque serveur à deux envois simultanés à partir de chaque ordinateur exécutant BizTalk Server.  
  
 Pour augmenter le nombre de connexions simultanées, vous pouvez modifier la valeur pour le paramètre maxconnection dans le fichier de configuration de BizTalk Server, BTSNTSvc.exe.config (ou BTSNTSvc64.exe.config pour les ordinateurs hôtes 64 bits) sur chaque serveur BizTalk Server. Vous pouvez l’augmenter pour l’appel des serveurs spécifiques. En règle générale, la valeur pour le paramètre maxconnection doit être définie à 12 * nombre de processeurs ou cœurs sur l’ordinateur qui héberge l’application web.  
  
> [!NOTE]  
>  N’augmentez pas la valeur pour le paramètre maxconnection une valeur plus élevée que le serveur Web qui est appelé est submergé par les connexions HTTP. Après avoir modifié la valeur pour le paramètre maxconnection, effectuer des tests de stress à envoyer des requêtes pour chaque serveur Web de destination afin de déterminer une valeur pour maxconnection qui fournira les bonnes performances et HTTP envoie sans pour autant submerger le site Web cible serveurs.  
  
 Voici un exemple de configuration de la propriété du nombre maximal de connexions :  
  
```  
<configuration>  
  <system.net>  
    <connectionManagement>  
      <add address="http://www.contoso.com" maxconnection="24" />  
      <add address="*" maxconnection="48" />  
    </connectionManagement>  
  </system.net>  
</configuration>  
```  
  
 Lorsque vous définissez la propriété maxconnection, HTTP, HTTPS, l’adresse IP du site web et le numéro de port peuvent être spécifiés. Autres exemples :  
  
 **\<add address="https://www.contoso.com" maxconnection="24" /\>**   
**\<Ajouter une adresse = « http://www.contoso.com : 8080 » maxconnection = « 24 » /\>**   
**\<Ajouter une adresse = « http://*IPAddress*« maxconnection = « 24 » /\>**  pour plus d’informations sur le réglage des paramètres IIS et ASP.NET pour les services Web, consultez les paramètres ASP.NET » qui peuvent avoir un impact sur l’adaptateur HTTP section de performances » de [les paramètres de Configuration qui affectent les performances carte](http://go.microsoft.com/fwlink/?LinkID=154200) (http://go.microsoft.com/fwlink/?LinkID=154200) dans l’aide de BizTalk Server 2010.  
  
## <a name="manage-aspnet-thread-usage-or-concurrently-executing-requests-for-web-applications-that-can-host--isolated-received-locations-back-end-web-services-and-wcf-services"></a>Gérer l’utilisation de thread ASP.NET ou de demandes pour les applications Web qui peuvent héberger de manière simultanée isolé des emplacements de réception, les services Web principaux et les services WCF  
 Le nombre de processus de travail et les threads d’e/s (IIS 7.5 et IIS 7.0 en mode classique) ou le nombre de demandes (IIS 7.5 et 7.0 mode intégré) pour une application Web ASP.NET que les hôtes isolés les emplacements de réception, les services Web principaux et les services WCF de manière simultanée doit être modifié dans les conditions suivantes :  
  
-   Utilisation du processeur n’est pas un goulot d’étranglement sur le serveur d’hébergement Web.  
  
-   La valeur de :  
  
    -   **ASP.NET Apps v4.0.30319 \Request du temps d’attente** ou **les applications ASP.NET v4.0.30319 \Request exécution** les compteurs de performance est anormalement élevée.  
  
    -   **ASP.NET Apps v2.0.50727\Request du temps d’attente** ou **les applications ASP.NET v2.0.50727\Request exécution** les compteurs de performance est anormalement élevée.  
  
-   Une erreur semblable au suivant est générée dans le journal des applications de l’ordinateur qui héberge l’application Web.  
  
    ```  
    Event Type: Warning  
    Event Source: W3SVC Event Category: None  
    Event ID: 1013  
    Date: 11/4/2010  
    Time: 1:03:47 PM  
    User: N/A  
    Computer: <ComputerName>  
    Description: A process serving application pool 'DefaultAppPool' exceeded time limits during shut down. The process id was '<xxxx>'  
    ```  
  
### <a name="manage-aspnet-thread-usage-for-web-applications-that-can-host-isolated-received-locations-back-end-web-services-and-wcf-services-on-iis-75-and-iis-70-running-in-classic-mode"></a>Gérer l’utilisation de thread ASP.NET pour les applications Web qui peuvent héberger des emplacements de réception isolés, les services Web principaux et les services WCF sur IIS 7.5 et IIS 7.0 en mode classique  
 Lorsque le **autoConfig** dans le fichier machine.config, d’un serveur IIS 7.5 et IIS 7.0 en mode classique a la valeur **true**, ASP.NET 2.0 et ASP.NET 4 gère le nombre de threads de travail et les threads d’e/s qui sont allouées à n’importe quel processus de travail IIS associés.  
  
```  
<processModel autoConfig="true" />  
```  
  
 Pour modifier manuellement le nombre de threads d’e/s pour une application ASP.NET 2.0 et Web ASP.Net 4 et de travail, ouvrez le fichier machine.config associée, puis entrez les nouvelles valeurs pour le **maxWorkerThreads** et **maxIoThreads**  paramètres.  
  
```  
<!-- <processModel autoConfig="true" /> -->  
    <processModel maxWorkerThreads="200" maxIoThreads="200" />  
```  
  
> [!NOTE]  
>  Ces valeurs sont à titre indicatif uniquement. Assurez-vous de que tester les modifications à ces paramètres.  
  
 Pour plus d’informations sur le réglage des paramètres dans le fichier machine.config pour une application Web ASP.NET 2.0, consultez l’article de la Base de connaissances Microsoft 821268 [blocages lorsque vous effectuez des demandes de service Web à partir d’ASP Contention et des performances médiocres. Les applications NET](http://go.microsoft.com/fwlink/?LinkID=144169) (http://go.microsoft.com/fwlink/?LinkID=144169).  
  
### <a name="manage-the-number-of-concurrently-executing-requests-for-aspnet-20-web-applications-that-can-host-isolated-received-locations-back-end-web-services-and-wcf-services-on-iis-75-and-iis-70-running-in-integrated-mode"></a>Gérer le nombre de demandes pour les applications Web ASP.NET 2.0 qui peuvent héberger des emplacements de réception isolés, les services Web principaux et les services WCF sur IIS 7.5 et IIS 7.0 en mode intégré de manière simultanée  
 Lorsque ASP.NET 2.0 est hébergé sur IIS 7.5 et IIS 7.0 en mode intégré, l’utilisation de threads est gérée différemment que sur IIS 7.5 et IIS 7.0 en mode classique. Lorsque ASP.NET 2.0 est hébergé sur IIS 7.5 et IIS 7.0 en mode intégré, ASP.NET 2.0 limite le nombre de manière simultanée **demandes** plutôt que le nombre de **threads** de manière simultanée demandes. Pour les scénarios synchrones cette limite indirectement le nombre de threads, mais pour les scénarios asynchrones le nombre de demandes et les threads seront probablement très différent. Lors de l’exécution d’ASP.NET 2.0 sur IIS 7.5 et IIS 7.0 en mode intégré, le **maxWorkerThreads** et **maxIoThreads** paramètres dans le fichier machine.config ne sont pas utilisés pour régir le nombre de threads en cours d’exécution. Au lieu de cela, le nombre de demandes de manière simultanée peut être modifié à partir de la valeur par défaut de 12 par UC en modifiant la valeur spécifiée pour **maxConcurrentRequestsPerCPU**. Le **maxConcurrentRequestsPerCPU** valeur peut être spécifiée dans le reqistry ou dans la section de configuration d’un fichier aspnet.config. Procédez comme suit pour modifier la valeur par défaut **maxConcurrentRequestsPerCPU** pour indiquer le nombre de demandes de manière simultanée :  
  
 **Pour définir la valeur maxConcurrentRequestsPerCPU la valeur dans le Registre**  
  
> [!WARNING]  
>  Une utilisation incorrecte de l'Éditeur du Registre peut causer des problèmes vous obligeant à réinstaller votre système d'exploitation. Son utilisation est sous votre entière responsabilité. Pour plus d’informations sur la façon de sauvegarder, restaurer et modifier le Registre, consultez l’article 256986 de la Base de connaissances Microsoft [informations du Registre Windows pour les utilisateurs expérimentés](http://go.microsoft.com/fwlink/?LinkId=62729) (http://go.microsoft.com/fwlink/?LinkId=62729).  
  
> [!NOTE]  
>  Ce paramètre est global et ne peut pas être modifié pour les applications ou les pools d’applications individuels.  
  
1.  Cliquez sur **Démarrer**, **Exécuter**, tapez **regedit.exe**, puis cliquez sur **OK** pour démarrer l'Éditeur du Registre.  
  
2.  Accédez à **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ASP.NET\2.0.50727.0**  
  
3.  Créez la clé en suivant ces étapes :  
  
    1.  Sur le **modifier** menu, cliquez sur **nouveau**, puis cliquez sur **clé**.  
  
    2.  Type **maxConcurrentRequestsPerCPU**, puis appuyez sur **entrée**.  
  
    3.  Sous le **maxConcurrentRequestsPerCPU** clé, créez une entrée DWORD avec la nouvelle valeur pour maxConcurrentRequestsPerCPU la valeur.  
  
    4.  Fermez l'Éditeur de Registre.  
  
 **Pour définir la valeur maxConcurrentRequestsPerCPU la valeur pour un pool d’applications dans la section de configuration d’un fichier aspnet.config**  
  
> [!NOTE]  
>  Microsoft .NET Framework 3.5 Service Pack 1 doit être installé pour prendre en charge la définition des valeurs ci-dessous via le fichier de configuration. Vous pouvez télécharger Microsoft .NET Framework 3.5 Service Pack 1 à partir de [Microsoft .NET Framework 3.5 Service Pack 1](http://go.microsoft.com/fwlink/?LinkID=136345) (http://go.microsoft.com/fwlink/?LinkID=136345).  
  
 Ouvrez le fichier aspnet.config du pool d’applications, puis entrez les nouvelles valeurs pour le **maxConcurrentRequestsPerCPU** et **requestQueueLimit** paramètres.  
  
```  
<system.web>  
    <applicationPool maxConcurrentRequestsPerCPU="12" requestQueueLimit="5000"/>  
</system.web>  
```  
  
> [!NOTE]  
>  Cette valeur remplace la valeur spécifiée pour **maxConcurrentRequestsPerCPU** dans le Registre. Le paramètre requestQueueLimit est le même que processModel/requestQueueLimit, sauf que le paramètre dans le fichier aspnet.config remplace le paramètre dans le fichier machine.config.  
  
 Pour plus d’informations sur la configuration de l’utilisation de Thread ASP.NET sur IIS 7.0, consultez [Blog de Thomas Marquardt sur l’utilisation de Thread ASP.NET sur IIS 7.0](http://go.microsoft.com/fwlink/?LinkId=157518) (http://go.microsoft.com/fwlink/?LinkId=157518).  
  
### <a name="manage-the-number-of-concurrently-executing-requests-for-aspnet-4web-applications-that-can-host-isolated-received-locations-back-end-web-services-and-wcf-services-on-iis-75-and-70-running-in-integrated-mode"></a>Gérer le nombre de demandes pour les applications ASP.NET 4Web qui peuvent héberger des emplacements de réception isolés, les services Web principaux et les services WCF sur IIS 7.5 et 7.0 en mode intégré de manière simultanée  
 .NET Framework 4, le paramètre par défaut pour maxConcurrentRequestsPerCPU la valeur est de 5 000, ce qui constitue un très grand nombre et par conséquent permettra beaucoup de demandes asynchrones à s’exécuter simultanément. Pour plus d’informations, consultez [ \<applicationPool\> élément (paramètres Web)](http://go.microsoft.com/fwlink/?LinkID=205339) (http://go.microsoft.com/fwlink/?LinkID=205339).  
  
 En mode IIS 7.5 et IIS 7.0 intégré, une valeur DWORD nommé MaxConcurrentRequestsPerCPU dans HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ASP.NET\4.0.30319.0 détermine le nombre de requêtes simultanées par UC. Par défaut, la clé de Registre n’existe pas et le nombre de demandes par UC est limité à 5000.  
  
 **Pour définir la valeur maxConcurrentRequestsPerCPU la valeur dans le Registre**  
  
> [!WARNING]  
>  Une utilisation incorrecte de l'Éditeur du Registre peut causer des problèmes vous obligeant à réinstaller votre système d'exploitation. Son utilisation est sous votre entière responsabilité. Pour plus d’informations sur la façon de sauvegarder, restaurer et modifier le Registre, consultez l’article 256986 de la Base de connaissances Microsoft [informations du Registre Windows pour les utilisateurs expérimentés](http://go.microsoft.com/fwlink/?LinkId=62729) (http://go.microsoft.com/fwlink/?LinkId=62729).  
  
> [!NOTE]  
>  Ce paramètre est global et ne peut pas être modifié pour les applications ou les pools d’applications individuels.  
  
1.  Cliquez sur **Démarrer**, **Exécuter**, tapez **regedit.exe**, puis cliquez sur **OK** pour démarrer l'Éditeur du Registre.  
  
2.  Accédez à **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ASP.NET\4.0.30319.0**.  
  
3.  Créez la clé en suivant ces étapes :  
  
    1.  Sur le **modifier** menu, cliquez sur **nouveau**, puis cliquez sur **clé**.  
  
    2.  Type **maxConcurrentRequestsPerCPU**, puis appuyez sur **entrée**.  
  
    3.  Sous le **maxConcurrentRequestsPerCPU** clé, créez une entrée DWORD avec la nouvelle valeur pour maxConcurrentRequestsPerCPU la valeur.  
  
    4.  Fermez l'Éditeur de Registre.  
  
 **Pour définir la valeur maxConcurrentRequestsPerCPU la valeur pour un pool d’applications dans la section de configuration d’un fichier aspnet.config**  
  
> [!NOTE]  
>  Microsoft .NET Framework 4 doit être installé pour prendre en charge la définition des valeurs ci-dessous via le fichier de configuration. Vous pouvez télécharger Microsoft .NET Framework 4 à partir de [Microsoft .NET Framework 4 (programme d’installation de Web)](http://go.microsoft.com/fwlink/?LinkID=189318) (http://go.microsoft.com/fwlink/?LinkID=189318).  
  
-   Ouvrez le fichier aspnet.config du pool d’applications, puis entrez les nouvelles valeurs pour le **maxConcurrentRequestsPerCPU** et **requestQueueLimit** paramètres.  
  
     Dans l’exemple suivant, les valeurs sont les valeurs par défaut.  
  
    ```  
    <system.web>  
        <applicationPool maxConcurrentRequestsPerCPU="5000" requestQueueLimit="5000"/>  
    </system.web>  
    ```  
  
> [!NOTE]  
>  Cette valeur remplace la valeur spécifiée pour **maxConcurrentRequestsPerCPU** dans le Registre. Le **requestQueueLimit** paramètre est le même que processModel/requestQueueLimit, sauf que le paramètre dans le fichier aspnet.config remplace le paramètre dans le fichier machine.config.  
  
## <a name="define-clr-hosting-thread-values-for-biztalk-host-instances"></a>Définir les valeurs de thread pour les instances d’hôte BizTalk d’hébergement du CLR  
 Un thread Windows étant l'unité exécutable la plus basique disponible pour un processus Windows, il est important d'en allouer suffisamment au pool de threads .NET associé à une instance d'un hôte BizTalk pour prévenir la pénurie de threads. Pareil cas, il ne sont pas suffisamment de threads disponibles pour effectuer le travail demandé qui affecte négativement les performances. En même temps, veillez à n’allouer plus de threads au pool de threads.NET associé à un hôte qu’il n’est nécessaire. L'allocation d'un nombre trop important de threads au pool de threads .NET associé à un hôte peut favoriser le basculement de contexte. Ce phénomène survient lorsque le noyau Windows bascule à partir de l’exécution d’un thread à un autre thread, ce qui entraîne une baisse des performances. Allocation de threads excessive peut entraîner le basculement de contexte excessifs, susceptible d’affecter les performances globales. Le nombre de threads alloués au pool de threads .NET d’une instance d’hôte BizTalk par défaut dépend de la version du .NET Framework est installée. Le .NET Framework 4 et .NET Framework 3.5 SP1 considérablement augmenté par défaut, ce qui peut entraîner d’allocation de threads excessive sur les ordinateurs BizTalk Server et la contention de verrouillage excessive de la base de données MessageBox.  
  
 À l’aide de la **Panneau de configuration BizTalk**, vous pouvez modifier la valeur par défaut pour le nombre de threads Windows disponibles dans le .NET thread pool associé à une instance d’un hôte BizTalk. Pour plus d’informations sur la façon de modifier les paramètres .NET CLR, consultez [comment modifier les paramètres .NET CLR](http://go.microsoft.com/fwlink/?LinkID=205344) (http://go.microsoft.com/fwlink/?LinkID=205344). Les paramètres de CLR .NET sont par noyau de processeur.  
  
> [!NOTE]  
>  **Threads de travail** sont utilisés pour traiter les éléments de travail en file d’attente et **les threads d’e/s** sont des threads de rappel dédiés associés à un port de terminaison d’e/s pour traiter une demande d’e/s asynchrone terminée.  
  
|Paramètres de Threading|Valeur par défaut|Valeur recommandée|  
|------------------------|-------------------|-----------------------|  
|Threads d’e/s maximales|250|250|  
|Maximum de Threads|25|100 **Important :** valeur supérieure à 100 peut avoir un effet néfaste sur les performances de l’ordinateur SQL Server hébergeant la base de données MessageBox de BizTalk Server. Lorsque ce problème se produit, SQL Server peut rencontrer une situation de blocage. Nous vous recommandons de n’augmente ne pas ce paramètre au-delà de la valeur 100.|  
|Threads d’e/s minimale|25|25|  
|Threads de travail minimale|5|25|  
  
> [!NOTE]  
>  Les valeurs recommandées ne sont pas absolus et devrez peut-être être ajusté en fonction de l’application BizTalk. Modifier un paramètre à la fois, puis mesurer l’impact sur les performances et la stabilité de la plate-forme BizTalk avant d’apporter des modifications supplémentaires.  
  
> [!NOTE]  
>  Ces valeurs sont implicitement multipliées par le nombre de processeurs sur le serveur. Par exemple, si le **MaxWorkerThreads** entrée à une valeur de 100 définiriez efficacement une valeur de 400 sur un serveur de l’UC de 4.  
  
## <a name="disable-biztalk-server-group-level-tracking"></a>Désactiver le suivi de BizTalk Server au niveau du groupe  
 Suivi entraîne des performances de traitement dans BizTalk Server donnée ne doit être écrite dans la base de données MessageBox et ensuite asynchrone vers la base de données des suivis BizTalk. Les considérations suivantes s’appliquent lors de la configuration de suivi dans un environnement BizTalk Server de production :  
  
-   En règle générale, si le suivi n’est pas une exigence, puis désactivez le suivi au niveau du groupe pour réduire la surcharge et augmenter les performances.  
  
     Pour désactiver le suivi au niveau du groupe de BizTalk Server, procédez comme suit :  
  
    1.  Dans le **Console d’Administration de BizTalk Server**, développez **Administration de BizTalk Server**, avec le bouton droit **groupe BizTalk**, puis cliquez sur **paramètres** .  
  
    2.  Dans la boîte de dialogue Panneau de configuration de BizTalk, dans la page de groupe, désactivez le **activer le suivi au niveau du groupe** case à cocher.  
  
    3.  Cliquez sur **OK** pour appliquer les modifications et quitter le panneau de configuration.  
  
-   Utilisez uniquement le corps du message de suivi si nécessaire. Selon le débit des messages et la taille de message, le suivi des corps de message peut provoquer un surcroît de traitement. Alors que le suivi des activités BizTalk a avantages pour l’audit et de débogage, il a également considérables des performances et les implications en matière d’évolutivité. Par conséquent, vous devez suivre uniquement les données qui sont strictement nécessaire pour des raisons de sécurité et de débogage et évite le suivi des informations redondantes.  
  
-   Par défaut, les options de suivi suivantes sont activées pour les orchestrations :  
  
    -   Orchestration début et fin  
  
    -   Envoi et réception de messages  
  
    -   Forme début et fin  
  
     L’option « de début de la forme et de fin » de suivi d’une orchestration entraîne une surcharge significative et ne doit pas être activée dans un environnement de production où un débit élevé est nécessaire. Options de suivi d’orchestration sont accessibles dans la console Administration de BizTalk sur le **suivi** page de la boîte de dialogue Propriétés d’Orchestration.  
  
 Pour plus d’informations sur la configuration de suivi, consultez [configuration de suivi à l’aide de la Console Administration de BizTalk Server](http://go.microsoft.com/fwlink/?LinkId=158021) (http://go.microsoft.com/fwlink/?LinkId=158021).  
  
## <a name="decrease-the-purging-period-for-the-dta-purge-and-archive-job-from-7-days-to-2-days-in-high-throughput-scenarios"></a>Réduisez la période de purge de la tâche d’archivage de 7 jours à 2 jours dans les scénarios de débits élevés et DTA Purge  
 Par défaut, l’intervalle de vidage pour le suivi des données dans BizTalk Server est défini sur 7 jours. Dans un scénario d’un débit élevé, cela peut entraîner une accumulation excessive de données dans la base de données de suivi qui finalement affectera les performances de la MessageBox et à son tour négativement débit de traitement des messages impact.  
  
 Dans les scénarios de débits élevés, réduire les matériels et logiciels purge intervalle à partir de la valeur par défaut de 7 jours à 2 jours. Pour plus d’informations sur la configuration de l’intervalle de vidage, consultez [la configuration de la Purge et archivage](http://go.microsoft.com/fwlink/?LinkID=153814) (http://go.microsoft.com/fwlink/?LinkID=153814) dans l’aide de BizTalk Server 2010.  
  
## <a name="configure-the-temp-path-for-the-biztalk-service-account-to-point-to-a-separate-disk-or-lun"></a>Configurer le chemin d’accès de %temp% % pour le compte de BizTalk Service pointer vers un disque ou un numéro d’unité logique  
 Cela doit être effectuée, car BizTalk Server utilise l’emplacement temporaire de diffuser des fichiers sur le disque lors des opérations de mappage complexe.  
  
## <a name="install-the-latest-service-packs"></a>Installer les derniers service packs  
 Les derniers service packs pour BizTalk Server et le .NET Framework doivent être installés, car ils contiennent les correctifs qui peuvent corriger les problèmes de performances que vous pouvez rencontrer.  
  
## <a name="performance-optimizations-in-the-biztalk-server-documentation"></a>Optimiser les performances dans la documentation de BizTalk Server  
 Appliquer les recommandations suivantes à partir de la documentation de BizTalk Server comme il convient :  
  
-   [Résolution des problèmes de latence de MessageBox](http://go.microsoft.com/fwlink/?LinkId=158019) (http://go.microsoft.com/fwlink/?LinkId=158019)  
  
-   [Identification des goulots d’étranglement de performances](http://go.microsoft.com/fwlink/?LinkID=154238) (http://go.microsoft.com/fwlink/?LinkID=154238)  
  
-   [Des exceptions DBNETLIB](http://go.microsoft.com/fwlink/?LinkID=155308) (http://go.microsoft.com/fwlink/?LinkID=155308)  
  
-   [Éviter l’épuisement du Port TCP/IP](http://go.microsoft.com/fwlink/?LinkID=153240) (http://go.microsoft.com/fwlink/?LinkID=153240)  
  
-   [Définition de la taille de pool de threads de terminaison](http://go.microsoft.com/fwlink/?LinkId=158020) (http://go.microsoft.com/fwlink/?LinkId=158020)  
  
## <a name="see-also"></a>Voir aussi  
 [Optimisation des performances de BizTalk Server](../technical-guides/optimizing-biztalk-server-performance.md)