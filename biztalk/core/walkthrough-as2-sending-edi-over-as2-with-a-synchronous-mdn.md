---
title: "Procédure pas à pas (AS2) : Envoi d’EDI via AS2 avec un MDN synchrone | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 21891d29-eb22-4b31-9258-14b72ae675dc
caps.latest.revision: "34"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4953e0f3cdc5373d20497d1510fafd9f24991c30
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="walkthrough-as2-sending-edi-over-as2-with-a-synchronous-mdn"></a>Procédure (AS2) : Envoi d'EDI via AS2 avec un MDN synchrone
Cette procédure pas à pas fournit des instructions détaillées sur la création d'une solution pour l'envoi de messages EDI via le transport AS2 et le renvoi d'un MDN synchrone. Vous pouvez créer et tester la solution complète dans cette procédure pas à pas sur un seul ordinateur.  
  
## <a name="prerequisites"></a>Conditions préalables  
 La configuration requise pour exécuter la procédure décrite dans cette rubrique est la suivante :  
  
-   Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
-   Internet Information Services (IIS) 7 doit être installé sur l'ordinateur sur lequel est exécutée la procédure pas à pas.  
  
-   Si une version 64 bits de Windows est installée sur l'ordinateur sur lequel est exécutée la procédure pas à pas, vous devez vérifier que les hôtes BizTalk sont marqués comme applications 32 bits uniquement. Vous devez également vérifier que le paramètre Activer les applications 32 bits pour les pools d'applications est défini sur True pour IIS. Pour plus d’informations, consultez [didacticiel 3 : didacticiel AS2](../core/tutorial-3-as2-tutorial.md).  
  
## <a name="how-the-solution-sends-an-edias2-message-and-returns-a-synchronous-mdn"></a>Envoi d'un message EDI/AS2 et renvoi d'un MDN synchrone par la solution  
 La solution effectue les opérations suivantes :  
  
1.  Un port de réception FILE unidirectionnel reçoit un échange EDI de Contoso.  
  
    > [!NOTE]
    >  Les événements dans cette liste peuvent se produire dans un ordre différent de celui indiqué.  
  
2.  À l'aide d'un pipeline de réception PassThrough, le port de réception dépose le message test, tel quel, dans la base de données MessageBox.  
  
3.  Un port d'envoi bidirectionnel statique récupère l'échange EDI et le code au format AS2.  
  
4.  Le port d'envoi envoie l'échange EDI AS2, via le transport AS2, au tiers Fabrikam.  
  
5.  Le port de réception bidirectionnel, au niveau de Fabrikam, reçoit le message AS2 à l'aide du répertoire virtuel de Fabrikam. Le pipeline de réception décode l'échange EDI à partir d'AS2, puis dépose l'échange EDI dans la base de données MessageBox.  
  
6.  Le port d'envoi associé au port de réception bidirectionnel renvoie un MDN synchrone.  
  
7.  Le port de réception associé au port d'envoi bidirectionnel reçoit le MDN, puis le dépose dans la base de données MessageBox.  
  
8.  Un port d'envoi unidirectionnel statique, avec un pipeline d'envoi PassThrough, récupère le MDN.  
  
9. Le port d'envoi unidirectionnel envoie le MDN vers un dossier local.  
  
10. Un port d'envoi unidirectionnel statique, avec un pipeline d'envoi PassThrough, récupère le message EDI.  
  
11. Le port d'envoi unidirectionnel envoie le message EDI vers un dossier local.  
  
 L'architecture de cette solution est représentée dans la figure suivante.  
  
 ![Envoi AS2 avec un MDN synchrone](../core/media/270d24b7-3b5d-45cc-ba06-6c9f74717194.gif "270d24b7-3b5d-45cc-ba06-6c9f74717194")  
  
## <a name="the-functionality-in-this-solution"></a>Fonctionnalités dans la solution  
 Les conditions suivantes s'appliquent aux fonctionnalités de cette procédure pas à pas :  
  
-   Cette procédure pas à pas porte sur la fonctionnalité AS2, et non sur la fonctionnalité EDI. Par conséquent, tous les ports impliqués dans le traitement AS2 utilisent le pipeline AS2Receive ou AS2Send, et non AS2EdiReceive ou AS2EdiSend. Les ports qui ne sont pas impliqués dans le traitement AS2 utilisent le pipeline PassThruReceive ou PassThruTransmit.  
  
-   Le rapport d'état n'est pas activé.  
  
-   Cette solution ne configure pas la signature, la compression, le chiffrement ou le stockage des messages dans la base de données de non-répudiation. Pour les procédures de configuration de ces propriétés, consultez [configuration des propriétés AS2](../core/configuring-as2-properties.md).  
  
## <a name="configuring-and-testing-the-walkthrough"></a>Configuration et test de la procédure pas à pas  
 Les étapes suivantes sont requises pour configurer cette solution :  
  
-   Créer et déployer un projet BizTalk avec le schéma de message requis, le schéma pouvant être utilisé par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dans le cadre du traitement de l'échange reçu.  
  
-   Activer le filtre BTS ISAPI utilisé pour la réception du message AS2.  
  
-   Créer un répertoire virtuel Fabrikam recevant le message AS2 de Contoso, comme configuré dans l'emplacement de réception.  
  
-   Spécifier que le répertoire virtuel de Fabrikam n'est pas géré par Windows SharePoint Services.  
  
-   Créer un port de réception FILE unidirectionnel pour recevoir le message test EDI à envoyer via le transport AS2. Créer le dossier local pour recevoir le message test.  
  
-   Créer un port d'envoi HTTP bidirectionnel statique pour [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour envoyer à Fabrikam le message AS2 contenant le document commercial EDI et recevoir la réponse MDN. Configurer le pipeline d'envoi pour être le pipeline AS2Send et le pipeline de réception pour être le pipeline AS2Receive.  
  
-   Créer un port de réception HTTP bidirectionnel pour [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour recevoir le message AS2 et envoyer la réponse MDN. Configurer le pipeline de réception pour être le pipeline AS2Receive et le pipeline d'envoi pour être le pipeline AS2Send. Configurer l'emplacement de réception pour recevoir le message AS2 via le répertoire virtuel de Fabrikam.  
  
    > [!NOTE]
    >  Cette solution cible un seul et unique ordinateur. Par conséquent, le port d'envoi bidirectionnel qui envoie le message AS2 (de Contoso) et le port de réception bidirectionnel recevant le message AS2 (en tant que Fabrikam) sont sur le même ordinateur.  
  
-   Créer un port d'envoi FILE unidirectionnel statique (avec un pipeline d'envoi PassThrough) pour router le MDN vers un dossier local. Créer le dossier local.  
  
-   Créer un port d'envoi FILE unidirectionnel statique (avec un pipeline d'envoi PassThrough) pour router la charge de message vers un dossier local. Créer le dossier local.  
  
    > [!NOTE]
    >  Si vous n'avez aucun port d'envoi abonné à la charge de message, il est interrompu dans la base de données MessageBox.  
  
-   Créer un tiers (partenaire commercial) pour Fabrikam et Contoso.  
  
-   Créer un profil d'entreprise pour les deux parties commerciales.  
  
-   Créer un accord AS2 entre les profils d'entreprise pour Fabrikam et Contoso. L’accord AS2 contiendra les propriétés pour envoyer un message AS2 et la réception d’un MDN synchrone en retour.  
  
-   Tester la procédure pas à pas en utilisant un échange EDI test.  
  
    > [!NOTE]
    >  Pour un message test, vous pouvez utiliser le fichier SamplePO.txt utilisé dans le didacticiel pour développeur d'interface EDI. Ce fichier figure dans le dossier [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]\SDK\EDI Interface Developer Tutorial\. Il s'agit d'un message X12 850.  
  
### <a name="configuring-the-walkthrough"></a>Configuration de la procédure pas à pas  
 Cette section décrit les étapes de configuration de la procédure pas à pas.  
  
##### <a name="to-deploy-the-message-schema"></a>Pour déployer le schéma de message  
  
1.  Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], créez ou ouvrez un projet BizTalk.  
  
    > [!NOTE]
    >  Cette rubrique part du principe que vous avez déjà ajouté une référence de votre application à l'application BizTalk EDI, qui contient les schémas, pipelines et orchestrations EDI. Dans le cas contraire, consultez [comment ajouter une référence à l’Application EDI de BizTalk Server](http://msdn.microsoft.com/library/7af066fb-372f-4709-b566-c8d6b4a9d782).  
  
2.  Avec le bouton droit de votre projet, pointez sur **ajouter**, puis cliquez sur **élément existant**. Pour utiliser le fichier SamplePO.txt pour tester votre solution, accédez au dossier [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial\Inbound_EDI. Sélectionnez le schéma X12_00401_850.xsd, puis cliquez sur **ajouter**.  
  
    > [!NOTE]
    >  Pour utiliser un autre schéma EDI, rendez-vous sur le [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_SchemaEDI dossier. Si les schémas EDI n’ont pas été décompressés dans les dossiers XSD_SchemaEDI, exécutez le **MicrosoftEdiXSDTemplates.exe** fichier dans le dossier XSD_SchemaEDI pour décompresser les schémas dans le dossier par défaut.  
  
3.  Définissez le fichier de clé d'assembly, puis créez et déployez l'assembly.  
  
##### <a name="to-enable-the-bts-isapi-filter"></a>Pour activer le filtre ISAPI BTS  
  
1.  Cliquez sur **Démarrer**, pointez sur **Tous les programmes**, puis sur **Outils d'administration**, puis cliquez sur **Gestionnaire des services Internet (IIS)**.  
  
    > [!TIP]
    >  Selon le système d'exploitation utilisé, l'option Outils d'administration du menu Démarrer peut être indisponible. Dans ce cas, cliquez sur **Démarrer**, cliquez sur **exécuter**, puis entrez `inetmgr` pour ouvrir le Gestionnaire des Services Internet (IIS).  
  
2.  Sélectionnez l’entrée de serveur Web racine et dans le **affichage des fonctionnalités**, double-cliquez sur **mappages de gestionnaires** , puis dans le volet Actions cliquez sur **ajouter un mappage de scripts**.  
  
    > [!NOTE]
    >  Configurer le mappage du script au niveau du serveur Web entraîne ce mappage à appliquer à tous les enfants de Sites Web. Si vous souhaitez limiter le mappage à un Site Web ou un dossier virtuel spécifique, sélectionnez le site cible ou le dossier au lieu du serveur Web.  
  
3.  Dans le **ajouter un mappage de scripts** boîte de dialogue, entrez `BtsHttpReceive.dll` dans les **chemin d’accès de la demande** champ.  
  
4.  Dans le **exécutable** , cliquez sur le **points de suspension (...)**  bouton et accédez à [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]HttpReceive. Sélectionnez BtsHttpReceive.dll, puis cliquez sur **OK**.  
  
5.  Entrez `BizTalk HTTP Receive` dans les `Name` champ, puis cliquez sur **Restrictions des demandes**.  
  
6.  Dans le **Restrictions des demandes** boîte de dialogue, sélectionnez le **verbes** onglet, puis sélectionnez **un des verbes suivants**. Entrez `POST` le verbe.  
  
7.  Sur le **accès** onglet, sélectionnez **Script** puis cliquez sur **OK**.  
  
8.  Cliquez sur **OK** lorsque vous êtes invité à autoriser l’extension ISAPI, cliquez sur **Oui**.  
  
##### <a name="to-configure-the-fabrikam-web-page"></a>Pour configurer la page Web Fabrikam  
  
1.  Avec le bouton droit dans le Gestionnaire des services Internet, **Pools d’applications** et sélectionnez **ajouter un Pool d’applications**.  
  
2.  Dans **ajouter le Pool d’applications** boîte de dialogue, entrez **BizTalkAppPool** dans **nom**, puis sélectionnez **.NET Framework V4.0.30210** dans le **Version du .NET framework** liste déroulante. Cliquez sur **OK**.  
  
    > [!NOTE]
    >  Le numéro de version peut varier selon la version de [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] installée sur l'ordinateur.  
  
3.  Sélectionnez **Pools d’applications**, dans le **affichage des fonctionnalités** sélectionnez **BizTalkAppPool**, puis cliquez sur **paramètres avancés** dans les  **Actions** volet.  
  
4.  Dans le **paramètres avancés** boîte de dialogue, sélectionnez **identité** puis cliquez sur le bouton de sélection (...).  
  
5.  Dans le **identité du Pool d’applications** boîte de dialogue, sélectionnez **compte personnalisé** puis cliquez sur **définir**.  
  
6.  Entrez le **nom d’utilisateur** et **mot de passe** pour un compte d’utilisateur qui est membre du groupe Administrateurs, entrez le mot de passe **confirmer le mot de passe** puis cliquez sur **OK** trois fois pour retourner le Gestionnaire des services Internet.  
  
7.  Dans le Gestionnaire des services Internet, ouvrez le **Sites** dossier. Cliquez sur le **Site Web par défaut** nœud et sélectionnez **ajouter une Application**.  
  
8.  Dans le **ajouter une Application** boîte de dialogue, entrez **Fabrikam** dans **Alias**, puis cliquez sur **sélectionnez**.  
  
9. Dans le **sélectionner un Pool d’applications** boîte de dialogue, sélectionnez **BizTalkAppPool** et cliquez sur **OK**.  
  
10. Cliquez sur le bouton de sélection (...) et accédez à [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]HttpReceive pour le **chemin d’accès physique**.  
  
11. Cliquez sur **des paramètres de Test** et vérifiez qu’il n’y a aucune erreur affiché dans le **tester la connexion** boîte de dialogue. Cliquez sur **Fermer**, puis sur **OK**.  
  
12. Dans le Gestionnaire des services Internet, sélectionnez le répertoire virtuel Fabrikam et dans le **affichage des fonctionnalités**, double-cliquez sur **authentification**.  
  
13. Dans le **authentification** page, sélectionnez **l’authentification anonyme** et vérifiez que le **état** est **activé**. Si le **état** est **désactivé**, cliquez sur **activer** dans les **Actions** volet.  
  
##### <a name="to-specify-that-your-virtual-directory-is-not-managed-by-windows-sharepoint-services"></a>Pour spécifier que votre répertoire virtuel n'est pas géré par les Windows SharePoint Services  
  
1.  Si Windows SharePoint Services est installé sur votre ordinateur, cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **outils d’administration**, puis cliquez sur **Administration centrale de SharePoint 3.0**.  
  
    > [!NOTE]
    >  Cette procédure est requise si Windows SharePoint Server est installé sur l'ordinateur sur lequel vous configurez la procédure pas à pas. Dans ce cas, vous devez spécifier que votre répertoire virtuel IIS n'est pas géré par Windows SharePoint Server.  
  
2.  Sur le **Administration centrale** sous **Administration centrale**, cliquez sur **gestion des applications**.  
  
3.  Sur le **gestion des applications** , cliquez sur **définir les chemins d’accès gérés**.  
  
4.  Dans le **définir les chemins d’accès gérés** sous **ajouter un nouveau chemin**, dans le **chemin d’accès** texte, entrez `Fabrikam`. Sous **Type**, cliquez sur **chemin d’accès exclu**, puis cliquez sur **OK**.  
  
##### <a name="to-create-a-receive-port-to-receive-the-edi-test-message"></a>Pour créer un port de réception pour recevoir le message test EDI  
  
1.  Dans l'Explorateur Windows, créez un dossier local pour recevoir l'échange EDI à partir de Contoso.  
  
2.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration, avec le bouton droit le **Ports de réception** nœud sous la **BizTalk Application 1** nœud, pointez sur **nouveau**, puis cliquez sur  **Unidirectionnel Port de réception**.  
  
3.  Nommez le port de réception **RecvISAFromCont**, puis cliquez sur **emplacements de réception** dans l’arborescence de la console.  
  
4.  Cliquez sur **Nouveau**.  
  
5.  Nom de l’emplacement de réception, sélectionnez **fichier** pour **Type**, puis cliquez sur **configurer**.  
  
6.  Pour **dossier de réception**, entrez le nom du dossier que vous avez créé à l’étape 1.  
  
7.  Pour **masque de fichier**, entrez l’extension de votre fichier. Si vous utilisez le fichier SamplePO.txt comme message test, entrez  **\*.txt**. Cliquez sur **OK**.  
  
8.  Pour **pipeline de réception**, acceptez la valeur par défaut **PassThruReceive**.  
  
9. Cliquez sur **OK**, puis cliquez sur **OK** à nouveau.  
  
10. Cliquez sur le **emplacements de réception** nœud, cliquez sur votre emplacement de réception, puis cliquez sur **activer**.  
  
##### <a name="to-create-a-two-way-send-port-to-send-the-edi-interchange-over-as2-to-fabrikam-and-receive-an-mdn-response"></a>Pour créer un port d'envoi bidirectionnel pour envoyer à Fabrikam l'échange EDI via le transport AS2 et recevoir une réponse MDN  
  
1.  > [!NOTE]
    >  Un port d'envoi bidirectionnel statique récupère l'échange EDI et le code au format AS2. Il envoie ensuite l'échange EDI AS2, via le transport AS2, au tiers Fabrikam. Le port de réception associé au port d'envoi bidirectionnel reçoit le MDN de Fabrikam, puis le dépose dans la base de données MessageBox.  
  
     Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration, avec le bouton droit le **Ports d’envoi** nœud sous la **BizTalk Application 1** nœud, pointez sur **nouveau**, puis cliquez sur **Port d’envoi statique avec sollicitation-réponse**.  
  
2.  Dans le **propriétés de Port d’envoi** boîte de dialogue, le nom du port d’envoi. Pour cette solution, nommez le port d’envoi **SendISAToFab_RecMDN**.  
  
3.  Dans le **Transport** section, sélectionnez **HTTP** pour **Type**, puis cliquez sur **configurer**.  
  
4.  Dans le **propriétés du Transport HTTP** boîte de dialogue, pour **URL de Destination**, entrez **http://localhost/Fabrikam/BTSHttpReceive.dll**.  
  
5.  Désactivez **activer le codage mémorisé en bloc**, puis cliquez sur **OK**.  
  
6.  Dans **pipeline d’envoi**, sélectionnez **AS2Send**.  
  
7.  Dans **pipeline de réception**, sélectionnez **AS2Receive**.  
  
8.  Dans l’arborescence de la console, sélectionnez **filtres**. Pour **propriété**, entrez **BTS. ReceivePortName**; pour **opérateur**, entrez  **==** ; et pour **valeur** Entrez le nom du port de réception qui recevra l’EDI échange (`RecvISAFromCont`).  
  
9. Cliquez sur **OK**.  
  
10. Cliquez sur le **Ports d’envoi** nœud dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, cliquez sur le port d’envoi, puis cliquez sur **Démarrer**.  
  
##### <a name="to-create-a-two-way-receive-port-to-receive-the-as2-message-and-return-an-mdn"></a>Pour créer un port de réception bidirectionnel pour recevoir le message AS2 et renvoyer un MDN  
  
1.  > [!NOTE]
    >  Le port de réception bidirectionnel, au niveau de Fabrikam, reçoit le message AS2 à l'aide du répertoire virtuel de Fabrikam. Le pipeline de réception décode l'échange EDI à partir d'AS2, puis dépose l'échange EDI dans la base de données MessageBox. Le port d'envoi associé au port de réception bidirectionnel renvoie un MDN synchrone.  
  
     Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la console, sous le **BizTalk Application 1** nœud, avec le bouton droit **Ports de réception**, pointez sur **nouveau**, puis cliquez sur **Port de réception de requête réponse**.  
  
2.  Nommez le port de réception **RecvAS2ForFab**, puis cliquez sur **emplacements de réception** dans l’arborescence de la console.  
  
3.  Cliquez sur **Nouveau**.  
  
4.  Dans le **propriétés de l’emplacement de réception** boîte de dialogue, le nom de votre emplacement de réception, sélectionnez **HTTP** pour **Type**, puis cliquez sur **configurer**.  
  
5.  Dans le **propriétés du Transport HTTP** boîte de dialogue, entrez **/Fabrikam/BTSHttpReceive.dll** pour **répertoire virtuel assorti de l’extension ISAPI**. Désactivez **un descripteur de corrélation de retour en cas de réussite** et sélectionnez **suspendre les requêtes ayant échoué**. Cliquez sur **OK**.  
  
6.  Sélectionnez **AS2Receive** pour le **Pipeline de réception**, et **AS2Send** pour le **Pipeline d’envoi**. Cliquez sur **OK**, puis cliquez sur **OK** à nouveau.  
  
7.  Cliquez sur le **emplacements de réception** nœud, cliquez sur votre emplacement de réception, puis cliquez sur **activer**.  
  
##### <a name="to-create-a-send-port-to-send-the-edi-payload-to-a-local-folder"></a>Pour créer un port d'envoi pour envoyer la charge EDI vers un dossier local  
  
1.  Dans l'Explorateur Windows, créez un dossier local auquel envoyer l'échange EDI.  
  
2.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration, avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi unidirectionnel statique**.  
  
3.  Dans le **propriétés de Port d’envoi** boîte de dialogue Nom de votre port d’envoi **SendEDIMsg**. Sélectionnez **fichier** pour **Type**, puis cliquez sur **configurer**.  
  
4.  Dans le **propriétés du Transport FILE** boîte de dialogue, pour **dossier de Destination**, entrez le dossier local que vous avez créé pour la charge EDI.  
  
5.  Pour **nom de fichier**, entrez le nom de fichier. Si vous utilisez le fichier SamplePO.txt comme message test, entrez **%MessageID%.txt**. Cliquez sur **OK**.  
  
6.  Acceptez la valeur par défaut **PassThruTransmit** pour **Pipeline d’envoi**.  
  
7.  Cliquez sur **filtres** dans la console de l’arborescence et ajouter des propriétés de filtre pour la sélection de la charge EDI. Sur la première ligne, pour **propriété**, entrez **BTS. ReceivePortName**; pour **opérateur**, entrez  **==** ; pour **valeur**, entrez le nom du port de réception qui reçoit le AS2 message (`RecvAS2ForFab`) ; et pour **regrouper par**, accepter **et**. Sur la deuxième ligne, pour **propriété**, entrez **EdiIntAS.IsAS2PayloadMessage**; pour **opérateur**, entrez  **==** ; et **Valeur**, entrez **True**.  
  
8.  Cliquez sur **OK**.  
  
9. Cliquez sur le **Ports d’envoi** nœud, cliquez sur le port d’envoi, puis cliquez sur **Démarrer**.  
  
##### <a name="to-create-a-send-port-to-send-the-mdn-to-a-local-folder"></a>Pour créer un port d'envoi pour envoyer le MDN vers un dossier local  
  
1.  Dans l'Explorateur Windows, créez un dossier local auquel envoyer le MDN.  
  
2.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration, avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi unidirectionnel statique**.  
  
3.  Dans le **propriétés de Port d’envoi** boîte de dialogue Nom de votre port d’envoi **SendMDN**. Sélectionnez **fichier** pour **Type**, puis cliquez sur **configurer**.  
  
4.  Dans le **propriétés du Transport FILE** boîte de dialogue, pour **dossier de Destination**, entrez le dossier local que vous avez créé pour envoyer le MDN.  
  
5.  Pour **nom de fichier**, entrez **%MessageID%.msg**. Cliquez sur **OK**.  
  
6.  Acceptez la valeur par défaut **PassThruTransmit** pour **Pipeline d’envoi**.  
  
7.  Cliquez sur **filtres** dans l’arborescence de la console. Pour **propriété**, entrez **BTS. SPName**; pour **opérateur**, entrez  **==** ; pour **valeur**, entrez le nom du port d’envoi qui envoie le message AS2 (`SendISAToFab_RecMDN`); et pour **regrouper par**, accepter **et**. Sur la deuxième ligne, pour **propriété**, entrez **EdiIntAS.IsAS2MdnResponseMessage**; pour **opérateur**, entrez  **==** ; pour **Valeur**, entrez **True**.  
  
8.  Cliquez sur **OK**.  
  
9. Cliquez sur le **Ports d’envoi** nœud, cliquez sur le port d’envoi, puis cliquez sur **Démarrer**.  
  
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
  
1.  Avec le bouton droit **Contoso_Profile**, pointez sur **nouveau**, puis cliquez sur **accord**.  
  
2.  Dans le **propriétés générales** page, pour le **nom** texte, entrez un nom pour l’accord.  
  
3.  À partir de la **protocole** la liste déroulante, sélectionnez **AS2**.  
  
4.  Dans le **deuxième partenaire** section, à partir de la **nom** la liste déroulante, sélectionnez **Fabrikam**.  
  
5.  Dans le **deuxième partenaire** section, à partir de la **profil** la liste déroulante, sélectionnez **Fabrikam_Profile**.  
  
     Vous remarquerez que les deux nouveaux onglets sont ajoutés à côté du **général** onglet. Chaque onglet permet de configurer un accord AS2 unidirectionnel.  
  
6.  Effectuer les tâches suivantes sur le **Contoso -> Fabrikam** onglet.  
  
    1.  Sur le **identificateurs** , entrez des valeurs pour **AS2-de** et **AS2-pour**. Pour **AS2-de**, entrez `Contoso`. Pour **AS2 - To**, entrez `Fabrikam`.  
  
    2.  Dans le **accusés de réception (MDN)** page, procédez comme suit :  
  
        1.  Sélectionnez le **traiter le MDN entrant dans MessageBox pour les options de routage/livraison** case à cocher.  
  
            > [!NOTE]
            >  Vérification de la **traiter le MDN entrant dans MessageBox pour les options de routage/livraison** est requise pour le test de cette procédure pas à pas, car seuls puis sera le MDN renvoyé supprimé dans la MessageBox. Cela vous permet de créer un port d'envoi abonné au MDN et d'envoyer le MDN vers un répertoire local, afin que vous puissiez vérifier la transmission AS2.  
  
        2.  Sélectionnez le **exiger le MDN** case à cocher.  
  
        3.  Assurez-vous que le **exiger le MDN signé** case à cocher est désactivée.  
  
        4.  Laissez **exiger le MDN asynchrone** désactivée.  
  
        5.  Dans **Disposition-Notification-To**, entrez une valeur quelconque. La valeur de ce champ n'est pas utilisée lors du traitement AS2, mais une valeur doit être entrée dans le champ.  
  
    3.  Sur le **Ports d’envoi** page, associez le port d’envoi bidirectionnel qui envoie l’échange EDI à Fabrikam. Dans le **ports d’envoi** grille, sous la **nom** colonne, cliquez sur une cellule vide et dans la liste déroulante, sélectionnez le port d’envoi **SendISAToFab_RecMDN**.  
  
7.  Effectuer les tâches suivantes sur le **Fabrikam -> Contoso** onglet.  
  
    > [!NOTE]
    >  Dans cette procédure pas à pas, la valeur requise est spécifiée sous l'onglet afin de permettre la création d'un accord. Pour créer un accord, les deux onglets d’accord unidirectionnel doivent avoir des valeurs définies pour **AS2_From** et **AS2-pour**.  
  
    1.  Sur le **identificateurs** , entrez des valeurs pour **AS2-de** et **AS2-pour**. Pour **AS2-de**, entrez `Fabrikam`. Pour **AS2 - To**, entrez `Contoso`.  
  
8.  Cliquez sur **Appliquer**.  
  
9. Cliquez sur **OK**. Le nouvel accord ajouté est répertorié dans le **accords** section de la **tiers et profils d’entreprise** volet. Le nouvel accord ajouté est activé par défaut.  
  
### <a name="testing-the-walkthrough"></a>Test de la procédure pas à pas  
 Cette section fournit des informations sur le test de la procédure pas à pas.  
  
##### <a name="to-test-the-solution"></a>Pour tester la solution  
  
1.  Dans l'Explorateur Windows, accédez à [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial. Copie le **SamplePO.txt** fichier.  
  
2.  Coller le **SamplePO.txt** fichier dans le dossier local que vous avez créé pour recevoir le message de test de Contoso.  
  
3.  Accédez au dossier local que vous avez créé, auquel envoyer la charge EDI. Confirmez que le dossier contient un fichier EDI. Ouvrez le fichier et le message test d'origine, puis vérifiez qu'ils ont le même contenu.  
  
4.  Accédez au dossier local que vous avez créé, auquel envoyer le MDN résultant. Confirmez que le dossier contient bien un fichier. Ouvrez le fichier, puis confirmez qu'il s'agit d'un fichier MDN.  
  
## <a name="see-also"></a>Voir aussi  
 [Développement et la configuration des Solutions AS2 BizTalk Server](../core/developing-and-configuring-biztalk-server-as2-solutions.md)