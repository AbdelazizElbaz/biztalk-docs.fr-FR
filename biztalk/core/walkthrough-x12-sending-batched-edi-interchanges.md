---
title: "Procédure pas à pas (X12) : Envoi d’échanges traités par lot EDI | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b80ea79b-6112-49bd-90e8-9a0a0e604df8
caps.latest.revision: "54"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5d5ce491b5cf9ff3d1c142599edee4e6c5f6a324
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="walkthrough-x12-sending-batched-edi-interchanges"></a>Procédure pas à pas (X12) : envoi d'échanges EDI traités par lot
Cette procédure pas à pas fournit des instructions détaillées sur la création d'une solution d'envoi d'échanges EDI par lot d'un tiers à un autre à l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
## <a name="how-the-solution-sends-batched-edi-interchanges"></a>Envoi des échanges EDI par lot par la solution  
 La solution effectue les opérations suivantes :  
  
1.  L’emplacement de réception reçoit un échange EDI à partir d’un **tiers A**.  
  
    > [!NOTE]
    >  Les événements dans cette liste peuvent se produire dans un ordre différent de celui indiqué.  
  
2.  Le pipeline de réception convertit le format EDI de l'échange au format XML interne. Le pipeline de réception détermine si l'échange doit être traité par lot. En conséquence, le composant BatchMarkerReceivePipeline promeut les propriétés `EDI.ToBeBatched==True` et `EDI.BatchId`. Il dépose ensuite l'échange dans la boîte MessageBox.  
  
3.  L'orchestration de traitement par lot récupère l'échange reçu dans la boîte MessageBox parce qu'il s'abonne au message sur la base de `EDI.ToBeBatched==True` et `EDI.BatchId==%BatchID%`.  
  
4.  L'emplacement de réception reçoit un deuxième échange EDI du même tiers qui a envoyé le premier échange.  
  
5.  L'emplacement de réception traite l'échange comme à l'étape 2, puis dépose l'échange dans la boîte MessageBox.  
  
6.  L'orchestration du traitement par lot récupère l'échange comme à l'étape 3.  
  
7.  Lorsque les critères de déclenchement sont satisfaits (les critères de déclenchement définissent comment les échanges doivent être mis en correspondance), l'orchestration du traitement par lot assemble l'échange contenant tous les échanges, puis promeut les propriétés de contexte `EDI.ToBeBatched==False`, `EDI.BatchName` et `EDI.DestinationPartyName`. Il dépose l'échange par lot dans la boîte MessageBox.  
  
8.  Le port d'envoi récupère l'échange par lot par un abonnement sur les propriétés de contexte `EDI.ToBeBatched`==False, `EDI.BatchName` et `EDI.DestinationPartyName`.  
  
9. Le pipeline d’envoi applique des propriétés supplémentaires à l’enveloppe de l’échange par lot, puis envoie l’échange au tiers de destination, **tiers B**.  
  
    > [!NOTE]
    >  Pour plus d’informations, consultez [assembler un échange EDI par lot](../core/assembling-a-batched-edi-interchange.md).  
  
 L'architecture de cette solution est représentée dans la figure suivante.  
  
 ![Envoi par lot des échanges EDI](../core/media/93a09e3c-476d-4bd2-a0e3-b5b219858791.gif "93a09e3c-476d-4bd2-a0e3-b5b219858791")  
  
## <a name="the-functionality-in-this-solution"></a>Fonctionnalités dans la solution  
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
  
## <a name="configuring-and-testing-the-walkthrough"></a>Configuration et test de la procédure pas à pas  
 Les étapes suivantes sont requises pour configurer cette solution :  
  
-   Ajouter le ou les schémas de message requis à un projet BizTalk, puis créer et déployer le projet afin que le ou les schémas soient mis à disposition de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] lors du traitement des messages.  
  
-   Mettre à jour de l’intervalle d’interrogation de l’adaptateur SQL dans le **BatchControlMessageReccvLoc** emplacement de réception, afin que l’orchestration de traitement par lot sera rapidement activée lorsque vous cliquez sur le **Démarrer** bouton à envoyer le message de contrôle permettant d’Active une instance d’orchestration de traitement par lot.  
  
-   Créez un port de réception pour [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour recevoir d'un tiers les messages entrants .txt EDI X12.  
  
-   Créer un tiers (partenaire commercial) pour Tiers A et Tiers B.  
  
-   Créer un profil d'entreprise pour les deux partenaires commerciaux.  
  
-   Créer un accord entre les deux profils via la configuration des propriétés EDI du message à recevoir. Configurez les propriétés EDI du message par lot à envoyer. Pour cette solution, configurez les accords de manière à ce que BizTalk Server envoie un lot au Tiers B dès réception de deux échanges 850.  
  
-   Créez un port d'envoi à partir duquel [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] puisse envoyer l'échange EDI par lot au partenaire commercial. Ce port d'envoi est un port d'envoi unidirectionnel statique.  
  
-   Associez le port d'envoi à l'accord qui traite les échanges et les met en correspondance.  
  
-   Faites glisser deux échanges EDI tests dans le dossier local associé à l'emplacement de réception, et vérifiez que BizTalk Server a déposé un échange par lot dans le dossier associé au port d'envoi.  
  
### <a name="configuring-the-walkthrough"></a>Configuration de la procédure pas à pas  
 Cette section décrit les étapes de configuration de la procédure pas à pas.  
  
##### <a name="to-deploy-the-message-schema"></a>Pour déployer le schéma de message  
  
1.  Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], créez ou ouvrez un projet BizTalk.  
  
    > [!NOTE]
    >  Cette rubrique part du principe que vous avez déjà ajouté une référence de votre application à l'application BizTalk EDI, qui contient les schémas, pipelines et orchestrations EDI. Dans le cas contraire, consultez [comment ajouter une référence à l’Application EDI de BizTalk Server](http://msdn.microsoft.com/library/7af066fb-372f-4709-b566-c8d6b4a9d782).  
  
2.  Avec le bouton droit de votre projet, pointez sur **ajouter**, puis cliquez sur **élément existant**. Accédez à [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema\EDI\X12\00401, puis double-cliquez sur le schéma correspondant à votre message test.  
  
    > [!NOTE]
    >  Si les schémas EDI n’ont pas été décompressés dans les dossiers \XSD_Schema\EDI, exécutez le **MicrosoftEdiXSDTemplates.exe** fichier dans le dossier \XSD_Schema\EDI pour décompresser les schémas dans le dossier par défaut.  
  
    > [!NOTE]
    >  Pour un message test, vous pouvez utiliser l'exemple de message 850 utilisé dans le didacticiel pour développeur d'interface EDI. Ce fichier est SamplePO.txt dans [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial\\. Dans ce cas, vous devez utiliser le schéma x12_00401_850.xsd situé dans [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial\Inbound_EDI.  
  
3.  Définissez le fichier de clé d'assembly, puis créez et déployez l'assembly.  
  
##### <a name="to-update-the-polling-interval"></a>Pour mettre à jour la fréquence d'interrogation  
  
1.  Dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, ouvrez le **groupe BizTalk**, **Applications**, **Application EDI BizTalk** nœuds, et **emplacements de réception**  nœuds. Sous le **emplacements de réception** nœud, avec le bouton droit **BatchControlMessageRecvLoc**, puis cliquez sur **propriétés**.  
  
2.  Pour le type de transport SQL, cliquez sur **configurer**.  
  
3.  Dans le **propriétés du Transport SQL** boîte de dialogue, définissez l’intervalle d’interrogation sur une valeur inférieure. Par exemple, vous pouvez modifier **unité de mesure de l’interrogation** à **secondes**, au lieu des minutes, pour modifier l’intervalle d’interrogation à 5 secondes.  
  
    > [!NOTE]
    >  La modification de la fréquence d'interrogation assure que l'orchestration de traitement par lot sera rapidement activée.  
  
4.  Cliquez sur **OK**, puis cliquez sur **OK** à nouveau.  
  
##### <a name="to-create-a-one-way-receive-port-to-receive-the-edi-messages-to-be-batched"></a>Pour créer un port de réception unidirectionnel pour recevoir les messages EDI à traiter par lot  
  
1.  Créez un dossier local pour recevoir les messages EDI à traiter par lot.  
  
2.  Dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, avec le bouton droit le **Ports de réception** nœud sous la **BizTalk Application 1** nœud **nouveau**, puis cliquez sur **Unidirectionnel Port de réception.**  
  
3.  Nommez le port de réception, puis cliquez sur **emplacements de réception** dans l’arborescence de la console.  
  
4.  Cliquez sur **Nouveau**.  
  
5.  Nom de l’emplacement de réception, sélectionnez **fichier** pour **Type**, puis cliquez sur **configurer**.  
  
6.  Entrez un dossier pour **dossier de réception**et un masque pour **masque de fichier**, tel que  **\*.txt**.  
  
7.  Cliquez sur **OK**.  
  
8.  Pour **pipeline de réception**, sélectionnez **EdiReceive**.  
  
9. Cliquez sur **OK**, puis cliquez sur **OK** à nouveau.  
  
10. Dans l’arborescence de la console, cliquez sur **emplacements de réception**. Dans le **emplacements de réception** volet, cliquez sur votre emplacement de réception, puis cliquez sur **activer**.  
  
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
  
    4.  Sur le **Configuration de lot** page sous le **paramètres de l’échange** section, procédez comme suit :  
  
        1.  Cliquez sur **nouveau lot**.  
  
        2.  Sous le **Identification** section, pour **nom** texte, entrez `Batch1`.  
  
        3.  Sous le **filtre** , cliquez sur le **filtre** bouton, puis, dans le **filtre par lot** boîte de dialogue zone, procédez comme suit :  
  
            1.  Cliquez sur la cellule vide sous la **propriété** colonne et sélectionnez **BTS. ReceivePortName**.  
  
            2.  Cliquez sur la cellule vide sous la **opérateur** colonne et sélectionnez  **==** .  
  
            3.  Cliquez sur la cellule vide sous la **valeur** colonne et entrez le nom du port de réception que vous avez créé précédemment.  
  
            4.  Cliquez sur **OK**.  
  
        4.  Sous le **version** section, sélectionnez le **nombre maximal de transaction définit** option, dans la liste déroulante, sélectionnez **échange**et dans la zone de texte, entrez le nombre de échanges sont traités par lot. Dans cette solution, vous serez traiter par lot deux échanges, dans la zone de texte, entrez `2`.  
  
        5.  Sous le **Activation** section, sélectionnez **démarrer immédiatement**.  
  
    5.  Sur le **enveloppes** page sous le **paramètres des documents informatisés** section, entrez des valeurs pour toutes les colonnes dans la première ligne de la grille.  
  
        |Utiliser|Pour effectuer cette opération|  
        |--------------|----------------|  
        |**Default**|Sélectionnez **par défaut**. **Remarque :** lorsque vous sélectionnez cette ligne en tant que la valeur par défaut, les valeurs de **GS1**, **GS2**, **GS3**, **GS7**et **GS8** sont utilisées même si les valeurs de **Type de Transaction**, **Version/publication**, et **espace de noms cible** ne sont pas une correspondance pour le Message.|  
        |**Type de transaction**|Sélectionnez le type de message de votre message test, **850 - bon de commande**.|  
        |**Version/publication**|Entrez la version EDI, **00401**.|  
        |**Espace de noms cible**|Sélectionnez **http://schemas.microsoft.com/BizTalk/Edi/X12/2006**.|  
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
  
##### <a name="to-create-a-static-one-way-send-port-to-send-the-batched-edi-interchange"></a>Pour créer un port d'envoi unidirectionnel statique pour envoyer l'échange EDI par lot  
  
1.  Créez un dossier local pour envoyer le message EDI à traiter par lot.  
  
2.  Dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, avec le bouton droit le **Ports d’envoi** nœud sous la **BizTalk Application 1** nœud **nouveau**, puis cliquez sur **Port d’envoi unidirectionnel statique.**  
  
3.  Dans le **propriétés de Port d’envoi** boîte de dialogue, le nom du port d’envoi.  
  
4.  Dans le **Transport** section, sélectionnez **fichier** pour **Type**, puis cliquez sur **configurer**.  
  
5.  Entrez un dossier pour **dossier de Destination**et un **nom de fichier**, tel que **%MessageID%.txt**.  
  
6.  Cliquez sur **OK**.  
  
7.  Dans **pipeline d’envoi**, sélectionnez **EdiSend**.  
  
8.  Dans l’arborescence de la console, sélectionnez **filtres**. Sur le **filtres** page, procédez comme suit :  
  
    1.  Sur la première ligne de la grille, sélectionnez **EDI. DestinationPartyName** pour **propriété**,  **==**  pour **opérateur**, le nom que vous avez sélectionné pour le tiers auquel envoyer le lot à pour  **Valeur**, et **et** pour **regrouper par**.  
  
    2.  Sur la deuxième ligne, sélectionnez **EDI. ToBeBatched** pour **propriété**,  **==**  pour **opérateur**, et **False** pour  **Valeur**, et **et** pour **regrouper par**.  
  
    3.  Sur la troisième ligne, sélectionnez **EDI. BatchName** pour **propriété**,  **==**  pour **opérateur**et le nom du lot pour **valeur**.  
  
9. Cliquez sur **OK**.  
  
10. Dans l’arborescence de la console, cliquez sur **Ports d’envoi**. Dans le **Ports d’envoi** volet, cliquez sur le port d’envoi, puis cliquez sur **Démarrer**.  
  
##### <a name="to-associate-the-send-port-with-the-agreement-created-for-batching"></a>Pour associer le port d'envoi à l'accord créé pour le traitement par lot  
  
1.  Avec le bouton droit de l’accord que vous avez créé précédemment et cliquez sur **propriétés**.  
  
2.  Dans le **propriétés de l’accord** boîte de dialogue le **pourquoi -> Tiersb** , cliquez sur **Ports d’envoi** dans le volet gauche.  
  
3.  Sur le **Ports d’envoi** page sous le **paramètres de l’échange** section, associez le port d’envoi que vous avez créé précédemment. Dans le **ports d’envoi** grille, sous la **nom** colonne, cliquez sur une cellule vide et dans la liste déroulante, sélectionnez le port d’envoi.  
  
4.  Cliquez sur **OK**.  
  
### <a name="testing-the-walkthrough"></a>Test de la procédure pas à pas  
 Cette section fournit des informations sur le test de la procédure pas à pas.  
  
##### <a name="to-test-the-walkthrough"></a>Pour tester la procédure pas à pas  
  
1.  Dans l'Explorateur Windows, ouvrez le dossier local associé à l'emplacement de réception, puis déposez un échange EDI test dans le dossier.  
  
    > [!NOTE]
    >  Pour un message test, vous pouvez utiliser l'exemple de message 850 utilisé dans le didacticiel pour développeur d'interface EDI. Ce fichier est SamplePO.txt dans [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial\\. Dans ce cas, vous devez utiliser le schéma x12_00401_850.xsd situé dans [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial\Inbound_EDI.  
  
2.  Placez une deuxième copie de l'échange EDI test dans le dossier.  
  
3.  Ouvrez le dossier que vous avez associé au port d'envoi des échanges, puis ouvrez l'échange traité par lot. Vérifiez que l'échange contient un jeu d'en-têtes ISA et GS, et deux documents informatisés.  
  
## <a name="see-also"></a>Voir aussi  
 [Développement et la configuration des Solutions EDI BizTalk Server](../core/developing-and-configuring-biztalk-server-edi-solutions.md)   
 [Configuration d’un lot sortant](../core/configuring-an-outgoing-batch.md)   
 [Assembler un échange EDI par lot](../core/assembling-a-batched-edi-interchange.md)   
 [Assembler un échange EDI par lot](../core/assembling-a-batched-edi-interchange.md)   
 [Procédure pas à pas (X12) : Réception des échanges EDI et envoi d’un accusé](../core/walkthrough-x12--receive-edi-interchanges-and-send-back-an-acknowledgement.md)   
 [Procédure pas à pas (X12) : Envoi d’échanges EDI](../core/walkthrough-x12-sending-edi-interchanges.md)