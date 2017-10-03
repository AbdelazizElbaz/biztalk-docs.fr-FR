---
title: "Tâche 4 : Configurer la Shape1 Message construction | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a3e66a9d-c549-42d0-849b-9e1744056429
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f781e03f83223f7d82628ee9c01728a0754b149f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="task-4-configure-the-construct-message-shape"></a><span data-ttu-id="4049c-102">Tâche 4 : Configurer la forme construire un Message</span><span class="sxs-lookup"><span data-stu-id="4049c-102">Task 4: Configure the Construct Message Shape</span></span>
<span data-ttu-id="4049c-103">La forme Construire un message conserve les assignations des messages avec les instructions relatives aux codes Begin, Edit et End Doc.</span><span class="sxs-lookup"><span data-stu-id="4049c-103">The Construct Messages hold messages assignments with the instructions for the Begin, Edit, and End Doc code.</span></span>  
  
 <span data-ttu-id="4049c-104">La procédure suivante permet de configurer la forme Construire un message.</span><span class="sxs-lookup"><span data-stu-id="4049c-104">Use the following procedure to configure the Construct Message shape.</span></span>  
  
### <a name="to-configure-the-construct-message-shape"></a><span data-ttu-id="4049c-105">Pour configurer la forme Construire un message</span><span class="sxs-lookup"><span data-stu-id="4049c-105">To configure the Construct Message shape</span></span>  
  
1.  <span data-ttu-id="4049c-106">Faites glisser une forme Construire un message entre ReceiveBeginDoc et SendBeginDoc.</span><span class="sxs-lookup"><span data-stu-id="4049c-106">Drag a Construct Message shape inbetween ReceiveBeginDoc and SendBeginDoc.</span></span>  
  
    -   <span data-ttu-id="4049c-107">**Messages construits :** BeginDocSessionMsg</span><span class="sxs-lookup"><span data-stu-id="4049c-107">**Messages Constructed:** BeginDocSessionMsg</span></span>  
  
    -   <span data-ttu-id="4049c-108">**Nom :** ConstructBeginDocMessageWithSession</span><span class="sxs-lookup"><span data-stu-id="4049c-108">**Name:** ConstructBeginDocMessageWithSession</span></span>  
  
    1.  <span data-ttu-id="4049c-109">Faites glisser une forme Assignation du message dans l'orchestration où vous souhaitez créer un message.</span><span class="sxs-lookup"><span data-stu-id="4049c-109">Drag a Message Assignment shape into your orchestration where you want to create a new message.</span></span>  
  
    2.  <span data-ttu-id="4049c-110">Double-cliquez sur la forme interne MessageAssignment_1.</span><span class="sxs-lookup"><span data-stu-id="4049c-110">Double-click the inner MessageAssignment_1 shape.</span></span>  
  
         <span data-ttu-id="4049c-111">L'Éditeur d'expression BizTalk s'affiche.</span><span class="sxs-lookup"><span data-stu-id="4049c-111">The BizTalk Expression Editor appears.</span></span>  
  
    3.  <span data-ttu-id="4049c-112">Tapez votre code, par exemple :</span><span class="sxs-lookup"><span data-stu-id="4049c-112">Type in your code, for example:</span></span>  
  
        ```  
        BeginDocSessionMsg = BeginDocMsg;  
        BeginDocSessionMsg(JDE.ReserveSession) = true;  
        BeginDocSessionMsg(JDE.SessionID) = 0;  
        ```  
  
         <span data-ttu-id="4049c-113">Ce code indique à l'adaptateur que vous voulez démarrer une session.</span><span class="sxs-lookup"><span data-stu-id="4049c-113">This tells the adapter you want to start a session.</span></span> <span data-ttu-id="4049c-114">L’élément SessionID est initialisé à 0, mais lorsque la réponse est renvoyée l’ID est attribué par le J.D.</span><span class="sxs-lookup"><span data-stu-id="4049c-114">The SessionID is initialized as 0 but when the response comes back the ID will be assigned by the J.D.</span></span> <span data-ttu-id="4049c-115">Edwards EnterpriseOne serveur.</span><span class="sxs-lookup"><span data-stu-id="4049c-115">Edwards EnterpriseOne Server.</span></span>  
  
     <span data-ttu-id="4049c-116">![Message de l’éditeur d’Expression](../core/media/message-expression-editor.gif "message_expression_editor")</span><span class="sxs-lookup"><span data-stu-id="4049c-116">![Message Expression Editor](../core/media/message-expression-editor.gif "message_expression_editor")</span></span>  
  
2.  <span data-ttu-id="4049c-117">Faites glisser une forme Construire un message avant SendEditLine.</span><span class="sxs-lookup"><span data-stu-id="4049c-117">Drag a Construct Message before SendEditLine.</span></span>  
  
    -   <span data-ttu-id="4049c-118">**Messages construits :** EditLineSessionMsg</span><span class="sxs-lookup"><span data-stu-id="4049c-118">**Messages Constructed:** EditLineSessionMsg</span></span>  
  
    -   <span data-ttu-id="4049c-119">**Nom :** ConstructEditLineMessageWithSession</span><span class="sxs-lookup"><span data-stu-id="4049c-119">**Name:** ConstructEditLineMessageWithSession</span></span>  
  
     <span data-ttu-id="4049c-120">![Modifier une ligne d’envoi](../core/media/constructoreditlinemessagewithsession.gif "constructoreditlinemessagewithsession")</span><span class="sxs-lookup"><span data-stu-id="4049c-120">![Send Edit Line](../core/media/constructoreditlinemessagewithsession.gif "constructoreditlinemessagewithsession")</span></span>  
  
    1.  <span data-ttu-id="4049c-121">Faites glisser une forme Assignation du message dans l'orchestration où vous souhaitez créer un message.</span><span class="sxs-lookup"><span data-stu-id="4049c-121">Drag a Message Assignment shape into your orchestration where you want to create a new message.</span></span>  
  
    2.  <span data-ttu-id="4049c-122">Double-cliquez sur la forme interne MessageAssignment_1.</span><span class="sxs-lookup"><span data-stu-id="4049c-122">Double-click the inner MessageAssignment_1 shape.</span></span>  
  
         <span data-ttu-id="4049c-123">L'Éditeur d'expression BizTalk s'affiche.</span><span class="sxs-lookup"><span data-stu-id="4049c-123">The BizTalk Expression Editor appears.</span></span>  
  
    3.  <span data-ttu-id="4049c-124">Tapez votre code, par exemple :</span><span class="sxs-lookup"><span data-stu-id="4049c-124">Type in your code, for example:</span></span>  
  
        ```  
        EditLineSessionMsg = EditLineMsg;  
        EditLineSessionMsg(JDE.ReserveSession) = true;  
        EditLineSessionMsg(JDE.SessionID) =  
        BeginDocResponseMsg(JDE.SessionID);  
        ```  
  
     <span data-ttu-id="4049c-125">![Éditeur de ligne](../core/media/editline-editor.gif "editline_editor")</span><span class="sxs-lookup"><span data-stu-id="4049c-125">![Edit Line Editor](../core/media/editline-editor.gif "editline_editor")</span></span>  
  
3.  <span data-ttu-id="4049c-126">Faites glisser une forme construire un Message avant SendEndDoc.</span><span class="sxs-lookup"><span data-stu-id="4049c-126">Drag a Construct Message shape before SendEndDoc.</span></span>  
  
    -   <span data-ttu-id="4049c-127">**Messages construits :** EndDocSessionMsg</span><span class="sxs-lookup"><span data-stu-id="4049c-127">**Messages Constructed:** EndDocSessionMsg</span></span>  
  
    -   <span data-ttu-id="4049c-128">**Nom :** ConstructEndDocMessageWithSession</span><span class="sxs-lookup"><span data-stu-id="4049c-128">**Name:** ConstructEndDocMessageWithSession</span></span>  
  
    1.  <span data-ttu-id="4049c-129">Faites glisser une forme Assignation du message dans l'orchestration où vous souhaitez créer un message.</span><span class="sxs-lookup"><span data-stu-id="4049c-129">Drag a Message Assignment shape into your orchestration where you want to create a new message.</span></span>  
  
    2.  <span data-ttu-id="4049c-130">Double-cliquez sur la forme interne MessageAssignment_1.</span><span class="sxs-lookup"><span data-stu-id="4049c-130">Double-click the inner MessageAssignment_1 shape.</span></span>  
  
         <span data-ttu-id="4049c-131">L'Éditeur d'expression BizTalk s'affiche.</span><span class="sxs-lookup"><span data-stu-id="4049c-131">The BizTalk Expression Editor appears.</span></span>  
  
    3.  <span data-ttu-id="4049c-132">Tapez votre code, par exemple :</span><span class="sxs-lookup"><span data-stu-id="4049c-132">Type in your code, for example:</span></span>  
  
        ```  
        EndDocSessionMsg = EndDocMsg;  
        EndDocSessionMsg(JDE.ReserveSession) = false;  
        EndDocSessionMsg(JDE.SessionID) =  
           BeginDocResponseMsg(JDE.SessionID);  
        ```  
  
## <a name="see-also"></a><span data-ttu-id="4049c-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4049c-133">See Also</span></span>  
 <span data-ttu-id="4049c-134">[Tâche 1 : Créer les Ports](../core/task-1-create-the-ports1.md) </span><span class="sxs-lookup"><span data-stu-id="4049c-134">[Task 1: Create the Ports](../core/task-1-create-the-ports1.md) </span></span>  
 <span data-ttu-id="4049c-135">[Tâche 2 : Créer les Messages](../core/task-2-create-the-messages2.md) </span><span class="sxs-lookup"><span data-stu-id="4049c-135">[Task 2: Create the Messages](../core/task-2-create-the-messages2.md) </span></span>  
 <span data-ttu-id="4049c-136">[Tâche 3 : Configurer l’envoi et réception des formes](../core/task-3-configure-the-send-and-receive-shapes2.md) </span><span class="sxs-lookup"><span data-stu-id="4049c-136">[Task 3: Configure the Send and Receive Shapes](../core/task-3-configure-the-send-and-receive-shapes2.md) </span></span>  
 [<span data-ttu-id="4049c-137">Tâche 5 : Configurer la forme Transformer</span><span class="sxs-lookup"><span data-stu-id="4049c-137">Task 5: Configure the Transform Shape</span></span>](../core/task-5-configure-the-transform-shape2.md)