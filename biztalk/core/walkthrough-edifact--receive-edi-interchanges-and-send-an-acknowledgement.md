---
title: "Procédure pas à pas (EDIFACT) : Réception d’échanges EDI et envoi d’un accusé de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 02751f0c-8e7e-4879-93e4-8bc475640756
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 566a1c5eec4fe6800f0c1906ed31c35391b23333
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="walkthrough-edifact-receiving-edi-interchanges-and-sending-back-an-acknowledgement"></a>Procédure pas à pas (EDIFACT) : réception d'échanges EDI et envoi d'un accusé de réception
Cette procédure pas à pas fournit des instructions détaillées sur la création d'une solution de réception d'échanges EDIFACT à l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Dans cette solution, un échange EDIFACT est envoyé par un partenaire commercial, Fabrikam, à un autre partenaire commercial, Contoso.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
## <a name="how-the-solution-receives-edifact-interchanges"></a>Réception des échanges EDIFACT par la solution  
 La solution effectue les opérations suivantes :  
  
> [!NOTE]
>  Les événements dans cette liste peuvent se produire dans un ordre différent de celui indiqué.  
  
1.  réception d'un échange de fichier plat EDIFACT de la part du partenaire commercial Fabrikam ;  
  
2.  validation de l'échange EDIFACT selon son schéma, désassemblage du message en XML, puis déplacement du message XML dans la MessageBox ;  
  
3.  génération d'une notification de transactions techniques (réception du message) vers l'échange EDI reçu, puis déplacement dans la MessageBox ;  
  
4.  génération d'une notification de transactions opérationnelles (acceptation ou rejet de l'échange EDI reçu) vers l'échange EDI reçu, puis déplacement dans la MessageBox ;  
  
5.  récupération du message XML par un port d'envoi FILE unidirectionnel, puis assemblage de l'échange du message EDI ;  
  
6.  envoi de l'échange EDI au dossier local Contoso ;  
  
7.  récupération de la notification de transactions techniques par un port d'envoi FILE unidirectionnel, puis assemblage de l'échange ;  
  
8.  envoi de la notification de transactions techniques au dossier local Fabrikam ;  
  
9. récupération de la notification de transactions opérationnelles par un port d'envoi FILE unidirectionnel, puis assemblage de l'échange ;  
  
10. envoi de la notification des transactions opérationnelles à Fabrikam.  
  
## <a name="the-functionality-in-this-solution"></a>Fonctionnalités dans la solution  
 Pour les besoins de cette procédure, la fonctionnalité suivante est activée :  
  
-   La solution est conçue pour les échanges basés sur le codage EDIFACT.  
  
    > [!NOTE]
    >  Pour obtenir des instructions sur la création d’une solution similaire pour les échanges X12, consultez [procédure pas à pas (X12) : réception des échanges EDI et envoi d’un accusé](../core/walkthrough-x12--receive-edi-interchanges-and-send-back-an-acknowledgement.md).  
  
-   La validation de type EDI et la validation étendue sont effectuées sur l'échange entrant.  
  
-   Les notifications de transactions techniques et opérationnelles sont générées de manière à être renvoyées à l'expéditeur de l'échange.  
  
-   La solution utilise un emplacement de réception unidirectionnel avec un type de transport FILE.  
  
    > [!NOTE]
    >  Vous pouvez utiliser un emplacement et un port de réception avec sollicitation-réponse bidirectionnels pour recevoir le message. Toutefois, si vous utilisez cette méthode, vous ne pourrez pas faire appel à un emplacement de réception disposant du type de transport FILE. Pour plus d’informations, consultez [configuration d’un Port de réception des Messages EDI et les accusés de réception](../core/configuring-a-port-to-receive-edi-messages-and-acknowledgments.md).  
  
-   La création de rapports EDI est activée. Les documents informatisés sont enregistrés pour être consultables depuis le rapport État de l'échange.  
  
-   À des fins de test, la solution utilise trois ports d'envoi pour envoyer aux dossiers locaux l'échange EDIFACT ainsi que les accusés de réception créés.  
  
 L'architecture de cette solution est représentée dans la figure suivante :  
  
 ![Réception d’échange EDIFACT et envoi d’un accusé de réception](../core/media/edifact-walkthrough.gif "EDIFACT_Walkthrough")  
  
## <a name="configuring-and-testing-the-walkthrough"></a>Configuration et test de la procédure pas à pas  
 Les étapes suivantes sont requises pour configurer cette solution :  
  
-   Ajouter le ou les schémas de message requis à un projet BizTalk, puis créer et déployer le projet afin que le ou les schémas soient mis à disposition de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] lors du traitement de l'échange reçu.  
  
-   Créer un port de réception unidirectionnel de manière à ce que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] reçoive l'échange EDIFACT en provenance du partenaire commercial, puis génère un accusé de réception. Cet emplacement de réception est lié au dossier de fichiers dans lequel Fabrikam place l'échange EDIFACT à envoyer à Contoso.  
  
    > [!NOTE]
    >  Vous pouvez utiliser sollicitation un double port de réception de réponse et l’emplacement pour recevoir le message, mais si vous le faites, vous ne serez pas en mesure d’utiliser un type de transport de fichier pour l’emplacement de réception.  
  
-   Créer un port d'envoi permettant d'envoyer l'échange EDI à un dossier Contoso local, ainsi qu'un port d'envoi des notifications de transactions techniques et opérationnelles à un dossier Fabrikam local.  
  
    > [!NOTE]
    >  Contrairement aux accusés de réception X12, les types de messages associés aux notifications de transactions techniques et opérationnelles sont identiques. Ainsi, le filtre du port d'envoi créé à l'aide de la propriété de contexte `BTS.MessageType` filtre les deux types de notifications de transactions et les expédie vers le même dossier.  
  
-   Créer un tiers (partenaire commercial) pour Fabrikam et Contoso.  
  
-   Créer un profil d'entreprise pour les deux partenaires commerciaux.  
  
-   Créer un accord entre les deux profils via la configuration des propriétés EDI du message à recevoir et de l'accusé de réception à envoyer.  
  
-   Tester la procédure pas à pas en utilisant un échange EDIFACT. Pour les besoins de cette procédure, vous pouvez copier puis coller ce qui suit dans un fichier texte. Le schéma de ce fichier est EFACT_D98A_APERAK.xsd.  
  
    ```  
    UNA:+,?*'  
    UNB+UNOB:1+7654321:ZZZ+1234567:ZZZ+353501:3023+UNB5'  
    UNG+INVOIC+UNG2.1:ZZZ+UNG3.1:ZZZ+060413:2314+UNG5+UN+D:98B'  
    UNH+UNH1+APERAK:D:98A:UN++13+UNH5.1+UNH6.1+UNH7.1'  
    BGM+1+C10601'  
    DTM+10'  
    FTX+AAA++C10701+C10801'  
    CNT+1:14'  
    RFF+AAA'  
    DTM+10'  
    NAD+AA+C08201+C05801+C08001+C05901'  
    CTA++C05601'  
    COM+C07601:AA'  
    ERC+C90101'  
    FTX+AAA++C10701+C10801'  
    RFF+AAA'  
    FTX+AAA++C10701+C10801'  
    UNT+15+UNH1'  
    UNE+1+UNG5'  
    UNZ+1+UNB5'  
    ```  
  
### <a name="configuring-the-walkthrough"></a>Configuration de la procédure pas à pas  
 Cette section décrit les étapes de configuration de la procédure pas à pas.  
  
##### <a name="to-deploy-the-message-schema"></a>Pour déployer le schéma de message  
  
1.  Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], créez ou ouvrez un projet BizTalk.  
  
    > [!NOTE]
    >  Cette rubrique part du principe que vous avez déjà ajouté une référence de votre application à l'application BizTalk EDI, qui contient les schémas, pipelines et orchestrations EDI. Dans le cas contraire, consultez [comment ajouter une référence à l’Application EDI de BizTalk Server](http://msdn.microsoft.com/library/7af066fb-372f-4709-b566-c8d6b4a9d782).  
  
2.  Avec le bouton droit de votre projet, pointez sur **ajouter**, puis cliquez sur **élément existant**. Accédez au dossier qui est votre schéma [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema\EDI\EDIFACT\D98A, puis double-cliquez sur votre schéma (**EFACT_D98A_APERAK.xsd**).  
  
    > [!NOTE]
    >  Si vous utilisez l’exemple de message de test fourni dans cette rubrique, vous devez utiliser le **EFACT_D98A_APERAK.xsd** schéma.  
  
    > [!NOTE]
    >  Si les schémas EDI n’ont pas été décompressés dans les dossiers \XSD_Schema\EDI, exécutez le **MicrosoftEdiXSDTemplates.exe** fichier dans le dossier \XSD_Schema\EDI pour décompresser les schémas dans le dossier par défaut.  
  
3.  Ajoutez le fichier de clé d'assembly au projet, puis créez et déployez l'assembly.  
  
##### <a name="to-create-a-one-way-receive-port-for-fabrikam-to-receive-the-edi-interchange"></a>Pour créer un port de réception unidirectionnel (pour Fabrikam) permettant de recevoir l'échange EDI  
  
1.  Dans l'Explorateur Windows, créez un dossier local qui recevra l'échange.  
  
2.  Dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, avec le bouton droit le **Ports de réception** nœud sous la **BizTalk Application 1** nœud **nouveau**, puis cliquez sur **Unidirectionnel Port de réception**.  
  
3.  Nommez le port de réception, puis cliquez sur **emplacements de réception** dans l’arborescence de la console.  
  
4.  Cliquez sur **Nouveau**.  
  
5.  Nom de l’emplacement de réception, sélectionnez **fichier** pour **Type**, puis cliquez sur **configurer**.  
  
6.  Accédez à un dossier pour **dossier de réception** zone de texte. Vous avez créé ce dossier au cours de l'étape 1 de cette procédure. Entrez un masque de fichier, tel que  **\*EDI ou** ou  **\*.txt**.  
  
7.  Cliquez sur **OK**.  
  
8.  Pour **pipeline de réception**, sélectionnez **EdiReceive**.  
  
9. Cliquez sur **OK** dans les **propriétés de l’emplacement de réception** boîte de dialogue. Cliquez sur **OK** à nouveau dans le **propriétés du Port de réception** boîte de dialogue.  
  
10. Dans l’arborescence de la console, cliquez sur **emplacements de réception**. Dans le **emplacements de réception** volet, cliquez sur votre emplacement de réception, puis cliquez sur **activer**.  
  
##### <a name="to-create-a-static-one-way-send-port-for-contoso-to-send-the-edi-interchange"></a>Pour créer un port d'envoi unidirectionnel statique (pour Contoso) permettant d'envoyer l'échange EDI  
  
1.  Dans l'Explorateur Windows, créez un dossier local dans lequel envoyer l'échange test.  
  
2.  Dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, avec le bouton droit le **Ports d’envoi** nœud sous la **BizTalk Application 1** nœud **nouveau**, puis cliquez sur **Port d’envoi unidirectionnel statique**.  
  
3.  Dans le **propriétés de Port d’envoi** boîte de dialogue, le nom du port d’envoi.  
  
4.  Dans le **Transport** section, sélectionnez **fichier** pour **Type**, puis cliquez sur **configurer**.  
  
5.  Pour **dossier de Destination**, accédez au dossier de réception de l’échange. Vous avez créé ce dossier au cours de l'étape 1 de cette procédure. Pour **masque de fichier**, entrez le format d’échange, tel que  **\*EDI ou** ou  **\*.txt**.  
  
6.  Cliquez sur **OK**.  
  
7.  Dans **pipeline d’envoi**, sélectionnez **EdiSend**.  
  
8.  Dans l’arborescence de la console, sélectionnez **filtres**. Spécifiez un filtre pour vous abonner à l'échange EDI. Par exemple, pour **propriété**, entrez **BTS. MessageType**; pour **opérateur**, entrez  **==** ; et pour **valeur** Entrez le schéma de l’échange, `http://schemas.microsoft.com/BizTalk/EDI/EDIFACT/2006#EFACT_D98A_APERAK`.  
  
    > [!NOTE]
    >  Le paramètre spécifié ci-dessus garantit que les échanges, et non les accusés de réception, seront envoyés vers le dossier associé au port d'envoi.  
  
9. Cliquez sur **OK**.  
  
10. Dans l’arborescence de la console, cliquez sur **Ports d’envoi**. Dans le **Ports d’envoi** volet, cliquez sur le port d’envoi, puis cliquez sur **Démarrer**.  
  
##### <a name="to-create-a-static-one-way-send-port-to-send-the-acknowledgments"></a>Pour créer un port d'envoi unidirectionnel statique permettant d'envoyer les accusés de réception  
  
1.  Dans l'Explorateur Windows, créez un dossier local auquel envoyer les notifications de transactions techniques et opérationnelles.  
  
2.  Dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, avec le bouton droit le **Ports d’envoi** nœud sous la **BizTalk Application 1** nœud **nouveau**, puis cliquez sur **Port d’envoi unidirectionnel statique**.  
  
3.  Dans le **propriétés de Port d’envoi** boîte de dialogue, le nom du port d’envoi.  
  
4.  Dans le **Transport** section, sélectionnez **fichier** pour **Type**, puis cliquez sur **configurer**.  
  
5.  Pour **dossier de Destination**, accédez à un dossier pour les deux accusés de réception. Vous avez créé ce dossier au cours de l'étape 1 de cette procédure. Pour **masque de fichier**, entrez le format d’échange, tel que  **\*EDI ou** ou  **\*.txt**.  
  
6.  Cliquez sur **OK**.  
  
7.  Dans **pipeline d’envoi**, sélectionnez **EdiSend**.  
  
8.  Dans l’arborescence de la console, sélectionnez **filtres**. Spécifiez un filtre pour vous abonner aux accusés de réception. Par exemple, pour **propriété**, entrez **BTS. MessageType**; pour **opérateur**, entrez  **==** ; et pour **valeur** Entrez le schéma de l’accusé de réception, `http://schemas.microsoft.com/Edi/Edifact#Efact_Contrl_Root`.  
  
9. Cliquez sur **OK**.  
  
10. Dans l’arborescence de la console, cliquez sur **Ports d’envoi**. Dans le **Ports d’envoi** volet, cliquez sur le port d’envoi, puis cliquez sur **Démarrer**.  
  
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
  
##### <a name="to-create-an-agreement-between-the-two-business-profiles"></a>Pour créer un accord entre les deux profils d'entreprise  
  
1.  Avec le bouton droit **Fabrikam_Profile**, pointez sur **nouveau**, puis cliquez sur **accord**.  
  
2.  Dans le **propriétés générales** page, pour le **nom** texte, entrez un nom pour l’accord.  
  
3.  À partir de la **protocole** la liste déroulante, sélectionnez **EDIFACT**.  
  
4.  Dans le **deuxième partenaire** section, à partir de la **nom** la liste déroulante, sélectionnez **Contoso**.  
  
5.  Dans le **deuxième partenaire** section, à partir de la **profil** la liste déroulante, sélectionnez **Contoso_Profile**.  
  
     Vous remarquerez que les deux nouveaux onglets sont ajoutés à côté du **général** onglet. Chaque onglet sert à configurer un accord unidirectionnel, et chaque accord unidirectionnel constitue la transaction complète d'un message (en prenant également en compte les transferts du message et de l'accusé de réception).  
  
6.  Dans le **général** sous l’onglet dans le **propriétés générales** page, dans le **paramètres d’hôte communs** section, sélectionnez **activer le rapport d’état**, puis Sélectionnez **stocker la charge de message de création de rapports**.  
  
7.  Effectuer les tâches suivantes sur le **Fabrikam -> Contoso** onglet.  
  
    1.  Sur le **identificateurs** page sous le **paramètres de l’échange** section, entrez des valeurs pour les champs de qualificateur et identificateur (**UNB2.1**, **UNB2.2**, **UNB3.1**, et **UNB3.2**) qui correspondent aux valeurs de ces champs d’en-tête dans le message de test.  
  
        > [!NOTE]
        >  Les champs de qualificateur et d'identificateur pour l'expéditeur et le récepteur permettent à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] de résoudre l'accord. Il compare les valeurs de **UNB2.1**, **UNB2.2**, **UNB3.1**, et **UNB3.2** dans l’en-tête d’échange à celles dans les propriétés d’un accord. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]sera également l’accord en comparant le qualificateur de l’expéditeur et l’identificateur (sans le qualificateur du récepteur et l’identificateur). Si [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ne peut pas résoudre l'accord, il utilise les propriétés d'accord de secours.  
  
        > [!NOTE]
        >  Si vous utilisez l’exemple de message fourni précédemment dans cette rubrique comme message test, définissez **UNB2.1** à **7654321**, **UNB2.2** à **ZZZ – défini mutuellement** , **UNB3.1** à **1234567**, et **UNB3.2** à **ZZZ – défini mutuellement**.  
  
    2.  Sur le **accusés de réception** page sous le **paramètres de l’échange** section, vérifiez **réception du message (CONTRL) attendu** et **(de l’accusé de réception CONTRL) attendu**.  
  
    3.  Sur le **enveloppes** page sous le **paramètres de l’échange** section, vérifiez **appliquer le segment UNA (options de l’échange)** et **UNG d’appliquer les segments () En-tête de groupe fonctionnel)**.  
  
    4.  Sur le **Validation** page sous le **paramètres de l’échange** section, assurez-vous que **numéro de contrôle de l’échange (UNB5)** option est désactivée.  
  
        > [!NOTE]
        >  Effacer la **numéro de contrôle de l’échange (UNB5)** propriété vous permet de recevoir plusieurs instances du même message.  
  
    5.  Sur le **jeu de caractères et séparateurs** page sous le **paramètres de l’échange** section, sélectionnez le **CR LF** est définie sur **suffixe UNA6**.  
  
    6.  Sur le **paramètres d’hôte Local** page sous le **paramètres de l’échange** section, désactivez le **port de réception de l’accusé de réception itinéraire un pipeline d’envoi de requête-réponse** option.  
  
        > [!NOTE]
        >  Si vous utilisiez un double port de réception pour recevoir l’échange et de renvoyer l’accusé de réception, vous devez vérifier **port de réception de l’accusé de réception itinéraire un pipeline d’envoi de requête-réponse**.  
  
    7.  Sur le **Ports d’envoi** page sous le **paramètres d’échange** section, associez les ports d’envoi qui recevra l’échange de Fabrikam et les ports d’envoi qui recevront le accusés de réception de Contoso. Dans le **ports d’envoi** grille, sous la **nom** colonne, cliquez sur une cellule vide et dans la liste déroulante, sélectionnez le port d’envoi créé pour la réception de l’échange EDI de Fabrikam. Répétez l'étape pour le port d'envoi créé à des fins de réception des notifications de transactions techniques et opérationnelles.  
  
    8.  Sur le **Validation** page sous le **paramètres des documents informatisés** conservez **Validation de type EDI** activée et activez **Validation de Type étendu**.  
  
    9. Si vous utilisez l’un des schémas standards fournis avec [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], dans le **paramètres d’hôte Local** page sous le **paramètres des documents informatisés** , sélectionnez l’espace de noms du schéma à être utilisé pour traiter l’échange entrant. Si vous utilisez un schéma personnalisé, entrez des valeurs dans le **espace de noms cible de personnaliser** grille, afin que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] peut déterminer l’espace de noms à l’aide de transactions et groupe de définie des valeurs d’en-tête.  
  
    10. Sur le **enveloppes** page sous le **paramètres des documents informatisés** section, entrez des valeurs pour toutes les colonnes dans la première ligne de la grille.  
  
        |Utiliser|Pour effectuer cette opération|  
        |--------------|----------------|  
        |**Default**|Sélectionnez **par défaut**.|  
        |**Pour le type de message UNH2.1**|Sélectionnez le type de message de votre message test, **APERAK**.|  
        |**UNH2.2**|Entrez la version EDI, **D**.|  
        |**UNH2.3**|Entrez le numéro de version, **98 a**.|  
        |**UNH2.5**|Laissez cette option vierge.|  
        |**Espace de noms cible**|Sélectionnez **http://schemas.microsoft.com/Edi/Edifact**.|  
        |**UNG1**|Spécifiez l’ID de groupe fonctionnel, **INVOIC**.|  
        |**UNG2.1**|Entrez une valeur d'identification de l'expéditeur de l'application.|  
        |**UNG2.1**|Entrez une valeur pour le qualificateur de code application expéditeur, par exemple **ZZZ**.|  
        |**UNG3.1**|Entrez une valeur d'identification du récepteur de l'application.|  
        |**UNG3.2**|Entrez une valeur pour le qualificateur de code de récepteur application, tel que **ZZZ**.|  
        |**UNG6**|Entrez une valeur pour l’entité de contrôle. Exemple, **UN**.|  
        |**UNG7.1**|Entrez le numéro de version du type de message. Exemple, **D**.|  
        |**UNG7.2**|Entrez le numéro de version finale du type de message. Exemple, **98 a**.|  
        |**UNG7.3**|Laissez cette option vierge.|  
        |**UNG8**|Laissez cette option vierge.|  
  
8.  Effectuer les tâches suivantes sur le **Contoso -> Fabrikam** onglet.  
  
    > [!NOTE]
    >  Dans cette procédure pas à pas, la valeur requise est spécifiée sous l'onglet afin de permettre la création d'un accord. Pour créer un accord, les deux onglets d’accord unidirectionnel doivent avoir des valeurs définies pour **UNG2.1**, **UNG2.2**, **UNG3.1**, et **UNG3.2**.  
  
    > [!NOTE]
    >  Même si l’accusé de réception fait partie de la même transaction de message, les propriétés relatives à la façon de générer l’accusé de réception sont configurées dans le **Contoso -> Fabrikam** onglet. Cela est nécessaire car les propriétés de contexte d’accusé de réception pour l’expéditeur et récepteur les qualificateurs sont définis sur le contraire des valeurs que vous avez spécifié dans le **Contoso -> Fabrikam** onglet. Par exemple, si l’expéditeur et récepteur identificateurs sont définis sur 7654321 et 1234567 dans le **Fabrikam -> Contoso** onglet, l’expéditeur et le destinataire des propriétés de contexte sont définies sur 1234567 et 7654321 dans l’accusé de réception. De manière générale, l'autre onglet d'accord unidirectionnel dispose également des identificateurs de l'expéditeur et du récepteur définis sur 1234567 et 7654321, respectivement. Ainsi, le message d'accusé de réception correspond à cet accord et la configuration des propriétés est choisie. Par conséquent, si vous souhaitez disposer de l’accusé de réception à utiliser d’autres séparateurs d’éléments ou si vous souhaitez disposer de l’accusé de réception à utiliser CR LF, spécifiez les propriétés de la **Contoso -> Fabrikam** onglet.  
    >   
    >  Sur le plan conceptuel, les propriétés de l'accusé de réception sont récupérées à partir de l'un des onglets de l'accord unidirectionnel possédant les mêmes qualificateurs d'expéditeur et de récepteur que ceux définis dans les propriétés de contexte de l'accusé de réception. Toutefois, pour des raisons de commodité, vous définissez ces propriétés sous l'autre onglet de l'accord unidirectionnel créé, auquel correspond l'échange.  
  
    1.  Sur le **identificateurs** page sous le **paramètres de l’échange** section, entrez des valeurs pour les champs de qualificateur et identificateur (**UNG2.1**, **UNG2.2**, **UNG3.1**, et **UNG3.2**) qui correspondent aux valeurs de ces champs d’en-tête dans le message de test.  
  
        > [!NOTE]
        >  Si vous utilisez l’exemple de message fourni précédemment dans cette rubrique comme message test, définissez **UNB2.1** à **1234567**, **UNB2.2** à **ZZZ – défini mutuellement** , **UNB3.1** à **7654321**, et **UNB3.2** à **ZZZ – défini mutuellement**.  
  
9. Cliquez sur **Appliquer**.  
  
10. Cliquez sur **OK**. Le nouvel accord ajouté est répertorié dans le **accords** section de la **tiers et profils d’entreprise** volet. Le nouvel accord ajouté est activé par défaut.  
  
### <a name="testing-the-walkthrough"></a>Test de la procédure pas à pas  
 Cette section fournit des informations sur le test de la procédure pas à pas.  
  
##### <a name="to-test-the-walkthrough"></a>Pour tester la procédure pas à pas  
  
1.  Dans l'Explorateur Windows, placez l'échange EDI de test dans le dossier de réception local.  
  
    > [!NOTE]
    >  Pour un message de test, vous pouvez utiliser l'exemple de message fourni précédemment dans cette rubrique. Copiez le message dans un fichier texte et enregistrez-le sous une extension .txt. Lorsque vous utilisez ce message, vous devez avoir préalablement déployé le schéma EFACT_D98A_APERAK.xsd. Le schéma est disponible en exécutant la **MicrosoftEdiXSDTemplates.exe** fichier (dans le dossier \XSD_Schema\EDI) pour décompresser les schémas dans le dossier par défaut. Le schéma EFACT_D98A_APERAK.xsd est ensuite accessible à partir de [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema\EDI\EDIFACT\D98A.  
  
2.  Ouvrez le dossier que vous avez associé au port d'envoi des échanges, puis vérifiez qu'il contient bien l'échange EDI.  
  
3.  Ouvrez le dossier que vous avez associé au port d'envoi des accusés de réception, puis vérifiez qu'il contient bien les notifications de transactions techniques et opérationnelles.  
  
## <a name="see-also"></a>Voir aussi  
 [Développement et la configuration des Solutions EDI BizTalk Server](../core/developing-and-configuring-biztalk-server-edi-solutions.md)