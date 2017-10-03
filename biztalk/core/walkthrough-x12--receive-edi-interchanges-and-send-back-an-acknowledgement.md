---
title: "Procédure pas à pas (X12) : Réception d’échanges EDI et envoi d’un accusé de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 25d2b5f3-6bd1-413c-aace-e4dd71f80403
caps.latest.revision: "45"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 79eb16ac77f2f1573735c36b19fa6aa68c001c76
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="walkthrough-x12-receiving-edi-interchanges-and-sending-back-an-acknowledgement"></a>Procédure pas à pas (X12) : réception des échanges EDI et envoi d'un accusé de réception
Cette procédure pas à pas fournit des instructions détaillées sur la création d'une solution de réception d'échanges EDI à l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Dans cette solution, un échange EDI est envoyé par un partenaire commercial, Fabrikam, à un autre partenaire commercial, Contoso.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
## <a name="how-the-solution-receives-edi-interchanges"></a>Réception des échanges EDI par la solution  
 La solution effectue les opérations suivantes :  
  
> [!NOTE]
>  Les événements dans cette liste peuvent se produire dans un ordre différent de celui indiqué.  
  
1.  réception d'un échange de fichier plat EDI de la part du partenaire commercial Fabrikam ;  
  
2.  validation de l'échange EDI selon son schéma, désassemblage du message en XML, puis déplacement du message XML dans la base de données MessageBox ;  
  
3.  génération d'un accusé de réception 997 vers l'échange EDI reçu, puis déplacement dans la base de données MessageBox ;  
  
4.  génération d'un accusé de réception TA1 vers l'échange EDI reçu, puis déplacement dans la base de données MessageBox ;  
  
5.  récupération du message XML par un port d'envoi unidirectionnel, puis assemblage de l'échange du message EDI ;  
  
6.  envoi de l'échange EDI à Contoso ;  
  
7.  récupération du message 997 XML par un port d'envoi unidirectionnel, puis assemblage de l'échange du message 997 EDI ;  
  
8.  envoi de l'échange 997 à Fabrikam.  
  
9. récupération du message TA1 XML par un port d'envoi unidirectionnel, puis assemblage de l'échange TA1 EDI ;  
  
10. envoi de l'échange TA1 à Fabrikam.  
  
## <a name="the-functionality-in-this-solution"></a>Fonctionnalités dans la solution  
 Pour les besoins de cette procédure, la fonctionnalité suivante est activée :  
  
-   La solution est conçue pour les échanges basés sur le codage X12, et non le codage EDIFACT.  
  
    > [!NOTE]
    >  La configuration utilisée pour le codage HIPAA est proche de celle utilisée pour le codage X12. Pour obtenir des instructions sur la création d’une solution similaire pour EDIFACT, consultez [procédure pas à pas (EDIFACT) : réception des échanges EDI et envoi d’un accusé](../core/walkthrough-edifact--receive-edi-interchanges-and-send-an-acknowledgement.md).  
  
-   La validation de type EDI et la validation étendue sont effectuées sur l'échange entrant.  
  
-   Les notifications de transactions techniques et opérationnelles sont générées de manière à être renvoyées à l'expéditeur de l'échange.  
  
-   La solution utilise un emplacement de réception unidirectionnel avec un type de transport FILE.  
  
    > [!NOTE]
    >  Vous pouvez utiliser un emplacement et un port de réception avec sollicitation-réponse bidirectionnels pour recevoir le message. Toutefois, si vous utilisez cette méthode, vous ne pourrez pas faire appel à un emplacement de réception disposant du type de transport FILE. Pour plus d’informations, consultez [configuration d’un Port de réception des Messages EDI et les accusés de réception](../core/configuring-a-port-to-receive-edi-messages-and-acknowledgments.md).  
  
-   La création de rapports EDI est activée. Les documents informatisés sont enregistrés pour être consultables depuis le rapport État de l'échange.  
  
-   À des fins de test, la solution utilise trois ports d'envoi pour envoyer aux dossiers locaux l'échange EDI ainsi que les accusés de réception créés.  
  
 L'architecture de cette solution est représentée dans la figure suivante :  
  
 ![Réception des échanges EDI](../core/media/c54cca56-c658-4081-9e2f-bf28ba647cda.gif "c54cca56-c658-4081-9e2f-bf28ba647cda")  
  
## <a name="configuring-and-testing-the-walkthrough"></a>Configuration et test de la procédure pas à pas  
 Les étapes suivantes sont requises pour configurer cette solution :  
  
-   Ajouter le ou les schémas de message requis à un projet BizTalk, puis créer et déployer le projet afin que le ou les schémas soient mis à disposition de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] lors du traitement de l'échange reçu.  
  
-   Créer un port de réception unidirectionnel de manière à ce que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] reçoive l'échange EDI en provenance du partenaire commercial, puis génère un accusé de réception. Cet emplacement de réception est lié au dossier de fichiers dans lequel Fabrikam place l'échange EDI à envoyer à Contoso.  
  
    > [!NOTE]
    >  Vous pouvez utiliser sollicitation un double port de réception de réponse et l’emplacement pour recevoir le message, mais si vous le faites, vous ne serez pas en mesure d’utiliser un type de transport de fichier pour l’emplacement de réception.  
  
-   Créer un port d'envoi permettant d'envoyer l'échange EDI à un dossier Contoso local, ainsi que deux ports d'envois permettant d'envoyer respectivement les accusés de réception 997 et TA1 à un dossier Fabrikam local.  
  
-   Créer un tiers (partenaire commercial) pour Fabrikam et Contoso.  
  
-   Créer un profil d'entreprise pour les deux partenaires commerciaux.  
  
-   Créer un accord entre les deux profils via la configuration des propriétés EDI du message à recevoir et de l'accusé de réception à envoyer.  
  
-   Tester la procédure pas à pas en utilisant un échange EDI test.  
  
    > [!NOTE]
    >  Pour un message test, vous pouvez utiliser le fichier SamplePO.txt utilisé dans le didacticiel pour développeur d'interface EDI. Ce fichier figure dans le dossier [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial\. Il s'agit d'un message X12 850.  
  
### <a name="configuring-the-walkthrough"></a>Configuration de la procédure pas à pas  
 Cette section décrit les étapes de configuration de la procédure pas à pas.  
  
##### <a name="to-deploy-the-message-schema"></a>Pour déployer le schéma de message  
  
1.  Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], créez ou ouvrez un projet BizTalk.  
  
    > [!NOTE]
    >  Cette rubrique part du principe que vous avez déjà ajouté une référence de votre application à l'application BizTalk EDI, qui contient les schémas, pipelines et orchestrations EDI. Dans le cas contraire, consultez [comment ajouter une référence à l’Application EDI de BizTalk Server](http://msdn.microsoft.com/library/7af066fb-372f-4709-b566-c8d6b4a9d782).  
  
2.  Avec le bouton droit de votre projet, pointez sur **ajouter**, puis cliquez sur **élément existant**. Accédez au dossier dans lequel se trouve votre schéma [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema\EDI, puis double-cliquez sur celui-ci.  
  
    > [!NOTE]
    >  Si les schémas EDI n’ont pas été décompressés dans les dossiers \XSD_Schema\EDI, exécutez le **MicrosoftEdiXSDTemplates.exe** fichier dans le dossier \XSD_Schema\EDI pour décompresser les schémas dans le dossier par défaut.  
  
    > [!NOTE]
    >  Si vous utilisez le fichier SamplePO.txt utilisé dans le didacticiel pour développeur d'interface EDI, vous devez utiliser le schéma X12_00401_850.xsd figurant dans le dossier [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial\Inbound_EDI. N'utilisez pas le schéma X12 850 figurant dans le dossier [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema.  
  
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
  
5.  Pour **dossier de Destination**, accédez au dossier de réception de l’échange. Vous avez créé ce dossier au cours de l'étape 1 de cette procédure. Pour **masque de fichier**, entrez le format d’échange, tel que  **\*EDI ou** ou  **\*.xml**.  
  
6.  Cliquez sur **OK**.  
  
7.  Dans **pipeline d’envoi**, sélectionnez **EdiSend**.  
  
8.  Dans l’arborescence de la console, sélectionnez **filtres**. Spécifiez un filtre pour vous abonner à l'échange EDI. Par exemple, pour **propriété**, entrez **BTS. MessageType**; pour **opérateur**, entrez  **==** ; et pour **valeur** Entrez le schéma de l’échange, par exemple, http:// schemas.microsoft.com/BizTalk/Edi/X12/2006#X12_00401_850.  
  
    > [!NOTE]
    >  Le paramètre spécifié ci-dessus garantit que les échanges, et non les accusés de réception, seront envoyés vers le dossier associé au port d'envoi.  
  
9. Cliquez sur **OK**.  
  
10. Dans l’arborescence de la console, cliquez sur **Ports d’envoi**. Dans le **Ports d’envoi** volet, cliquez sur le port d’envoi, puis cliquez sur **Démarrer**.  
  
##### <a name="to-create-a-static-one-way-send-port-to-send-the-997n-acknowledgment"></a>Pour créer un port d'envoi unidirectionnel statique permettant d'envoyer les accusés de réception 997  
  
1.  Dans l'Explorateur Windows, créez un dossier local auquel envoyer les accusés de réception 997.  
  
2.  Dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, avec le bouton droit le **Ports d’envoi** nœud sous la **BizTalk Application 1** nœud **nouveau**, puis cliquez sur **Port d’envoi unidirectionnel statique**.  
  
3.  Dans le **propriétés de Port d’envoi** boîte de dialogue, le nom du port d’envoi.  
  
4.  Dans le **Transport** section, sélectionnez **fichier** pour **Type**, puis cliquez sur **configurer**.  
  
5.  Pour **dossier de Destination**, accédez au dossier de réception de l’accusé de réception 997. Vous avez créé ce dossier au cours de l'étape 1 de cette procédure. Pour **masque de fichier**, entrez le format d’échange, tel que  **\*EDI ou** ou  **\*.txt**.  
  
6.  Cliquez sur **OK**.  
  
7.  Dans **pipeline d’envoi**, sélectionnez **EdiSend**.  
  
8.  Dans l’arborescence de la console, sélectionnez **filtres**. Spécifiez un filtre pour vous abonner aux accusés de réception 997. Par exemple, pour **propriété**, entrez **BTS. MessageType**; pour **opérateur**, entrez  **==** ; et pour **valeur** Entrez le schéma pour l’accusé de réception, par exemple, `http://schemas.microsoft.com/Edi/X12#X12_997_Root`.  
  
9. Cliquez sur **OK**.  
  
10. Dans l’arborescence de la console, cliquez sur **Ports d’envoi**. Dans le **Ports d’envoi** volet, cliquez sur le port d’envoi, puis cliquez sur **Démarrer**.  
  
##### <a name="to-create-a-static-one-way-send-port-to-send-the-ta1-acknowledgment"></a>Pour créer un port d'envoi unidirectionnel statique permettant d'envoyer les accusés de réception TA1  
  
1.  Dans l'Explorateur Windows, créez un dossier local auquel envoyer les accusés de réception TA1.  
  
2.  Dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, avec le bouton droit le **Ports d’envoi** nœud sous la **BizTalk Application 1** nœud **nouveau**, puis cliquez sur **Port d’envoi unidirectionnel statique**.  
  
3.  Dans le **propriétés de Port d’envoi** boîte de dialogue, le nom du port d’envoi.  
  
4.  Dans le **Transport** section, sélectionnez **fichier** pour **Type**, puis cliquez sur **configurer**.  
  
5.  Pour **dossier de Destination**, accédez au dossier de réception de l’accusé de réception TA1. Vous avez créé ce dossier au cours de l'étape 1 de cette procédure. Pour **masque de fichier**, entrez le format d’échange, tel que  **\*EDI ou** ou  **\*.txt**.  
  
6.  Cliquez sur **OK**.  
  
7.  Dans **pipeline d’envoi**, sélectionnez **EdiSend**.  
  
8.  Dans l’arborescence de la console, sélectionnez **filtres**. Spécifiez un filtre pour vous abonner aux accusés de réception TA1. Par exemple, pour **propriété**, entrez **BTS. MessageType**; pour **opérateur**, entrez  **==** ; et pour **valeur** Entrez le schéma de l’accusé de réception, par exemple, http:// schemas.microsoft.com/Edi/X12#X12_TA1_Root.  
  
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
  
3.  À partir de la **protocole** la liste déroulante, sélectionnez **X12**.  
  
4.  Dans le **deuxième partenaire** section, à partir de la **nom** la liste déroulante, sélectionnez **Contoso**.  
  
5.  Dans le **deuxième partenaire** section, à partir de la **profil** la liste déroulante, sélectionnez **Contoso_Profile**.  
  
     Vous remarquerez que les deux nouveaux onglets sont ajoutés à côté du **général** onglet. Chaque onglet sert à configurer un accord unidirectionnel, et chaque accord unidirectionnel constitue la transaction complète d'un message (en prenant également en compte les transferts du message et de l'accusé de réception).  
  
6.  Dans le **général** sous l’onglet dans le **propriétés générales** page, dans le **paramètres d’hôte communs** section, sélectionnez **activer le rapport d’état**, puis Sélectionnez **stocker la charge de message de création de rapports**.  
  
7.  Effectuer les tâches suivantes sur le **Fabrikam -> Contoso** onglet.  
  
    1.  Sur le **identificateurs** page sous le **paramètres de l’échange** section, entrez des valeurs pour les champs de qualificateur et identificateur (**ISA5**, **ISA6**, **ISA7**, et **ISA8**) qui correspondent aux valeurs de ces champs d’en-tête dans le message de test.  
  
        > [!NOTE]
        >  Les champs de qualificateur et d'identificateur pour l'expéditeur et le récepteur permettent à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] de résoudre l'accord. Il compare les valeurs de **ISA5**, **ISA6**, **ISA7**, et **ISA8** dans l’en-tête d’échange à celles dans les propriétés d’un accord. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]sera également l’accord en comparant le qualificateur de l’expéditeur et l’identificateur (sans le qualificateur du récepteur et l’identificateur). Si [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ne peut pas résoudre l'accord, il utilise les propriétés d'accord de secours.  
  
        > [!NOTE]
        >  Si vous utilisez le fichier SamplePO.txt à partir de « EDI Interface Developer Tutorial » comme message test, définissez **ISA5** à **ZZ**, **ISA6** à **THEM**, **ISA7** à **ZZ**, et **ISA8** à **US**.  
  
    2.  Sur le **accusé de réception** page sous le **paramètres de l’échange** section, cocher **TA1 attendu** et **997 attendu**.  
  
    3.  Sur le **Validation** page sous le **paramètres de l’échange** section, assurez-vous que **chercher isa13 en double** option est désactivée.  
  
        > [!NOTE]
        >  Effacer la **chercher isa13 en double** propriété vous permet de recevoir plusieurs instances du même message.  
  
    4.  Sur le **jeu de caractères et séparateurs** page sous le **paramètres de l’échange** section, sélectionnez le **CR LF** option.  
  
    5.  Sur le **paramètres d’hôte Local** page sous le **paramètres de l’échange** section, désactivez le **port de réception de l’accusé de réception itinéraire un pipeline d’envoi de requête-réponse** option.  
  
        > [!NOTE]
        >  Si vous utilisiez un double port de réception pour recevoir l’échange et de renvoyer l’accusé de réception, vous devez vérifier **port de réception de l’accusé de réception itinéraire un pipeline d’envoi de requête-réponse**.  
  
    6.  Sur le **Ports d’envoi** page sous le **paramètres d’échange** section, associez les ports d’envoi qui recevra l’échange de Fabrikam et les ports d’envoi qui recevront le accusés de réception de Contoso. Dans le **ports d’envoi** grille, sous la **nom** colonne, cliquez sur une cellule vide et dans la liste déroulante, sélectionnez le port d’envoi créé pour la réception de l’échange EDI de Fabrikam. Répétez l'étape pour les ports d'envoi créés à des fins de réception des accusés de réception TA1 et 997.  
  
    7.  Sur le **Validation** page sous le **paramètres des documents informatisés** conservez **Validation de Type EDI** activée et activez **devalidationétendue**.  
  
    8.  Si vous utilisez l’un des schémas standards fournis avec [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], dans le **paramètres d’hôte Local** page sous le **paramètres des documents informatisés** , sélectionnez l’espace de noms du schéma à être utilisé pour traiter l’échange entrant. Si vous utilisez un schéma personnalisé, entrez des valeurs dans le **espace de noms cible de personnaliser** grille, afin que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] peut déterminer l’espace de noms à l’aide de transactions et groupe de définie des valeurs d’en-tête.  
  
    9. Sur le **enveloppes** page sous le **paramètres des documents informatisés** section, entrez des valeurs pour toutes les colonnes dans la première ligne de la grille.  
  
        |Utiliser|Pour effectuer cette opération|  
        |--------------|----------------|  
        |**Default**|Sélectionnez **par défaut**. **Remarque :** lorsque vous sélectionnez cette ligne en tant que la valeur par défaut, les valeurs de **GS1**, **GS2**, **GS3**, **GS7**et **GS8** sont utilisées même si les valeurs de **Type de Transaction**, **Version/publication**, et **espace de noms cible** ne sont pas une correspondance pour le Message.|  
        |**Type de transaction**|Sélectionnez le type de message de votre message test, **850 - bon de commande**.|  
        |**Version/publication**|Entrez la version EDI, **00401**.|  
        |**Espace de noms cible**|Sélectionnez **http://schemas.microsoft.com/Edi/X12**.|  
        |**GS1**|Vérifiez que le type de message du message de test est sélectionné, **PO - bon de commande (850)**.|  
        |**GS2**|Entrez une valeur pour l'expéditeur de l'application.|  
        |**GS3**|Entrez une valeur pour l'application réceptrice.|  
        |**GS4**|Sélectionnez le format de date souhaité. **Remarque :** vous devez sélectionner la valeur dans la liste déroulante, ne cliquez pas seulement dans le champ pour afficher la valeur par défaut. Si vous cliquez dans le champ sans sélectionner la valeur dans la liste déroulante, la valeur ne sera pas réellement sélectionnée.|  
        |**GS5**|Sélectionnez le format d'heure souhaité.|  
        |**GS7**|Sélectionnez **X - Accredited Standards Committee X12**.|  
        |**GS8**|Vérifiez que la version EDI a été entrée, **00401**.|  
  
        > [!NOTE]
        >  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]effet de définir les valeurs de GS01, GS02, GS03, GS04, GS05, GS07 et GS08 des accusés de réception sortants selon les valeurs entrées pour **Type de Transaction**, **Version/publication**, et **cible espace de noms**. Le pipeline d'envoi tente de faire correspondre le type de transaction, la version X12 et l'espace de noms cible avec les valeurs correspondantes dans l'en-tête du message. Si réussie, elle utilise les valeurs GS associées le **Type de Transaction**, **Version/publication**, et **espace de noms cible** valeurs.  
  
8.  Effectuer les tâches suivantes sur le **Contoso -> Fabrikam** onglet.  
  
    > [!NOTE]
    >  Dans cette procédure pas à pas, la valeur requise est spécifiée sous l'onglet afin de permettre la création d'un accord. Pour créer un accord, les deux onglets d’accord unidirectionnel doivent avoir des valeurs définies pour **ISA5**, **ISA6**, **ISA7**, et **ISA8**.  
  
    > [!NOTE]
    >  Même si l’accusé de réception fait partie de la même transaction de message, les propriétés relatives à la façon de générer l’accusé de réception sont configurées dans le **Contoso -> Fabrikam** onglet. Cela est nécessaire car les propriétés de contexte d’accusé de réception pour l’expéditeur et récepteur les qualificateurs sont définis sur le contraire des valeurs que vous avez spécifié dans le **Contoso -> Fabrikam** onglet. Par exemple, si l’expéditeur et récepteur identificateurs sont définis sur THEM et US dans le **Fabrikam -> Contoso** onglet, l’expéditeur et le destinataire des propriétés de contexte sont définies sur US et THEM dans l’accusé de réception. De manière générale, l'autre onglet de l'accord unidirectionnel dispose également des identificateurs de l'expéditeur et du récepteur définis sur US et THEM, respectivement. Ainsi, le message d'accusé de réception correspond à cet accord et la configuration des propriétés est choisie. Par conséquent, si vous souhaitez disposer de l’accusé de réception à utiliser d’autres séparateurs d’éléments ou si vous souhaitez disposer de l’accusé de réception à utiliser CR LF, spécifiez les propriétés de la **Contoso -> Fabrikam** onglet.  
    >   
    >  Sur le plan conceptuel, les propriétés de l'accusé de réception sont récupérées à partir de l'un des onglets de l'accord unidirectionnel possédant les mêmes qualificateurs d'expéditeur et de récepteur que ceux définis dans les propriétés de contexte de l'accusé de réception. Toutefois, pour des raisons de commodité, vous définissez ces propriétés sous l'autre onglet de l'accord unidirectionnel créé, auquel correspond l'échange.  
  
    1.  Sur le **identificateurs** page sous le **paramètres de l’échange** section, entrez des valeurs pour les champs de qualificateur et identificateur (**ISA5**, **ISA6**, **ISA7**, et **ISA8**) qui correspondent aux valeurs de ces champs d’en-tête dans le message de test.  
  
        > [!NOTE]
        >  Si vous utilisez le fichier SamplePO.txt à partir de « EDI Interface Developer Tutorial » comme message test, définissez **ISA5** à **ZZ**, **ISA6** à **américain**, **ISA7** à **ZZ**, et **ISA8** à **THEM**.  
  
9. Cliquez sur **Appliquer**.  
  
10. Cliquez sur **OK**. Le nouvel accord ajouté est répertorié dans le **accords** section de la **tiers et profils d’entreprise** volet. Le nouvel accord ajouté est activé par défaut.  
  
### <a name="testing-the-walkthrough"></a>Test de la procédure pas à pas  
 Cette section fournit des informations sur le test de la procédure pas à pas.  
  
##### <a name="to-test-the-walkthrough"></a>Pour tester la procédure pas à pas  
  
1.  Dans l'Explorateur Windows, placez l'échange EDI de test dans le dossier de réception local.  
  
    > [!NOTE]
    >  Pour un message test, vous pouvez utiliser le fichier SamplePO.txt utilisé dans le didacticiel pour développeur d'interface EDI. Ce fichier est fourni dans le [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]dossier de SDK\EDI Interface Developer Tutorial. Il s'agit d'un message X12 850. Si vous utilisez ce message, vous devez avoir déployé le schéma X12_00401_850.xsd figurant dans le dossier [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial\Inbound_EDI. N'utilisez pas le schéma X12 850 figurant dans le dossier [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema.  
  
2.  Ouvrez le dossier que vous avez associé au port d'envoi des échanges, puis vérifiez qu'il contient bien l'échange EDI.  
  
3.  Ouvrez le dossier que vous avez associé au port d'envoi de l'accusé de réception 997, puis vérifiez qu'il contient bien un accusé de réception 997.  
  
4.  Ouvrez le dossier que vous avez associé au port d'envoi de l'accusé de réception TA1, puis vérifiez qu'il contient bien un accusé de réception TA1.  
  
## <a name="see-also"></a>Voir aussi  
 [Développement et la configuration des Solutions EDI BizTalk Server](../core/developing-and-configuring-biztalk-server-edi-solutions.md)