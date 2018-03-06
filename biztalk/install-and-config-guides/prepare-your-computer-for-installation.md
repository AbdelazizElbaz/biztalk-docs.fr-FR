---
title: "Préparer votre ordinateur pour l’Installation | Documents Microsoft"
ms.custom: 
ms.date: 03/15/2016
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 53df7a2f-638b-4921-a97f-736760248526
caps.latest.revision: 
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 26c2e732073ccc787cad32984720d7fac422a8cb
ms.sourcegitcommit: 32f380810b90b70e5df7be72a6a14988a747868e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2018
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
  
-   **Windows 8.1, Windows Server 2012 et Windows Server 2012 R2**: cliquez sur le bouton Windows du clavier et tapez **mise à jour Windows**. À partir des résultats de la recherche, cliquez sur **Windows Update**.  
  
 Après avoir installé les mises à jour, vous devrez peut-être redémarrer l'ordinateur.  
  
##  <a name="BKMK_IIS"></a> Activation d’Internet Information Services  
 Microsoft Internet Information Services (IIS) fournit une infrastructure d’application Web pour de nombreuses fonctionnalités de BizTalk Server, y compris :  
  
-   adaptateur HTTP  
  
-   adaptateur SOAP  
  
-   Adaptateur Windows SharePoint Services  
  
-   Chiffrement SSL (Secure Sockets Layer)  
  
-   Portail BAM  
  
#### <a name="install-iis"></a>Installer IIS

Étapes d’installation spécifique, consultez : 

[Installer les services IIS (Windows 8 et Windows Server 2012)](https://docs.microsoft.com/iis/get-started/whats-new-in-iis-8/installing-iis-8-on-windows-server-2012)

[Installer les services IIS (Windows 7 et Windows Vista)](https://docs.microsoft.com/iis/install/installing-iis-7/installing-iis-on-windows-vista-and-windows-7)


Lorsque vous installez IIS, en plus des options par défaut activée, vérifiez également les points suivants :  
  
- **Outils d’administration Web** : Cochez également :  
  
    - Compatibilité avec la gestion IIS 6 :  
  
        - Console de gestion IIS 6  
  
        - Compatibilité avec la métabase IIS et la configuration IIS 6  
  
    - Console de gestion IIS  
  
- **Services World Wide Web** : Développez **Sécurité** et sélectionnez également :  
  
    - Authentification de base  
  
    - Authentification Windows  

Prenez également en considération les points suivants :  
  
- **Fonctionnalités .net framework 3.5**: .NET Framework 4.5 et .NET Framework 3.5 peuvent être utilisé pour développer des applications .net impliquant BizTalk Adapter Pack. En règle générale, **fonctionnalités .NET Framework 4.5** est déjà installé. Si vous utilisez .NET Framework 3.5 pour créer des applications sur cet ordinateur, puis **fonctionnalités .net Framework 3.5** peut également être installé.  
  
- **Message Queuing** : Si vous utilisez l’adaptateur MSMQ, vous pouvez créer un magasin MSMQ local en cochant **Message Queuing**.  
  
- **Serveur SMTP** : Si vous utilisez l’adaptateur SMTP, vous pouvez créer un serveur SMTP local en cochant **Serveur SMTP**.  
  
- **Windows Identity Foundation 3.5**: Windows Identity Foundation (WIF) est requis par l’adaptateur SharePoint lors de l’utilisation de l’option d’installation CSOM. [Annexe b : installer l’adaptateur SharePoint de Microsoft](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md) décrit l’option d’installation CSOM pour l’adaptateur SharePoint.    
  
 
##  <a name="BKMK_XLS"></a> Installation de Microsoft Office Excel  
  
1.  Exécutez le programme d'installation de Microsoft Office.  
  
2.  Dans la page **Type d’installation**, sélectionnez **Installation personnalisée**, puis **Suivant**.  
  
3.  Dans la page **Installation personnalisée**, sélectionnez **Excel**, puis **Suivant**.  
  
4.  Sélectionnez **Installer**.  
  
5.  Dans **Fin de l’installation**, sélectionnez **Terminer**.  
  
 **Supplément**  
  
-   BizTalk Server prend en charge uniquement la version 32 bits de Microsoft Office.  
  
-   Microsoft Office Excel est requis par analyse BAM (Business Activity) dans BizTalk Server. Le classeur BAM Office Excel définit les processus d'entreprise que vous souhaitez analyser. Vous utilisez également le classeur Excel BAM pour définir la manière dont les utilisateurs des activités visualisent les données collectées par l’analyse BAM.  
  
-   Pour charger correctement le fichier BAM.xla dans Excel, installez **Visual Basic pour Applications** sous **Composants partagés d’Office**. Dans le cas contraire, vous risquez de recevoir l’erreur « Ce classeur a perdu son projet VBA, ses contrôles ActiveX et d’autres fonctionnalités liées à la programmabilité ».  
  
##  <a name="BKMK_VS"></a> Installation de Visual Studio  
  
1.  Exécutez l'installation de Visual Studio en tant qu'administrateur.  
  
2.  Acceptez le contrat de licence et cliquez sur **Suivant**.  
  
3.  Dans **Fonctionnalités facultatives à installer**, sélectionnez les options dont vous avez besoin, puis sélectionnez **Installer**. BizTalk Server ne nécessite aucune des fonctionnalités facultatives.  
  
4.  Dans la page **Terminer**, fermez la fenêtre ou cliquez sur **Lancer** pour ouvrir Visual Studio.  
  
 **Supplément**  
  
-   Si vous installez Visual Studio avant d’installer BizTalk Server, puis mettre à niveau vers Visual Studio Team Explorer, vous devrez peut-être réparer votre installation de BizTalk Server à partir de la **le panneau de configuration** / **programmes**  option.  
  
-   Visual Studio installe automatiquement Microsoft SQL Server Express, qui n’est pas utilisé par BizTalk Server. La bonne pratique est de désinstaller Microsoft SQL Server Express.  
  
-   Les outils de développement de BizTalk Server sont basés sur Visual Studio. Au minimum, vous devez installer le composant de Microsoft Visual c#® .NET de Visual Studio avant d’installer BizTalk Server**outils de développement et Kit de développement logiciel**.  
  
-   Visual Studio est *pas* nécessaire si vous installez BizTalk Server sur un ordinateur de production (exécution uniquement), sur lequel aucune application développement ou débogage n’est requis.  
  
-   L’exécution de BizTalk Server requiert .NET Framework 4.5. .NET Framework 3.0 est indispensable si l’adaptateur ou l’intercepteur WCF (Windows Communication Foundation) est installé.  
  
##  <a name="BKMK_SQL"></a> Installation de SQL Server  
 Installation de [SQL Server 2008 R2](http://msdn.microsoft.com/library/bb500395\(v=sql.105\).aspx)  
  
 Installation de [SQL Server 2012](http://msdn.microsoft.com/library/bb500469\(v=sql.110\).aspx)  
  
 Installation de [SQL Server 2014](http://msdn.microsoft.com/library/bb500469\(v=sql.120\).aspx)  
  
 Lorsque vous installez SQL Server, sélectionnez les fonctionnalités suivantes :  
  
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
  
-   BizTalk Server prend en charge tous les classements SQL Server qui respectent la casse et qui ne la respectent pas, à l’exception des classements binaires. Les classements binaires ne sont pas pris en charge.  
  
-   Pour des performances optimales, Microsoft recommande d’utiliser SQL Server Enterprise Edition. Consultez les [éditions SQL Server 2008 R2](http://msdn.microsoft.com/library/cc645993\(v=sql.105\).aspx), les [éditions SQL Server 2012](http://msdn.microsoft.com/library/cc645993\(v=sql.110\).aspx) ou les [éditions SQL Server 2014](http://msdn.microsoft.com/library/cc645993\(v=sql.120\).aspx).  
  
-   Les Service Packs et mises à jour Windows sont pris en charge et doivent être installés.  
  
-   Lorsque BizTalk Server et SQL Server se trouvent sur des ordinateurs distincts, Distributed Transaction Coordinator (MS DTC) gère les transactions entre les ordinateurs. La fonctionnalité AlwaysOn de SQL Server ne prend pas en charge les transactions MSDTC. La fonctionnalité AlwaysOn de SQL Server n’est pas pris en charge.  
  
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
>  Si une version WebSphere MQ spécifique n’est pas répertoriée, comme MQ 5.x, puis il n'est pas pris en charge avec cette version de BizTalk Server.  
  
 **Supplément**  
  
-   Il est recommandé de toujours installer le dernier pack de correctifs WebSphere MQ. Consultez [http://www.ibm.com/support/docview.wss?uid=swg27006037](http://www.ibm.com/support/docview.wss?uid=swg27006037).  
  
-   Si IBM WebSphere MQ est installé sur un ordinateur non-Windows, installez l’**application MQSAgent COM+** (MQSConfigWiz.exe) et **MQSeries Server for Windows** sur le même ordinateur. Si IBM WebSphere MQ est installé sur un ordinateur Windows, l’**application MQSAgent COM+** et le programme **MQSeries Server for Windows** ne sont ni utilisés ni nécessaires.  
  
     **MQSConfigWiz.exe** est inclus dans les fichiers d’installation de BizTalk Server.  
  
     **MQSeries Server pour Windows** n’est pas un programme Microsoft et doit être obtenu avec votre programme IBM WebSphere MQ.  
  
-   L’article [Adaptateur MQSeries](http://technet.microsoft.com/library/aa547973\(v=BTS.80\).aspx) fournit plus d’informations sur l’adaptateur MQSeries, y compris la configuration des différents composants. La page [BizTalk Server : Adaptateurs MQSeries et MQSeries Client (MQSC)](http://social.technet.microsoft.com/wiki/contents/articles/18316.biztalk-server-mqseries-and-mqseries-client-mqsc-adapters.aspx) fournit des détails supplémentaires sur les adaptateurs MQSeries et MQSC.  
  
-   IBM WebSphere n'est pas un produit Microsoft et n'est pas pris en charge par Microsoft. Microsoft ne donne aucune garantie quant à la pertinence de ce programme. Pour plus d'informations sur IBM WebSphere MQ, y compris les instructions de téléchargement, consultez www.ibm.com.  
  
##  <a name="BKMK_BAMAlerts"></a> Alertes BAM  
 Alertes BAM avec SQL Server 2012 et les versions plus récentes utilisent la messagerie de base de données dans SQL Server. Alertes BAM avec SQL Server 2008 R2 et versions antérieures utilisent les Services de Notification SQL. Avant d’installer ou de configurer des alertes BAM, vous devez configurer les Services de Notification ou messagerie de base de données dans SQL Server.  
  
###  <a name="BKMK_DBMail"></a> Alertes BAM utilisant SQL Server 2012/2014  
 Configurez la [messagerie de base de données SQL Server 2012](http://msdn.microsoft.com/library/hh245116\(v=sql.110\).aspx).  
  
 Configurez la [messagerie de base de données SQL Server 2014](http://msdn.microsoft.com/library/hh245116\(v=sql.120\).aspx).  
  
 **Supplément**  
  
-   La fonctionnalité Messagerie de base de données utilise un serveur SMTP pour envoyer les alertes BAM. Serveur SMTP peut être installé localement sur le serveur BizTalk Server ou sur un autre serveur IIS. L’[annexe D : Création du serveur SMTP](../install-and-config-guides/appendix-d-create-the-smtp-server.md) répertorie les étapes de l’installation et de la configuration d’un serveur SMTP.  
  
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
  
-   Services de Notification SQL doit-elle pas être configurée ; installé uniquement sur le serveur BizTalk Server.  
  
##  <a name="BKMK_WIF"></a> Windows Identity Foundation  
  
|||  
|-|-|  
|Windows 8.1, Windows Server 2012 et Windows Server 2012 R2|Windows Identity Foundation est inclus dans le système d’exploitation comme fonctionnalité dans **Activer ou désactiver des fonctionnalités Windows**.|  
|Windows Vista SP1|Téléchargement disponible sur la page [Windows Identity Foundation](http://www.microsoft.com/download/details.aspx?id=17331) LIEN HYPERTEXTE "http://www.microsoft.com/download/details.aspx?id=17331".|  
  
 **Supplément**  
  
-   Windows Identity Foundation (WIF) est requis pour l’adaptateur SharePoint ou SharePoint Online lorsqu’il est utilisé avec SharePoint objet modèle CSOM (Client Side). Plus précisément :  
  
    |Option d’installation|WIF requis|  
    |-------------------------|------------------|  
    |Adaptateur SharePoint avec CSOM|Oui|  
    |SharePoint Online avec CSOM|Oui|  
    |Service Web de SharePoint adaptateur (déconseillée)|non|  
    |Pas de SharePoint|non|  
  
-   [Annexe b : installer l’adaptateur SharePoint de Microsoft](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md) fournit des informations spécifiques sur les options d’installation de SharePoint.  
  
##  <a name="BKMK_WSS"></a> Installation et configuration de Microsoft SharePoint  
 Installation de [SharePoint 2013](http://technet.microsoft.com/library/cc303424.aspx)  
  
 Installation de [SharePoint Online Service](http://technet.microsoft.com/library/jj819267.aspx)  
  
 Installation de [SharePoint Server 2010](http://technet.microsoft.com/library/cc303424\(v=office.14\).aspx)  
  
 Installation de [SharePoint 2007](http://technet.microsoft.com/library/cc303424\(v=office.12\).aspx)  
  
 **Supplément**  
  
-   Si vous installez SharePoint, vous devez le faire avant de poursuivre la configuration requise de BizTalk Server restante.  
  
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
  
-   Dans certains cas de surcharge (comme des clients accédant à SQL Server à partir d'un seul ordinateur), il est possible que le protocole de mémoire partagée pour SQL Server diminue les performances de BizTalk Server. Vous pouvez corriger ce comportement en désactivant le protocole de réseau de la mémoire partagée dans la configuration du réseau SQL Server.  
  
-   ReplaceThisText  
  
##  <a name="BKMK_LocalAdmin"></a> Adhésion au groupe Administrateurs local  
 **Windows Server 2012** : [Windows Server 2012 : l’ajout d’un compte à un groupe d’administrateurs Local](http://social.technet.microsoft.com/wiki/contents/articles/13436.windows-server-2012-how-to-add-an-account-to-a-local-administrator-group.aspx)  
  
 **Windows 8.1** : Pour ouvrir Utilisateurs et groupes locaux sur Windows 8.1, appuyez sur le bouton Windows du clavier et tapez **groupes**. Dans la fenêtre de recherche, cliquez sur **Paramètres**. Dans la fenêtre des résultats, cliquez sur **Modifier les utilisateurs et les groupes locaux**. Cliquez sur **Groupes**, puis double-cliquez sur Administrateurs pour ajouter un compte.  
  
 **Windows 7 SP1** : Cliquez sur Démarrer. Dans la zone de texte **Rechercher**, tapez **Gestion de l’ordinateur** et cliquez dessus pour l’ouvrir. Développez **Utilisateurs et groupes locaux**, cliquez sur **Groupes**, puis double-cliquez sur Administrateurs pour ajouter un compte.  
  
 **Supplément**  
  
-   Vous devez être membre du groupe Administrateurs local pour installer et configurer BizTalk Server.  
  
##  <a name="BKMK_AppLog"></a> Configuration du journal des événements de l’application  
  
1.  Cliquez sur **Observateur d’événements** :  
  
     **Windows Server 2012** : cliquez sur le bouton Windows du clavier et tapez **Observateur d’événements**. Dans la fenêtre des résultats, cliquez sur **Observateur d’événements**.  
  
     **Windows 8.1** : Appuyez sur le bouton Windows du clavier et tapez **Observateur d’événements**. Dans la fenêtre de recherche, cliquez sur **Paramètres**. Dans la fenêtre des résultats, cliquez sur **Afficher les journaux d’événements**.  
  
     **Windows 7 SP1** : Cliquez sur Démarrer. Dans la zone de texte **Rechercher**, tapez **Observateur d’événements**, et cliquez dessus pour l’ouvrir.  
  
2.  Développez **Journaux Windows**, cliquez avec le bouton droit sur **Application**, puis cliquez sur **Propriétés**. Dans **Propriétés du journal** :  
  
    -   Pour déterminer l’espace disponible, comparez les propriétés **Taille du journal** et **Taille maximale du journal**.  
  
    -   Pour fournir plus d’espace, entrez un numéro supérieur dans **Taille maximale du journal**.  
  
    -   Pour activer le remplacement des anciens événements lorsque le journal est plein, sélectionnez **Remplacer les événements si nécessaire**.  
  
    -   Pour effacer les événements du journal, sélectionnez **Effacer le journal**.  
  
3.  Cliquez sur **OK** pour fermer l’**Observateur d’événements**.  
  
 **Supplément**  
  
-   Le programme d'installation de BizTalk Server conserve un enregistrement des événements dans le journal des événements de l'application. Selon les fonctionnalités de BizTalk Server installées, il se peut que la limite d'espace requis dans le journal soit dépassée. Si le journal des événements application suffisamment d’espace lors de l’installation de BizTalk Server, l’installation échoue. Le fait de modifier les paramètres du journal d'événements d'applications permet d'empêcher cet échec.  
  
## <a name="next"></a>Suivant  
 [Choix des fonctionnalités et composants de BizTalk Server](http://msdn.microsoft.com/library/b8c43fcf-9e5c-48ba-830b-13a5177e30f0)  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de l’installation de BizTalk Server 2013 et 2013 R2](http://msdn.microsoft.com/library/8041926c-cfc9-4eaf-9c28-a2c6e8015bc5)   
 [Annexe A : Installation sans assistance](../install-and-config-guides/appendix-a-silent-installation.md)   
 [Annexe B : Installation de l’adaptateur Microsoft SharePoint](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md)   
 [Annexe C : Fichiers CAB redistribuables](../install-and-config-guides/appendix-c-redistributable-cab-files.md)   
 [Annexe D : Création du serveur SMTP](../install-and-config-guides/appendix-d-create-the-smtp-server.md)
