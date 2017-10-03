---
title: Architecture de runtime | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- runtime, architecture
- architecture, runtime
- runtime
ms.assetid: feff9a84-f19b-44c9-8d05-8e6015bb1ef9
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9e45ac745dbf6704f06f61155b3f57edfdec9e09
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="runtime-architecture"></a>Architecture d'exécution
Avant de voir plus en détail les différents composants de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], il est important de comprendre comment ces composants s'intègrent dans l'architecture globale du produit. Le composant d'exécution de BizTalk Server repose sur une architecture de type « publication-abonnement », dans laquelle un message est publié au sein du système, puis réceptionné par un ou plusieurs abonnés actifs. Différentes versions de cette architecture existent, mais le modèle implémenté dans BizTalk Server est souvent appelé *en fonction du contenu de publication/abonnement*.  
  
 Dans ce modèle, les abonnés définissent les messages qu'ils veulent recevoir à l'aide d'un ensemble de critères. Lorsqu'il est publié, un message est analysé et envoyé à tous les abonnés actifs dont l'abonnement (défini par le biais d'expressions de filtre) correspond. Dans le cas de BizTalk Server, parler de contenu peut induire en erreur, car les critères utilisés pour les abonnements ne sont pas nécessairement liés au contenu des messages, mais peuvent également se rapporter à des informations contextuelles sur le message lui-même. Pour plus d’informations, le mécanisme d’abonnement, consultez [publier et s’abonner une Architecture](../core/publish-and-subscribe-architecture.md).  
  
 Les sections suivantes décrivent les différents composants de l'architecture d'exécution BizTalk Server.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Le Message BizTalk Server](../core/the-biztalk-server-message.md)  
  
-   [Cycle de vie d’un Message](../core/lifecycle-of-a-message.md)  
  
-   [Le traitement du Message](../core/processing-the-message.md)  
  
-   [Messages de requête-réponse](../core/request-response-messaging.md)  
  
-   [Le moteur de messagerie](../core/the-messaging-engine.md)  
  
-   [Entités](../core/entities.md)  
  
-   [Artefacts](../core/artifacts.md)  
  
-   [Enterprise Single Sign-On (SSO)](../core/enterprise-single-sign-on-sso.md)  
  
-   [Moteur des règles d’entreprise](../core/business-rules-engine.md)  
  
-   [Assemblys BizTalk](../core/biztalk-assemblies.md)