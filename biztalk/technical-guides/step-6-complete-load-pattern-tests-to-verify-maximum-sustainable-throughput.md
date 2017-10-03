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
# <a name="step-6-perform-constant-load-pattern-tests-to-verify-maximum-sustainable-throughput"></a><span data-ttu-id="32372-102">Étape 6 : Effectuer des Tests de modèle de charge Constant pour vérifier le débit maximal acceptable</span><span class="sxs-lookup"><span data-stu-id="32372-102">Step 6: Perform Constant Load Pattern Tests to Verify Maximum Sustainable Throughput</span></span>
<span data-ttu-id="32372-103">Charger lorsque le test d’une solution BizTalk Server à l’aide de Visual Studio 2010, un test de modèle de charge constant doit être effectué une fois l’approximative maximale acceptable débit acceptable de la solution est déterminé comme décrit dans [étape 5 : exécuter l’étape charger Les Tests pour déterminer le débit maximal acceptable de modèle](../technical-guides/step-5-complete-step-load-tests-to-determine-maximum-sustainable-throughput.md).</span><span class="sxs-lookup"><span data-stu-id="32372-103">When load testing a BizTalk Server solution using Visual Studio 2010, a constant load pattern test should be performed once the approximate Maximum Sustainable Throughput (MST) of the solution is determined as described in [Step 5: Perform Step Load Pattern Tests to Determine Maximum Sustainable Throughput](../technical-guides/step-5-complete-step-load-tests-to-determine-maximum-sustainable-throughput.md).</span></span> <span data-ttu-id="32372-104">Cela doit être effectuée pour confirmer que le débit maximal acceptable est en fait acceptable au fil du temps et afin de créer un test de charge de ligne de base progresser à évaluer les effets de n’importe quel réglage des performances pour l’application BizTalk Server ou l’environnement.</span><span class="sxs-lookup"><span data-stu-id="32372-104">This should be done to confirm that the MST is in fact sustainable over time and also so as to create a baseline load test moving forward to evaluate the effects of any performance tuning applied to the BizTalk Server application or environment.</span></span>  
  
## <a name="create-and-run-a-constant-load-pattern-test"></a><span data-ttu-id="32372-105">Créer et exécuter un Test de modèle de charge Constant</span><span class="sxs-lookup"><span data-stu-id="32372-105">Create and run a Constant Load Pattern Test</span></span>  
 <span data-ttu-id="32372-106">Le moyen le plus simple pour créer un test de modèle de charge Constant qui utilise la même la combinaison de tests, les ensembles de compteurs et les mappages des ensembles de compteurs utilisés par le test de modèle de charge étape consiste à simplement enregistrer le test de modèle de charge dans l’étape « BTS_Messaging_Step.loadtest » en tant que « BTS_Messaging_ Constant.LoadTest », puis rendez certaines modifications apportées à « BTS_Messaging_Constant.loadtest ».</span><span class="sxs-lookup"><span data-stu-id="32372-106">The easiest way to create a Constant Load Pattern test that uses the same Test Mix, Counter Sets, and Counter Set Mappings used by the Step Load Pattern test is to simply save the Step Load Pattern test “BTS_Messaging_Step.loadtest” as “BTS_Messaging_Constant.loadtest” and then make some changes to “BTS_Messaging_Constant.loadtest”.</span></span> <span data-ttu-id="32372-107">Suivez ces étapes pour créer un modèle de charge Constant de test qui est basé sur le test de modèle de charge étape existant :</span><span class="sxs-lookup"><span data-stu-id="32372-107">Follow these steps to create a Constant Load Pattern test that is based upon the existing Step Load Pattern test:</span></span>  
  
1.  <span data-ttu-id="32372-108">Ouvrez BTS_Messaging_Step.loadtest si elle n’est pas déjà ouvert.</span><span class="sxs-lookup"><span data-stu-id="32372-108">Open BTS_Messaging_Step.loadtest if it is not already open.</span></span>  
  
2.  <span data-ttu-id="32372-109">Cliquez sur **fichier** et sélectionnez **enregistrer LoadTests\BTS_Messaging_Step.loadtest sous**.</span><span class="sxs-lookup"><span data-stu-id="32372-109">Click **File** and select **Save LoadTests\BTS_Messaging_Step.loadtest As**.</span></span>  
  
3.  <span data-ttu-id="32372-110">Dans le **enregistrer le fichier sous** boîte de dialogue, à côté **nom de fichier**, entrez C:\Projects\LoadTest\BTSLoad\LoadTests\BTS_Messaging_Constant.loadtest, puis sur **enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="32372-110">In the **Save File As** dialog box, next to **File name**, enter C:\Projects\LoadTest\BTSLoad\LoadTests\BTS_Messaging_Constant.loadtest and then click **Save**.</span></span>  
  
4.  <span data-ttu-id="32372-111">Dans l’éditeur de Test de charge, renommez le scénario **BTS_Messaging_Step** à **BTS_Messaging_Constant**.</span><span class="sxs-lookup"><span data-stu-id="32372-111">In the Load Test Editor, rename the scenario **BTS_Messaging_Step** to **BTS_Messaging_Constant**.</span></span> <span data-ttu-id="32372-112">Le nom du scénario s’affiche directement sous le **scénarios** dossier.</span><span class="sxs-lookup"><span data-stu-id="32372-112">The scenario name is displayed directly under the **Scenarios** folder.</span></span>  
  
5.  <span data-ttu-id="32372-113">Laissez les valeurs pour **combinaison de tests** et **la combinaison de réseaux** inchangée mais sélectionnez **modèle de charge étape**.</span><span class="sxs-lookup"><span data-stu-id="32372-113">Leave the values for **Test Mix** and **Network Mix** unchanged but click to select **Step Load Pattern**.</span></span>  
  
6.  <span data-ttu-id="32372-114">Avec le bouton droit **modèle de charge étape** et sélectionnez **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="32372-114">Right-click **Step Load Pattern** and select **Properties**.</span></span>  
  
7.  <span data-ttu-id="32372-115">Dans le **propriétés** section sous **modèle de charge** cliquez sur la liste déroulante en regard **modèle** et modifier le modèle à partir de **étape** à **Constante**.</span><span class="sxs-lookup"><span data-stu-id="32372-115">In the **Properties** section, under **Load Pattern** click the dropdown list next to **Pattern** and change the Pattern from **Step** to **Constant**.</span></span>  
  
8.  <span data-ttu-id="32372-116">Dans le **propriétés** section sous **paramètres**, modifiez la valeur de **constante du nombre d’utilisateurs** à une valeur légèrement inférieur au nombre d’utilisateurs à laquelle le modèle de charge par étape test est devenu inacceptables (autrement dit, la valeur de la **BizTalk:Messaging\Documents reçus par seconde** a commencé à constamment dépasser la valeur de **BizTalk:Messaging\Documents traitées par seconde** et la valeur de la **BizTalk : zone : général Counters\Spool taille** a commencé à augmenter unbounded).</span><span class="sxs-lookup"><span data-stu-id="32372-116">In the **Properties** section, under **Parameters**, change the value for **Constant User Count** to a value slightly less than the number of users at which the Step Load Pattern test was becoming unsustainable (i.e. the value for the **BizTalk:Messaging\Documents received per/Sec** began to consistently exceed the value for **BizTalk:Messaging\Documents processed/Sec** and the value of the **BizTalk:Message Box:General Counters\Spool Size** began to increase unbounded).</span></span>  
  
9. <span data-ttu-id="32372-117">Sous le **paramètres d’exécution** dossier, avec le bouton droit **Setting1 d’exécuter [actif]** et sélectionnez **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="32372-117">Under the **Run Settings** folder, right-click **Run Setting1 [Active]** and select **Properties**.</span></span>  
  
10. <span data-ttu-id="32372-118">Défilement vers le bas de la liste des propriétés pour le **minutage** section et entrez une valeur pour **durée d’exécution** d’au moins 10 minutes (00 : 10:00) et vérifiez que la valeur de **taux d’échantillonnage** est toujours définie à 5 secondes (00 : 00:05).</span><span class="sxs-lookup"><span data-stu-id="32372-118">Scroll down the list of properties to the **Timing** section and enter a value for **Run Duration** of at least 10 minutes (00:10:00) and verify that the value for **Sample Rate** is still set to 5 seconds (00:00:05).</span></span>  
  
11. <span data-ttu-id="32372-119">Démarrer le test de charge en cliquant sur le nom du test (par exemple, BTS_Messaging_Constant), puis le **exécuter le Test** option de menu.</span><span class="sxs-lookup"><span data-stu-id="32372-119">Start the load test by right-clicking the test name (e.g. BTS_Messaging_Constant) and then click the **Run Test** menu option.</span></span>