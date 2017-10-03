---
title: Outils de conception | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BizTalk Adapter Framework
- BTAHL7, tools
- Starter Project
- Pipeline Designer
- BizTalk Editor
- Visual Studio Starter Project
- BizTalk Mapper
- design-time tools
- Orchestration Designer
ms.assetid: 709bd782-d2ad-49be-ba33-e957eba2a0cc
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e22272fd04dd3bf2461e4b9fef104657cf007fbb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="design-time-tools"></a>Outils de conception
Les développeurs qui travaillent sur [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) a accès à un ensemble d’outils de conception intégrée [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)]. Ces outils sont intégrés dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]. Pour plus d’informations sur [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] outils, consultez [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] aide.  
  
## <a name="biztalk-editor"></a>Éditeur BizTalk  
 L’Éditeur BizTalk vous permet de gérer des schémas XSD de HL7. Vous pouvez utiliser les modèles de schéma pris en charge suivants (en tant que fichiers XSD) pour le développement de votre solution :  
  
-   HL7 : 2.1 (y compris les 37 événements)  
  
-   HL7 : 2.2 (y compris les 56 événements)  
  
-   HL7 : 2.3 (y compris les 182 événements)  
  
-   HL7 : 2.3.1 (y compris les 189 événements)  
  
-   HL7 : 2.4 (y compris les 288 événements)  
  
-   HL7 : 2.5 (y compris environ 390 schémas)  
  
-   HL7 : 2 XML (y compris environ 450 schémas pour V2.3.1 et 2.4)  
  
## <a name="biztalk-mapper"></a>Mappeur BizTalk  
 Le Mappeur BizTalk vous permet de créer et personnaliser des cartes qui définissent les transformations de données. Le Mappeur BizTalk vous permet de mapper des transformations entrantes et sortantes [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] types de messages.  
  
## <a name="biztalk-orchestration-designer"></a>Concepteur d'Orchestration BizTalk  
 Le Concepteur d’Orchestration BizTalk vous permet de concevoir et implémenter des processus d’entreprise.  
  
## <a name="biztalk-pipeline-designer"></a>Concepteur de Pipeline BizTalk  
 Le Concepteur de Pipeline BizTalk vous permet de créer et configurer les pipelines qui définissent et les étapes de traitement de lien. Pipelines divisent le traitement en étapes et déterminent l’ordre dans lequel vous effectuez chaque catégorie de travail.  
  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]fournit à la fois recevant et transmettent des pipelines pour toutes les versions prises en charge de HL7. [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]fournit un modèle de pipeline qui a un analyseur HL7 personnalisé et le composant désassembleur/assembleur.  
  
## <a name="biztalk-adapter-framework"></a>Infrastructure d’adaptateurs BizTalk  
 L’infrastructure d’adaptateurs BizTalk avec les adaptateurs de point de terminaison vous permet d’intégrer des partenaires et des applications.  
  
## <a name="visual-studio-starter-project"></a>Projet de démarrage de Visual Studio  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]inclut le [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] projet de démarrage, vous pouvez utiliser pour votre implémentation de solutions HL7 de démarrage rapide. Le projet de démarrage contient les projets suivants :  
  
-   **Vide**[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]**projet**.     N’inclut pas tous les schémas.  
  
-   [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]**V2XCommon projet**. Inclut des schémas d’en-tête et d’accusé de réception.  
  
-   [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]**V21Common projet**. Inclut des schémas courants pour HL7 version 2.1.  
  
-   [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]**V22Common projet**. Inclut des schémas courants pour HL7 version 2.2.  
  
-   [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]**V23Common projet**. Inclut des schémas courants pour HL7 version 2.3.  
  
-   [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]**V231Common projet**. Inclut des schémas courants pour HL7 version 2.3.1.  
  
-   [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]**V24Common projet**. Inclut des schémas courants pour HL7 version 2.4.  
  
-   BTAHL7**V25Common projet**. Inclut des schémas courants pour HL7 version 2.5.  
  
## <a name="see-also"></a>Voir aussi  
 [Outils et fonctionnalités](../../adapters-and-accelerators/accelerator-hl7/tools-and-features.md)   
 [Outils d’analyse](../../adapters-and-accelerators/accelerator-hl7/analysis-tools2.md)