---
title: "Résolution des problèmes : Problèmes et Resolutions3 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: troubleshooting
ms.assetid: 40f59f54-183e-43db-afb5-0a45b437697f
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 68c63e7aeab46436e894d43d77b92a2a061d5b60
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="troubleshooting-issues-and-resolutions"></a>Résolution des problèmes : Problèmes et résolutions
Cette rubrique traite des problèmes liés à l’exécution [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]. La personne émet en détail un problème spécifique, des causes possibles et une solution.  
  
## <a name="error-publishing-a-batch-of-n-messages"></a>Erreur de publication d’un lot de messages « n »  
  
### <a name="symptom"></a>Symptôme  
 Vous recevez l’erreur suivante ou similaire dans le journal des événements :  
  
 Le moteur de messagerie a rencontré une erreur de publication d’un lot de messages de « n » à la base de données de la boîte de Message pour l’adaptateur de transport « Récepteur de HTTP BizTalk ». Reportez-vous à l’outil suivi des activités et des informations plus détaillées sur ce problème et vérifiez que les liaisons de point de terminaison sont correctement configurés.  
  
### <a name="possible-cause"></a>Cause possible  
 Cette erreur peut être causée par l'une des raisons suivantes :  
  
-   Certificat de déchiffrement manquant  
  
-   Incorrectement un message chiffré  
  
-   Message non autorisé (source ne pas reconnu comme un partenaire valide)  
  
-   Échec de validation de n’importe quelle partie de l’en-tête de message : préambule, en-tête de remise ou en-tête de service.  
  
 Ce message peut être précédé d’un autre message d’erreur qui explique la cause.  
  
### <a name="solution"></a>Solution  
 Passez en revue les détails fournis avec le message d’erreur pour obtenir une aide supplémentaire. Le redémarrage de [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]™ peut résoudre ce problème.  
  
## <a name="you-cannot-unenlist-all-artifacts"></a>Vous ne pouvez pas désinscrire tous les artefacts  
  
### <a name="symptom"></a>Symptôme  
 Exécute la [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]utilitaire de nettoyage de ne pas désinscrire tous les artefacts.  
  
### <a name="possible-cause"></a>Cause possible  
 Si vous exécutez le [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]nettoyer utilitaire avant de supprimer des contrats et les partenaires à partir de la [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® Management Console (MMC), l’utilitaire BtarnClean ne pourrez pas désinscrire tous les artefacts car elles sont toujours utilisées.  
  
### <a name="solution"></a>Solution  
  
##### <a name="to-remove-artifacts-using-the-loopback-utility"></a>Pour supprimer les artefacts à l’aide de l’utilitaire de bouclage  
  
1.  À l'invite de commandes, tapez :  
  
    ```  
    lookback.exe /disable <home org or partner>  
    ```  
  
2.  Exécutez le fichier BtarnClean.exe.  
  
3.  Dans l’Explorateur BizTalk, supprimez les parties.  
  
## <a name="installing-btarn-on-a-computer-without-biztalk-server-causes-missing-files"></a>Installation de BTARN sur un ordinateur sans BizTalk Server provoque des fichiers manquants  
  
### <a name="symptom"></a>Symptôme  
 L’exécution du fichier ConfigFramework.exe aboutit à aucun résultat sur un ordinateur qui n’a pas [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]BizTalk Server ou [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] installé. Vous pouvez utiliser uniquement cette [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] configuration comme un client HTTP.  
  
### <a name="possible-cause"></a>Cause possible  
 Deux fichiers DLL sont manquantes dans l’installation.  
  
### <a name="solution"></a>Solution  
 Installation de SQLXML sur l’ordinateur et ensuite copier manuellement les fichiers Msxml4.dll et Atl71.dll au dossier du système.  
  
## <a name="you-receive-an-access-error-when-attempting-to-change-the-btarn-configuration"></a>Vous recevez une erreur d’accès lors de la tentative de modifier la configuration de BTARN  
  
### <a name="symptom"></a>Symptôme  
 Le message d’erreur suivant s’affiche lorsque vous importez un fichier de configuration en utilisant le [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] Console de gestion :  
  
 N’a pas pu les données de type de transport pour le Transport principal du Port d’envoi ' RNSTT. Async » à la banque de configuration. Accès refusé.  
  
 Vous pouvez également recevoir cette erreur lorsque vous essayez de modifier la configuration, par exemple en créant un nouveau partenaire.  
  
### <a name="possible-cause"></a>Cause possible  
 L’utilisateur actuel n’est pas un membre du groupe Administrateurs de BizTalk.  
  
### <a name="solution"></a>Solution  
 Assurez-vous que l’utilisateur actuel est membre du groupe Administrateurs de BizTalk.  
  
## <a name="you-receive-bam-errors"></a>Vous recevez des erreurs d’analyse BAM  
  
### <a name="symptom"></a>Symptôme  
 Vous recevez des messages d’erreur suivants dans l’Observateur d’événements :  
  
 Erreur s’est produite dans le suivi de l’activité du Message. Message d’erreur est stocké n’existe pas.  
  
 -ou-  
  
 Erreur lors de la fin d’activité de message BAM avec l’id  *\<numéro d’identification\>*.  
  
### <a name="possible-cause"></a>Cause possible  
 L’outil de suivi d’analyse BAM (Business Activity) n’est pas installé.  
  
### <a name="solution"></a>Solution  
 Installer l’à l’aide de l’outil de suivi BAM le **Installation personnalisée** option. Si vous n’avez pas besoin de fonctionnalités d’analyse BAM, vous pouvez ignorer ces messages ou désactiver le suivi à l’aide du [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] Console de gestion. Après avoir désactivé le suivi, vous devez redémarrer [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] et Internet et les Information Services (IIS).  
  
## <a name="your-xsd-schema-does-not-display-properly-in-biztalk-editor"></a>Votre schéma XSD ne pas s’afficher correctement dans l’Éditeur BizTalk  
  
### <a name="symptom"></a>Symptôme  
 Vous ne pouvez pas afficher le contenu d’un schéma correctement dans l’Éditeur BizTalk.  
  
### <a name="possible-cause"></a>Cause possible  
 Il manque le schéma le `displayroot_reference` d’attribut pour le `schemaInfo` élément.  
  
### <a name="solution"></a>Solution  
 Ouvrez le schéma dans le bloc-notes ou un autre éditeur de texte et ajoutez le `displayroot_reference` attribut le `schemaInfo` élément. La valeur de la `displayroot_reference` attribut doit être le même que le `root_reference` attribut.  
  
 Exemple :  
  
 \<schemaInfo document_type = « 4A1 » version = « V02_00 » xmlns = « http://schemas.microsoft.com/BizTalk/2003 » *displayroot_reference = « Pip4A1StrategicForecastNotification »* root_reference = » Pip4A1StrategicForecastNotification »\>  
  
## <a name="404-not-found-error-when-sending-a-http-request"></a>Erreur 404 introuvable lors de l’envoi d’une requête HTTP  
  
### <a name="symptom"></a>Symptôme  
 Vous recevez les erreurs suivantes ou similaires lors de l’envoi d’une requête HTTP :  
  
 Le serveur distant a retourné une erreur : (404) introuvable.  
  
 Impossible d’envoyer le message à... / BTSHttpReceive.dll.  
  
### <a name="possible-cause"></a>Cause possible  
 Le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] DLL (BTSHttpReceive.dll) d’extension Internet Server API (ISAPI) n’a pas été configurée dans Internet Information Services (IIS). Cela se produit si l’extension du service web HwsMessages HttpReceive n’est pas configurée et si cette extension de service web est configurée, mais non autorisée.  
  
### <a name="solution"></a>Solution  
 Pour déterminer si l’extension du service web HwsMessages HttpReceive est configurée et si elle n'est pas configurée, afin d’autoriser son, effectuez la procédure suivante.  
  
##### <a name="to-configure-the-biztalk-isapi-extension-dll-in-iis"></a>Pour configurer la DLL d’extension ISAPI de BizTalk dans IIS  
  
1.  Cliquez sur **Démarrer**, pointez sur **outils d’administration**, puis cliquez sur **Gestionnaire des Services Internet (IIS)**.  
  
2.  Développez  **\<nom de l’ordinateur\> (ordinateur local)**, puis cliquez sur **Extensions du Service Web**.  
  
3.  Dans le **Extension du Service Web** volet, vérifiez que l’état de HwsMessages HttpReceive est autorisé. Avec le bouton droit dans le cas contraire, **HwsMessages HttpReceive**, puis cliquez sur **autoriser**.  
  
 Si l’extension du service web HwsMessages HttpReceive n’est pas configurée (il n'est pas inclus dans la liste d’Extensions du Service Web dans le Gestionnaire des services Internet), effectuez la procédure suivante.  
  
##### <a name="to-configure-the-biztalk-isapi-extension-dll-in-iis"></a>Pour configurer la DLL d’extension ISAPI de BizTalk dans IIS  
  
1.  Cliquez sur **Démarrer**, pointez sur **outils d’administration**, puis cliquez sur **Gestionnaire des Services Internet (IIS)**.  
  
2.  Développez  **\<nom de l’ordinateur\> (ordinateur local)**, avec le bouton droit **Extensions du Service Web**, puis cliquez sur **ajouter une nouvelle extension de service Web** .  
  
3.  Dans le **nouvelle Extension de Service Web** boîte de dialogue le **nom de l’Extension** , tapez **BizTalk d’Extension ISAPI**, puis cliquez sur **ajouter**.  
  
4.  Dans le **ajouter un fichier** boîte de dialogue le **chemin d’accès au fichier** , tapez  **\<lecteur\>: \Program Files\Microsoft BizTalk Server \<version\>\HttpReceive\BTSHttpReceive.dll**, puis cliquez sur **OK**.  
  
5.  Dans le **nouvelle Extension de Service Web** boîte de dialogue, sélectionnez **définir l’état de l’extension à autorisée**, puis cliquez sur **OK**.  
  
## <a name="an-access-violation-occurs-when-running-the-configuration-wizard"></a>Une violation d’accès se produit lors de l’exécution de l’Assistant Configuration  
  
### <a name="symptom"></a>Symptôme  
 Vous recevez l’erreur suivante ou similaire dans le journal des événements :  
  
 Une instance d’hôte BizTalk isolé configurée avec le compte d’utilisateur '\HostSvc' n’est pas exécuté ou n’existe pas sur cet ordinateur. Utilisez la Console Administration de BizTalk pour créer un hôte isolé ou reconfigurer un existant pour s’exécuter en tant que '\hostsvc'.  
  
### <a name="possible-cause"></a>Cause possible  
 Pour exécuter l’Assistant Configuration, l’utilisateur doit être configuré comme\<*nom de l’ordinateur*\>\hostsvc', pas '\hostsvc'.  
  
### <a name="solution"></a>Solution  
 Ouvrez la Console Administration de BizTalk et modifier les hôtes qui sont exécutent sous le compte '\hostsvc', afin qu’ils s’exécutent sous le compte '\<*nom de l’ordinateur*\>\hostsvc'.  
  
## <a name="you-receive-an-error-when-importing-and-compiling-a-rosettanet-next-generation-pip-schema"></a>Vous recevez une erreur lors de l’importation et de la compilation d’un schéma d’adresse PIP de RosettaNet prochaine génération  
  
### <a name="symptom"></a>Symptôme  
 Vous recevez l’erreur suivante ou similaire dans le journal des événements :  
  
 erreur CS0234 : le nom de l’espace de noms ou de type 'SerializableAttribute' n’existe pas dans la classe ou l’espace de noms 'RosettaNet.Schemas.System' (vous manque-t-il une référence d’assembly ?).  
  
### <a name="possible-cause"></a>Cause possible  
 Un de vos schémas, par exemple, StandardDocumentHeader.xsd, a un [!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)] espace de noms de RosettaNet.Schemas.System.  
  
### <a name="solution"></a>Solution  
 Supprimer le « système » de la [!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)] espace de noms pour le schéma, afin que l’espace de noms est RosettaNet.Schemas.  
  
## <a name="you-receive-an-error-when-trying-to-manually-deploy-the-bam-package"></a>Vous recevez une erreur lorsque vous tentez de déployer manuellement le Package d’analyse BAM  
  
### <a name="symptom"></a>Symptôme  
 Lorsque vous essayez manuellement déployer le package d’analyse BAM pour [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)], vous recevez une erreur indiquant que vous ne pouvez pas déployer le package.  
  
### <a name="possible-cause"></a>Cause possible  
 Les packages DTS BAM_DM_Process et BAM_DM_Message sont installés sur votre système, ce qui empêche le déploiement du package d’analyse BAM.  
  
### <a name="solution"></a>Solution  
  
##### <a name="to-recover-from-the-error-condition-and-deploy-the-bam-package"></a>Pour récupérer à partir de la condition d’erreur et de déployer le package d’analyse BAM  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft SQL Server**, puis cliquez sur **Enterprise Manager**.  
  
2.  Dans Enterprise Manager, développez **serveurs Microsoft SQL Server**, **groupe SQL Server**, **(local) (Windows NT)**, et **Data Transformation Services**.  
  
3.  Cliquez sur **lots locaux**, avec le bouton droit **BAM_DM_Message**, puis cliquez sur **supprimer**.  
  
4.  Avec le bouton droit **BAM_DM_Process**, puis cliquez sur **supprimer**.  
  
5.  Cliquez sur **Démarrer**, puis sur **Exécuter**, tapez **cmd**, puis cliquez sur **OK**.  
  
6.  À l’invite de commandes, tapez le code suivant pour déployer le fichier de suivi, puis cliquez sur **OK**.  
  
    ```  
    cd %ProgramFiles%\Microsoft BizTalk Server <version>\Tracking  
    bm deploy all  "%ProgramFiles%\Microsoft BizTalk <version> Accelerator for RosettaNet\BAMTracking\tracking.xml"  
    ```  
  
## <a name="you-receive-an-error-when-adding-a-new-pip"></a>Vous recevez une erreur lors de l’ajout d’un nouveau PIP  
  
### <a name="symptom"></a>Symptôme  
 Vous recevez l’erreur suivante ou similaire dans le journal des événements :  
  
 UNP. SCON. VALERR : Une erreur s’est produite lors de la validation du contenu du service.  
  
 Détails : La recherche de spécification de document par type de message a échoué. Vérifiez que le schéma est correctement déployé.  
  
### <a name="possible-cause"></a>Cause possible  
 L’espace de noms du document ou de la propriété de nœud racine du schéma déployé pour l’instance Pip4A5NotifyofForecastReply est incorrect.  
  
### <a name="solution"></a>Solution  
 Vérifiez que l’espace de noms du document et de la propriété de nœud racine pour le schéma déployé Pip4A5NotifyofForecastReply pour l’instance est correct.  
  
## <a name="error-during-the-configuration-of-btarn-at-installation-time-caused-by-presumed-network-connectivity-issues"></a>Erreur lors de la configuration BTARN au moment de l’installation, due supposées réseau des problèmes de connectivité  
  
### <a name="symptom"></a>Symptôme  
 Pendant le processus de configuration, vous recevez une erreur dans la boîte de dialogue d’erreur indiquant que l’ordinateur n’est pas correctement connecté au réseau, quand il est en fait.  
  
### <a name="possible-cause"></a>Cause possible  
 Cette erreur peut être dû à la [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] programme de configuration IP de mauvaise adresses. Le fichier hosts à C:\Windows\system32\drivers\etc contient une entrée de mappage du nom d’hôte localhost à l’adresse IP 127.0.0.1. Le programme de configuration peut confondre cette valeur avec l’adresse de bouclage et supposent que l’ordinateur n’est pas connecté correctement au réseau.  
  
### <a name="solution"></a>Solution  
  
##### <a name="to-avoid-this-error-and-complete-the-configuration-process"></a>Pour éviter cette erreur et de terminer le processus de configuration  
  
1.  Dans [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Explorer, atteindre C:\Windows\system32\drivers\etc et ouvrez le fichier d’hôtes à l’aide du bloc-notes.  
  
2.  Commentez la ligne « 127.0.0.1 localhost » en plaçant « # » au début de la ligne. Enregistrez le fichier hôtes modifié.  
  
3.  Cliquez sur **réessayer** dans la boîte de dialogue d’erreur.  
  
4.  Une fois la configuration terminée, ouvrez à nouveau le fichier d’hôtes dans le bloc-notes, supprimer la marque de commentaire au début de l’hôte local mappage de ligne, puis enregistrez le fichier hosts.  
  
## <a name="you-receive-an-error-regarding-incorrect-signature-length"></a>Vous recevez une erreur concernant la longueur de la signature incorrecte  
  
### <a name="symptom"></a>Symptôme  
 Vous recevez l’erreur suivante ou similaire dans le journal des événements :  
  
 Échec de l’exécution du pipeline de réception : « Microsoft.Solutions.BTARN.Pipelines.Receive » Source : « Décodeur MIME/SMIME » emplacement de réception : « / BTARNHttpReceive/BTSHTTPReceive.dll?xRNResponseType=async « raison : longueur de signature incorrecte, valeur = 1935897193.  
  
### <a name="possible-cause"></a>Cause possible  
 Ce message d’erreur indique que la longueur de la signature est incorrecte. En plus de la cause ci-dessus, cette erreur pourrait être également dû à la longueur de contenu incorrecte ou incomplète en-tête prospects vers les octets incorrects de lecture sur la longueur de signature.  
  
### <a name="solution"></a>Solution  
 Vérifiez que les deux de la longueur de la signature et la longueur de contenu d’en-tête est correct.  
  
## <a name="you-receive-503-service-unavailable-from-internet-explorer-on-64-bit-machine"></a>Vous recevez « 503 : Service non disponible » à partir d’Internet Explorer sur un ordinateur 64 bits  
  
### <a name="symptom"></a>Symptôme  
 Après avoir [!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)] configuration terminée, lorsque vous essayez d’accéder à [http://localhost](http://localhost/) ou [http://localhost/BtarnApp/RnifSend.aspx](http://localhost/BtarnApp/RnifSend.aspx), vous pouvez recevoir l’erreur suivante ou similaire :  
  
 503 : Service non disponible  
  
### <a name="possible-cause"></a>Cause possible  
 Cette erreur peut être provoquée par le filtre ISAPI situé sous C:\windows\system32\rpcproxy\rpcproxy.dll définie sur les Sites Web IIS.  
  
### <a name="solution"></a>Solution  
  
##### <a name="to-remove-rpcproxy-filter-entry-in-iis"></a>Pour supprimer l’entrée de filtre RpcProxy dans IIS  
  
1.  Cliquez sur **Démarrer**, pointez sur **outils d’administration**, puis cliquez sur **Gestionnaire des Services Internet (IIS)**.  
  
2.  Développez  **\<nom de l’ordinateur\> (ordinateur local)**, avec le bouton droit **Sites Web**, puis cliquez sur **propriétés**.  
  
3.  Sélectionnez **filtres ISAPI** onglet.  
  
4.  Sélectionnez **RpcProxy filtre**, puis cliquez sur **supprimer**.  
  
5.  Cliquez sur **OK**.  
  
6.  Cliquez sur **Démarrer**, puis sur **Exécuter**, tapez **cmd**, puis cliquez sur **OK**.  
  
7.  À l’invite de commandes, tapez le code suivant pour réinitialiser IIS.  
  
    ```  
    iisreset  
    ```  
  
> [!NOTE]
>  Si vous essayez d’accéder à http://localhost ou http://localhost/BtarnApp/RnifSend.aspx après les étapes ci-dessus, vous recevrez les messages HTTP 400 à partir d’Internet Explorer, ce qui signifie que IIS fonctionne désormais correctement.  
  
## <a name="the-hubscenario-sample-will-not-be-installed-correctly-if-the-assembly-key-files-are-not-entered-for-the-projects"></a>L’exemple HubScenario ne sera pas installé correctement si les fichiers de clé d’assembly ne sont pas entrés pour les projets  
  
### <a name="symptom"></a>Symptôme  
 Lorsque vous exécutez setup.bat dans  *\<lecteur\>*: \Program Files\\ [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk \<version\> Accelerator pour RosettaNet\SDK\HubScenario configurer le L’exemple HubScenario, l’opération échoue.  
  
### <a name="possible-cause"></a>Cause possible  
 Les assemblys HubScenario et HubHelper ont été pas déployés correctement, car les fichiers de clé d’assembly n’ont pas été définies dans les projets.  
  
### <a name="solution"></a>Solution  
 Définir les fichiers de clé d’assembly pour les projets HubScenario et HubHelper. Pour plus d’informations, consultez [exemple HubScenario](../../adapters-and-accelerators/accelerator-rosettanet/hubscenario-sample.md).  
  
## <a name="run-setupx64bat-to-set-up-the-double-action-pipautomation-orchestration-sample-on-sql-server-2008-r22008-sp1"></a>Exécutez setupx64.bat pour installer l’exemple d’Orchestration Double Action PIPAutomation sur SQL Server 2008 R2/2008 SP1  
  
### <a name="symptom"></a>Symptôme  
 Lorsque vous exécutez setup.bat pour créer et initialiser l’exemple d’Orchestration Double Action PIPAutomation, la PipAutomationGetAction procédure stockée dans la base de données n’est pas créé de BTARNData.  
  
### <a name="possible-cause"></a>Cause possible  
 Vous avez exécuté setup.bat sur un ordinateur 64 bits ou sur une installation de BizTalk Server est en cours d’exécution sur SQL Server 2008 R2/2008 SP1. Ces deux cas vous amener à exécutez setupx64.bat.  
  
### <a name="solution"></a>Solution  
 Exécutez setupx64.bat pour créer la procédure stockée. Pour plus d’informations, consultez [Orchestration Double Action PIPAutomation](../../adapters-and-accelerators/accelerator-rosettanet/double-action-pipautomation-orchestration.md).  
  
## <a name="enable-the-btarn-application-pools-for-32-bit-on-windows-server-2008-64-bit-windows-operating-system-os"></a>Activer les Pools d’applications BTARN pour 32 bits sur Windows Server 2008, le système d’exploitation de Windows 64 bits (OS)  
 Pour exécuter le scénario de bout en bout BTARN sur Windows Server 2008,64 bits système d’exploitation (système d’exploitation Windows), Internet Information Services Manager 7.5/7.0.  
  
 1. Activer les Pools d’applications BTARN pour 32 bits.  
  
 2. Ajoutez un gestionnaire HTTP pour *.dll référence les filtres IsapiModule.  
  
## <a name="see-also"></a>Voir aussi  
 [BtarnClean](../../adapters-and-accelerators/accelerator-rosettanet/btarnclean.md)   
 [Loopback](../../adapters-and-accelerators/accelerator-rosettanet/loopback.md)