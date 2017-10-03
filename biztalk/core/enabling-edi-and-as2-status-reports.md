---
title: "L’activation des rapports d’état AS2 et EDI | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aa40fbad-51ad-40e0-9fe3-68e54beb11a5
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cef3d25040c253badd0f517326cc7830b6962df8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="enabling-edi-and-as2-status-reports"></a>Activation des rapports d'état EDI et AS2
Cette rubrique décrit comment configurer les rapports d’état EDI et AS2 dans le **vue d’ensemble du groupe** page de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration.  
  
 Les données de suivi des rapports d'état sont conservées dans la base des suivis BizTalk (BizTalkDTADb), conformément aux propriétés de stockage choisies dans les procédures ci-dessous. Vous pouvez configurer [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour activer les rapports d'état de chaque accord : Selon la quantité de données conservées, vous devrez régulièrement archiver les données depuis le magasin actif et, le cas échéant, les supprimer à terme du magasin d'archivage. Pour plus d’informations sur la gestion de la base de données BizTalkDTADb, consultez [l’archivage et la purge de la base de données de suivi BizTalk](../core/archiving-and-purging-the-biztalk-tracking-database.md).  
  
 Les rapports d'état peuvent être activés de trois manières différentes :  
  
-   Activez les rapports d'état pour les échanges EDI entrants ou sortants auxquels correspond un accord.  
  
-   Activez les rapports d'état pour les propriétés de l'accord EDI de secours, afin que les rapports d'état soient activés pour les échanges EDI pour lesquels [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] n'a pas pu trouver d'accord.  
  
-   Activez les rapports d'état pour les messages AS2.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez ouvrir une session en tant que membre du groupe Administrateurs de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou Opérateurs B2B de BizTalk Server.  
  
### <a name="to-enable-edi-status-reports-for-an-agreement"></a>Pour activer la création de rapports d'état EDI pour un accord  
  
1.  Dans le  **[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration** Console, cliquez sur le **Parties** nœud sous la [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)] et **groupe BizTalk** nœuds.  
  
2.  Dans le **tiers et profils d’entreprise** volet, cliquez sur le tiers qui a l’accord X12 ou EDIFACT pour lequel vous souhaitez activer le rapport d’état.  
  
3.  Dans le **accords** section, avec le bouton droit de l’accord pour lequel vous souhaitez activer le rapport d’état, puis cliquez sur **propriétés**.  
  
4.  Dans le **général** sous l’onglet du **paramètres d’hôte communs** , cliquez sur **activer la création de rapports**.  
  
    > [!NOTE]
    >  Cette étape inscrit les entrées de message dans l'interface de rapport d'état dans la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
5.  Sélectionnez **stocker les transactions/données utiles pour les rapports** pour stocker les documents des jeux dans les tables EDI de la base de données des suivis (BizTalk BizTalkDTADb).  
  
    > [!NOTE]
    >  Si vous activez le stockage des documents informatisés alors qu'une instance de l'orchestration de traitement par lot est activée, aucun document informatisé n'est stocké pour le lot en cours de création. En revanche, si vous désactivez le stockage des documents informatisés alors qu'une instance de l'orchestration de traitement par lot est activée, le stockage sera désactivé au milieu du traitement par lot.  
  
6.  Cliquez sur **OK**.  
  
7.  Redémarrez le service BizTalk (dans la boîte de dialogue Gestion de l'ordinateur). Si le pipeline AS2EdiReceive ou AS2EdiSend est utilisé dans votre solution, redémarrez le service d’administration IIS (à l’aide de la *iisreset* commande), ainsi que.  
  
    > [!NOTE]
    >  Le service BizTalk doit être redémarré après l'activation ou la désactivation de la création de rapports d'état EDI pour que la modification prenne effet. Si le pipeline AS2EdiReceive ou AS2EdiSend est utilisé dans votre solution, les services BizTalk et IIS doivent être redémarrés pour que la modification prenne effet. Notez que cela n'est pas nécessaire en cas d'activation de la création de rapports d'état AS2.  
  
### <a name="to-enable-edi-status-reports-for-fallback-agreements"></a>Pour activer la création de rapports d'état EDI pour les accords de secours  
  
1.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez **groupe BizTalk** avec le bouton droit de nœuds, **Parties**, puis sélectionnez **X12 paramètres de secours**ou **paramètres de secours EDIFACT**.  
  
    > [!NOTE]
    >  Lorsque vous configurez les rapports d'état dans les accords de secours, la configuration ne s'applique que lorsqu'aucun accord n'a été identifié pour un message.  
  
2.  Dans le **paramètres de secours** , cliquez sur **création de rapports EDI d’activer**.  
  
    > [!NOTE]
    >  Cette étape inscrit les entrées de message dans l'interface de rapport d'état dans la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
3.  Sélectionnez **stocker les transactions/données utiles pour les rapports** pour stocker les documents des jeux dans les tables EDI de la base de données des suivis (BizTalk BizTalkDTADb).  
  
    > [!NOTE]
    >  **Pour les messages encodés en EDIFACT**: Si vous sélectionnez cette propriété, vous devez également sélectionner une valeur pour le champ UNB3.2 (qualificateur du Code) dans la page Définition du Segment UNB de la boîte de dialogue Propriétés globales EDI. Cette propriété n’est pas définie par défaut, et l’échange sera suspendu si **stocker les transactions/données utiles pour les rapports** est sélectionnée, mais aucune valeur n’est pas sélectionnée pour UNB3.2.  
  
4.  Cliquez sur **OK**.  
  
### <a name="to-enable-as2-status-reports"></a>Pour activer les rapports d'état AS2  
  
1.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la Console, sous le [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)] et **groupe BizTalk** nœuds, cliquez sur le **Parties** nœud.  
  
2.  Dans le **tiers et profils d’entreprise** volet, cliquez sur le tiers qui a l’accord X12 ou EDIFACT pour lequel vous souhaitez activer le rapport d’état.  
  
3.  Dans le **accords** section, avec le bouton droit de l’accord pour lequel vous souhaitez activer le rapport d’état, puis cliquez sur **propriétés**.  
  
4.  Dans le **paramètres d’hôte communs** , cliquez sur **activer la création de rapports**.  
  
    > [!NOTE]
    >  Cette étape inscrit les entrées de message dans l'interface de rapport d'état dans la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
5.  Dans l’onglet d’accord unidirectionnel de la **propriétés de l’accord** boîte de dialogue, cliquez sur le **le suivi des messages du récepteur (NRR)** page.  
  
6.  Dans le **le suivi des messages du récepteur (NRR)** , cliquez sur **NRR activé pour les messages AS2 encodés entrants** pour permettre l’affichage du format câble des messages entrants.  
  
    > [!NOTE]
    >  Le format de transmission du message s’affichera lorsque vous cliquez sur le message dans le Message AS2 et la Page d’état MDN corrélé, puis cliquez sur **Message au Format câble**.  
  
    > [!NOTE]
    >  Le **activer la création de rapports** propriété doit être sélectionnée pour activer le stockage de données dans la base de données de non-répudiation. Si vous choisissez cette propriété, ou d'autres propriétés permettant de stocker des données dans la base de données de non-répudiation, une fenêtre contextuelle s'affiche pour vous inviter à activer la création de rapports AS2. Si vous cliquez sur **Oui**, création de rapports AS2 sera activée pour vous.  
  
7.  Dans le **le suivi des messages du récepteur (NRR)** , cliquez sur **NRR activé pour les messages AS2 décodés entrants** pour permettre l’affichage du format décodé des messages entrants.  
  
8.  Dans le **le suivi des messages du récepteur (NRR)** , cliquez sur **NRR activé pour les MDN sortants** pour permettre l’affichage des réponses MDN aux messages entrants.  
  
9. Dans l’onglet d’accord unidirectionnel de la **propriétés de l’accord** boîte de dialogue, cliquez sur le **de suivi des messages de l’expéditeur (NRR)** page.  
  
10. Dans le **de suivi des messages de l’expéditeur (NRR)** , cliquez sur **NRR activé pour les messages AS2 encodés sortants** pour permettre l’affichage du format câble des messages sortants.  
  
11. Dans le **de suivi des messages de l’expéditeur (NRR)** , cliquez sur **NRR activé pour les messages AS2 décodés sortants** pour permettre l’affichage du format décodé des messages sortants.  
  
12. Dans le **de suivi des messages de l’expéditeur (NRR)** , cliquez sur **NRR activé pour les MDN entrants** pour permettre l’affichage des réponses MDN aux messages sortants.  
  
13. Cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Surveillance des Solutions EDI et AS2](../core/monitoring-edi-and-as2-solutions.md)   
 [Configuration d’un EDI et le rapport d’état AS2](../core/configuring-an-edi-and-as2-status-report.md)   
 [EDI et AS2 le rapport d’état](../core/edi-and-as2-status-reporting.md)   