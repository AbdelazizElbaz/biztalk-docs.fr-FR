---
title: "Étape 4 : Création du projet de HeaderHelper | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects, helper projects
- private process tutorial, creating helper projects
ms.assetid: 82413537-032a-4368-8d77-d024a7c83b0b
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2525e0e87106e2eeb82fb05b52b3ec69d4be876d
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="step-4-creating-the-headerhelper-project"></a><span data-ttu-id="bb5cd-102">Étape 4 : Création du projet de HeaderHelper</span><span class="sxs-lookup"><span data-stu-id="bb5cd-102">Step 4: Creating the HeaderHelper Project</span></span>
<span data-ttu-id="bb5cd-103">Dans cette étape, vous allez créer une [!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)] bibliothèque de classes.</span><span class="sxs-lookup"><span data-stu-id="bb5cd-103">In this step, you create a [!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)] class library.</span></span> <span data-ttu-id="bb5cd-104">Lorsqu’une orchestration de processus privé reçoit un message entrant, la bibliothèque HeaderHelper détermine si la conversion d’un document est requise et si elle est nécessaire, effectue cette conversion.</span><span class="sxs-lookup"><span data-stu-id="bb5cd-104">When a private process orchestration receives an incoming message, the HeaderHelper library determines whether a document conversion is required and if it is required, performs that conversion.</span></span> <span data-ttu-id="bb5cd-105">Cela permet à l’orchestration de travailler avec différentes versions des documents de Framework RNIF (RosettaNet Implementation).</span><span class="sxs-lookup"><span data-stu-id="bb5cd-105">This lets your orchestration work with different versions of RosettaNet Implementation Framework (RNIF) documents.</span></span> <span data-ttu-id="bb5cd-106">En outre, lorsqu’un message de réponse 3A2 est envoyé, la bibliothèque HeaderHelper effectue une conversion de documents supplémentaires avant de transmettre le message.</span><span class="sxs-lookup"><span data-stu-id="bb5cd-106">Additionally, when a 3A2 response message is sent, the HeaderHelper library performs an additional document conversion before transmitting the message.</span></span>  
  
### <a name="to-create-the-headerhelper-project"></a><span data-ttu-id="bb5cd-107">Pour créer le projet HeaderHelper</span><span class="sxs-lookup"><span data-stu-id="bb5cd-107">To create the HeaderHelper project</span></span>  
  
1.  <span data-ttu-id="bb5cd-108">Dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], dans l’Explorateur de solutions, cliquez sur la solution Contoso, pointez sur **ajouter**, puis cliquez sur **nouveau projet**.</span><span class="sxs-lookup"><span data-stu-id="bb5cd-108">In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], in Solution Explorer, right-click the Contoso solution, point to **Add**, and then click **New Project**.</span></span>  
  
2.  <span data-ttu-id="bb5cd-109">Dans la boîte de dialogue Ajouter un nouveau projet, dans le volet Types de projets, sélectionnez **Visual C#**.</span><span class="sxs-lookup"><span data-stu-id="bb5cd-109">In the Add New Project dialog box, in the Project Types pane, select **Visual C#**.</span></span>  
  
3.  <span data-ttu-id="bb5cd-110">Dans le volet Modèles, sélectionnez le **bibliothèque de classes** modèle.</span><span class="sxs-lookup"><span data-stu-id="bb5cd-110">In the Templates pane, select the **Class Library** template.</span></span>  
  
4.  <span data-ttu-id="bb5cd-111">Dans le **nom** , tapez **HeaderHelper**, puis cliquez sur **OK** pour créer le projet.</span><span class="sxs-lookup"><span data-stu-id="bb5cd-111">In the **Name** box, type **HeaderHelper**, and then click **OK** to create the project.</span></span>  
  
5.  <span data-ttu-id="bb5cd-112">Dans l’Explorateur de solutions, avec le bouton droit sur le **Class1.cs** de fichiers dans le **HeaderHelper** de projet, cliquez sur **renommer**, type **HeaderHelper.cs**, puis appuyez sur **entrée**.</span><span class="sxs-lookup"><span data-stu-id="bb5cd-112">In Solution Explorer, right click the **Class1.cs** file in the **HeaderHelper** project, click **Rename**, type **HeaderHelper.cs**, and then press **Enter**.</span></span>  
  
### <a name="to-create-the-helper-class"></a><span data-ttu-id="bb5cd-113">Pour créer la classe d’assistance</span><span class="sxs-lookup"><span data-stu-id="bb5cd-113">To create the Helper class</span></span>  
  
1.  <span data-ttu-id="bb5cd-114">Dans l’Explorateur de solutions, développez le **HeaderHelper** de projet, puis double-cliquez sur le **HeaderHelper.cs** nœud pour ouvrir le fichier source HeaderHelper.</span><span class="sxs-lookup"><span data-stu-id="bb5cd-114">In Solution Explorer, expand the **HeaderHelper** project, and then double-click the **HeaderHelper.cs** node to open the HeaderHelper source file.</span></span>  
  
2.  <span data-ttu-id="bb5cd-115">Tapez le code suivant dans le fichier source, en remplaçant tout le code existant :</span><span class="sxs-lookup"><span data-stu-id="bb5cd-115">Type the following code into the source file, overwriting all the existing code:</span></span>  
  
    ```  
    using System;  
    using System.Xml;  
  
    namespace ContosoPriceAndAvailability  
    {  
        public class Helper  
        {  
            static public XmlDocument NormalizeHeader( XmlDocument curPip )  
            {  
                string strInput = curPip.OuterXml;  
                try  
                {  
                    XmlDocument xDoc = new XmlDocument();  
  
                    strInput = strInput.Replace("<!DOCTYPE Pip3A2PriceAndAvailabilityQuery SYSTEM \"3A2PriceAndAvailabilityQueryMessageGuideline_v1_3.dtd\"[]>",String.Empty);  
                    strInput = strInput.Replace("<Pip3A2PriceAndAvailabilityQuery>","<Pip3A2PriceAndAvailabilityQuery xmlns=\"http://schemas.microsoft.com/biztalk/btarn/2004/3A2PriceAndAvailabilityQueryMessageGuideline_v1_3.dtd\">");  
                    strInput = strInput.Replace("xml:",String.Empty);  
                    strInput = strInput.Replace("b:",String.Empty);  
                    strInput = strInput.Replace("lang:",String.Empty);  
                    strInput = strInput.Replace("ns1:",String.Empty);  
  
                    xDoc.LoadXml(strInput);  
  
                    return xDoc;  
                }  
                catch(Exception ex)  
                {  
                    System.Diagnostics.Debug.Write( ex.Message );  
                    throw ex;  
                }  
            }  
  
            static public string ReturnSCWithDocType( XmlDocument xmlDoc )  
            {  
                try  
                {  
                    string sResponse = xmlDoc.InnerXml;  
                    sResponse=sResponse.Replace("ns0:",String.Empty);  
                    xmlDoc.LoadXml(sResponse);  
                    xmlDoc.DocumentElement.RemoveAllAttributes();  
                    sResponse = xmlDoc.InnerXml;  
  
                    sResponse = sResponse.Insert(0,"<!DOCTYPE Pip3A2PriceAndAvailabilityResponse SYSTEM \"3A2PriceAndAvailabilityResponseMessageGuideline_v1_3.dtd\">");  
                    sResponse = sResponse.Replace("ns0:",String.Empty);  
                    sResponse = sResponse.Replace("b:",String.Empty);  
                    sResponse = sResponse.Replace("lang:",String.Empty);  
                    sResponse = sResponse.Replace("ns1:",String.Empty);  
  
                    return sResponse;  
                }  
                catch(Exception ex)  
                {  
                    throw ex;  
                }  
            }  
        }  
    }  
    ```  
  
3.  <span data-ttu-id="bb5cd-116">Dans le menu **Fichier** , cliquez sur **Enregistrer tout**.</span><span class="sxs-lookup"><span data-stu-id="bb5cd-116">On the **File** menu, click **Save All**.</span></span>  
  
### <a name="to-create-a-strong-named-assembly-for-the-headerhelper-project"></a><span data-ttu-id="bb5cd-117">Pour créer un assembly à nom fort pour le projet HeaderHelper</span><span class="sxs-lookup"><span data-stu-id="bb5cd-117">To create a strong named assembly for the HeaderHelper project</span></span>  
  
1.  <span data-ttu-id="bb5cd-118">Dans l’Explorateur de solutions, cliquez sur le **HeaderHelper** de projet, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="bb5cd-118">In Solution Explorer, right-click the **HeaderHelper** project, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="bb5cd-119">Dans la boîte de dialogue Pages de propriétés HeaderHelper, sélectionnez **signature** dans le volet gauche du volet Propriétés HeaderHelp.</span><span class="sxs-lookup"><span data-stu-id="bb5cd-119">In the HeaderHelper Property Pages dialog box, select **Signing** in the left pane of the HeaderHelp properties pane.</span></span>  
  
3.  <span data-ttu-id="bb5cd-120">Dans le volet droit, cliquez sur **signer l’Assembly**.</span><span class="sxs-lookup"><span data-stu-id="bb5cd-120">In the right pane, click **Sign the Assembly**.</span></span>  
  
4.  <span data-ttu-id="bb5cd-121">Cliquez sur le **choisir un fichier de clé de nom fort** zone de texte, puis sélectionnez  **\<Parcourir\>**  dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="bb5cd-121">Click the **Choose a strong name key file** text box, and then select **\<Browse\>** from the drop-down list.</span></span>  
  
5.  <span data-ttu-id="bb5cd-122">Dans la boîte de dialogue Sélectionner le fichier, accédez à l’emplacement de votre assembly de Contoso, double-cliquez sur **FabConPriceAvail.snk**.</span><span class="sxs-lookup"><span data-stu-id="bb5cd-122">In the Select File dialog box, move to the location of your Contoso assembly, and double-click **FabConPriceAvail.snk**.</span></span>  
  
6.  <span data-ttu-id="bb5cd-123">Dans le menu **Fichier** , cliquez sur **Enregistrer tout**.</span><span class="sxs-lookup"><span data-stu-id="bb5cd-123">On the **File** menu, click **Save All**.</span></span>  
  
7.  <span data-ttu-id="bb5cd-124">Dans l’Explorateur de solutions, développez le **HeaderHelper** de projet, développez le **propriétés** nœud, puis double-cliquez sur le **AssemblyInfo.cs** nœud ouvrir AssemblyInfo.cs fichier source.</span><span class="sxs-lookup"><span data-stu-id="bb5cd-124">In Solution Explorer, expand the **HeaderHelper** project, expand the **Properties** node, and then double-click the **AssemblyInfo.cs** node to open the AssemblyInfo.cs source file.</span></span>  
  
8.  <span data-ttu-id="bb5cd-125">Dans le fichier AssemblyInfo.cs source, tapez le code suivant sur la ligne après l’attribut AssemblyCulture :</span><span class="sxs-lookup"><span data-stu-id="bb5cd-125">In the AssemblyInfo.cs source file, type the following code on the line after the AssemblyCulture attribute:</span></span>  
  
    ```  
    [assembly: AssemblyKeyFile("../../../FabConPriceAvail.snk")]  
    ```  
  
9. <span data-ttu-id="bb5cd-126">Dans le menu **Fichier** , cliquez sur **Enregistrer tout**.</span><span class="sxs-lookup"><span data-stu-id="bb5cd-126">On the **File** menu, click **Save All**.</span></span>  
  
### <a name="to-build-and-deploy-the-headerhelper-project"></a><span data-ttu-id="bb5cd-127">Pour générer et déployer le projet HeaderHelper</span><span class="sxs-lookup"><span data-stu-id="bb5cd-127">To build and deploy the HeaderHelper project</span></span>  
  
1.  <span data-ttu-id="bb5cd-128">Dans l’Explorateur de solutions, cliquez sur le **HeaderHelper** de projet, puis cliquez sur **Build**.</span><span class="sxs-lookup"><span data-stu-id="bb5cd-128">In Solution Explorer, right-click the **HeaderHelper** project, and then click **Build**.</span></span>  
  
2.  <span data-ttu-id="bb5cd-129">Démarrez une **invite de commandes Visual Studio 2012**.</span><span class="sxs-lookup"><span data-stu-id="bb5cd-129">Start **Visual Studio 2012 Command Prompt**.</span></span>  
  
3.  <span data-ttu-id="bb5cd-130">À l’invite de commandes, accédez à l’emplacement de la **HeaderHelper** le répertoire de sortie de projet (le dossier \Bin\Debug).</span><span class="sxs-lookup"><span data-stu-id="bb5cd-130">At the command prompt, move to the location of the **HeaderHelper** project output directory (the \Bin\Debug folder).</span></span>  
  
4.  <span data-ttu-id="bb5cd-131">À l’invite de commandes, tapez **gacutil /if HeaderHelper.dll** et appuyez sur **entrée** pour installer le **HeaderHelper** assembly dans le **Global Assembly Cache** .</span><span class="sxs-lookup"><span data-stu-id="bb5cd-131">At the command prompt, type **gacutil /if HeaderHelper.dll** and press **Enter** to install the **HeaderHelper** assembly into the **Global Assembly Cache**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb5cd-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bb5cd-132">See Also</span></span>  
 [<span data-ttu-id="bb5cd-133">Étape 5 : Modification de l’orchestration du processus privé de Contoso</span><span class="sxs-lookup"><span data-stu-id="bb5cd-133">Step 5: Modifying the Contoso Private Process Orchestration</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-5-modifying-the-contoso-private-process-orchestration.md)