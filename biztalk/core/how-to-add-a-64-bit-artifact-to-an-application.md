---
title: "Comment ajouter un artefact 64 bits à une Application | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- artifacts, 64-bit support
- scripts, 64-bit support
- virtual directories, 64-bit support
- artifacts, applications
- 64-bit support, COM components
- 64-bit support, virtual directories
- applications, artifacts
- 64-bit support, scripts
- 64-bit support, artifacts
- COM components, 64-bit support
- BizTalk Server, 64-bit support
- applications, 64-bit support
ms.assetid: 46aca7d4-c5be-421e-b16d-7f3095c8cc67
caps.latest.revision: "24"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 69707401fee8b7f48b30a79bab166a9f22c29a89
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-a-64-bit-artifact-to-an-application"></a>Ajout d'un artefact 64 bits à une application
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] inclut la prise en charge des applications 64 bits. Autrement dit, vous pouvez ajouter des artefacts 64 bits à une application BizTalk de la même façon que s'il s'agissait d'artefacts 32 bits. Vous êtes toutefois susceptible de rencontrer les problèmes suivants si vous installez les artefacts 64 bits suivants sur un ordinateur 32 bits :  
  
-   **Répertoire virtuel à partir d’un serveur Web qui exécute un processus de travail 64 bits.** le répertoire virtuel sera installé sur l'ordinateur 32 bits, mais risque de ne pas fonctionner correctement. Une erreur d'incompatibilité sera consignée.  
  
-   **Composants non managés de COM ou COM + managés marqués comme 64 bits.** ces composants ne peuvent être installés sur un ordinateur 32 bits.  
  
-   **scripts 64 bits enregistrés en tant que fichiers .exe.** ce type de script peut ne pas correctement fonctionner.  
  
 Pour obtenir des instructions générales sur l’ajout d’artefacts, consultez [comment créer ou ajouter un artefact](../core/how-to-create-or-add-an-artifact.md). Pour obtenir des instructions sur l’ajout de types particuliers d’artefacts, consultez [la gestion des artefacts](../core/managing-artifacts.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Création et modification des Applications BizTalk](../core/creating-and-modifying-biztalk-applications.md)   
 [Comment installer une Application BizTalk](../core/how-to-install-a-biztalk-application.md)