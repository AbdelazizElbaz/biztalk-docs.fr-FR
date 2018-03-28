---
title: Installation et la résolution des problèmes de Configuration | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- installing, troubleshooting
- configuring, troubleshooting
- troubleshooting, configuring
- troubleshooting, installing
ms.assetid: 25a2f6c5-c049-4042-8e38-4f7a2556e066
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 62cb7d6181c7be44f7095a6c1d1149132df4e21e
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="installation-and-configuration-troubleshooting"></a>Installation et la résolution des problèmes de Configuration
## <a name="setup-is-unable-to-deploy-the-runtimeschemas-assembly"></a>Le programme d’installation ne parvient pas à déployer l’assembly RuntimeSchemas  
  
### <a name="symptom"></a>Symptôme  
 Le programme d’installation d’A4SWIFT n’a pas pu déployer RuntimeSchemas.dll. Si l’assembly n’est pas déployé manuellement après l’installation, l’Assistant de Configuration d’A4SWIFT échoue.  
  
### <a name="possible-cause"></a>Cause possible  
 Une des conditions suivantes existe :  
  
-   L’assembly de schémas d’exécution a déjà été déployé lorsque vous avez essayé d’effectuer une installation initiale d’A4SWIFT.  
  
-   [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] n’a pas démarré sur l’ordinateur sur lequel vous avez essayé d’installer A4SWIFT.  
  
-   L’assembly de schémas d’exécution a déjà été déployé lorsque vous a tenté de mettre à niveau A4SWIFT et a été référencé par un autre assembly. Cet a empêché l’annulation du déploiement de l’assembly de schémas d’exécution par le A4SWIFT mettre à niveau le programme.  
  
### <a name="solution"></a>Solution  
 Procédez comme suit, selon la nature du problème :  
  
-   Si l’assembly de schémas d’exécution a déjà été déployé lorsque vous avez tenté d’exécuter une installation initiale de A4SWIFT, ouvrez l’Explorateur BizTalk dans [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] [!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)], avec le bouton droit de l’assembly [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]. Solutions.FinancialServices.SWIFT.RuntimeSchemas, puis cliquez sur Annuler le déploiement. Utilisez l’Assistant Déploiement BizTalk pour déployer la dernière version de RuntimeSchemas.dll de *% ProgramFiles%*\Microsoft BizTalk Accelerator pour SWIFT\Assemblies.  
  
-   Si [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] a été ne pas démarré, démarrez [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] dans le [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] Service Manager. Utilisez l’Assistant Déploiement BizTalk pour déployer la dernière version de RuntimeSchemas.dll de *% ProgramFiles%*\Microsoft BizTalk Accelerator pour SWIFT\Assemblies.  
  
-   Si l’assembly de schémas d’exécution a déjà été déployé lorsque vous a tenté de mettre à niveau A4SWIFT et a été référencé par un autre assembly, annuler le déploiement de l’assembly de référence dans l’Explorateur BizTalk et annuler le déploiement RuntimeSchemas.dll dans l’Explorateur BizTalk. Utilisez l’Assistant Déploiement BizTalk pour déployer la dernière version de RuntimeSchemas.dll de *% ProgramFiles%*\Microsoft BizTalk Accelerator pour SWIFT\Assemblies.  
  
## <a name="after-the-web-components-feature-is-removed-message-repair-and-reconciliation-is-incorrectly-shown-as-uninstalled"></a>Une fois la fonctionnalité des composants Web est supprimée, Message Repair et rapprochement incorrectement apparaissent en tant que tels  
  
### <a name="symptom"></a>Symptôme  
 Après avoir supprimé les composants Web pour Message Repair et New Submission fonctionnalité d’A4SWIFT, vous ne peut pas désinstaller, installer ou configurer le Message Repair et fonction rapprochement (ou les composants A4SWIFT). Si le Message Repair et rapprochement est installé, A4SWIFT ne reconnaît pas que la fonctionnalité est installée. Si vous tentez d’installer, modifier ou supprimer le Message de réparation et réconciliation à partir d’Ajout/Suppression de programmes (affiché dans le panneau de configuration), Ajout/Suppression de programmes indique que la fonctionnalité n’est pas installée.  
  
### <a name="possible-cause"></a>Cause possible  
 Vous ont été supprimés de la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] une fois que vous aviez installé les composants Web pour la fonctionnalité de Message Repair et New Submission et la fonctionnalité de Message Repair et rapprochement du groupe Administrateurs. Si vous supprimez ensuite la fonctionnalité des composants Web (vous pouvez ainsi faire sans être membres de le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] groupe Administrateurs), le programme d’installation A4SWIFT supprimera les fichiers que le Message réparer et fonctionnalité de réconciliation a une dépendance sur. Ces fichiers incluent ConfigFramework.exe.  
  
### <a name="solution"></a>Solution  
 Si vous rencontrez ce problème, procédez comme suit :  
  
1.  Dans la fenêtre Gestion de l’ordinateur, ajouter vous-même dans le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] groupes d’administration, la session, puis vous reconnecter.  
  
2.  Réinstallez les composants Web pour Message Repair et New Submission fonctionnalité.  
  
    > [!NOTE]
    >  Étape 2 ajoute ConfigFramework.exe dans l’installation d’A4SWIFT.  
  
3.  Réinstallez la fonctionnalité MRSR.  
  
4.  Si vous encore ne souhaitez pas les composants Web pour Message Repair et la fonctionnalité de nouvelle soumission, supprimez-le.  
  
## <a name="repairing-a4swift-to-add-the-service-folder-can-result-in-improper-access-permissions-for-that-folder"></a>A4SWIFT pour ajouter le dossier du Service de réparation peut entraîner des autorisations d’accès incorrect pour ce dossier  
  
### <a name="symptom"></a>Symptôme  
 Si vous supprimez le dossier *% ProgramFiles%*\Microsoft BizTalk Accelerator pour SWIFT\Service à partir d’une installation d’A4SWIFT correctement configurée et puis exécutez le A4SWIFT de nouveau la fonctionnalité réparer du programme d’installation A4SWIFT pour ajouter le dossier de serveur installation, les autorisations d’accès pour le dossier du Service ne seront pas correctes. Les autorisations appropriées sont contrôle total pour les administrateurs d’A4SWIFT et de lecture et exécution pour les utilisateurs d’A4SWIFT.  
  
 Cela se produit également si vous exécutez la fonctionnalité réparer du programme d’installation A4SWIFT lorsque le dossier Service existe. Les autorisations d’accès, tel que défini par l’Assistant de Configuration d’A4SWIFT, seront remplacées par des valeurs incorrectes.  
  
### <a name="possible-cause"></a>Cause possible  
 Installation des composants Web pour Message Repair et New Submission fonctionnalité ajoute le dossier du Service. Si vous supprimez le dossier, puis exécutez l’option de réparation du programme d’installation A4SWIFT pour ajouter les composants Web pour Message Repair et New Submission A4SWIFT le programme d’installation ne s’exécute pas l’Assistant de configuration (ConfigFramework.exe) pour définir les autorisations pour le dossier. Étant donné que l’Assistant configuration a déjà été exécuté, il est très difficile exécuter l’Assistant pour réinitialiser la configuration. Par conséquent, l’option de réparation recréera tous les fichiers et dossiers supprimés, mais les autorisations d’accès ne sera pas défini correctement.  
  
 Le processus de réparation remplace également des autorisations pour le dossier de Service si le dossier existe lorsque la réparation est effectuée. Comme avec le cas de la suppression du dossier Service avant l’exécution de repair, il sera très difficile d’exécuter le programme de configuration pour définir les autorisations. Dans cette instance, ainsi, les autorisations seront incorrectes et vous devez les définir manuellement.  
  
### <a name="solution"></a>Solution  
 Si vous rencontrez ce problème, définir manuellement les autorisations d’accès suivants pour le dossier du Service :  
  
|Groupe ou nom d'utilisateur|Autorisation|  
|------------------------|----------------|  
|Administrateurs d’A4SWIFT|Contrôle total|  
|Utilisateurs d’A4SWIFT|Lire et exécuter|  
  
 Pour définir ces autorisations, procédez comme suit :  
  
 Dans [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Explorer, accédez à *% ProgramFiles%*\Microsoft BizTalk Accelerator pour SWIFT\Service.  
  
1.  Cliquez sur le dossier du Service, cliquez sur **propriétés**, puis cliquez sur le **sécurité** onglet.  
  
2.  Dans le volet de noms utilisateur ou de groupe, de la boîte de dialogue Propriétés du Service, cliquez sur **ajouter**, entrez ***\<nom du serveur\>* \A4SWIFT administrateurs**, puis cliquez sur **OK** .  
  
    > [!NOTE]
    >  Si le groupe d’administrateurs d’A4SWIFT est un groupe de domaine, entrez ***\<nom de domaine\>* \A4SWIFT administrateurs**.  
  
3.  Répétez l’étape 2 pour ***\<nom du serveur\>* \A4SWIFT utilisateurs**, ou  **\< *nom de domaine*\>\A4SWIFT utilisateurs** si le Groupe d’utilisateurs d’A4SWIFT est un groupe de domaine.  
  
4.  Dans le volet noms d’utilisateur ou de groupe, sélectionnez **A4SWIFT administrateurs**. Dans le volet d’autorisations, sélectionnez **autoriser** pour **contrôle total**.  
  
5.  Dans le volet noms d’utilisateur ou de groupe, sélectionnez **A4SWIFT utilisateurs**. Dans le volet d’autorisations, cliquez sur **autoriser** pour **lire & exécuter**, **contenu du dossier**, et **en lecture**.  
  
6.  Cliquez sur **OK**.  
  
## <a name="upgrade-results-in-a-side-by-side-installation-of-two-versions-of-a4swift"></a>Résultats de la mise à niveau dans une installation côte à côte de deux versions d’A4SWIFT  
  
### <a name="symptom"></a>Symptôme  
 Lorsque vous essayez de mettre à niveau vers [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)], les versions précédentes de A4SWIFT ne peuvent pas être supprimées complètement. Si vous exécutez Ajout/Suppression de programmes à partir du panneau, la liste des programmes actuellement installés peut afficher actuel et les versions précédentes.  
  
### <a name="possible-cause"></a>Cause possible  
 Toutes les conditions suivantes peuvent provoquer la ci-dessus se produise :  
  
-   L’utilisateur tente de mettre à niveau n’est pas un membre de le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] groupe Administrateurs.  
  
-   Le [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] service (MSSQLSERVER) est arrêté.  
  
-   Vous avez effectué une mise à niveau en mode silencieux en utilisant le **setup.exe /addlocal** commande.  
  
### <a name="solution"></a>Solution  
 Pour empêcher une installation côte à côte de [!INCLUDE[btaA4SWIFToldest](../../includes/btaa4swiftoldest-md.md)] et [!INCLUDE[btaA4SWIFT2.3abbrev](../../includes/btaa4swift2-3abbrev-md.md)] qui se produisent au cours de la mise à niveau, assurez-vous que vous (l’utilisateur connecté à) un membre de la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] groupe Administrateurs et que le [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] service (MSSQLSERVER) est démarré.  
  
 Si vous vous retrouvez avec une installation côte à côte de [!INCLUDE[btaA4SWIFToldest](../../includes/btaa4swiftoldest-md.md)] ou [!INCLUDE[btaA4SWIFT2.1abbrev](../../includes/btaa4swift2-1abbrev-md.md)] et [!INCLUDE[btaA4SWIFT2.3abbrev](../../includes/btaa4swift2-3abbrev-md.md)], procédez comme suit :  
  
1.  Sauvegarder les données dans le dossier les Messages SWIFT.  
  
2.  Ouvrez une session sur le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] en tant que membre du groupe Administrateurs BizTalk Server de groupe et assurez-vous que le service MSSQLSERVER est en cours d’exécution.  
  
3.  Supprimer la version précédente d’A4SWIFT.  
  
4.  Mise à niveau vers la dernière version de A4SWIFT à nouveau. Cette fois la mise à niveau fonctionne, et aucune installation côte à côte n’est créée.  
  
5.  À l’aide de l’utilitaire de déploiement BizTalk, annulez manuellement le déploiement [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]. Solutions.FinancialServices.SWIFT.RuntimeSchemas.dll, puis le redéployer à partir du dossier des assemblys de votre emplacement d’installation A4SWIFT. Pour plus d’informations sur cet outil, consultez [l’utilitaire de déploiement BRE](../../adapters-and-accelerators/accelerator-swift/bre-deployment-utility.md).  
  
## <a name="the-uninstall-or-upgrade-process-may-not-complete-correctly-if-you-do-not-restart-when-prompted"></a>Le processus de désinstallation ou de mise à niveau ne peut pas terminée correctement si vous ne redémarrez pas lorsque vous êtes invité  
  
### <a name="symptom"></a>Symptôme  
 Désinstaller ou le processus de mise à niveau ne se terminent pas correctement.  
  
### <a name="possible-cause"></a>Cause possible  
 Si vous n’avez pas annulé un projet qui fait référence à un assembly déployé existant, vous pouvez recevoir un message indiquant que vous devez redémarrer votre système pour que les modifications de configuration A4SWIFT entrent en vigueur. Si vous ne cliquez pas sur **Oui** pour redémarrer immédiatement, certains assemblys qui ont été affectées pour la suppression dans le global assembly cache ne peuvent pas être supprimés, à l’origine de la désinstallation supplémentaires ou des processus de mise à niveau à ne pas terminée correctement.  
  
### <a name="solution"></a>Solution  
 Annuler le déploiement d’un projet qui fait référence à un assembly déployé existant, puis exécutez de nouveau le processus de désinstallation ou de mise à niveau.  
  
## <a name="if-the-iis-admin-service-is-stopped-during-setup-you-must-reconfigure-the-webservice-feature"></a>Si le Service d’administration IIS est arrêté pendant l’installation, vous devez reconfigurer la fonctionnalité du service Web  
  
### <a name="symptom"></a>Symptôme  
 Le [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] Configuration Assistant ne configure pas correctement la fonctionnalité de service Web. Vous recevez l’erreur suivante :  
  
 « Impossible de créer les artefacts MRSR : Impossible de se connecter au serveur distant. »  
  
### <a name="possible-cause"></a>Cause possible  
 Le Service d’administration IIS a été arrêté lorsque vous avez exécuté le [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] Assistant de Configuration.  
  
### <a name="solution"></a>Solution  
 Pour terminer le processus de configuration avec succès, procédez comme suit :  
  
1.  Fermer le [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] console de Configuration.  
  
2.  Redémarrez le Service d’administration IIS.  
  
3.  Exécutez *% ProgramFiles%*\Microsoft BizTalk Accelerator pour SWIFT\Configuration.exe.  
  
4.  Dans le [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] console de Configuration, sélectionnez **annuler la configuration des fonctionnalités** , puis sélectionnez **WebService**.  
  
5.  Assurez-vous que l’état de la fonctionnalité de service Web dans la console de Configuration s’affiche comme étant non configurée.  
  
6.  Sélectionnez **appliquer la Configuration**.  
  
    > [!NOTE]
    >  L’Assistant de Configuration d’A4SWIFT va maintenant configurer la fonctionnalité de service Web correctement.  
  
## <a name="a4swift-configuration-will-fail-if-the-biztalkserverapplication-host-was-not-created-in-biztalk-server-configuration"></a>Configuration d’A4SWIFT échoue si l’hôte BizTalkServerApplication n’a pas été créé dans la configuration de BizTalk Server  
  
### <a name="symptom"></a>Symptôme  
 Le [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] Configuration Assistant ne configure pas correctement la fonctionnalité de service Web. Vous recevez l’erreur suivante :  
  
 « Impossible de créer les artefacts MRSR : référence non définie sur une instance d’un objet de l’objet. »  
  
### <a name="possible-cause"></a>Cause possible  
 Un hôte In-Process et une Instance d’hôte n’ont pas été créés lors de la configuration de l’exécution de BizTalk Server.  
  
### <a name="solution"></a>Solution  
 Pour réparer la configuration d’A4SWIFT, procédez comme suit :  
  
-   Créer un hôte dans l’Administration de BizTalk Server. Il n’est pas nécessaire d’installer une instance en cours d’exécution maintenant.  
  
-   Exécutez l’outil RepairBAS dans le *% ProgramFiles%*\Microsoft BizTalk Accelerator pour SWIFT\SDK\Tools des dossiers de l’installation d’A4SWIFT.  
  
 Pour ce faire, procédez comme suit :  
  
1.  Démarrer **Administration de BizTalk Server** console.  
  
2.  Dans la Console Administration de BizTalk Server, développez **Administration de BizTalk Server**, puis développez **groupe BizTalk**, puis développez **paramètres de plateforme.**  
  
3.  Avec le bouton droit **hôtes**, pointez sur **nouveau**, puis sélectionnez **hôte**.  
  
4.  Dans l’écran de propriétés de l’hôte, dans le volet Général, entrez les éléments suivants :  
  
    -   Nom d’hôte : **BizTalkServerApplication**  
  
    -   Type : **In-Process**  
  
    -   Groupe Windows :  **\< *domaine*\>\BizTalk utilisateurs d’applications** (ou le compte que vous avez configurée lors de la configuration de BizTalk Server pour l’exécution de BizTalk In-Process applications)  
  
    -   Dans la section Options, sélectionnez à la fois **autoriser le suivi de hôte** et **transformer en hôte par défaut dans le groupe**.  
  
5.  Cliquez sur **OK**.  
  
6.  Cliquez sur **Démarrer** puis cliquez sur Exécuter. Type **cmd** puis cliquez sur **OK**.  
  
7.  À l’invite de commandes, accédez au * % programfiles % ***\Microsoft BizTalk Accelerator pour SWIFT\SDK\Tools**.  
  
8.  Type **RepairBAS.exe** , puis appuyez sur **entrée**.  
  
## <a name="you-must-change-the-bre-deployment-configuration-file-when-running-the-bre-deployment-utility-on-a-64-bit-computer"></a>Vous devez modifier le fichier de configuration BRE lors de l’exécution de l’utilitaire de déploiement du moteur BRE sur un ordinateur 64 bits  
  
### <a name="symptom"></a>Symptôme  
 L’utilitaire de déploiement du moteur BRE ne fonctionne pas correctement lorsque vous l’exécutez sur un ordinateur 64 bits, ou dans un répertoire par défaut (autre que C:\Program Files\Microsoft BizTalk Accelerator pour SWIFT) sur un ordinateur 32 bits.  
  
### <a name="possible-cause"></a>Cause possible  
 L’utilitaire de déploiement du moteur BRE ne fonctionnera pas correctement tant que vous modifiez les chemins d’accès dans le fichier BREDeployment.exe.config situé dans le \<lecteur\>: \Program Files\Microsoft BizTalk Accelerator pour SWIFT\SDK\Tools dossier.  
  
### <a name="solution"></a>Solution  
 Mettre à jour la configuration de l’utilitaire en ouvrant BREDeployment.exe.config dans le bloc-notes et en modifiant les dossiers pour les stratégies de base, les schémas et les répertoires de vocabulaire.  
  
## <a name="see-also"></a>Voir aussi  
 [Dépannage : problèmes et résolutions](../../adapters-and-accelerators/accelerator-swift/troubleshooting-issues-and-resolutions1.md)