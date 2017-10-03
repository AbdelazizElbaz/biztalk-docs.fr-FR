---
title: "Comment créer des Orchestrations | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- building, orchestrations
- building, solutions
- building, projects
- solutions, building
- projects, building
- orchestrations, building
ms.assetid: f12d5da0-fbae-4f0e-85bf-1ca2e9bf7d62
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 79e91ec6ecfa061aa4621effba9a1f868cad5d96
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-build-orchestrations"></a>Création d'orchestrations
Après avoir terminé le dessin d'une orchestration, vous construisez votre projet BizTalk dans un assembly qui encapsule une orchestration exécutable.  
  
 Pendant le processus de construction, le Concepteur d'Orchestration BizTalk examine chaque forme pour déterminer si elle est complète et correcte, et signale une erreur dans la liste des tâches si ce n'est pas le cas.  
  
 Il existe plusieurs options de construction dans Visual Studio :  
  
-   Vous pouvez construire l'ensemble de la solution dans laquelle votre orchestration réside.  
  
-   Vous pouvez construire un projet unique au sein de la solution.  
  
-   Vous pouvez ignorer l'orchestration lorsque vous construisez le projet ou la solution.  
  
 Si vous voulez construire d'autres composants, dont d'autres orchestrations, mais pas une orchestration en particulier, vous pouvez indiquer dans les propriétés de fichier du fichier .odx de cette orchestration que vous ne souhaitez pas la construire. Elle sera alors ignorée.  
  
### <a name="to-build-an-orchestration"></a>Pour construire une orchestration  
  
-   Après avoir créé votre orchestration, vous devez construire le projet BizTalk qui la contient avant de pouvoir la tester ou l'utiliser. Vous pouvez construire l'ensemble de la solution ou un projet unique au sein de la solution.  
  
### <a name="to-build-a-solution"></a>Pour construire une solution  
  
-   Dans l’Explorateur de solutions, cliquez sur la solution et sélectionnez **générer la Solution**.  
  
### <a name="to-build-a-project"></a>Pour construire un projet  
  
-   Cliquez sur un projet et sélectionnez **Build**.  
  
### <a name="to-build-a-project-or-solution-without-compiling-a-particular-orchestration"></a>Pour générer un projet ou une solution sans compiler une orchestration en particulier  
  
-   Cliquez sur le fichier .odx correspondant à l’orchestration et dans la fenêtre Propriétés, cliquez sur le **Action de génération** et sélectionnez **aucun**.