---
title: "Étape 3 : Ajouter un filtre pour les Notifications d’insertion | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 53a1e9ef-a179-42a7-b4ae-b1170181053b
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 97fc32fe7dd657bb45edca91fda0eddaa537b32a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-3-add-a-filter-for-insert-notifications"></a><span data-ttu-id="427d2-102">Étape 3 : Ajouter un filtre pour les Notifications d’insertion</span><span class="sxs-lookup"><span data-stu-id="427d2-102">Step 3: Add a Filter for Insert Notifications</span></span>
<span data-ttu-id="427d2-103">![Étape 3 sur 3](../../adapters-and-accelerators/adapter-oracle-database/media/step-3of3.gif "Step_3of3")</span><span class="sxs-lookup"><span data-stu-id="427d2-103">![Step 3 of 3](../../adapters-and-accelerators/adapter-oracle-database/media/step-3of3.gif "Step_3of3")</span></span>  
  
 <span data-ttu-id="427d2-104">**Durée :** 5 minutes</span><span class="sxs-lookup"><span data-stu-id="427d2-104">**Time to complete:** 5 minutes</span></span>  
  
 <span data-ttu-id="427d2-105">**Objectif :** dans cette étape, vous ajoutez une forme décider à l’orchestration pour filtrer les messages de notification pour l’opération d’insertion.</span><span class="sxs-lookup"><span data-stu-id="427d2-105">**Objective:** In this step, you add a Decide shape to the orchestration to filter for notification messages for Insert operation.</span></span> <span data-ttu-id="427d2-106">Les opérations suivantes dans l’orchestration sont effectuées uniquement si la notification reçue est de type de l’insertion.</span><span class="sxs-lookup"><span data-stu-id="427d2-106">Subsequent operations in the orchestration are performed only if the notification received is of Insert type.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="427d2-107">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="427d2-107">Prerequisites</span></span>  
 <span data-ttu-id="427d2-108">Vous devez avoir terminé [étape 2 : extraction de Type de Notification de Message de Notification](../../adapters-and-accelerators/adapter-sql/step-2-extract-notification-type-from-notification-message.md).</span><span class="sxs-lookup"><span data-stu-id="427d2-108">You must have completed [Step 2: Extract Notification Type from Notification Message](../../adapters-and-accelerators/adapter-sql/step-2-extract-notification-type-from-notification-message.md).</span></span>  
  
### <a name="to-filter-for-notification-messages"></a><span data-ttu-id="427d2-109">Pour filtrer les messages de notification</span><span class="sxs-lookup"><span data-stu-id="427d2-109">To filter for notification messages</span></span>  
  
1.  <span data-ttu-id="427d2-110">Ajouter un **décider** mettre en forme à l’orchestration, après le **Expression** forme.</span><span class="sxs-lookup"><span data-stu-id="427d2-110">Add a **Decide** shape to the orchestration, after the **Expression** shape.</span></span> <span data-ttu-id="427d2-111">Dans la boîte à outils, faites glisser le **décider** forme sur la ligne de connexion directement sous la **Expression** forme.</span><span class="sxs-lookup"><span data-stu-id="427d2-111">From the Toolbox, drag the **Decide** shape onto the connecting line directly below the **Expression** shape.</span></span>  
  
     <span data-ttu-id="427d2-112">Le **décider** forme se développe pour afficher une branche pour le **si** instruction **(Rule_1)** et une branche pour le **Else** instruction.</span><span class="sxs-lookup"><span data-stu-id="427d2-112">The **Decide** shape expands to show a branch for the **If** statement **(Rule_1)** and a branch for the **Else** statement.</span></span>  
  
2.  <span data-ttu-id="427d2-113">Sur l’aire de conception, cliquez sur le **décider** mettre en forme, puis cliquez sur **fenêtre Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="427d2-113">On the design surface, right-click the **Decide** shape, and then click **Properties Window**.</span></span>  
  
3.  <span data-ttu-id="427d2-114">Dans le **propriétés** volet pour le **décider** mettre en forme, dans le **nom** , tapez `CheckNotification`.</span><span class="sxs-lookup"><span data-stu-id="427d2-114">In the **Properties** pane for the **Decide** shape, in the **Name** property, type `CheckNotification`.</span></span>  
  
4.  <span data-ttu-id="427d2-115">Sur l’aire de conception, cliquez sur le **Rule_1** forme (à l’intérieur de la **décider** forme), puis cliquez sur **fenêtre Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="427d2-115">On the design surface, right-click the **Rule_1** shape (inside of the **Decide** shape), and then click **Properties Window**.</span></span>  
  
5.  <span data-ttu-id="427d2-116">Dans le **propriétés** volet pour **Rule_1**, dans le **nom** , tapez **insérer**.</span><span class="sxs-lookup"><span data-stu-id="427d2-116">In the **Properties** pane for **Rule_1**, in the **Name** property, type **Insert**.</span></span>  
  
6.  <span data-ttu-id="427d2-117">Cliquez sur le **insérer** mettre en forme, puis cliquez sur **modifier l’Expression booléenne**.</span><span class="sxs-lookup"><span data-stu-id="427d2-117">Right-click the **Insert** shape, and then click **Edit Boolean Expression**.</span></span>  
  
7.  <span data-ttu-id="427d2-118">Dans l’éditeur d’Expression BizTalk, tapez le texte suivant :</span><span class="sxs-lookup"><span data-stu-id="427d2-118">In the BizTalk Expression Editor, type the following:</span></span>  
  
    ```  
    NotificationType.Equals("Insert")  
    ```  
  
     <span data-ttu-id="427d2-119">Cette condition indique à l’orchestration permettant d’effectuer les opérations suivantes uniquement si la valeur de la **NotificationType** variable est **insérer**.</span><span class="sxs-lookup"><span data-stu-id="427d2-119">This condition tells the orchestration to perform subsequent operations only if the value in the **NotificationType** variable is **Insert**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="427d2-120">Vous avez ajouté cette variable dans [étape 2 : extraction de Type de Notification de Message de Notification](../../adapters-and-accelerators/adapter-sql/step-2-extract-notification-type-from-notification-message.md) pour extraire le type de notification à partir du message de notification reçu à partir de la base de données SQL Server.</span><span class="sxs-lookup"><span data-stu-id="427d2-120">You added this variable in [Step 2: Extract Notification Type from Notification Message](../../adapters-and-accelerators/adapter-sql/step-2-extract-notification-type-from-notification-message.md) to extract the type of notification from the notification message received from the SQL Server database.</span></span>  
  
8.  <span data-ttu-id="427d2-121">L’illustration suivante montre l’orchestration en cours avec le **décider** forme inclus.</span><span class="sxs-lookup"><span data-stu-id="427d2-121">The following figure shows the in-progress orchestration with the **Decide** shape included.</span></span>  
  
     <span data-ttu-id="427d2-122">![Ajouter une forme décider à l’orchestration](../../adapters-and-accelerators/adapter-sql/media/sql-adap-tut-03-add-filter-orch.gif "sql_adap_tut_03_add_filter_orch")</span><span class="sxs-lookup"><span data-stu-id="427d2-122">![Add a Decide shape to the orchestration](../../adapters-and-accelerators/adapter-sql/media/sql-adap-tut-03-add-filter-orch.gif "sql_adap_tut_03_add_filter_orch")</span></span>  
  
## <a name="what-did-i-just-do"></a><span data-ttu-id="427d2-123">Actions effectuées</span><span class="sxs-lookup"><span data-stu-id="427d2-123">What did I just do?</span></span>  
 <span data-ttu-id="427d2-124">Dans cette étape, vous avez ajouté un **décider** forme pour filtrer les messages de notification pour effectuer les opérations suivantes uniquement si la notification reçue est pour les opérations d’insertion.</span><span class="sxs-lookup"><span data-stu-id="427d2-124">In this step, you added a **Decide** shape to filter the notification messages to perform subsequent operations only if the notification received is for Insert operations.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="427d2-125">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="427d2-125">Next Steps</span></span>  
 <span data-ttu-id="427d2-126">Dans l’étape suivante, vous ajoutez des formes d’orchestration à appeler le UPDATE_EMPLOYE de procédure stockée dans la table Employee, comme décrit dans [leçon 3 : exécuter une procédure stockée pour sélectionnez Nouveau employés ajouté](../../adapters-and-accelerators/adapter-sql/lesson-3-execute-a-stored-procedure-to-select-new-employees-added.md).</span><span class="sxs-lookup"><span data-stu-id="427d2-126">In the next step, you add orchestration shapes to invoke the UPDATE_EMPLOYE stored procedure on the Employee table, as described in [Lesson 3: Execute a Stored Procedure to Select New Employees Added](../../adapters-and-accelerators/adapter-sql/lesson-3-execute-a-stored-procedure-to-select-new-employees-added.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="427d2-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="427d2-127">See Also</span></span>  
 <span data-ttu-id="427d2-128">[Étape 2 : Extraire le Type de Notification de Message de Notification](../../adapters-and-accelerators/adapter-sql/step-2-extract-notification-type-from-notification-message.md) </span><span class="sxs-lookup"><span data-stu-id="427d2-128">[Step 2: Extract Notification Type from Notification Message](../../adapters-and-accelerators/adapter-sql/step-2-extract-notification-type-from-notification-message.md) </span></span>  
 [<span data-ttu-id="427d2-129">Leçon 2 : Réception et filtrer les Notifications</span><span class="sxs-lookup"><span data-stu-id="427d2-129">Lesson 2: Receive and Filter Notifications</span></span>](../../adapters-and-accelerators/adapter-sql/lesson-2-receive-and-filter-notifications.md)