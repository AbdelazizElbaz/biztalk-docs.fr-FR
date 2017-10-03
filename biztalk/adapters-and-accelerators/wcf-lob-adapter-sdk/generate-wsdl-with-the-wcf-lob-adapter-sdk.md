---
title: "Générer le WSDL avec le Kit de développement logiciel de l’adaptateur LOB WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f701d78d-b3ad-4f75-b814-e5b1f1319fb9
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f1075bbe59e15e3eeabde6c1d5c954460d1cb570
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="generate-wsdl-with-the-wcf-lob-adapter-sdk"></a><span data-ttu-id="5e72b-102">Générer le WSDL avec le Kit de développement logiciel de l’adaptateur LOB WCF</span><span class="sxs-lookup"><span data-stu-id="5e72b-102">Generate WSDL with the WCF LOB Adapter SDK</span></span>
<span data-ttu-id="5e72b-103">Pendant le développement d’un adaptateur, ou lorsque les métadonnées retournées par les modifications du système LOB, il est souvent utile d’afficher le Web Services Description Language (WSDL) qui est retourné à partir de l’adaptateur pour vérifier que les métadonnées pour vos opérations sont générées correctement.</span><span class="sxs-lookup"><span data-stu-id="5e72b-103">During development of an adapter, or when the metadata that is returned from the LOB system changes, it is often useful to view the Web Services Description Language (WSDL) that is returned from the adapter to verify that the metadata for your operations is generated correctly.</span></span> <span data-ttu-id="5e72b-104">Il existe plusieurs méthodes pour générer le WSDL.</span><span class="sxs-lookup"><span data-stu-id="5e72b-104">There are several methods to generate the WSDL.</span></span> <span data-ttu-id="5e72b-105">Cette rubrique fournit des informations sur l’utilisation de svcutil.exe et le contrôle de recherche de métadonnées Parcourir.</span><span class="sxs-lookup"><span data-stu-id="5e72b-105">This topic provides information about using svcutil.exe and the Metadata Search Browse control.</span></span>  

  
## <a name="use-svcutilexe"></a><span data-ttu-id="5e72b-106">Utiliser svcutil.exe</span><span class="sxs-lookup"><span data-stu-id="5e72b-106">Use svcutil.exe</span></span>  
 <span data-ttu-id="5e72b-107">SvcUtil.exe est un utilitaire de ligne de commande fourni avec le Kit de développement qui accepte une URL et des paramètres facultatifs et retourne le WSDL.</span><span class="sxs-lookup"><span data-stu-id="5e72b-107">Svcutil.exe is a command-line utility shipped with the Windows SDK that accepts a URL and optional switches, and returns WSDL.</span></span> <span data-ttu-id="5e72b-108">Voici un exemple d’utilisation de svcutil.exe pour retourner le WSDL de l’adaptateur d’écho :</span><span class="sxs-lookup"><span data-stu-id="5e72b-108">The following is an example of using svcutil.exe to return the WSDL of the Echo Adapter:</span></span>  
  
 ```
 Svcutil.exe “echov2://lobhostname/lobapplication?enableAuthentication=False” /target:metadata
 ```
  
 <span data-ttu-id="5e72b-109">Il enregistre les métadonnées en tant que Microsoft.Adapters.Samples.Echov2.wsdl.</span><span class="sxs-lookup"><span data-stu-id="5e72b-109">This saves the metadata as Microsoft.Adapters.Samples.Echov2.wsdl.</span></span> <span data-ttu-id="5e72b-110">Si votre adaptateur possède de nombreuses opérations, vous pouvez choisir de retourner uniquement les opérations souhaitées à l’aide de ' op = NomOpération ' en tant que partie de l’URI.</span><span class="sxs-lookup"><span data-stu-id="5e72b-110">If your adapter has many operations, you can choose to return only the desired operations by using ‘op=OperationName’ as part of the URI.</span></span> <span data-ttu-id="5e72b-111">Voici un exemple d’utilisation de ce pour retourner uniquement les informations de EchoStrings :</span><span class="sxs-lookup"><span data-stu-id="5e72b-111">The following is an example of using this to return only the EchoStrings information:</span></span>  
  
```  
SvcUtil.exe “echov2://lobhostname/lobapplication?enableAuthentication=False&op=Echo/EchoStrings” /target:metadata  
```  
  
## <a name="use-the-metadata-search-browse-control"></a><span data-ttu-id="5e72b-112">Utilisez le contrôle de navigation de recherche de métadonnées</span><span class="sxs-lookup"><span data-stu-id="5e72b-112">Use the Metadata Search Browse Control</span></span>  
 <span data-ttu-id="5e72b-113">Le contrôle de recherche de métadonnées Parcourir est un contrôle Windows qui est utilisé dans les Assistants inclus dans [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5e72b-113">The Metadata Search Browse control is a Windows control that is used in the wizards included in [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span></span> <span data-ttu-id="5e72b-114">Vous pouvez ajouter ce contrôle à un projet Windows Forms dans Visual Studio et l’utiliser pour sélectionner votre adaptateur, les opérations de votre choisies et puis générer le WSDL.</span><span class="sxs-lookup"><span data-stu-id="5e72b-114">You can add this control to any Windows Forms project in Visual Studio, and use it to select your adapter, the desired operations, and then generate the WSDL.</span></span>  
  
1.  <span data-ttu-id="5e72b-115">Ouvrir un [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="5e72b-115">Open a [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] command prompt.</span></span>  
  
2.  <span data-ttu-id="5e72b-116">Sur le **fichier** menu, sélectionnez **nouveau**, puis cliquez sur **projet**.</span><span class="sxs-lookup"><span data-stu-id="5e72b-116">On the **File** menu, select **New**, and then click **Project**.</span></span>  
  
3.  <span data-ttu-id="5e72b-117">Dans le **nouveau projet** boîte de dialogue, sélectionnez **Application Windows** de **modèles**.</span><span class="sxs-lookup"><span data-stu-id="5e72b-117">In the **New Project** dialog box, select **Windows Application** from **Templates**.</span></span> <span data-ttu-id="5e72b-118">Entrez un nom de projet, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="5e72b-118">Enter a project name, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="5e72b-119">Ouvrez le **boîte à outils**, développez **contrôles communs**, avec le bouton droit le **boîte à outils**, puis cliquez sur **choisir des éléments de**.</span><span class="sxs-lookup"><span data-stu-id="5e72b-119">Open the **Toolbox**, expand **Common Controls**, right-click the **Toolbox**, and then click **Choose Items**.</span></span>  
  
5.  <span data-ttu-id="5e72b-120">Dans le **choisir des éléments de boîte à outils** boîte de dialogue Rechercher **MetadataUserControl** sur la **composants .NET Framework** onglet, sélectionnez la case à cocher en regard de cet élément, puis cliquez sur  **OK**.</span><span class="sxs-lookup"><span data-stu-id="5e72b-120">In the **Choose Toolbox Items** dialog box, find **MetadataUserControl** on the **.NET Framework Components** tab, select the check box beside this item, and then click **OK**.</span></span>  
  
6.  <span data-ttu-id="5e72b-121">À partir de la boîte à outils, faites glisser le MetadataUserControl vers Form1.</span><span class="sxs-lookup"><span data-stu-id="5e72b-121">From the Toolbox, drag the MetadataUserControl to Form1.</span></span> <span data-ttu-id="5e72b-122">Vous devrez peut-être redimensionner le formulaire pour afficher l’ensemble du contrôle.</span><span class="sxs-lookup"><span data-stu-id="5e72b-122">You may need to resize the form to see the entire control.</span></span> <span data-ttu-id="5e72b-123">Vous devez être en mesure d’exécuter le projet maintenant et vérifiez que le contrôle fonctionne, ce qui vous permet de sélectionner un adaptateur et les opérations.</span><span class="sxs-lookup"><span data-stu-id="5e72b-123">You should be able to run the project now and verify that the control is functional, allowing you to select an adapter and operations.</span></span>  
  
7.  <span data-ttu-id="5e72b-124">Pour générer le WSDL à l’aide de ce contrôle, vous devez ajouter du code à votre formulaire pour appeler le **GetWsdl** méthode de ce contrôle.</span><span class="sxs-lookup"><span data-stu-id="5e72b-124">To generate WSDL by using this control, you must add code to your form to call the **GetWsdl** method of this control.</span></span> <span data-ttu-id="5e72b-125">L’exemple suivant montre comment appeler **GetWsdl** et enregistrer les données dans le fichier :</span><span class="sxs-lookup"><span data-stu-id="5e72b-125">The following example demonstrates how to call **GetWsdl** and save the data to file:</span></span>  
  
    ```csharp  
    private void button1_Click(object sender, EventArgs e)  
    {  
       ServiceDescription sd = mdUserControl.GetWsdl();  
       FileStream myFileStream = new FileStream(tbWsdlFileName.Text, FileMode.OpenOrCreate, FileAccess.Write);  
       StreamWriter myStreamWriter = new StreamWriter(myFileStream);  
       sd.Write(myStreamWriter);  
       myStreamWriter.Flush();  
       myStreamWriter.Close();  
       MessageBox.Show("WSDL file " + tbWsdlFileName.Text + " is created.");  
    }  
  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="5e72b-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5e72b-126">See Also</span></span>  
 [<span data-ttu-id="5e72b-127">Résoudre les problèmes d’adaptateur créé à l’aide de WCF LOB Adapter SDK</span><span class="sxs-lookup"><span data-stu-id="5e72b-127">Troubleshoot adapter created using the WCF LOB Adapter SDK</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/troubleshoot-adapter-created-using-the-wcf-lob-adapter-sdk.md)