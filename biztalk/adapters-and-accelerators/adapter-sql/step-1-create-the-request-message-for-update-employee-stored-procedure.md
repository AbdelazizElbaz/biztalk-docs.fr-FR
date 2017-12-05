---
title: "Étape 1 : Créer le Message de demande pour UPDATE_EMPLOYEE procédure stockée | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4dd975d9-4b38-46e0-a926-4b325b0d7b5e
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4e30225b79b14ffc237798ddde6f3fe40fb4aea9
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="step-1-create-the-request-message-for-updateemployee-stored-procedure"></a><span data-ttu-id="7de10-102">Étape 1 : Créer le Message de demande pour UPDATE_EMPLOYEE procédure stockée</span><span class="sxs-lookup"><span data-stu-id="7de10-102">Step 1: Create the Request Message for UPDATE_EMPLOYEE Stored Procedure</span></span>
<span data-ttu-id="7de10-103">![Étape 1 sur 2](../../adapters-and-accelerators/adapter-sql/media/step-1of2.gif "Step_1of2")</span><span class="sxs-lookup"><span data-stu-id="7de10-103">![Step 1 of 2](../../adapters-and-accelerators/adapter-sql/media/step-1of2.gif "Step_1of2")</span></span>  
  
 <span data-ttu-id="7de10-104">**Durée :** 10 minutes</span><span class="sxs-lookup"><span data-stu-id="7de10-104">**Time to complete:** 10 minutes</span></span>  
  
 <span data-ttu-id="7de10-105">**Objectif :** dans cette étape, vous ajoutez un projet de bibliothèque de classes c# à votre solution.</span><span class="sxs-lookup"><span data-stu-id="7de10-105">**Objective:** In this step, you add a C# class library project to your solution.</span></span> <span data-ttu-id="7de10-106">Cette bibliothèque crée un message de demande de mémoire pour le **UPDATE_EMPLOYEE** procédure stockée.</span><span class="sxs-lookup"><span data-stu-id="7de10-106">This library creates an in-memory request message for the **UPDATE_EMPLOYEE** stored procedure.</span></span> <span data-ttu-id="7de10-107">Dans les étapes ultérieures, l’orchestration envoie ce message à SQL Server pour exécuter la procédure stockée.</span><span class="sxs-lookup"><span data-stu-id="7de10-107">In later steps, the orchestration sends this message to SQL Server to execute the stored procedure.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="7de10-108">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="7de10-108">Prerequisites</span></span>  
 <span data-ttu-id="7de10-109">Vous devez avoir terminé les étapes de [leçon 2 : recevoir des Notifications de filtre et](../../adapters-and-accelerators/adapter-sql/lesson-2-receive-and-filter-notifications.md).</span><span class="sxs-lookup"><span data-stu-id="7de10-109">You must have completed the steps in [Lesson 2: Receive and Filter Notifications](../../adapters-and-accelerators/adapter-sql/lesson-2-receive-and-filter-notifications.md).</span></span>  
  
### <a name="to-create-a-request-message-for-updateemployee-stored-procedure"></a><span data-ttu-id="7de10-110">Pour créer un message de demande pour UPDATE_EMPLOYEE procédure stockée</span><span class="sxs-lookup"><span data-stu-id="7de10-110">To create a request message for UPDATE_EMPLOYEE stored procedure</span></span>  
  
1.  <span data-ttu-id="7de10-111">Ajouter un projet de bibliothèque de classes Visual c# à votre solution.</span><span class="sxs-lookup"><span data-stu-id="7de10-111">Add a Visual C# class library project to your solution.</span></span> <span data-ttu-id="7de10-112">Pour le nom du projet, tapez `UpdateEmployeeMessageCreator`.</span><span class="sxs-lookup"><span data-stu-id="7de10-112">For the name of the project, type `UpdateEmployeeMessageCreator`.</span></span>  
  
2.  <span data-ttu-id="7de10-113">Renommer **Class1.cs** à **UpdateEmployeeMessageCreator.cs**.</span><span class="sxs-lookup"><span data-stu-id="7de10-113">Rename **Class1.cs** to **UpdateEmployeeMessageCreator.cs**.</span></span>  
  
3.  <span data-ttu-id="7de10-114">Copiez le code suivant dans le fichier .cs :</span><span class="sxs-lookup"><span data-stu-id="7de10-114">Copy the following code to the .cs file:</span></span>  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.Text;  
    using System.Xml;  
    using System.IO;  
  
    namespace UpdateEmployeeMessageCreator  
    {  
        public class UpdateEmployeeMessageCreator  
        {  
            private static XmlDocument Message;  
            private static string XmlFileLocation;  
            private static string ResponseDoc;  
  
            public static XmlDocument XMLMessageCreator()  
            {  
                XmlFileLocation = "C:\\TestLocation\\CreateEmployeeMessage";  
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
  
     <span data-ttu-id="7de10-115">Cet extrait de code attend un message de demande pour le **UPDATE_EMPLOYEE** une procédure stockée à être présentes au C:\TestLocation\CreateEmployeeMessage.</span><span class="sxs-lookup"><span data-stu-id="7de10-115">This code snippet expects a request message for the **UPDATE_EMPLOYEE** stored procedure to be present at C:\TestLocation\CreateEmployeeMessage.</span></span> <span data-ttu-id="7de10-116">Le code utilise le message de demande pour créer un message de demande similaire au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="7de10-116">The code uses the request message to create a similar request message at run time.</span></span>  
  
4.  <span data-ttu-id="7de10-117">Ajouter un fichier de clé de nom fort au projet.</span><span class="sxs-lookup"><span data-stu-id="7de10-117">Add a strong-name key file to the project.</span></span> <span data-ttu-id="7de10-118">Consultez [conditions préalables requises pour créer des applications SQL à l’aide de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/prerequisites-to-create-sql-applications-using-the-sql-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="7de10-118">See [Prerequisites to create SQL applications using the SQL adapter](../../adapters-and-accelerators/adapter-sql/prerequisites-to-create-sql-applications-using-the-sql-adapter.md).</span></span>  
  
    1.  <span data-ttu-id="7de10-119">Dans l’Explorateur de solutions, cliquez sur le **UpdateEmployeeMessageCreator** de projet, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="7de10-119">In the Solution Explorer, right-click the **UpdateEmployeeMessageCreator** project, and then click **Properties**.</span></span>  
  
    2.  <span data-ttu-id="7de10-120">Dans le **propriété** fenêtre, cliquez sur **signature**.</span><span class="sxs-lookup"><span data-stu-id="7de10-120">In the **Property** window, click **Signing**.</span></span>  
  
    3.  <span data-ttu-id="7de10-121">Dans le **signature** onglet, sélectionnez le **signer l’assembly** case à cocher.</span><span class="sxs-lookup"><span data-stu-id="7de10-121">In the **Signing** tab, select the **Sign the assembly** check box.</span></span>  
  
    4.  <span data-ttu-id="7de10-122">À partir de la **choisir un fichier de clé de nom fort** , cliquez sur  **\<Parcourir\>**.</span><span class="sxs-lookup"><span data-stu-id="7de10-122">From the **Choose a strong-name key file** list, click **\<Browse\>**.</span></span>  
  
    5.  <span data-ttu-id="7de10-123">Accédez au dossier où vous avez créé le fichier de clé de nom fort, puis cliquez sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="7de10-123">Navigate to the folder where you created the strong-name key file, and then click **Open**.</span></span>  
  
    6.  <span data-ttu-id="7de10-124">Cliquez sur **enregistrer** sur la barre de menus Standard.</span><span class="sxs-lookup"><span data-stu-id="7de10-124">Click **Save** on the Standard menu bar.</span></span> <span data-ttu-id="7de10-125">Fermer le **propriété** fenêtre.</span><span class="sxs-lookup"><span data-stu-id="7de10-125">Close the **Property** window.</span></span>  
  
5.  <span data-ttu-id="7de10-126">créer le projet ;</span><span class="sxs-lookup"><span data-stu-id="7de10-126">Build the project.</span></span> <span data-ttu-id="7de10-127">Cliquez sur le projet, puis cliquez sur **Build**.</span><span class="sxs-lookup"><span data-stu-id="7de10-127">Right-click the project, and then click **Build**.</span></span>  
  
6.  <span data-ttu-id="7de10-128">Ajoutez une référence de projet au projet BizTalk dans la solution.</span><span class="sxs-lookup"><span data-stu-id="7de10-128">Add a reference of this project to the BizTalk project in the solution.</span></span>  
  
    1.  <span data-ttu-id="7de10-129">Dans l’Explorateur de solutions, développez le projet BizTalk, cliquez sur **références**, puis cliquez sur **ajouter une référence**.</span><span class="sxs-lookup"><span data-stu-id="7de10-129">In the Solution Explorer, expand the BizTalk project, right-click **References**, and then click **Add Reference**.</span></span>  
  
    2.  <span data-ttu-id="7de10-130">Dans le **ajouter une référence** boîte de dialogue, cliquez sur le **projets** onglet.</span><span class="sxs-lookup"><span data-stu-id="7de10-130">In the **Add Reference** dialog box, click the **Projects** tab.</span></span>  
  
    3.  <span data-ttu-id="7de10-131">Dans la liste des noms de projet, sélectionnez **UpdateEmployeeMessageCreator**, cliquez sur **ajouter**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="7de10-131">From the list of project names, select **UpdateEmployeeMessageCreator**, click **Add**, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="7de10-132">Création du projet crée la DLL d’assembly dans le dossier \bin\Debug du projet.</span><span class="sxs-lookup"><span data-stu-id="7de10-132">Building the project creates the assembly DLL under \bin\Debug folder of the project.</span></span> <span data-ttu-id="7de10-133">Vous devez ajouter cette DLL pour le Global Assembly Cache (GAC).</span><span class="sxs-lookup"><span data-stu-id="7de10-133">You must add this DLL to the Global Assembly Cache (GAC).</span></span>  
  
    1.  <span data-ttu-id="7de10-134">Démarrez une invite de commandes Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7de10-134">Start a Visual Studio Command Prompt.</span></span>  
  
    2.  <span data-ttu-id="7de10-135">À partir de l’invite de commandes, accédez au dossier \bin\Debug\ de la **UpdateEmployeeMessageCreator** projet.</span><span class="sxs-lookup"><span data-stu-id="7de10-135">From the command prompt, navigate to the \bin\Debug\ folder of the **UpdateEmployeeMessageCreator** project.</span></span>  
  
    3.  <span data-ttu-id="7de10-136">Sur l’invite de commandes, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="7de10-136">Run the following command on the command prompt:</span></span>  
  
        ```  
        gacutil /i UpdateEmployeeMessageCreator.dll  
        ```  
  
## <a name="what-did-i-just-do"></a><span data-ttu-id="7de10-137">Actions effectuées</span><span class="sxs-lookup"><span data-stu-id="7de10-137">What did I just do?</span></span>  
 <span data-ttu-id="7de10-138">Dans cette étape, vous avez ajouté un projet de bibliothèque de classes UpdateEmployeeMessageCreator qui crée un message de demande au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="7de10-138">In this step, you added an UpdateEmployeeMessageCreator class library project that creates request message at run-time.</span></span> <span data-ttu-id="7de10-139">Vous ajouté la référence à ce projet dans le projet BizTalk et également ajouter la DLL d’assembly dans le GAC.</span><span class="sxs-lookup"><span data-stu-id="7de10-139">You added the reference to this project in the BizTalk project and also added the assembly DLL to the GAC.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="7de10-140">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="7de10-140">Next Steps</span></span>  
 <span data-ttu-id="7de10-141">Envoyer le message de demande à SQL Server et de recevoir la réponse, comme décrit dans [étape 2 : envoyer le Message de demande à SQL Server et de recevoir une réponse](../../adapters-and-accelerators/adapter-sql/step-2-send-the-request-message-to-sql-server-and-receive-response.md).</span><span class="sxs-lookup"><span data-stu-id="7de10-141">You send the request message to SQL Server and receive the response, as described in [Step 2: Send the Request Message to SQL Server and Receive Response](../../adapters-and-accelerators/adapter-sql/step-2-send-the-request-message-to-sql-server-and-receive-response.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7de10-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7de10-142">See Also</span></span>  
 [<span data-ttu-id="7de10-143">Leçon 3 : Exécuter une procédure stockée pour sélectionner les nouveaux employés ajoutés</span><span class="sxs-lookup"><span data-stu-id="7de10-143">Lesson 3: Execute a Stored Procedure to Select New Employees Added</span></span>](../../adapters-and-accelerators/adapter-sql/lesson-3-execute-a-stored-procedure-to-select-new-employees-added.md)