---
title: Comment BTAHL7 route les Messages | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- routing, about routing
- routing, messages
- messages, routing
- BTAHL7, message routing
ms.assetid: 555696c7-6023-44eb-b13d-cf7527bbc92f
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 61dd223a014ae8ea7de35d8d73f1a7cf7ef35449
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-btahl7-routes-messages"></a>Comment BTAHL7 route les Messages
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) s’appuie sur les fonctionnalités de traitement des messages [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], mais il permet également d’étendre de plusieurs façons qui sont spécifiques à la configuration requise de la messagerie de HL7.  

## <a name="routing-overview"></a>Vue d’ensemble du routage

HL7 reçoit des messages à partir d’un système métier (LOB) et peut s’afficher à l’aide de l’adaptateur MLLP. Le système métier se connecte à l’adaptateur MLLP sur [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] via un port TCP, puis envoie des messages à l’adaptateur MLLP.

Dans  **[!INCLUDE[bts2013r2_md](../../includes/bts2013r2-md.md)] et les versions antérieures**, le MLLP HL7 recevoir l’adaptateur de transport attend le système métier à distance pour se connecter à MLLP. Une fois que le système métier à distance se connecte, le système métier envoie les messages à l’aide de MLLP à la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]. Plus précisément : 

1. Le système LOB distant se connecte à l’adaptateur MLLP local [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] à l’aide d’un port TCP 
2. Le BTA4HL7 emplacement de réception avec l’adaptateur MLLP accepte la connexion 
3. Le système métier à distance offre un ou plusieurs messages 
4. Le système métier à distance se déconnecte.

Dans  **[!INCLUDE[bts2016_md](../../includes/bts2016-md.md)] et les versions plus récentes**, la connexion au système métier est lancée par l’adaptateur MLLP et recevoir les messages de push système LOB à la MLLP. En d’autres termes, le système métier à distance attend que la connexion avant d’envoyer des messagings à MLLP. Plus précisément : 

1. Local [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] se connecte au système métier à distance à l’aide d’un port TCP 
2. Le BTA4HL7 emplacement de réception avec MLLP adaptateur lance la connexion 
3. Le système métier à distance offre un ou plusieurs messages 
4. Le système métier à distance se déconnecte. 

Pour la compatibilité descendante, vous pouvez utiliser le comportement par défaut d’origine en où le système métier à distance établit les connexions. Cette option est configurable dans le MLLP propriétés de l’emplacement de réception. 
 
Une fois le message HL7 est reçu, il est ensuite soumis à une HL7 pipeline de réception. Dans ce pipeline, le désassembleur HL7 analysera le message et permet de valider le message en fonction de la configuration de définition et la validation de schéma approprié. À ce stade, un message d’accusé de réception peut être de HL7 généré (succès ou erreur), en fonction de la validité du message et la configuration de l’accusé de réception approprié. À ce stade, le pipeline envoie l’instance de message et un accusé de réception facultatif pour la base de données MessageBox pour traitement ultérieur et de routage.  
  
 Une fois qu’une instance de message arrive dans la base de données MessageBox, [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] vérifie par filtrage les abonnements et achemine le message vers un ou plusieurs ports d’envoi (éventuellement les ports MLLP) via un pipeline d’envoi HL7. Le pipeline d’envoi peut valider les instances de message en fonction de la configuration de définition et la validation de schéma approprié. En plus de la validation, il est possible de remplacer certaines valeurs de champ dans le segment MSH du message sortant. Cette possibilité de remplacement est particulièrement utile si plusieurs ports sont abonnés à un message et que chaque application de réception a attentes uniques au sein des valeurs de segment MSH.  
  
 Bien entendu, toutes les autres [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] d’envoi et de port de réception fonctionnalités seront disponibles pour les messages HL7, ainsi que certaines des fonctionnalités qui peuvent être uniques pour le type de port sélectionné, telles que les paramètres de port d’envoi MLLP. Un exemple de la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] fonctionnalités serait la possibilité d’appliquer un mappage de transformation à un message sortant.  
  
## <a name="how-routing-works"></a>Fonctionnement du routage

Le [!INCLUDE[btaBTAHL7NoNumber_md](../../includes/btabtahl7nonumber-md.md)] itinéraires HL7 message instances en fonction des abonnements qui gère de la base de données MessageBox. Ces abonnements utilisent des filtres que vous définissez pour chaque port d’envoi. Exemple de filtre peut inclure le routage basé sur type de message ID et/ou HL7 port de réception (ADT ^ A03, par exemple) et/ou en envoyant l’application (valeur MSH3.1).  
  
 En plus de définir [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] abonnements, vous devez effectuer une configuration de messagerie HL7 spécifiques qui affecte les instances de message HL7 comme [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] les route. Cette configuration supplémentaire vous permet d’appliquer des règles de validation HL7 uniques, la génération automatique des accusés de réception et la possibilité de remplacer les valeurs MSH. [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]s’applique cette configuration au niveau du tiers. Vous devez définir les parties de l’Explorateur BizTalk et effectuer la configuration HL7 connexe dans [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] l’Explorateur de Configuration.  
  
 Pour appliquer HL7 messagerie configuration unique (par exemple, la validation ou les remplacements MSH) à plusieurs ports d’envoi qui s’abonnent à un message, vous devez créer des associations entre les parties et les ports d’envoi. Vous configurez les associations de port de tiers à envoyer en tant que propriétés de tiers dans l’Explorateur BizTalk.  
  
 Si vous ne pas devez router HL7 vers plusieurs ports d’envoi des messages, ou appliquer une configuration de traitement HL7 unique à plusieurs ports d’envoi, vous pouvez éliminer l’étape d’association des parties avec les ports d’envoi. Dans ce cas, [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] associe la partie de sa configuration de messagerie HL7 via le champ d’application réceptrice dans le message HL7 (MSH 3.1). Cette situation est susceptible de se produire dans un interrogative HL7 (requête/réponse) exchange du message.  
  
## <a name="see-also"></a>Voir aussi  
 [Validation de message](../../adapters-and-accelerators/accelerator-hl7/message-validation.md)