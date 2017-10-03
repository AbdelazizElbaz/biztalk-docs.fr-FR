---
title: "Résolution des problèmes d’analyse BAM | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e63299a8-5c74-4337-ba20-3213e0c6ea1f
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d47932ffd9f7843d0b3d95073ca54bce987b8f75
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshooting-bam"></a>Résolution des problèmes d’analyse BAM
Cette rubrique fournit des informations permettant de faciliter la résolution des problèmes que vous pouvez rencontrer lors de l'utilisation de l'analyse BAM (Business Activity Monitoring).  
  
## <a name="bam-deployment-failed"></a>Échec du déploiement de l'analyse BAM  
 Si vous tentez de déployer une définition BAM qui inclut une agrégation RTA lorsque SQL Server Analysis Services n'est pas disponible, la commande Bm.exe affiche le message suivant :  
  
 Erreur : Échec du déploiement de l’analyse BAM. Impossible d'établir une connexion. Vérifiez que le serveur fonctionne. Aucune connexion n’a pu être établie, car l’ordinateur cible l’a activement refusée  *\<adresse IP >*.  
  
 Cette erreur se produit car SQL Server Analysis Services doit avoir été installé et configuré, et doit être en cours d'exécution afin de déployer une définition BAM qui inclut une valeur RTA.  
  
## <a name="cannot-refresh-the-live-data-workbook"></a>Impossible d'actualiser le classeur de données actives  
 Lorsque vous tentez d'actualiser les données d'un classeur de données actives, Microsoft Office Excel risque d'afficher l'erreur suivante :  
  
 `XML for Analysis parser: The CurrentCatalog XML/A property was not specified.`  
  
 Cette erreur se produit car le complément BAM n'a pas été ajouté à Excel.  
  
#### <a name="to-add-the-bam-add-in-to-excel"></a>Pour ajouter le complément BAM à Excel  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft Office**, puis cliquez sur **Microsoft Office Excel**.  
  
2.  Cliquez sur le **bouton Microsoft Office**, puis cliquez sur **Options Excel**.  
  
3.  Dans le **Options Excel** boîte de dialogue, cliquez sur **compléments**.  
  
4.  Dans le **compléments** volet, cliquez sur **accédez**.  
  
5.  Dans le **compléments** boîte de dialogue, sélectionnez le **Business Activity Monitoring** case à cocher, puis cliquez sur **OK**.  
  
     ![Ajouter &#45; boîte de dialogue complémentaires](../core/media/addins.gif "AddIns")  
  
## <a name="errorobject-library-invalid-or-contains-references-to-object-definitions-that-could-not-be-found-with-bam-excel-add-in-in-office"></a>Erreur : « Bibliothèque d’objets incorrecte ou contenant des références à des définitions d’objets introuvables » avec le complément BAM pour Excel dans Office  
 Vous pouvez recevoir cette erreur lorsque vous tentez d’utiliser le complément BAM pour Excel après la mise à niveau de Microsoft Excel.  
  
 **Résolution :** étant donné que le complément BAM utilise des contrôles ActiveX, vous devez supprimer tous les fichiers .exd mis en cache dans les répertoires suivants :  
  
-   C:\Documents and Settings\\< nom d’utilisateur\>\Application Data\Microsoft\Forms  
  
-   C:\Documents and Settings\\< nom d’utilisateur\>\AppData\Local\Temp\VBE  
  
## <a name="bam-portal-cannot-connect"></a>Le portail BAM ne parvient pas à se connecter  
 Dans [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] ou [!INCLUDE[btsWinVista](../includes/btswinvista-md.md)], vous devez exécuter le portail BAM en tant qu'administrateur.  
  
#### <a name="to-run-the-bam-portal-on-windows-server-2008-r2-or-windows-7"></a>Pour exécuter le portail BAM sur Windows Server 2008 R2 ou Windows 7  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, avec le bouton droit **Internet Explorer**, puis cliquez sur **exécuter en tant qu’administrateur**.  
  
2.  Dans le **contrôle de compte d’utilisateur** boîte de dialogue, cliquez sur **continuer**.  
  
3.  Dans la barre d’adresses Internet Explorer, tapez `http://<server>/BAM`, où  *\<server >* est le nom de l’ordinateur qui exécute le portail BAM.  
  
## <a name="bam-portal-does-not-work-if-invalid-users-are-granted-permissions"></a>Le portail BAM ne fonctionne pas si des autorisations sont accordées à des utilisateurs non valides  
 Si un utilisateur Active Directory disposant des autorisations Vue BAM est retiré d'AD, le portail BAM ne se charge pas correctement pour tous les utilisateurs (à l'exception des DBO).  
  
 Pour résoudre ce problème, supprimez l'utilisateur non valide du rôle de sécurité bam_{viewname}view correspondant.  
  
## <a name="cannot-export-or-import-a-bam-definition-to-localhost"></a>Impossible d'exporter une définition BAM vers localhost ou d'en importer une depuis localhost  
 Lorsque vous exportez une définition BAM dans un fichier XML, le message d'erreur suivant s'affiche si vous tentez de le faire vers localhost :  
  
 `The system cannot find the path specified.`  
  
 L'exportation d'une définition BAM vers localhost n'est pas prise en charge. De même, l'importation d'une définition BAM à partir de localhost n'est pas prise en charge.  
  
## <a name="alerts-do-not-work-after-upgrading-sql-server-editions"></a>Les alertes ne fonctionnent plus après la mise à niveau des différentes éditions de SQL Server  
 Si vous avez mis à niveau une édition de [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] vers une autre (par exemple, une édition Standard vers une édition Entreprise), les alertes BAM ne démarreront plus. Pour résoudre ce problème, supprimez les alertes BAM, puis recréez-les ou mettez à niveau [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Notification Service.  
  
#### <a name="to-upgrade-the-sql-server-notification-service"></a>Pour mettre à niveau SQL Server Notification Service  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur **Microsoft SQL Server 2005**, puis cliquez sur **invite de commandes de Service de Notification**.  
  
2.  À l'invite de commandes, tapez la commande suivante :  
  
     `nscontrol.exe upgrade -name <instanceName>`  
  
## <a name="objectdisposedexception-exception"></a>ObjectDisposedException Exception  
 Si votre application utilise l’intercepteur WF BAM 3.5, vous pouvez recevoir le message d’erreur suivant : **System.ObjectDisposedException : Impossible d’accéder à un objet supprimé**. Pour plus d’informations sur ce message d’erreur, consultez [ObjectDisposedException Exception](http://go.microsoft.com/fwlink/?LinkID=195338) (http://go.microsoft.com/fwlink/?LinkID=195338).   
Pour résoudre ce problème, installez le correctif 960754 disponible à l’adresse [http://go.microsoft.com/fwlink/?LinkID=195339](http://go.microsoft.com/fwlink/?LinkID=195339).  
  
## <a name="workbook-has-lost-its-vba-project-activex-controls-and-other-programmability-related-features"></a>Un classeur a perdu son projet VBA, ses contrôles ActiveX ainsi que d'autres fonctionnalités de programmabilité  
 Lorsque vous tentez d’utiliser BAM.xla dans Microsoft Excel, vous pouvez recevoir l’erreur suivante :  
  
 `This workbook has lost its VBA project, ActiveX controls and any other programmability-related features.`  
  
 Pour résoudre ce problème, installez le **Visual Basic pour Applications** sous **composants partagés d’Office** avec Microsoft Office.  
  
## <a name="pivot-table-fails-to-get-the-data"></a>Le tableau croisé dynamique ne parvient pas à récupérer les données  
 Vous avez reçu les autorisations pour accéder aux bases de données BAM ainsi qu'un rôle et des autorisations sur les vues déployées. La page Recherche d'activité fonctionne normalement et vous pouvez consulter les données. Cependant, dans le tableau croisé dynamique, l'erreur suivante s'affiche :  
  
```  
Failed to get data.  If available, errors returned from the provider are listed below.  
* The following system error occurred:  No connection could be made because the target machine actively refused it.  
```  
  
 Pour résoudre ce problème, ajoutez les paramètres DNS correspondants comme suit :  
  
1.  Cliquez sur **Démarrer** et accédez à **le panneau de configuration**.  
  
2.  Cliquez sur **réseau et Internet** puis cliquez sur **connexions réseau**.  
  
3.  Avec le bouton droit sur la connexion réseau (par exemple, la connexion au réseau Local), puis sélectionnez **propriétés**.  
  
4.  Sur le **connexion au réseau Local** page, sélectionnez **Internet Protocol Version 4 (TCP/IPv4)**, puis cliquez sur **propriétés**.  
  
5.  Cliquez sur **Avancé**. Sur le **paramètres TCP/IP avancés** , cliquez sur le **DNS** onglet.  
  
6.  Sélectionnez **ajouter ces suffixes DNS** , puis ajoutez les suffixes DNS nécessaires.  
  
7.  Cliquez sur **OK** et fermez toutes les fenêtres ouvertes.  
  
## <a name="pivot-table-view-shows-all-values-as-0"></a>La vue du tableau croisé dynamique affiche toutes les valeurs comme étant égales à « 0 »  
 Lorsque vous déployez le portail BAM, la page Recherche d'activité affiche les résultats attendus. Cependant, la vue du tableau croisé dynamique affiche toutes les valeurs comme étant égales à « 0 ». Le message d'erreur suivant s'affiche :  
  
```  
Failed to get data.  If available, errors returned from the provider are listed below.  
* Safety settings on this machine prohibit accessing a data source on another domain.  
```  
  
 Pour résoudre ce problème, ajoutez le site à la zone, comme suit :  
  
1.  Dans la fenêtre Internet Explorer, cliquez sur **outils**, puis cliquez sur **Options Internet**. Cliquez sur le **sécurité** onglet, puis sélectionnez le **sites de confiance** zone.  
  
2.  Cliquez sur **niveau personnalisé** pour définir le niveau de sécurité pour la zone.  
  
3.  Sur le **paramètres** sous le **accéder aux sources de données sur plusieurs domaines** , cliquez sur **invite**. Une invite s'affichera lorsqu'un composant nécessite cette autorisation.  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide de Business Activity Monitoring](../core/using-business-activity-monitoring.md)