---
title: "Procédure pas à pas (X12) : Envoi d’échanges EDI | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 05533821-b9eb-44bc-af65-b6fb0b545137
caps.latest.revision: "36"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fc29d8739aeff07241c1491ba7ae96dcf7260372
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="walkthrough-x12-sending-edi-interchanges"></a>Procédure pas à pas (X12) : envoi des échanges EDI
Cette procédure pas à pas fournit des instructions détaillées sur la création d'une solution d'envoi d'échanges EDI à l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
## <a name="how-the-solution-sends-edi-interchanges"></a>Envoi des échanges EDI par la solution  
 La solution effectue les opérations suivantes :  
  
1.  Un port unidirectionnel de réception FILE reçoit un message EDI de Fabrikam.  
  
2.  À l'aide du pipeline EdiReceive, le port de réception contrôle le message et le convertit en XML. Le port de réception dépose ensuite le message test dans MessageBox.  
  
3.  Un port d'envoi unidirectionnel statique récupère le message XML dans MessageBox.  
  
4.  Le port d'envoi unidirectionnel statique valide le message EDI par rapport au schéma de message, sérialise le message EDI dans un échange EDI, puis envoie le message EDI au dossier local du partenaire commercial Contoso.  
  
## <a name="the-functionality-in-this-solution"></a>Fonctionnalités dans la solution  
 Cette procédure pas à pas utilise les fonctionnalités suivantes :  
  
-   Cette procédure pas à pas ne teste pas la réception d'un accusé de réception. Pour comprendre comment recevoir un accusé de réception, consultez la rubrique [procédure pas à pas (X12) : réception des échanges EDI et envoi d’un accusé](../core/walkthrough-x12--receive-edi-interchanges-and-send-back-an-acknowledgement.md)  
  
-   La solution est conçue pour les échanges basés sur le codage X12, et non le codage EDIFACT.  
  
    > [!NOTE]
    >  La configuration utilisée pour HIPAA et pour le codage EDIFACT est proche de celle utilisée pour le codage X12.  
  
-   La validation de type EDI et la validation étendue sont effectuées sur l'échange sortant.  
  
-   La solution utilise un port d'envoi unidirectionnel statique avec un type de transport FILE.  
  
    > [!NOTE]
    >  Au lieu d'un port d'envoi unidirectionnel statique, vous pouvez utiliser un port d'envoi bidirectionnel statique pour envoyer l'échange et recevoir l'accusé de réception. Vous pouvez également utiliser un port d'envoi unidirectionnel dynamique pour envoyer l'échange. Pour plus d’informations sur l’utilisation d’un port d’envoi dynamique, consultez [configuration d’un Port d’envoi dynamique pour envoyer les échanges EDI et les accusés de réception](../core/configuring-a-dynamic-send-port-to-send-edi-interchanges-and-acknowledgments.md).  
  
    > [!NOTE]
    >  Vous pouvez utiliser un adaptateur HTTP et un transport AS2. Pour plus d’informations, consultez [procédure pas à pas (AS2) : envoi d’EDI via AS2 avec un MDN synchrone](../core/walkthrough-as2-sending-edi-over-as2-with-a-synchronous-mdn.md) ou [procédure pas à pas (AS2) : envoi d’EDI via AS2 avec MDN asynchrone](../core/walkthrough-as2-sending-edi-over-as2-with-an-asynchronous-mdn.md).  
  
-   La création de rapports EDI est activée. Les documents informatisés sont enregistrés pour être consultables depuis le rapport État de l'échange.  
  
-   À des fins de test, la solution utilise un emplacement de réception pour recevoir un message test.  
  
 La figure suivante présente l'architecture de cette solution qui utilise un port d'envoi unidirectionnel statique.  
  
 ![Envoi d’échanges EDI](../core/media/6915024c-687c-4076-a730-3f7b9d2db7fb.gif "6915024c-687c-4076-a730-3f7b9d2db7fb")  
  
## <a name="configuring-and-testing-the-walkthrough"></a>Configuration et test de la procédure pas à pas  
 Les étapes suivantes sont requises pour configurer cette solution :  
  
-   Ajouter le ou les schémas de message requis à un projet BizTalk, puis créer et déployer le projet afin que le ou les schémas soient mis à disposition de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] lors du traitement de l'échange sortant.  
  
-   Créer un port de réception et un emplacement où [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] puisse recevoir l'échange EDI. Cet emplacement de réception est lié au dossier de fichiers dans lequel Fabrikam place l'échange EDI à envoyer à Contoso. L'emplacement de réception utilise un pipeline de réception EdiReceive.  
  
-   Créer un port d'envoi à partir duquel [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] puisse envoyer l'échange EDI à Contoso. Dans cette procédure pas à pas, vous allez créer un port d'envoi unidirectionnel statique.  
  
-   Créer un tiers (partenaire commercial) pour Fabrikam et Contoso.  
  
-   Créer un profil d'entreprise pour les deux partenaires commerciaux.  
  
-   Créer un accord entre les deux profils via la configuration des propriétés EDI du message à recevoir.  
  
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
  
1.  Dans l’Explorateur Windows, créez un dossier local pour recevoir l’échange dans.  
  
2.  Dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, avec le bouton droit le **Ports de réception** nœud sous la **BizTalk Application 1** nœud **nouveau**, puis cliquez sur **Unidirectionnel Port de réception**.  
  
3.  Nommez le port de réception, puis cliquez sur **emplacements de réception** dans l’arborescence de la console.  
  
4.  Cliquez sur **Nouveau**.  
  
5.  Nom de l’emplacement de réception, sélectionnez **fichier** pour **Type**, puis cliquez sur **configurer**.  
  
6.  Entrez un dossier pour **dossier de réception**, puis entrez  **\*.txt** pour le masque de fichier.  
  
7.  Cliquez sur **OK**.  
  
8.  Pour **pipeline de réception**, sélectionnez **EdiReceive**.  
  
9. Cliquez sur **OK**, puis cliquez sur **OK** à nouveau.  
  
10. Dans l’arborescence de la console, cliquez sur **emplacements de réception**. Dans le **emplacements de réception** volet, cliquez sur votre emplacement de réception, puis cliquez sur **activer**.  
  
##### <a name="to-create-a-static-one-way-send-port-for-contoso-to-send-the-edi-interchange"></a>Pour créer un port d'envoi unidirectionnel statique (pour Contoso) permettant d'envoyer l'échange EDI  
  
1.  Dans l'Explorateur Windows, créez un dossier local auquel envoyer l'échange EDI.  
  
2.  Dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, avec le bouton droit le **Ports d’envoi** nœud sous la **BizTalk Application 1** nœud **nouveau**, puis cliquez sur **Port d’envoi unidirectionnel statique**.  
  
3.  Dans le **propriétés de Port d’envoi** boîte de dialogue, le nom du port d’envoi.  
  
4.  Dans le **Transport** section, sélectionnez le **Type**, par exemple, **fichier**.  
  
5.  Si vous utilisez un type de fichier, cliquez sur **configurer**. Dans **dossier de Destination**, accédez au dossier pour envoyer l’échange. Pour **nom de fichier**, entrez **%MessageID%.edi**. Cliquez sur **OK**.  
  
6.  Dans **pipeline d’envoi**, sélectionnez **EdiSend**.  
  
7.  Dans l’arborescence de la console, sélectionnez **filtres**, puis entrez une expression de filtre du port d’envoi à utiliser pour vous abonner au message. Par exemple, vous pouvez utiliser comme expression de filtre l'emplacement de réception qui recevra le message test original. Pour ce faire, **propriété**, entrez **BTS. ReceivePortName**; pour **opérateur**, entrez  **==** ; et pour **valeur** Entrez le nom du port de réception que vous avez créé à recevoir le message XML de Fabrikam.  
  
    > [!NOTE]
    >  Vous pouvez filtrer sur une autre propriété de votre choix, telle que BTS.MessageType.  
  
8.  Cliquez sur **OK**.  
  
9. Cliquez sur le **Ports d’envoi** nœud dans la Console d’Administration, cliquez sur le port d’envoi, puis cliquez sur **Démarrer**.  
  
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
  
    2.  Sur le **Validation** page sous le **paramètres de l’échange** section, assurez-vous que **chercher isa13 en double** option est désactivée.  
  
        > [!NOTE]
        >  Effacer la **chercher isa13 en double** propriété vous permet de recevoir plusieurs instances du même message.  
  
    3.  Sur le **jeu de caractères et séparateurs** page sous le **paramètres de l’échange** section, sélectionnez le **CR LF** option.  
  
    4.  Sur le **Ports d’envoi** page sous le **paramètres d’échange** section, associez le port d’envoi qui recevra l’échange EDI de Fabrikam. Dans le **ports d’envoi** grille, sous la **nom** colonne, cliquez sur une cellule vide et dans la liste déroulante, sélectionnez le port d’envoi créé pour la réception de l’échange EDI de Fabrikam.  
  
    5.  Sur le **Validation** page sous le **paramètres des documents informatisés** conservez **Validation de Type EDI** activée et activez **devalidationétendue**.  
  
    6.  Si vous utilisez l’un des schémas standards fournis avec [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], dans le **paramètres d’hôte Local** page sous le **paramètres des documents informatisés** , sélectionnez l’espace de noms du schéma à être utilisé pour traiter l’échange entrant.  
  
        |Utiliser|Pour effectuer cette opération|  
        |--------------|----------------|  
        |**Default**|Activez la case à cocher dans la colonne.|  
        |**Pour ST1**|Sélectionnez **850 - bon de commande**.|  
        |**GS2**|Entrez **THEM**.|  
        |**Cible Namespace**|Sélectionnez **http://schemas.microsoft.com/BizTalk/EDI/X12/2006**.|  
  
        > [!NOTE]
        >  La définition des propriétés permet à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] d'identifier le schéma à utiliser pour le traitement de l'échange 850 entrant. Si les valeurs GS02 et ST01 d'un échange sont entrées dans une ligne de la grille, l'espace de noms cible dans la même ligne sert à déterminer le schéma à utiliser.  
  
    7.  Sur le **enveloppes** page sous le **paramètres des documents informatisés** section, entrez des valeurs pour toutes les colonnes dans la première ligne de la grille.  
  
        |Utiliser|Pour effectuer cette opération|  
        |--------------|----------------|  
        |**Default**|Activez la case à cocher dans la **par défaut** colonne. **Remarque :** lorsque vous sélectionnez cette ligne en tant que la valeur par défaut, les valeurs de **GS1**, **GS2**, **GS3**, **GS7**et **GS8** sont utilisées même si les valeurs de **Type de Transaction**, **Version/publication**, et **espace de noms cible** ne sont pas une correspondance pour le Message.|  
        |**Type de transaction**|Sélectionnez le type de message de votre message test, **850 - bon de commande**.|  
        |**Version/publication**|Entrez la version EDI, **00401**.|  
        |**Espace de noms cible**|Sélectionnez **http://schemas.microsoft.com/BizTalk/Edi/X12/2006**.|  
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
  
2.  Dans l'Explorateur Windows, ouvrez le dossier de destination spécifié pour le port d'envoi. Vérifiez que le dossier contient un échange EDI de sortie dont les en-têtes ISA, GS et ST correspondent aux valeurs entrées dans les propriétés d'accord.  
  
## <a name="see-also"></a>Voir aussi  
 [Développement et la configuration des Solutions EDI BizTalk Server](../core/developing-and-configuring-biztalk-server-edi-solutions.md)