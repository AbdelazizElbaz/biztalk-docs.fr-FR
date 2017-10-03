---
title: "Étapes de post-installation pour BizTalk Server 2013 et 2013 R2 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c3b47843-9da5-4144-8b84-135494b8ab43
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b86d8c4c1e1a22dad349c2cc8c2be5ca4b206b2c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="post-installation-steps-for-biztalk-server-2013-and-2013-r2"></a>Étapes de post-installation pour BizTalk Server 2013 et 2013 R2
  
##  <a name="BKMK_NamedPipes"></a> Activation du protocole TCP/IP et des canaux nommés  
  
1.  Ouvrez le **Gestionnaire de configuration SQL Server**.  
  
2.  Développez **Configuration du réseau SQL Server** et sélectionnez **Protocoles pour MSSQLSERVER**.  
  
4.  Vérifiez que les options **TCP/IP** et **Canaux nommés** sont activées. Si elles sont activées, passez à l’étape suivante.  
  
     Sinon :  
  
    -   Cliquez avec le bouton droit sur le protocole, puis cliquez sur **Activer**.  
  
    -   Répétez l'opération pour activer l'autre protocole, le cas échéant.  
  
    -   Dans le volet gauche, cliquez sur **Services SQL Server**.  
  
    -   Dans le volet droit, cliquez avec le bouton droit sur **SQL Server (MSSQLSERVER)** et cliquez sur **Arrêter**.  
  
    -   Une fois le service arrêté, cliquez avec le bouton droit sur **SQL Server (MSSQLSERVER)** et cliquez sur **Démarrer**.  
  
    > [!IMPORTANT]
    >  Si vous utilisez [!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)], le service **NS$BAMAlerts** peut être arrêté. Redémarrage du service.  
  
5.  Fermez le **Gestionnaire de configuration**.  
  
##  <a name="BKMK_DTC"></a> Activation de DTC (Distributed Transaction Coordinator) sur le serveur hôte local  
  
1.  Ouvrez Services de composants :  
  
     **[!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)]** : Sélectionnez le bouton Windows et tapez **Services de composants**. Dans la fenêtre des résultats, sélectionnez **Services de composants**.  
  
     **Windows 8.1** : Sélectionnez le bouton Windows et tapez **Outils d’administration**. Dans la fenêtre de recherche, sélectionnez **Paramètres**. Dans la fenêtre des résultats, cliquez sur **Outils d’administration**. Double-cliquez sur **Services de composants**.  
  
     **Windows 7 SP1** : Sélectionnez **Démarrer**. Dans la zone de texte **Rechercher**, tapez **Services de composants** et cliquez dessus pour les ouvrir.  
  
2.  Dans l’arborescence de la console, développez **Services de composants**, **Ordinateurs**, **Poste de travail**, **Distributed Transaction Coordinator**, puis cliquez sur **DTC local**.  
  
3.  Cliquez avec le bouton droit sur **DTC local** et sélectionnez **Propriétés** pour afficher la boîte de dialogue **Propriétés DTC locales**.  
  
4.  Sélectionnez l’onglet **Sécurité**.  
  
5.  Veiller à activer les options suivantes :  
  
    -   **Accès DTC réseau**  
  
    -   **Autoriser les transactions entrantes**  
  
    -   **Autoriser les transactions sortantes**  
  
    -   **Aucune authentification requise**  
  
     Pour obtenir des paramètres supplémentaires qui peuvent être nécessaires, consultez [Résolution des problèmes liés à MSDTC](../core/troubleshooting-problems-with-msdtc.md).  
  
6.  Sélectionnez **OK** pour fermer la boîte de dialogue **Propriétés DTC locales**. Redémarrez le service MSDTC, si vous y êtes invité.  
  
7.  Fermez **Services de composants**.  
  
##  <a name="BKMK_Firewall"></a> Configuration du Pare-feu Windows pour activer DTC  
  
1.  Ouvrez le **Pare-feu Windows** :  
  
     **[!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)]** : appuyez sur le bouton Windows du clavier et tapez **Pare-feu Windows**. Dans la fenêtre des résultats, cliquez sur **Pare-feu Windows**.  
  
     **Windows 8.1**: appuyez sur le bouton Windows et tapez **Pare-feu Windows**. Dans la fenêtre de recherche, cliquez sur **Paramètres**. Dans la fenêtre des résultats, cliquez sur **Pare-feu Windows**.  
  
     **Windows 7 SP1** : cliquez sur **Démarrer**. Dans la zone de texte **Rechercher**, tapez **Pare-feu Windows** et cliquez dessus pour l’ouvrir.  
  
2.  Cliquez sur **Paramètres avancés**, puis sur **Règles de trafic entrant**.  
  
3.  Dans le volet **Règles entrantes**, cliquez avec le bouton droit sur **Distributed Transaction Coordinator** \* (selon le cas), puis cliquez sur **Activer la règle**.  
  
4.  Cliquez sur **Règles sortantes**.  
  
5.  Dans le volet **Règles sortantes**, cliquez avec le bouton droit sur **Distributed Transaction Coordinator** \* (selon le cas), puis cliquez sur **Activer la règle**.  
  
6.  Dans le **Panneau de configuration**, modifiez l’affichage des listes en affichant des icônes, puis double-cliquez sur **Outils d’administration**.  
  
7.  Double-cliquez sur **Services**.  
  
8.  Cliquez avec le bouton droit sur **Application système COM+**, cliquez sur **Redémarrer** et attendez que le service redémarre.  
  
9. Effectuez un clic droit et redémarrez le service **Distributed Transaction Coordinator**.  
  
10. Effectuez un clic droit et redémarrez le service **SQL Server (MSSQLSERVER)**.  
  
11. Fermez la page **Services (local)**, puis la page **Outils d’administration**.  
  
##  <a name="BKMK_SQLAgent"></a> Configuration des travaux de l’Agent SQL  
  
|Travail|Description|Raisons|  
|---------|-----------------|-------------------|  
|**Sauvegarde de BizTalk Server**|Ce travail de l’Agent SQL sauvegarde les bases de données et les fichiers journaux de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Dans le cadre de la configuration de ce travail, vous déterminez divers paramètres tels que la fréquence et l’emplacement de fichier.<br /><br /> Les liens suivants décrivent le travail de l’Agent SQL et ses paramètres :<br /><br /> [Sauvegarde et restauration des bases de données BizTalk Server](http://msdn.microsoft.com/library/aa561125\(v=bts.80\).aspx)<br /><br /> [Configuration du travail de sauvegarde de BizTalk Server](http://msdn.microsoft.com/library/aa546765\(v=bts.80\).aspx)|Ce travail de l’Agent SQL tronque par ailleurs les journaux des transactions, ce qui permet d’améliorer les performances.<br /><br /> Le travail **Sauvegarde de BizTalk Server** ne supprime pas les fichiers de sauvegarde, même les fichiers plus anciens. Pour supprimer les fichiers de sauvegarde, consultez la rubrique [Échec du travail « Sauvegarde de BizTalk Server » suite à l’accumulation de fichiers sur le serveur de base de données Microsoft BizTalk Server](http://support.microsoft.com/kb/982546).|  
|**Purge et archivage DTA**|Ce travail de l’Agent SQL tronque et archive la base de données des suivis [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] (BizTalkDTADb). Dans le cadre de la configuration du travail, vous déterminez les paramètres tels que le délai de conservation des instances terminées et de toutes les données.<br /><br /> Les liens suivants décrivent le travail de l’Agent SQL et ses paramètres :<br /><br /> [Archivage et purge de la base de données de suivi BizTalk](http://msdn.microsoft.com/library/aa560754\(v=bts.80\).aspx)<br /><br /> [Configuration du travail de purge et d’archivage DTA](http://msdn.microsoft.com/library/aa558715\(v=bts.80\).aspx)|Ce travail de l’Agent SQL affecte directement les performances en conservant les événements de l’hôte de suivi et de purge du suivi.<br /><br /> Les rubriques suivantes ont trait aux performances :<br /><br /> [Gestion et dépannage des bases de données BizTalk Server](http://support.microsoft.com/kb/952555)<br /><br /> [Instructions pour le dimensionnement de la base de données de suivi](http://msdn.microsoft.com/library/aa559162\(v=bts.80\).aspx)|  
  
 **Supplément**  
  
-   Lorsque [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est installé, plusieurs travaux de l’Agent SQL sont créés automatiquement, comme décrit dans les liens suivants :  
  
     [Description des travaux de l’Agent SQL Server dans BizTalk Server](http://support.microsoft.com/kb/919776)  
  
     [Structure et travaux de base de données](http://msdn.microsoft.com/library/aa561960\(v=bts.80\).aspx)  
  
##  <a name="BKMK_InstallCU"></a> Installation des mises à jour cumulatives  
 Après avoir installé [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], installez les éventuelles mises à jour cumulatives de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] répertoriées dans Windows Update. L’[article 2555976 de la Base de connaissances](http://support.microsoft.com/kb/2555976) répertorie les Services Pack et les mises à jour cumulatives disponibles.  
  
## <a name="next"></a>Suivant  
[Configuration de BizTalk Server](../install-and-config-guides/configure-biztalk-server.md)
  
## <a name="see-also"></a>Voir aussi  
 [Annexe A : Installation sans assistance](../install-and-config-guides/appendix-a-silent-installation.md) 
 
[Annexe B : Installation de l’adaptateur Microsoft SharePoint](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md)  

[Annexe C : Fichiers CAB redistribuables](../install-and-config-guides/appendix-c-redistributable-cab-files.md)  

[Annexe D : Création du serveur SMTP](../install-and-config-guides/appendix-d-create-the-smtp-server.md)

[Désinstallation et annulation de la configuration de BizTalk Server pour le supprimer](../install-and-config-guides/uninstall-and-unconfigure-biztalk-server-to-remove-it.md)
