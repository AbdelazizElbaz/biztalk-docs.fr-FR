---
title: "Le Service d’analyse de la Solution avec BAM orientée services | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- monitoring, service solutions
- service solution tutorial, monitoring
- OrchestrationEventStream object
ms.assetid: 9b251580-9371-490e-9218-0ce3f6b00fa6
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dc1aeaec2513ebe3c6d7fe62ef542b6f044bca56
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="monitoring-the-service-oriented-solution-with-bam"></a>Le Service d’analyse de la Solution avec BAM orientée services
La solution surveille l’activité dans toutes les versions de la **CustomerService** orchestration à l’aide de l’analyse BAM (Business Activity) API. Plus spécifiquement, il utilise le nouveau **OrchestrationEventStream** objet.  
  
## <a name="what-is-the-orchestrationeventstream-object"></a>Qu'est-ce que l'objet OrchestrationEventStream ?  
 La nouvelle **OrchestrationEventStream** objet permet le suivi et l’analyse à partir d’orchestrations. Les informations capturées maintiennent la cohérence transactionnelle avec l'état de l'orchestration. Par exemple, si l'instance de l'hôte de l'orchestration redémarre au milieu d'une exécution de l'orchestration, le redémarrage s'effectue à partir du dernier point de persistance de l'instance. Le **OrchestrationEventStream** classe garantit que les données capturées sont cohérentes avec le dernier point de persistance de l’instance d’orchestration. Tous les **OrchestrationEventStream** méthodes sont statiques, afin que votre orchestration n’a pas besoin créer une instance de celui-ci.  
  
> [!NOTE]
>  Pour utiliser le **OrchestrationEventStream** de l’objet, vous devez ajouter des références à la **Microsoft.BizTalk.Bam.XLANGs** et **Microsoft.BizTalk.Bam.EventObservation** assemblys. Bien que le **OrchestrationEventStream** objet se trouve dans le **Microsoft.BizTalk.Bam.EventObservation** espace de noms, il réside dans le **Microsoft.BizTalk.Bam.XLANGs** assembly.  
  
 Bien que l'Éditeur de modèle de suivi (TPE) soit l'outil recommandé dans le cadre de l'analyse BAM, il ne peut ni capturer les valeurs des variables de l'orchestration, ni gérer les objets personnalisés. La solution utilise l'API BAM pour remédier à ce problème.  
  
 Pour obtenir des informations générales sur l’analyse BAM, consultez [à l’aide de l’analyse BAM](../core/using-business-activity-monitoring.md). Pour plus d’informations sur l’éditeur de profil de suivi (TPE), consultez [éditeur](../core/tracking-profile-editor.md).  
  
## <a name="wrapping-the-orchestrationeventstream-object"></a>Classe enveloppante de l'objet OrchestrationEventStream  
 Le retour automatique à la solution orientée le **OrchestrationEventStream** classe avec le **ServiceLevelTracking** classe. Le **ServiceLevelTracking** classe fournit des méthodes de l’étape majeure de spécifiques à l’application et masque les détails de l’utilisation de certaines **OrchestrationEventStream**.  
  
 Comme dans **OrchestrationEventStream**, toutes les méthodes de **ServiceLevelTracking** sont statiques. Ainsi, l'orchestration ou le composant personnalisé n'a pas besoin d'en créer une instance. La méthode qui démarre le suivi d’une activité, **TrackingBeginRequest**, retourne un ID d’instance unique d’activité. Tous les événements de suivi suivantes doivent être associés à cet ID d’instance activité afin de capturer les données de niveau de service correctement, car il est propre à l’instance de la **CustomerService** orchestration.  
  
## <a name="see-also"></a>Voir aussi  
 [Développement d’un Service de la Solution orientée services](../core/developing-a-service-oriented-solution.md)   
 [Caractéristiques de l’implémentation du Service orienté solutions](../core/implementation-highlights-of-the-service-oriented-solution.md)