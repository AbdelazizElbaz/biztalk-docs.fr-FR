---
title: "Qu'est-ce que l'adaptateur WCF-CustomIsolated ? | Microsoft Docs"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: WCF-CustomIsolated adapters, about WCF-CustomIsolated adapters
ms.assetid: 872fe97a-8a96-4b2a-8cc1-2db9b315c44f
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2fdf5a646f586030df6c9492fc6fb2999e49527a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="what-is-the-wcf-customisolated-adapter"></a>Qu'est-ce que l'adaptateur WCF-CustomIsolated ?
L'adaptateur WCF-CustomIsolated permet d'activer l'utilisation des composants d'extensibilité WCF dans BizTalk Server avec un hôte isolé. Il optimise la flexibilité de l'infrastructure WCF. Il permet également aux utilisateurs de sélectionner et configurer une liaison WCF pour l'emplacement de réception, et de spécifier les comportements de point de terminaison et les paramètres de sécurité. Cet adaptateur peut uniquement être utilisé par les transports hébergés dans IIS (Internet Information Services).  
  
 L'adaptateur WCF-CustomIsolated est constitué d'un adaptateur de réception uniquement L'adaptateur de réception WCF-CustomIsolated permet de recevoir les requêtes de service WCF via les liaisons WCF, le comportement de service, le comportement de point de terminaison, le mécanisme de sécurité et la source du corps de message entrant que vous avez sélectionnés et configurés pour l'emplacement de réception exécuté dans un hôte isolé. Un emplacement de réception qui utilise l'adaptateur de réception WCF-CustomIsolated peut être configuré comme emplacement de réception unidirectionnel ou de requête-réponse (bidirectionnel).  
  
 Pour plus d’informations sur WCF des adaptateurs de réception, consultez [quelles sont les adaptateurs WCF ?](../core/what-are-the-wcf-adapters.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration de l’adaptateur WCF-CustomIsolated](../core/configuring-the-wcf-customisolated-adapter.md)   
 [Adaptateurs WCF](../core/wcf-adapters.md)