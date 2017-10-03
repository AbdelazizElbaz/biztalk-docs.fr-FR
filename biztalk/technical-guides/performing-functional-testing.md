---
title: "Exécution de tests fonctionnels | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6b9c8c95-5a25-4255-a4c2-e26c67b7a620
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f17c2701d6aa90393b8839bafc933bea2fba5746
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="performing-functional-testing"></a>Exécution de tests fonctionnelles
Test fonctionnel permet de tester un scénario de bout en bout spécifique ou un cas d’usage donné dans le contexte d’une application BizTalk particulier. Un test fonctionnel doit couvrir tous les chemins d’accès possibles via un scénario donné, y compris les chemins d’accès de l’échec. Chemins d’accès de l’échec doivent être évaluées pour vous assurer que l’application traite correctement avec les conditions d’échec.  
  
 Tous les artefacts (par exemple, des orchestrations, les composants de pipeline personnalisés et les assemblys personnalisés) doivent être appelées, et toutes les branches de code à ces objets doivent être testées ainsi. Toutes les combinaisons possibles des messages doivent être testés pour vous assurer que les messages circulent correctement dans le système. Messages non valides doivent être testées ainsi pour vous assurer que l’application réagit de la manière attendue en cas d’erreur et tester le code contenu dans tous les blocs d’exception des orchestrations et des composants personnalisés.  
  
## <a name="automating-functional-testing"></a>Automatisation des tests fonctionnels  
 Vous devez automatiser le test fonctionnel afin qu’il soit rapide, afin qu’il peut être répété et afin qu’elle permet d’éviter les erreurs humaines. **BizUnit** est une infrastructure de test déclaratif conçue pour permettre aux développeurs de rapidement les cas de test de conception. En fait, un fichier de configuration XML appelé des cas de test BizUnit XML est suffisant pour définir la façon dont un test doit être effectué. Pour exécuter des tests, vous pouvez créer votre propre pilote personnalisé ou plus facilement tirer parti de **test Visual Studio unité** ou **NUnit** pour héberger et exécuter vos tests.  
  
 Chaque cas de test BizUnit XML contient trois phases : **TestSetup**, **TestExecution**, et **TestCleanup**. Chacune de ces phases peut contenir zéro ou plusieurs étapes de test. Chaque étape représente une unité de travail et est implémenté comme une classe .NET conçue pour effectuer une tâche particulière. Cette infrastructure offre un ensemble complet de composants. Toutefois, si vous avez besoin de savoir composants spécialisés pour répondre aux besoins spécifiques, vous pouvez écrire vos propres composants d’étape de test personnalisée. Pour plus d’informations sur ces outils, consultez [outils de test](~/technical-guides/tools-for-testing.md).  
  
> [!NOTE]  
>  Utilisation de cet outil n’est pas prise en charge par Microsoft et Microsoft n’apporte aucune garantie quant à l’adéquation de ce programme. L'utilisation de ce programme relève de votre seule responsabilité.  
  
## <a name="see-also"></a>Voir aussi  
 [Liste de vérification : Test opérationnelle](../technical-guides/checklist-testing-operational-readiness.md)