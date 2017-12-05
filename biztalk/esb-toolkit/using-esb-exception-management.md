---
title: "À l’aide de la gestion des exceptions ESB | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: de6ce411-2d34-4fd8-9644-6fbc9cec266d
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c4eff5a729b8c8ca191b2185180e312f9e895c02
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="using-esb-exception-management"></a>À l’aide de la gestion des exceptions ESB
Erreurs et exceptions peuvent se produire dans une plage de contextes et pendant un nombre différent d’étapes de traitement dans une architecture ESB. Cette section fournit des informations sur la gestion des exceptions et décrit comment vous pouvez publier des informations via le portail de gestion ESB.  
  
## <a name="overview"></a>Vue d'ensemble  
 Il existe de nombreuses façons de gérer les exceptions dans une solution BizTalk Server, y compris à l’aide d’infrastructures telles que la bibliothèque de l’entreprise. Toutefois, lorsque vous développez avec ESB et BizTalk Server, vous travaillez dans un environnement basé sur le message. Tous les éléments dans une solution BizTalk sont orienté messages, et les développeurs BizTalk de réflexion d’une manière orientée message. Par conséquent, le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] implémente une approche orientée message pour la gestion des exceptions.  
  
 L’infrastructure de gestion d’Exception ESB suit un modèle de conception qui permet une approche flexible permettant l’analyse des exceptions et réponses d’erreur proviennent en dehors de la solution, peut-être au niveau de la division.  
  
 Les rubriques suivantes traitent de l’infrastructure de gestion d’Exception ESB plus en détail :  
  
-   [Conception de l’infrastructure de gestion des exceptions ESB](../esb-toolkit/design-of-the-esb-exception-management-framework.md)  
  
-   [Les composants de l’infrastructure de gestion des exceptions](../esb-toolkit/the-components-of-the-exception-management-framework.md)  
  
-   [Utilisation de l’infrastructure de gestion des exceptions](../esb-toolkit/using-the-exception-management-framework.md)  
  
-   [Création de gestionnaires d’exceptions personnalisés](../esb-toolkit/creating-custom-exception-handlers.md)