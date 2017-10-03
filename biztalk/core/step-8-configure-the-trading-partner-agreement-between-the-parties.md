---
title: "Étape 8 : Configurer l’accord de partenariat commercial entre les Parties | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9f532f85-3f09-4b60-b7bb-817ee3c79899
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 25e49bf5dcae7324fa3b68fe5080d094b4a2f603
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-8-configure-the-trading-partner-agreement-between-the-parties"></a>Étape 8 : Configurer l’accord de partenariat commercial entre les Parties
![Étape 8 9](../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-8of9.gif "Step_8of9")  
  
 Au cours de cette étape, vous allez configurer un accord de partenariat commercial X12 pour définir les paramètres de l’échange de messages X12 entre les partenaires commerciaux OrderSystem et Fabrikam.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez ouvrir une session en tant que membre du groupe Administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
### <a name="to-configure-an-agreement"></a>Pour configurer un accord  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur **Microsoft BizTalk Server**, puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration, cliquez sur **Parties** dans l’arborescence de la console, puis, dans le **tiers et profils d’entreprise** page, cliquez sur **Fabrikam_Profile**, pointez sur **nouveau**, puis cliquez sur **accord**.  
  
3.  Dans le **propriétés générales** page, pour le **nom** texte, entrez un nom pour l’accord.  
  
4.  À partir de la **protocole** la liste déroulante, sélectionnez **X12**.  
  
5.  Dans le **deuxième tiers** section, à partir de la **tiers** la liste déroulante, sélectionnez **OrderSystem**.  
  
6.  Dans le **deuxième tiers** section, à partir de la **Business** la liste déroulante, sélectionnez **OrderSystem_Profile**.  
  
     Vous remarquerez que les deux nouveaux onglets sont ajoutés à côté du **général** onglet. Chaque onglet sert à configurer un accord unidirectionnel, et chaque accord unidirectionnel constitue la transaction complète d'un message (en prenant également en compte les transferts du message et de l'accusé de réception).  
  
7.  Dans le **général** sous l’onglet dans le **propriétés générales** page, dans le **paramètres d’hôte communs** section, sélectionnez **activer le rapport d’état**, puis Sélectionnez **stocker la charge de message de création de rapports**.  
  
8.  Effectuer les tâches suivantes sur le **Fabrikam -> OrderSystem** onglet.  
  
    1.  Sur le **identificateurs** page sous le **paramètres de l’échange** section, entrez des valeurs pour les champs de qualificateur et identificateur (**ISA5**, **ISA6**, **ISA7**, et **ISA8**) qui correspondent aux valeurs de ces champs d’en-tête dans le message de test.  
  
        |Utiliser|Pour effectuer cette opération|  
        |--------------|----------------|  
        |**Qualificateur de l’expéditeur (ISA5)**|Sélectionnez **ZZ - défini mutuellement**.|  
        |**Identificateur de l’expéditeur (ISA6)**|Entrez **THEM**.|  
        |**Qualificateur du récepteur (ISA7)**|Sélectionnez **ZZ - défini mutuellement**.|  
        |**Identificateur du récepteur (ISA8)**|Entrez **US**.|  
  
        > [!NOTE]
        >  Les champs de qualificateur et d'identificateur pour l'expéditeur et le récepteur permettent à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] de résoudre l'accord. Il compare les valeurs de **ISA5**, **ISA6**, **ISA7**, et **ISA8** dans l’en-tête d’échange à celles dans les propriétés d’un accord. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]sera également l’accord en comparant le qualificateur de l’expéditeur et l’identificateur (sans le qualificateur du récepteur et l’identificateur). Si [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ne peut pas résoudre l'accord, il utilise les propriétés d'accord de secours.  
  
    2.  Sur le **accusés de réception** sous le **paramètres de l’échange** , cliquez sur **997 attendu**. Activer cette case à cocher indique au pipeline de réception de générer un accusé de réception 997 lorsqu'il reçoit l'échange 850.  
  
    3.  Sur le **Validation** page sous le **paramètres de l’échange** section, assurez-vous que **numéro de contrôle de l’échange (vérifier les doublons ISA13)** option est désactivée.  
  
        > [!NOTE]
        >  Effacer la **chercher isa13 en double** propriété vous permet de recevoir plusieurs instances du même message.  
  
    4.  Sur le **paramètres d’hôte Local** sous le **paramètres de l’échange** section, désactivez **port de réception de l’accusé de réception itinéraire un pipeline d’envoi de requête-réponse**.  
  
        > [!NOTE]
        >  Effacer la **l’accusé de réception itinéraire** propriété est obligatoire, car cela permet de renvoyer un accusé de réception asynchrone via un distinct port d’envoi, plutôt que d’un accusé de réception synchrone via le port d’envoi associé à un double port de réception.  
  
    5.  Sur le **paramètres d’hôte Local** page sous le **paramètres des documents informatisés** , sélectionnez l’espace de noms pour le schéma à utiliser pour traiter l’échange entrant.  
  
        |Utiliser|Pour effectuer cette opération|  
        |--------------|----------------|  
        |**Default**|Activez la case à cocher dans la colonne.|  
        |**Pour ST1**|Sélectionnez **850 - bon de commande**.|  
        |**GS2**|Entrez **THEM**.|  
        |**Cible Namespace**|Sélectionnez **http://schemas.microsoft.com/BizTalk/EDI/X12/2006**.|  
  
        > [!NOTE]
        >  La définition des propriétés permet à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] d'identifier le schéma à utiliser pour le traitement de l'échange 850 entrant. Si les valeurs GS02 et ST01 d'un échange sont entrées dans une ligne de la grille, l'espace de noms cible dans la même ligne sert à déterminer le schéma à utiliser.  
  
9. Effectuer les tâches suivantes sur le **OrderSystem -> Fabrikam** onglet.  
  
    1.  Sur le **identificateurs** page sous le **paramètres de l’échange** section, entrez des valeurs pour les champs de qualificateur et identificateur (**ISA5**, **ISA6**, **ISA7**, et **ISA8**) qui correspondent aux valeurs de ces champs d’en-tête dans le message de test.  
  
        |Utiliser|Pour effectuer cette opération|  
        |--------------|----------------|  
        |**Qualificateur de l’expéditeur (ISA5)**|Sélectionnez **ZZ - défini mutuellement**.|  
        |**Identificateur de l’expéditeur (ISA6)**|Entrez **US**.|  
        |**Qualificateur du récepteur (ISA7)**|Sélectionnez **ZZ - défini mutuellement**.|  
        |**Identificateur du récepteur (ISA8)**|Entrez **THEM**.|  
  
    2.  Sur le **jeu de caractères et séparateurs** sous le **paramètres de l’échange** section, sélectionnez **CR LF** pour le **suffixe** propriété.  
  
    3.  Sur le **Ports d’envoi** page sous le **paramètres de l’échange** section, associez le port d’envoi qui envoie l’accusé de réception à Fabrikam. Dans le **ports d’envoi** grille, sous la **nom** colonne, cliquez sur une cellule vide et dans la liste déroulante, sélectionnez le port d’envoi (**toTHEM_997**) créé pour envoyer le 997 accusé de réception à Fabrikam.  
  
    4.  Sur le **enveloppes** page sous le **paramètres des documents informatisés** section, entrez des valeurs pour toutes les colonnes dans la première ligne de la grille.  
  
        |Utiliser|Pour effectuer cette opération|  
        |--------------|----------------|  
        |**Default**|Activez la case à cocher dans la **par défaut** colonne. **Remarque :** lorsque vous sélectionnez cette ligne en tant que la valeur par défaut, les valeurs de **GS1**, **GS2**, **GS3**, **GS7**et **GS8** sont utilisées même si les valeurs de **Type de Transaction**, **Version/publication**, et **espace de noms cible** ne sont pas une correspondance pour le Message.|  
        |**Type de transaction**|Sélectionnez le type de message de votre message test, **850 - bon de commande**.|  
        |**Version/publication**|Entrez la version EDI, **00401**.|  
        |**Espace de noms cible**|Sélectionnez **http://schemas.microsoft.com/Edi/X12**.|  
        |**GS1**|Vérifiez que **PO - bon de commande (850)** est sélectionnée.|  
        |**GS2**|Entrez **1234567**.<br /><br /> **ID d’Application expéditrice.**|  
        |**GS3**|Entrez **0000000**.<br /><br /> **ID d’Application destinataire.**|  
        |**GS4**|Sélectionnez **SSAAMMJJ**. **Remarque :** vous devez sélectionner la valeur dans la liste déroulante, ne cliquez pas seulement dans le champ pour afficher la valeur par défaut. Si vous cliquez dans le champ sans sélectionner la valeur dans la liste déroulante, la valeur ne sera pas réellement sélectionnée.|  
        |**GS5**|Sélectionnez **HHMM**.|  
        |**GS7**|Sélectionnez **X - Accredited Standards Committee X12**.|  
        |**GS8**|Vérifiez que **00401** a été entré.|  
  
        > [!NOTE]
        >  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]effet de définir les valeurs de GS01, GS02, GS03, GS04, GS05, GS07 et GS08 des accusés de réception sortants selon les valeurs entrées pour **Type de Transaction**, **Version/publication**, et **cible espace de noms**. Le pipeline d'envoi tente de faire correspondre le type de transaction, la version X12 et l'espace de noms cible avec les valeurs correspondantes dans l'en-tête du message. Si réussie, elle utilise les valeurs GS associées le **Type de Transaction**, **Version/publication**, et **espace de noms cible** valeurs.  
  
10. Cliquez sur **Appliquer**.  
  
11. Cliquez sur **OK**. Le nouvel accord ajouté est répertorié dans le **accords** section de la **tiers et profils d’entreprise** volet. Le nouvel accord ajouté est activé par défaut.  
  
12. Redémarrez le service BizTalk. Dans la Console Administration de BizTalk Server, sous **paramètres de plateforme**, cliquez sur **Instances d’hôte**, avec le bouton droit **BizTalkServerApplication**, puis cliquez sur  **Redémarrez**.  
  
    > [!NOTE]
    >  Le service BizTalk doit être redémarré après l'activation ou la désactivation de la création de rapports d'état EDI pour que la modification prenne effet.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Tester la solution EDI, comme décrit dans [étape 9 : tester la Solution EDI](../core/step-9-test-the-edi-solution.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration des propriétés d’accord encodage](../core/configuring-encoding-agreement-properties.md)