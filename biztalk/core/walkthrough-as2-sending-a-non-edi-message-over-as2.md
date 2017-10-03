---
title: "Procédure pas à pas (AS2) : Envoi d’un Message Non-EDI via AS2 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6120b81e-bdd5-44ad-9040-26be88c71258
caps.latest.revision: "33"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a37daa53e5c8d78efdb22fd6f37b15365cde73a2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="walkthrough-as2-sending-a-non-edi-message-over-as2"></a>Procédure (AS2) : Envoi d'un message non EDI via AS2
Cette procédure pas à pas fournit des instructions détaillées sur la création d'une solution d'envoi de message non-EDI via AS2. Dans cette procédure, un message PIDX est envoyé via AS2. La solution utilise un port d'envoi bidirectionnel avec un pipeline d'envoi AS2Send et un pipeline de réception AS2Receive. Vous pouvez créer et tester la solution complète dans cette procédure pas à pas sur un seul ordinateur.  
  
## <a name="prerequisites"></a>Conditions préalables  
 La configuration requise pour exécuter la procédure décrite dans cette rubrique est la suivante :  
  
-   Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
-   Internet Information Services (IIS) 7 doit être installé sur l'ordinateur sur lequel est exécutée la procédure pas à pas.  
  
-   Si une version 64 bits de Windows est installée sur l'ordinateur sur lequel est exécutée la procédure pas à pas, vous devez vérifier que les hôtes BizTalk sont marqués comme applications 32 bits uniquement. Vous devez également vérifier que le paramètre Activer les applications 32 bits pour les pools d'applications est défini sur True pour IIS. Pour plus d’informations, consultez [didacticiel 3 : didacticiel AS2](../core/tutorial-3-as2-tutorial.md).  
  
## <a name="how-the-solution-sends-a-non-edias2-message-and-returns-a-synchronous-mdn"></a>Envoi d'un message non-EDI/AS2 et renvoi d'un MDN synchrone par la solution  
 La solution effectue les opérations suivantes :  
  
1.  Un port de réception FILE unidirectionnel reçoit un message XML de Contoso.  
  
    > [!NOTE]
    >  Les événements dans cette liste peuvent se produire dans un ordre différent de celui indiqué.  
  
2.  À l'aide du pipeline de réception XML, le port de réception contrôle le message. Le port de réception dépose ensuite le message tel quel dans la base de données MessageBox.  
  
3.  Un port d'envoi bidirectionnel statique récupère le message XML, en s'abonnant aux messages reçus par le port de réception.  
  
4.  Le port de réception bidirectionnel, au niveau de Fabrikam, reçoit le message AS2 à l'aide du répertoire virtuel de Fabrikam. Le pipeline de réception décode le message à partir d'AS2, puis dépose le message dans la base de données MessageBox.  
  
5.  Un port d'envoi unidirectionnel statique, avec un pipeline d'envoi PassThrough, récupère le message XML.  
  
6.  Le port d'envoi unidirectionnel envoie le message XML vers un dossier local.  
  
7.  Le port d'envoi associé au port de réception bidirectionnel renvoie un MDN synchrone.  
  
8.  Le port de réception associé au port d'envoi bidirectionnel reçoit le MDN, puis le dépose dans la base de données MessageBox.  
  
9. Un port d'envoi unidirectionnel statique, avec un pipeline d'envoi PassThrough, récupère le MDN.  
  
10. Le port d'envoi unidirectionnel envoie le MDN vers un dossier local.  
  
 L'architecture de la solution est représentée dans la figure suivante.  
  
 ![Envoi d’un non &#45; Message EDI sur AS2](../core/media/57b7dc54-b8e8-462e-98d1-9cddedd14107.gif "57b7dc54-b8e8-462e-98d1-9cddedd14107")  
  
## <a name="the-functionality-in-this-solution"></a>Fonctionnalités dans la solution  
 Les conditions suivantes s'appliquent aux fonctionnalités de cette procédure pas à pas :  
  
-   Cette procédure porte sur la fonctionnalité AS2. Par conséquent, tous les ports impliqués dans le traitement AS2 utilisent le pipeline AS2Receive ou AS2Send. Les ports qui ne sont pas impliqués dans le traitement AS2 utilisent le pipeline XMLReceive ou PassThruTransmit.  
  
-   Cette procédure utilise un message test XML.  
  
    > [!NOTE]
    >  Vous devez fournir un message test XML et un schéma pour le message test.  
  
-   Le rapport d'état n'est pas activé.  
  
-   Cette solution ne configure pas la signature, la compression, le chiffrement ou le stockage des messages dans la base de données de non-répudiation. Pour les procédures de configuration de ces propriétés, consultez [configuration des propriétés AS2](../core/configuring-as2-properties.md).  
  
## <a name="configuring-and-testing-the-walkthrough"></a>Configuration et test de la procédure pas à pas  
 Les étapes suivantes sont requises pour configurer cette solution :  
  
-   Créer et déployer un projet BizTalk avec le schéma de message requis, le schéma pouvant être utilisé par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dans le cadre du traitement du message reçu.  
  
-   Activer le filtre BTS ISAPI utilisé pour la réception du message AS2.  
  
-   Créer un répertoire virtuel Fabrikam recevant le message AS2 de Contoso, comme configuré dans l'emplacement de réception.  
  
-   Spécifier que le répertoire virtuel de Fabrikam n'est pas géré par Windows SharePoint Services.  
  
-   Créer un port de réception FILE unidirectionnel pour recevoir le message test XML à envoyer via le transport AS2. Créer le dossier local pour recevoir le message test.  
  
-   Créer un port d'envoi HTTP de sollicitation-réponse statique en configurant le pipeline d'envoi pour être le pipeline AS2Send et le pipeline de réception pour être le pipeline AS2Receive. Le port envoie le message AS2 à Fabrikam, puis reçoit la réponse MSN de Fabrikam qu'il dépose dans la base de données MessageBox.  
  
-   Créer un port de réception HTTP bidirectionnel pour [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour recevoir le message AS2 et envoyer la réponse MDN. Configurer le pipeline de réception pour être le pipeline AS2Receive et le pipeline d'envoi pour être le pipeline AS2Send. Configurer l'emplacement de réception pour recevoir le message AS2 via le répertoire virtuel de Fabrikam.  
  
    > [!NOTE]
    >  La solution test se trouve sur un seul et unique ordinateur. Par conséquent, le port d'envoi bidirectionnel qui envoie le message AS2 (de Contoso) et le port de réception bidirectionnel qui reçoit le message AS2 (en tant que Fabrikam) sont sur le même ordinateur.  
  
-   Créer un port d'envoi FILE unidirectionnel statique (avec un pipeline d'envoi PassThrough) pour router la charge XML de message vers un dossier local. Créer le dossier local.  
  
    > [!NOTE]
    >  Si vous n'avez aucun port d'envoi abonné à la charge de message, il est interrompu dans la base de données MessageBox.  
  
-   Créer un port d'envoi FILE unidirectionnel statique (avec un pipeline d'envoi PassThrough) pour router le MDN vers un dossier local. Créer le dossier local.  
  
-   Créer un tiers (partenaire commercial) pour Fabrikam et Contoso.  
  
-   Créer un profil d'entreprise pour les deux parties commerciales.  
  
-   Créer un accord AS2 entre les profils d'entreprise pour Fabrikam et Contoso. L’accord AS2 contiendra les propriétés pour envoyer un message AS2 et la réception d’un MDN synchrone en retour.  
  
-   Tester la procédure avec un message test XML.  
  
### <a name="configuring-the-walkthrough"></a>Configuration de la procédure pas à pas  
 Cette section décrit les étapes de configuration de la procédure pas à pas.  
  
##### <a name="to-deploy-the-test-message-schema"></a>Pour déployer le schéma de message test  
  
1.  Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], créez ou ouvrez un projet BizTalk.  
  
    > [!NOTE]
    >  Cette rubrique part du principe que vous avez déjà ajouté une référence de votre application à l'application BizTalk EDI, qui contient les schémas, pipelines et orchestrations EDI. Dans le cas contraire, consultez [comment ajouter une référence à l’Application EDI de BizTalk Server](http://msdn.microsoft.com/library/7af066fb-372f-4709-b566-c8d6b4a9d782).  
  
2.  Avec le bouton droit de votre projet, pointez sur **ajouter**, puis cliquez sur **élément existant**. Pour tester votre solution à l'aide d'un fichier XML, accédez au dossier local qui contient le schéma XSD du message test XML, puis sélectionnez le fichier XSD. Cliquez sur **Ajouter**.  
  
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
  
##### <a name="to-create-a-receive-port-to-receive-the-test-message"></a>Pour créer un port de réception pour recevoir le message test  
  
1.  Dans l'Explorateur Windows, créez un dossier local pour recevoir l'échange EDI à partir de Contoso.  
  
2.  Dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, avec le bouton droit le **Ports de réception** nœud sous la **BizTalk Application 1** nœud **nouveau**, puis cliquez sur **Unidirectionnel Port de réception**.  
  
3.  Dans le **propriétés du Port de réception** boîte de dialogue, nommez la réception port **RecvXMLFromCont**.  
  
4.  Cliquez sur **emplacements de réception** dans l’arborescence de la console, puis cliquez sur **nouveau**.  
  
5.  Nom de l’emplacement de réception, sélectionnez **fichier** pour **Type**, puis cliquez sur **configurer**.  
  
6.  Pour **dossier de réception**, entrez le nom du dossier que vous avez créé à l’étape 1.  
  
7.  Dans **masque de fichier**, entrez  **\*.xml**, puis cliquez sur **OK**.  
  
8.  Dans le pipeline de réception, sélectionnez **XMLReceive**.  
  
    > [!NOTE]
    >  Si vous utilisez un autre type de fichier non-EDI, autre que XML, entrez **PassThruTranmit**.  
  
9. Cliquez sur **OK**, puis cliquez sur **OK** à nouveau.  
  
10. Cliquez sur le **emplacements de réception** nœud, cliquez sur votre emplacement de réception, puis cliquez sur **activer**.  
  
##### <a name="to-create-a-send-port-to-send-the-as2-message-to-fabrikam"></a>Pour créer un port d'envoi pour envoyer le message AS2 à Fabrikam  
  
1.  Dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, avec le bouton droit le **Ports d’envoi** nœud sous la **BizTalk Application 1** nœud **nouveau**, puis cliquez sur **Port d’envoi statique avec sollicitation-réponse**.  
  
    > [!NOTE]
    >  Si vous utilisez l'application BizTalk Application 1, vous devez y ajouter une référence à l'application EDI BizTalk, afin que votre application puisse utiliser ses artefacts. Pour plus d’informations, consultez [comment ajouter une référence à l’Application EDI de BizTalk Server](http://msdn.microsoft.com/library/7af066fb-372f-4709-b566-c8d6b4a9d782).  
  
2.  Dans le **propriétés de Port d’envoi** boîte de dialogue, nommez le port d’envoi **SendToFab_RecvMDN**.  
  
3.  Dans le **Transport** section, sélectionnez **HTTP** pour **Type**, puis cliquez sur **configurer**.  
  
4.  Dans le **propriétés du Transport HTTP** boîte de dialogue, pour **URL de Destination**, entrez **http://localhost/Fabrikam/BTSHttpReceive.dll**.  
  
5.  Désactivez **activer le codage segmenté**. Cliquez sur **OK**.  
  
6.  Pour **pipeline d’envoi**, sélectionnez **AS2Send**.  
  
7.  Pour **pipeline de réception**, sélectionnez **AS2Receive**.  
  
8.  Dans l’arborescence de la console, sélectionnez **filtres**. Pour **propriété**, entrez **BTS. ReceivePortName**; pour **opérateur**, entrez  **==** ; et pour **valeur** Entrez le nom du port de réception qui recevra l’EDI échange (`RecvXMLFromCont`).  
  
    > [!NOTE]
    >  Si vous envoyez un message PIDX, vous pouvez créer une expression de filtre qui filtre sur le type du message (**PIDX**).  
  
9. Si vous souhaitez appliquer un mappage pour transformer le document XML, cliquez sur **mappages sortants** dans l’arborescence de la console. Entrez le **Document Source** pour le mappage sortant, sélectionnez le **carte**, puis entrez le **Document cible**. Cliquez sur **OK**.  
  
10. Cliquez sur **OK**.  
  
11. Cliquez sur le **Ports d’envoi** nœud dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, cliquez sur le port d’envoi, puis cliquez sur **Démarrer**.  
  
##### <a name="to-create-a-receive-port-to-receive-the-as2-message-and-return-an-acknowledgment"></a>Pour créer un port de réception pour recevoir le message AS2 et renvoyer un accusé de réception  
  
1.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la Console, sous le **BizTalk Application 1** nœud, avec le bouton droit **Ports de réception**, pointez sur **nouveau**, puis cliquez sur **Port de réception de requête réponse**.  
  
2.  Nommez le port de réception **RecvAS2Msg**, puis cliquez sur **emplacements de réception** dans l’arborescence de la console.  
  
3.  Cliquez sur **Nouveau**.  
  
4.  Dans le **propriétés de l’emplacement de réception** boîte de dialogue, le nom de votre emplacement de réception, sélectionnez **HTTP** pour **Type**, puis cliquez sur **configurer**.  
  
5.  Dans le **propriétés du Transport HTTP** boîte de dialogue, entrez **/Fabrikam/BTSHttpReceive.dll** pour **répertoire virtuel assorti de l’extension ISAPI**. Désactivez **un descripteur de corrélation de retour en cas de réussite** et sélectionnez **suspendre les requêtes ayant échoué**. Cliquez sur **OK**.  
  
6.  Sélectionnez **AS2Receive** pour le **Pipeline de réception**, et **AS2Send** pour le **Pipeline d’envoi**. Cliquez sur **OK**, puis cliquez sur **OK** à nouveau.  
  
7.  Cliquez sur le **emplacements de réception** nœud, cliquez sur votre emplacement de réception, puis cliquez sur **activer**.  
  
##### <a name="to-create-a-send-port-to-send-the-test-xml-payload-to-a-local-folder"></a>Pour créer un port d'envoi pour envoyer la charge XML test vers un dossier local  
  
1.  Dans l'Explorateur Windows, créez un dossier local auquel envoyer l'échange EDI.  
  
2.  Dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi unidirectionnel statique**.  
  
3.  Dans le **propriétés de Port d’envoi** boîte de dialogue Nom de votre port d’envoi **SendXMLPayload**. Sélectionnez **fichier** pour **Type**, puis cliquez sur **configurer**.  
  
4.  Dans le **propriétés du Transport FILE** boîte de dialogue, pour **dossier de Destination**, entrez le dossier local que vous avez créé pour la charge EDI.  
  
5.  Pour **nom de fichier**, entrez le nom de fichier. Si vous utilisez un fichier XML comme message test, entrez **%MessageID%.xml**. Cliquez sur **OK**.  
  
6.  Acceptez la valeur par défaut **PassThruTransmit** pour **Pipeline d’envoi**.  
  
7.  Cliquez sur **filtres** dans la console de l’arborescence et ajouter des propriétés de filtre pour la sélection de la charge EDI. Sur la première ligne, pour **propriété**, entrez **BTS. ReceivePortName**; pour **opérateur**, entrez  **==** ; pour **valeur**, entrez le nom du port de réception qui reçoit le AS2 message (`RecvAS2Msg`) ; et pour **regrouper par**, accepter **et**. Sur la deuxième ligne, pour **propriété**, entrez **EdiIntAS.IsAS2PayloadMessage**; pour **opérateur**, entrez  **==** ; et **Valeur**, entrez **True**.  
  
8.  Cliquez sur **OK**.  
  
9. Cliquez sur le **Ports d’envoi** nœud, cliquez sur le port d’envoi, puis cliquez sur **Démarrer**.  
  
##### <a name="to-create-a-send-port-to-send-the-mdn-to-a-local-folder"></a>Pour créer un port d'envoi pour envoyer le MDN vers un dossier local  
  
1.  Dans l'Explorateur Windows, créez un dossier local auquel envoyer le MDN.  
  
2.  Dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi unidirectionnel statique**.  
  
3.  Dans le **propriétés de Port d’envoi** boîte de dialogue Nom de votre port d’envoi **SendMDNToContoso**. Sélectionnez **fichier** pour **Type**, puis cliquez sur **configurer**.  
  
4.  Dans le **propriétés du Transport FILE** boîte de dialogue, pour **dossier de Destination**, entrez le dossier local que vous avez créé pour envoyer le MDN.  
  
5.  Pour **nom de fichier**, entrez **%MessageID%.msg**. Cliquez sur **OK**.  
  
6.  Acceptez la valeur par défaut **PassThruTransmit** pour **Pipeline d’envoi**.  
  
7.  Cliquez sur **filtres** dans l’arborescence de la console. Pour **propriété**, entrez **BTS. SPName**; pour **opérateur**, entrez  **==** ; pour **valeur**, entrez le nom du port d’envoi qui envoie le message AS2 (`SendToFab_RecvMDN`); et pour **regrouper par**, accepter **et**. Sur la deuxième ligne, pour **propriété**, entrez **EdiIntAS.IsAS2MdnResponseMessage**. Pour **opérateur**, entrez  **==** . Pour **valeur**, entrez **True**.  
  
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
  
    3.  Sur le **Ports d’envoi** page, associez le port d’envoi bidirectionnel qui envoie l’échange EDI à Fabrikam. Dans le **ports d’envoi** grille, sous la **nom** colonne, cliquez sur une cellule vide et dans la liste déroulante, sélectionnez le port d’envoi **SendToFab_RecvMDN**.  
  
7.  Effectuer les tâches suivantes sur le **Fabrikam -> Contoso** onglet.  
  
    > [!NOTE]
    >  Dans cette procédure pas à pas, la valeur requise est spécifiée sous l'onglet afin de permettre la création d'un accord. Pour créer un accord, les deux onglets d’accord unidirectionnel doivent avoir des valeurs définies pour **AS2_From** et **AS2-pour**.  
  
    1.  Sur le **identificateurs** , entrez des valeurs pour **AS2-de** et **AS2-pour**. Pour **AS2-de**, entrez `Fabrikam`. Pour **AS2 - To**, entrez `Contoso`.  
  
8.  Cliquez sur **Appliquer**.  
  
9. Cliquez sur **OK**. Le nouvel accord ajouté est répertorié dans le **accords** section de la **tiers et profils d’entreprise** volet. Le nouvel accord ajouté est activé par défaut.  
  
### <a name="testing-the-walkthrough"></a>Test de la procédure pas à pas  
 Cette section fournit des informations sur le test de la procédure pas à pas.  
  
##### <a name="to-test-the-solution"></a>Pour tester la solution  
  
1.  Dans l'Explorateur Windows, collez votre fichier test XML dans le dossier local que vous avez créé pour recevoir le message test de Contoso.  
  
2.  Accédez au dossier local que vous avez créé, auquel envoyer la charge XML. Confirmez que le dossier contient un fichier XML. Ouvrez le fichier et le message test d'origine, puis vérifiez qu'ils ont le même contenu.  
  
3.  Accédez au dossier local que vous avez créé, auquel envoyer le MDN résultant. Confirmez que le dossier contient bien un fichier. Ouvrez le fichier, puis confirmez qu'il s'agit d'un fichier MDN.  
  
## <a name="see-also"></a>Voir aussi  
 [Développement et la configuration des Solutions AS2 BizTalk Server](../core/developing-and-configuring-biztalk-server-as2-solutions.md)   
 [Traitement côté envoi d’un Message Non EDI sortant sur AS2](../core/send-side-processing-of-an-outgoing-non-edi-message-over-as2.md)