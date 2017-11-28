---
title: "Didacticiel 2 : Employé - processus de bon de commande à l’aide de l’adaptateur SQL | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eeb4dd1e-209a-47eb-9c0e-a138e02f0ff2
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8fca0c11aeb1f84a5e9f05a4df4f995b7c2b52e5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="tutorial-2-employee---purchase-order-process-using-the-sql-adapter"></a><span data-ttu-id="59977-102">Didacticiel 2 : Employé - processus de bon de commande à l’aide de l’adaptateur SQL</span><span class="sxs-lookup"><span data-stu-id="59977-102">Tutorial 2: Employee - Purchase Order Process using the SQL adapter</span></span>
<span data-ttu-id="59977-103">Dans ce didacticiel, vous automatisez le processus dans lequel le service des achats qui place un équipement de commande chaque fois qu’un nouvel employé rejoint l’organisation.</span><span class="sxs-lookup"><span data-stu-id="59977-103">In this tutorial, you are automating the process where the Purchases department that places an equipment order every time a new employee joins the organization.</span></span> <span data-ttu-id="59977-104">Détails de l’employé et purchase order Detail est conservés dans **employé** et **Purchase_Order** tables respectivement, dans une base de données SQL Server.</span><span class="sxs-lookup"><span data-stu-id="59977-104">Both employee details and purchase order details are maintained in **Employee** and **Purchase_Order** tables respectively, in a SQL Server database.</span></span> <span data-ttu-id="59977-105">Le service des achats est informé en mettant à jour la table Purchase_Order dans la base de données SQL Server et en envoyant un message électronique.</span><span class="sxs-lookup"><span data-stu-id="59977-105">The Purchases department is informed by updating the Purchase_Order table in the SQL Server database and by sending an e-mail.</span></span> <span data-ttu-id="59977-106">Dans le processus, les actions suivantes se produisent :</span><span class="sxs-lookup"><span data-stu-id="59977-106">Within the process, the following actions occur:</span></span>  
  
1.  <span data-ttu-id="59977-107">L’adaptateur reçoit une notification chaque fois que le **employé** table est mise à jour.</span><span class="sxs-lookup"><span data-stu-id="59977-107">The adapter receives a notification each time the **Employee** table is updated.</span></span> <span data-ttu-id="59977-108">Ensuite, l’adaptateur envoie une notification à l’orchestration BizTalk.</span><span class="sxs-lookup"><span data-stu-id="59977-108">The adapter then sends a notification to the BizTalk orchestration.</span></span>  
  
2.  <span data-ttu-id="59977-109">L’orchestration BizTalk détermine si la notification est pour un nouvel enregistrement est inséré dans le **employé** table.</span><span class="sxs-lookup"><span data-stu-id="59977-109">The BizTalk orchestration figures out whether the notification is for a new record inserted into the **Employee** table.</span></span> <span data-ttu-id="59977-110">Si la notification est pour toute autre opération sur le **employé** table, l’orchestration n’effectue aucune opération.</span><span class="sxs-lookup"><span data-stu-id="59977-110">If the notification is for any other operation on the **Employee** table, the orchestration does not perform any operation.</span></span>  
  
3.  <span data-ttu-id="59977-111">Si la notification est pour une opération d’insertion sur la **employé** table, notification qu’un nouvel enregistrement d’employé a été ajouté, l’orchestration utilise le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] pour lire les détails du nouvel enregistrement.</span><span class="sxs-lookup"><span data-stu-id="59977-111">If the notification is for an Insert operation on the **Employee** table, notifying that a new employee record was added, the orchestration uses the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] to read the details of the new record.</span></span>  
  
4.  <span data-ttu-id="59977-112">L’orchestration reçoit une réponse qui contient les détails du nouvel enregistrement d’employé.</span><span class="sxs-lookup"><span data-stu-id="59977-112">The orchestration receives a response that contains the details of the new added employee record.</span></span> <span data-ttu-id="59977-113">Les mappages d’orchestration le **Employee_ID** et **désignation** champs dans la réponse au message de demande pour l’opération d’insertion sur la **Purchase_Order** table.</span><span class="sxs-lookup"><span data-stu-id="59977-113">The orchestration maps the **Employee_ID** and **Designation** fields in the response to the request message for the Insert operation on the **Purchase_Order** table.</span></span>  
  
5.  <span data-ttu-id="59977-114">L’orchestration utilise la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] pour effectuer une opération d’insertion sur la **Purchase_Order** table.</span><span class="sxs-lookup"><span data-stu-id="59977-114">The orchestration then uses the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] to perform an Insert operation on the **Purchase_Order** table.</span></span> <span data-ttu-id="59977-115">La réponse pour l’opération d’insertion est envoyée au service des achats comme un message électronique.</span><span class="sxs-lookup"><span data-stu-id="59977-115">The response for the Insert operation is sent to the Purchases department as an e-mail.</span></span>  
  
## <a name="about-the-database-objects-used-in-this-sample"></a><span data-ttu-id="59977-116">Sur les objets de base de données utilisées dans cet exemple</span><span class="sxs-lookup"><span data-stu-id="59977-116">About the Database Objects Used in this Sample</span></span>  
 <span data-ttu-id="59977-117">Ce didacticiel utilise les objets de base de données créés par le script SQL inclu dans les exemples.</span><span class="sxs-lookup"><span data-stu-id="59977-117">This tutorial uses the database objects created by the SQL script shipped with the samples.</span></span> <span data-ttu-id="59977-118">Pour plus d’informations sur le script et les exemples, consultez [exemples d’adaptateur](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md).</span><span class="sxs-lookup"><span data-stu-id="59977-118">For more information about the script and the samples, see [Adapter Samples](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md).</span></span> <span data-ttu-id="59977-119">Les objets de base de données que vous utiliserez dans ce didacticiel sont :</span><span class="sxs-lookup"><span data-stu-id="59977-119">The database objects that you will use in this tutorial are:</span></span>  
  
-   <span data-ttu-id="59977-120">**ADAPTER_SAMPLES** base de données.</span><span class="sxs-lookup"><span data-stu-id="59977-120">**ADAPTER_SAMPLES** database.</span></span>  
  
-   <span data-ttu-id="59977-121">**Employé** et **Purchase_Order** tables.</span><span class="sxs-lookup"><span data-stu-id="59977-121">**Employee** and **Purchase_Order** tables.</span></span>  
  
-   <span data-ttu-id="59977-122">**UPDATE_EMPLOYEE** procédure stockée.</span><span class="sxs-lookup"><span data-stu-id="59977-122">**UPDATE_EMPLOYEE** stored procedure.</span></span>  
  
 <span data-ttu-id="59977-123">Tous ces objets de base de données sont créés lorsque vous exécutez le script SQL fourni avec l’exemple.</span><span class="sxs-lookup"><span data-stu-id="59977-123">All these database objects are created when you run the SQL script provided with the sample.</span></span> <span data-ttu-id="59977-124">Assurez-vous que vous exécutez le script avant de commencer avec le didacticiel.</span><span class="sxs-lookup"><span data-stu-id="59977-124">Make sure you run the script before you start with the tutorial.</span></span>  
  
## <a name="sample-based-on-this-tutorial"></a><span data-ttu-id="59977-125">Exemple basé sur ce didacticiel</span><span class="sxs-lookup"><span data-stu-id="59977-125">Sample Based on This Tutorial</span></span>  
 <span data-ttu-id="59977-126">Un exemple, **Employee_PurchaseOrder**, qui est basé sur ce didacticiel est également fourni avec le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="59977-126">A sample, **Employee_PurchaseOrder**, which is based on this tutorial is also provided with the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span></span> <span data-ttu-id="59977-127">Pour plus d’informations, consultez [exemples d’adaptateur](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md).</span><span class="sxs-lookup"><span data-stu-id="59977-127">For more information, see [Adapter Samples](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md).</span></span>  
  
 <span data-ttu-id="59977-128">Nous vous recommandons de suivre le didacticiel complètement pour comprendre comment créer des projets BizTalk à l’aide de l’adaptateur puis d’observer l’échantillon sous la forme d’une référence.</span><span class="sxs-lookup"><span data-stu-id="59977-128">We recommend that you go through the tutorial completely to understand how to create BizTalk projects using the adapter, and then look at the sample as a reference.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="59977-129">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="59977-129">In This Section</span></span>  
  
-   [<span data-ttu-id="59977-130">Leçon 1 : Générer des schémas et créer des Messages</span><span class="sxs-lookup"><span data-stu-id="59977-130">Lesson 1: Generate Schemas and Create Messages</span></span>](../../adapters-and-accelerators/adapter-sql/lesson-1-generate-schemas-and-create-messages.md)  
  
-   [<span data-ttu-id="59977-131">Leçon 2 : Réception et filtrer les Notifications</span><span class="sxs-lookup"><span data-stu-id="59977-131">Lesson 2: Receive and Filter Notifications</span></span>](../../adapters-and-accelerators/adapter-sql/lesson-2-receive-and-filter-notifications.md)  
  
-   [<span data-ttu-id="59977-132">Leçon 3 : Exécuter une procédure stockée pour sélectionner les nouveaux employés ajoutés</span><span class="sxs-lookup"><span data-stu-id="59977-132">Lesson 3: Execute a Stored Procedure to Select New Employees Added</span></span>](../../adapters-and-accelerators/adapter-sql/lesson-3-execute-a-stored-procedure-to-select-new-employees-added.md)  
  
-   [<span data-ttu-id="59977-133">Leçon 4 : Effectuer une opération d’insertion sur la Table de commande d’achat</span><span class="sxs-lookup"><span data-stu-id="59977-133">Lesson 4: Perform an Insert Operation on the Purchase Order Table</span></span>](../../adapters-and-accelerators/adapter-sql/lesson-4-perform-an-insert-operation-on-the-purchase-order-table.md)  
  
-   [<span data-ttu-id="59977-134">Leçon 5 : Déployer la Solution</span><span class="sxs-lookup"><span data-stu-id="59977-134">Lesson 5: Deploy the Solution</span></span>](../../adapters-and-accelerators/adapter-sql/lesson-5-deploy-the-solution.md)