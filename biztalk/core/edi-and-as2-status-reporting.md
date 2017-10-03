---
title: "EDI et AS2 le rapport d’état | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a9e58b29-9be0-41d6-ad35-1aae28e1a784
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 31b08fd8222cee0cb0f04750eedcb32d06c28820
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="edi-and-as2-status-reporting"></a>Rapport d'état EDI et AS2
Le rapport d'état EDI permet au personnel de back-office de suivre l'état des transmissions EDI et AS2. S'ils sont activés, les rapports d'état fournissent l'état complet d'une transaction d'échange de documents, notamment l'échange et les accusés de réception corrélés à l'échange. Ces rapports fournissent des données sur la réception, la validation, le traitement par lot et le traitement des accusés de réception des messages EDI et AS2.  
  
 Vous pouvez les utiliser pour obtenir l'état des échanges en attente et sans accusé de réception, des échanges complets, des scénarios d'erreur ou des scénarios d'application professionnelle. Ces rapports permettent d'effectuer les tâches suivantes :  
  
-   Confirmer la réception des échanges.  
  
-   Répertorier les échanges sortants en attente d'accusé de réception.  
  
-   Répertorier les échanges rejetés reçus.  
  
-   Répertorier les échanges sortants signalés comme étant rejetés ou partiellement acceptés.  
  
 Les données incluses dans les rapports d'état sont obtenues à partir des segments de contrôle de l'échange, tels que ISA, TA1, GS, UNB et UNG (à l'exception de l'état de l'accusé de réception fonctionnel).  
  
 **Interface utilisateur de rapport État**  
  
 Les rapports d'état EDI et AS2 sont disponibles dans la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. À partir de la **Hub du groupe** page de la **groupe BizTalk** nœud, vous avez des liens vers échange EDI et état de l’accusé de réception corrélé, état du lot et message AS2 et état MDN corrélé. Chacun de ces rapports fournit une plage de paramètres d'état que vous pouvez inclure ou exclure d'une requête d'expression, ce qui vous permet de créer le rapport d'état nécessaire.  
  
 Outre l'affichage de l'état d'un échange EDI, vous pouvez aussi consulter les documents informatisés contenus dans un échange. Pour cela, activez le stockage des charges de message dans les tables EDI de la base de données des suivis BizTalk (BizTalkDTADb). Pour afficher les documents informatisés, utilisez la commande Afficher les détails dans l'interface utilisateur de rapport d'état.  
  
 Vous pouvez aussi stocker les messages AS2 entrants ou sortants ou les messages MDN dans la base de données de non-répudiation. Pour afficher les documents informatisés ou les messages AS2, cliquez avec le bouton droit sur un message dans le rapport d'état, puis cliquez sur la commande appropriée.  
  
 **Composants de rapport d’état**  
  
 Les composants [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] impliqués dans le rapport d'état sont les suivants :  
  
-   le Désassembleur EDI dans le pipeline de réception EDI qui crée et met à jour les entrées d'état dans la banque de données pour un échange entrant ;  
  
-   l'Assembleur EDI dans le pipeline d'envoi EDI qui crée et met à jour les entrées d'état dans la banque de données pour un échange sortant ;  
  
-   les banques de données qui stockent les entrées du rapport d'état. Il s'agit de la base de données d'importation principale BAM pour les données de suivi et de la table Contenu du message EDI de la base de données des suivis BizTalk (BizTalkDTADb) pour les documents informatisés et/ou le contenu des messages AS2 ;  
  
-   État de l’interface utilisateur de création de rapports sur le **Hub du groupe** page de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration, qui est utilisé pour afficher les données du rapport d’état  
  
-   les options de propriété d'accord et d'accord de secours dans la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], qui permettent d'activer et de configurer le rapport d'état ;  
  
-   DTA et SQL Analysis Server qui exploitent l'infrastructure BAM.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Configuration d’EDI et AS2 le rapport d’état](../core/configuration-of-edi-and-as2-status-reporting.md)  
  
-   [Types de rapports d’état AS2 et EDI](../core/types-of-edi-and-as2-status-reports.md)  
  
-   [Données stockées pour les rapports d’état AS2 et EDI](../core/data-stored-for-edi-and-as2-status-reports.md)  
  
-   [Stockage des données pour les rapports d’état AS2 et EDI](../core/how-data-is-stored-for-edi-and-as2-status-reports.md)