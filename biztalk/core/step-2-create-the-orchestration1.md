---
title: "Étape 2 : Créer le Orchestration1 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a88cafbb-3b6f-4d27-8516-79a2391b4e31
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1989fe18d9c9c81741ac83bd2f96627ea818eb91
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-2-create-the-orchestration"></a>Étape 2 : Créer l’Orchestration
Le programme d'installation de l'orchestration fait appel à un projet appelé BeginDocTest, comme décrit ci-dessous :  
  
-   Ports  
  
-   Messages  
  
-   Envoi et réception  
  
-   Construire un message  
  
-   Transforms  
  
 L'orchestration ne gère pas les exceptions. J.D. Edwards OneWorld procède à l'opération BeginDoc puis à d'autres opérations ultérieures par l'intermédiaire d'une transaction implicite, de manière qu'elle soit annulée si la connexion expire. L'orchestration BizTalk n'a donc aucune opération à effectuer pour annuler les modifications apportées par J.D. Edwards OneWorld. Toutefois, un délai d'expiration génèrera une exception au sein de l'orchestration BizTalk. Celle-ci sera enregistrée dans le journal des événements. Si vous voulez ajouter la gestion des exceptions à l’orchestration, consultez les rubriques « Ajout d’un bloc Intercepter l’exception » et « Ajout d’un bloc de compensation » dans l’aide de Microsoft BizTalk Server.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Tâche 1 : Créer les Ports](../core/task-1-create-the-ports2.md)  
  
-   [Tâche 2 : Créer les Messages](../core/task-2-create-the-messages1.md)  
  
-   [Tâche 3 : Configurer l’envoi et réception des formes](../core/task-3-configure-the-send-and-receive-shapes1.md)  
  
-   [Tâche 4 : Configurer la forme construire un Message](../core/task-4-configure-the-construct-message-shape2.md)  
  
-   [Tâche 5 : Configurer la forme Transformer](../core/task-5-configure-the-transform-shape1.md)