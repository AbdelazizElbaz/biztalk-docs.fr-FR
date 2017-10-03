---
title: Outils de conception BizTalk | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BizTalk Adapter Framework
- schemas, tools
- BizTalk Orchestration Designer
- schemas, BTARN schemas
- BizTalk Editor
- BizTalk Mapper
- tools, schemas
- BTARN, schemas
- BizTalk Pipeline Designer
ms.assetid: a981e167-f178-4fef-be0e-02fa15feffc2
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 203f02c3cf14ddf468419160187b5ef2a2f9d325
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="biztalk-design-time-tools"></a>Outils de conception BizTalk
Les développeurs qui travaillent sur [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] pouvez utiliser le jeu d’outils au moment du design intégrés [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)]. Ces outils sont intégrés dans [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] [!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)]. Pour plus d’informations sur [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] outils, consultez [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] aide.  
  
## <a name="biztalk-editor"></a>Éditeur BizTalk  
 L’Éditeur BizTalk vous permet de gérer [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] schémas XSD qui sont basées sur les processus d’Interface RosettaNet partenaires (PIP). [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]Installe les schémas suivants pour le développement de votre solution :  
  
-   0A1_FailureNotificationPropertySchema.xsd  
  
-   0A1_MS_V02_00_FailureNotification.xsd  
  
-   0A1_V1_FailureNotificationMessageGuideline.xsd  
  
-   0C1_MS_R01_02_AsynchronousTestNotification.xsd  
  
-   0C2_MS_R01_02_AsynchronousTestConfirmation.xsd  
  
-   0C2_MS_R01_02_AsynchronousTestRequest.xsd  
  
-   0C3_MS_R01_02_SynchronousTestNotification.xsd  
  
-   0C4_MS_R01_02_SynchronousTestQuery.xsd  
  
-   0C4_MS_R01_02_SynchronousTestResponse.xsd  
  
-   2A12_MS_V01_03_ProductMasterNotification.xsd  
  
-   3A2PriceAndAvailabilityQueryMessageGuideline_v1_3.xsd  
  
-   3A2PriceAndAvailabilityResponseMessageGuideline_v1_3.xsd  
  
-   3A4_MS_V02_02_PurchaseOrderConfirmation.xsd  
  
-   3A4_MS_V02_02_PurchaseOrderRequest.xsd  
  
 Ces schémas sont disponibles à \< *lecteur*> : \Program Files\\ [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk \<version > Accelerator for RosettaNet\SDK\Schemas.  
  
 Vous pouvez ajouter d’autres schémas en téléchargeant le PIP sur le site Web de RosettaNet à [http://go.microsoft.com/fwlink/?linkid=33859](http://go.microsoft.com/fwlink/?linkid=33859). Pour plus d’informations, consultez [comprenant un nouveau Partner Interface Process](../../adapters-and-accelerators/accelerator-rosettanet/incorporating-a-new-partner-interface-process.md).  
  
## <a name="biztalk-mapper"></a>Mappeur BizTalk  
 Le Mappeur BizTalk vous permet de créer et personnaliser des cartes qui définissent les transformations de données. Le Mappeur BizTalk vous permet de mapper les transformations de types de messages RosettaNet entrants et sortants.  
  
## <a name="biztalk-orchestration-designer"></a>Concepteur d'Orchestration BizTalk  
 Le Concepteur d’Orchestration BizTalk vous permet de concevoir et implémenter des processus d’entreprise. Vous pouvez personnaliser les processus privés fournis dans le [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] Kit de développement logiciel. Pour plus d’informations, consultez [les processus privés &#91; RN3 &#93; ](../../adapters-and-accelerators/accelerator-rosettanet/private-processes.md) et [personnalisation des processus privé &#91; RN3 &#93; ](../../adapters-and-accelerators/accelerator-rosettanet/customizing-private-processes.md). Vous ne pouvez pas personnaliser les processus publics ; Cette opération annulent leur conformité RosettaNet.  
  
## <a name="biztalk-pipeline-designer"></a>Concepteur de Pipeline BizTalk  
 Le Concepteur de Pipeline BizTalk vous permet de créer et configurer les pipelines qui définissent et lier des étapes de traitement des messages. Pipelines divisent en différentes étapes de traitement des messages et déterminent l’ordre dans lequel vous effectuez chaque catégorie de travail.  
  
 Le [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] SDK comprend à la fois recevoir et transmettre des pipelines de Framework RNIF (RosettaNet Implementation). Pour plus d’informations, consultez [RNIF Pipelines](../../adapters-and-accelerators/accelerator-rosettanet/rnif-pipelines.md).  
  
## <a name="biztalk-adapter-framework"></a>Infrastructure d’adaptateurs BizTalk  
 L’infrastructure d’adaptateurs BizTalk avec les adaptateurs de point de terminaison vous permet d’intégrer des partenaires et des applications.  
  
## <a name="see-also"></a>Voir aussi  
 [Outils et fonctionnalités de BizTalk Server et de BTARN](../../adapters-and-accelerators/accelerator-rosettanet/tools-and-features-of-biztalk-server-and-btarn.md)   
 [Outils d’administration et exécution](../../adapters-and-accelerators/accelerator-rosettanet/administration-and-run-time-tools.md)   
 [Outils d’analyse](../../adapters-and-accelerators/accelerator-rosettanet/analysis-tools1.md)   
 [Vous incorporez un nouveau Partner Interface Process](../../adapters-and-accelerators/accelerator-rosettanet/incorporating-a-new-partner-interface-process.md)