---
title: BizTalk Accelerator pour SWIFT Runtime | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- runtime, architecture
- developing, components
- architecture, topology
- messages, message flow diagram
- runtime, components
- SWIFT runtime
- architecture, runtime architecture
- SWIFT network
- A4SWIFT, network
- topology
ms.assetid: c0f59760-7d7d-4b22-a7dc-54e563971d4a
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f312a91d403d125fe6d245b92bf83da57d1031fe
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="biztalk-accelerator-for-swift-runtime"></a>BizTalk Accelerator pour SWIFT Runtime
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] fournit les fonctionnalités sous deux formes : matériaux de développement et les composants d’exécution. Matériaux de développement inclure des schémas XSD, les règles de validation et les stratégies et les exemples de code. Composants d’exécution incluent le désassembleur SWIFT personnalisé, l’assembleur SWIFT personnalisé, la réparation de Message et d’orchestration (MrsrRepair.odx) de la nouvelle soumission et l’orchestration de rapprochement de réponse de FIN (FrrMain.odx). Pour plus d’informations sur Message Repair et New Submission, consultez [Message Repair et New Submission](../../adapters-and-accelerators/accelerator-swift/message-repair-and-new-submission.md). Pour plus d’informations sur FRR, consultez [rapprochement de réponse de FIN](../../adapters-and-accelerators/accelerator-swift/fin-response-reconciliation.md).  
  
 L’illustration suivante montre l’architecture de haut niveau de système de [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)].  
  
 ![](../../adapters-and-accelerators/accelerator-swift/media/a4swiftsystemarchitecture-end-to-end.gif "A4SWIFTSystemArchitecture_End_to_End")  
  
 La figure suivante illustre le flux des messages entre A4SWIFT et une application back-end et comment A4SWIFT utilise [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] formulaires dans MRSR de site pour Message Repair et New Submission.  
  
 ![](../../adapters-and-accelerators/accelerator-swift/media/a4swiftsystemarchitecture-interfaceswithbackendapplications.gif "A4SWIFTSystemArchitecture_InterfaceswithBackEndApplications")  
  
 La figure suivante illustre le flux des messages entre A4SWIFT et le réseau SWIFT.  
  
 ![](../../adapters-and-accelerators/accelerator-swift/media/a4swiftsystemarchitecture-interfaceswiththeswiftnetwork.gif "A4SWIFTSystemArchitecture_InterfaceswiththeSWIFTNetwork")  
  
 Vous pouvez définir tous les composants A4SWIFT comme des implémentations spécifiques à la verticale de [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] composants d’application. Les accélérateurs BizTalk fournissent des fonctionnalités de développement et d’exécution pour accélérer le développement d’applications BizTalk verticales spécifiques sur de [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]. Par conséquent, tous les composants A4SWIFT (développement ou runtime) se conformer à et s’adaptent, le [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] architecture d’application. A4SWIFT installe les composants d’exécution dans le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] runtime en tant que composants personnalisés. Après le développement des matériaux est compilés et déployés, A4SWIFT et [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] runtime les utiliser pour fournir des fonctionnalités de messagerie et d’automatisation de SWIFT.  
  
 La figure suivante illustre la topologie de l’application de haut niveau pour [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)].  
  
 ![](../../adapters-and-accelerators/accelerator-swift/media/fsa-intro1.gif "FSA_Intro1")  
  
 Le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] modèle d’application utilise la base de données MessageBox et le modèle d’éditeur-abonné qui régit le flux de messages vers et depuis la base de données MessageBox. Pour plus d’informations sur la conception d’architecture et l’application BizTalk, consultez [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] aide.  
  
 Le modèle d’application A4SWIFT hérite le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] modèle d’application et lui ajoute des composants SWIFT spécifiques afin de faciliter les solutions SWIFT sur [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]. La liste suivante décrit ces composants A4SWIFT spécifiques :  
  
-   **Composants d’exécution.** Désassembleur SWIFT dans le pipeline de réception, l’assembleur SWIFT dans le pipeline d’envoi, Message Repair et New Submission orchestration et d’orchestration de rapprochement de réponse de FIN.  
  
-   **Documents de développement.** Schémas SWIFT, des règles, des orchestrations et des exemples de projets à inclure dans les solutions des clients et déployée sur le runtime pour l’exécution.  
  
 Cette section décrit le runtime A4SWIFT en détail.  
  
 Contenu de cette section :  
  
-   [Désassembleur SWIFT](../../adapters-and-accelerators/accelerator-swift/swift-disassembler.md)  
  
-   [Assembleur SWIFT](../../adapters-and-accelerators/accelerator-swift/swift-assembler.md)  
  
-   [Envoi de Messages via emplacements de réception et des formulaires InfoPath](../../adapters-and-accelerators/accelerator-swift/submitting-messages-through-receive-locations-and-infopath-forms.md)  
  
-   [Moteur de Validation de message](../../adapters-and-accelerators/accelerator-swift/message-validation-engine.md)