---
title: "Objets du Pack d’administration détecte | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 291e8936-b299-4719-9f7e-edc86f76fcbd
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 109612c690c1e4e2ecb1c0a4a34a07c7bda27e02
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="objects-the-management-pack-discovers"></a>Objets découverts par le pack d’administration
Le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Pack d’administration détecte les types d’objets décrits dans le tableau suivant. Pour plus d’informations sur la détection d’objets, consultez la [détections dans Operations Manager 2007](http://go.microsoft.com/fwlink/?LinkId=108505) rubrique dans la bibliothèque en ligne d’Operations Manager 2007 R2/2012 (http://go.microsoft.com/fwlink/?LinkId=108505).  
  
|Nom|Catégorie|Type d'objet|  
|----------|--------------|-----------------|  
|BizTalkGroup|Entité logique|Objets de vue d’application|  
|BizTalkHost|Entité logique|Objets de vue d’application|  
|BizTalkApplication|Entité logique|Objets de vue d’application|  
|ApplicationArtifact|Entité logique|Objets de vue d’application|  
|HostedApplicationArtifact|Entité logique|Objets de vue d’application|  
|ReceivePort|Artefact de l’application|Objets de vue d’application|  
|ReceiveLocation|Artefact de l’application|Objets de vue d’application|  
|Orchestration|Artefact de l’application|Objets de vue d’application|  
|SendPort|Artefact de l’application|Objets de vue d’application|  
|Envoi|Artefact de l’application|Objets de vue d’application|  
|BizTalkGroupDeployment|System.Service|Objets de vue de déploiement|  
|BizTalkInstallation|Windows.SoftwareInstallation|Objets de vue de déploiement|  
|ServerRole|Windows.ComputerRole|Objets de vue de déploiement|  
|BiztalkRuntimeRole|ServerRole|Objets de vue de déploiement|  
|RulesEngineRole|BizTalkServerRole|Objets de vue de déploiement|  
|BAMRole|Entité logique|Objets de vue de déploiement|  
|BAMRuntime|Entité logique|Objets de vue de déploiement|  
|BAMAnalysis|Entité logique|Objets de vue de déploiement|  
|BAMAlerts|Entité logique|Objets de vue de déploiement|  
|BAMPortal|site Web|Objets de vue de déploiement|  
|BizTalkApplicationService|Windows.ApplicationComponent|Objets de vue de déploiement|  
|BizTalkHostDeployment|Entité logique|Objets de vue de déploiement|