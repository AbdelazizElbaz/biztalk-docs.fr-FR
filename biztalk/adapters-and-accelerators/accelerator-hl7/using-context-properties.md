---
title: "À l’aide des propriétés de contexte | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, context properties
- messages, promoted properties
- promoted properties, context properties
- context properties, messages
ms.assetid: 306127a9-df03-4aaf-8dd8-76df51eb193d
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3a3fad82b8d537fcc017dfed175c5348cc1529d3
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="using-context-properties"></a>À l’aide des propriétés de contexte
BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) moteur de messagerie et de ses composants utilisent en interne les propriétés de contexte. Modification des valeurs définies par le moteur pour certaines propriétés de contexte est déconseillée, car elle peut affecter la logique d’exécution du moteur. Toutefois, vous pouvez modifier un grand nombre de propriétés non définies par le moteur. Vous pouvez utiliser les propriétés de contexte pour la création d’expressions de filtre sur les ports d’envoi (pour plus d’informations, consultez [définition d’Expressions de filtre sur les Ports d’envoi](../../adapters-and-accelerators/accelerator-hl7/setting-filter-expressions-on-send-ports.md)). Vous pouvez également utiliser des propriétés de contexte dans les expressions de filtre pour les orchestrations. Les propriétés sont disponibles pour les expressions de filtre tant qu’un projet a une référence aux schémas de propriétés globales (qui [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] crée lorsque vous utilisez un des modèles courants).  
  
 Le tableau suivant contient une liste de [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] que le moteur de messagerie utilise les propriétés de contexte de message. Le moteur utilise beaucoup de ces propriétés pour le routage. Le sérialiseur utilise d’autres personnes pour son traitement. Ces propriétés ont un préfixe de [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)].  
  
 Pour plus d’informations sur [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] des propriétés de contexte (celles identifié dans les expressions de filtre par un préfixe de BizTalk Server), consultez « Propriétés de contexte de Message » dans l’aide de BizTalk Server. **BIZTALK SERVER. SchemaStrongName** et **BTS. MessageType** sont deux propriétés qui la [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] moteur utilise.  
  
 Dans le tableau suivant, la promotion et est requis colonnes ont les effets suivants :  
  
-   Lorsque IsPromoted est « N », [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] écrit la valeur dans le contexte, au lieu d’en cours de promotion.  
  
-   Lorsque le paramètre IsRequired est « N » pour les types booléens, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] écrit la valeur uniquement si elle est true.  
  
-   Lorsque le paramètre IsRequired est « N » pour les types de chaîne, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] écrit la valeur si elle n’est pas vide ou une valeur par défaut.  
  
|Nom de la propriété|Est promue|Est requis|Remarques|  
|-------------------|-----------------|-----------------|-----------|  
|BatchDateTime|O|N|[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]promeut cette propriété lorsqu’il traite un lot de messages.|  
|[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]MessageType|O|O|Le sérialiseur utilise cette propriété pour distinguer les messages simples et traité par lot. Le désassembleur HL7 lui affecte uniquement les messages du lot. La propriété indique si le message est un message unique, un message par lot entrant ou un message de lot sortant. Si le sérialiseur ne la trouve pas, il suppose que le message est un message unique.|  
|FHS10|O|N|[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]promeut cette propriété lorsqu’il traite un lot de messages.|  
|FHS3|O|N|[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]promeut cette propriété lorsqu’il traite un lot de messages.|  
|FHS4|O|N|[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]promeut cette propriété lorsqu’il traite un lot de messages.|  
|FHS5|O|N|[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]promeut cette propriété lorsqu’il traite un lot de messages.|  
|FHS6|O|N|[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]promeut cette propriété lorsqu’il traite un lot de messages.|  
|DateHeureFich|O|N|[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]promeut cette propriété lorsqu’il traite un lot de messages.|  
|LastSegmentDelimiter manquant|N|N|[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]promeut cette propriété lorsqu’il traite un lot de messages.|  
|MessageClass|O|O|Contient soit **MessageClass2X** ou **MessageClass2Xml** faire la distinction entre les deux classes de messages.|  
|MSA1|O|O|Applicable uniquement pour les messages d’accusé de réception.|  
|MSH1|N|O|Le champ qui contient le séparateur de champ. Le sérialiseur utilise cette propriété.|  
|OÙ MSH2 A ÉTÉ|N|O|Le sérialiseur utilise cette propriété. Le champ contenant les caractères de codage (séparateur de composants, séparateur de répétition, caractère d’échappement et le séparateur de sous-composant).|  
|MSH3_1|O|N|Le premier composant du champ d’application émettrice.|  
|MSH3_2|O|N|Le second composant du champ d’application émettrice.|  
|MSH3_3|O|N|Le troisième composant du champ d’application émettrice.|  
|MSH5_1|O|N|Le premier composant du champ d’application réceptrice.|  
|MSH5_2|O|N|Le second composant du champ d’application réceptrice.|  
|MSH5_3|O|N|Le troisième composant du champ d’application réceptrice.|  
|ParseError|O|O|Indique qu’une erreur s’est produite lors de l’analyse.|  
|SegmentDelimiter2Char|N|N|Le caractère qui délimite les segments.|  
|ToBeBatched|O|N|Lorsque la valeur est False, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] ne met pas en mémoire tampon du message par lot ultérieurement ; sinon, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] envoie le message en tant que partie d’un lot.|  
|ZPartPresent|O|N|Indique si un segment Z non déclaré est présent.|  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Définition d’expressions de filtre sur les ports d’envoi](../../adapters-and-accelerators/accelerator-hl7/setting-filter-expressions-on-send-ports.md)