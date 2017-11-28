---
title: "Tâche 4 : Configurer la Shape2 Message construction | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 43a7b912-0293-41be-b992-309eca550801
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6616fec48eb0915527a95f94992e4bda838e9d37
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="task-4-configure-the-construct-message-shape"></a><span data-ttu-id="6aa76-102">Tâche 4 : Configurer la forme construire un Message</span><span class="sxs-lookup"><span data-stu-id="6aa76-102">Task 4: Configure the Construct Message Shape</span></span>
<span data-ttu-id="6aa76-103">La forme Construire un message conserve les assignations des messages avec les instructions relatives aux codes Begin, Edit et End Doc.</span><span class="sxs-lookup"><span data-stu-id="6aa76-103">The Construct Messages hold messages assignments with the instructions for the Begin, Edit, and End Doc code.</span></span>  
  
 <span data-ttu-id="6aa76-104">La procédure suivante permet de configurer la forme Construire un message.</span><span class="sxs-lookup"><span data-stu-id="6aa76-104">Use the following procedure to configure the Construct Message shape.</span></span>  
  
### <a name="to-configure-the-construct-message-shape"></a><span data-ttu-id="6aa76-105">Pour configurer la forme Construire un message</span><span class="sxs-lookup"><span data-stu-id="6aa76-105">To configure the Construct Message shape</span></span>  
  
1.  <span data-ttu-id="6aa76-106">Faites glisser une forme Construire un message entre ReceiveBeginDoc et SendBeginDoc.</span><span class="sxs-lookup"><span data-stu-id="6aa76-106">Drag a Construct Message shape inbetween ReceiveBeginDoc and SendBeginDoc.</span></span>  
  
    -   <span data-ttu-id="6aa76-107">**Messages construits :** BeginDocSessionMsg</span><span class="sxs-lookup"><span data-stu-id="6aa76-107">**Messages Constructed:** BeginDocSessionMsg</span></span>  
  
    -   <span data-ttu-id="6aa76-108">**Nom :** ConstructBeginDocMessageWithSession</span><span class="sxs-lookup"><span data-stu-id="6aa76-108">**Name:** ConstructBeginDocMessageWithSession</span></span>  
  
    1.  <span data-ttu-id="6aa76-109">Faites glisser une forme Assignation du message dans l'orchestration où vous souhaitez créer un message.</span><span class="sxs-lookup"><span data-stu-id="6aa76-109">Drag a Message Assignment shape into your orchestration where you want to create a new message.</span></span>  
  
    2.  <span data-ttu-id="6aa76-110">Double-cliquez sur la forme interne MessageAssignment_1.</span><span class="sxs-lookup"><span data-stu-id="6aa76-110">Double-click the inner MessageAssignment_1 shape.</span></span>  
  
         <span data-ttu-id="6aa76-111">L'Éditeur d'expression BizTalk s'affiche.</span><span class="sxs-lookup"><span data-stu-id="6aa76-111">The BizTalk Expression Editor appears.</span></span>  
  
    3.  <span data-ttu-id="6aa76-112">Tapez votre code, par exemple :</span><span class="sxs-lookup"><span data-stu-id="6aa76-112">Type in your code, for example:</span></span>  
  
    ```  
    BeginDocSessionMsg = BeginDocMsg;  
    BeginDocSessionMsg(JDE.ReserveSession) = true;  
    BeginDocSessionMsg(JDE.SessionID) = 0;  
    ```  
  
     <span data-ttu-id="6aa76-113">Ce code indique à l'adaptateur que vous voulez démarrer une session.</span><span class="sxs-lookup"><span data-stu-id="6aa76-113">This tells the adapter you want to start a session.</span></span> <span data-ttu-id="6aa76-114">L’élément SessionID est initialisé à 0, mais lorsque la réponse est renvoyée l’ID est attribué par le J.D.</span><span class="sxs-lookup"><span data-stu-id="6aa76-114">The SessionID is initialized as 0 but when the response comes back the ID will be assigned by the J.D.</span></span> <span data-ttu-id="6aa76-115">Serveur Edwards OneWorld.</span><span class="sxs-lookup"><span data-stu-id="6aa76-115">Edwards OneWorld Server.</span></span>  
  
     ![](../core/media/jde-message-expression-editor.gif "JDE_message_expression_editor")  
  
2.  <span data-ttu-id="6aa76-116">Faites glisser une forme Construire un message avant SendEditLine.</span><span class="sxs-lookup"><span data-stu-id="6aa76-116">Drag a Construct Message before SendEditLine.</span></span>  
  
    -   <span data-ttu-id="6aa76-117">**Messages construits :** EditLineSessionMsg</span><span class="sxs-lookup"><span data-stu-id="6aa76-117">**Messages Constructed:** EditLineSessionMsg</span></span>  
  
    -   <span data-ttu-id="6aa76-118">**Nom :** ConstructEditLineMessageWithSession</span><span class="sxs-lookup"><span data-stu-id="6aa76-118">**Name:** ConstructEditLineMessageWithSession</span></span>  
  
     ![](../core/media/jde-constructoreditlinemessagewithsession.gif "JDE_constructoreditlinemessagewithsession")  
  
    1.  <span data-ttu-id="6aa76-119">Faites glisser une forme Assignation du message dans l'orchestration où vous souhaitez créer un message.</span><span class="sxs-lookup"><span data-stu-id="6aa76-119">Drag a Message Assignment shape into your orchestration where you want to create a new message.</span></span>  
  
    2.  <span data-ttu-id="6aa76-120">Double-cliquez sur la forme interne MessageAssignment_1.</span><span class="sxs-lookup"><span data-stu-id="6aa76-120">Double-click the inner MessageAssignment_1 shape.</span></span>  
  
         <span data-ttu-id="6aa76-121">L'Éditeur d'expression BizTalk s'affiche.</span><span class="sxs-lookup"><span data-stu-id="6aa76-121">The BizTalk Expression Editor appears.</span></span>  
  
    3.  <span data-ttu-id="6aa76-122">Tapez votre code, par exemple :</span><span class="sxs-lookup"><span data-stu-id="6aa76-122">Type in your code, for example:</span></span>  
  
    ```  
    EditLineSessionMsg = EditLineMsg;  
    EditLineSessionMsg(JDE.ReserveSession) = true;  
    EditLineSessionMsg(JDE.SessionID) =  
       BeginDocResponseMsg(JDE.SessionID);  
    ```  
  
     ![](../core/media/jde-editline-editor.gif "JDE_editline_editor")  
  
3.  <span data-ttu-id="6aa76-123">Faites glisser une forme Construire un message avant SendEndDoc.</span><span class="sxs-lookup"><span data-stu-id="6aa76-123">Drag a Construct Message before SendEndDoc.</span></span>  
  
    -   <span data-ttu-id="6aa76-124">**Messages construits :** EndDocSessionMsg</span><span class="sxs-lookup"><span data-stu-id="6aa76-124">**Messages Constructed:** EndDocSessionMsg</span></span>  
  
    -   <span data-ttu-id="6aa76-125">**Nom :** ConstructEndDocMessageWithSession</span><span class="sxs-lookup"><span data-stu-id="6aa76-125">**Name:** ConstructEndDocMessageWithSession</span></span>  
  
    1.  <span data-ttu-id="6aa76-126">Faites glisser une forme Assignation du message dans l'orchestration où vous souhaitez créer un message.</span><span class="sxs-lookup"><span data-stu-id="6aa76-126">Drag a Message Assignment shape into your orchestration where you want to create a new message.</span></span>  
  
    2.  <span data-ttu-id="6aa76-127">Double-cliquez sur la forme interne MessageAssignment_1.</span><span class="sxs-lookup"><span data-stu-id="6aa76-127">Double-click the inner MessageAssignment_1 shape.</span></span>  
  
         <span data-ttu-id="6aa76-128">L'Éditeur d'expression BizTalk s'affiche.</span><span class="sxs-lookup"><span data-stu-id="6aa76-128">The BizTalk Expression Editor appears.</span></span>  
  
    3.  <span data-ttu-id="6aa76-129">Tapez votre code, par exemple :</span><span class="sxs-lookup"><span data-stu-id="6aa76-129">Type in your code, for example:</span></span>  
  
    ```  
    EndDocSessionMsg = EndDocMsg;  
    EndDocSessionMsg(JDE.ReserveSession) = false;  
    EndDocSessionMsg(JDE.SessionID) =  
       BeginDocResponseMsg(JDE.SessionID);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="6aa76-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6aa76-130">See Also</span></span>  
 <span data-ttu-id="6aa76-131">[Tâche 1 : Créer les Ports](../core/task-1-create-the-ports2.md) </span><span class="sxs-lookup"><span data-stu-id="6aa76-131">[Task 1: Create the Ports](../core/task-1-create-the-ports2.md) </span></span>  
 <span data-ttu-id="6aa76-132">[Tâche 2 : Créer les Messages](../core/task-2-create-the-messages1.md) </span><span class="sxs-lookup"><span data-stu-id="6aa76-132">[Task 2: Create the Messages](../core/task-2-create-the-messages1.md) </span></span>  
 <span data-ttu-id="6aa76-133">[Tâche 3 : Configurer l’envoi et réception des formes](../core/task-3-configure-the-send-and-receive-shapes1.md) </span><span class="sxs-lookup"><span data-stu-id="6aa76-133">[Task 3: Configure the Send and Receive Shapes](../core/task-3-configure-the-send-and-receive-shapes1.md) </span></span>  
 [<span data-ttu-id="6aa76-134">Tâche 5 : Configurer la forme Transformer</span><span class="sxs-lookup"><span data-stu-id="6aa76-134">Task 5: Configure the Transform Shape</span></span>](../core/task-5-configure-the-transform-shape1.md)