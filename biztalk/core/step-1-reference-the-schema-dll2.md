---
title: "Étape 1 : Référencer le schéma DLL2 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1db92227-6164-42b9-b60c-12dd2cae46e2
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a5b009e2c79c0ea68030561c51e3a90ceef24eba
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-1-reference-the-schema-dll"></a><span data-ttu-id="9b789-102">Étape 1 : Faire référence à la DLL du schéma</span><span class="sxs-lookup"><span data-stu-id="9b789-102">Step 1: Reference the Schema DLL</span></span>
<span data-ttu-id="9b789-103">Dans BizTalk, les messages sont immuables.</span><span class="sxs-lookup"><span data-stu-id="9b789-103">In BizTalk, messages are immutable.</span></span> <span data-ttu-id="9b789-104">C'est pourquoi, pour modifier une valeur de propriété, vous devez créer et modifier un nouveau message.</span><span class="sxs-lookup"><span data-stu-id="9b789-104">Therefore, to change a property value you must create and modify a new message.</span></span> <span data-ttu-id="9b789-105">Pour ce faire, insérez une forme Assignation de message entre les formes Réception et Envoi.</span><span class="sxs-lookup"><span data-stu-id="9b789-105">You create and modify the new message by inserting a message assignment shape between the Receive and Send shapes.</span></span>  
  
 <span data-ttu-id="9b789-106">Tout d’abord, toutefois, vous devez référencer la fichier DLL pour accéder à la J.D. du schéma</span><span class="sxs-lookup"><span data-stu-id="9b789-106">First, however, you must reference the schema DLL to gain access to the J.D.</span></span> <span data-ttu-id="9b789-107">Propriétés de contexte Edwards.</span><span class="sxs-lookup"><span data-stu-id="9b789-107">Edwards context properties.</span></span>  
  
### <a name="to-reference-the-schema-dll"></a><span data-ttu-id="9b789-108">Pour référencer le fichier DLL du schéma</span><span class="sxs-lookup"><span data-stu-id="9b789-108">To reference the schema DLL</span></span>  
  
1.  <span data-ttu-id="9b789-109">Créez un dossier de travail (par exemple, c:\class\JDE\BeginDoc) pour votre projet, ainsi qu'un dossier dans lequel vous allez placer le fichier XML test (par exemple, c:\class\JDE\input).</span><span class="sxs-lookup"><span data-stu-id="9b789-109">Create a working folder, for example, c:\class\JDE\BeginDoc, for your project and a folder in which you will put the test XML, for example, c:\class\JDE\input.</span></span>  
  
2.  <span data-ttu-id="9b789-110">Créer un Port d’envoi statique avec sollicitation-réponse pour envoyer la demande vers J.D.</span><span class="sxs-lookup"><span data-stu-id="9b789-110">Create a Static Solicit-Response Send Port to send the request to J.D.</span></span> <span data-ttu-id="9b789-111">Edwards OneWorld.</span><span class="sxs-lookup"><span data-stu-id="9b789-111">Edwards OneWorld.</span></span>  
  
     ![](../core/media/jde-example-2waysendport-ow.gif "JDE_example_2waysendport_OW")  
  
3.  <span data-ttu-id="9b789-112">Dans l'Éditeur de solution, cliquez avec le bouton droit sur votre projet.</span><span class="sxs-lookup"><span data-stu-id="9b789-112">In the Solution Editor, right-click your project.</span></span>  
  
    1.  <span data-ttu-id="9b789-113">Sélectionnez **ajouter**, sélectionnez **ajouter les éléments générés**, puis cliquez sur **ajouter un adaptateur**.</span><span class="sxs-lookup"><span data-stu-id="9b789-113">Select **Add**, select **Add Generated Items**, and then click **Add Adapter**.</span></span>  
  
    2.  <span data-ttu-id="9b789-114">Sélectionnez l’adaptateur Microsoft BizTalk pour J.D.</span><span class="sxs-lookup"><span data-stu-id="9b789-114">Select the Microsoft BizTalk Adapter for J.D.</span></span> <span data-ttu-id="9b789-115">Edwards OneWorld et le port que vous venez de créer.</span><span class="sxs-lookup"><span data-stu-id="9b789-115">Edwards OneWorld and the port you just created.</span></span>  
  
    3.  <span data-ttu-id="9b789-116">Dans le **Assistant Ajout d’adaptateur**, sélectionnez **CSALES\B4200310**.</span><span class="sxs-lookup"><span data-stu-id="9b789-116">In the **Add Adapter Wizard**, select **CSALES\B4200310**.</span></span>  
  
    4.  <span data-ttu-id="9b789-117">Cliquez sur **Terminer** pour générer le schéma qui contient le format du message.</span><span class="sxs-lookup"><span data-stu-id="9b789-117">Click **Finish** to generate the schema containing the format for the Message.</span></span>  
  
     ![](../core/media/jde-add-adapter-wizard.gif "JDE_add_adapter_wizard")  
  
4.  <span data-ttu-id="9b789-118">Dans Visual Studio, ouvrez l'Explorateur de solutions.</span><span class="sxs-lookup"><span data-stu-id="9b789-118">In Visual Studio, open the Solution Explorer.</span></span>  
  
5.  <span data-ttu-id="9b789-119">Avec le bouton droit **références**, puis sélectionnez **ajouter une référence**.</span><span class="sxs-lookup"><span data-stu-id="9b789-119">Right-click **References**, and then select **Add Reference**.</span></span>  
  
6.  <span data-ttu-id="9b789-120">Sur le **ajouter une référence** , cliquez sur le **Parcourir** bouton.</span><span class="sxs-lookup"><span data-stu-id="9b789-120">On the **Add Reference** screen, click the **Browse** button.</span></span>  
  
     ![](../core/media/jde-add-reference-dll.gif "JDE_add_reference_dll")  
  
7.  <span data-ttu-id="9b789-121">Sur le **sélectionner le composant** écran, accédez à %SystemDrive%\Program Files\Common Files\Microsoft BizTalk Adapters for Enterprise Applications\bin.</span><span class="sxs-lookup"><span data-stu-id="9b789-121">On the **Select Component** screen, navigate to %SystemDrive%\Program Files\Common Files\Microsoft BizTalk Adapters for Enterprise Applications\bin.</span></span>  
  
8.  <span data-ttu-id="9b789-122">Sélectionnez **Microsoft.Adapters.JDEProperties.dll**, puis cliquez sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="9b789-122">Select **Microsoft.Adapters.JDEProperties.dll**, and then click **Open**.</span></span>  
  
9. <span data-ttu-id="9b789-123">Sur le **ajouter une référence** apparaît, la DLL dans le **composants sélectionnés** section.</span><span class="sxs-lookup"><span data-stu-id="9b789-123">On the **Add Reference** screen, the DLL appears in the **Selected Components** section.</span></span>  
  
     ![](../core/media/jde-properties-selection.gif "JDE_properties_selection")  
  
10. <span data-ttu-id="9b789-124">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="9b789-124">Click **OK**.</span></span>  
  
11. <span data-ttu-id="9b789-125">Double-cliquez sur votre orchestration pour accéder au Concepteur d'orchestration.</span><span class="sxs-lookup"><span data-stu-id="9b789-125">Double-click your orchestration to access the Orchestration Designer.</span></span>  
  
     <span data-ttu-id="9b789-126">\- - OU -</span><span class="sxs-lookup"><span data-stu-id="9b789-126">\- OR -</span></span>  
  
     <span data-ttu-id="9b789-127">Sélectionnez **vue**, sélectionnez **autres fenêtres**, puis cliquez sur **Vue Orchestration**.</span><span class="sxs-lookup"><span data-stu-id="9b789-127">Select **View**, select **Other Windows**, and then click **Orchestration View**.</span></span>  
  
     <span data-ttu-id="9b789-128">La vue Orchestration est affichée.</span><span class="sxs-lookup"><span data-stu-id="9b789-128">The Orchestration View appears.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b789-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9b789-129">See Also</span></span>  
 <span data-ttu-id="9b789-130">[Étape 2 : Créer l’Orchestration](../core/step-2-create-the-orchestration1.md) </span><span class="sxs-lookup"><span data-stu-id="9b789-130">[Step 2: Create the Orchestration](../core/step-2-create-the-orchestration1.md) </span></span>  
 <span data-ttu-id="9b789-131">[Étape 3 : Créer et exécuter le projet](../core/step-3-complete-and-run-the-project2.md) </span><span class="sxs-lookup"><span data-stu-id="9b789-131">[Step 3: Complete and Run the Project](../core/step-3-complete-and-run-the-project2.md) </span></span>  
 [<span data-ttu-id="9b789-132">Étape 4 : Créer un exemple XML BeginDoc</span><span class="sxs-lookup"><span data-stu-id="9b789-132">Step 4: Create a Sample XML BeginDoc</span></span>](../core/step-4-create-a-sample-xml-begindoc1.md)