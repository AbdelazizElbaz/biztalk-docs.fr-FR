---
title: "Comment installer la Solution gestion des processus d’entreprise | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- installing, examples
- process management solution tutorial, installing
- process management solution tutorial, deployment prerequisites
ms.assetid: 930f3bb1-05e6-4b02-852d-6139aaf341f0
caps.latest.revision: "61"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 22b16e8c33dfdbf44b000cc9a048e86a5869d616
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-install-the-business-process-management-solution"></a>Installation de la solution de gestion des processus d'entreprise
La procédure suivante décrit la préparation de votre ordinateur pour l'installation de la solution de gestion des processus d'entreprise, puis l'installation de la solution sur votre ordinateur.  
  
-   [Préparer l’ordinateur pour l’installation de la Solution gestion des processus d’entreprise](#step1)  
  
     Dans le cadre de la préparation, vous êtes amené à créer des dossiers, des files d'attente et une base de données SQL qui seront utilisés par les ports de réception et d'envoi. Vous devez également créer deux répertoires virtuels pour l'application cliente (CSRWebApp) et le service Web proxy OrderBroker.  
  
-   [Configurez l’ordinateur pour l’installation de la Solution gestion des processus d’entreprise](#step3)  
  
-   [Installer la Solution gestion des processus d’entreprise](#step5)  
  
> [!NOTE]
>  Vous devez exécuter des fichiers de commandes pour déployer la solution. Il est recommandé de rediriger la sortie des fichiers de commandes vers un fichier texte pour vérifier l'exécution correcte du script.  
  
##  <a name="step1"></a>Préparer l’ordinateur pour l’installation de la Solution gestion des processus d’entreprise  
  
#### <a name="to-prepare-the-computer-for-installing-the-business-process-management-solution"></a>Pour préparer l'ordinateur pour l'installation de la solution de gestion des processus d'entreprise  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **outils d’administration**, puis cliquez sur **Services**. À l’aide de la **Services** de la console, assurez-vous que les services suivants sont en cours d’exécution :  
  
    -   **Publication FTP**  
  
    -   **Message Queuing**  
  
    -   **Publication du World Wide Web**  
  
2.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **outils d’administration**, cliquez sur **gestion de l’ordinateur** de la console, puis ajoutez le Compte de service BizTalk au groupe Administrateurs local.  
  
3.  Si vous avez installé Windows SharePoint Services, excluez la (racine) de la **Site Web par défaut** à partir de Windows SharePoint Services de chemins d’accès gérés comme suit : cliquez sur **Démarrer**, pointez sur **tous les programmes** , pointez sur **outils d’administration**, puis cliquez sur **Administration centrale de SharePoint**.  
  
    1.  Sous **Configuration du serveur virtuel**, sélectionnez **configurer les paramètres du serveur virtuel**.  
  
    2.  Sur le **liste des serveurs virtuels** , cliquez sur **Site Web par défaut**.  
  
    3.  Sur le **paramètres du serveur virtuel** , cliquez sur **définir les chemins d’accès gérés**.  
  
    4.  Dans le **chemins d’accès inclus** section de la **défini par chemin d’accès géré** page, sélectionnez **racine** puis cliquez sur **supprimer des chemins d’accès sélectionnés**.  
  
    5.  Ouvrez une invite de commandes, puis exécutez IISReset.  
  
##  <a name="step3"></a>Configurez l’ordinateur pour l’installation de la Solution gestion des processus d’entreprise  
  
#### <a name="to-configure-the-computer-for-installing-the-business-process-management-solution"></a>Pour configurer l'ordinateur pour l'installation de la solution de gestion des processus d'entreprise  
  
1.  Fermez votre session, puis ouvrez une session sur l'ordinateur à l'aide du compte de service BizTalk.  
  
2.  Ouvrez une invite de commandes, tapez la commande suivante, puis appuyez sur ENTRÉE pour définir la variable d'environnement %BTSSolutionsPath% et indiquer le dossier de base pour les solutions E2E. Fermez ensuite l'invite de commandes.  
  
    -   `setx BTSSolutionsPath "%ProgramFiles%\Microsoft BizTalk Server 2009\SDK\Scenarios"`  
  
        > [!NOTE]
        >  Si vous utilisez un ordinateur 64 bits, utilisez %ProgramFiles(x86)% à la place de %ProgramFiles%.  
  
        > [!NOTE]
        >  Pour plus d’informations sur la commande SETX, consultez le site Web Microsoft TechNet à l’adresse [http://go.microsoft.com/fwlink/?LinkId=67831](http://go.microsoft.com/fwlink/?LinkId=67831).  
  
3.  Ouvrez une invite de commandes, accédez au répertoire en cours %BTSSolutionsPath%\BPM\HistoryDB dossier, tapez `CreateDatabase.cmd`, puis appuyez sur ENTRÉE pour créer la base de données de l’historique.  
  
    > [!NOTE]
    >  L'utilisateur exécutant l'hôte spécifié comme gestionnaire pour l'adaptateur d'envoi SQL doit être autorisé à exécuter les procédures stockées dans la base de données SouthridgeVideoHistory.  
  
4.  Ouvrez une invite de commandes, puis exécutez la commande suivante pour définir l'environnement d'exécution de scripts par défaut sur CScript.exe.  
  
    -   `CScript /H:CScript`  
  
5.  Ouvrez une invite de commandes, puis exécutez la commande suivante pour créer l'application Web CSRWebApp.  
  
    -   `iisvdir /create "Default Web Site" CSRWebApp "%BTSSolutionsPath%\BPM\CSRWebApp"`  
  
        > [!NOTE]
        >  Pour plus d’informations sur iisvdir.vbs, consultez le site Web Microsoft TechNet à l’adresse [http://go.microsoft.com/fwlink/?LinkId=67830](http://go.microsoft.com/fwlink/?LinkId=67830).  
  
6.  Ouvrez une invite de commandes, puis exécutez la commande suivante pour créer le répertoire virtuel IIS OrderBroker_Proxy.  
  
    -   `iisvdir /create "Default Web Site" BTSScn.BPM.OrderBroker_Proxy "%BTSSolutionsPath%\BPM\OrderBroker_Proxy"`  
  
    > [!NOTE]
    >  Vous pouvez utiliser le Gestionnaire des Services Internet (IIS) pour créer l'application Web. Pour plus d’informations sur la création d’applications dans IIS 7.0, consultez la Documentation d’IIS 7.0 à [http://go.microsoft.com/fwlink/?LinkId=59263](http://go.microsoft.com/fwlink/?LinkId=59263).  
  
7.  Créez un pool d'applications IIS et définissez son identité en tant qu'utilisateur membre du groupe Utilisateurs d'hôtes BizTalk isolés et du groupe IIS_WPG, comme suit :  
  
    1.  Dans le Gestionnaire des Services Internet (IIS), cliquez sur **Pools d’applications**, sélectionnez **nouveau**, puis sélectionnez **Pool d’applications**.  
  
    2.  Type de la **ID du pool d’applications** (toute valeur), puis cliquez sur **OK**.  
  
    3.  Cliquez sur le pool d’applications que vous avez créé, puis sélectionnez **paramètres avancés**.  
  
    4.  Développez **modèle de processus**, cliquez dans la colonne de droite pour le **identité** définition, puis cliquez sur **...**  
  
    5.  Sélectionnez un compte d’utilisateur (soit un **compte** ou **compte personnalisé** ) qui dispose des autorisations pour créer et exécuter des fichiers dans le répertoire Windows\Temp. Lorsque vous avez configuré BizTalk, le processus de configuration a déjà défini ces autorisations pour l'utilisateur ajouté au groupe Utilisateurs d'hôtes BizTalk isolés. Spécifier le même utilisateur constitue une bonne option.  
  
8.  Dans le Gestionnaire des Services Internet (IIS), développez **Sites Web**, développez **Site Web par défaut**, avec le bouton droit **BTSScn.BPM.OrderBroker_Proxy**, pointez sur **Gérer l’Application**, puis cliquez sur **paramètres avancés**.  
  
9. Définissez **Pool d’applications** au pool d’applications que vous avez créé à l’étape précédente.  
  
10. Répétez les deux étapes précédentes pour le **CSRWebApp** application.  
  
11. Réinitialisez IIS pour que ces modifications prennent effet immédiatement. Pour ce faire, exécutez **iisreset** à une invite de commandes.  
  
12. À l’invite de commandes, remplacer le dossier actuel par le répertoire % BTSSolutionsPath%\BPM\Scripts, tapez `CreateQueues.vbs`, puis appuyez sur ENTRÉE pour créer les files d’attente privées suivantes.  
  
    |Nom|Transactionnelle|Protocole de transaction|  
    |----------|-------------------|--------------------------|  
    |ToFacilitiesQ|Oui|Natif|  
    |FromFacilitiesQ|Oui|Natif|  
    |FromFixedOrdersQ|Oui|Natif|  
    |ToServicingSystemQ|Oui|Natif|  
    |ToCSRSystemQ|Non|HTTP|  
    |ToVendorSystemQ|Non|HTTP|  
  
    > [!NOTE]
    >  Vous pouvez utiliser **gestion de l’ordinateur** -composant logiciel enfichable pour créer les files d’attente. Pour plus d’informations sur la création d’une file d’attente privée, consultez la documentation de Message Queuing à [http://go.microsoft.com/fwlink/?LinkId=59264](http://go.microsoft.com/fwlink/?LinkId=59264). Pour plus d’informations sur l’installation de MSMQ 3.0, consultez la documentation de Message Queuing à [http://go.microsoft.com/fwlink/?LinkId=59265](http://go.microsoft.com/fwlink/?LinkId=59265).  
  
13. À l’invite de commandes, remplacer le dossier actuel par le répertoire % BTSSolutionsPath%\BPM\Scripts, tapez `CreateTestDirectories.cmd`, puis appuyez sur ENTRÉE.  
  
    -   Les dossiers suivants sont créés dans le dossier %SystemDrive%\BPMTest  
  
         CSRResponse-DSP  
  
         VendorResponse-DSP  
  
         OrderErrors-SP  
  
         ErrorResponse-RP-TestRL  
  
         Facilities-SP  
  
         Facilities-RP-TestRL  
  
         HistoryInsert-SP  
  
         HistoryUpdate-SP  
  
         Order-RP-TestRL  
  
         ServicingSystem-SP  
  
         Vendor-RP-TestRL  
  
         BizTalkErrors-SP  
  
    -   Le dossier FromVendor est créé dans le dossier %SystemDrive%\Inetpub\ftproot.  
  
        > [!NOTE]
        >  Si le système Windows n'est pas installé sur le lecteur C, vous devez remplacer %SystemDrive% par C:. Les noms de dossier doivent correspondre à l'adresse figurant dans les fichiers de liaison fournis par la solution de gestion des processus d'entreprise.  
  
        > [!NOTE]
        >  Le compte de service BizTalk doit avoir l'autorisation de lecture/écriture sur le dossier FromVendor.  
  
##  <a name="step5"></a>Installer la Solution gestion des processus d’entreprise  
  
#### <a name="to-install-the-business-process-management-solution"></a>Pour installer la solution de gestion des processus d'entreprise  
  
1.  À l’invite de commandes, remplacer le dossier actif à % BTSSolutionsPath%\BPM, tapez `SetupBPM.bat`, puis appuyez sur ENTRÉE.  
  
    > [!NOTE]
    >  Avant d’exécuter SetupBPM.bat, dans les fichiers **%BTSInstallPath%/SDK/Scenarios/BPM/CSDWebApp/App_WebReferences/SouthridgeVideo_OrderBroker/OrderBrokerOrch_OrderPort.WSDL** et **%BTSInstallPath%/SDK/ Scenarios/BPM/OrderBroker_Proxy/App_Code/OrderBrokerOrch_OrderPort.asmx.cs**, remplacez toutes les instances de 8f8bbebbb3fb375a with XXXXXXXXXXXXXXXX.  
  
     La commande SetupBPM.bat effectue les tâches suivantes :  
  
    1.  création d'une clé de nom fort unique (SNK) pour signer les assemblys de la solution de gestion des processus d'entreprise ;  
  
    2.  extraction du jeton de clé publique de la clé de nom fort ;  
  
    3.  mise à jour des fichiers de liaison à l'aide du jeton de clé publique ;  
  
    4.  création de la solution de gestion des processus d'entreprise et installation d'OpsAdapter ;  
  
    5.  création de SSOApplicationConfig dans le dossier %BTSSolutionsPath%\Common.  
  
2.  Déployez les règles d'entreprise de Southridge Video à l'aide de l'Assistant Déploiement du moteur de règles d'entreprise :  
  
    1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], puis cliquez sur **Assistant de déploiement du moteur de règles d’entreprise**.  
  
        > [!NOTE]
        >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur. Pour ce faire, cliquez sur l’application, puis **exécuter en tant qu’administrateur**.  
  
    2.  Sur le **Bienvenue** , cliquez sur **suivant**.  
  
    3.  Sur le **la tâche de déploiement** page, sélectionnez **importer et publier la stratégie/vocabulaire à base de données à partir du fichier**, puis cliquez sur **suivant**.  
  
    4.  Sur le **magasin de stratégies** page, conservez tous les autres paramètres par défaut, puis cliquez sur **suivant**.  
  
    5.  Sur le **fichier du moteur de règles d’importation stratégie/vocabulaire** , cliquez sur **Parcourir**, sélectionnez le fichier DecodeAndValidateOrderRules.xml dans le dossier %BTSSolutionsPath%\BPM\Rules, puis cliquez sur **Suivant**.  
  
    6.  Sur le **prêt** , cliquez sur **suivant**, puis, dans le **l’importation de la stratégie/le vocabulaire** , cliquez sur **suivant**  
  
    7.  Sur la page de fin, sélectionnez **réexécuter l’Assistant** pour ouvrir l’Assistant à nouveau, puis cliquez sur **Terminer**.  
  
    8.  Sur le **Bienvenue** , cliquez sur **suivant**.  
  
    9. Sur le **la tâche de déploiement** page, sélectionnez **déployer la stratégie**, puis cliquez sur **suivant**.  
  
    10. Sur le **magasin de stratégies** page, conservez tous les autres paramètres par défaut, puis cliquez sur **suivant**.  
  
    11. Sur le **déployer la stratégie de** page, sélectionnez **DecodeAndValidateOrder 1.0** dans les **stratégie du moteur de règles** liste déroulante, puis cliquez sur **suivant** .  
  
    12. Sur le **prêt** , cliquez sur **suivant**, puis, dans le **déploiement de la stratégie** , cliquez sur **suivant**.  
  
    13. Dans la page de fin, cliquez sur **Terminer**.  
  
3.  Si vous installez la solution de gestion des processus d'entreprise sur un ordinateur 64 bits,  
  
    1.  Ouvrez une invite de commandes 32 bits comme suit : cliquez sur **Démarrer**, cliquez sur **exécuter**, type `%SYSTEMROOT%\SYSWOW64\CMD.EXE`, puis appuyez sur ENTRÉE.  
  
    2.  À l'invite de commandes 32 bits, accédez au répertoire %BTSSolutionsPath%\BPM\Scripts.  
  
    3.  À l'aide du Bloc-notes, ouvrez CreateSouthridgeVideoApplication.cmd, puis remplacez « %CommonProgramFiles%\Enterprise Single Sign-On\ssomanage.exe » par « %SystemDrive%\Program Files\Common Files\Enterprise Single Sign-On\ssomanage.exe ».  
  
        > [!NOTE]
        >  À l'invite de commandes 32 bits, la variable %CommonProgramFiles est modifiée en « % ProgramFiles(x86) %\Common files ». L'utilitaire d'administration SSO étant installé dans %ProgramFiles% même sur un ordinateur 64 bits, vous devez modifier le chemin d'accès. DeployBPM.cmd appelle CreateSouthridgeVideoApplication.cmd.  
  
    4.  À l’invite de commandes 32 bits, tapez type `DeployBPM.cmd`, puis appuyez sur ENTRÉE.  
  
        > [!NOTE]
        >  DeployBPM.cmd doit être exécuté dans une invite de commandes 32 bits car cette commande inclut le script VB d'évaluation des objets x86 nécessitant la version x86 de cscript.exe.  
  
4.  À l’invite de commandes, remplacer le dossier actif pour le répertoire % BTSSolutionsPath%\BPM\Scripts, tapez `DeployBPM.cmd`, puis appuyez sur ENTRÉE. DeployBPM.cmd effectue les tâches suivantes :  
  
    1.  création d'applications BizTalk pour la solution de gestion des processus d'entreprise ;  
  
    2.  ajout de références entre les applications ;  
  
    3.  importation des fichiers de liaison ;  
  
    4.  déploiement des fichiers de définition BAM ;  
  
    5.  enregistrement de la source d'événements SouthridgeVideo ;  
  
    6.  création d'une application associée à authentification unique (SSO) et enregistrement des valeurs de configuration dans l'application SSO.  
  
5.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
    1.  Dans le **Console d’Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, développez **BTSScn.BPM.OrderBrokerApp**, développez **emplacements de réception**, avec le bouton droit **fournisseur-RP-RL**, puis cliquez sur Propriétés.  
  
    2.  Sur le **propriétés** boîte de dialogue, cliquez sur **configurer**, puis entrez les valeurs dans le tableau suivant le **propriétés du Transport** boîte de dialogue :  
  
        |Nom de la propriété|Valeur|  
        |-------------------|-----------|  
        |**Server**|`localhost`|  
        |**Nom d'utilisateur**|\<*Nom de compte de service BizTalk*>|  
        |**Mot de passe**|\<*Mot de passe du compte de service BizTalk*>|  
  
6.  Exécutez la solution de gestion des processus d'entreprise. Pour plus d’informations sur l’exécution de la solution, consultez [l’exécution de la Solution de gestion des processus métier](../core/how-to-run-the-business-process-management-solution.md).  
  
## <a name="next-steps"></a>Étapes suivantes  
 Tester le fonctionnement de la Solution de gestion d’entreprise dans [l’exécution de la Solution de gestion des processus métier](../core/how-to-run-the-business-process-management-solution.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Avant d’installer la Solution gestion des processus d’entreprise](../core/before-installing-the-business-process-management-solution.md)   
 [Programme d’installation de développeur Machine pour la Solution gestion des processus d’entreprise](../core/developer-machine-setup-for-the-business-process-management-solution.md)