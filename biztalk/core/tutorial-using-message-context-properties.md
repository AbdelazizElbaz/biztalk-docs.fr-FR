---
title: "Didacticiel : Utiliser des propriétés de contexte de Message TIBCO EMS | Documents Microsoft"
description: "guide pas à pas pour utiliser les champs de descripteur de message TIBCO Enterprise Message Service dans l’orchestration de BizTalk Server"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6e52593b-5001-4740-89fb-e003e12d8e69
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9fafde77ad1e6edcae71d2c33a722ac63ab8e75b
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="tutorial-use-tibco-ems-message-descriptors"></a><span data-ttu-id="6b2ba-103">Didacticiel : Descripteurs de message utilisation TIBCO EMS</span><span class="sxs-lookup"><span data-stu-id="6b2ba-103">Tutorial: Use TIBCO EMS message descriptors</span></span>

## <a name="overview"></a><span data-ttu-id="6b2ba-104">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="6b2ba-104">Overview</span></span>
<span data-ttu-id="6b2ba-105">Ce didacticiel présente l'utilisation des propriétés de contexte de BizTalk Server pour définir les champs du descripteur de message de TIBCO Enterprise Message Service (EMS) dans votre orchestration.</span><span class="sxs-lookup"><span data-stu-id="6b2ba-105">This tutorial demonstrates how to use BizTalk Server context properties to set TIBCO Enterprise Message Service (EMS) message descriptor fields in your orchestration.</span></span> <span data-ttu-id="6b2ba-106">Ce didacticiel suppose que vous disposez d'une orchestration qui reçoit un message en provenance d'un port de réception et qui l'envoie vers un port d'envoi lié à l'adaptateur Microsoft BizTalk pour TIBCO Enterprise Message Service.</span><span class="sxs-lookup"><span data-stu-id="6b2ba-106">The tutorial assumes that you have an orchestration that receives a message from a receive port and sends the message to a send port bound to Microsoft BizTalk Adapter for TIBCO Enterprise Message Service.</span></span>  
  
 <span data-ttu-id="6b2ba-107">La procédure suivante décrit la manière de modifier la priorité du message TIBCO EMS en modifiant la valeur de la propriété de contexte TibcoEMS.Priority.</span><span class="sxs-lookup"><span data-stu-id="6b2ba-107">The following procedure demonstrates how to change the priority of the TIBCO EMS message by changing the value of the TibcoEMS.Priority context property.</span></span> <span data-ttu-id="6b2ba-108">Dans BizTalk Server, les messages sont immuables.</span><span class="sxs-lookup"><span data-stu-id="6b2ba-108">In BizTalk Server, messages are immutable.</span></span> <span data-ttu-id="6b2ba-109">Par conséquent, pour modifier une valeur de propriété, vous devez créer et modifier un nouveau message.</span><span class="sxs-lookup"><span data-stu-id="6b2ba-109">Therefore, to change a property value, you must create and modify a new message.</span></span> <span data-ttu-id="6b2ba-110">Pour ce faire, insérez une forme Assignation de message entre les formes Réception et Envoi.</span><span class="sxs-lookup"><span data-stu-id="6b2ba-110">You create and modify the new message by inserting a message assignment shape between the Receive and Send shapes.</span></span> <span data-ttu-id="6b2ba-111">Toutefois, vous devez commencer par référencer le fichier DLL du schéma pour accéder aux propriétés TIBCO EMS.</span><span class="sxs-lookup"><span data-stu-id="6b2ba-111">First, however, you must reference the schema DLL to gain access to the TIBCO EMS properties.</span></span>  
  
## <a name="reference-the-schema-dll"></a><span data-ttu-id="6b2ba-112">Référence le fichier DLL du schéma</span><span class="sxs-lookup"><span data-stu-id="6b2ba-112">Reference the schema DLL</span></span>  
  
1.  <span data-ttu-id="6b2ba-113">Dans Visual Studio, ouvrez votre projet BizTalk Server et ouvrez **l’Explorateur de solutions** .</span><span class="sxs-lookup"><span data-stu-id="6b2ba-113">In Visual Studio, open your BizTalk Server project, and open **Solution Explorer** .</span></span>  
  
2.  <span data-ttu-id="6b2ba-114">Avec le bouton droit **références**, puis sélectionnez **ajouter une référence**.</span><span class="sxs-lookup"><span data-stu-id="6b2ba-114">Right-click **References**, and select **Add Reference**.</span></span>  
  
     <span data-ttu-id="6b2ba-115">La boîte de dialogue **Ajouter une référence** s’affiche.</span><span class="sxs-lookup"><span data-stu-id="6b2ba-115">The **Add Reference** dialog box appears.</span></span>  
  
3.  <span data-ttu-id="6b2ba-116">Cliquez sur le **Parcourir** onglet.</span><span class="sxs-lookup"><span data-stu-id="6b2ba-116">Click the **Browse** tab.</span></span>  
  
     <span data-ttu-id="6b2ba-117">Le **sélectionner le composant** boîte de dialogue s’affiche.</span><span class="sxs-lookup"><span data-stu-id="6b2ba-117">The **Select Component** dialog box appears.</span></span>  
  
4.  <span data-ttu-id="6b2ba-118">Recherchez  **\<TIBCO EMS_Adapter_installation_directory\>\bin**, puis sélectionnez **Microsoft.Adapters.TibcoEMSProperties.dll**.</span><span class="sxs-lookup"><span data-stu-id="6b2ba-118">Locate **\<TIBCO EMS_Adapter_installation_directory\>\bin**, and then select **Microsoft.Adapters.TibcoEMSProperties.dll**.</span></span>  
  
5.  <span data-ttu-id="6b2ba-119">Cliquez sur **Ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="6b2ba-119">Click **Open**.</span></span>  
  
     <span data-ttu-id="6b2ba-120">Le fichier DLL apparaît dans le **composants sélectionnés** dans les **ajouter une référence** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="6b2ba-120">The DLL appears in the **Selected Components** in the **Add Reference** dialog box.</span></span>  
  
6.  <span data-ttu-id="6b2ba-121">Cliquez sur **OK** , puis double-cliquez sur votre orchestration pour accéder au Concepteur d’Orchestration.</span><span class="sxs-lookup"><span data-stu-id="6b2ba-121">Click **OK** and then double-click your orchestration to access the Orchestration Designer.</span></span>  
  
7.  <span data-ttu-id="6b2ba-122">Sur le **vue** menu, pointez sur **autres fenêtres**, puis cliquez sur **Vue Orchestration**.</span><span class="sxs-lookup"><span data-stu-id="6b2ba-122">On the **View** menu, point to **Other Windows**, and then click **Orchestration View**.</span></span>  
  
8.  <span data-ttu-id="6b2ba-123">Dans la vue Orchestration, cliquez sur **Messages** et sélectionnez **nouveau Message**.</span><span class="sxs-lookup"><span data-stu-id="6b2ba-123">In the Orchestration view, right-click **Messages** and select **New Message**.</span></span>  
  
9. <span data-ttu-id="6b2ba-124">Modifier les propriétés de votre nouveau message et attribuer un **Type de Message**.</span><span class="sxs-lookup"><span data-stu-id="6b2ba-124">Edit your new message properties and assign a **Message Type**.</span></span>  
  
     <span data-ttu-id="6b2ba-125">Vous allez affecter Message_1 à Message_2.</span><span class="sxs-lookup"><span data-stu-id="6b2ba-125">You will assign Message_1 to Message_2.</span></span> <span data-ttu-id="6b2ba-126">Vous devez donc attribuer le même type de message aux deux messages.</span><span class="sxs-lookup"><span data-stu-id="6b2ba-126">Therefore, you must assign the same message type to both messages.</span></span>  
  
10. <span data-ttu-id="6b2ba-127">Dans le menu **Affichage** , cliquez sur **Boîte à outils**.</span><span class="sxs-lookup"><span data-stu-id="6b2ba-127">On the **View** menu, click **Toolbox**.</span></span>  
  
11. <span data-ttu-id="6b2ba-128">Faites glisser un **assignation du Message** forme sur votre orchestration où vous souhaitez créer un nouveau message.</span><span class="sxs-lookup"><span data-stu-id="6b2ba-128">Drag a **Message Assignment** shape onto your orchestration where you want to create a new message.</span></span>  
  
12. <span data-ttu-id="6b2ba-129">Modifier la forme externe ConstructMessage_1 et sélectionnez votre nouveau message, Message_2, dans le **Messages construits** propriété.</span><span class="sxs-lookup"><span data-stu-id="6b2ba-129">Edit the outer ConstructMessage_1 shape and select your new message, Message_2, in the **Constructed Messages** property.</span></span>  
  
13. <span data-ttu-id="6b2ba-130">Double-cliquez sur la forme interne MessageAssignment_1.</span><span class="sxs-lookup"><span data-stu-id="6b2ba-130">Double-click the inner MessageAssignment_1 shape.</span></span>  
  
     <span data-ttu-id="6b2ba-131">L'Éditeur d'expression BizTalk s'affiche.</span><span class="sxs-lookup"><span data-stu-id="6b2ba-131">The BizTalk Expression Editor appears.</span></span>  
  
14. <span data-ttu-id="6b2ba-132">Dans l'Éditeur d'expression BizTalk, tapez votre code.</span><span class="sxs-lookup"><span data-stu-id="6b2ba-132">In the BizTalk Expression Editor, type your code.</span></span>  
  
15. <span data-ttu-id="6b2ba-133">Copiez d'abord un message existant puis affectez des valeurs aux propriétés de contexte.</span><span class="sxs-lookup"><span data-stu-id="6b2ba-133">First copy an existing message and then assign values to message context properties.</span></span>  
  
     <span data-ttu-id="6b2ba-134">La syntaxe est `Message(property) = value;`.</span><span class="sxs-lookup"><span data-stu-id="6b2ba-134">The syntax is `Message(property) = value;`.</span></span> <span data-ttu-id="6b2ba-135">Exemple :</span><span class="sxs-lookup"><span data-stu-id="6b2ba-135">For example:</span></span>  
  
    ```  
    Message_2 = Message_1;  
    Message_2( TibcoEMS.Priority) = 6;  
    ```  
  
     <span data-ttu-id="6b2ba-136">Pour obtenir une liste des propriétés prises en charge que vous pouvez utiliser dans vos messages personnalisés, consultez TIBCO EMS.</span><span class="sxs-lookup"><span data-stu-id="6b2ba-136">See TIBCO EMS for a list of supported properties that you can use in your custom message.</span></span>  
  
16. <span data-ttu-id="6b2ba-137">Cliquez sur **OK** pour fermer l’éditeur d’Expression BizTalk et enregistrer votre code.</span><span class="sxs-lookup"><span data-stu-id="6b2ba-137">Click **OK** to close the BizTalk Expression Editor and save your code.</span></span>  
  
17. <span data-ttu-id="6b2ba-138">Cliquez sur la forme envoi et affectez le **Message** être **Message_2**.</span><span class="sxs-lookup"><span data-stu-id="6b2ba-138">Click the Send shape and assign the **Message** to be **Message_2**.</span></span>  
  
18. <span data-ttu-id="6b2ba-139">Vérifiez que les formes dans le reste du flux de messages fonctionnent sur le message approprié.</span><span class="sxs-lookup"><span data-stu-id="6b2ba-139">Verify that the shapes in the rest of the message flow operate on the appropriate message.</span></span>  
  
19. <span data-ttu-id="6b2ba-140">Avec le bouton droit de votre projet dans l’Explorateur de solutions, puis sélectionnez **Build**.</span><span class="sxs-lookup"><span data-stu-id="6b2ba-140">Right-click your project in Solution Explorer, and select **Build**.</span></span>  
  
20. <span data-ttu-id="6b2ba-141">Avec le bouton droit de votre projet et sélectionnez **déployer**.</span><span class="sxs-lookup"><span data-stu-id="6b2ba-141">Right-click your project and select **Deploy**.</span></span>  
  
21. <span data-ttu-id="6b2ba-142">Sélectionnez **lier**, **Enlist**, et **Démarrer** dans l’Explorateur BizTalk pour tester votre orchestration.</span><span class="sxs-lookup"><span data-stu-id="6b2ba-142">Select **Bind**, **Enlist**, and **Start** in the BizTalk Explorer to test your orchestration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b2ba-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6b2ba-143">See Also</span></span>  
[<span data-ttu-id="6b2ba-144">Propriétés de contexte de message TIBCO EMS</span><span class="sxs-lookup"><span data-stu-id="6b2ba-144">TIBCO EMS message context properties</span></span>](../core/message-context-properties-in-biztalk-server.md)