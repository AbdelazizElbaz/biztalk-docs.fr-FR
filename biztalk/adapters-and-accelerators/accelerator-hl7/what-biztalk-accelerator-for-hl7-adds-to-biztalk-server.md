---
title: "BizTalk Accelerator pour HL7 ajoutée à BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- batching, documents
- BTAHL7, batching
- messages, acknowledgements
- messages, auditing
- Configuration Explorer
- BTAHL7, message validation
- BTAHL7, Configuration Explorer
- messages, processing
- BTAHL7, BizTalk Server
- BTAHL7, message processing
- auditing, messages
- BTAHL7, auditing
- validating, messages
- acknowledgements, messages
- BTAHL7, logging
- BizTalk Server, BTAHL7
- messages, validating
- logging
- BTAHL7, acknowledgements
- errors, logging
ms.assetid: 862e9f26-588a-4e91-8ebc-f53aab6f46c2
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7b9e9d1277c5d037a42fd85ca48ec13c8f1893a3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="what-biztalk-accelerator-for-hl7-adds-to-biztalk-server"></a>BizTalk Accelerator pour HL7 ajoutée à BizTalk Server
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) génère un [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] système d’intégration dans un système de soins de santé d’intégration. Il ajoute des fonctionnalités qui nécessitent des organisations de soins de santé.  
  
 Vous installez [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] sur [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]. [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]Ajoute des fonctionnalités dans le noyau [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] moteur. Il ajoute des fonctionnalités, outils et utilitaires à celles qui [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] fournit. Il ajoute également les interfaces de programmation d’applications (API) à ce que le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] SDK fournit.  
  
## <a name="btahl72x-message-processing"></a>Traitement des messages BTAHL72X  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]Ajoute un nombre de fonctionnalités et outils qui permettent le système pour traiter les messages HL7 en mode natif, sans nécessiter de personnalisation. [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]inclut toutes les spécifications de document, les applications et les composants dont vous avez besoin pour développer et déployer pour traiter les transactions de la plage complète de HL7-spécifiques. [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]prend en charge [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]2 X schémas de fichier plat. Les éléments suivants [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] composants effectuent [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]2 X le traitement du message :  
  
-   HL7 désassembleur et assembleur qui permettent au système analyser et sérialiser les messages HL7 en mode natif. Le désassembleur et assembleur font partie de la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] pipeline, qui effectue une série d’étapes de traitement sur les messages, y compris la conversion vers ou à partir de XML, le décodage ou d’encodage et la validation du message.  
  
-   Une carte de protocole de couche inférieure minimale (MLLP) qui permet au système de réception ou envoi de messages en fonction de HL7, lequel [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] généralement transports en utilisant le protocole MLLP. L’adaptateur MLLP garantit que [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] et [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] sont interopérables avec les applications de messagerie HL7.  
  
-   Schémas de message HL7 qui permettent au système recevoir des messages encodés HL7.  
  
## <a name="btahl72xml-message-processing"></a>Traitement des messages BTAHL72XML  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]Ajoute un nombre de fonctionnalités et des outils qui permettent au système pour traiter les messages XML. [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]Convertit les messages HL7 au format XML afin d’activer [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], qui utilise XML en interne pour effectuer des opérations sur les messages. [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]effectue la conversion en XML uniquement pour HL7 V2. Messages de X, car ils sont en mode natif dans le format de fichier plat. Il n’effectue pas la conversion des messages XML 2, qui sont au format XML. [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]analyse et valide ces messages sans conversion.  
  
 Les schémas de message XML pris en charge sont les [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]2XML les schémas générés par l’organisation HL7 pour le V2 HL7. Version XML et le [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]des schémas X 2 utilisés pour HL7 V2. Messages de la version X (au format de fichier plat). [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]inclut les spécifications de document, les applications et les composants dont vous avez besoin pour développer et déployer pour le traitement de la gamme complète des [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]2XML transactions. Les éléments suivants [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] composants effectuent [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]2XML le traitement des messages :  
  
-   Désassembleur XML et assembleur qui permettent au système analyser et sérialiser les messages XML qui correspondent aux messages de HL7. Le désassembleur XML et assembleur des améliorations au-delà de la fonctionnalité de le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] XML désassembleur et assembleur, y compris la validation automatique-accusé de réception et le message.  
  
-   Schémas HL7 compatible XML qui permettent au système recevoir des messages de HL7 (les deux V2. X et V2. Messages XML). Le système convertit V2. X les messages dans les messages XML (V2. Les messages XML sont déjà au format XML), puis les envoie à un autre système qui prend en charge de XML. De même, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] peut recevoir les messages XML et les convertir en HL7 pour l’envoi. [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]transforme les données de HL7 spécifiques depuis ou vers un autre format à l’aide des spécifications de document basé sur XML, ainsi que l’Analyseur de HL7, cartes et d’autres [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] outils qui appellent les schémas et mappages. Par exemple, vous pouvez recevoir un échange dans un format standard HL7 2.0 ou 2.5 et transformer dans un autre format une application médicale existante peut utiliser.  
  
## <a name="validation"></a>Validation  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]effectue une validation de HL7 V2. Les messages X [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] ne peut pas effectuer. [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]effectue automatiquement une validation syntaxique et schématique de l’en-tête d’un message HL7 et effectue automatiquement une validation structurelle du corps d’un message HL7. [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]exécute la validation de schéma du corps d’un message HL7, si vous activez cette fonctionnalité (voir [les paramètres de Validation](../../adapters-and-accelerators/accelerator-hl7/validation-settings.md)).  
  
 La validation du corps d’un message codé HL7 inclut le schéma, format de données, des en-tête de champs et des valeurs d’énumération. La validation des messages XML de 2 inclut la validation par rapport à leur schéma, qui est la validation XML standard. Pour plus d’informations, consultez [traitement de fichier plat BTAHL72X](../../adapters-and-accelerators/accelerator-hl7/btahl72x-flat-file-processing.md) et [BTAHL72XML traitement](../../adapters-and-accelerators/accelerator-hl7/btahl72xml-processing.md).  
  
## <a name="auto-acknowledgment"></a>Accusé de réception automatique  
 Pour garantir la fiabilité du système de messagerie, vous pouvez souhaiter nécessitent des messages d’accusés de réception (ACK) à HL7 que [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] génère automatiquement en fonction des paramètres de configuration.  
  
 Accusés de réception d’origine en mode confirmer la validation de l’en-tête de message et le corps. En mode étendu, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] génère deux types d’accusés de réception : un accusé de réception envoyé sur la validation de l’en-tête d’acceptation et une application de l’accusé de réception envoyé sur la validation de la totalité du message. [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]génère un accusé de réception différé par l’application métier-qui reçoit un message à partir de [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].  
  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]facilite le traitement d’accusé de réception prenant en charge les transports de messages bidirectionnel.  
  
## <a name="batching"></a>Traitement par lot  
 Vous pouvez traiter des documents en mode batch, ce qui permet une charge de traitement. Vous pouvez également traiter par lots les réponses à ces lots. [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]Permet d’effectuer trois types de traitement par lot pour HL7 2.X messages :  
  
-   Trafic entrant de traitement par lot, dans lequel le système reçoit des messages en tant que lot, puis les fragments en messages individuels.  
  
-   Traitement par lots dans / out, du lot dans lequel le système reçoit et envoie des messages en tant que lot.  
  
-   Créer un traitement par lots, dans lequel le système envoie un lot de messages reçus en tant que messages individuels.  
  
    > [!NOTE]
    >  [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]ne fournit pas de fonctionnalités de traitement par lot pour V2. Messages XML.  
  
## <a name="logging"></a>Journalisation  
 Pour améliorer la résolution des problèmes, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] permet la création de rapports d’erreurs ou avertissements signalés par les composants du système. Vous pouvez filtrer ces événements, les stocker dans un des trois magasins de journal ([!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] journal des événements, WMI, ou un [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] magasin de journaux), ou bien les personnaliser à l’aide de la [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Kit de développement logiciel.  
  
## <a name="configuration-explorer"></a>Explorateur de configuration  
 Vous pouvez configurer [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] parties, les lots, les accusés de réception et les stocker dans le journal des [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] l’Explorateur de Configuration, un outil d’administration ajouté pour les outils qui [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] fournit. Cet outil vous permet également à lancer au niveau du tiers de traitement par lots. Le [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] SDK vous permet de personnaliser ces paramètres par programmation.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment BizTalk Server résout les besoins de l’entreprise](../../adapters-and-accelerators/accelerator-hl7/how-biztalk-server-solves-the-business-need2.md)