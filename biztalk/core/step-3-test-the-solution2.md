---
title: "Étape 3 : Tester la Solution2 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 30dbc7c9-3c5f-4953-b26f-5c41141c22ad
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6c0e484a9f6af788775ec4ae7309965327378267
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-3-test-the-solution"></a>Étape 3 : Tester la Solution
![Étape 3 sur 3](../adapters-and-accelerators/adapter-oracle-database/media/step-3of3.gif "Step_3of3")  
  
 **Durée :** 5 minutes  
  
 **Objectif :** dans cette étape, vous testez comment la solution EAI traite les messages.  
  
 **Objectif :** dans cette étape, vous vérifiez que l’orchestration EAIProcess traite correctement les messages. Pour ce faire, vous allez déposer des exemples de message dans l'emplacement de réception spécifié pour l'application IAE. Lorsque la solution IAE fonctionne correctement, si l'orchestration EAIProcess reçoit un message de l'entrepôt demandant plus de 500 éléments, l'orchestration génère un message de refus de la demande. Si l'orchestration EAIProcess reçoit un message de l'entrepôt demandant moins de 500 éléments, l'orchestration transmet le message au système ERP.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Avant de commencer cette étape, vous devez effectuer [étape 2 : configurer et démarrer l’Application](../core/step-2-configure-and-start-the-application1.md).  
  
## <a name="procedures"></a>Procédures  
  
#### <a name="to-test-the-eai-solution"></a>Pour tester la solution IAE  
  
1.  Ouvrez l’Explorateur Windows et accédez à **C:\BTSTutorials\WareHouse**.  Ce dossier est créé pendant l'installation des fichiers de didacticiels.  
  
2.  Copie **RequestInstance.XML** et collez-le dans **C:\BTSTutorials\WareHouse\Request**.  
  
3.  Lorsque le fichier disparaît, consultez **C:\BTSTutorials\ERP\Request**.  
  
4.  Dans l’Explorateur Windows, accédez à **C:\BTSTutorials\WareHouse**.  
  
5.  Copie **RequestInstance (plus de limite). XML** et collez-le dans **C:\BTSTutorials\WareHouse\Request**.  
  
6.  Lorsque le fichier disparaît, consultez **C:\BTSTutorials\WareHouse\RequestDecline**.  
  
## <a name="what-did-i-just-do"></a>Actions effectuées  
 Vous avez testé la solution IAE en plaçant des exemples de message dans l'emplacement de réception de l'application IAE.  
  
## <a name="see-also"></a>Voir aussi  
 [Étape 1 : Déployer des projets](../core/step-1-deploy-the-projects.md)   
 [Étape 2 : Configurer et démarrer l’Application](../core/step-2-configure-and-start-the-application1.md)