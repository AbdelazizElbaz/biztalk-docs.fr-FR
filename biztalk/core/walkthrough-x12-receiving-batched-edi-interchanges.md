---
title: "Procédure pas à pas (X12) : Réception par lot des échanges EDI | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1f6e6e96-39ec-469d-a845-1bfdce6cc0bf
caps.latest.revision: "34"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 95c4bb48805eb0d2b349a8802c0bc8af1d12925a
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="walkthrough-x12-receiving-batched-edi-interchanges"></a>Procédure pas à pas (X12) : réception d'échanges EDI reçus traités par lot
Cette procédure pas à pas fournit des instructions détaillées sur la création d'une solution de réception de lots EDI à l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Cette solution montre deux manières de recevoir un échange EDI par lot :  
  
-   En fractionnant le lot en documents informatisés qui le composent.  
  
-   En conservant l'échange, en le traitant comme un document unique sans fractionner les documents informatisés.  
  
 Cette procédure pas à pas montre comment configurer le fractionnement et la conservation des lots.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
## <a name="how-the-solution-splits-received-edi-batches"></a>Fractionnement par la solution des lots EDI reçus  
 Lorsque vous configurez la solution pour fractionner l'échange par lot en documents informatisés qui le composent, la solution effectue les opérations suivantes :  
  
1.  L'emplacement de réception reçoit d'un tiers un échange EDI par lot contenant plusieurs documents informatisés.  
  
    > [!NOTE]
    >  Les événements dans cette liste peuvent se produire dans un ordre différent de celui indiqué.  
  
2.  Le pipeline de réception fractionne l'échange reçu en documents informatisés qui le composent, en convertissant les documents informatisés au format XML interne.  
  
3.  Le pipeline de réception promeut l'ensemble des en-têtes d'échange et de groupe dans le contexte de chaque document informatisé fractionné de l'échange. Il promeut également certains en-têtes d'échange et de groupe spécifiques, tels que ISA6, GS1 et GS2, afin que ces champs puissent être utilisés pour le routage.  
  
4.  Le pipeline de réception dépose chaque fichier XML de document informatisé dans la MessageBox.  
  
    > [!NOTE]
    >  Dans cette solution, le lot contient plusieurs instances du même type de message.  
  
5.  Le port d'envoi récupère chaque document informatisé par un abonnement sur une propriété de contexte appropriée.  
  
6.  Le pipeline d'envoi crée chaque document informatisé dans un échange EDI, puis envoie l'échange à la destination.  
  
    > [!NOTE]
    >  Pour plus d’informations sur la façon de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] fractionnements les ensembles de transactions dans un lot, consultez [fractionner un échange EDI par lot](../core/splitting-a-batched-edi-interchange.md).  
  
 La figure suivante montre l'architecture et le flux de messages de la solution lorsqu'elle est configurée pour fractionner les documents informatisés dans l'échange par lot.  
  
 ![Les échanges EDI traités par lot de fractionnement](../core/media/ef386df6-e195-45d9-abff-4d0bd3a82a4f.gif "ef386df6-e195-45d9-abff-4d0bd3a82a4f")  
  
## <a name="how-the-solution-preserves-received-edi-batches"></a>Conservation par la solution des lots EDI reçus  
 Lorsque vous configurez la solution pour conserver l'échange par lot, la solution effectue les opérations suivantes :  
  
1.  L'emplacement de réception reçoit du tiers un échange EDI par lot contenant plusieurs documents informatisés.  
  
2.  Le pipeline de réception traite l'échange sans fractionner les documents informatisés, en convertissant les deux documents informatisés en tant qu'unité au format XML interne.  
  
3.  Le pipeline de réception promeut les mêmes propriétés que si l'échange n'était pas un lot, à ceci près qu'une balise réservée est appliquée au XML qu'il génère. Cette balise est \<X12InterchangeXml\> pour un échange EDI codée au format X12 ou \<EdifactInterchangeXml\> pour un échange EDI de type EDIFACT. Le pipeline de réception EDI applique également la propriété de contexte `ReuseEnvelope` pour identifier l'échange comme conservé.  
  
    > [!NOTE]
    >  Le pipeline d’envoi EDI utilise la \<X12InterchangeXml\> ou \<EdifactInterchangeXml\> étiquette pour identifier le message comme lot conservé. La propriété de contexte `ReuseEnvelope` vous permet de créer un port d'envoi qui s'abonne à tous les échanges par lot conservés.  
  
4.  Le pipeline de réception dépose le fichier XML du message dans la MessageBox.  
  
5.  Le port d'envoi récupère l'échange par un abonnement sur une propriété de contexte appropriée.  
  
6.  Le pipeline d'envoi crée les deux documents informatisés du fichier XML dans un échange EDI par lot, puis envoie l'échange à la destination.  
  
    > [!NOTE]
    >  Pour plus d’informations sur la façon de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] traite un lot conservé, consultez [en conservant un reçu échange EDI par lot](../core/preserving-a-received-batched-edi-interchange.md).  
  
## <a name="functionality-in-this-solution"></a>Fonctionnalités dans cette solution  
 Pour les besoins de cette procédure, la fonctionnalité suivante est activée :  
  
-   La solution est conçue pour les échanges basés sur le codage X12, et non le codage EDIFACT.  
  
    > [!NOTE]
    >  La configuration utilisée pour HIPAA et pour le codage EDIFACT est proche de celle utilisée pour le codage X12.  
  
-   Des accusés de réception techniques ou fonctionnels ne sont pas renvoyés en réponse à l'échange initialement reçu ou à tout échange par lot envoyé.  
  
    > [!NOTE]
    >  Pour plus d’informations sur la génération d’accusés de réception EDI, consultez [procédure pas à pas (X12) : réception des échanges EDI et envoi d’un accusé](../core/walkthrough-x12--receive-edi-interchanges-and-send-back-an-acknowledgement.md).  
  
-   Cette solution utilise un unidirectionnel port de réception et le port d’envoi statique unidirectionnel. Ces ports sont configurés avec le type de transport FILE.  
  
-   La création de rapports EDI est activée.  
  
-   Les documents informatisés sont enregistrés pour être consultables depuis le rapport État de l'échange.  
  
-   À des fins de test, la solution utilise un port d'envoi pour envoyer à un dossier local les échanges fractionnés ou le lot conservé.  
  
## <a name="configuring-and-testing-the-walkthrough"></a>Configuration et test de la procédure pas à pas  
 Les étapes suivantes sont requises pour configurer cette solution :  
  
-   Ajouter le ou les schémas de message requis à un projet BizTalk, puis créer et déployer le projet afin que le ou les schémas soient mis à disposition de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] lors du traitement des messages.  
  
-   Créer un port de réception pour [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour recevoir d'un tiers le message entrant par lot .txt EDI X12.  
  
-   Créer un port d'envoi pour [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour créer un échange de chaque document informatisé reçu dans le lot (en cas de fractionnement du lot), ou pour créer un seul échange à partir des documents informatisés dans le lot reçu (en cas de conservation du lot). Le port d'envoi envoie ensuite le ou les échanges au tiers de destination. Ce port d'envoi est un port d'envoi unidirectionnel statique.  
  
-   Créer un tiers (partenaire commercial) pour Tiers A et Tiers B.  
  
-   Créer un profil d'entreprise pour les deux partenaires commerciaux.  
  
-   Créer un accord entre les deux profils en configurant les propriétés EDI pour recevoir le message, en fractionnant ou conservant l'échange.  
  
-   Déposer un échange EDI par lot dans le dossier local associé à l'emplacement de réception. Vous pouvez ensuite vérifier que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] a déposé les échanges distincts du lot reçu (en cas de fractionnement du lot) ou le seul échange par lot conservé (en cas de conservation du lot) dans le dossier associé au port d'envoi.  
  
    > [!NOTE]
    >  Si vous avez effectué les étapes de la procédure pas à pas d'envoi des échanges par lot, vous pouvez utiliser la sortie de cette solution comme entrée pour cette solution. La sortie de cette solution est un lot de deux messages 850. Pour plus d’informations, consultez [procédure pas à pas (X12) : envoi d’échanges traités par lot EDI](../core/walkthrough-x12-sending-batched-edi-interchanges.md).  
  
 Cette section décrit les étapes de configuration de la procédure pas à pas.  
  
##### <a name="to-deploy-the-message-schema"></a>Pour déployer le schéma de message  
  
1.  Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], créez ou ouvrez un projet BizTalk.  
  
    > [!NOTE]
    >  Cette rubrique part du principe que vous avez déjà ajouté une référence de votre application à l'application BizTalk EDI, qui contient les schémas, pipelines et orchestrations EDI. Dans le cas contraire, consultez [comment ajouter une référence à l’Application EDI de BizTalk Server](http://msdn.microsoft.com/library/7af066fb-372f-4709-b566-c8d6b4a9d782).  
  
2.  Avec le bouton droit de votre projet, pointez sur **ajouter**, puis cliquez sur **élément existant**. Déplacer vers  **\<lecteur\>: \Program Files\Microsoft 2009\XSD_Schema\EDI\X12\00401 de BizTalk Server**, puis double-cliquez sur le schéma correspondant à votre message de test.  
  
    > [!NOTE]
    >  Si les schémas EDI n’ont pas été décompressés dans les dossiers XSD_SchemaEDI, exécutez le **MicrosoftEdiXSDTemplates.exe** fichier dans le dossier XSD_SchemaEDI pour décompresser les schémas dans le dossier par défaut.  
  
    > [!NOTE]
    >  Pour un message test, vous pouvez utiliser l'échange par lot généré par la solution dans la procédure pas à pas d'envoi des échanges par lot. La sortie de cette solution est un lot de deux instances de l'exemple de message 850 utilisé pour le didacticiel pour développeur d'interface EDI Si vous le faites, vous devez utiliser le schéma x12_00401_850.xsd situé dans [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDKEDI Interface développeur TutorialInbound_EDI.  
  
3.  Définissez le fichier de clé d'assembly, puis créez et déployez l'assembly.  
  
##### <a name="to-create-a-one-way-receive-port-to-receive-the-batched-edi-messages"></a>Pour créer un port de réception unidirectionnel pour recevoir les messages EDI par lot  
  
1.  Dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, avec le bouton droit le **Ports de réception** nœud sous la **BizTalk Application 1** nœud **nouveau**, puis cliquez sur **Unidirectionnel Port de réception.**  
  
2.  Nommez le port de réception, puis cliquez sur **emplacements de réception** dans l’arborescence de la console.  
  
3.  Cliquez sur **Nouveau**.  
  
4.  Nom de l’emplacement de réception, sélectionnez **fichier** pour **Type**, puis cliquez sur **configurer**.  
  
5.  Entrez un dossier pour **dossier de réception**et un masque pour **masque de fichier**, tel que  **\*.txt**.  
  
6.  Cliquez sur **OK**.  
  
7.  Pour **pipeline de réception**, sélectionnez **EdiReceive**.  
  
8.  Cliquez sur **OK**.  
  
9. Dans l’arborescence de la console, cliquez sur **emplacements de réception**. Dans le **emplacements de réception** volet, cliquez sur votre emplacement de réception, puis cliquez sur **activer**.  
  
##### <a name="to-create-a-static-one-way-send-port-to-send-the-batched-edi-interchange"></a>Pour créer un port d'envoi unidirectionnel statique pour envoyer l'échange EDI par lot  
  
1.  Dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, avec le bouton droit le **Ports d’envoi** nœud sous la **BizTalk Application 1** nœud **nouveau**, puis cliquez sur **Port d’envoi unidirectionnel statique.**  
  
2.  Dans le **propriétés de Port d’envoi** boîte de dialogue, le nom du port d’envoi.  
  
3.  Dans le **Transport** section, sélectionnez **fichier** pour **Type**, puis cliquez sur **configurer**.  
  
4.  Entrez un dossier pour **dossier de Destination**et un masque pour **masque de fichier**, tel que  **\*.txt**.  
  
5.  Cliquez sur **OK**.  
  
6.  Dans **pipeline d’envoi**, sélectionnez **EdiSend**.  
  
7.  Dans l’arborescence de la console, sélectionnez **filtres**. Sur le **filtres** , entrez une expression de filtre qui peuvent s’abonner aux messages dans le lot. Par exemple, sélectionnez **BTS. ReceivePortName** pour **propriété**,  **==**  pour **opérateur**et le nom du port de réception que vous venez de créer pour **Valeur**.  
  
8.  Cliquez sur **OK**.  
  
9. Dans l’arborescence de la console, cliquez sur **Ports d’envoi**. Dans le **Ports d’envoi** volet, cliquez sur le port d’envoi, puis cliquez sur **Démarrer**.  
  
##### <a name="to-create-a-party-and-a-business-profile-for-party-a"></a>Pour créer un tiers et un profil d'entreprise pour Tiers A  
  
1.  Avec le bouton droit le **Parties** nœud dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, pointez sur **nouveau**, puis cliquez sur **tiers**.  
  
2.  Entrez un nom pour le tiers dans le **nom** zone de texte, puis cliquez sur **OK**.  
  
    > [!NOTE]
    >  En sélectionnant le **BizTalk Local traite les messages reçus par le tiers ou prend en charge l’envoi de messages à partir de ce tiers** case à cocher, vous pouvez spécifier que le tiers en cours de création est pour la même organisation qui héberge également [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. En prenant ces éléments en compte, certaines propriétés devront être activées et d'autres désactivées lors de la création d'un accord. Toutefois, pour les besoins de cette procédure pas à pas, vous pouvez laisser cette case à cocher activée.  
  
3.  Cliquez sur le nom du tiers, pointez sur **nouveau**, puis cliquez sur **profil d’entreprise**.  
  
4.  Dans le **propriétés de profil** boîte de dialogue le **général** , entrez **Tiersa_profile** dans les **nom** zone de texte.  
  
    > [!NOTE]
    >  Lorsque vous créez un tiers, un profil est également créé. Vous pouvez renommer et utiliser ce profil plutôt que d'en créer un nouveau. Pour renommer un profil, cliquez sur le profil et sélectionnez **propriétés**. Dans le **général** , spécifiez un nom pour le profil.  
  
##### <a name="to-create-a-party-and-a-business-profile-for-party-b"></a>Pour créer un tiers et un profil d'entreprise pour Tiers B  
  
1.  Avec le bouton droit le **Parties** nœud dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, pointez sur **nouveau**, puis cliquez sur **tiers**.  
  
2.  Entrez un nom pour le tiers dans le **nom** zone de texte, puis cliquez sur **OK**.  
  
    > [!NOTE]
    >  En sélectionnant le **BizTalk Local traite les messages reçus par le tiers ou prend en charge l’envoi de messages à partir de ce tiers** case à cocher, vous pouvez spécifier que le tiers en cours de création est pour la même organisation qui héberge également [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. En prenant ces éléments en compte, certaines propriétés devront être activées et d'autres désactivées lors de la création d'un accord. Toutefois, pour les besoins de cette procédure pas à pas, vous pouvez laisser cette case à cocher activée.  
  
3.  Cliquez sur le nom du tiers, pointez sur **nouveau**, puis cliquez sur **profil d’entreprise**.  
  
4.  Dans le **propriétés de profil** boîte de dialogue le **général** , entrez **Tiersb_profile** dans les **nom** zone de texte.  
  
    > [!NOTE]
    >  Lorsque vous créez un tiers, un profil est également créé. Vous pouvez renommer et utiliser ce profil plutôt que d'en créer un nouveau. Pour renommer un profil, cliquez sur le profil et sélectionnez **propriétés**. Dans le **général** , spécifiez un nom pour le profil.  
  
##### <a name="to-create-an-agreement-between-the-two-business-profiles"></a>Pour créer un accord entre les deux profils d'entreprise  
  
1.  Avec le bouton droit **Tiersa_profile**, pointez sur **nouveau**, puis cliquez sur **accord**.  
  
2.  Dans le **propriétés générales** page, pour le **nom** texte, entrez un nom pour l’accord.  
  
3.  À partir de la **protocole** la liste déroulante, sélectionnez **X12**.  
  
4.  Dans le **deuxième partenaire** section, à partir de la **nom** la liste déroulante, sélectionnez **Tiersb**.  
  
5.  Dans le **deuxième partenaire** section, à partir de la **profil** la liste déroulante, sélectionnez **Tiersb_profile**.  
  
     Vous remarquerez que les deux nouveaux onglets sont ajoutés à côté du **général** onglet. Chaque onglet sert à configurer un accord unidirectionnel, et chaque accord unidirectionnel constitue la transaction complète d'un message (en prenant également en compte les transferts du message et de l'accusé de réception).  
  
6.  Dans le **général** sous l’onglet dans le **propriétés générales** page, dans le **paramètres d’hôte communs** section, sélectionnez **activer le rapport d’état**, puis Sélectionnez **stocker la charge de message de création de rapports**.  
  
7.  Effectuer les tâches suivantes sur le **pourquoi -> Tiersb** onglet.  
  
    1.  Sur le **identificateurs** page sous le **paramètres de l’échange** section, entrez des valeurs pour les champs de qualificateur et identificateur (**ISA5**, **ISA6**, **ISA7**, et **ISA8**) qui correspondent aux valeurs de ces champs d’en-tête dans le message de test.  
  
        > [!NOTE]
        >  Les champs de qualificateur et d'identificateur pour l'expéditeur et le récepteur permettent à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] de résoudre l'accord. Il compare les valeurs de **ISA5**, **ISA6**, **ISA7**, et **ISA8** dans l’en-tête d’échange à celles dans les propriétés d’un accord. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]sera également l’accord en comparant le qualificateur de l’expéditeur et l’identificateur (sans le qualificateur du récepteur et l’identificateur). Si [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ne peut pas résoudre l'accord, il utilise les propriétés d'accord de secours.  
  
        > [!NOTE]
        >  Si vous utilisez le fichier SamplePO.txt à partir de « EDI Interface Developer Tutorial » comme message test, définissez **ISA5** à **ZZ**, **ISA6** à **THEM**, **ISA7** à **ZZ**, et **ISA8** à **US**.  
  
    2.  Sur le **Validation** page sous le **paramètres de l’échange** section, assurez-vous que **chercher isa13 en double** option est désactivée.  
  
        > [!NOTE]
        >  Effacer la **chercher isa13 en double** propriété vous permet de recevoir plusieurs instances du même message.  
  
    3.  Sur le **jeu de caractères et séparateurs** page sous le **paramètres de l’échange** section, sélectionnez le **CR LF** option.  
  
    4.  Sur le **paramètres d’hôte Local** page sous le **paramètres de l’échange** section, dans le **Option de traitement de Message entrant** boîte, sélectionnez le **Split L’échange en documents informatisés - suspendre les documents informatisés en cas d’erreur** option.  
  
        > [!NOTE]
        >  Pour commencer, dans cette solution, nous fractionnerons l'échange en sélectionnant cette option. Une version ultérieure, dans le cadre de [pour tester la procédure pas à pas](../core/walkthrough-x12-receiving-batched-edi-interchanges.md#BKMK_Proc) la procédure ci-dessous, nous allons configurer la solution pour préserver l’échange.  
  
    5.  Sur le **Ports d’envoi** page sous le **paramètres de l’échange** section, associez le port d’envoi que vous avez créé précédemment. Dans le **ports d’envoi** grille, sous la **nom** colonne, cliquez sur une cellule vide et dans la liste déroulante, sélectionnez le port d’envoi.  
  
    6.  Sur le **enveloppes** page sous le **paramètres des documents informatisés** section, entrez des valeurs pour toutes les colonnes dans la première ligne de la grille.  
  
        |Utiliser|Pour effectuer cette opération|  
        |--------------|----------------|  
        |**Default**|Sélectionnez **par défaut**. **Remarque :** lorsque vous sélectionnez cette ligne en tant que la valeur par défaut, les valeurs de **GS1**, **GS2**, **GS3**, **GS7**et **GS8** sont utilisées même si les valeurs de **Type de Transaction**, **Version/publication**, et **espace de noms cible** ne sont pas une correspondance pour le Message.|  
        |**Type de transaction**|Sélectionnez le type de message de votre message test, **850 - bon de commande**.|  
        |**Version/publication**|Entrez la version EDI, **00401**.|  
        |**Espace de noms cible**|Sélectionnez **http://schemas.microsoft.com/Edi/X12**.|  
        |**GS1**|Vérifiez que le type de message du message de test est sélectionné, **PO - bon de commande (850)**.|  
        |**GS2**|Entrez une valeur pour l’Application émettrice, par exemple, **achats**.|  
        |**GS3**|Entrez une valeur pour l’Application réceptrice, par exemple, **OrderControl**.|  
        |**GS4**|Sélectionnez le format de date souhaité. **Remarque :** vous devez sélectionner la valeur dans la liste déroulante, ne cliquez pas seulement dans le champ pour afficher la valeur par défaut. Si vous cliquez dans le champ sans sélectionner la valeur dans la liste déroulante, la valeur ne sera pas réellement sélectionnée.|  
        |**GS5**|Sélectionnez le format d'heure souhaité.|  
        |**GS7**|Sélectionnez **X - Accredited Standards Committee X12**.|  
        |**GS8**|Vérifiez que la version EDI a été entrée, **00401**.|  
  
        > [!NOTE]
        >  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]effet de définir les valeurs de GS01, GS02, GS03, GS04, GS05, GS07 et GS08 des accusés de réception sortants selon les valeurs entrées pour **Type de Transaction**, **Version/publication**, et **cible espace de noms**. Le pipeline d'envoi tente de faire correspondre le type de transaction, la version X12 et l'espace de noms cible avec les valeurs correspondantes dans l'en-tête du message. Si réussie, elle utilise les valeurs GS associées le **Type de Transaction**, **Version/publication**, et **espace de noms cible** valeurs.  
  
8.  Effectuer les tâches suivantes sur le **Tiersb -> Pourquoi** onglet.  
  
    > [!NOTE]
    >  Dans cette procédure pas à pas, la valeur requise est spécifiée sous l'onglet afin de permettre la création d'un accord. Pour créer un accord, les deux onglets d’accord unidirectionnel doivent avoir des valeurs définies pour **ISA5**, **ISA6**, **ISA7**, et **ISA8**.  
  
    1.  Sur le **identificateurs** page sous le **paramètres de l’échange** section, entrez des valeurs pour les champs de qualificateur et identificateur (**ISA5**, **ISA6**, **ISA7**, et **ISA8**) qui correspondent aux valeurs de ces champs d’en-tête dans le message de test.  
  
        > [!NOTE]
        >  Si vous utilisez le fichier SamplePO.txt à partir de « EDI Interface Developer Tutorial » comme message test, définissez **ISA5** à **ZZ**, **ISA6** à **américain**, **ISA7** à **ZZ**, et **ISA8** à **THEM**.  
  
9. Cliquez sur **Appliquer**.  
  
10. Cliquez sur **OK**. Le nouvel accord ajouté est répertorié dans le **accords** section de la **tiers et profils d’entreprise** volet. Le nouvel accord ajouté est activé par défaut.  
  
### <a name="testing-the-walkthrough"></a>Test de la procédure pas à pas  
 Cette section fournit des informations sur le test de la procédure pas à pas.  
  
####  <a name="BKMK_Proc"></a>Pour tester la procédure pas à pas  
  
1.  Dans l'Explorateur Windows, ouvrez le dossier local associé à l'emplacement de réception, puis déposez un échange EDI par lot test dans le dossier.  
  
    > [!NOTE]
    >  Pour un message test, vous pouvez utiliser la sortie de l'échange par lot générée par la solution dans la procédure pas à pas d'envoi des échanges par lot. Cet exemple de message contient deux documents informatisés.  
  
2.  Ouvrez le dossier que vous avez associé au port d'envoi que vous avez créé précédemment. Vérifiez que le dossier contient deux nouveaux fichiers et que chaque fichier est un échange 850 contenant l'un des documents informatisés dans le message par lot test.  
  
3.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, cliquez sur le **Parties** nœud, cliquez sur un des profils d’entreprise qui font partie de l’accord créé précédemment. Dans le **accords** section, avec le bouton droit de l’accord, puis cliquez sur **propriétés**.  
  
4.  Dans le **propriétés de l’accord** boîte de dialogue le **paramètres d’hôte Local** page sous le **paramètres de l’échange** section, dans le **Message entrant Option de traitement** , sélectionnez soit **préserver l’échange : suspendre l’échange en cas d’erreur** ou **préserver l’échange : suspendre les documents informatisés en cas d’erreur** et cliquez sur **OK**.  
  
5.  Cliquez sur **Instances d’hôte** sous le **paramètres de plateforme** nœud, avec le bouton droit **BizTalkServerApplication**, puis cliquez sur **redémarrer**.  
  
6.  Dans l'Explorateur Windows, ouvrez le dossier local associé à l'emplacement de réception, puis déposez à nouveau l'échange EDI par lot test dans le dossier.  
  
7.  Dans l'Explorateur Windows, ouvrez le dossier que vous avez associé au port d'envoi que vous avez créé précédemment. Assurez-vous que le dossier contient désormais uniquement un nouveau fichier, à savoir un échange contenant les deux documents informatisés 850 qui étaient dans le message par lot test.  
  
## <a name="see-also"></a>Voir aussi  
 [Développement et la configuration des Solutions EDI BizTalk Server](../core/developing-and-configuring-biztalk-server-edi-solutions.md)   
 [Fractionnement d’un échange EDI par lot](../core/splitting-a-batched-edi-interchange.md)   
 [Fractionnement de sous-documents HIPAA](../core/splitting-hipaa-subdocuments.md)   
 [En conservant un reçu par lot échange EDI](../core/preserving-a-received-batched-edi-interchange.md)   
 [Procédure pas à pas (X12) : Envoi d’échanges EDI par lot](../core/walkthrough-x12-sending-batched-edi-interchanges.md)   
 [Procédure pas à pas (X12) : Réception des échanges EDI et envoi d’un accusé](../core/walkthrough-x12--receive-edi-interchanges-and-send-back-an-acknowledgement.md)   
 [Procédure pas à pas (X12) : envoi des échanges EDI](../core/walkthrough-x12-sending-edi-interchanges.md)