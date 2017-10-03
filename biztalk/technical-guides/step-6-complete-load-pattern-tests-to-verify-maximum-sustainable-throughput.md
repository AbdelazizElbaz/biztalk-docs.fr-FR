---
title: "Étape 6 : Effectuer des Tests de modèle de charge Constant pour vérifier le débit maximal acceptable | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dd790354-be9f-4278-bd15-493eac8970c9
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b6bfc0b9670366ab2f38046fcdc5497234b51ba5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-6-perform-constant-load-pattern-tests-to-verify-maximum-sustainable-throughput"></a>Étape 6 : Effectuer des Tests de modèle de charge Constant pour vérifier le débit maximal acceptable
Charger lorsque le test d’une solution BizTalk Server à l’aide de Visual Studio 2010, un test de modèle de charge constant doit être effectué une fois l’approximative maximale acceptable débit acceptable de la solution est déterminé comme décrit dans [étape 5 : exécuter l’étape charger Les Tests pour déterminer le débit maximal acceptable de modèle](../technical-guides/step-5-complete-step-load-tests-to-determine-maximum-sustainable-throughput.md). Cela doit être effectuée pour confirmer que le débit maximal acceptable est en fait acceptable au fil du temps et afin de créer un test de charge de ligne de base progresser à évaluer les effets de n’importe quel réglage des performances pour l’application BizTalk Server ou l’environnement.  
  
## <a name="create-and-run-a-constant-load-pattern-test"></a>Créer et exécuter un Test de modèle de charge Constant  
 Le moyen le plus simple pour créer un test de modèle de charge Constant qui utilise la même la combinaison de tests, les ensembles de compteurs et les mappages des ensembles de compteurs utilisés par le test de modèle de charge étape consiste à simplement enregistrer le test de modèle de charge dans l’étape « BTS_Messaging_Step.loadtest » en tant que « BTS_Messaging_ Constant.LoadTest », puis rendez certaines modifications apportées à « BTS_Messaging_Constant.loadtest ». Suivez ces étapes pour créer un modèle de charge Constant de test qui est basé sur le test de modèle de charge étape existant :  
  
1.  Ouvrez BTS_Messaging_Step.loadtest si elle n’est pas déjà ouvert.  
  
2.  Cliquez sur **fichier** et sélectionnez **enregistrer LoadTests\BTS_Messaging_Step.loadtest sous**.  
  
3.  Dans le **enregistrer le fichier sous** boîte de dialogue, à côté **nom de fichier**, entrez C:\Projects\LoadTest\BTSLoad\LoadTests\BTS_Messaging_Constant.loadtest, puis sur **enregistrer**.  
  
4.  Dans l’éditeur de Test de charge, renommez le scénario **BTS_Messaging_Step** à **BTS_Messaging_Constant**. Le nom du scénario s’affiche directement sous le **scénarios** dossier.  
  
5.  Laissez les valeurs pour **combinaison de tests** et **la combinaison de réseaux** inchangée mais sélectionnez **modèle de charge étape**.  
  
6.  Avec le bouton droit **modèle de charge étape** et sélectionnez **propriétés**.  
  
7.  Dans le **propriétés** section sous **modèle de charge** cliquez sur la liste déroulante en regard **modèle** et modifier le modèle à partir de **étape** à **Constante**.  
  
8.  Dans le **propriétés** section sous **paramètres**, modifiez la valeur de **constante du nombre d’utilisateurs** à une valeur légèrement inférieur au nombre d’utilisateurs à laquelle le modèle de charge par étape test est devenu inacceptables (autrement dit, la valeur de la **BizTalk:Messaging\Documents reçus par seconde** a commencé à constamment dépasser la valeur de **BizTalk:Messaging\Documents traitées par seconde** et la valeur de la **BizTalk : zone : général Counters\Spool taille** a commencé à augmenter unbounded).  
  
9. Sous le **paramètres d’exécution** dossier, avec le bouton droit **Setting1 d’exécuter [actif]** et sélectionnez **propriétés**.  
  
10. Défilement vers le bas de la liste des propriétés pour le **minutage** section et entrez une valeur pour **durée d’exécution** d’au moins 10 minutes (00 : 10:00) et vérifiez que la valeur de **taux d’échantillonnage** est toujours définie à 5 secondes (00 : 00:05).  
  
11. Démarrer le test de charge en cliquant sur le nom du test (par exemple, BTS_Messaging_Constant), puis le **exécuter le Test** option de menu.