---
title: "Étape 4 : Tester l’Application | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 488b13fa-7a71-4430-bbf5-dbf47ba55562
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 347c2bcf459d7e9ce7b1fb9efc07579be81d989d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-4-test-the-application"></a><span data-ttu-id="b8561-102">Étape 4 : Tester l’Application</span><span class="sxs-lookup"><span data-stu-id="b8561-102">Step 4: Test the Application</span></span>
<span data-ttu-id="b8561-103">![Étape 4 sur 4](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-4of4.gif "Step_4of4")</span><span class="sxs-lookup"><span data-stu-id="b8561-103">![Step 4 of 4](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-4of4.gif "Step_4of4")</span></span>  
  
 <span data-ttu-id="b8561-104">**Durée :** 10 minutes</span><span class="sxs-lookup"><span data-stu-id="b8561-104">**Time to complete:** 10 minutes</span></span>  
  
 <span data-ttu-id="b8561-105">**Objectif :** dans cette étape, vous testez l’application en insérant un enregistrement dans le **employé** table de la **ADAPTER_SAMPLES** base de données.</span><span class="sxs-lookup"><span data-stu-id="b8561-105">**Objective:** In this step, you test the application by inserting a record in the **Employee** table of the **ADAPTER_SAMPLES** database.</span></span> <span data-ttu-id="b8561-106">Si l’application fonctionne correctement, l’orchestration reçoit une notification pour les modifications apportées à la **employé** table.</span><span class="sxs-lookup"><span data-stu-id="b8561-106">If the application is working properly, the orchestration receives a notification for changes to the **Employee** table.</span></span> <span data-ttu-id="b8561-107">L’orchestration extrait le type de notification reçue.</span><span class="sxs-lookup"><span data-stu-id="b8561-107">The orchestration then extracts the type of notification received.</span></span> <span data-ttu-id="b8561-108">Si la notification est pour une opération d’insertion, l’orchestration exécute la **UPDATE_EMPLOYEE** procédure stockée et reçoit une réponse.</span><span class="sxs-lookup"><span data-stu-id="b8561-108">If the notification is for an Insert operation, the orchestration executes the **UPDATE_EMPLOYEE** stored procedure and receives a response.</span></span> <span data-ttu-id="b8561-109">L’orchestration extrait les valeurs de **Employee_ID** et **nom** à partir de la réponse et les insère dans le **Purchase_Order** table.</span><span class="sxs-lookup"><span data-stu-id="b8561-109">The orchestration extracts the values of **Employee_ID** and **Name** from the response and inserts them into the **Purchase_Order** table.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="b8561-110">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="b8561-110">Prerequisites</span></span>  
 <span data-ttu-id="b8561-111">Avant de commencer cette étape, vous devez vérifier les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="b8561-111">Before starting with this step, you must ensure the following:</span></span>  
  
-   <span data-ttu-id="b8561-112">Un message de demande pour appeler le **UPDATE_EMPLOYEE** procédure stockée est disponible à l’adresse C:\TestLocation\CreateEmployeeMessage.</span><span class="sxs-lookup"><span data-stu-id="b8561-112">A request message to invoke the **UPDATE_EMPLOYEE** stored procedure is available at C:\TestLocation\CreateEmployeeMessage.</span></span> <span data-ttu-id="b8561-113">Le message de demande ressemble à ceci :</span><span class="sxs-lookup"><span data-stu-id="b8561-113">The request message looks like the following:</span></span>  
  
    ```  
    <UPDATE_EMPLOYEE xmlns="http://schemas.microsoft.com/Sql/2008/05/TypedProcedures/dbo" />  
    ```  
  
-   <span data-ttu-id="b8561-114">Un message de demande à appeler l’opération d’insertion sur la **Purchase_Order** table est disponible à l’adresse C:\TestLocation\CreatePOMessage.</span><span class="sxs-lookup"><span data-stu-id="b8561-114">A request message to invoke the Insert operation on the **Purchase_Order** table is available at C:\TestLocation\CreatePOMessage.</span></span> <span data-ttu-id="b8561-115">Le message de demande ressemble à ceci :</span><span class="sxs-lookup"><span data-stu-id="b8561-115">The request message looks like the following:</span></span>  
  
    ```  
    <Insert xmlns="http://schemas.microsoft.com/Sql/2008/05/TableOp/dbo/Purchase_Order">  
      <Rows>  
        <Purchase_Order xmlns="http://schemas.microsoft.com/Sql/2008/05/Types/Tables/dbo">  
          <Employee_ID>10</Employee_ID><Employee_Name>Employee_Name</Employee_Name>  
        </Purchase_Order>  
      </Rows>  
    </Insert>  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="b8561-116">Les valeurs pour le **Employee_ID** et **Employee_Name** champs sont des espaces réservés.</span><span class="sxs-lookup"><span data-stu-id="b8561-116">The values for the **Employee_ID** and **Employee_Name** fields are placeholders.</span></span> <span data-ttu-id="b8561-117">Les valeurs réelles sont insérés par l’orchestration au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="b8561-117">The actual values are inserted by the orchestration at run-time.</span></span>  
  
-   <span data-ttu-id="b8561-118">Vous devez avoir terminé [étape 3 : configurer et démarrer l’Application](../../adapters-and-accelerators/adapter-sql/step-3-configure-and-start-the-application.md).</span><span class="sxs-lookup"><span data-stu-id="b8561-118">You must have completed [Step 3: Configure and Start the Application](../../adapters-and-accelerators/adapter-sql/step-3-configure-and-start-the-application.md).</span></span>  
  
### <a name="to-test-the-application"></a><span data-ttu-id="b8561-119">Pour tester l'application</span><span class="sxs-lookup"><span data-stu-id="b8561-119">To test the application</span></span>  
  
1.  <span data-ttu-id="b8561-120">Insérer un enregistrement dans le **employé** table.</span><span class="sxs-lookup"><span data-stu-id="b8561-120">Insert a record in the **Employee** table.</span></span> <span data-ttu-id="b8561-121">Vous pouvez le faire en exécutant l’instruction suivante à partir de SQL Server Management Studio.</span><span class="sxs-lookup"><span data-stu-id="b8561-121">You can do so by running the following statement from SQL Server Management Studio.</span></span>  
  
    ```  
    INSERT INTO [ADAPTER_SAMPLES].[dbo].[Employee] ([Name] ,[Designation] ,[Salary])  
    VALUES('John Smith' ,'Manager' ,500000)  
    ```  
  
2.  <span data-ttu-id="b8561-122">Vérifiez le **employé** table dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="b8561-122">Check the **Employee** table in the database.</span></span> <span data-ttu-id="b8561-123">Vous remarquerez que le nouvel enregistrement est ajouté par le **état** colonne est « 0 ».</span><span class="sxs-lookup"><span data-stu-id="b8561-123">You will notice that the new record is added by the **Status** column is “0.”</span></span>  
  
3.  <span data-ttu-id="b8561-124">Conserver l’actualisation du **employé** enregistrements de la table.</span><span class="sxs-lookup"><span data-stu-id="b8561-124">Keep refreshing the **Employee** table records.</span></span> <span data-ttu-id="b8561-125">Vous remarquerez que la **état** colonne pour le nouvel enregistrement est maintenant définie sur « 1 ».</span><span class="sxs-lookup"><span data-stu-id="b8561-125">You will notice that the **Status** column for the new record is now set to “1.”</span></span>  
  
4.  <span data-ttu-id="b8561-126">Vérifiez le **Purchase_Order** table.</span><span class="sxs-lookup"><span data-stu-id="b8561-126">Check the **Purchase_Order** table.</span></span> <span data-ttu-id="b8561-127">Vous remarquerez qu’un enregistrement avec le même nom de l’employé et désignation, que vous avez fourni dans l’instruction Insert, est ajouté à la table.</span><span class="sxs-lookup"><span data-stu-id="b8561-127">You will notice that a record with the same employee name and designation, as you provided in the Insert statement, is added to the table.</span></span>  
  
5.  <span data-ttu-id="b8561-128">Si vous avez fourni votre alias de messagerie dans la configuration du port SMTP, vous recevrez un message électronique avec le message de réponse pour l’opération d’insertion.</span><span class="sxs-lookup"><span data-stu-id="b8561-128">If you provided your e-mail alias in the SMTP port configuration, you will also receive an e-mail with the response message for the Insert operation.</span></span>  
  
## <a name="what-did-i-just-do"></a><span data-ttu-id="b8561-129">Actions effectuées</span><span class="sxs-lookup"><span data-stu-id="b8561-129">What did I just do?</span></span>  
 <span data-ttu-id="b8561-130">Tester l’application SampleApplication en insérant un enregistrement dans le **employé** table.</span><span class="sxs-lookup"><span data-stu-id="b8561-130">Tested the SampleApplication application by inserting a record in the **Employee** table.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="b8561-131">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="b8561-131">Next Steps</span></span>  
 <span data-ttu-id="b8561-132">Si le test a réussi, félicitations !</span><span class="sxs-lookup"><span data-stu-id="b8561-132">If the test worked, congratulations!</span></span> <span data-ttu-id="b8561-133">Vous avez terminé la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] didacticiel.</span><span class="sxs-lookup"><span data-stu-id="b8561-133">You have completed the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] tutorial.</span></span>  
  
 <span data-ttu-id="b8561-134">Si le test a échoué, vérifiez votre travail avec attention et assurez-vous d'avoir ajouté les objets nécessaires et défini correctement leurs propriétés.</span><span class="sxs-lookup"><span data-stu-id="b8561-134">If the test did not work, carefully check your work to make sure that you added all of the necessary objects and set their properties correctly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8561-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b8561-135">See Also</span></span>  
 <span data-ttu-id="b8561-136">[Étape 3 : Configurer et démarrer l’Application](../../adapters-and-accelerators/adapter-sql/step-3-configure-and-start-the-application.md) </span><span class="sxs-lookup"><span data-stu-id="b8561-136">[Step 3: Configure and Start the Application](../../adapters-and-accelerators/adapter-sql/step-3-configure-and-start-the-application.md) </span></span>  
 [<span data-ttu-id="b8561-137">Leçon 5 : Déployer la Solution</span><span class="sxs-lookup"><span data-stu-id="b8561-137">Lesson 5: Deploy the Solution</span></span>](../../adapters-and-accelerators/adapter-sql/lesson-5-deploy-the-solution.md)