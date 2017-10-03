---
title: "Schémas XML HL7 2.X et 2. | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- schemas, schema types
- HL7-encoded messages
- 2.X schemas
- schemas, HL7 organization
- BTAHL7, HL7 schemas
- HL7, 2.XML schemas
- Update2XMLSchema tool
- schemas, common schemas
- 2.X schemas, about 2.X schemas
- 2.X schemas, compatibility
- 2.XML schemas, compatibility
- messages, HL7-encoded messages
- HL7 Schema Selector
- schemas, 2.XML schemas
- 2.XML schemas
- 2.XML schemas, about 2.XML schemas
- HL7, 2.X schemas
- schemas, compatibility
- common schemas
- schemas, 2.X schemas
ms.assetid: 02532d72-1948-48d8-a8ef-6b5a814eb573
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7eec467f644919427fa6a3bc65264284f35ae650
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="hl7-2x-and-2xml-schemas"></a>Schémas XML HL7 2.X et 2.
L’organisation HL7 publie deux ensembles de schémas : HL7 schémas 2.X, utilisés pour les messages encodés HL7 et les schémas XML HL7 2, utilisés pour les messages encodés en XML.  
  
 [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] fonctionne en mode natif avec le HL7 2.X schémas. [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]le programme d’installation de fichiers de schéma de charge le HL7 2.X dans \< *lecteur*> : \program files\\ [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk \<version > Accelerator for HL7\Templates\Schemas\2.X. Par conséquent, le HL7 2.X schémas sont disponibles dans le sélecteur de schéma HL7. Vous exécutez le sélecteur de schéma HL7 dans [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].  
  
 BTAHL7 fonctionne avec les schémas XML de 2 HL7, mais le programme d’installation BTAHL7 ne charge pas de schémas XML HL7 2 avec les fichiers de programme BTAHL7, et vous devrez modifier certaines des schémas XML HL7 2. pour qu’elle fonctionne avec BTAHL7. Pour les rendre disponibles dans le sélecteur de schéma HL7 et apporter les modifications nécessaires, téléchargez les schémas XML de 2 à partir du site Web d’organisation HL7, puis exécutez le **Update2XMLSchema** outil (pour plus d’informations, consultez [ Outil de Update2XMLSchema](../../adapters-and-accelerators/accelerator-hl7/update2xmlschema-tool.md)). L’outil modifiera les schémas XML de 2 HL7 comme requis pour fonctionner avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], puis les placer dans \< *lecteur*> : \program files\\ [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk \<version > Accelerator for HL7\Templates\Schemas.  
  
 Chacun de ces jeux de schémas contient une série de versions. Versions de schéma dynamique HL7 2.X incluent 2.1 à 2.5 (pour plus d’informations, consultez [HL7 Versions](../../adapters-and-accelerators/accelerator-hl7/hl7-versions.md)). HL72. Les versions de schéma XML incluent 2.3.1, 2.4 et 2.5. Versions de schéma HL7 2.X sont descendante conforme. Versions de schéma XML HL7 2 ne sont pas descendante conforme.  
  
> [!NOTE]
>  Car la version 2.4 de 2 XML n’est pas descendante compatible avec 2.3.1 pour 2.XML, une erreur peut se produire si vous déployez une version 2.4 du schéma XML 2., puis soumettez une instance d’un message conforme à la 2.3.1 version. Pour corriger ce problème, vous devrez peut-être créer un espace de noms cible différent 2.3.1 traiter les messages.  
  
 Lorsque vous créez un HL7 multipartie 2.X message, vous devez définir le type du corps à un schéma spécifique. Si ce n’est pas le cas, le sérialiseur rejette le message.  
  
 Le tableau suivant décrit les deux types de schémas avec lequel fonctionne BTAHL7.  
  
|Type de schéma| Description|  
|-----------------|-----------------|  
|HL7FF – ER7 codé les schémas (2.X)|BTAHL7 fournit HL7 schémas 2.X dérivées de la base de données HL7 accès, notamment :<br /><br /> : Un jeu de tous les schémas spécifiques en fonction de la version, le type de message ou l’événement<br />-Les schémas courants pour les segments, les types de données, les tables, les en-têtes et les accusés de réception (ACK)<br /><br /> BTAHL7 prend en charge les modèles de schéma suivants :<br /><br /> -V2.1<br />-VERSION 2.2<br />-VERSION 2.3<br />-V2.3.1<br />-V2.4<br />-2.5<br /><br /> Le programme d’installation BTAHL7 installe V2. X schémas dans \< *lecteur*> \Program Files\\ [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator pour HL7\Templates\Schemas.|  
|HL7XML – l’encodage XML 2.|BTAHL7 prend en charge les schémas suivants :<br /><br /> -V2.3.1<br />-V2.4<br />-2.5<br /><br /> BTAHL7 le programme d’installation n’installe pas les schémas XML de 2. Pour les installer et les modifier pour travailler avec l’Éditeur BizTalk, consultez [Update2XMLSchema outil](../../adapters-and-accelerators/accelerator-hl7/update2xmlschema-tool.md).|  
  
## <a name="common-schemas"></a>Schémas courants  
 BTAHL7 utilise un schéma HL7 spécifique à un type de message pour créer et valider le corps d’une instance de ce type de message. Il utilise également des schémas courants, outre les schémas spécifiques. BTAHL7 utilise des schémas HL7 courants pour valider les accusés de réception et les en-têtes de message HL7. Ces fichiers sont MSH_25_GLO_DEF.xsd pour les en-têtes et ACK_24_GLO_DEF pour les accusés de réception.  
  
 BTAHL7 utilise également des schémas courants pour valider les types de données, les segments et les valeurs de la table. Ces schémas sont spécifiques à chaque version des normes HL7. Par exemple, les schémas courants pour les messages de la version 2.2 sont datatype_22.xsd, segments_22.xsd et tablevalues_22.xsd. BTAHL7 utilise ces schémas pour valider les types de données, les segments et les valeurs de la table pour tous les messages de la version 2.2.  
  
## <a name="see-also"></a>Voir aussi  
 [Traitement des messages](../../adapters-and-accelerators/accelerator-hl7/message-processing.md)   
 [Traitement des fichiers plats BTAHL72X](../../adapters-and-accelerators/accelerator-hl7/btahl72x-flat-file-processing.md)   
 [Traitement de BTAHL72XML](../../adapters-and-accelerators/accelerator-hl7/btahl72xml-processing.md)   
 [Le traitement des Messages HL7](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md)   
 [L’utilisation des schémas 2.X HL7](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md)   
 [Utilisation de schémas XML de 2 HL7](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-xml-schemas.md)