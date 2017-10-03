---
title: "Étape 1 : Référencer le schéma DLL1 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 47e4b773-e484-4931-9ab2-b8dd0080ea1c
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a9c2d5051c7dfd3c0f971b34922ca4e5747117c9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-1-reference-the-schema-dll"></a><span data-ttu-id="de9ba-102">Étape 1 : Faire référence à la DLL du schéma</span><span class="sxs-lookup"><span data-stu-id="de9ba-102">Step 1: Reference the Schema DLL</span></span>
<span data-ttu-id="de9ba-103">Dans BizTalk, les messages sont immuables.</span><span class="sxs-lookup"><span data-stu-id="de9ba-103">In BizTalk, messages are immutable.</span></span> <span data-ttu-id="de9ba-104">C'est pourquoi, pour modifier une valeur de propriété, vous devez créer et modifier un nouveau message.</span><span class="sxs-lookup"><span data-stu-id="de9ba-104">Therefore, to change a property value you must create and modify a new message.</span></span> <span data-ttu-id="de9ba-105">Pour ce faire, insérez une forme Assignation de message entre les formes Réception et Envoi.</span><span class="sxs-lookup"><span data-stu-id="de9ba-105">You create and modify the new message by inserting a message assignment shape between the Receive and Send shapes.</span></span>  
  
 <span data-ttu-id="de9ba-106">Tout d’abord, toutefois, vous devez référencer la fichier DLL pour accéder à la J.D. du schéma</span><span class="sxs-lookup"><span data-stu-id="de9ba-106">First, however, you must reference the schema DLL to gain access to the J.D.</span></span> <span data-ttu-id="de9ba-107">Propriétés de contexte Edwards EnterpriseOne.</span><span class="sxs-lookup"><span data-stu-id="de9ba-107">Edwards EnterpriseOne context properties.</span></span>  
  
### <a name="to-reference-the-schema-dll"></a><span data-ttu-id="de9ba-108">Pour référencer le fichier DLL du schéma</span><span class="sxs-lookup"><span data-stu-id="de9ba-108">To reference the schema DLL</span></span>  
  
1.  <span data-ttu-id="de9ba-109">Créez un dossier de travail (par exemple, c:\class\JDE\BeginDoc) pour votre projet, ainsi qu'un dossier dans lequel vous allez placer le fichier XML test (par exemple, c:\class\JDE\input).</span><span class="sxs-lookup"><span data-stu-id="de9ba-109">Create a working folder, for example, c:\class\JDE\BeginDoc, for your project and a folder in which you will put the test XML, for example, c:\class\JDE\input.</span></span>  
  
2.  <span data-ttu-id="de9ba-110">Créer un Port d’envoi statique avec sollicitation-réponse pour envoyer la demande vers J.D.</span><span class="sxs-lookup"><span data-stu-id="de9ba-110">Create a Static Solicit-Response Send Port to send the request to J.D.</span></span> <span data-ttu-id="de9ba-111">Edwards EnterpriseOne.</span><span class="sxs-lookup"><span data-stu-id="de9ba-111">Edwards EnterpriseOne.</span></span>  
  
     <span data-ttu-id="de9ba-112">![Les propriétés du Transport JDOneWorld](../core/media/example-2waysendport-ow.gif "example_2waysendport_OW")</span><span class="sxs-lookup"><span data-stu-id="de9ba-112">![JDOneWorld Transport Properties](../core/media/example-2waysendport-ow.gif "example_2waysendport_OW")</span></span>  
  
3.  <span data-ttu-id="de9ba-113">Dans l'Éditeur de solution, cliquez avec le bouton droit sur votre projet.</span><span class="sxs-lookup"><span data-stu-id="de9ba-113">In the Solution Editor, right-click your project.</span></span>  
  
    1.  <span data-ttu-id="de9ba-114">Sélectionnez **ajouter**, sélectionnez **ajouter les éléments générés**, puis cliquez sur **ajouter un adaptateur**.</span><span class="sxs-lookup"><span data-stu-id="de9ba-114">Select **Add**, select **Add Generated Items**, and then click **Add Adapter**.</span></span>  
  
    2.  <span data-ttu-id="de9ba-115">Sélectionnez l’adaptateur Microsoft BizTalk pour J.D.</span><span class="sxs-lookup"><span data-stu-id="de9ba-115">Select the Microsoft BizTalk Adapter for J.D.</span></span> <span data-ttu-id="de9ba-116">Edwards EnterpriseOne et le port que vous venez de créer.</span><span class="sxs-lookup"><span data-stu-id="de9ba-116">Edwards EnterpriseOne and the port you just created.</span></span>  
  
    3.  <span data-ttu-id="de9ba-117">Dans le **Assistant Ajout d’adaptateur**, sélectionnez **CSALES\B4200310**.</span><span class="sxs-lookup"><span data-stu-id="de9ba-117">In the **Add Adapter Wizard**, select **CSALES\B4200310**.</span></span>  
  
    4.  <span data-ttu-id="de9ba-118">Cliquez sur **Terminer** pour générer le schéma qui contient le format du message.</span><span class="sxs-lookup"><span data-stu-id="de9ba-118">Click **Finish** to generate the schema containing the format for the Message.</span></span>  
  
     <span data-ttu-id="de9ba-119">![Assistant Ajout d’adaptateur](../core/media/add-adapter-wizard.gif "add_adapter_wizard")</span><span class="sxs-lookup"><span data-stu-id="de9ba-119">![Add Adapter Wizard](../core/media/add-adapter-wizard.gif "add_adapter_wizard")</span></span>  
  
4.  <span data-ttu-id="de9ba-120">Dans Visual Studio, ouvrez l'Explorateur de solutions.</span><span class="sxs-lookup"><span data-stu-id="de9ba-120">In Visual Studio, open the Solution Explorer.</span></span>  
  
5.  <span data-ttu-id="de9ba-121">Avec le bouton droit **références**, puis sélectionnez **ajouter une référence**.</span><span class="sxs-lookup"><span data-stu-id="de9ba-121">Right-click **References**, and then select **Add Reference**.</span></span>  
  
6.  <span data-ttu-id="de9ba-122">Sur le **ajouter une référence** , cliquez sur le **Parcourir** bouton.</span><span class="sxs-lookup"><span data-stu-id="de9ba-122">On the **Add Reference** screen, click the **Browse** button.</span></span>  
  
7.  <span data-ttu-id="de9ba-123">Sur le **sélectionner le composant** écran, accédez à %SystemDrive%\Program Files\Common Files\Microsoft BizTalk Adapters for Enterprise Applications\bin.</span><span class="sxs-lookup"><span data-stu-id="de9ba-123">On the **Select Component** screen, navigate to %SystemDrive%\Program Files\Common Files\Microsoft BizTalk Adapters for Enterprise Applications\bin.</span></span>  
  
8.  <span data-ttu-id="de9ba-124">Sélectionnez **Microsoft.Adapters.JDEProperties.dll**, puis cliquez sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="de9ba-124">Select **Microsoft.Adapters.JDEProperties.dll**, and then click **Open**.</span></span>  
  
9. <span data-ttu-id="de9ba-125">Sur le **ajouter une référence** apparaît, la DLL dans le **composants sélectionnés** section.</span><span class="sxs-lookup"><span data-stu-id="de9ba-125">On the **Add Reference** screen, the DLL appears in the **Selected Components** section.</span></span>  
  
     <span data-ttu-id="de9ba-126">![Écran de sélection de propriétés](../core/media/properties-selection.gif "properties_selection")</span><span class="sxs-lookup"><span data-stu-id="de9ba-126">![Properties Selection screen](../core/media/properties-selection.gif "properties_selection")</span></span>  
  
10. <span data-ttu-id="de9ba-127">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="de9ba-127">Click **OK**.</span></span>  
  
11. <span data-ttu-id="de9ba-128">Double-cliquez sur votre orchestration pour accéder au Concepteur d'orchestration.</span><span class="sxs-lookup"><span data-stu-id="de9ba-128">Double-click your orchestration to access the Orchestration Designer.</span></span>  
  
     <span data-ttu-id="de9ba-129">\- - OU -</span><span class="sxs-lookup"><span data-stu-id="de9ba-129">\- OR -</span></span>  
  
     <span data-ttu-id="de9ba-130">Sélectionnez **vue**, sélectionnez **autres fenêtres**, puis cliquez sur **Vue Orchestration**.</span><span class="sxs-lookup"><span data-stu-id="de9ba-130">Select **View**, select **Other Windows**, and then click **Orchestration View**.</span></span>  
  
     <span data-ttu-id="de9ba-131">La vue Orchestration est affichée.</span><span class="sxs-lookup"><span data-stu-id="de9ba-131">The Orchestration View appears.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de9ba-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="de9ba-132">See Also</span></span>  
 <span data-ttu-id="de9ba-133">[Étape 2 : Créer l’Orchestration](../core/step-2-create-the-orchestration2.md) </span><span class="sxs-lookup"><span data-stu-id="de9ba-133">[Step 2: Create the Orchestration](../core/step-2-create-the-orchestration2.md) </span></span>  
 <span data-ttu-id="de9ba-134">[Tâche 4 : Configurer la forme construire un Message](../core/task-4-configure-the-construct-message-shape1.md) </span><span class="sxs-lookup"><span data-stu-id="de9ba-134">[Task 4: Configure the Construct Message Shape](../core/task-4-configure-the-construct-message-shape1.md) </span></span>  
 <span data-ttu-id="de9ba-135">[Tâche 5 : Configurer la forme Transformer](../core/task-5-configure-the-transform-shape2.md) </span><span class="sxs-lookup"><span data-stu-id="de9ba-135">[Task 5: Configure the Transform Shape](../core/task-5-configure-the-transform-shape2.md) </span></span>  
 <span data-ttu-id="de9ba-136">[Étape 3 : Créer et exécuter le projet](../core/step-3-complete-and-run-the-project1.md) </span><span class="sxs-lookup"><span data-stu-id="de9ba-136">[Step 3: Complete and Run the Project](../core/step-3-complete-and-run-the-project1.md) </span></span>  
 [<span data-ttu-id="de9ba-137">Étape 4 : Créer un exemple XML BeginDoc</span><span class="sxs-lookup"><span data-stu-id="de9ba-137">Step 4: Create a Sample XML BeginDoc</span></span>](../core/step-4-create-a-sample-xml-begindoc2.md)