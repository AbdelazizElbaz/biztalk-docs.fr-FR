---
title: "Étape 10 : Configurer l’accord de partenariat X12 et AS2 commerciaux | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8fcdb3af-727a-4d20-9dcf-cf162e7d3398
caps.latest.revision: "46"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bd0ce0ef6fef056c52e06fc1843024cbcf683c84
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-10-configure-the-x12-and-as2-trading-partner-agreement"></a>Étape 10 : Configurer l’accord de partenariat X12 et AS2 commerciaux
![Étape 10 11](../core/media/tut-step10-of-11.gif "Tut_Step10_of_11")  
  
 Au cours de cette étape, vous allez définir des accords de partenariat commercial X12 et AS2 pour transporter un message EDIINT/AS2 via HTTP. Le tiers Fabrikam envoie l'échange EDI à Contoso, qui renvoie l'accusé de réception 997 et un MDN asynchrone à Fabrikam.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez ouvrir une session en tant que membre du groupe Administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
### <a name="to-create-an-as2-agreement"></a>Pour créer un accord AS2  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur **Microsoft BizTalk Server**, puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration, cliquez sur **Parties** dans l’arborescence de la console, puis, dans le **tiers et profils d’entreprise** page, cliquez sur **Fabrikam_Profile**, pointez sur **nouveau**, puis cliquez sur **accord**.  
  
3.  Dans le **propriétés générales** page, pour le **nom** texte, entrez un nom pour l’accord.  
  
4.  À partir de la **protocole** la liste déroulante, sélectionnez **AS2**.  
  
5.  Dans le **deuxième partenaire** section, à partir de la **nom** la liste déroulante, sélectionnez **Contoso**.  
  
6.  Dans le **deuxième partenaire** section, à partir de la **profil** la liste déroulante, sélectionnez **Contoso_Profile**.  
  
     Vous remarquerez que les deux nouveaux onglets sont ajoutés à côté du **général** onglet. Chaque onglet permet de configurer un accord AS2 unidirectionnel.  
  
7.  Dans le **général** sous l’onglet dans le **propriétés générales** page, dans le **paramètres d’hôte communs** section, sélectionnez **activer le rapport d’état**.  
  
8.  Effectuer les tâches suivantes sur le **Fabrikam -> Contoso** onglet.  
  
    1.  Sur le **identificateurs** , entrez des valeurs pour **AS2-de** et **AS2-pour**. Pour **AS2-de**, entrez `Fabrikam`. Pour **AS2 - To**, entrez `Contoso`.  
  
    2.  Sur le **Validation** page, sélectionnez le **utiliser les paramètres de l’accord pour validation et MDN au lieu de l’en-tête de message** case à cocher  
  
        > [!NOTE]
        >  La configuration de cette propriété garantit que les propriétés du tiers seront utilisées lors de la génération du MDN, au lieu des en-têtes AS2 du message AS2 reçu.  
  
    3.  Dans le **accusés de réception (MDN)** page, procédez comme suit :  
  
        1.  Sélectionnez le **exiger le MDN** case à cocher.  
  
        2.  Assurez-vous que le **exiger le MDN signé** case à cocher est désactivée.  
  
        3.  Sélectionnez le **exiger le MDN asynchrone** case à cocher.  
  
        4.  Dans le **Receipt-Delivery-Option (URL)** texte, entrez `http://localhost/Fabrikam/Default.aspx?Destination=_MDNToFabrikam`.  
  
9. Effectuer les tâches suivantes sur le **Contoso -> Fabrikam** onglet.  
  
    1.  Sur le **identificateurs** , entrez des valeurs pour **AS2-de** et **AS2-pour**. Pour **AS2-de**, entrez `Contoso`. Pour **AS2 - To**, entrez `Fabrikam`.  
  
    2.  Sur le **Ports d’envoi** page sous le **paramètres de l’échange** section, dans le **Ports d’envoi** liste, pour **nom** sélectionnez  **Send_Async_997**.  
  
        > [!NOTE]
        >  Le port d’envoi Send_Async_997 doit être entré dans le **Ports d’envoi** liste afin que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] peut résoudre le tiers pour le message 997 sortant. Le pipeline d'envoi mappe le nom du port d'envoi au port d'envoi dans les propriétés de l'accord. Une telle opération est nécessaire car dans ce cas, la propriété AS2-To n'est pas promue dans le contexte du message, qui est la première correspondance que le pipeline d'envoi tente d'effectuer pour résoudre le tiers. Pour plus d’informations, consultez [résolution de l’accord pour les Messages AS2 sortants](../core/agreement-resolution-for-outgoing-as2-messages.md).  
  
10. Cliquez sur **Appliquer**.  
  
11. Cliquez sur **OK**. Le nouvel accord ajouté est répertorié dans le **accords** section de la **tiers et profils d’entreprise** volet. Le nouvel accord ajouté est activé par défaut.  
  
### <a name="to-create-an-x12-agreement"></a>Pour créer un accord X12  
  
1.  Avec le bouton droit **Fabrikam_Profile**, pointez sur **nouveau**, puis cliquez sur **accord**.  
  
2.  Dans le **propriétés générales** page, pour le **nom** texte, entrez un nom pour l’accord.  
  
3.  À partir de la **protocole** la liste déroulante, sélectionnez **X12**.  
  
4.  Dans le **deuxième partenaire** section, à partir de la **nom** la liste déroulante, sélectionnez **Contoso**.  
  
5.  Dans le **deuxième partenaire** section, à partir de la **profil** la liste déroulante, sélectionnez **Contoso_Profile**.  
  
     Vous remarquerez que les deux nouveaux onglets sont ajoutés à côté du **général** onglet. Chaque onglet permet de configurer un accord X12 unidirectionnel.  
  
6.  Dans le **général** sous l’onglet dans le **propriétés générales** page, dans le **paramètres d’hôte communs** section, sélectionnez **activer le rapport d’état**, puis Sélectionnez **stocker la charge de message de création de rapports**.  
  
7.  Effectuer les tâches suivantes sur le **Fabrikam -> Contoso** onglet.  
  
    1.  Sur le **identificateurs** page sous le **paramètres de l’échange** section, entrez des valeurs pour les champs de qualificateur et identificateur (**ISA5**, **ISA6**, **ISA7**, et **ISA8**) qui correspondent aux valeurs de ces champs d’en-tête dans le message de test. Pour ce didacticiel, définissez **ISA5** à **ZZ**, **ISA6** à **7654321**, **ISA7** à **ZZ** , et **ISA8** à **1234567**.  
  
        > [!NOTE]
        >  Les champs de qualificateur et d'identificateur pour l'expéditeur et le récepteur permettent à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] de résoudre l'accord. Il compare les valeurs de **ISA5**, **ISA6**, **ISA7**, et **ISA8** dans l’en-tête d’échange à celles dans les propriétés d’un accord. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]sera également l’accord en comparant le qualificateur de l’expéditeur et l’identificateur (sans le qualificateur du récepteur et l’identificateur). Si [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ne peut pas résoudre l'accord, il utilise les propriétés d'accord de secours.  
  
    2.  Sur le **accusés de réception** page sous le **paramètres de l’échange** section, sélectionnez le **997 attendu** case à cocher.  
  
    3.  Sur le **Validation** page sous le **paramètres de l’échange** section, assurez-vous que **chercher isa13 en double** option est désactivée.  
  
        > [!NOTE]
        >  Effacer la **chercher isa13 en double** propriété vous permet de recevoir plusieurs instances du même message.  
  
    4.  Sur le **paramètres d’hôte Local** page sous le **paramètres de l’échange** section sous **paramètres du récepteur**, désactivez **pipeline d’envoi l’accusé de réception itinéraire port de réception requête-réponse**.  
  
        > [!NOTE]
        >  La désactivation de cette propriété permet d'envoyer l'accusé de réception 997 via un port d'envoi distinct, plutôt que de l'envoyer via le port d'envoi associé au port de réception bidirectionnel.  
  
8.  Effectuer les tâches suivantes sur le **Contoso -> Fabrikam** onglet.  
  
    1.  Sur le **identificateurs** page sous le **paramètres de l’échange** section, entrez des valeurs pour les champs de qualificateur et identificateur (**ISA5**, **ISA6**, **ISA7**, et **ISA8**) qui correspondent aux valeurs de ces champs d’en-tête dans le message de test.  Pour cette procédure pas à pas, définissez **ISA5** à **ZZ**, **ISA6** à **1234567**, **ISA7** à **ZZ** , et **ISA8** à **7654321**.  
  
    2.  Sur le **jeu de caractères et séparateurs** page sous le **paramètres de l’échange** section, pour **suffixe**, sélectionnez **CR LF**.  
  
    3.  Sur le **enveloppes** page sous le **paramètres des documents informatisés** section, procédez comme suit :  
  
        |Utiliser|Pour effectuer cette opération|  
        |--------------|----------------|  
        |**Default**|Sélectionnez **par défaut**. **Remarque :** lorsque vous sélectionnez cette ligne en tant que la valeur par défaut, les valeurs de **GS1**, **GS2**, **GS3**, **GS7**et **GS8** sont utilisées même si les valeurs de **Type de Transaction**, **Version/publication**, et **espace de noms cible** ne sont pas une correspondance pour le Message.|  
        |**Type de transaction**|Sélectionnez le type de message de votre message test, par exemple, **864 – Text Message**.|  
        |**Version/publication**|Entrez **00401**.|  
        |**Espace de noms cible**|Sélectionnez **http://schemas.microsoft.com/BizTalk/EDI/X12/2006**.|  
        |**GS1**|Vérifiez que le type de message du message de test est sélectionné, par exemple, **TX - Text Message (864)**.|  
        |**GS2**|Entrez **01**.|  
        |**GS3**|Entrez **7654321**.|  
        |**GS4**|Sélectionnez le format de date souhaité. Sélectionnez **SSAAMMJJ**. **Remarque :** vous devez sélectionner la valeur dans la liste déroulante, ne cliquez pas seulement dans le champ pour afficher la valeur par défaut. Si vous cliquez dans le champ sans sélectionner la valeur dans la liste déroulante, la valeur ne sera pas réellement sélectionnée.|  
        |**GS5**|Sélectionnez le format d'heure souhaité. Sélectionnez **HHMMSSdd**.|  
        |**GS7**|Sélectionnez **T - Transportation Data Coordinating Committee (TDCC)**.|  
        |**GS8**|Vérifiez que la version EDI a été entrée comme **00401**.|  
  
9. Cliquez sur **Appliquer**.  
  
10. Cliquez sur **OK**. Le nouvel accord ajouté est répertorié dans le **accords** section de la **tiers et profils d’entreprise** volet. Le nouvel accord ajouté est activé par défaut.  
  
11. Redémarrez le service BizTalk. Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la Console, sous **paramètres de plateforme**, cliquez sur **Instances d’hôte**, avec le bouton droit **BizTalkServerApplication**, puis cliquez sur  **Redémarrez**.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Tester la solution AS2, comme décrit dans [étape 11 : tester la Solution AS2](../core/step-11-test-the-as2-solution.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration des propriétés AS2](../core/configuring-as2-properties.md)   
 [Configuration des propriétés EDI](../core/configuring-edi-properties.md)