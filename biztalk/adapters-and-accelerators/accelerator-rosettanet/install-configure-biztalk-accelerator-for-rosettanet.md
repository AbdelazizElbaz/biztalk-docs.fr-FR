---
title: Installer BizTalk Accelerator pour RosettaNet (BTARN) sur le serveur BizTalk | Documents Microsoft
description: "Consultez les exigences matérielles et logicielles, les étapes d’installation et les étapes de configuration de BTARN dans BizTalk Server"
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a40eca3ccd2092cc3024e0ad69d3737bad869180
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="install-biztalk-accelerator-for-rosettanet"></a>Installer BizTalk Accelerator pour RosettaNet

## <a name="overview"></a>Vue d'ensemble
Installer Microsoft BizTalk Accelerator pour RosettaNet (BTARN).
  
> [!NOTE]
>  Sur l’édition entreprise de BizTalk Server, vous pouvez installer uniquement Enterprise Edition de BizTalk Accelerator pour RosettaNet (BTARN). Dans l’Édition Standard de BizTalk Server, vous pouvez installer uniquement le Standard Edition de BizTalk Accelerator pour RosettaNet (BTARN).  
  
 L’installation de BTARN inclut les éléments suivants :  
  
-   Administration de BTARN  
  
-   Planifications BizTalk Orchestration Designer XLANG (modèles Partner Interface Process)  
  
-   RNIF (RosettaNet Implementation Framework)  
  
-   Base de données BTARN  
  
-   Applications Web frontales HTTP  
  
## <a name="hardware-and-software-requirements"></a>Configuration matérielle et logicielle requise

La configuration matérielle et logicielle requise est les mêmes que BizTalk Server.

|  |Configuration requise pour BizTalk  |Configuration requise de SQL et du système d’exploitation |  
|---------|---------|--------- | 
| [!INCLUDE[bts2016_md](../../includes/bts2016-md.md)] | [Configurations logicielle et matérielle pour BizTalk Server 2016](../../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2016.md) | **Exigences matérielles et logicielles de SQL Server**: <br/>[SQL Server 2016](https://msdn.microsoft.com/library/ms143506(v=sql.130).aspx)<br/>[SQL Server 2014](https://msdn.microsoft.com/library/ms143506(v=sql.120).aspx)<br/><br/>**Configuration matérielle de Windows Server**: <br/>[Windows Server 2016](https://technet.microsoft.com/windows-server-docs/get-started/server-basics)<br/>[Windows Server 2012](https://technet.microsoft.com/library/jj134246.aspx) |
| [!INCLUDE[bts2013r2_md](../../includes/bts2013r2-md.md)] <br/><br/> BizTalk Server 2013 | [Configurations matérielle et logicielle requises pour BizTalk Server 2013 et 2013 R2](../../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2013-and-2013-r2.md) |**Exigences matérielles et logicielles de SQL Server**: <br/>[SQL Server 2014](https://msdn.microsoft.com/library/ms143506(v=sql.120).aspx)<br/>[SQL Server 2012](https://msdn.microsoft.com/library/ms143506(v=sql.110).aspx)<br/>[SQL Server 2008 R2](https://msdn.microsoft.com/library/ms143506(v=sql.105).aspx)<br/><br/>**Configuration matérielle de Windows Server**: <br/>[Windows Server 2012](https://technet.microsoft.com/library/jj134246.aspx)<br/>[Windows Server 2008 R2](https://technet.microsoft.com/library/dd379511(v=ws.10).aspx)  |

> [!TIP] 
> La configuration matérielle répertoriée correspond au minimum nécessaire. Chaque environnement est différent et il est très probable que votre environnement nécessite plus. Consultez [Recommandations pour l’installation, le dimensionnement, le déploiement et la maintenance d’une solution BizTalk Server](http://social.technet.microsoft.com/wiki/contents/articles/666.recommendations-for-installing-sizing-deploying-and-maintaining-a-biztalk-server-solution.aspx). 

## <a name="install-and-configure"></a>Installation et configuration

### <a name="before-you-begin"></a>Avant de commencer

* Pour la base de données BTARN, BTARN configure uniquement les propriétés du nom nom et la base de données de l’ordinateur SQL Server. Pour plus d’informations sur ces propriétés sont stockées dans le Registre.
* Connectez-vous à l’aide d’un compte qui est membre de la le groupe d’administrateurs BizTalk Server. 
* Dans le téléchargement de BizTalk Server, le programme d’installation BTARN se trouve dans le `\BizTalk Accelerators` dossier.
* BizTalk Server doit être installé, et SQL Server doit être en cours d’exécution.
* BTARN et BizTalk Server requièrent Microsoft .NET Framework comme condition préalable du logiciel. Si vous avez plusieurs versions de .NET Framework installée sur votre ordinateur, assurez-vous que l’application Web btarnapp fait référence standard de .NET Framework 4.0. Pour configurer cela, vous pouvez utiliser le Gestionnaire IIS (Internet Information Services).  
* Le compte de l'instance de l'hôte BizTalk et le compte de l'instance de l'hôte BizTalk isolé doivent être identiques. Sinon, BTARN ne fonctionne pas correctement.  
* BTARN vous permet d’ajouter uniquement des comptes de service individuels et pas les groupes, le groupe d’administrateurs BizTalk Server ou le groupe d’utilisateurs d’applications BizTalk.  
* Vous devez créer une extension de service web pour BTSHTTPReceive.dll et configurer le mode d'isolation IIS. Pour plus d’informations, consultez l’entrée « erreur 404 introuvable lors de l’envoi d’une requête HTTP » dans la rubrique « Résolution des problèmes : problèmes et les résolutions » au [http://go.microsoft.com/fwlink/?LinkId=188560](http://go.microsoft.com/fwlink/?LinkId=188560). Consultez également [comment configurer les services IIS pour un emplacement de réception HTTP](../../core/how-to-configure-iis-for-an-http-receive-location.md).  
* Ajoutez votre serveur (http:// <*nom du serveur*>) à la zone Internet Local dans les options de sécurité Internet Explorer.  
*  Si une instance SQL distante utilisant un port autre que celui par défaut est utilisée pour configurer BTARN, les outils clients SQL Server doivent être installés localement. Pour plus d’informations, consultez [Guide d’Installation de BizTalk Server pour un environnement multiserveur](../../install-and-config-guides/install-biztalk-server-in-a-multi-computer-environment.md).
*  Un groupe distinct doit être utilisé pour le rôle - administrateur de BizTalk, les utilisateurs d’hôtes BizTalk et les utilisateurs d’hôtes BizTalk isolés lors de la configuration de BizTalk Server.  
*  BTARN ne prend pas en charge l’utilisation d’alias créés pour l’instance SQL configurer la base de données BTARN.  

### <a name="install-btarn"></a>Installer BTARN

1.  Exécutez le BTARN **setup.exe** en tant qu’administrateur.
  
2.  Sélectionnez **Installer**.  
  
3.  Sur le **informations client** page, tapez votre nom d’utilisateur, d’organisation et de la clé de produit, puis cliquez sur **suivant**.  
  
4.  Sur le **contrat de licence** page, lisez le contrat de licence utilisateur final, puis cliquez sur **accepter**.  
  
    > [!NOTE]
    >  Si vous n'acceptez pas le contrat de licence, vous ne pouvez pas poursuivre l'installation.  
  
5.  Sur le **Options d’Installation** page, sélectionnez **Complete** pour une installation complète ou **personnalisé** pour une installation partielle. Vérifiez le chemin d’installation est correct, puis cliquez sur **suivant**.  
  
    > [!NOTE]
    >  Si vous sélectionnez **personnalisé**, sélectionnez les composants à installer à partir de la **Installation personnalisée** page. Si vous choisissez d’installer uniquement les composants Kit de développement logiciel ou la Documentation, vous devez disposer de .NET Framework est installé avant d’exécuter le programme d’installation.  
  
6.  Sur le **Résumé** passez en revue les composants que vous installez, puis cliquez sur **installer**. Le **progression de l’Installation** écran affiche la progression de la procédure d’installation.  
  
7.  Sur le **l’Installation terminée** , vérifiez le **exécuter l’Assistant Configuration** zone est sélectionnée, puis cliquez sur **Terminer**.  
  
     L'Assistant Configuration de BTARN s'ouvre. Ensuite, configurez BTARN.  
  
    > [!IMPORTANT]
    >  Si vous effectuez une installation personnalisée pour installer uniquement la fonction frontale HTTP BTARN, la configuration BTARN peut échouer une fois l’installation terminée en affichant le « Impossible de créer l’objet pour le composant : WebApp « erreur. Si cela se produit, copiez les deux fichiers (**Microsoft.VC80.ATL.manifest** et **atl80.dll**) à partir d’un ordinateur avec BizTalk Server installé sur celui-ci, à l’ordinateur où vous avez installé la fonction frontale HTTP BTARN.  
    >   
    >  Si Visual Studio est installé sur le même ordinateur que BizTalk Server, le dossier source pour les deux fichiers est *< lecteur\>*: \Program Files\Microsoft Visual Studio 11.0\VC\redist\x86\Microsoft.VC100.ATL. Si Visual Studio n’est pas installé sur le serveur BizTalk server, le dossier source pour les deux fichiers sur le serveur BizTalk est un dossier sous *< lecteur\>*: \WINDOWS\WinSxS. Les fichiers doivent avoir la version 8.0.50727.42. Le dossier de destination sur l’ordinateur où vous avez installé la fonction frontale HTTP est le répertoire d’installation de BTARN (par défaut, *< lecteur\>*: \Program Files\Microsoft BTARN).  
    >   
    >  Après avoir copié ces fichiers à l’ordinateur avec la fonctionnalité de serveur frontal HTTP installée, réexécutez **Configuration.exe**.  
  
### <a name="configure-btarn"></a>Configurer BTARN  

> [!TIP]
 >  Avant de configurer BTARN, veillez à que mapper .NET Framework sous les mappages de gestionnaires dans IIS. En outre, lors de la configuration BTARN, vous devez créer le groupe IIS_WPG manuellement.  
   
1.  Sur le **Assistant de Configuration de BTARN Microsoft** page, sélectionnez **configuration de base** pour configurer le serveur avec les paramètres par défaut, ou **configuration personnalisée** à configurer le serveur à l’aide des options de configuration avancées.  
  
    > [!NOTE]
    >  Si vous souhaitez configurer BTARN à l’aide d’un compte d’administrateur local, entrez le compte en tant que *< nom de l’ordinateur\>\\< nom de l’administrateur\>*  dans les **ID utilisateur** champ de la **informations d’identification du Service** zone.  
  
2.  Dans le **nom du serveur de base de données** texte, vérifiez que le nom de serveur affiché est correct. Dans le **informations d’identification du Service** zone, entrez le nom d’utilisateur (domaine) et le mot de passe pour le compte de services sous lequel seront exécutera. Cliquez sur **configurer**.  
  
3.  Si votre compte dispose des privilèges d’administrateur, cliquez sur **Oui** pour poursuivre la configuration.  
  
4.  Si vous avez sélectionné **configuration de base** à l’étape 1, vérifiez la liste des composants à configurer dans le **Résumé** boîte de dialogue, puis cliquez sur **suivant**. Passez à l'étape 10.  
  
5.  Si vous avez sélectionné **configuration personnalisée** à l’étape 1, procédez comme suit :  
  
    > [!NOTE]
    >  La configuration de BTARN échoue si vous utilisez un caractère spécial dans le nom de l'une des bases de données de BTARN.  
  
6.  Pour configurer l’exécution, dans le **Configuration de Microsoft BTRAN** boîte de dialogue, cliquez sur **Runtime** dans le volet gauche. Dans la droite **Runtime** volet, cliquez sur **activer la fonctionnalité d’exécution sur cet ordinateur**. Pour joindre un groupe existant de la base de données, désactivez **vous souhaitez créer un nouveau groupe de base de données**. Sélectionnez le nom de serveur Web, le numéro de port, les magasins de données, le compte de service du pool d'applications et le dossier virtuel de réception HTTP BizTalk appropriés.  
  
7.  Pour configurer la fonctionnalité WebApps, dans le **Configuration de Microsoft BTRAN** boîte de dialogue, cliquez sur **WebApps** dans le volet gauche, puis cliquez sur **activer la fonctionnalité d’exécution sur cet ordinateur**. Entrez le nom de BizTalk Server approprié et numéro de port ou sélectionnez les valeurs par défaut. Sélectionnez le dossier virtuel approprié de l'application Web.  
  
8.  Cliquez sur **Appliquer la configuration**.  
  
9. Sur le **Résumé** , cliquez sur **suivant**.  
  
10. Sur le **Configuration terminée** , cliquez sur **Terminer**.  
  
    > [!NOTE]
    >  Après avoir installé BTARN, votre administrateur système doit ajouter des utilisateurs aux groupes d'utilisateur d'entreprise (BAS Business User), de gestionnaire d'entreprise (Business Manager) et d'administrateur d'entreprise (Business Administrator). Si vous êtes un administrateur système, vous devrez remplir ces groupes et vous en déconnecter, puis vous connecter en vous ajoutant aux groupes.
  
    > [!WARNING]
    >  Trois groupes doivent être utilisés lors de la configuration de BizTalk Server pour l’administrateur BizTalk, les utilisateurs d’hôtes BizTalk et utilisateurs d’hôtes BizTalk isolés.  

## <a name="start-the-artifacts"></a>Démarrage des artefacts
Les orchestrations BTARN, ports d’envoi et emplacements de réception ne sont pas démarrés automatiquement après la configuration de BTARN.
  
> [!NOTE]
>  Lancez les ports d'envoi PrivateInitiator_To_LOB et PrivateResponder_To_LOB avant de lancer les orchestrations PrivateInitiatorProcess et PrivateResponderProcess.  
  
-   Sur les postes sur lesquels vous avez configuré un serveur virtuel IIS (Internet Information Services) avec le protocole SSL (Secure Sockets Layer), vous devez configurer le serveur virtuel de telle sorte qu'il accepte le certificat du client. Consultez [étape 4 : sécurisé Sockets Layer dans IIS](step-4-enabling-secure-sockets-layer-in-iis.md) dans les [Double Action didacticiel](double-action-tutorial.md).
  
 
1.  Ouvrez **Administration de BizTalk Server** en tant qu’administrateur.  
  
2.  Développez **groupe BizTalk**, développez **Applications**, puis développez **BizTalk Application 1**.  
  
3.  Cliquez sur **Ports d’envoi**. Dans le volet droit, pour chaque port d’envoi qui n’est pas démarré, avec le bouton droit, puis **Démarrer**.  
  
4.  Cliquez sur **Ports de réception** et **les emplacements de réception**. Dans le volet droit, pour chaque emplacement de réception qui n’est pas démarré, avec le bouton droit, puis **Démarrer**.  
  
    > [!NOTE]
    >  Vous devez lancer les ports d'envoi PrivateInitiator_To_LOB et PrivateResponder_To_LOB avant de lancer les orchestrations PrivateInitiatorProcess et PrivateResponderProcess.  
  
5.  Cliquez sur **Orchestrations** et **les emplacements de réception**. Dans le volet droit, pour chaque orchestration n’est pas démarrée, avec le bouton droit, puis **Démarrer**.  
  
## <a name="restart-your-computer"></a>Redémarrez votre ordinateur.  
  
Redémarrez votre ordinateur pour appliquer les éventuelles modifications apportées à la configuration et aux autorisations.  
  
> [!NOTE]
>  Les développeurs peuvent choisir d'installer et de configurer BTARN sur un serveur unique pour le développement, la gestion intermédiaire et les tests. Les développeurs utilisent ce serveur pour écrire leur code personnalisé et le tester avant de passer à la phase de production.  
  
 Pour plus d’informations sur l’installation de BTARN sur un serveur unique, consultez le [didacticiel bouclage](loopback-tutorial.md).
  
## <a name="next-steps"></a>Étapes suivantes  
  
* [Mise à niveau de l’accélérateur RosettaNet](upgrade-biztalk-accelerator-for-rosettanet.md)
* [Désinstallez l’accélérateur RosettaNet](uninstall-biztalk-accelerator-for-rosettanet.md)
* [Résoudre les problèmes de l’installation et de voir les problèmes d’installation connus](troubleshoot-known-issues-installation.md)