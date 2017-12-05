---
title: "Installation en ligne et la Solution orientée services des Versions d’adaptateur du Service | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6050cfe9-4e94-4a55-8b24-fbcc74d9e8f4
caps.latest.revision: "97"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2d648db0f3a7c6ad4dccdbcc7555fc3c0727568c
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="how-to-install-the-inline-and-adapter-versions-of-the-service-oriented-solution"></a>Installation des versions Inline et d'adaptateur de la solution orientée services
La procédure suivante décrit la préparation de votre ordinateur pour l'installation des versions d'adaptateur et Inline de la solution orientée services, puis l'installation de la solution sur votre ordinateur.  
  
> [!NOTE]
>  - Le service de solution orientée services se trouve dans le dossier \< *dossier d’Installation de BizTalk Server*\>\SDK\Scenarios\SO.  
>  - Si vous ne disposez pas d'un macroordinateur pour la solution, vous pouvez modifier la liaison du port de manière à utiliser le service Web Pending Transactions stub. Le service Web génère des transactions localement pour émuler celles du macroordinateur.  
  
##  <a name="step1"></a>Préparer l’ordinateur pour l’installation des versions d’adaptateur et inline de la Solution orientée services  
  
1.  Si vous avez installé Windows SharePoint Services, excluez la (racine) du Site Web par défaut à partir de Windows SharePoint Services de chemins d’accès gérés comme suit : cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur  **Outils d’administration**, puis cliquez sur **Administration centrale de SharePoint**.  
  
    1.  Sous **Configuration du serveur virtuel**, sélectionnez **configurer les paramètres du serveur virtuel**.  
  
    2.  Sur le **liste des serveurs virtuels** , cliquez sur **Site Web par défaut**.  
  
    3.  Sur le **paramètres du serveur virtuel** , cliquez sur **définir les chemins d’accès gérés**.  
  
    4.  Dans le **chemins d’accès inclus** section de la **défini par chemin d’accès géré** page, sélectionnez **racine** puis cliquez sur **supprimer des chemins d’accès sélectionnés**.  
  
    5.  Ouvrez une invite de commandes, puis exécutez IISReset.  
  
2.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **outils d’administration**, cliquez sur **gestion de l’ordinateur** de la console, puis ajoutez le Compte de service BizTalk au groupe Administrateurs local.  
  
3.  Fermez votre session, puis ouvrez une session sur l'ordinateur à l'aide du compte de service BizTalk.  
  
4.  Ouvrez une invite de commandes, tapez la commande suivante, puis appuyez sur ENTRÉE pour définir la variable d'environnement %BTSSolutionsPath%. Fermez ensuite l'invite de commandes.  
  
    -   setx BTSSolutionsPath [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Scenarios"  
  
        > [!NOTE]
        >  Si vous utilisez un ordinateur 64 bits, utilisez %ProgramFiles(x86)% à la place de %ProgramFiles%.  
  
        > [!NOTE]
        >  Pour plus d’informations sur la commande SETX, consultez le site Web Microsoft TechNet à l’adresse [http://go.microsoft.com/fwlink/?LinkId=67831](http://go.microsoft.com/fwlink/?LinkId=67831).  
  
##  <a name="step3"></a>Supprimer la version stub de la Solution orientée services  
  
1.  Ouvrez le **Console d’Administration de BizTalk Server** comme suit : cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], puis cliquez sur  **Administration de BizTalk Server**.  
  
2.  Dans le **Console d’Administration de BizTalk Server**, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, avec le bouton droit **BTSScn.SO.CustomerService**, puis cliquez sur **arrêter**. Dans le **arrêter l’Application** boîte de dialogue, sélectionnez **arrêt complet - arrêter les Instances**, puis cliquez sur **arrêter**.  
  
    > [!NOTE]
    >  Il n'est pas nécessaire de supprimer la version stub pour installer les versions d'adaptateur et Inline. Si vous souhaitez rassembler toutes les versions, ignorez cette étape.  
  
3.  Ouvrez une invite de commandes, tapez la commande suivante, puis appuyez sur ENTRÉE. Cette commande définit l'environnement d'exécution de scripts par défaut sur CScript.exe :  
  
    -   `cscript /H:CScript`  
  
4.  À l'invite de commandes, accédez au répertoire %BTSSolutonsPath%\SO\BTSSoln\Scripts, tapez la commande suivante, puis appuyez sur ENTRÉE :  
  
    -   `UnEnlistStub.vbs`  
  
5.  À l'invite de commandes, tapez la commande suivante, puis appuyez sur ENTRÉE :  
  
    -   `UndeployStub.vbs`  
  
6.  À l'invite de commandes, exécutez la commande suivante :  
  
     SET PATH=%PATH%;[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking"  
  
     Cette opération définit le chemin d'accès des utilitaires BAM.  
  
    > [!NOTE]
    >  Si vous utilisez un ordinateur 64 bits, tapez `%ProgramFiles(x86)%` au lieu de `%ProgramFiles%`.  
  
7.  À l'invite de commandes, accédez au répertoire %BTSSolutionsPath%\SO\BTSSoln\BAM, puis exécutez la commande suivante :  
  
    -   `bm remove-all -DefinitionFile:ServiceLevelTracking.xml`  
  
8.  À l’invite de commandes, accédez au répertoire \< *unique Sign-On installer annuaire d’entreprise*\>, puis exécutez la commande suivante :  
  
    -   `ssomanage -tickets no no`  
  
9. À l'invite de commandes, exécutez la commande suivante pour supprimer l'application associée SSO WoodgroveBank.CustomerService :  
  
    -   `ssomanage -deleteapp WoodgroveBank.CustomerService`  
  
10. À l'invite de commandes, exécutez les commandes suivantes pour supprimer les sites Web utilisés par la version stub. Pour plus d’informations sur iisvdir.vbs, consultez le site Web Microsoft TechNet à l’adresse [http://go.microsoft.com/fwlink/?LinkId=67830](http://go.microsoft.com/fwlink/?LinkId=67830).  
  
    -   `iisvdir /delete W3SVC/1/ROOT/Microsoft.Samples.BizTalk.WoodgroveBank.OrchProxy.Stub`  
  
    -   `iisvdir /delete W3SVC/1/ROOT/Microsoft.Samples.BizTalk.WoodgroveBank.StubSAP`  
  
    -   `iisvdir /delete W3SVC/1/ROOT/Microsoft.Samples.BizTalk.WoodgroveBank.StubPendingTransactions`  
  
    -   `iisvdir /delete W3SVC/1/ROOT/Microsoft.Samples.BizTalk.WoodgroveBank.StubPaymentTracker`  
  
11. Démarrez le Gestionnaire des Services Internet (IIS) comme suit : cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **les outils d’Administration**, puis cliquez sur **Internet Information Services (IIS) Manager**.  
  
    -   Développez le **Pools d’applications**, cliquez sur le pool d’applications que vous avez créé pour les applications Web précédentes, cliquez sur **supprimer**, puis cliquez sur **OK** dans la confirmation boîte de dialogue.  
  
12. Cliquez sur **Démarrer**, pointez sur **le panneau de configuration**, cliquez sur **Ajout / Suppression de programmes**, puis désinstallez le Client IBM WebSphere MQ pour Windows.  
  
13. Démarrer **invite de commandes Visual Studio** , puis exécutez la commande suivante pour supprimer le fichier amqmdnet.dll que vous avez installé pour la version stub.  
  
    -   `gacutil /u amqmdnet`  
  
##  <a name="step5"></a>Préparation des systèmes principaux pour la Solution orientée services pour accéder à  
  
1.  Installez IBM WebSphere MQ pour Windows Server sur l’ordinateur local.  
  
    1.  Conservez tous les paramètres par défaut. Configurer le **Configuration par défaut** à la fin de la **préparation de WebSphere MQ Assistant**. Le Gestionnaire de file d’attente est nommé QM_\<*nom de votre ordinateur*\>.  
  
    2.  Installez le Fix Pack 10 (CSD10). Conservez tous les paramètres par défaut.  
  
2.  Installez MQSeries Agent.  
  
    1.  Réexécutez le programme d’installation de BizTalk Server.  
  
    2.  Sur le **Maintenance du programme** page, sélectionnez **modifier**, puis cliquez sur **suivant**.  
  
    3.  Sur le **Installation des composants** page, développez le **des logiciels supplémentaires** nœud et sélectionnez **MQSeries Agent**.  
  
    4.  Sur le **achèvement** , assurez-vous que **lancer l’Assistant de Configuration de BizTalk MQSeries Agent** n’est pas sélectionnée.  
  
    > [!NOTE]
    >  Le **MQSeries Agent** case à cocher est activée uniquement après l’IBM WebSphere MQ pour Windows est installé.  
  
3.  Ouvrir un **invite de commandes Visual Studio**, remplacez le répertoire par le \< *répertoire d’Installation IBM MQSeries*\>dossier \bin, puis exécutez la commande suivante :  
  
    -   `gacutil /i amqmdnet.dll`  
  
4.  Installez Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] si vous souhaitez installer Microsoft Host Integration Server 2004 pour accéder au macroordinateur. Le programme d’installation, sur le **Options** page, sélectionnez **Visual c# .NET**, puis désactivez les autres cases à cocher des composants. Vous n’avez pas besoin d’installer les autres composants que le **Visual c# .NET**.  
  
    > [!NOTE]
    >  Le Concepteur TI inclus dans Host Integration Server 2004 requiert [!INCLUDE[btsVStudioNet2003](../includes/btsvstudionet2003-md.md)].  
  
5.  Installez et configurez Microsoft Host Integration Server 2004 si vous avez un macroordinateur accessible. Conservez tous les paramètres par défaut.  
  
#### <a name="create-the-mqseries-queues"></a>Créer les files d’attente MQSeries  
  
1.  Ouvrez WebSphere MQ Explorer, développez **gestionnaires de file d’attente**, puis développez le Gestionnaire de file d’attente dans laquelle vous souhaitez créer les files d’attente. En règle générale, un gestionnaire de file d’attente est nommé QM_\<*nom de votre ordinateur*\>.  
  
2.  Dans WebSphere MQ Explorer, cliquez sur **les files d’attente**, pointez sur **nouveau**, cliquez sur **file d’attente locale**, puis créer les files d’attente locales suivantes pour la version de l’adaptateur de le solution :  
  
    -   AdapterSOAInputQueue  
  
    -   AdapterSOAOutputQueue  
  
    > [!NOTE]
    >  Les files d'attente peuvent partager un cluster MQSeries (facultatif).  
  
    > [!NOTE]
    >  Les noms des gestionnaires de file d'attente MQSeries et les noms des files d'attente respectent la casse.  
  
3.  Répétez l'étape précédente pour créer les files d'attente locales suivantes pour la version Inline :  
  
    -   InlineSOAOutputQueue  
  
    -   InlineSOAInputQueue  
  
4.  Répétez l'étape précédente pour créer les files d'attente locales suivantes pour le simulateur Payment Tracker (ce dispositif est utilisé à la fois dans la version d'adaptateur et dans la version Inline) :  
  
    -   LastPaymentsInputQueue  
  
    -   LastPaymentsOutputQueue  
  
#### <a name="complete-configuration-of-the-mqseries-adapter"></a>Terminer la configuration de l’adaptateur MQSeries  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Assistant Configuration de BizTalk MQSeries Agent**.  
  
2.  Sur le **Bienvenue** , cliquez sur **suivant**.  
  
3.  Sur le **identité de l’Application** page, sélectionnez **cet utilisateur**, puis entrez le nom d’utilisateur et un mot de passe. L'application COM+ pour MQSeries Agent est exécutée sous ce compte d'utilisateur. Dans le cadre de cette procédure pas à pas, vous devez utiliser le même compte d'utilisateur que celui utilisé par le service BizTalk. S’il n’est pas, les comptes d’utilisateur pour les services BizTalk hébergeant l’adaptateur MQSeries doivent être ajoutés à la **CreatorOwner** rôle de l’application COM +.  
  
4.  Cliquez sur **Oui** sur la **MQSConfigWiz** boîte de dialogue, si vous y êtes invité que le compte d’utilisateur que vous avez entré à l’étape précédente a des privilèges d’administrateur.  
  
5.  Sur le **nom du rôle** , cliquez sur **suivant**.  
  
6.  Sur le **création de l’Application MQSAgent COM +** , cliquez sur **suivant**, puis cliquez sur **Terminer** sur la **achèvement** page.  
  
#### <a name="configure-the-mainframe-cics-application"></a>Configurer l’application CICS du macroordinateur.  
  
1.  À l'aide du Bloc-notes, ouvrez le fichier bizcbl.txt, ainsi que le fichier associé MainFrameProgramVTCS2Description.txt, dans le dossier %BTSSolutionsPath%\SO\MFAccess\HISTIComponent, puis passez en revue leur contenu.  
  
    -   Bizcbl.txt inclut la procédure COBOL qui renvoie les relevés de compte aléatoires d'après une entrée de numéro de compte.  
  
    -   Le fichier MainFrameProgramVTCS2Description.txt contient la COMMAREA qui décrit les informations des données d'entrée et de sortie. La COMMAREA constitue un bloc de mémoire contiguë servant à échanger des données entre les programmes appelés et les programmes appelants.  
  
    > [!NOTE]
    >  Vous pouvez également utiliser le livre de copie pour générer le fichier de métadonnées de Transaction Integrator (TI) à l’aide de Visual Studio avec le concepteur TI plug-in.  
  
    > [!NOTE]
    >  Bien que les étapes suivantes soient essentielles à la réussite du déploiement, elles ne sont généralement pas effectuées par un développeur BizTalk Server. Il revient au personnel chargé de l'administration du macroordinateur de configurer correctement l'environnement du macroordinateur. Les logiciels requis dans le cadre de cette procédure pas à pas sont généralement installés dans la plupart des environnements de macroordinateur. Pour plus d’informations sur l’environnement de système d’exploitation minimale macroordinateur, consultez la documentation de Host Integration Server.  
  
2.  Copiez le code COBOL sur l'ordinateur hôte via FTP par exemple.  
  
3.  Compilez le code COBOL et le fichier associé. Le code suivant illustre un exemple de langage JCL (Job Control Language) utilisé par le compilateur COBOL.  
  
    ```  
    //COB      EXEC PGM=IGYCRCTL,  
    //            PARM=&COBPARM,  
    //            REGION=&REG  
    //STEPLIB  DD DSN=&COMPINDX..SIGYCOMP,DISP=SHR  
    //SYSLIB   DD DSN=&INDEX..SDFHCOB,DISP=SHR  
    //         DD DSN=&INDEX..SDFHMAC,DISP=SHR  
    //         DD DSN=&HLQ..&COMP..COBCOPY,DISP=SHR  
    //SYSPRINT DD SYSOUT=&OUTC  
    //*SYSPRINT DD DSN=&&INPUT,DISP=(,PASS),UNIT=SYSDA,  
    //*         SPACE=(TRK,(100,50)),  
    //*         DCB=(DSORG=PS,LRECL=121,BLKSIZE=2420,RECFM=FBA)  
    //SYSIN    DD DSN=&&SYSCIN,DISP=(OLD,DELETE)  
    //SYSLIN   DD DSN=&&LOADSET,  
    //            DISP=(MOD,PASS),  
    //            UNIT=&WORK,  
    //            SPACE=(80,(250,100))  
    //SYSUT1   DD UNIT=&WORK,SPACE=(460,(350,150))  
    //SYSUT2   DD UNIT=&WORK,SPACE=(460,(350,150))  
    //SYSUT3   DD UNIT=&WORK,SPACE=(460,(350,150))  
    //SYSUT4   DD UNIT=&WORK,SPACE=(460,(350,150))  
    //SYSUT5   DD UNIT=&WORK,SPACE=(460,(350,150))  
    //SYSUT6   DD UNIT=&WORK,SPACE=(460,(350,150))  
    //SYSUT7   DD UNIT=&WORK,SPACE=(460,(350,150))  
    ```  
  
4.  Éditez les liens de la source compilée pour créer l'exécutable. Le code suivant montre un exemple de langage JCL pour l'édition de liens COBOL.  
  
    ```  
    //LKED     EXEC PGM=IEWL,REGION=&REG,  
    //            PARM=&LNKPARM,COND=(5,LT,COB)  
    //SYSLIB   DD DSN=&INDEX..SDFHLOAD,DISP=SHR  
    //         DD DSN=CEE.SCEELKED,DISP=SHR  
    //         DD DSN=&TCPINDX..SEZATCP,DISP=SHR  
    //SYSLMOD  DD DSN=&LMINDX..&COMP..LOADLIB,DISP=SHR  
    //SYSUT1   DD UNIT=&WORK,  
    //            DCB=BLKSIZE=1024,  
    //            SPACE=(1024,(200,20))  
    //SYSPRINT DD SYSOUT=&OUTC  
    //SYSLIN   DD DSN=&&LOADSET,DISP=(OLD,DELETE)  
    //         DD DSN=&&COPYLINK,DISP=(OLD,DELETE)  
    ```  
  
5.  Configurez l'application de macroordinateur CICS.  
  
    -   Au cours de cette étape, le programmateur système du macroordinateur ou le développeur CICS doit installer les définitions de ressource relatives au service TCP/IP, aux sessions, aux connexions, aux transactions et aux programmes.  
  
    -   Consultez les administrateurs du macroordinateur pour obtenir l'adresse IP, le numéro de port et le nom de lien au programme auxquels accéder.  
  
        > [!NOTE]
        >  Cette procédure pas à pas implique que le macroordinateur exploite un serveur d'applications CICS et que le modèle de programmation de la transaction soit TCP/IP (lien ELM [Enhanced Listener Mode]).  
  
##  <a name="step7"></a>Configurer le serveur Web pour SSL Secure Socket Layers)  
  
#### <a name="install-certificate-services"></a>Installer les Services de certificats  
  
1.  Cliquez sur **Démarrer**, pointez sur **le panneau de configuration**, puis cliquez sur **Ajout / Suppression de programmes**.  
  
2.  Dans le **Ajout / Suppression de programmes** boîte de dialogue, cliquez sur **ajouter/supprimer des composants Windows**.  
  
3.  Dans le **Assistant Composants de Windows**, sélectionnez le **les Services de certificats**, cliquez sur **suivant**, puis suivez l’à l’écran des instructions pour terminer l’installation.  
  
#### <a name="create-a-certificate-request"></a>Créer une demande de certificat  
  
1.  Dans le **Gestionnaire des Services Internet (IIS)**, développez **Sites Web**, avec le bouton droit le **Site Web par défaut**, cliquez sur **propriétés** , cliquez sur le **sécurité du répertoire** onglet, puis cliquez sur **certificat de serveur**.  
  
2.  Sur le **Bienvenue** page de la **Assistant certificat de serveur Web**, cliquez sur **suivant**.  
  
3.  Sur le **certificat de Service** page, sélectionnez **créer un nouveau certificat**, puis cliquez sur **suivant**.  
  
4.  Sur le **demande ultérieure ou immédiate** , cliquez sur **préparer la demande maintenant, mais l’envoyer ultérieurement**, puis cliquez sur **suivant**.  
  
5.  Sur le **nom et les paramètres de sécurité** page, conservez tous les paramètres par défaut, puis cliquez sur **suivant**.  
  
6.  Sur le **informations de l’organisation** page, tapez votre organisation et noms de l’unité d’organisation, puis cliquez sur **suivant**.  
  
7.  Sur le **nom commun de votre Site** , tapez le nom de votre ordinateur dans le **nom commun** zone, puis cliquez sur **suivant**.  
  
8.  Sur le **informations géographiques** page, remplir vos informations géographiques, puis cliquez sur **suivant**.  
  
9. Sur le **nom du fichier de demande de certificat** , tapez `c:\certreq.txt` dans les **nom de fichier** zone, puis cliquez sur **suivant**.  
  
10. Sur le **résumé du fichier de demande** , cliquez sur **suivant**, puis cliquez sur **Terminer** sur la **achèvement** page.  
  
#### <a name="submit-the-certificate-request-to-the-certification-authority"></a>Soumettre la demande de certificat de l’autorité de Certification  
  
1.  Dans Internet Explorer, dans la zone Adresse, tapez `http://localhost/certsrvt`, puis appuyez sur ENTRÉE.  
  
2.  Sur le **Bienvenue** , cliquez sur **demander un certificat**, puis cliquez sur **demande de certificat avancée** sur la **demander un certificat** page.  
  
3.  Sur le **demande de certificat avancée** , cliquez sur **soumettre une demande de certificat à l’aide de base64 encodé PKCS #10 ou une demande de renouvellement à l’aide d’un fichier de PKCS #7 codé en base64**.  
  
4.  Copiez le texte à partir de la c:\certreq.txt que vous avez créé dans la procédure « pour créer d’une demande de certificat », collez-le dans le **demande enregistrée** zone sur le **soumettre une demande de certificat ou une demande de renouvellement** page, puis cliquez sur **Submit**.  
  
#### <a name="issue-a-certificate-using-certification-authority-management-tool"></a>Émettre un certificat à l’aide d’outil de gestion d’autorité de Certification  
  
1.  Cliquez sur **Démarrer**, pointez sur **outils d’administration**, puis cliquez sur **autorité de Certification**.  
  
2.  Dans le **autorité de Certification** de la console, développez le nom de votre autorité de certification, le **demande en attente**, avec le bouton droit de la demande de certificat que vous avez envoyé à l’étape précédente, le point pour **toutes les tâches**, puis cliquez sur **problème**.  
  
3.  Fermer le **autorité de Certification** console.  
  
#### <a name="download-the-certificate-to-the-web-server"></a>Téléchargez le certificat sur le serveur Web  
  
1.  Dans Internet Explorer, dans la zone Adresse, tapez `http://localhost/certsrvt`, puis appuyez sur ENTRÉE.  
  
2.  Sur le **Bienvenue** , cliquez sur **afficher l’état d’une demande de certificat en attente**.  
  
3.  Sur le **afficher l’état d’une demande de certificat en attente** , cliquez sur le certificat **demande** que vous avez créé dans la procédure « pour créer une demande de certificat ».  
  
4.  Sur le **délivré** page, sélectionnez un des schémas d’encodage, puis cliquez sur **télécharger le certificat**.  
  
5.  Sur le **avertissement de sécurité** boîte de dialogue, cliquez sur **enregistrer**, puis enregistrez le certificat sous c:\certnew.cer.  
  
#### <a name="install-the-certificate-to-the-web-server"></a>Installez le certificat pour le serveur Web  
  
1.  Dans le **Gestionnaire des Services Internet (IIS)**, développez **Sites Web**, avec le bouton droit le **Site Web par défaut** pour lequel vous avez créé la demande de certificat, puis Cliquez sur **propriétés**.  
  
2.  Sur le **propriétés** boîte de dialogue, cliquez sur le **sécurité du répertoire** onglet, puis cliquez sur **certificat de serveur**.  
  
3.  Sur le **Bienvenue** page de la **Assistant certificat de serveur Web**, cliquez sur **suivant**.  
  
4.  Sur le **demande de certificat en attente** page, sélectionnez **traiter la demande en attente et installer le certificat**, puis cliquez sur **suivant**.  
  
5.  Sur le **traiter une demande en attente** , tapez `c:\certnew.cer` dans les **chemin d’accès et nom de fichier** zone de texte, puis cliquez sur **suivant**.  
  
6.  Cliquez sur **suivant** sur la **Port SSL** , cliquez sur **suivant** sur la **résumé du certificat** page, puis cliquez sur **Terminer** sur la **Confirmation** page.  
  
    > [!NOTE]
    >  Au cours de cette procédure pas à pas, il n'est pas nécessaire d'installer le certificat de serveur dans le magasin d'autorités de certification de racine de confiance de l'ordinateur local car les services de certificats et le serveur Web sont installés sur le même ordinateur.  
  
##  <a name="step9"></a>Créer des services Web pour les systèmes back-end  
  
1.  Dans le **Gestionnaire des Services Internet (IIS)**, avec le bouton droit **Pools d’applications**, sélectionnez **nouveau**, puis sélectionnez **Poold’applications**.  
  
    > [!NOTE]
    >  La solution orientée services accède au macroordinateur via ce service Web.  
  
2.  Sur le **Ajouter nouveau Pool d’applications** boîte de dialogue, entrez le **ID du pool d’applications** (toute valeur), puis cliquez sur **OK**.  
  
3.  Dans le **Gestionnaire des Services Internet (IIS)**, cliquez sur le pool d’applications que vous venez de créée, puis sélectionnez **propriétés**.  
  
4.  Sur le **propriétés** , cliquez sur le **identité** onglet, sélectionnez **Configurable**, entrez la **nom d’utilisateur** et **mot de passe** , puis cliquez sur **OK**. Dans le cadre de cette procédure pas à pas, vous devez utiliser le même compte d'utilisateur que celui utilisé par le service BizTalk.  
  
#### <a name="create-the-pendingtransactions-web-service-for-runtime"></a>Créer le service PendingTransactions Web pour l’exécution  
  
1.  Dans le **Gestionnaire des Services Internet (IIS)**, développez **Sites Web**, avec le bouton droit le **Site Web par défaut**, pointez sur **nouveau**, et puis cliquez sur **répertoire virtuel** pour exécuter **Assistant de création de répertoire virtuel**.  
  
     À l’aide de la **Assistant de création de répertoire virtuel**, créez le répertoire virtuel suivant pour le service Web SAP stub :  
  
     Alias = Microsoft.Samples.BizTalk.WoodgroveBank.PendingTransactions  
  
     Chemin d’accès = \< *répertoire d’installation de BizTalk*\>\SDK\Scenarios\SO\MFAccess\PendingTransactions  
  
     Access Permissions = Read, Run scripts  
  
2.  Dans le **Gestionnaire des Services Internet (IIS)**, développez **Sites Web**, développez le **Site Web par défaut**, avec le bouton droit Microsoft.Samples.BizTalk.WoodgroveBank.PendingTransactions, puis cliquez sur **propriétés**.  
  
    1.  Dans le **sécurité du répertoire** , cliquez sur **modifier** modifier **d’authentification et contrôle d’accès**. Sélectionnez **l’authentification de base (mot de passe est envoyé en texte clair)**et désactivez les autres **d’accès d’authentification** cases à cocher. Cliquez sur **OK** pour fermer la **les méthodes d’authentification** boîte de dialogue.  
  
    2.  Dans le **sécurité du répertoire** , cliquez sur **modifier** sous le **une Communication sécurisée** zone de groupe, puis vérifiez **requérir un canal sécurisé (SSL)**dans les **Communications sécurisées** boîte de dialogue.  
  
    3.  Dans le **répertoire virtuel** onglet, définissez la **Pool d’applications** au pool d’applications que vous avez créé dans la procédure « pour créer un nouveau pool d’applications IIS pour les services Web Pending transactions ».  
  
#### <a name="create-the-pendingtransactions-web-service-for-development-environment"></a>Créer le service PendingTransactions Web pour l’environnement de développement  
  
1.  Dans le **Gestionnaire des Services Internet (IIS)**, développez **Sites Web**, avec le bouton droit le **Site Web par défaut**, pointez sur **nouveau**, et puis cliquez sur **répertoire virtuel** pour exécuter **Assistant de création de répertoire virtuel**.  
  
     À l’aide de la **Assistant de création de répertoire virtuel**, créez le répertoire virtuel suivant pour le service Web SAP stub :  
  
     Alias = PendingTransactions  
  
     Chemin d’accès = \< *répertoire d’installation de BizTalk*\>\SDK\Scenarios\SO\MFAccess\PendingTransactions  
  
     Access Permissions = Read, Run scripts  
  
2.  Dans le **Gestionnaire des Services Internet (IIS)**, développez **Sites Web**, développez le **Site Web par défaut**, cliquez sur PendingTransactions, puis cliquez sur **Propriétés**.  
  
    1.  Dans le **sécurité du répertoire** , cliquez sur **modifier** modifier **d’authentification et contrôle d’accès**. Sélectionnez **activer l’accès anonyme**. Cliquez sur **OK** pour quitter.  
  
        > [!NOTE]
        >  L'application Web PendingTransactions pour l'environnement de développement sera utilisée par [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]. Cette application Web n'est pas requise pour l'environnement de production.  
  
    2.  Dans le **répertoire virtuel** onglet, définissez la **Pool d’applications** au pool d’applications que vous avez créé dans la procédure « pour créer un nouveau pool d’applications IIS pour les services Web Pending transactions ».  
  
#### <a name="create-the-stub-sap-web-service"></a>Créer le service Web SAP Stub  
  
1.  Dans le **Gestionnaire des Services Internet (IIS)**, développez **Sites Web**, avec le bouton droit le **Site Web par défaut**, pointez sur **nouveau**, et puis cliquez sur **répertoire virtuel** pour exécuter **Assistant de création de répertoire virtuel**.  
  
     À l’aide de la **Assistant de création de répertoire virtuel**, créez le répertoire virtuel suivant pour le service Web SAP stub :  
  
     Alias = Microsoft.Samples.BizTalk.WoodgroveBank.StubSAP  
  
     Chemin d’accès = \< *répertoire d’installation de BizTalk*\>\SDK\Scenarios\SO\BTSSoln\StubWebServices\SAP  
  
     Access Permissions = Read, Run scripts  
  
2.  Dans le **Gestionnaire des Services Internet (IIS)**, développez **Sites Web**, développez le **Site Web par défaut**, avec le bouton droit Microsoft.Samples.BizTalk.WoodgroveBank.StubSAP, cliquez sur **propriétés**, puis modifiez les paramètres comme suit :  
  
    1.  Dans le **répertoire virtuel** onglet, définissez la **Pool d’applications** à \< *YourAppPool* \> que vous avez créé dans la procédure « pour créer un nouveau serveur IIS pool d’applications pour les services Web Pending transactions ».  
  
    2.  Dans le **sécurité du répertoire** , cliquez sur **modifier** dans les **d’authentification et contrôle d’accès** zone de groupe, puis sélectionnez **activer l’accès anonyme**. Cliquez sur **OK** pour quitter.  
  
##  <a name="step11"></a>Créer le composant TI pour la Solution orientée services  
  
#### <a name="create-a-com-application-for-the-ti-component"></a>Créer une application COM + pour le composant TI  
  
1.  Ouvrez une invite de commandes, puis exécutez %systemroot%\system32\com\comexp.msc.  
  
2.  Dans **Services de composants** de la console, développez **Services de composants**, développez **ordinateurs**, développez **poste**, avec le bouton droit  **L’Application COM +**, pointez sur **nouveau**, puis cliquez sur **Application**.  
  
    1.  Sur le **Bienvenue** , cliquez sur **suivant**, puis cliquez sur **créer une application vide** sur la **installer ou créer une nouvelle Application** page.  
  
    2.  Type `BTSScn SO TI Component` dans les **Entrez un nom pour la nouvelle application** boîte, sélectionnez **application serveur** en tant que **type d’Activation**, puis cliquez sur **suivant**.  
  
    3.  Dans le **compte** zone de groupe de la **définir l’identité Application** page, sélectionnez **cet utilisateur**, puis tapez le nom d’utilisateur et un mot de passe dans la **utilisateur**et **mot de passe** cases. La nouvelle application COM+ sera exécutée sous ce compte d'utilisateur. Celui-ci doit appartenir au groupe d'utilisateurs HIS Runtime locaux. Dans le cadre de cette procédure pas à pas, vous devez utiliser le même compte d'utilisateur que celui utilisé par le service BizTalk.  
  
    4.  Sur le **ajouter des rôles d’Application** , cliquez sur **suivant**.  
  
    5.  Sur le **ajouter des utilisateurs aux rôles** page, développez **CreatorOwner**, cliquez sur **utilisateurs**, puis cliquez sur **ajouter**.  
  
    6.  Sur le **sélectionner des utilisateurs ou groupes** boîte de dialogue, sélectionnez un compte d’utilisateur qui sera utilisé pour accéder au macroordinateur. Dans le cadre de cette procédure pas à pas, ajoutez le compte local UserID.  
  
        > [!NOTE]
        >  Pour accéder à la transaction CICS via le composant TI, vous pouvez utiliser l'application COM+ ou l'application Web hébergeant le composant d'accès à distance .NET. Cette procédure pas à pas utilise l'application COM+ et COM Interop pour permettre aux composants TI d'accéder au macroordinateur à des fins d'amélioration des performances.  
  
    7.  Sur le **achèvement** , cliquez sur **Terminer**.  
  
#### <a name="create-a-remote-environment-to-access-the-mainframe"></a>Créer un environnement à distance pour accéder au macroordinateur  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft Host Integration Server 2004**, puis cliquez sur **Gestionnaire TI**.  
  
2.  Dans le **Gestionnaire TI** de la console, cliquez sur **intégrateur de transactions (Configuration)**, développez **traitement initié par Windows**, avec le bouton droit **à distance Environnements**, pointez sur **nouveau**, puis cliquez sur **environnement distant**.  
  
    1.  Sur le **Bienvenue** , cliquez sur **suivant**.  
  
    2.  Sur le **configurer un nouvel environnement distant** , tapez le **nom de l’Application à distance**, puis cliquez sur **suivant**. Dans le cadre de cette procédure pas à pas, utilisez le nom Mainframe_TCP.  
  
    3.  Sur le **configurer l’environnement hôte et le modèle de programmation** page, sélectionnez **CICS** pour le **hôte cible** et **lien ELM** pour la  **Modèle de programmation**, puis cliquez sur **suivant**.  
  
    4.  Sur **le point de terminaison configurer TCP/IP** , tapez l’adresse IP du macroordinateur dans le **adresse IP/DNS** zone, puis cliquez sur **modifier** pour ajouter le numéro de port. Le HIS COM accèdera aux transactions via l'adresse du point de terminaison.  
  
    5.  Sur le **achèvement** , cliquez sur **Terminer**.  
  
#### <a name="create-the-ti-component-for-the-service-oriented-solution"></a>Créer le composant TI pour la Solution orientée services  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft Host Integration Server 2004**, puis cliquez sur **Gestionnaire TI**.  
  
2.  Dans le **Gestionnaire TI** de la console, cliquez sur **intégrateur de transactions (Configuration)**, cliquez sur **traitement initié par Windows**, puis cliquez sur **objets**. Avec le bouton droit **objets**, cliquez sur **nouveau**, puis cliquez sur **objet**.  
  
    1.  Sur le **Bienvenue** , cliquez sur **suivant**.  
  
    2.  Sur le **spécifier ou rechercher un objet** , cliquez sur **Parcourir**, choisissez l’objet SOHISTIUsingCOM.TLB dans le dossier %BTSSolutionsPath%\SO\MFAccess\HISTIComponent, puis cliquez sur **suivant**.  
  
    3.  Sur le **caractéristiques de l’environnement définir pour l’objet COM** page, sélectionnez **BTSScn SO TI Component** pour le **l’application COM +**, puis cliquez sur **suivant** .  
  
    4.  Sur le **définir l’environnement distant** , sélectionnez l’environnement distant que vous avez créé dans la procédure précédente pour le **environnement distant, puis cliquez sur Suivant.**  
  
    5.  Sur le **création d’objets WIP** , cliquez sur **suivant**, puis cliquez sur **Terminer** sur la **achèvement** page.  
  
#### <a name="test-the-connectivity-to-the-mainframe"></a>Tester la connectivité au macroordinateur  
  
1.  Dans l'Explorateur Windows, accédez au dossier %BTSSolutionsPath%\SO\MFAccess\HISTISimpleTester, puis double-cliquez sur le fichier Interop.SOHISTIUsingCOM.dll.reg. Cette action a pour effet d'ajouter des valeurs correspondant à l'application HISTISimpleTester au Registre afin d'appeler le composant TI via le wrapper RCW (Runtime Callable Wrapper).  
  
2.  Dans l'Explorateur Windows, accédez au dossier %BTSSolutionsPath%\SO\MFAccess\, puis exécutez SetupMFAccess.bat.  
  
3.  Dans l'Explorateur Windows, accédez au dossier %BTSSolutionsPath%\SO\MFAccess\HISTISimpleTester\bin\Debug, puis exécutez BTSScnSOHISTIComponentSimpleTester.exe.  
  
    -   Dans l’application HISTISimpleTester, cliquez sur **appeler le programme du macroordinateur - utiliser COM**. Cinq enregistrements sont renvoyés de l'application COBOL exécutée sur le macroordinateur.  
  
##  <a name="step13"></a>Créer les répertoires virtuels pour l’orchestration des services Web  
  
1.  Dans le **Gestionnaire des Services Internet (IIS)**, avec le bouton droit **Pools d’applications**, sélectionnez **nouveau**, puis sélectionnez **Poold’applications**.  
  
    1.  Sur le **Ajouter nouveau Pool d’applications** boîte de dialogue, entrez le **ID du pool d’applications** (toute valeur), puis cliquez sur **OK**.  
  
    2.  Cliquez sur le pool d’applications que vous venez de créée, puis sélectionnez **propriétés**.  
  
    3.  Sur le **propriétés** , cliquez sur le **identité** onglet, sélectionnez **Configurable**, entrez la **nom d’utilisateur** et **mot de passe** , puis cliquez sur **OK**. Pour cette procédure pas à pas utiliser le même compte d’utilisateur qui utilise le service BizTalk.  
  
    > [!NOTE]
    >  Cet utilisateur doit être autorisé à exécuter le service Web Orchestration Proxy et être ajouté au groupe Administrateurs BizTalk Server, Administrateurs de l'authentification unique ou Administrateurs d'applications associées à authentification unique.  
  
2.  Dans le **Gestionnaire des Services Internet (IIS)**, développez **Sites Web**, avec le bouton droit le **Site Web par défaut**, pointez sur **nouveau**, et puis cliquez sur **répertoire virtuel** pour exécuter **Assistant de création de répertoire virtuel**.  
  
     À l’aide de la **Assistant de création de répertoire virtuel**, créez le répertoire virtuel suivant pour le proxy de service Web pour la version d’adaptateur :  
  
     Alias = Microsoft.Samples.BizTalk.WoodgroveBank.OrchProxy.Adapter  
  
     Chemin d’accès = \< *répertoire d’installation de BizTalk*\>\SDK\Scenarios\SO\BTSSoln\OrchProxy\Adapter  
  
     Access Permissions = Read, Run scripts  
  
3.  Dans le **Gestionnaire des Services Internet (IIS)**, développez **Sites Web,** développer le **Site Web par défaut**, avec le bouton droit Microsoft.Samples.BizTalk.WoodgroveBank.OrchProxy.Adapter, cliquez sur **propriétés**, puis modifiez les paramètres comme suit :  
  
    1.  Dans le **répertoire virtuel** onglet, définissez la **Pool d’applications** à \< *YourAppPool* \> que vous avez créé à l’étape précédente.  
  
    2.  Dans le **sécurité du répertoire** , cliquez sur **modifier** dans les **d’authentification et contrôle d’accès** zone de groupe, sélectionnez **uniquement l’authentification Windows intégrée activé**, puis désactivez les autres **d’accès d’authentification** cases à cocher. Cliquez sur **OK** pour quitter.  
  
4.  Dans le **Gestionnaire des Services Internet (IIS)**, développez **Sites Web**, avec le bouton droit le **Site Web par défaut**, pointez sur **nouveau**, et puis cliquez sur **répertoire virtuel** pour exécuter **Assistant de création de répertoire virtuel**.  
  
     À l’aide de la **Assistant de création de répertoire virtuel**, créez le répertoire virtuel suivant pour le proxy de service Web pour la version inline :  
  
     Alias = Microsoft.Samples.BizTalk.WoodgroveBank.OrchProxy.Inline  
  
     Chemin d’accès = \< *répertoire d’installation de BizTalk*\>\SDK\Scenarios\SO\BTSSoln\OrchProxy\Inline  
  
     Access Permissions = Read, Run scripts  
  
5.  Dans le **Gestionnaire des Services Internet (IIS)**, développez **Sites Web**, développez le **Site Web par défaut**, avec le bouton droit Microsoft.Samples.BizTalk.WoodgroveBank.OrchProxy.Inline, cliquez sur **propriétés**, puis modifiez les paramètres comme suit :  
  
    1.  Sur le **répertoire virtuel** onglet, définissez la **Pool d’applications** à \< *YourAppPool* \> vous venez de créer.  
  
    2.  Cliquez sur **sécurité du répertoire** , cliquez sur **modifier** dans les **d’authentification et contrôle d’accès** zone de groupe, sélectionnez **uniquement l’authentification Windows intégrée activé**, puis désactivez les autres **d’accès d’authentification** cases à cocher. Cliquez sur **OK** pour quitter.  
  
##  <a name="step15"></a>Générez la Solution orientée services  
  
-   À l’invite de commandes, accédez au répertoire % BTSSolutionsPath%\SO\BTSSoln, tapez `SetupBTSSoln.bat`, puis appuyez sur ENTRÉE. La commande SetupBTSSoln.bat effectue les tâches suivantes :  
  
    -   Crée une clé de nom fort unique (SNK) pour signer les assemblys de la solution orientée services.  
  
    -   extraction du jeton de clé publique de la clé de nom fort et mise à jour des fichiers de liaison avec le jeton public ;  
  
    -   création de la solution orientée services ;  
  
    -   création de SSOApplicationConfig dans le dossier %BTSSolutionsPath%\Common.  
  
##  <a name="step17"></a>Créer des applications associées SSO  
  
1.  Ouvrez une invite de commandes, puis accédez au répertoire %BTSSolutionsPath%\SO\BTSSoln\Scripts.  
  
2.  À l'invite de commandes, ouvrez le fichier PendTransAffApp.xml à l'aide du Bloc-notes, puis passez-le en revue. Il n'est pas nécessaire de modifier ce fichier.  
  
    > [!NOTE]
    >  Le fichier PendTransAffApp.xml définit l'application associée SSO (WoodgroveBank.PendingTransactions) pour le système principal Pending Transactions. Il définit également les groupes d'utilisateurs et les groupes d'administration pour l'application associée SSO. Pour cette procédure pas à pas, utilisez **utilisateurs d’applications BizTalk** et **administrateurs de BizTalk Server**.  
    >   
    >  Si vous souhaitez utiliser d’autres groupes pour l’application associée SSO, vous devez créer des groupes Windows (avec n’importe quel nom) dans Active Directory et modifier le **appAdminAccount** et **appUserAccount** nœuds dans le fichier PendTransAffApp.xml. Si vous faites cela, vous devez définir la valeur de **groupApp** attribut de **indicateurs** nœud sur « yes ».  
    >   
    >  Pour plus d’informations sur les applications associées SSO, consultez [Applications associées SSO](../core/sso-affiliate-applications.md).  
  
3.  À l'invite de commandes, ouvrez le fichier PendTransUserMap.xml à l'aide du Bloc-notes, puis effectuez les modifications suivantes :  
  
    ```  
    <mapping>  
      <windowsDomain><DomainName></windowsDomain>  
      <windowsUserId><UserID></windowsUserId>  
      <externalUserId><ExternalUserID></externalUserId>  
    </mapping>  
    ```  
  
    > [!NOTE]
    >  Le fichier PendTransUserMap.xml contient les mappages utilisateur du système principal Pending Transactions.  
  
    > [!NOTE]
    >  Pour le **externalUserId** nœud, utilisez l’ID utilisateur externe pour le système principal Pending Transactions. Dans le cadre de cette procédure pas à pas, utilisez l'ID externe UserID.  
  
    > [!NOTE]
    >  Pour le **windowsUserId** nœud, entrez le nom d’utilisateur nom qui le **externalUserId** sont mappés à. Vous pouvez utiliser un groupe de domaine et un compte d'utilisateur de domaine. L'utilisateur doit faire partie d'un groupe autorisé à utiliser le système principal Pending Transactions. Dans le cadre de cette procédure pas à pas, utilisez le nom d'utilisateur du service BizTalk.  
  
    > [!NOTE]
    >  Pour le **windowsDomain** nœud, entrez le nom de domaine de la **windowsUserId**.  
  
4.  À l'invite de commandes, ouvrez le fichier PmntTrckAffApp.xml à l'aide du Bloc-notes, puis passez en revue le contenu du fichier. Il n'est pas nécessaire de modifier ce fichier.  
  
    > [!NOTE]
    >  Le fichier PmntTrckAffApp.xml définit l'application associée SSO (WoodgroveBank.PaymentTracker) pour le système principal Payment Tracker.  
  
5.  À l'invite de commandes, ouvrez le fichier PmntTrckUserMap.xml à l'aide du Bloc-notes, puis effectuez les modifications suivantes :  
  
    ```  
    <mapping>  
      <windowsDomain><DomainName></windowsDomain>  
      <windowsUserId><UserID></windowsUserId>  
      <externalUserId><ExternalUserID></externalUserId>  
    </mapping>  
    ```  
  
    > [!NOTE]
    >  L'application associée SSO Payment Tracker sera utilisée pour l'adaptateur MQSeries. L'ID utilisateur externe/le mot de passe mappés sont envoyés via les propriétés d'en-tête de MQSeries. Le serveur MQSeries valide uniquement le compte de service BizTalk, sous lequel l'adaptateur MQSeries est exécuté. Il ne valide pas les informations d'identification de l'utilisateur externe.  
    >   
    >  Pour plus d’informations sur l’authentification unique applications associées pour l’adaptateur MQSeries, consultez [comment configurer les emplacements de réception de la carte de MQSeries et les Ports d’envoi](../core/how-to-configure-mqseries-adapter-receive-locations-and-send-ports.md).  
  
    > [!NOTE]
    >  Le fichier PmntTrckUserMap.xml contient les mappages utilisateur SSO pour le système principal Payment Tracker. Le programme de simulation Payment Tracker permet de recréer les conditions de réussite et d'échec de l'authentification des utilisateurs.  
    >   
    >  Le programme authentifie correctement tous les ID d’utilisateur qui commencent par les lettres **PT** (par exemple, **PTUserID**) et ne parvient pas à authentifier les ID d’utilisateur qui ne commencent pas par **PT**. Vous pouvez ainsi choisir l'ID utilisateur approprié en fonction de la condition que vous voulez tester. Vous pouvez également répéter l’intégralité **mappage** nœud pour chaque ID d’utilisateur et définir plusieurs mappages dans le même fichier.  
  
    > [!NOTE]
    >  Pour le **externalUserId** nœud, entrez l’ID utilisateur externe pour le système principal Payment Tracker. Dans le cadre de cette procédure pas à pas, utilisez l'ID externe PTUserID.  
  
    > [!NOTE]
    >  Pour le **windowsUserId** nœud, entrez le nom d’utilisateur nom qui le **externalUserId** sont mappés à. L'utilisateur doit faire partie d'un groupe qui est autorisé à utiliser le système principal Payment Tracker. Dans le cadre de cette procédure pas à pas, utilisez le nom d'utilisateur du service BizTalk.  
  
    > [!NOTE]
    >  Pour le **windowsDomain** nœud, entrez le nom de domaine de la **windowsUserId**.  
  
6.  À l'invite de commandes, ouvrez le fichier ConfigStoreApp.xml à l'aide du Bloc-notes, puis passez en revue le contenu du fichier.  
  
     Ce fichier définit l'application de magasin de configuration dans SSO que le scénario utilise pour conserver les paramètres de configuration. Certains de ces paramètres incluent une valeur de délai d'expiration lors de la communication avec SAP (à la fois pour la version d'adaptateur et pour la version Inline), le nom du gestionnaire de file d'attente, ainsi que les files d'attente à utiliser avec la version Inline. Il n'est pas nécessaire de modifier ce fichier.  
  
7.  À l'invite de commandes, ouvrez le fichier SetConfigValuesInSSO.cmd à l'aide du Bloc-notes, puis examinez et modifiez son contenu selon le tableau suivant.  
  
    > [!NOTE]
    >  Ce fichier de commande définit les valeurs des paramètres de configuration dans la base de données SSO. Il contient plusieurs commandes Set qui attribuent les valeurs à des variables locales au début du fichier de commande.  
    >   
    >  Les valeurs SAPAdapterTimeout, PendingTransactionsAdapterTimeout et PaymentTrackingAdapterTimeout sont utilisées dans la version d'adaptateur. Les valeurs restantes sont utilisées dans la version Inline.  
  
    > [!NOTE]
    >  Vous pouvez entrer « » (deux guillemets doubles) pour les valeurs par défaut marquées \<spécifié par l’utilisateur\> dans le tableau suivant.  
  
    |Paramètre|Valeur par défaut| Description|  
    |---------------|-------------------|-----------------|  
    |SAPAdapterTimeout|20000|Délai d'attente maximal (en millisecondes) avant l'expiration d'une demande effectuée auprès du système principal SAP|  
    |SAPInlineTimeout|20000|Délai d'attente maximal (en millisecondes) avant l'expiration d'une demande effectuée auprès du système principal SAP|  
    |SAPInlineHostName|\<Utilisateur spécifié\>|Identificateur principal SAP|  
    |SAPInlineClientNumber|\<Utilisateur spécifié\>|Numéro de client SAP|  
    |SAPInlineSystemNumber|\<Utilisateur spécifié\>|Numéro de système SAP|  
    |SAPInlineUserName|\<Utilisateur spécifié\>|Nom d'utilisateur permettant de se connecter au système principal SAP|  
    |SAPInlinePassword|\<Utilisateur spécifié\>|Mot de passe permettant de se connecter au système principal SAP|  
    |PendingTransactionsAdapterTimeout|20000|Délai d'attente maximal (en millisecondes) avant l'expiration d'une demande effectuée auprès du serveur Pending Transactions|  
    |PendingTransactionsInlineTimeout|20000|Délai d'attente maximal (en millisecondes) avant l'expiration d'une demande effectuée auprès du serveur Pending Transactions|  
    |PendingTransactionsInlineURL|https://\<*nom de votre ordinateur*\>/Microsoft.Samples.BizTalk.WoodgroveBank.PendingTransactions/PendTransWS.asmx|URL du service Pending Transactions. \<*Nom de votre ordinateur* \> doit correspondre à la **nom commun** dans la procédure « pour créer une demande de certificat ». Vous ne devez pas utiliser « localhost » pour \< *nom de votre ordinateur*\>.|  
    |PendingTransactionsInlineSSOAffiliateApp|WoodgroveBank.PendingTransactions|Nom de l'application SSO Pending Transactions|  
    |PaymentTrackingAdapterTimeout|20000|Délai d'attente maximal (en millisecondes) avant l'expiration d'une demande effectuée auprès du système Payment Tracking|  
    |PaymentTrackingInlineTimeout|20000|Délai d'attente maximal (en millisecondes) avant l'expiration d'une demande effectuée auprès du système Payment Tracking|  
    |PaymentTrackingInlineQManager|\<Utilisateur spécifié\> (généralement QM_\<*nom de votre ordinateur*\>).|Nom du gestionnaire de file d'attente MQSeries|  
    |PaymentTrackingInlineMQChannelDefinition|" " (vous devez entrer deux guillemets doubles).|Chaîne vide si local, ou nom de chaîne formaté du serveur MQ distant. Si vous conservez tous les paramètres par défaut de la configuration d’IBM WebSphere MQ, la définition de la chaîne sera S__\<*nom de votre ordinateur*\>/TCP/\<*nom de votre ordinateur* \>(1414).|  
    |PaymentTrackingInlineRequestQueue|LastPaymentsInputQueue|Nom de la file d'attente MQ pour les demandes de Payment Tracking|  
    |PaymentTrackingInlineResponseQueue|LastPaymentsOutputQueue|Nom de la file d'attente MQ pour les réponses de Payment Tracking|  
    |PaymentTrackingInlineSSOAffiliateApp|WoodgroveBank.PaymentTracker|Nom de l'application SSO Payment Tracking|  
    |StubSAPWebServiceURL|http://localhost/Microsoft.Samples.BizTalk.WoodgroveBank.StubSAP/StubSAPWS.asmx|URL du service Web stub du système SAP Credit Limit|  
  
8.  À l'invite de commandes, exécutez la commande suivante pour définir l'environnement PATH :  
  
    -   `SET PATH=%PATH%;"%CommonProgramFiles%\Enterprise Single Sign-On"`  
  
9. À l'invite de commandes, exécutez la commande CreateInitialConfigInSSO.cmd. Celle-ci crée les applications associées SSO, l'application de magasin de configuration SSO et les mappages utilisateur des applications associées. Elle exécute ensuite SetConfigValuesInSSO.cmd pour stocker les valeurs de configuration dans l'application de magasin de configuration SSO.  
  
10. À l'invite de commandes, exécutez la commande suivante pour définir les informations d'identification de l'utilisateur de l'application associée Pending Transactions. Utilisez le \< **DomainName** \> et \< **UserID** \> défini dans le fichier PendTransUserMap.xml pour la \<WindowsDomain\> \\< WindowsUserId\>. Cette commande vous invite à entrer le mot de passe de l'utilisateur externe (UserID dans le cadre de cette procédure).  
  
    -   `ssomanage -setcredentials <WindowsDomain>\<WindowsUserId> WoodgroveBank.PendingTransactions`  
  
11. À l'invite de commandes, exécutez la commande suivante pour définir les informations d'identification de l'utilisateur de l'application associée Payment Tracker. Utilisez le \< **DomainName** \> et \< **UserID** \> défini dans le fichier PmntTrckUserMap.xml pour la \<WindowsDomain\> \\< WindowsUserId\>. Cette commande vous invite à entrer le mot de passe de l'utilisateur externe (PTUserID dans le cadre de cette procédure).  
  
    > [!NOTE]
    >  Le simulateur Payment Tracker ne valide pas les informations d'identification de l'utilisateur externe. Vous pouvez entrer n'importe quel mot de passe pour l'utilisateur PTUserID.  
  
    -   `ssomanage -setcredentials < WindowsDomain >\< WindowsUserId > WoodgroveBank.PaymentTracker`  
  
##  <a name="step19"></a>Déployer le fichier de définition BAM pour la Solution orientée services  
  
1.  Ouvrez une invite de commandes, tapez la commande suivante, puis appuyez sur ENTRÉE pour définir le chemin d'accès des utilitaires BAM :  
  
    -   SET PATH=%PATH%;[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking"  
  
2.  À l'invite de commandes, accédez au répertoire %BTSSolutionsPath%\SO\BTSSoln\BAM, tapez la commande suivante, puis appuyez sur ENTRÉE :  
  
    -   `bm deploy-all -DefinitionFile:ServiceLevelTracking.xml`  
  
##  <a name="step21"></a>Déployer la Solution orientée services  
  
#### <a name="update-the-binding-files-for-the-service-oriented-solution"></a>Mettre à jour les fichiers de liaison pour la Solution orientée services  
  
1.  Ouvrez une invite de commandes, accédez au répertoire %BTSSolutionsPath%\SO\BTSSoln\Scripts, ouvrez le fichier Deployallbinding.xml à l'aide du Bloc-notes, puis effectuez les modifications suivantes :  
  
    -   Remplacez le nom du serveur dans les variables SET MGMT_DB_SERVER et MBMT_DB par les noms du serveur et de la base de données utilisés par BizTalk Server.  
  
    -   Remplacez la valeur de la variable SOLNDIR par "%BTSSolutionsPath%\SO\BTSSoln".  
  
2.  À l'invite de commandes, accédez au répertoire %BTSSolutionsPath%\SO\BTSSoln\Bindings.  
  
3.  Pour la version d'adaptateur, ouvrez le fichier AdapterSOAOrchBindings.xml à l'aide du Bloc-notes, puis effectuez les modifications suivantes :  
  
    -   Remplacez toutes les occurrences de __MQ_SERVER_NAME\_ \_ avec le nom du serveur MQSeries.  
  
    -   Remplacez toutes les occurrences de __MQ_QMANAGER_NAME\_ \_ avec le nom du Gestionnaire de file d’attente MQSeries.  
  
    -   Remplacez toutes les occurrences de __PT_WS_SERVER_NAME\_ \_ dans la chaîne «\<adresse\>https://\__PT_WS_SERVER_NAME\_\_» avec le nom du serveur où l’en attente Service Web de transactions est déployé. Le nom du serveur doit correspondre à la **nom commun** à l’étape, « pour configurer le serveur Web pour SSL ». Vous ne devez pas utiliser « localhost ».  
  
    > [!NOTE]
    >  Le fichier de liaison, AdapterSOAOrchBindings.xml, utilise le service Web stub pour :  
    >   
    >  1.  le système principal SAP Credit Limit ;  
    > 2.  l'adaptateur MQSeries à des fins d'intégration au système principal Payment Tracking ;  
    > 3.  le service Web Pending Transactions pour appeler le composant .NET TI HIS à des fins d'intégration au système principal du macroordinateur.  
    >   
    >  Si vous ne disposez d'aucun macroordinateur, vous devez utiliser le service Web stub pour générer des données dans le système Pending Transactions.  
  
4.  Pour la version Inline, ouvrez le fichier InlineSOAOrchBindings.xml à l'aide du Bloc-notes, puis effectuez les modifications suivantes :  
  
    -   Remplacez toutes les occurrences de __MQ_SERVER_NAME\_ \_ avec le nom du serveur MQSeries.  
  
    -   Remplacez toutes les occurrences de __MQ_QMANAGER_NAME\_ \_ avec le nom du Gestionnaire de file d’attente MQSeries.  
  
#### <a name="deploy-the-service-oriented-solution"></a>Déployer la solution orientée services  
  
-   À l’invite de commandes, accédez au répertoire dans le dossier %BTSSolutionsPath%\SO\BTSSoln\Scripts, tapez la commande suivante, puis appuyez sur ENTRÉE.  
  
    -   `Deployallbinding.cmd`  
  
    > [!NOTE]
    >  La commande Deployallbinding.cmd crée l'application BizTalk appelée BTSScn.SO.CustomerService et importe les fichiers de liaison pour les versions d'adaptateur et Inline.  
  
##  <a name="step23"></a>Configurer le Services Web Pending Transactions stub lorsqu’un macroordinateur n’est pas disponible  
  
#### <a name="configure-the-stub-pending-transactions-web-service-for-using-the-adapter-version-without-a-mainframe"></a>Configurer le service Web Pending Transactions (pour utiliser la version d’adaptateur sans macroordinateur) stub  
  
1.  Dans le **Gestionnaire des Services Internet (IIS)**, développez **Sites Web**, avec le bouton droit le **Site Web par défaut**, pointez sur **nouveau**, et puis cliquez sur **répertoire virtuel** pour exécuter **Assistant de création de répertoire virtuel**.  
  
     À l’aide de la **Assistant de création de répertoire virtuel**, créez le répertoire virtuel suivant pour le service Web Pending Transactions pour la version d’adaptateur stub :  
  
     Alias = Microsoft.Samples.BizTalk.WoodgroveBank.StubPendingTransactions  
  
     Chemin d’accès = \< *répertoire d’installation de BizTalk*\>\SDK\Scenarios\SO\BTSSoln\StubWebServices\PendingTrans  
  
     Access Permissions = Read, Run scripts  
  
2.  Dans le **Gestionnaire des Services Internet (IIS)**, développez **Sites Web**, développez le **Site Web par défaut**, avec le bouton droit Microsoft.Samples.BizTalk.WoodgroveBank.StubPendingTransactions, cliquez sur **propriétés**, puis modifiez les paramètres comme suit à l’aide de la **propriétés** boîte de dialogue.  
  
    1.  Dans le **répertoire virtuel** onglet, définissez la **Pool d’applications** à \< *YourAppPool* \> vous avez créé à l’étape, « pour créer le serveur virtuel répertoires dans IIS pour la solution ».  
  
    2.  Dans le **sécurité du répertoire** , cliquez sur **modifier** dans les **d’authentification et contrôle d’accès** zone de groupe, puis sélectionnez **activer l’accès anonyme**. Cliquez sur **OK** pour quitter.  
  
3.  Dans le **Console d’Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, btsscn.so.CustomerService, puis **envoyer Ports**, avec le bouton droit **PendingTransactionSolicitResponsePort**, puis cliquez sur **propriétés**.  
  
    1.  Dans le **général** , cliquez sur **configurer** pour afficher les **propriétés du Transport** boîte de dialogue zone, puis modifiez le **URL du Service Web** à le stub Web en attente de Transaction de service, par exemple :  
  
         `http://localhost/Microsoft.Samples.BizTalk.WoodgroveBank.StubPendingTransactions/StubPendTransWS.asmx`  
  
    2.  Fermez toutes les boîtes de dialogue.  
  
#### <a name="configure-the-stub-pending-transactions-web-service-for-using-the-inline-version-without-a-mainframe"></a>Configurer le service Web Pending Transactions (pour utiliser la version inline sans macroordinateur) stub  
  
1.  Dans le **Gestionnaire des Services Internet (IIS)**, développez **Sites Web**, avec le bouton droit le **Site Web par défaut**, pointez sur **nouveau**, et puis cliquez sur **répertoire virtuel** pour exécuter **Assistant de création de répertoire virtuel**.  
  
     À l’aide de la **Assistant de création de répertoire virtuel**, créez le répertoire virtuel suivant pour le service Web Pending Transactions pour la version d’adaptateur stub :  
  
     Alias = Microsoft.Samples.BizTalk.WoodgroveBank.StubPendingTransactions  
  
     Chemin d’accès = \< *répertoire d’installation de BizTalk*\>\SDK\Scenarios\SO\BTSSoln\StubWebServices\PendingTrans  
  
     Access Permissions = Read, Run scripts  
  
2.  Dans le **Gestionnaire des Services Internet (IIS)**, développez **Sites Web**, développez le **Site Web par défaut**, avec le bouton droit Microsoft.Samples.BizTalk.WoodgroveBank.StubPendingTransactions, cliquez sur **propriétés**, puis modifiez les paramètres comme suit :  
  
    1.  Dans le **répertoire virtuel** onglet, définissez la **Pool d’applications** à \< *YourAppPool* \> vous avez créé à l’étape, « pour créer le serveur virtuel répertoires dans IIS pour la solution ».  
  
    2.  Dans le **sécurité du répertoire** , cliquez sur **modifier** dans les **d’authentification et contrôle d’accès** zone de groupe, puis sélectionnez **activer l’accès anonyme**. Cliquez sur **OK** pour quitter.  
  
3.  Ouvrez une invite de commandes, puis accédez au répertoire %BTSSolutionsPath%\SO\BTSSoln\Scripts.  
  
4.  À l’invite de commandes, ouvrez le fichier SetConfigValuesInSSO.cmd à l’aide du bloc-notes, puis définissez la valeur de la **PendingTransactionsInlineURL** à l’URL du Service Web Pending transactions stub.  
  
    -   `http://localhost/Microsoft.Samples.BizTalk.WoodgroveBank.StubPendingTransactions/StubPendTransWS.asmx`  
  
5.  À l'invite de commandes, tapez `SetConfigValuesInSSO.cmd`, puis appuyez sur ENTRÉE.  
  
##  <a name="step25"></a>Démarrer le Service orienté solutions  
  
1.  Ouvrez une invite de commandes, accédez au répertoire %BTSSolutionsPath%\SO\BTSSoln\Scripts, tapez la commande suivante, puis appuyez sur ENTRÉE pour démarrer toutes les orchestrations des versions d'adaptateur et Inline.  
  
    -   `startAll.vbs`  
  
2.  Exécutez la solution orientée services. Pour plus d’informations sur l’exécution de la solution, consultez [l’exécution de la Solution orientée services](../core/how-to-run-the-service-oriented-solution.md).  
  
## <a name="next-steps"></a>Étapes suivantes  
 Test de la version d’adaptateur et inline de la solution orientée services dans [l’exécution de la Solution orientée services](../core/how-to-run-the-service-oriented-solution.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Avant d’installer la Solution orientée services](../core/before-installing-the-service-oriented-solution.md)   
 [Pour installer la Version Stub de Service de la Solution orientée services](../core/how-to-install-the-stub-version-of-the-service-oriented-solution.md)   
 [Configuration de l’ordinateur de développement pour la solution orientée services](../core/developer-machine-setup-for-the-service-oriented-solution.md)