---
title: "Étape 1 : Créer le Message de demande pour l’opération d’insertion sur la Table de Purchase_Order | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fde018d8-9d9a-42ea-8ee9-e3632450b9d7
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 71021bb0a9bbb71f17f0899e625ac184f9087429
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="step-1-create-the-request-message-for-insert-operation-on-purchaseorder-table"></a><span data-ttu-id="14e4b-102">Étape 1 : Créer le Message de demande pour l’opération d’insertion sur la Table de Purchase_Order</span><span class="sxs-lookup"><span data-stu-id="14e4b-102">Step 1: Create the Request Message for Insert Operation on Purchase_Order Table</span></span>
<span data-ttu-id="14e4b-103">![Étape 1 sur 4](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-1of4.gif "Step_1of4")</span><span class="sxs-lookup"><span data-stu-id="14e4b-103">![Step 1 of 4](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-1of4.gif "Step_1of4")</span></span>  
  
 <span data-ttu-id="14e4b-104">**Durée :** 10 minutes</span><span class="sxs-lookup"><span data-stu-id="14e4b-104">**Time to complete:** 10 minutes</span></span>  
  
 <span data-ttu-id="14e4b-105">**Objectif :** dans cette étape, vous ajoutez un projet de bibliothèque de classes c# à votre solution.</span><span class="sxs-lookup"><span data-stu-id="14e4b-105">**Objective:** In this step, you add a C# class library project to your solution.</span></span> <span data-ttu-id="14e4b-106">Cette bibliothèque crée un message de demande de mémoire pour l’opération d’insertion sur la **Purchase_Order** table.</span><span class="sxs-lookup"><span data-stu-id="14e4b-106">This library creates an in-memory request message for the Insert operation on the **Purchase_Order** table.</span></span> <span data-ttu-id="14e4b-107">Dans les étapes ultérieures, l’orchestration envoie ce message à SQL Server pour insérer des enregistrements dans la table.</span><span class="sxs-lookup"><span data-stu-id="14e4b-107">In later steps, the orchestration sends this message to SQL Server to insert records in the table.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="14e4b-108">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="14e4b-108">Prerequisites</span></span>  
 <span data-ttu-id="14e4b-109">Vous devez avoir terminé les étapes de [leçon 3 : exécuter une procédure stockée pour sélectionnez Nouveau employés ajouté](../../adapters-and-accelerators/adapter-sql/lesson-3-execute-a-stored-procedure-to-select-new-employees-added.md).</span><span class="sxs-lookup"><span data-stu-id="14e4b-109">You must have completed the steps in [Lesson 3: Execute a Stored Procedure to Select New Employees Added](../../adapters-and-accelerators/adapter-sql/lesson-3-execute-a-stored-procedure-to-select-new-employees-added.md).</span></span>  
  
### <a name="to-create-a-request-message-for-insert-operation"></a><span data-ttu-id="14e4b-110">Pour créer un message de demande pour l’opération d’insertion</span><span class="sxs-lookup"><span data-stu-id="14e4b-110">To create a request message for Insert operation</span></span>  
  
1.  <span data-ttu-id="14e4b-111">Ajouter un projet de bibliothèque de classes Visual c# à votre solution.</span><span class="sxs-lookup"><span data-stu-id="14e4b-111">Add a Visual C# class library project to your solution.</span></span> <span data-ttu-id="14e4b-112">Pour le nom du projet, tapez `UpdatePOMessageCreator`.</span><span class="sxs-lookup"><span data-stu-id="14e4b-112">For the name of the project, type `UpdatePOMessageCreator`.</span></span>  
  
2.  <span data-ttu-id="14e4b-113">Renommer **Class1.cs** à **UpdatePOMessageCreator.cs**.</span><span class="sxs-lookup"><span data-stu-id="14e4b-113">Rename **Class1.cs** to **UpdatePOMessageCreator.cs**.</span></span>  
  
3.  <span data-ttu-id="14e4b-114">Copiez le code suivant dans le fichier .cs :</span><span class="sxs-lookup"><span data-stu-id="14e4b-114">Copy the following code to the .cs file:</span></span>  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.Text;  
    using System.Xml;  
    using System.IO;  
  
    namespace UpdatePOMessageCreator  
    {  
        public class UpdatePOMessageCreator  
        {  
            private static XmlDocument Message;  
            private static string XmlFileLocation;  
            private static string ResponseDoc;  
  
            public static XmlDocument XMLMessageCreator()  
            {  
                XmlFileLocation = "C:\\TestLocation\\CreatePOMessage";  
                try  
                {  
                    ResponseDoc = (Directory.GetFiles(XmlFileLocation, "*.xml", SearchOption.TopDirectoryOnly))[0];  
                }  
                catch (Exception ex)  
                {  
                    Console.WriteLine("Trying to get XML from: " + XmlFileLocation);  
                    Console.WriteLine("EXCEPTION: " + ex.ToString());  
                    throw ex;  
                }  
  
                //Create Message From XML  
                Message = new XmlDocument();  
  
                Message.PreserveWhitespace = true;  
  
                Message.Load(ResponseDoc);  
  
                return Message;  
            }  
        }  
    }  
  
    ```  
  
     <span data-ttu-id="14e4b-115">Cet extrait de code attend un message de demande pour l’opération d’insertion sur la **Purchase_Order** table se trouver devant C:\TestLocation\CreatePOMessage.</span><span class="sxs-lookup"><span data-stu-id="14e4b-115">This code snippet expects a request message for the Insert operation on the **Purchase_Order** table to be present at C:\TestLocation\CreatePOMessage.</span></span> <span data-ttu-id="14e4b-116">Le code utilise le message de demande pour créer un message de demande similaire au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="14e4b-116">The code uses the request message to create a similar request message at run time.</span></span>  
  
4.  <span data-ttu-id="14e4b-117">Ajouter un fichier de clé de nom fort au projet.</span><span class="sxs-lookup"><span data-stu-id="14e4b-117">Add a strong-name key file to the project.</span></span> <span data-ttu-id="14e4b-118">Pour obtenir des instructions sur la création d’un fichier de clé de nom fort, consultez [conditions préalables requises pour créer des applications SQL à l’aide de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/prerequisites-to-create-sql-applications-using-the-sql-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="14e4b-118">For instructions on creating a strong-name key file, see [Prerequisites to create SQL applications using the SQL adapter](../../adapters-and-accelerators/adapter-sql/prerequisites-to-create-sql-applications-using-the-sql-adapter.md).</span></span>  
  
    1.  <span data-ttu-id="14e4b-119">Dans l’Explorateur de solutions, cliquez sur le **UpdatePOMessageCreator** projet puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="14e4b-119">In the Solution Explorer, right-click the **UpdatePOMessageCreator** project and click **Properties**.</span></span>  
  
    2.  <span data-ttu-id="14e4b-120">Dans le **propriété** fenêtre, cliquez sur **signature**.</span><span class="sxs-lookup"><span data-stu-id="14e4b-120">In the **Property** window, click **Signing**.</span></span>  
  
    3.  <span data-ttu-id="14e4b-121">Dans le **signature** onglet, sélectionnez le **signer l’assembly** case à cocher.</span><span class="sxs-lookup"><span data-stu-id="14e4b-121">In the **Signing** tab, select the **Sign the assembly** check box.</span></span>  
  
    4.  <span data-ttu-id="14e4b-122">À partir de la **choisir un fichier de clé de nom fort** , cliquez sur  **\<Parcourir\>**.</span><span class="sxs-lookup"><span data-stu-id="14e4b-122">From the **Choose a strong-name key file** list, click **\<Browse\>**.</span></span>  
  
    5.  <span data-ttu-id="14e4b-123">Accédez au dossier où vous avez créé le fichier de clé de nom fort, puis cliquez sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="14e4b-123">Navigate to the folder where you created the strong-name key file, and then click **Open**.</span></span>  
  
    6.  <span data-ttu-id="14e4b-124">Cliquez sur **enregistrer** sur la **Standard** barre de menus.</span><span class="sxs-lookup"><span data-stu-id="14e4b-124">Click **Save** on the **Standard** menu bar.</span></span> <span data-ttu-id="14e4b-125">Fermer le **propriété** fenêtre.</span><span class="sxs-lookup"><span data-stu-id="14e4b-125">Close the **Property** window.</span></span>  
  
5.  <span data-ttu-id="14e4b-126">créer le projet ;</span><span class="sxs-lookup"><span data-stu-id="14e4b-126">Build the project.</span></span> <span data-ttu-id="14e4b-127">Cliquez sur le projet, puis cliquez sur **Build**.</span><span class="sxs-lookup"><span data-stu-id="14e4b-127">Right-click the project and click **Build**.</span></span>  
  
6.  <span data-ttu-id="14e4b-128">Ajoutez une référence de projet au projet BizTalk dans la solution.</span><span class="sxs-lookup"><span data-stu-id="14e4b-128">Add a reference of this project to the BizTalk project in the solution.</span></span>  
  
    1.  <span data-ttu-id="14e4b-129">Dans l’Explorateur de solutions, développez le projet BizTalk, cliquez sur **références**, puis cliquez sur **ajouter une référence**.</span><span class="sxs-lookup"><span data-stu-id="14e4b-129">In the Solution Explorer, expand the BizTalk project, right-click **References**, and then click **Add Reference**.</span></span>  
  
    2.  <span data-ttu-id="14e4b-130">Dans le **ajouter une référence** boîte de dialogue, cliquez sur le **projets** onglet.</span><span class="sxs-lookup"><span data-stu-id="14e4b-130">In the **Add Reference** dialog box, click the **Projects** tab.</span></span>  
  
    3.  <span data-ttu-id="14e4b-131">Dans la liste des noms de projet, sélectionnez **UpdatePOMessageCreator**, cliquez sur **ajouter**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="14e4b-131">From the list of project names, select **UpdatePOMessageCreator**, click **Add**, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="14e4b-132">Création du projet crée la DLL d’assembly dans le dossier \bin\Debug du projet.</span><span class="sxs-lookup"><span data-stu-id="14e4b-132">Building the project creates the assembly DLL under \bin\Debug folder of the project.</span></span> <span data-ttu-id="14e4b-133">Vous devez ajouter cette DLL pour le Global Assembly Cache (GAC).</span><span class="sxs-lookup"><span data-stu-id="14e4b-133">You must add this DLL to the Global Assembly Cache (GAC).</span></span>  
  
    1.  <span data-ttu-id="14e4b-134">Démarrez une invite de commandes Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="14e4b-134">Start a Visual Studio Command Prompt.</span></span>  
  
    2.  <span data-ttu-id="14e4b-135">À partir de l’invite de commandes, accédez au dossier \bin\Debug\ de la **UpdatePOMessageCreator** projet.</span><span class="sxs-lookup"><span data-stu-id="14e4b-135">From the command prompt, navigate to the \bin\Debug\ folder of the **UpdatePOMessageCreator** project.</span></span>  
  
    3.  <span data-ttu-id="14e4b-136">Sur l’invite de commandes, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="14e4b-136">Run the following command on the command prompt:</span></span>  
  
        ```  
        gacutil /i UpdatePOMessageCreator.dll  
        ```  
  
## <a name="what-did-i-just-do"></a><span data-ttu-id="14e4b-137">Actions effectuées</span><span class="sxs-lookup"><span data-stu-id="14e4b-137">What did I just do?</span></span>  
 <span data-ttu-id="14e4b-138">Dans cette étape, vous avez ajouté un projet de bibliothèque de classes UpdatePOMessageCreator qui crée un message de demande au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="14e4b-138">In this step, you added an UpdatePOMessageCreator class library project that creates request message at run-time.</span></span> <span data-ttu-id="14e4b-139">Vous ajouté la référence à ce projet dans le projet BizTalk et également ajouter la DLL d’assembly dans le GAC.</span><span class="sxs-lookup"><span data-stu-id="14e4b-139">You added the reference to this project in the BizTalk project and also added the assembly DLL to the GAC.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="14e4b-140">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="14e4b-140">Next Steps</span></span>  
 <span data-ttu-id="14e4b-141">Vous mappez le message de réponse pour la procédure stockée de UPDATE_EMPLOYEE au message de demande pour l’opération d’insertion sur **Purchaser_Order** table.</span><span class="sxs-lookup"><span data-stu-id="14e4b-141">You map the response message for the UPDATE_EMPLOYEE stored procedure to the request message for the Insert operation on **Purchaser_Order** table.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14e4b-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="14e4b-142">See Also</span></span>  
 <span data-ttu-id="14e4b-143">[Étape 2 : Mapper le Message de réponse UPDATE_EMPLOYEE insérer le Message de demande d’opération](../../adapters-and-accelerators/adapter-sql/step-2-map-update_employee-response-to-insert-operation-request.md) </span><span class="sxs-lookup"><span data-stu-id="14e4b-143">[Step 2: Map the UPDATE_EMPLOYEE Response Message to Insert Operation Request Message](../../adapters-and-accelerators/adapter-sql/step-2-map-update_employee-response-to-insert-operation-request.md) </span></span>  
 [<span data-ttu-id="14e4b-144">Leçon 4 : Effectuer une opération d’insertion sur la table des bons de commande</span><span class="sxs-lookup"><span data-stu-id="14e4b-144">Lesson 4: Perform an Insert Operation on the Purchase Order Table</span></span>](../../adapters-and-accelerators/adapter-sql/lesson-4-perform-an-insert-operation-on-the-purchase-order-table.md)