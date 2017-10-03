---
title: "Tâche 2 : Créer le Messages2 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2db67595-bcb6-455b-ad81-07b4426b7ea4
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3f970e692f72af21c8b1c3c76dfdebae15350f5f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="task-2-create-the-messages"></a><span data-ttu-id="03c15-102">Tâche 2 : Créer les Messages</span><span class="sxs-lookup"><span data-stu-id="03c15-102">Task 2: Create the Messages</span></span>
<span data-ttu-id="03c15-103">Créez les messages suivants qui seront utilisés dans l'orchestration.</span><span class="sxs-lookup"><span data-stu-id="03c15-103">Create the following Messages, which will be used in the orchestration.</span></span>  
  
### <a name="to-create-the-messages"></a><span data-ttu-id="03c15-104">Pour créer les messages</span><span class="sxs-lookup"><span data-stu-id="03c15-104">To create the messages</span></span>  
  
1.  <span data-ttu-id="03c15-105">Avec le bouton droit **Message**, puis sélectionnez **nouveau Message**.</span><span class="sxs-lookup"><span data-stu-id="03c15-105">Right-click **Message**, and then select **New Message**.</span></span>  
  
2.  <span data-ttu-id="03c15-106">Renseignez les valeurs suivantes pour les champs Identificateur et Type de message>Schéma, et sélectionnez le type dans la liste affichée pour chaque message.</span><span class="sxs-lookup"><span data-stu-id="03c15-106">Fill in the following for the Identifier and the Message Type>Schema and select the type from the displayed list for each message.</span></span>  
  
    |<span data-ttu-id="03c15-107">Identificateur</span><span class="sxs-lookup"><span data-stu-id="03c15-107">Identifier</span></span>|<span data-ttu-id="03c15-108">Type de message > Schéma</span><span class="sxs-lookup"><span data-stu-id="03c15-108">Message Type > Schema</span></span>|  
    |----------------|----------------------------|  
    |<span data-ttu-id="03c15-109">BeginDocMsg</span><span class="sxs-lookup"><span data-stu-id="03c15-109">BeginDocMsg</span></span>|<span data-ttu-id="03c15-110">BeginDocTest.B4200310Service_1.F4211FSBeginDoc</span><span class="sxs-lookup"><span data-stu-id="03c15-110">BeginDocTest.B4200310Service_1.F4211FSBeginDoc</span></span>|  
    |<span data-ttu-id="03c15-111">BeginDocResponseMsg</span><span class="sxs-lookup"><span data-stu-id="03c15-111">BeginDocResponseMsg</span></span>|<span data-ttu-id="03c15-112">BeginDocTest.B4200310Service_1.F4211FSBeginDocResponse</span><span class="sxs-lookup"><span data-stu-id="03c15-112">BeginDocTest.B4200310Service_1.F4211FSBeginDocResponse</span></span>|  
    |<span data-ttu-id="03c15-113">BeginDocSessionMsg</span><span class="sxs-lookup"><span data-stu-id="03c15-113">BeginDocSessionMsg</span></span>|<span data-ttu-id="03c15-114">BeginDocTest.B4200310Service_1.F4211FSBeginDoc</span><span class="sxs-lookup"><span data-stu-id="03c15-114">BeginDocTest.B4200310Service_1.F4211FSBeginDoc</span></span>|  
    |<span data-ttu-id="03c15-115">EditLineMsg</span><span class="sxs-lookup"><span data-stu-id="03c15-115">EditLineMsg</span></span>|<span data-ttu-id="03c15-116">BeginDocTest.B4200310Service_1.F4211FSEditLine</span><span class="sxs-lookup"><span data-stu-id="03c15-116">BeginDocTest.B4200310Service_1.F4211FSEditLine</span></span>|  
    |<span data-ttu-id="03c15-117">EditLineResponseMsg</span><span class="sxs-lookup"><span data-stu-id="03c15-117">EditLineResponseMsg</span></span>|<span data-ttu-id="03c15-118">BeginDocTest.B4200310Service_1.F4211FSEditLineResponse</span><span class="sxs-lookup"><span data-stu-id="03c15-118">BeginDocTest.B4200310Service_1.F4211FSEditLineResponse</span></span>|  
    |<span data-ttu-id="03c15-119">EditLineSessionMsg</span><span class="sxs-lookup"><span data-stu-id="03c15-119">EditLineSessionMsg</span></span>|<span data-ttu-id="03c15-120">BeginDocTest.B4200310Service_1.F4211FSEditLine</span><span class="sxs-lookup"><span data-stu-id="03c15-120">BeginDocTest.B4200310Service_1.F4211FSEditLine</span></span>|  
    |<span data-ttu-id="03c15-121">EndDocMsg</span><span class="sxs-lookup"><span data-stu-id="03c15-121">EndDocMsg</span></span>|<span data-ttu-id="03c15-122">BeginDocTest.B4200310Service_1.F4211FSEndDoc</span><span class="sxs-lookup"><span data-stu-id="03c15-122">BeginDocTest.B4200310Service_1.F4211FSEndDoc</span></span>|  
    |<span data-ttu-id="03c15-123">EndDocResponseMsg</span><span class="sxs-lookup"><span data-stu-id="03c15-123">EndDocResponseMsg</span></span>|<span data-ttu-id="03c15-124">BeginDocTest.B4200310Service_1.F4211FSEndDocResponse</span><span class="sxs-lookup"><span data-stu-id="03c15-124">BeginDocTest.B4200310Service_1.F4211FSEndDocResponse</span></span>|  
    |<span data-ttu-id="03c15-125">EndDocSessionMsg</span><span class="sxs-lookup"><span data-stu-id="03c15-125">EndDocSessionMsg</span></span>|<span data-ttu-id="03c15-126">BeginDocTest.B4200310Service_1.F4211FSEndDoc</span><span class="sxs-lookup"><span data-stu-id="03c15-126">BeginDocTest.B4200310Service_1.F4211FSEndDoc</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="03c15-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="03c15-127">See Also</span></span>  
 <span data-ttu-id="03c15-128">[Tâche 1 : Créer les Ports](../core/task-1-create-the-ports1.md) </span><span class="sxs-lookup"><span data-stu-id="03c15-128">[Task 1: Create the Ports](../core/task-1-create-the-ports1.md) </span></span>  
 <span data-ttu-id="03c15-129">[Tâche 3 : Configurer l’envoi et réception des formes](../core/task-3-configure-the-send-and-receive-shapes2.md) </span><span class="sxs-lookup"><span data-stu-id="03c15-129">[Task 3: Configure the Send and Receive Shapes](../core/task-3-configure-the-send-and-receive-shapes2.md) </span></span>  
 <span data-ttu-id="03c15-130">[Tâche 4 : Configurer la forme construire un Message](../core/task-4-configure-the-construct-message-shape1.md) </span><span class="sxs-lookup"><span data-stu-id="03c15-130">[Task 4: Configure the Construct Message Shape](../core/task-4-configure-the-construct-message-shape1.md) </span></span>  
 [<span data-ttu-id="03c15-131">Tâche 5 : Configurer la forme Transformer</span><span class="sxs-lookup"><span data-stu-id="03c15-131">Task 5: Configure the Transform Shape</span></span>](../core/task-5-configure-the-transform-shape2.md)