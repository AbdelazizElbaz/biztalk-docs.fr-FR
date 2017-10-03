---
title: "Qu'est-ce que l'adaptateur WCF-Custom ? | Microsoft Docs"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: WCF-Custom adapters, about WCF-Custom adapters
ms.assetid: 7b2178dd-f737-4784-9bcb-e2b3979bfb0d
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5e090f82bc43d96dc14295af2fac2807cf1fd137
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="what-is-the-wcf-custom-adapter"></a>Qu'est-ce que l'adaptateur WCF-Custom ?
L'adaptateur WCF-Custom permet d'activer l'utilisation des composants d'extensibilité WCF dans BizTalk Server. Il optimise la flexibilité de l'infrastructure WCF. Les utilisateurs peuvent ainsi sélectionner et configurer une liaison WCF pour l'emplacement de réception et le port d'envoi. L'adaptateur permet également de définir les comportements de point de terminaison et les paramètres de sécurité.  
  
 L'adaptateur WCF-Custom est constitué de deux adaptateurs : un adaptateur de réception et un adaptateur d'envoi.  
  
 **Adaptateur de réception WCF-Custom**  
  
 L'adaptateur de réception WCF-Custom permet de recevoir les requêtes de service WCF via les liaisons, le comportement de service, le comportement de point de terminaison, le mécanisme de sécurité et la source du corps de message entrant que vous avez sélectionnés et configurés dans la boîte de dialogue Propriétés du transport de l'emplacement de réception. Un emplacement de réception qui utilise l'adaptateur de réception WCF-Custom peut être configuré comme emplacement de réception unidirectionnel ou de requête-réponse (bidirectionnel).  
  
 **Adaptateur d’envoi WCF-Custom**  
  
 L'adaptateur d'envoi WCF-Custom permet d'appeler un service WCF à l'aide du contrat sans type avec les liaisons, le comportement de service, le comportement de point de terminaison, le mécanisme de sécurité et la source du corps de message sortant que vous avez sélectionnés et configurés.  
  
 Pour plus d’informations sur WCF de réception et les adaptateurs d’envoi, consultez [quelles sont les adaptateurs WCF ?](../core/what-are-the-wcf-adapters.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration de l’adaptateur WCF-Custom](../core/configuring-the-wcf-custom-adapter.md)   
 [Adaptateurs WCF](../core/wcf-adapters.md)