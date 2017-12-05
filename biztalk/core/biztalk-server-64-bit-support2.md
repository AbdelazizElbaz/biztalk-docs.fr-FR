---
title: "vue d’ensemble de la prise en charge 64 bits pour BizTalk Server | Documents Microsoft"
description: prise en charge de 64 bits dans les adaptateurs, les processus, Administration de BizTalk, les outils BAM, assemblys, orchestrations, etc. dans BizTalk Server
ms.custom: 
ms.date: 09/27/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 52ae9037-a7af-48e4-b6a3-bff7600802de
caps.latest.revision: "42"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c67e68c210566a4f0ba42fcfa0e10cd0260fb6b2
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="biztalk-server-64-bit-support"></a>Prise en charge 64 bits pour BizTalk Server
Dans cette rubrique, vous trouverez les réponses à certaines questions fréquemment posées ayant trait à la prise en charge du mode d'exécution 64 bits de Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
## <a name="which-versions-of-64-bit-windows-are-supported"></a>Quelles sont les versions de Windows 64 bits prises en charge ?  
 Toutes les éditions de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] prend en charge l’exécution 32 bits et l’exécution 64 bits native sur les systèmes d’exploitation pris en charge. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]inclut des options de configuration 32 bits et 64 bits. 
 
  [Configurations logicielle et matérielle pour BizTalk Server 2016](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2016.md)  
  
 [Configuration matérielle et logicielle requise pour BizTalk Server 2013 et 2013 R2](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2013-and-2013-r2.md)  
  
## <a name="is-there-an-extra-cost-for-64-bit-support"></a>La prise en charge du mode 64 bits induit-elle des frais supplémentaires ?  
 Non. prise en charge 64 bits est incluse sans frais supplémentaires.  
  
## <a name="is-itanium-based-hardware-supported"></a>Le matériel Itanium est-il pris en charge ?  
 Pour le composant d’exécution, aucune. Pour les bases de données BizTalk, Oui.  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] requiert un matériel UC qui prend en charge AMD64 ou EM64T. Par conséquent, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] n’est pas pris en charge sur Windows exécuté sur des processeurs de 64 bits basé sur Itanium. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]prend en charge en cours d’exécution avec un Itanium et [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]. Toutes les bases de données [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sont donc prises en charge sur des UC Itanium 64 bits.  
  
## <a name="which-biztalk-server-processes-run-in-64-bit-mode"></a>Quels processus BizTalk Server s'exécutent en mode 64 bits ?  
 Les exécutables [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sont hébergés au sein de plusieurs composants d'exécution serveur. Le tableau suivant répertorie les processus [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] qui s'exécutent en mode 64 bits.  
  
|Traiter|prise en charge 32 bits|prise en charge 64 bits|  
|-------------|---------------------|---------------------|  
|Adaptateurs HTTP (IIS)|Oui|Partielle|  
|Instances d'hôte BizTalk|Oui|Oui|  
|Microsoft Enterprise Single Sign-On|Oui|Oui|  
|Portail BAM (IIS)|Oui|Non|  
|SQL Server|Oui|Oui|  
  
##### <a name="http-based-adapters-iis"></a>Adaptateurs HTTP (IIS)  
 Les composants [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], tels que les adaptateurs HTTP et SOAP sont hébergés et exécutés au sein des services IIS. Tous les adaptateurs sont pris en charge dans IIS en mode 32 bits. Certains adaptateurs prennent en charge l'exécution d'IIS en mode 64 bits. Pour obtenir une liste exhaustive des adaptateurs 64 bits, reportez-vous à la liste des adaptateurs proposée plus loin dans cette rubrique.  
  
##### <a name="biztalk-host-instances"></a>Instances d'hôte BizTalk  
 Un hôte BizTalk est un groupe logique de serveurs, chacun appelé « instance d'hôte ». Chaque instance d’hôte est déployé en tant que service NT basé sur BTSNTSvc.exe. Orchestrations et les adaptateurs in-process sont chargés et exécutés dans des instances de l’hôte. Les instances d’hôte peuvent être configurées pour s’exécuter en mode 32 bits ou 64 bits à l’aide de la **32 bits uniquement** case à cocher de la **propriétés de l’hôte** boîte de dialogue dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration.  
  
##### <a name="enterprise-sso"></a>Microsoft Enterprise Single Sign-On  
 Microsoft Enterprise Single Sign-On (SSO) est exécuté dans un service NT (ENTSSO.exe) dédié. Il est 32 bits natif sous [!INCLUDE[btsWinNoVersion](../includes/btswinnoversion-md.md)] 32 bits, et 64 bits natif sous [!INCLUDE[btsWinNoVersion](../includes/btswinnoversion-md.md)] 64 bits.  
  
##### <a name="bam-portal-iis"></a>Portail BAM (IIS)  
 Les composants du portail BAM (Business Activity Monitoring) doivent s'exécuter dans IIS avec ASP.NET 3.5 32 bits. Le portail BAM s'exécute sur un matériel 64 bits en mode WOW. Voir « En cours d’exécution du portail BAM dans un environnement 64 bits » [personnaliser la Configuration du portail BAM](../core/customizing-the-bam-portal-configuration.md).  
  
##### <a name="sql-server"></a>SQL Server  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] communique avec Microsoft [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] par l'intermédiaire de protocoles de transport natifs qui fonctionnent sur les versions 32 et 64 bits de [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]. Par conséquent, les exécutables [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 32 bits et 64 bits peuvent communiquer avec des versions 32 bits ou 64 bits de [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]. Toutes les procédures stockées [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sont prises en charge dans [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] en mode 32 bits et 64 bits.  
  
## <a name="what-about-32-bit64-bit-support-in-non-server-processes"></a>Qu'en est-il de la prise en charge 32/64 bits dans des processus ne s'exécutant pas sur le serveur ?  
 **Microsoft Visual Studio**  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]fichiers exécutables de concepteur sont hébergés au sein de 32 bits [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] IDE. [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]prend en charge le développement de projets 64 bits à l’aide de Microsoft [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)], ce qui peut être déployé dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
 **Microsoft Management Console (MMC)**  
  
 La console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ne s'exécute qu'en tant qu'application MMC 32 bits, même sous [!INCLUDE[btsWinNoVersion](../includes/btswinnoversion-md.md)] 64 bits. Microsoft Enterprise Single Sign-On prend en charge la console MMC en modes 32 et 64 bits.  
  
 **Internet Explorer**  
  
 Le client BAM a besoin d'Internet Explorer 32 bits pour être installé et pour être utilisé sur [!INCLUDE[btsWinNoVersion](../includes/btswinnoversion-md.md)] 64 bits.  
  
## <a name="how-do-i-enable-native-64-bit-execution-of-orchestrations"></a>Comment puis-je activer l'exécution 64 bits native d'orchestrations ?  
 Affectez l’orchestration pour s’exécuter dans une instance d’hôte qui a le **32 bits seulement** ne pas activée. L'instance de l'hôte doit s'exécuter sur un ordinateur sur lequel Windows x64 est installé.  
  
## <a name="can-i-build-net-assemblies-that-run-in-64-bit-orchestrations"></a>Puis-je générer des assemblys .NET qui s'exécutent dans des orchestrations 64 bits ?  
 Oui. Un développeur d'applications [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], peut, à l'aide de [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)] et de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], générer des assemblys qui prennent en charge l'exécution 64 bits. Ces assemblys peuvent être déployés avec des orchestrations et s'exécuter au sein d'instances d'hôte configurées pour l'exécution 64 bits native.  
  
## <a name="will-net-framework-20-compiled-assemblies-jit-compile-properly-in-both-32-bit-and-64-bit"></a>Les assemblys compilés juste-à-temps avec .NET Framework 2.0 s'exécuteront-ils correctement dans les systèmes 32 bits et 64 bits ?  
 Oui. Si l’assembly a été compilé avec le [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)] 2.0 et le **AnyCPU** indicateur, un seul fichier DLL pourra effectuer la compilation JIT correctement dans le CLR 32 bits ou 64 bits.  
  
## <a name="can-i-install-both-32-bit-and-64-bit-components-in-a-single-biztalk-msi-package"></a>Est-ce que je peux installer des composants 32 bits et 64 bits dans un seul package MSI BizTalk ?  
 Oui. Un administrateur peut créer un fichier de package MSI à partir d'une application [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Le fichier MSI peut contenir des fichiers DLL et EXE 32 bits et 64 bits qui ont été ajoutés à l'application BizTalk. Sous Windows 32 bits, seuls les fichiers DLL et EXE 32 bits seront installés. Sous [!INCLUDE[btsWinNoVersion](../includes/btswinnoversion-md.md)] x64, vous pourrez installer des fichiers DLL et EXE 32 et 64 bits.  
  
## <a name="how-do-32-bit-biztalk-server-executables-run-on-windows-x64"></a>Les exécutables 32 bits BizTalk Server fonctionnent-ils dans un environnement Windows x64 ?  
 Windows x64 permet d'exécuter des exécutables 32 bits et 64 bits sur le même ordinateur. Les exécutables 32 bits utilisent le service WOW64 pour émuler un environnement d'exécution 32 bits.  
  
## <a name="will-32-bit-biztalk-server-executables-have-4gb-of-addressable-process-memory-on-windows-x64"></a>Les exécutables 32 bits de BizTalk Server disposeront-ils, sous Windows x64, de 4 Go de mémoire de processus adressable ?  
 Oui. Sur les systèmes [!INCLUDE[btsWinNoVersion](../includes/btswinnoversion-md.md)] x64, les processus 32 bits BTSNTSVC et IIS sont exécutés sous WOW64 et peuvent utiliser la totalité des 4 Go de mémoire virtuelle. Cela représente une amélioration par rapport aux 2 Go de mémoire virtuelle adressable par défaut sous Windows 32 bits.  
  
 Vous pouvez définir le seuil de limitation de la mémoire selon les valeurs de pourcentage (%) disponibles, ou à l'aide d'une valeur absolue. Exemple :  
  
-   Si vous utilisez le pourcentage disponible (de 0 à 100), la valeur d'entrée est un pourcentage de 2048 Mo.  
  
-   Si vous utilisez une valeur absolue, la valeur d'entrée peut être n'importe quelle valeur en Mo jusqu'à 4096 Mo (limite des systèmes 32 bits). Sur les ordinateurs hôtes 64 bits, vous pouvez spécifier une valeur plus élevée jusqu'à la limite théorique de 2 To pour les systèmes 64 bits.  
  
## <a name="which-adapters-are-capable-of-running-in-64-bit-mode"></a>Quels adaptateurs peuvent fonctionner en mode 64 bits ?  
 Par défaut, tous les adaptateurs peuvent s'exécuter en mode 32 bits sous [!INCLUDE[btsWinNoVersion](../includes/btswinnoversion-md.md)] 32 bits et sous WOW64 dans [!INCLUDE[btsWinNoVersion](../includes/btswinnoversion-md.md)] 64 bits. Les adaptateurs suivants peuvent s'exécuter en mode natif 64 bits (avec IIS ou BTSNTSVC comme processus hôte) :  
  
-   Fichier  
  
-   HTTP  
  
-   MSMQ  
  
-   MQSeries  
  
-   SFTP  
  
-   SMTP  
  
-   SOAP  
  
-   WCF  
  
> [!NOTE]
>  L'adaptateur MQSeries prend en charge à la fois les processus 32 bits et 64 bits. Il possède un agent MQSeries Agent qui s'exécute sur IBM WebSphere MQ Server sous Windows. [Préparer votre ordinateur pour l’Installation](../install-and-config-guides/prepare-your-computer-for-installation.md) répertorie les exigences MQ.  
  
> [!NOTE]
>  Si votre [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] applications de se connecter à un ordinateur Windows Server 2003 (par exemple, l’authentification unique, SQL adaptateur, MQSeries, MQSAgent, Oracle et ainsi de suite), puis installez [934016](http://support.microsoft.com/kb/934016) et [934849](http://support.microsoft.com/kb/934849) sur ces serveurs Windows serveurs 2003.  
  
> [!NOTE]
>  L'exécution des adaptateurs FTP et POP3 et du décodeur MIME sur des instances d'hôte 64 bits n'est pas prise en charge.  
  
## <a name="are-persisted-biztalk-orchestrations-dependent-on-32-bit-or-64-bit-runtimes"></a>Les orchestrations BizTalk persistantes dépendent-elles l'exécution 32 bits ou 64 bits ?  
 Non. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]composants d’exécution à l’aide des formats qui sont indépendants des runtimes 32 bits ou 64 bits est conservé. Cela inclut des orchestrations, des messages et des ports. Ce modèle de persistance permet à un administrateur de basculer la configuration hôte entre 32 bits et 64 bits sans créer d'incompatibilités au sein des données [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
## <a name="when-i-upgrade-to-biztalk-server-will-my-biztalk-hosts-run-as-64-bit-by-default"></a>Après une mise à niveau vers BizTalk Server, mes hôtes BizTalk s’exécuteront-ils par défaut en mode 64 bits ?  
 Non. Par défaut, de mises à niveau vers BizTalk Server marquer toutes les instances d’hôte BizTalk en tant que 32 bits uniquement. Un administrateur doit créer de nouvelles instances d'hôte sur des ordinateurs Windows 64 bits et configurer les applications devant les utiliser.  
  
## <a name="can-i-have-a-mixed-biztalk-server-group-that-includes-both-32-bit-and-64-bit-biztalk-runtimes"></a>Puis-je disposer d’un groupe BizTalk Server « mixte » qui inclue des composants d’exécution 32 bits et 64 bits ?  
 Oui.  
  
## <a name="what-languages-are-supported-on-64-bit-runtimes"></a>Quelles langues sont prises en charge dans le mode d'exécution 64 bits ?  
 Toutes les langues sont prises en charge dans les deux modes d'exécution.  
  
## <a name="what-64-bit-sql-server-components-are-required-to-configure-bam-tools"></a>Quels sont les composants SQL Server 64 bits nécessaires à la configuration des outils BAM ?  
 L'Assistant Configuration est un processus 32 bits. Un certain nombre de composants sont donc requis afin de lui permettre de communiquer avec [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 64 bits. Vous devez installer les composants de client [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] afin de permettre la configuration des outils BAM :  
  
-   Composants de connectivité  
  
-   Outils de gestion  
  
-   Composants hérités  
  
## <a name="see-also"></a>Voir aussi  
 [Performances et planification de capacité](../core/performance-and-capacity-planning.md)
