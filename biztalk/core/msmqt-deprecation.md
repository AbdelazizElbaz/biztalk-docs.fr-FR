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
ms.openlocfilehash: 27e7095c73cd337a1fb08f2d867e817ad5838206
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="msmqt-deprecation"></a>Suppression de MSMQT
La fonctionnalité MSMQT a été supprimée de BizTalk Server. Dans le Concepteur d’Orchestration, l’option de transport MSMQT reste disponible dans l’Assistant Configuration du Port au moment du design, comme indiqué dans l’image ci-dessous lorsque vous choisissez la **spécifier maintenant** est définie sur **deliaisondePort**.  
  
 **Assistant Configuration du port montrant le transport MSMQT**  
  
 ![](../core/media/portconfigurationwizard-msmqt-transport.gif "PortConfigurationWizard_MSMQT_Transport")  
  
## <a name="biztalk-server-projects"></a>Projets BizTalk Server  
 Les nouveaux projets [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ne doivent pas utiliser l'option de transport MSMQT. Déploiement d’application à [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] échoue avec l’erreur **le type de protocole « MSMQT » introuvable**.  
  
## <a name="migrated-biztalk-server-projects"></a>Projets BizTalk Server migrés  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]les projets peuvent être migrés vers [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] à l’aide de la [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] comme indiqué dans l’Assistant Conversion [migration d’un projet BizTalk Server](../core/migrating-a-biztalk-server-project.md). Les projets contenant des ports configurés pour utiliser le transport MSMQT doivent être reconfigurés manuellement avant leur déploiement vers [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]. La reconfiguration recommandée consiste à utiliser l'adaptateur MSMQ.  Pour plus d’informations sur l’adaptateur MSMQ, consultez [quel est l’adaptateur MSMQ ?](../core/what-is-the-msmq-adapter.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Migration à partir de l’adaptateur MSMQT vers l’adaptateur MSMQ](../core/migrating-from-the-msmqt-adapter-to-the-msmq-adapter.md)