---
title: "Préparer votre ordinateur pour l’Installation | Documents Microsoft"
ms.custom: 
ms.date: 2016-03-15
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 53df7a2f-638b-4921-a97f-736760248526
caps.latest.revision: "32"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a493c1a0ef38e9be5e229ff82f8773211adfe765
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="prepare-your-computer-for-installation"></a>Préparation de votre ordinateur pour l'installation
Cette rubrique présente les étapes nécessaires pour préparer votre ordinateur en installant et en configurant tous les composants logiciels requis, puis en créant des comptes et en définissant les autorisations.  

> [!TIP] 
> Un MVP d’intégration a préparé un guide pas à pas très détaillé pour installer les prérequis et BizTalk Server : [Installation et configuration de BizTalk 2013, partie 1](http://sandroaspbiztalkblog.wordpress.com/2013/05/05/biztalk-2013-installation-and-configuration-important-considerations-before-set-up-the-server-part-1/).  
> 
> Certaines étapes ne sont pas recommandées par Microsoft, telles que la désactivation du contrôle d’accès d’utilisateur ou du Pare-feu Windows. 
  
> [!IMPORTANT]
>  Effectuez ces tâches dans l’ordre indiqué.  
  
##  <a name="BKMK_InstUpdates"></a> Installation des mises à jour Windows  
  
-   **Windows 7** : Cliquez sur Démarrer. Dans la zone de texte **Rechercher**, tapez **Windows Update**.  
  
-   **Windows 8.1, [!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)] et [!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)] R2** : Appuyez sur le bouton Windows du clavier et tapez **Windows Update**. À partir des résultats de la recherche, cliquez sur **Windows Update**.  
  
 Après avoir installé les mises à jour, vous devrez peut-être redémarrer l'ordinateur.  
  
##  <a name="BKMK_IIS"></a> Activation d’Internet Information Services  
 Microsoft Internet Information Services (IIS) offre une infrastructure d'applications Web pour de nombreuses fonctionnalités de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], notamment :  
  
-   adaptateur HTTP  
  
-   adaptateur SOAP  
  
-   Adaptateur Windows SharePoint Services  
  
-   Chiffrement SSL (Secure Sockets Layer)  
  
-   Portail BAM  
  
#### <a name="install-iis-75-on-windows-7-sp1"></a>Installation d'IIS 7.5 sur Windows 7 SP1  
  
1.  Sélectionnez **Démarrer**. Dans la zone de texte **Rechercher**, tapez **Programmes et fonctionnalités** et ouvrez la fonctionnalité.  
  
2.  Sélectionnez **Activer ou désactiver des fonctionnalités Windows**.  
  
3.  Sélectionnez **Internet Information Services** et développez **Internet Information Services**. En plus des options activées par défaut, sélectionnez également ce qui suit :  
  
    -   **Outils d’administration Web** : Cochez également :  
  
        -   Compatibilité avec la gestion IIS 6 :  
  
            -   Console de gestion IIS 6  
  
            -   Compatibilité avec la métabase IIS et la configuration IIS 6  
  
        -   Console de gestion IIS  
  
    -   **Services World Wide Web** : Développez **Sécurité** et sélectionnez également :  
  
        -   Authentification de base  
  
        -   Authentification Windows  
  
4.  Sélectionnez **OK**. Une fois terminé, cliquez sur **Fermer**.  
  
 L’article [http://go.microsoft.com/fwlink/p/?LinkID=257033](http://go.microsoft.com/fwlink/p/?LinkId=257033) présente aussi les étapes permettant d’activer IIS sur Windows 7.  
  
#### <a name="install-iis-80-on-windows-8"></a>Installation d’IIS 8.0 sur Windows 8  
  
1.  Sélectionnez le bouton Windows de votre clavier. Tapez **Programmes et fonctionnalités**, puis sélectionnez **Paramètres**. Dans la fenêtre des résultats, sélectionnez **Programmes et fonctionnalités**.  
  
2.  Sélectionnez **Activer ou désactiver des fonctionnalités Windows**.  
  
3.  Sélectionnez **Internet Information Services** et développez **Internet Information Services**. En plus des options activées par défaut, sélectionnez également :  
  
    -   **Outils d’administration Web** : Cochez également :  
  
        -   Compatibilité avec la gestion IIS 6 :  
  
            -   Console de gestion IIS 6  
  
            -   Compatibilité avec la métabase IIS et la configuration IIS 6  
  
        -   Console de gestion IIS  
  
    -   **Services World Wide Web** : Développez **Sécurité** et cochez également :  
  
        -   Authentification de base  
  
        -   Authentification Windows  
  
4.  Cliquez sur **OK**. Une fois terminé, cliquez sur **Fermer**.  
  
 L’article [http://go.microsoft.com/fwlink/p/?LinkID=291297](http://go.microsoft.com/fwlink/p/?LinkID=291297) présente aussi les étapes permettant d’activer IIS sur Windows 8.  
  
#### <a name="install-iis-80-on-windows-server-2012"></a>Installation d'IIS 8.0 sur Windows Server 2012  
  
1.  Ouvrez le **Gestionnaire de serveur**, puis cliquez sur **Tableau de bord** dans le volet gauche.  
  
2.  Cliquez sur **Ajouter des rôles et fonctionnalités**. Vous pouvez aussi ouvrir **Ajouter des rôles et fonctionnalités** à partir du menu **Gérer** en haut à droite.  
  
3.  Dans la fenêtre **Avant de commencer**, cliquez sur **Suivant**.  
  
4.  Dans la fenêtre **Type d’installation**, cliquez sur **Installation basée sur un rôle ou une fonctionnalité**, puis sur **Suivant**.  
  
5.  Dans la fenêtre **Sélection du serveur**, cliquez sur **Sélectionner un serveur du pool de serveurs**, cliquez sur le serveur voulu, puis cliquez sur **Suivant**.  
  
     La fenêtre **Sélection du serveur** répertorie les serveurs qui ont été ajoutés avec **Ajouter un serveur** dans le **Gestionnaire de serveur**. Le serveur local est sélectionné par défaut. [Ajouter des serveurs au Gestionnaire de serveur](http://go.microsoft.com/fwlink/p/?LinkID=241353) répertorie les étapes permettant d’utiliser **Ajouter un serveur** sur [!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)].  
  
6.  Dans la fenêtre **Rôles du serveur**, cliquez sur **Serveur Web (IIS)**. Si vous y êtes invité, cliquez sur **Ajouter des fonctionnalités**, puis cliquez sur **Suivant**.  
  
7.  Dans la fenêtre **Fonctionnalités**, laissez les options par défaut activées et tenez également compte de ce qui suit :  
  
     **Fonctionnalités de .NET Framework 3.5** : [!INCLUDE[dotnet45](../includes/dotnet45-md.md)] et [!INCLUDE[btsDotNetFramework3.5](../includes/btsdotnetframework3-5-md.md)] peuvent être utilisés pour développer des applications .NET impliquant le [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]. En règle générale, les **fonctionnalités de [!INCLUDE[dotnet45](../includes/dotnet45-md.md)]** sont déjà installées. Si vous envisagez d’utiliser [!INCLUDE[btsDotNetFramework3.5](../includes/btsdotnetframework3-5-md.md)] pour créer des applications sur cet ordinateur, vous pouvez également installer les **fonctionnalités de .NET Framework 3.5**.  
  
     **Message Queuing** : Si vous utilisez l’adaptateur MSMQ, vous pouvez créer un magasin MSMQ local en cochant **Message Queuing**.  
  
     **Serveur SMTP** : Si vous utilisez l’adaptateur SMTP, vous pouvez créer un serveur SMTP local en cochant **Serveur SMTP**.  
  
     **Windows Identity Foundation (WIF) 3.5** : Windows Identity Foundation (WIF) est requis par l’adaptateur [!INCLUDE[btsWinSharePointSvcsNoVersion](../includes/btswinsharepointsvcsnoversion-md.md)] lors de l’utilisation de l’option d’installation CSOM. L’[annexe B : Installation de l’adaptateur Microsoft SharePoint](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md) décrit l’option d’installation CSOM pour l’adaptateur [!INCLUDE[btsWinSharePointSvcsNoVersion](../includes/btswinsharepointsvcsnoversion-md.md)].  
  
     Cliquez sur **Suivant**.  
  
8.  Dans la fenêtre **Rôle Serveur Web (IIS)**, cliquez sur **Suivant**.  
  
9. Dans la fenêtre **Services de rôle** (sous **Rôle Serveur Web (IIS)**), cliquez sur les options suivantes :  
  
     **Sécurité** : Outre les options par défaut, cliquez également sur ce qui suit :  
  
    -   Authentification de base  
  
    -   Authentification Windows  
  
     **Développement d’applications** : Les options par défaut sont suffisantes pour [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Si vous hébergez d'autres applications IIS basées sur cet ordinateur, sélectionnez les rôles nécessaires.  
  
     **Outils de gestion** : Outre les options par défaut, cliquez également sur :  
  
    -   Console de gestion IIS  
  
    -   Compatibilité avec la gestion IIS 6 :  
  
        -   Compatibilité avec la métabase IIS 6  
  
        -   Console de gestion IIS 6  
  
     Cliquez sur **Suivant**.  
  
10. Dans la fenêtre **Confirmation**, cliquez sur **Installer**. Une fois terminé, cliquez sur **Fermer**.  
  
 L’article [http://go.microsoft.com/fwlink/p/?LinkID=291297](http://go.microsoft.com/fwlink/p/?LinkID=291297) présente aussi les étapes permettant d’activer IIS sur [!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)].  
  
##  <a name="BKMK_XLS"></a> Installation de Microsoft Office Excel  
  
1.  Exécutez le programme d'installation de Microsoft Office.  
  
2.  Dans la page **Type d’installation**, sélectionnez **Installation personnalisée**, puis **Suivant**.  
  
3.  Dans la page **Installation personnalisée**, sélectionnez **Excel**, puis **Suivant**.  
  
4.  Sélectionnez **Installer**.  
  
5.  Dans **Fin de l’installation**, sélectionnez **Terminer**.  
  
 **Supplément**  
  
-   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] prend uniquement en charge la version 32 bits de Microsoft Office.  
  
-   Microsoft Office Excel est requis par BAM (Business Activity Monitoring) dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Le classeur BAM Office Excel définit les processus d'entreprise que vous souhaitez analyser. Vous utilisez également le classeur Excel BAM pour définir la manière dont les utilisateurs des activités visualisent les données collectées par l’analyse BAM.  
  
-   Pour charger correctement le fichier BAM.xla dans Excel, installez **Visual Basic pour Applications** sous **Composants partagés d’Office**. Dans le cas contraire, vous risquez de recevoir l’erreur « Ce classeur a perdu son projet VBA, ses contrôles ActiveX et d’autres fonctionnalités liées à la programmabilité ».  
  
##  <a name="BKMK_VS"></a> Installation de Visual Studio  
  
1.  Exécutez l'installation de Visual Studio en tant qu'administrateur.  
  
2.  Acceptez le contrat de licence et cliquez sur **Suivant**.  
  
3.  Dans **Fonctionnalités facultatives à installer**, sélectionnez les options dont vous avez besoin, puis sélectionnez **Installer**. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ne nécessite aucune des fonctionnalités facultatives.  
  
4.  Dans la page **Terminer**, fermez la fenêtre ou cliquez sur **Lancer** pour ouvrir Visual Studio.  
  
 **Supplément**  
  
-   Si vous installez Visual Studio avant d’installer [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], puis effectuez une mise à niveau vers Visual Studio Team Explorer, vous devrez peut-être réparer votre installation [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] à partir de l’option **Panneau de configuration** / **Programmes**.  
  
-   Visual Studio installe automatiquement Microsoft SQL Server Express, qui n'est pas utilisé par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. La bonne pratique est de désinstaller Microsoft SQL Server Express.  
  
-   Les outils de développement de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sont en effet basés sur Visual Studio. Au minimum, vous devez installer le composant Microsoft Visual C#® .NET de Visual Studio avant d’installer le composant **Outils et kit de développement [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]**.  
  
-   Visual Studio n’est *pas* nécessaire si vous installez [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sur un ordinateur de production (d’exécution uniquement) sur lequel aucun débogage ni développement d’application n’est requis.  
  
-   Le composant d'exécution [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] exige [!INCLUDE[dotnet45](../includes/dotnet45-md.md)]. .NET Framework 3.0 est indispensable si l’adaptateur ou l’intercepteur WCF (Windows Communication Foundation) est installé.  
  
##  <a name="BKMK_SQL"></a> Installation de SQL Server  
 Installation de [SQL Server 2008 R2](http://msdn.microsoft.com/library/bb500395\(v=sql.105\).aspx)  
  
 Installation de [SQL Server 2012](http://msdn.microsoft.com/library/bb500469\(v=sql.110\).aspx)  
  
 Installation de [SQL Server 2014](http://msdn.microsoft.com/library/bb500469\(v=sql.120\).aspx)  
  
 Lors de l'installation de [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)], sélectionnez les fonctionnalités suivantes :  
  
-   Services Moteur de base de données  
  
    -   Réplication SQL Server  
  
    -   Recherche en texte intégral  
  
-   Analysis Services  
  
-   Reporting Services  
  
-   Fonctionnalités partagées  
  
    -   SQL Server Data Tools (SQL Server 2014/SQL Server 2012) ou Business Intelligence Development Studio (SQL Server 2008 R2)  
  
         [Téléchargez SQL Server 2014 Data Tools](http://www.microsoft.com/download/details.aspx?id=42313)  
  
    -   Connectivité des outils clients  
  
    -   Integration Services  
  
    -   Outils de gestion - Base  
  
        -   Outils de gestion - Complet  
  
 **Supplément**  
  
-   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] prend en charge tous les classements SQL Server qui respectent la casse et qui ne la respectent pas, à l'exception des classements binaires. Les classements binaires ne sont pas pris en charge.  
  
-   Pour des performances optimales, Microsoft recommande d’utiliser SQL Server Enterprise Edition. Consultez les [éditions SQL Server 2008 R2](http://msdn.microsoft.com/library/cc645993\(v=sql.105\).aspx), les [éditions SQL Server 2012](http://msdn.microsoft.com/library/cc645993\(v=sql.110\).aspx) ou les [éditions SQL Server 2014](http://msdn.microsoft.com/library/cc645993\(v=sql.120\).aspx).  
  
-   Les Service Packs et mises à jour Windows sont pris en charge et doivent être installés.  
  
-   Lorsque [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] sont installés sur des ordinateurs distincts, MS DTC (Microsoft Distributed Transaction Coordinator) gère les transactions entre les ordinateurs. La fonctionnalité [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] AlwaysOn ne prend pas en charge les transactions MSDTC. La fonctionnalité AlwaysOn [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] n'est pas prise en charge.  
  
##  <a name="BKMK_MQSeries"></a> Installation des composants requis pour MQSeries  
 **Adaptateur MQSeries** : Installé automatiquement avec l’installation de BizTalk Server.  
  
 **Adaptateur MQSeries Client (MQSC)** :  
  
1.  Exécuter l'installation de HIS (Host Integration Server)  
  
2.  Dans l’installation des composants, développez **Adaptateurs BizTalk**.  
  
3.  Sélectionnez **Adaptateur BizTalk pour WebSphere MQ (basé sur le client)**.  
  
 **Versions prises en charge d’IBM WebSphere MQ** :  
  
-   IBM WebSphere MQ 6.0.2.12 et versions ultérieures  
  
-   IBM WebSphere MQ 7.0.1.9 et versions ultérieures  
  
-   IBM WebSphere MQ 7.1.0.5 et versions ultérieures  
  
-   IBM WebSphere MQ 7.5.0.3 et versions ultérieures  
  
-   IBM WebSphere MQ 8 (limité à l’exécution, aucune API d’administration)  
  
     La prise en charge de MQ version 8 est incluse avec [Host Integration Server CU3](https://support.microsoft.com/kb/3019572).  
  
> [!NOTE]
>  Si une version WebSphere MQ spécifique n'est pas répertoriée, comme MQ 5.x, c'est qu'elle n'est pas prise en charge par cette version de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
 **Supplément**  
  
-   Il est recommandé de toujours installer le dernier pack de correctifs WebSphere MQ. Consultez [http://www.ibm.com/support/docview.wss?uid=swg27006037](http://www.ibm.com/support/docview.wss?uid=swg27006037).  
  
-   Si IBM WebSphere MQ est installé sur un ordinateur non-Windows, installez l’**application MQSAgent COM+** (MQSConfigWiz.exe) et **MQSeries Server for Windows** sur le même ordinateur. Si IBM WebSphere MQ est installé sur un ordinateur Windows, l’**application MQSAgent COM+** et le programme **MQSeries Server for Windows** ne sont ni utilisés ni nécessaires.  
  
     **MQSConfigWiz.exe** est inclus dans les fichiers d’installation de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
     **MQSeries Server pour Windows** n’est pas un programme Microsoft et doit être obtenu avec votre programme IBM WebSphere MQ.  
  
-   L’article [Adaptateur MQSeries](http://technet.microsoft.com/library/aa547973\(v=BTS.80\).aspx) fournit plus d’informations sur l’adaptateur MQSeries, y compris la configuration des différents composants. La page [BizTalk Server : Adaptateurs MQSeries et MQSeries Client (MQSC)](http://social.technet.microsoft.com/wiki/contents/articles/18316.biztalk-server-mqseries-and-mqseries-client-mqsc-adapters.aspx) fournit des détails supplémentaires sur les adaptateurs MQSeries et MQSC.  
  
-   IBM WebSphere n'est pas un produit Microsoft et n'est pas pris en charge par Microsoft. Microsoft ne donne aucune garantie quant à la pertinence de ce programme. Pour plus d'informations sur IBM WebSphere MQ, y compris les instructions de téléchargement, consultez www.ibm.com.  
  
##  <a name="BKMK_BAMAlerts"></a> Alertes BAM  
 Les alertes BAM avec [!INCLUDE[sqlserver2014](../includes/sqlserver2014-md.md)] ou [!INCLUDE[sqlserver2012](../includes/sqlserver2012-md.md)] utilisent la fonctionnalité Messagerie de base de données dans [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]. Alertes BAM avec [!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)] utilise SQL Notification Services. Avant d'installer ou de configurer les alertes BAM, vous devez configurer les services de notification Services ou la messagerie de base de données dans [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)].  
  
###  <a name="BKMK_DBMail"></a> Alertes BAM utilisant SQL Server 2012/2014  
 Configurez la [messagerie de base de données SQL Server 2012](http://msdn.microsoft.com/library/hh245116\(v=sql.110\).aspx).  
  
 Configurez la [messagerie de base de données SQL Server 2014](http://msdn.microsoft.com/library/hh245116\(v=sql.120\).aspx).  
  
 **Supplément**  
  
-   La fonctionnalité Messagerie de base de données utilise un serveur SMTP pour envoyer les alertes BAM. Le serveur SMTP peut être installé localement sur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou un autre serveur IIS. L’[annexe D : Création du serveur SMTP](../install-and-config-guides/appendix-d-create-the-smtp-server.md) répertorie les étapes de l’installation et de la configuration d’un serveur SMTP.  
  
###  <a name="BKMK_SSNS"></a> Alertes BAM utilisant SQL Server 2008 R2 – Installation de SQL Server 2005 Notification Services  
  
1.  Consultez [Feature Pack pour Microsoft SQL Server 2005 SP4](http://go.microsoft.com/fwlink/p/?LinkId=286285).  
  
2.  Téléchargez et installez le package de plate-forme approprié pour les composants suivants :  
  
     **Microsoft SQL Server Native Client**  
  
    -   LIEN HYPERTEXTE "http://download.microsoft.com/download/3/1/6/316FADB2-E703-4351-8E9C-E0B36D9D697E/sqlncli.msi" Package X86 (sqlncli.msi)  
  
    -   LIEN HYPERTEXTE "http://download.microsoft.com/download/3/1/6/316FADB2-E703-4351-8E9C-E0B36D9D697E/sqlncli_x64.msi" Package X64 (sqlncli_x64.msi)  
  
     **Collection d’objets de gestion de Microsoft SQL Server 2005**  
  
    -   LIEN HYPERTEXTE "http://download.microsoft.com/download/3/1/6/316FADB2-E703-4351-8E9C-E0B36D9D697E/SQLServer2005_XMO.msi" Package X86 (SQLServer2005_XMO.msi)  
  
    -   LIEN HYPERTEXTE "http://download.microsoft.com/download/3/1/6/316FADB2-E703-4351-8E9C-E0B36D9D697E/SQLServer2005_XMO_x64.msi" Package X64 (SQLServer2005_XMO_x64.msi)  
  
     **Composants clients Notification Services de Microsoft SQL Server 2005**  
  
    -   LIEN HYPERTEXTE "http://download.microsoft.com/download/3/1/6/316FADB2-E703-4351-8E9C-E0B36D9D697E/SQLServer2005_NS.msi" Package X86 (SQLServer2005_NS.msi)  
  
    -   LIEN HYPERTEXTE "http://download.microsoft.com/download/3/1/6/316FADB2-E703-4351-8E9C-E0B36D9D697E/SQLServer2005_NS_x64.msi" Package X64 (SQLServer2005_NS_x64.msi)  
  
 **Supplément**  
  
-   Il n'est pas nécessaire de configurer SQL Notification Services ; installez-le seulement sur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
##  <a name="BKMK_WIF"></a> Windows Identity Foundation  
  
|||  
|-|-|  
|[!INCLUDE[btsWinNoVersion](../includes/btswinnoversion-md.md)] 8.1, [!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)] et [!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)] R2|Windows Identity Foundation est inclus dans le système d’exploitation comme fonctionnalité dans **Activer ou désactiver des fonctionnalités Windows**.|  
|[!INCLUDE[btsWinVista](../includes/btswinvista-md.md)] SP1|Téléchargement disponible sur la page [Windows Identity Foundation](http://www.microsoft.com/download/details.aspx?id=17331) LIEN HYPERTEXTE "http://www.microsoft.com/download/details.aspx?id=17331".|  
  
 **Supplément**  
  
-   Windows Identity Foundation (WIF) est requis pour l’adaptateur [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] ou SharePoint Online lorsque celui-ci est utilisé avec le modèle CSOM (Client Side Object Model) [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)]. Plus précisément :  
  
    |Option d’installation|WIF requis|  
    |-------------------------|------------------|  
    |Adaptateur [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] avec CSOM|Oui|  
    |SharePoint Online avec CSOM|Oui|  
    |Service Web Adaptateur [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] (supprimé)|Non|  
    |Pas de SharePoint|Non|  
  
-   L’[annexe B : Installation de l’adaptateur Microsoft SharePoint](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md) fournit des informations spécifiques sur les options d’installation de [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)].  
  
##  <a name="BKMK_WSS"></a> Installation et configuration de Microsoft SharePoint  
 Installation de [SharePoint 2013](http://technet.microsoft.com/library/cc303424.aspx)  
  
 Installation de [SharePoint Online Service](http://technet.microsoft.com/library/jj819267.aspx)  
  
 Installation de [SharePoint Server 2010](http://technet.microsoft.com/library/cc303424\(v=office.14\).aspx)  
  
 Installation de [SharePoint 2007](http://technet.microsoft.com/library/cc303424\(v=office.12\).aspx)  
  
 **Supplément**  
  
-   Si vous installez SharePoint, vous devez le faire avant de continuer avec le reste de la configuration requise de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
-   L’installation et la configuration de SharePoint s’effectuent comme suit :  
  
    -   installation de SharePoint ;  
  
    -   configuration de SharePoint ;  
  
    -   extension du site Web par défaut en tant que serveur virtuel.  
  
-   L’[annexe B : Installation de l’adaptateur Microsoft SharePoint](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md) décrit les options d’installation de l’adaptateur SharePoint pour BizTalk Server.  
  
-   Lorsque vous utilisez l’adaptateur SharePoint, il est recommandé d’installer la nouvelle option CSOM à la place du service web SharePoint Service, qui est décrite dans l’[annexe B : Installation de l’adaptateur Microsoft SharePoint](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md).  
  
##  <a name="BKMK_SharedMem"></a> Désactivation du protocole de mémoire partagée  
  
1.  Ouvrez le **Gestionnaire de configuration SQL Server**.  
  
2.  Dans le **Gestionnaire de configuration SQL Server**, développez **Configuration du réseau SQL Server**, puis sélectionnez **Protocoles pour MSSQLSERVER**.  
  
3.  Cliquez avec le bouton droit sur **Mémoire partagée**, puis sélectionnez **Désactiver**.  
  
4.  Sélectionnez **Services SQL Server**, cliquez avec le bouton droit sur **SQL Server (MSSQLSERVER)**, puis sélectionnez **Arrêter**. Une fois le service arrêté, cliquez de nouveau avec le bouton droit sur **SQL Server (MSSQLSERVER)**, puis sélectionnez **Démarrer**.  
  
5.  Fermez le **Gestionnaire de configuration SQL Server**.  
  
 **Supplément**  
  
-   Sous certaines conditions de surcharge (telles que l’accès à un serveur SQL Server par des clients à partir du même ordinateur), le protocole de mémoire partagée du serveur SQL Server risque de réduire les performances de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Vous pouvez corriger ce comportement en désactivant le protocole de réseau de la mémoire partagée dans la configuration du réseau SQL Server.  
  
-   ReplaceThisText  
  
##  <a name="BKMK_LocalAdmin"></a> Adhésion au groupe Administrateurs local  
 **[!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)]** : [Windows Server 2012 : Guide pratique pour ajouter un compte dans un groupe Administrateurs local](http://social.technet.microsoft.com/wiki/contents/articles/13436.windows-server-2012-how-to-add-an-account-to-a-local-administrator-group.aspx)  
  
 **Windows 8.1** : Pour ouvrir Utilisateurs et groupes locaux sur Windows 8.1, appuyez sur le bouton Windows du clavier et tapez **groupes**. Dans la fenêtre de recherche, cliquez sur **Paramètres**. Dans la fenêtre des résultats, cliquez sur **Modifier les utilisateurs et les groupes locaux**. Cliquez sur **Groupes**, puis double-cliquez sur Administrateurs pour ajouter un compte.  
  
 **Windows 7 SP1** : Cliquez sur Démarrer. Dans la zone de texte **Rechercher**, tapez **Gestion de l’ordinateur** et cliquez dessus pour l’ouvrir. Développez **Utilisateurs et groupes locaux**, cliquez sur **Groupes**, puis double-cliquez sur Administrateurs pour ajouter un compte.  
  
 **Supplément**  
  
-   Vous devez être connecté en tant que membre du groupe Administrateurs pour installer et configurer [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
##  <a name="BKMK_AppLog"></a> Configuration du journal des événements de l’application  
  
1.  Cliquez sur **Observateur d’événements** :  
  
     **[!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)]** : Appuyez sur le bouton Windows du clavier et tapez **Observateur d’événements**. Dans la fenêtre des résultats, cliquez sur **Observateur d’événements**.  
  
     **Windows 8.1** : Appuyez sur le bouton Windows du clavier et tapez **Observateur d’événements**. Dans la fenêtre de recherche, cliquez sur **Paramètres**. Dans la fenêtre des résultats, cliquez sur **Afficher les journaux d’événements**.  
  
     **Windows 7 SP1** : Cliquez sur Démarrer. Dans la zone de texte **Rechercher**, tapez **Observateur d’événements**, et cliquez dessus pour l’ouvrir.  
  
2.  Développez **Journaux Windows**, cliquez avec le bouton droit sur **Application**, puis cliquez sur **Propriétés**. Dans **Propriétés du journal** :  
  
    -   Pour déterminer l’espace disponible, comparez les propriétés **Taille du journal** et **Taille maximale du journal**.  
  
    -   Pour fournir plus d’espace, entrez un numéro supérieur dans **Taille maximale du journal**.  
  
    -   Pour activer le remplacement des anciens événements lorsque le journal est plein, sélectionnez **Remplacer les événements si nécessaire**.  
  
    -   Pour effacer les événements du journal, sélectionnez **Effacer le journal**.  
  
3.  Cliquez sur **OK** pour fermer l’**Observateur d’événements**.  
  
 **Supplément**  
  
-   Le programme d’installation de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] conserve un enregistrement des événements dans le journal des événements de l’application. Selon les fonctionnalités de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installées, il se peut que la limite d’espace requis dans le journal soit dépassée. L'installation échoue si le journal des événements de l'application ne dispose plus de suffisamment d'espace lors de l'installation de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Le fait de modifier les paramètres du journal d'événements d'applications permet d'empêcher cet échec.  
  
## <a name="next"></a>Suivant  
 [Choix des fonctionnalités et composants de BizTalk Server](http://msdn.microsoft.com/library/b8c43fcf-9e5c-48ba-830b-13a5177e30f0)  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de l’installation de BizTalk Server 2013 et 2013 R2](http://msdn.microsoft.com/library/8041926c-cfc9-4eaf-9c28-a2c6e8015bc5)   
 [Annexe A : Installation sans assistance](../install-and-config-guides/appendix-a-silent-installation.md)   
 [Annexe B : Installation de l’adaptateur Microsoft SharePoint](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md)   
 [Annexe C : Fichiers CAB redistribuables](../install-and-config-guides/appendix-c-redistributable-cab-files.md)   
 [Annexe D : Création du serveur SMTP](../install-and-config-guides/appendix-d-create-the-smtp-server.md)
