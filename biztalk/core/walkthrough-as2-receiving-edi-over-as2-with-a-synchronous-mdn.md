---
title: "Procédure pas à pas (AS2) : Réception d’EDI via AS2 avec un MDN synchrone | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0b63395f-03f4-45e8-a68a-9bbbd8dfa344
caps.latest.revision: "53"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bd2c43392cf8e9fa1153be9b674e9ac1b7f26e84
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="walkthrough-as2-receiving-edi-over-as2-with-a-synchronous-mdn"></a>Procédure pas à pas (AS2) : réception EDI via AS2 avec un MDN synchrone
Cette procédure pas à pas fournit des instructions détaillées sur la création d'une solution pour la réception de messages EDI via le transport AS2 et le renvoi de MDN synchrones.  
  
## <a name="prerequisites"></a>Conditions préalables  
 La configuration suivante est requise pour exécuter les procédures décrites dans cette rubrique :  
  
-   Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
-   Internet Information Services (IIS) 7 doit être installé sur l'ordinateur sur lequel est exécutée la procédure pas à pas.  
  
-   Si une version 64 bits de Windows est installée sur l'ordinateur sur lequel est exécutée la procédure pas à pas, vous devez vérifier que les hôtes BizTalk sont marqués comme applications 32 bits uniquement. Vous devez également vérifier que IIS le paramètre d’Application Enable 32 bits pour les Pools d’applications est défini sur **True**. Pour plus d’informations, consultez [didacticiel 3 : didacticiel AS2](../core/tutorial-3-as2-tutorial.md).  
  
## <a name="how-the-solution-receives-an-edias2-message-and-returns-a-synchronous-mdn"></a>Réception d'un message EDI/AS2 et renvoi d'un MDN synchrone par la solution  
 La solution assure les tâches suivantes :  
  
1.  Réception d'un message AS2 contenant un échange EDI via HTTP du partenaire commercial Fabrikam et décodage de l'échange à partir d'EDIINT/AS2.  
  
    > [!NOTE]
    >  Les événements dans cette liste peuvent se produire dans un ordre différent de celui indiqué.  
  
2.  Renvoi d'un MDN synchrone au partenaire commercial à l'aide du port de réception de requête-réponse.  
  
3.  Conversion du format EDI de l'échange au format XML interne et placement dans la MessageBox.  
  
4.  Un port d'envoi FILE avec un pipeline PassThruTransmit récupère le fichier XML du message.  
  
5.  Le port d'envoi transmet le fichier XML d'échange EDI à un dossier du tiers Contoso.  
  
 L'architecture de cette solution est représentée dans la figure suivante.  
  
 ![Réception AS2 avec un MDN synchrone](../core/media/4ff20070-1c36-42e5-af14-832771d63b88.gif "4ff20070-1c36-42e5-af14-832771d63b88")  
  
## <a name="the-functionality-in-this-solution"></a>Fonctionnalités dans la solution  
 Les conditions suivantes s'appliquent aux fonctionnalités de cette procédure pas à pas :  
  
-   Aucun accusé de réception EDI n'est généré. Génération d’un accusé de réception EDI est illustrée dans [procédure pas à pas (X12) : réception des échanges EDI et envoi d’un accusé](../core/walkthrough-x12--receive-edi-interchanges-and-send-back-an-acknowledgement.md). Envoi d’un accusé de réception EDI via le transport AS2 est décrit dans [procédure pas à pas (AS2) : envoi d’EDI via AS2 avec un MDN synchrone](../core/walkthrough-as2-sending-edi-over-as2-with-a-synchronous-mdn.md).  
  
-   La solution est conçue pour les échanges basés sur le codage X12, et non le codage EDIFACT.  
  
    > [!NOTE]
    >  La configuration utilisée pour le codage EDIFACT est proche de celle utilisée pour le codage X12.  
  
-   La validation de type EDI et la validation étendue sont effectuées sur l'échange entrant.  
  
-   La création de rapports AS2 et EDI est activée. Les documents informatisés sont enregistrés pour être consultables depuis le rapport État de l'échange.  
  
-   Cette solution ne configure pas la signature, la compression, le chiffrement ou le stockage des messages dans la base de données de non-répudiation. Pour les procédures de configuration de ces propriétés, consultez [configuration des propriétés AS2](../core/configuring-as2-properties.md).  
  
## <a name="configuring-and-testing-the-walkthrough"></a>Configuration et test de la procédure pas à pas  
 Les étapes suivantes sont requises pour configurer cette solution :  
  
-   Créer et déployer un projet BizTalk avec le schéma de message requis, le schéma pouvant être utilisé par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dans le cadre du traitement de l'échange reçu.  
  
-   Activer le filtre BTS ISAPI utilisé pour la réception du message AS2.  
  
-   Créer un répertoire virtuel Contoso recevant le message AS2 de Fabrikam, comme configuré dans l'emplacement de réception.  
  
-   Spécifier que le répertoire virtuel Contoso n'est pas géré par les services Windows SharePoint.  
  
-   Créer un port de réception HTTP bidirectionnel statique pour [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour recevoir le message AS2 contenant l'échange EDI du partenaire commercial et envoyer la réponse MDN. Configurer le pipeline AS2EDIReceive comme pipeline de réception et le pipeline AS2Send comme pipeline d'envoi.  
  
-   Créer un port d'envoi FILE unidirectionnel statique pour transférer la charge EDI (au format XML) vers un dossier local. Créer le dossier local.  
  
-   Créer un tiers (partenaire commercial) pour Fabrikam et Contoso.  
  
-   Créer un profil d'entreprise pour les deux parties commerciales.  
  
-   Créer un accord AS2 entre les profils d'entreprise pour Fabrikam et Contoso. L'accord AS2 contiendra les propriétés relatives à l'envoi d'un message AS2 et la réception d'un MDN synchrone en retour.  
  
-   Créer un accord X12 entre les profils d'entreprise pour Fabrikam et Contoso pour la réception des messages X12.  
  
-   Tester la solution à l'aide de l'utilitaire HTTP Sender inclus dans les fichiers du didacticiel AS2. Cet utilitaire envoie un message AS2 de test contenant un échange EDI via le transport AS2 (X12_00401_864-Sync.edi, également inclus dans le didacticiel AS2). Vous devez modifier l'utilitaire HTTP Sender et le message de test des versions incluses dans le didacticiel. Ces modifications sont décrites dans les sections appropriées ci-dessous.  
  
### <a name="configuring-the-walkthrough"></a>Configuration de la procédure pas à pas  
 Cette section décrit les étapes de configuration de la procédure pas à pas.  
  
##### <a name="to-deploy-the-message-schema"></a>Pour déployer le schéma de message  
  
1.  Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], ouvrez le projet [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\Schemas\Schemas.btproj.  
  
    > [!NOTE]
    >  Ce projet, intégré au didacticiel AS2, inclut un schéma 864 à utiliser avec le message de test.  
  
    > [!NOTE]
    >  Cette rubrique part du principe que vous avez déjà ajouté une référence de votre application à l'application BizTalk EDI, qui contient les schémas, pipelines et orchestrations EDI. Dans le cas contraire, consultez [comment ajouter une référence à l’Application EDI de BizTalk Server](http://msdn.microsoft.com/library/7af066fb-372f-4709-b566-c8d6b4a9d782).  
  
2.  Cliquez sur le **schémas** de projet dans l’Explorateur de solutions, puis cliquez sur **propriétés**. Cliquez sur le **signature** onglet dans le Concepteur de projet, vérifiez le **signer l’Assembly** case à cocher, puis, dans la liste déroulante, sélectionnez **nouveau** et fournir les valeurs nécessaires pour créer un fichier de clé de nom fort. Enregistrez les modifications et fermez la fenêtre de propriétés du projet.  
  
3.  Créez et déployez Schemas.btproj.  
  
##### <a name="to-enable-the-bts-isapi-filter"></a>Pour activer le filtre ISAPI BTS  
  
1.  Cliquez sur **Démarrer**, pointez sur **Tous les programmes**, puis sur **Outils d'administration**, puis cliquez sur **Gestionnaire des services Internet (IIS)**.  
  
    > [!TIP]
    >  Selon le système d'exploitation utilisé, l'option Outils d'administration du menu Démarrer peut être indisponible. Dans ce cas, cliquez sur **Démarrer**, cliquez sur **exécuter**, puis entrez `inetmgr` pour ouvrir le Gestionnaire des Services Internet (IIS).  
  
2.  Sélectionnez l’entrée de serveur Web racine et dans le **affichage des fonctionnalités**, double-cliquez sur **mappages de gestionnaires** puis, dans le **Actions** volet, cliquez sur **ajouter un mappage de scripts**.  
  
    > [!NOTE]
    >  Configurer le mappage du script au niveau du serveur Web entraîne ce mappage à appliquer à tous les enfants de Sites Web. Si vous souhaitez limiter le mappage à un Site Web ou un dossier virtuel spécifique, sélectionnez le site cible ou le dossier au lieu du serveur Web.  
  
3.  Dans le **ajouter un mappage de scripts** boîte de dialogue, entrez `BtsHttpReceive.dll` dans les **chemin d’accès de la demande** champ.  
  
4.  Dans le **exécutable** , cliquez sur le **points de suspension (...)**  bouton et accédez à [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]HttpReceive. Sélectionnez BtsHttpReceive.dll, puis cliquez sur **OK**.  
  
5.  Entrez `BizTalk HTTP Receive` dans les **nom** champ, puis cliquez sur **Restrictions des demandes**.  
  
6.  Dans le **Restrictions des demandes** boîte de dialogue, sélectionnez le **verbes** onglet, puis sélectionnez **un des verbes suivants**. Entrez `POST` le verbe.  
  
7.  Sur le **accès** onglet, sélectionnez **Script** puis cliquez sur **OK**.  
  
8.  Cliquez sur **OK** lorsque vous êtes invité à autoriser l’extension ISAPI, cliquez sur **Oui**.  
  
##### <a name="to-configure-the-contoso-web-page"></a>Pour configurer la page Web Contoso  
  
1.  Avec le bouton droit dans le Gestionnaire des services Internet, **Pools d’applications** et sélectionnez **ajouter un Pool d’applications**.  
  
2.  Dans le **ajouter un Pool d’applications** boîte de dialogue, entrez **BizTalkAppPool** dans **nom**, puis sélectionnez **.NET Framework V4.0.30210** dans le **Version du .NET framework** liste déroulante. Cliquez sur **OK**.  
  
    > [!NOTE]
    >  Le numéro de version peut varier selon la version de [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] installée sur l'ordinateur.  
  
3.  Sélectionnez **Pools d’applications**, dans la sélection de l’affichage des fonctionnalités **BizTalkAppPool**, puis cliquez sur **paramètres avancés** dans les **Actions** volet.  
  
4.  Dans le **paramètres avancés** boîte de dialogue, sélectionnez **identité** puis cliquez sur le **points de suspension (...)**  bouton.  
  
5.  Dans le **identité du Pool d’applications** boîte de dialogue, sélectionnez **compte personnalisé** puis cliquez sur **définir**.  
  
6.  Entrez le **nom d’utilisateur** et **mot de passe** pour un compte d’utilisateur qui est membre du groupe Administrateurs, entrez le mot de passe **confirmer le mot de passe** puis cliquez sur **OK** trois fois pour retourner le Gestionnaire des services Internet.  
  
7.  Dans le Gestionnaire des services Internet, ouvrez le **Sites** dossier. Cliquez sur le **Site Web par défaut** nœud et sélectionnez **ajouter une Application**.  
  
8.  Dans le **ajouter une Application** boîte de dialogue, entrez **Contoso** dans les **Alias** zone de texte, puis cliquez sur **sélectionnez**.  
  
9. Dans le **sélectionner un Pool d’applications** boîte de dialogue, sélectionnez **BizTalkAppPool** et cliquez sur **OK**.  
  
10. Pour le **chemin d’accès physique**, cliquez sur le **points de suspension (...)**  bouton et accédez à [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]HttpReceive.  
  
11. Cliquez sur **des paramètres de Test** et vérifiez qu’il n’y a aucune erreur affiché dans le **tester la connexion** boîte de dialogue. Cliquez sur **Fermer**, puis sur **OK**.  
  
12. Dans le Gestionnaire des services Internet, sélectionnez le répertoire virtuel Contoso et dans le **affichage des fonctionnalités**, double-cliquez sur **authentification**.  
  
13. Dans le **authentification** page, sélectionnez **l’authentification anonyme** et vérifiez que le **état** est **activé**. Si le **état** est **désactivé**, cliquez sur **activer** dans les **Actions** volet.  
  
##### <a name="to-specify-that-your-virtual-directory-is-not-managed-by-windows-sharepoint-services"></a>Pour spécifier que votre répertoire virtuel n'est pas géré par les Windows SharePoint Services  
  
1.  Si Windows SharePoint Services est installé sur votre ordinateur, cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **outils d’administration**, puis cliquez sur **Administration centrale de SharePoint 3.0**.  
  
    > [!NOTE]
    >  Cette procédure est requise si Windows SharePoint Server est installé sur l'ordinateur sur lequel vous configurez la procédure pas à pas. Dans ce cas, vous devez spécifier que votre répertoire virtuel IIS n'est pas géré par Windows SharePoint Server.  
  
2.  Sur le **Administration centrale** sous **Administration centrale**, cliquez sur **gestion des applications**.  
  
3.  Sur le **gestion des applications** , cliquez sur **définir les chemins d’accès gérés**.  
  
4.  Dans le **définir les chemins d’accès gérés** sous **ajouter un nouveau chemin**et dans le **chemin d’accès** texte, entrez **Contoso**. Sous **Type**, cliquez sur **chemin d’accès exclu**, puis cliquez sur **OK**.  
  
##### <a name="to-create-a-receive-port-to-receive-the-edi-over-as2-message-and-return-an-mdn"></a>Pour créer un port de réception pour recevoir le message EDI via AS2 et renvoyer un MDN  
  
1.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, avec le bouton droit le **Ports de réception** nœud sous la **BizTalk Application 1** nœud, pointez sur **nouveau**, puis cliquez sur  **Port de réception requête-réponse**.  
  
2.  Nommez le port de réception, puis cliquez sur **emplacements de réception** dans l’arborescence de la console.  
  
3.  Cliquez sur **Nouveau**.  
  
4.  Nom de l’emplacement de réception, sélectionnez **HTTP** pour **Type**, puis cliquez sur **configurer**.  
  
5.  Pour **répertoire virtuel assorti de l’extension ISAPI**, entrez `/Contoso/BTSHTTPReceive.dll`.  
  
6.  Sélectionnez le **suspendre les requêtes ayant échoué** case à cocher, puis cliquez sur **OK**.  
  
7.  Pour **pipeline de réception**, sélectionnez **AS2EDIReceive**.  
  
8.  Pour **pipeline d’envoi**, sélectionnez **AS2Send**.  
  
9. Cliquez sur **OK**, puis cliquez sur **OK** à nouveau.  
  
10. Dans le **emplacements de réception** volet de la Console Administration de BizTalk Server, cliquez sur l’emplacement de réception, puis cliquez sur **activer**.  
  
##### <a name="to-create-a-send-port-to-send-the-edi-payload-to-a-local-folder"></a>Pour créer un port d'envoi pour envoyer la charge EDI vers un dossier local  
  
1.  Dans l’Explorateur Windows, créez un dossier local nommé **EDI_to_Contoso** pour envoyer la charge EDI.  
  
2.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi unidirectionnel statique**.  
  
3.  Dans le **propriétés de Port d’envoi** boîte de dialogue Nom de votre port d’envoi, par exemple, **Send_Payload**. Sélectionnez **fichier** pour **Type**, puis cliquez sur **configurer**.  
  
4.  Dans le **propriétés du Transport FILE** boîte de dialogue, pour **dossier de Destination**, recherchez et sélectionnez le **EDI_to_Contoso** dossier que vous avez créé à l’étape 1. Laissez **nom de fichier** en tant que **%MessageID%.xml**. Cliquez sur **OK**.  
  
5.  Pour le **Pipeline d’envoi** liste déroulante, acceptez la valeur par défaut **PassThruTransmit**.  
  
6.  Cliquez sur **filtres** dans l’arborescence de la console. Pour **propriété**, entrez **BTS. MessageType**. Pour **opérateur**, entrez  **==** . Pour **valeur**, entrez le type de message de votre message, `http://schemas.microsoft.com/BizTalk/Edi/X12/2006#X12_00401_864`.  
  
7.  Cliquez sur **OK**.  
  
8.  Dans le **Ports d’envoi** volet de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, cliquez sur le port d’envoi, puis cliquez sur **Démarrer**.  
  
##### <a name="to-create-a-party-and-a-business-profile-for-fabrikam"></a>Pour créer un tiers et un profil d'entreprise pour Fabrikam  
  
1.  Avec le bouton droit le **Parties** nœud dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, pointez sur **nouveau**, puis cliquez sur **tiers**.  
  
2.  Entrez un nom pour le tiers dans le **nom** zone de texte, puis cliquez sur **OK**.  
  
    > [!NOTE]
    >  En sélectionnant le **BizTalk Local traite les messages reçus par le tiers ou prend en charge l’envoi de messages à partir de ce tiers** case à cocher, vous pouvez spécifier que le tiers en cours de création est pour la même organisation qui héberge également [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. En prenant ces éléments en compte, certaines propriétés devront être activées et d'autres désactivées lors de la création d'un accord. Toutefois, pour les besoins de cette procédure pas à pas, vous pouvez laisser cette case à cocher activée.  
  
3.  Cliquez sur le nom du tiers, pointez sur **nouveau**, puis cliquez sur **profil d’entreprise**.  
  
4.  Dans le **propriétés de profil** boîte de dialogue le **général** , entrez **Fabrikam_Profile** dans les **nom** zone de texte.  
  
    > [!NOTE]
    >  Lorsque vous créez un tiers, un profil est également créé. Vous pouvez renommer et utiliser ce profil plutôt que d'en créer un nouveau. Pour renommer un profil, cliquez sur le profil et sélectionnez **propriétés**. Dans le **général** , spécifiez un nom pour le profil.  
  
##### <a name="to-create-a-party-and-a-business-profile-for-contoso"></a>Pour créer un tiers et un profil d'entreprise pour Contoso  
  
1.  Avec le bouton droit le **Parties** nœud dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, pointez sur **nouveau**, puis cliquez sur **tiers**.  
  
2.  Entrez un nom pour le tiers dans le **nom** zone de texte, puis cliquez sur **OK**.  
  
    > [!NOTE]
    >  En sélectionnant le **BizTalk Local traite les messages reçus par le tiers ou prend en charge l’envoi de messages à partir de ce tiers** case à cocher, vous pouvez spécifier que le tiers en cours de création est pour la même organisation qui héberge également [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. En prenant ces éléments en compte, certaines propriétés devront être activées et d'autres désactivées lors de la création d'un accord. Toutefois, pour les besoins de cette procédure pas à pas, vous pouvez laisser cette case à cocher activée.  
  
3.  Cliquez sur le nom du tiers, pointez sur **nouveau**, puis cliquez sur **profil d’entreprise**.  
  
4.  Dans le **propriétés de profil** boîte de dialogue le **général** , entrez **Contoso_Profile** dans les **nom** zone de texte.  
  
    > [!NOTE]
    >  Lorsque vous créez un tiers, un profil est également créé. Vous pouvez renommer et utiliser ce profil plutôt que d'en créer un nouveau. Pour renommer un profil, cliquez sur le profil et sélectionnez **propriétés**. Dans le **général** , spécifiez un nom pour le profil.  
  
##### <a name="to-create-an-as2-agreement-between-the-two-business-profiles"></a>Pour créer un accord AS2 entre les deux profils d'entreprise  
  
1.  Avec le bouton droit **Fabrikam_Profile**, pointez sur **nouveau**, puis cliquez sur **accord**.  
  
2.  Dans le **propriétés générales** page, pour le **nom** texte, entrez un nom pour l’accord.  
  
3.  À partir de la **protocole** la liste déroulante, sélectionnez **AS2**.  
  
4.  Dans le **deuxième partenaire** section, à partir de la **nom** la liste déroulante, sélectionnez **Contoso**.  
  
5.  Dans le **deuxième partenaire** section, à partir de la **profil** la liste déroulante, sélectionnez **Contoso_Profile**.  
  
     Vous remarquerez que les deux nouveaux onglets sont ajoutés à côté du **général** onglet. Chaque onglet permet de configurer un accord AS2 unidirectionnel.  
  
6.  Dans le **général** sous l’onglet dans le **propriétés générales** page, dans le **paramètres d’hôte communs** section, sélectionnez **activer le rapport d’état**.  
  
7.  Effectuer les tâches suivantes sur le **Fabrikam -> Contoso** onglet.  
  
    1.  Sur le **identificateurs** , entrez des valeurs pour **AS2-de** et **AS2-pour**. Pour **AS2-de**, entrez `Fabrikam`. Pour **AS2 - To**, entrez `Contoso`.  
  
8.  Effectuer les tâches suivantes sur le **Contoso -> Fabrikam** onglet.  
  
    > [!NOTE]
    >  Dans cette procédure pas à pas, la valeur requise est spécifiée sous l'onglet afin de permettre la création d'un accord. Pour créer un accord, les deux onglets d’accord unidirectionnel doivent avoir des valeurs définies pour **AS2_From** et **AS2-pour**.  
  
    1.  Sur le **identificateurs** , entrez des valeurs pour **AS2-de** et **AS2-pour**. Pour **AS2-de**, entrez `Contoso`. Pour **AS2 - To**, entrez `Fabrikam`.  
  
9. Cliquez sur **Appliquer**.  
  
10. Cliquez sur **OK**. Le nouvel accord ajouté est répertorié dans le **accords** section de la **tiers et profils d’entreprise** volet. Le nouvel accord ajouté est activé par défaut.  
  
##### <a name="to-create-an-x12-agreement-between-the-two-business-profiles"></a>Pour créer un accord X12 entre les deux profils d'entreprise  
  
1.  Avec le bouton droit **Fabrikam_Profile**, pointez sur **nouveau**, puis cliquez sur **accord**.  
  
2.  Dans le **propriétés générales** page, pour le **nom** texte, entrez un nom pour l’accord.  
  
3.  À partir de la **protocole** la liste déroulante, sélectionnez **X12**.  
  
4.  Dans le **deuxième partenaire** section, à partir de la **nom** la liste déroulante, sélectionnez **Contoso**.  
  
5.  Dans le **deuxième partenaire** section, à partir de la **profil** la liste déroulante, sélectionnez **Contoso_Profile**.  
  
     Vous remarquerez que les deux nouveaux onglets sont ajoutés à côté du **général** onglet. Chaque onglet permet de configurer un accord X12 unidirectionnel.  
  
6.  Dans le **général** sous l’onglet dans le **propriétés générales** page, dans le **paramètres d’hôte communs** section, sélectionnez **activer le rapport d’état**, puis Sélectionnez **stocker la charge de message de création de rapports**.  
  
7.  Effectuer les tâches suivantes sur le **Fabrikam -> Contoso** onglet.  
  
    1.  Sur le **identificateurs** page sous le **paramètres de l’échange** section, entrez des valeurs pour les champs de qualificateur et identificateur (**ISA5**, **ISA6**, **ISA7**, et **ISA8**) qui correspondent aux valeurs de ces champs d’en-tête dans le message de test.  
  
        > [!NOTE]
        >  Les champs de qualificateur et d'identificateur pour l'expéditeur et le récepteur permettent à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] de résoudre l'accord. Il compare les valeurs de **ISA5**, **ISA6**, **ISA7**, et **ISA8** dans l’en-tête d’échange à celles dans les propriétés d’un accord. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]sera également l’accord en comparant le qualificateur de l’expéditeur et l’identificateur (sans le qualificateur du récepteur et l’identificateur). Si [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ne peut pas résoudre l'accord, il utilise les propriétés d'accord de secours.  
  
        > [!NOTE]
        >  Pour cette procédure pas à pas, définissez **ISA5** à **ZZ**, **ISA6** à **7654321**, **ISA7** à **ZZ** , et **ISA8** à **1234567**.  
  
    2.  Sur le **Validation** page sous le **paramètres de l’échange** section, assurez-vous que **chercher isa13 en double** option est désactivée.  
  
        > [!NOTE]
        >  Effacer la **chercher isa13 en double** propriété vous permet de recevoir plusieurs instances du même message.  
  
    3.  Si vous utilisez l’un des schémas standards fournis avec [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], dans le **paramètres d’hôte Local** page sous le **paramètres des documents informatisés** , sélectionnez l’espace de noms du schéma à être utilisé pour traiter l’échange entrant.  
  
        |Utiliser|Pour effectuer cette opération|  
        |--------------|----------------|  
        |**Default**|Activez la case à cocher dans la colonne.|  
        |**Cible Namespace**|Sélectionnez **http://schemas.microsoft.com/BizTalk/EDI/X12/2006**.|  
  
        > [!NOTE]
        >  La définition des propriétés permet à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] d'identifier le schéma à utiliser pour le traitement de l'échange 850 entrant. Si les valeurs GS02 et ST01 d'un échange sont entrées dans une ligne de la grille, l'espace de noms cible dans la même ligne sert à déterminer le schéma à utiliser.  
  
8.  Effectuer les tâches suivantes sur le **Contoso -> Fabrikam** onglet.  
  
    > [!NOTE]
    >  Dans cette procédure pas à pas, la valeur requise est spécifiée sous l'onglet afin de permettre la création d'un accord. Pour créer un accord, les deux onglets d’accord unidirectionnel doivent avoir des valeurs définies pour **ISA5**, **ISA6**, **ISA7**, et **ISA8**.  
  
    1.  Sur le **identificateurs** page sous le **paramètres de l’échange** section, entrez des valeurs pour les champs de qualificateur et identificateur (**ISA5**, **ISA6**, **ISA7**, et **ISA8**) qui correspondent aux valeurs de ces champs d’en-tête dans le message de test.  
  
        > [!NOTE]
        >  Pour cette procédure pas à pas, définissez **ISA5** à **ZZ**, **ISA6** à **1234567**, **ISA7** à **ZZ** , et **ISA8** à **7654321**.  
  
9. Cliquez sur **Appliquer**.  
  
10. Cliquez sur **OK**. Le nouvel accord ajouté est répertorié dans le **accords** section de la **tiers et profils d’entreprise** volet. Le nouvel accord ajouté est activé par défaut.  
  
### <a name="testing-the-walkthrough"></a>Test de la procédure pas à pas  
 Cette section fournit des informations sur le test de la procédure pas à pas.  
  
##### <a name="to-test-the-solution"></a>Pour tester la solution  
  
1.  Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], ouvrez le projet Sender.csproj dans le dossier [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\Sender.  
  
2.  Dans HttpSender.cs, commentez la ligne suivante (immédiatement sous la ligne de commentaire //Request Asynchronous MDN) :  
  
    ```  
    Stream sr = new FileStream(getBizTalkInstallPath() + @"SDK\AS2 Tutorial\X12_00401_864.edi", FileMode.Open, FileAccess.Read);  
    ```  
  
3.  Supprimez les commentaires dans la ligne suivante (immédiatement sous la ligne de commentaire //Request Synchronous MDN) :  
  
    ```  
    Stream sr = new FileStream(getBizTalkInstallPath() + @"SDK\AS2 Tutorial\X12_00401_864-Sync.edi", FileMode.Open, FileAccess.Read);  
    ```  
  
4.  Créez ce projet.  
  
5.  Dans l'Explorateur Windows, accédez au didacticiel [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2. Ouvrez X12_00401_864-Sync.edi dans le Bloc-notes. Supprimez la ligne définissant l'en-tête Disposition-Notification-Options, puis enregistrez le fichier.  
  
6.  Ouvrez une fenêtre de commande. Accédez à [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\Sender\bin\debug. Exécutez **Sender.exe**.  
  
    > [!NOTE]
    >  L'exécution de Sender.exe dans cette instance publie le message X12_00401_864-sync.edi dans le répertoire virtuel Contoso (emplacement de réception HTTP BTS).  
  
7.  Vérifiez qu'un MDN est affiché dans la fenêtre de commande. Vérifiez que l'en-tête AS2-From est Contoso et que l'en-tête AS2-To est Fabrikam dans le MDN.  
  
    > [!NOTE]
    >  Sender.exe affiche le MDN dans la fenêtre de commande.  
  
8.  Ouvrez le dossier local Contoso que vous créez pour envoyer la charge EDI (**\EDI_to_Contoso**). Vérifiez que le dossier contient un fichier .XML. Ouvrez le fichier XML et vérifiez qu'il contient un document informatisé 864.  
  
9. Ouvrez le message de test X12_00401_864-Sync.EDI dans le bloc-notes et vérifiez que la transaction définie dans le message de sortie dans le **\EDI_to_Contoso** dossier local correspond à la transaction définie dans l’entrée X12_00401_864-Sync.EDI Message.  
  
## <a name="see-also"></a>Voir aussi  
 [Développement et la configuration des Solutions AS2 BizTalk Server](../core/developing-and-configuring-biztalk-server-as2-solutions.md)