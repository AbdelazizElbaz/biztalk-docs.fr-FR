---
title: Suppression de MSMQT | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 007d65ce-d2a2-4602-80c8-55b26617f397
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f869dde7cb4c793e1e36beee6a20bc89d19272e8
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="msmqt-deprecation"></a>Suppression de MSMQT
La fonctionnalité MSMQT a été supprimée de BizTalk Server. Dans le Concepteur d’Orchestration, l’option de transport MSMQT reste disponible dans l’Assistant Configuration du Port au moment du design, comme indiqué dans l’image ci-dessous lorsque vous choisissez la **spécifier maintenant** est définie sur **deliaisondePort**.  
  
 **Assistant Configuration du port montrant le transport MSMQT**  
  
 ![](../core/media/portconfigurationwizard-msmqt-transport.gif "PortConfigurationWizard_MSMQT_Transport")  
  
## <a name="biztalk-server-projects"></a>Projets BizTalk Server  
 Les nouveaux projets [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ne doivent pas utiliser l'option de transport MSMQT. Déploiement d’application à BizTalk Server échoue avec l’erreur **le type de protocole « MSMQT » introuvable**.  
  
## <a name="migrated-biztalk-server-projects"></a>Projets BizTalk Server migrés  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]les projets peuvent être migrés vers BizTalk Server à l’aide de la [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] comme indiqué dans l’Assistant Conversion [migration d’un projet BizTalk Server](../core/migrating-a-biztalk-server-project.md). Les projets contenant des ports configurés pour utiliser le transport MSMQT doivent être reconfigurés manuellement avant le déploiement de BizTalk Server. La reconfiguration recommandée consiste à utiliser l'adaptateur MSMQ.  Pour plus d’informations sur l’adaptateur MSMQ, consultez [quel est l’adaptateur MSMQ ?](../core/what-is-the-msmq-adapter.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Migration de l’adaptateur MSMQT vers l’adaptateur MSMQ](../core/migrating-from-the-msmqt-adapter-to-the-msmq-adapter.md)