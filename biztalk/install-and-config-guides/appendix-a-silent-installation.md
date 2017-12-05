---
title: "Annexe a : Installation sans assistance | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 94ded6b3-13ca-47e6-a038-254514f500e7
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c03568f86b8c3b609fed74a9faf7f6057614151c
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="appendix-a-silent-installation"></a>Annexe A : Installation sans assistance
Cette rubrique énumère les étapes nécessaires pour créer une installation sans assistance de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
## <a name="create-a-silent-installation"></a>Créer une installation sans assistance  
  
1.  Cliquez successivement sur **Démarrer**, **Tous les programmes**, **Accessoires**, puis **Invite de commandes**.  
  
2.  Accédez à l'emplacement d'installation. À l’invite de commandes, tapez `setup.exe /``<command name> <options>` et appuyez sur **Entrée**. Le fichier journal montre l'état de l'installation.  
  
|Nom de la commande|Option|Description|  
|------------------|------------|-----------------|  
|/HELP, ou /? ou /H||Fournit de l'aide et une référence rapide.|  
|/QUIET||Supprime l'interface utilisateur durant l'installation, c'est-à-dire toutes les boîtes de dialogue, les erreurs ou les invites nécessitant des saisies de l'utilisateur. Tous les messages sont entrés dans le fichier journal de l'installation. **Remarque :** L’indicateur Quiet (Silencieux) ne peut pas être spécifié pour une mise à niveau, car celle-ci nécessite la confirmation par l’utilisateur des options sélectionnées.|  
|/CABPATH|\<*Emplacement du fichier CAB*\>|Indique l'emplacement du fichier CAB redistribuable.|  
|/S|\<*Fichier XML de configuration*\>|Effectue une installation sans assistance des composants trouvés dans le fichier de configuration spécifié. **Remarque :** Pour installer tous les composants, spécifiez ALL pour le paramètre `InstalledFeature` du fichier XML de configuration.|  
|/PASSIVE||Effectue une installation passive. Le programme d'installation affiche uniquement la barre de progression.|  
|/NORESTART||Supprime les invites de redémarrage et les redémarrages automatiques à la fin de l'installation.|  
|/FORCERESTART||Impose toujours un redémarrage à la fin de l'installation.|  
|/PROMPTRESTART||Affiche un message d'invite utilisateur avant de lancer le redémarrage.|  
|/X ou /UNINSTALL||Désinstalle [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].|  
|/L|\<Fichier journal\> [i] [w] [e] [a] [r] [u] [c] [m] [p] [v] [*]|Écrit les informations de journalisation dans un fichier journal situé dans le chemin spécifié. Utilise toujours l'enregistrement du programme d'installation Windows commenté et l'ajoute à un fichier existant.<br /><br /> Les indicateurs suivants désignent les informations à consigner :<br /><br /> i - Messages d'état<br /><br /> w - Avertissements récupérables<br /><br /> e - Tous les messages d'erreur<br /><br /> a - Démarrage des actions<br /><br /> r - Enregistrements spécifiques à certaines actions<br /><br /> u - Requêtes de l'utilisateur<br /><br /> c - Paramètres d'interface utilisateur initiaux<br /><br /> m - Mémoire insuffisante<br /><br /> p - Propriétés du terminal<br /><br /> v – Mode documenté<br /><br /> * - Tous|  
|/IGNOREDEPENDENCIES||Ignore les vérifications des composants téléchargeables requis.|  
|/ INSTALLDIR \< *le chemin d’installation*\>|\<*dossier Program files\>*|Spécifie le chemin d'accès complet de l'emplacement d'installation du produit.|  
|/COMPANYNAME|\<*nom de la société*\>|Définit le nom de la société ou de l'organisation.|  
|/USERNAME|\<*nom d’utilisateur*\>|Définit le nom de l'utilisateur.|  
|/ADDLOCAL ALL||Installe tous les composants. Pour plus d’informations sur la commande ADDLOCAL, consultez [Liste de valeurs pour la commande ADDLOCAL](http://go.microsoft.com/fwlink/p/?LinkID=189319).|  
|/REMOVE ALL||Supprime tous les composants.|  
|/REPAIR ALL||Répare tous les composants.|  
|/CEIP||Active le Programme d’amélioration du produit (CEIP)|  
|/PRODUCT UDDI||Installe UDDI|  
|msiexec.exe /i  [CHEMIN_MSI] INSTALLDIR=[CHEMIN_REP_INSTALL] DATADIR=[CHEMIN_REP_DONNEES] SQLSERVERMACHINENAME=[NOM_SQLSERVER] OVERWRITERFIDSTORE=1 INSTALLLEVEL=5 /lvxp RfidServicesInstall.txt /q<br /><br /> Par exemple : msiexec.exe /i "\\\ABC\XYZ\RFID_x86\RfidServices.msi" INSTALLDIR=“C:\Program Files\Microsoft BizTalk RFID\” DATADIR=“C:\Program Files\Microsoft BizTalk RFID\” SQLSERVERMACHINENAME=(local) OVERWRITERFIDSTORE=1 INSTALLLEVEL=5 /lvxp RfidServicesInstall.txt /q||Installe Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] RFID|  
  
 **Supplément**  
  
-   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] active la distribution électronique automatisée des logiciels, également appelée installation sans assistance (ou silencieuse). L'installation sans assistance procède ainsi :  
  
    -   Installe [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sur les ordinateurs qui ont la même configuration.  
  
    -   Permet aux administrateurs qui souhaitent installer [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sur des ordinateurs distants de le faire sans l’intervention des utilisateurs.  
  
    -   L'utilisateur n'a pas à surveiller l'installation et fournir des commentaires.  
  
-   Pour créer une installation sans assistance, utilisez les options de ligne de commande pour supprimer toute interaction.  
  
-   Lorsque vous terminez une installation sans assistance, aucun message ne s'affiche dans la fenêtre de commande. Utilisez le fichier journal d'installation pour examiner la situation.  
  
