---
title: Traitement des fichiers plats BTAHL72X | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ACKs
- 2.X messages, disassembler
- property promotion, MSH-header schemas
- disassembler, validating messages
- HL7, errors
- 2.X messages, validating headers
- acknowledgements, generating
- assembler, validating messages
- messages, multi-part messages
- property promotion, property schemas
- generating aknowledgements
- messages, 2.X messages
- schemas, MSH-header schemas
- 2.X messages, validating message bodies
- 2.X messages
- schemas, property schemas
- message modes, 2.X messages
- errors, HL7 error format
- flat files
- validating, messages
- schemas, property promotion
- headers, validating
- 2.X messages, message modes
- 2.X messages, header validation
- 2.X messages, parsing flat files
ms.assetid: c92e2f70-0bfa-4bc8-8044-4a6e62cabee3
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b15d21653b9f0d6109487677484506c7a5d6bcc2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="btahl72x-flat-file-processing"></a>Traitement des fichiers plats BTAHL72X
Les composants suivants dans [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) processus HL7 2.X (HL7 messages codés au format) :  
  
-   Pipelines et les bibliothèques principales : [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]. PipelineCommon.dll et [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]. PipelineMessageCore.dll  
  
-   Bibliothèques d’assembleur et désassembleur : [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]. HL72fAsm.dll et [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]. HL72fDAsm.dll  
  
-   Adaptateur d’envoi de la bibliothèque de validation d’accusé de réception (ACK) utilisée pour le MLLP bidirectionnelle : [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]. HL7ACKHelper.dll  
  
## <a name="hl7-message-modes"></a>HL7 Modes de Message  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]prend en charge les modes de message suivants pour les messages 2.X :  
  
-   Mode éditeur-abonné (pub-sub)  
  
     Le serveur de publication diffuse à un tiers d’abonnés, comme déclaratives ou une non sollicité mise à jour. [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]et [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] fournissent une grande souplesse pour ce mode, étant donné que vous pouvez gérer les abonnements et les parties après le moment du design.  
  
-   Mode de requête-réponse  
  
     Un échange de messages interrogative ou d’une requête dans lequel une demande spécifique à partir d’une entité spécifique génère un message de répond.  
  
## <a name="flat-file-parsing"></a>Analyse de fichier plat  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]messages à parties multiples 2.X analyse HL7 en trois parties :  
  
-   Partie d’en-tête-MSH  
  
-   Partie du corps  
  
-   Partie de Z  
  
## <a name="hl7-header-validation"></a>HL7 Validation de l’en-tête  
 Le HL7 désassembleur et assembleur effectuent une validation structurelle et schématique de l’en-tête d’un message 2.X, afin de vérifier qu’il peut traiter le message. [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]base de la validation de schéma sur le schéma d’en-tête commun, MSH_25_GLO_DEF.  
  
 Par exemple, l’analyseur détermine que les champs MSH1 et où MSH2 a été sont bien formés. MSH1 doit avoir qu’un seul caractère. Où MSH2 a été doit être comprise entre deux et quatre caractères, et aucun caractère ne peut se répéter.  
  
## <a name="hl7-body-validation"></a>HL7 Validation du corps  
 Le HL7 désassembleur et assembleur effectuent une validation structurelle de base du corps d’un message 2.X et la validation de schéma, si vous l’activez.  
  
 La validation structurelle de base du corps, lequel [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] toujours effectue, consiste à vérifier les éléments suivants :  
  
-   Qu’il n’y a trois caractères dans des segments  
  
-   Que le délimiteur de segment est \<CR > ou \<CR >\<LF > (facultatif pour le dernier segment)  
  
-   Conviennent de séparateurs de champs  
  
-   Qu’il n’y a aucun segment déclaré (avec une balise de segment de trois caractères défini) dans un segment Z non déclaré  
  
 Validation de schéma plus étendue du corps inclut les éléments suivants :  
  
-   Délimiteurs de fin de champ  
  
     Dans le segment d’en-tête-MSH et segments de corps  
  
-   Segment de Z  
  
-   Type de données pris en charge XSD et personnalisées  
  
     XSD prises en charge et les types de non XSD (TS (date), DT (date), TM (heure) et TN (numéro de téléphone)  
  
-   Énumérations  
  
     ID (tables définies par l’HL7) et IS (tables définies par l’utilisateur)  
  
-   Caractère facultatif  
  
     Obligatoires et facultatifs  
  
-   Répétition  
  
     Segment et champ  
  
-   Séquences d’échappement  
  
     Encodage de caractères, la mise en forme et les jeux de caractères  
  
 Pour activer ou désactiver la validation de schéma pour tous les messages reçus ou envoyés à un tiers spécifique (tiers de source pour le désassembleur, tiers de destination de l’assembleur). [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]schémas 2.X utilise le HL7 directement pour ce traitement, comme déterminé par le champ d’en-tête de message-structure MSH9.3, le champ ID de Version MSH12 (2.3.1, 2.4 ou 2.5) et l’espace de noms définissant dans [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] l’Explorateur de Configuration.  
  
## <a name="hl7-disassembler-processing"></a>HL7 Le traitement du désassembleur  
 Le désassembleur HL7 analyse les messages entrants HL7 en segments XML pour le traitement. Comme il traite les messages, le désassembleur effectue les tâches suivantes :  
  
-   Gère les séquences d’échappement  
  
-   Gère les vérifications des propriétés obligatoire ou facultatif  
  
-   Handles défini des segments et des segments Z indéfinis ou inattendus (pour obtenir une description des segments de Z, consultez [personnalisation des Messages via des objets de Z](../../adapters-and-accelerators/accelerator-hl7/customizing-messages-through-z-objects.md)).  
  
-   Ignore les segments inattendues à la fin d’une instance (qui deviennent des segments Z non déclarés)  
  
## <a name="error-reporting"></a>Rapport d'erreurs  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]signale la plupart des erreurs dans le format d’erreur HL7 standard, notamment le code de segment, séquence, champ et d’erreur. Toutefois, la condition d’erreur peut être que tous ces éléments soient disponibles, par exemple, si aucun schéma n’est présent. Pour gérer cet cas, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] peuvent signaler les erreurs dans un autre [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] format d’erreur. Le segment dans un message d’erreur comprend deux parties : un pour l’erreur HL7 et un pour l’autre [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] erreur.  
  
## <a name="ack-generation"></a>Génération de l’accusé de réception  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]prend en charge les types d’accusés de réception (ACK) suivants pour les messages 2.X. Les deux le type d’erreur HL7 et [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] type d’erreur (secondaire) sont utilisées :  
  
-   Mappage du message d’origine et de l’accusé de réception  
  
-   Accusés de réception d’origine HL7  
  
-   HL7 améliorée des accusés de réception  
  
     Validation acceptent et Application  
  
-   Statique/proxy l’accusé de réception  
  
     L’accusé de réception ou NAK  
  
## <a name="property-promotion"></a>Promotion des propriétés  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]prend en charge la promotion des propriétés 2.X suivantes :  
  
-   Schéma de propriété  
  
-   Schéma d’en-tête de MSH  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Détermination du schéma dans le désassembleur 2.X HL7](../../adapters-and-accelerators/accelerator-hl7/schema-determination-in-the-hl7-2-x-disassembler.md)  
  
-   [Détermination du schéma dans l’assembleur 2.X HL7](../../adapters-and-accelerators/accelerator-hl7/schema-determination-in-the-hl7-2-x-assembler.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Traitement des messages](../../adapters-and-accelerators/accelerator-hl7/message-processing.md)   
 [Le traitement des Messages HL7](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md)   
 [L’utilisation des schémas 2.X HL7](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md)