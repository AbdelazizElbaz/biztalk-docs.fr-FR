---
title: "Étape 2 : Classer l’adaptateur et les propriétés de connexion | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 45b3dc64-2078-4008-878b-501f727f4a11
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6e9d49323695b1070a8065cf7a5e548e61fc5db9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-2-categorize-the-adapter-and-connection-properties"></a><span data-ttu-id="0bbc8-102">Étape 2 : Classer l’adaptateur et les propriétés de connexion</span><span class="sxs-lookup"><span data-stu-id="0bbc8-102">Step 2: Categorize the Adapter and Connection Properties</span></span>
<span data-ttu-id="0bbc8-103">![Étape 2 sur 9](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-2of9.gif "Step_2of9")</span><span class="sxs-lookup"><span data-stu-id="0bbc8-103">![Step 2 of 9](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-2of9.gif "Step_2of9")</span></span>  
  
 <span data-ttu-id="0bbc8-104">**Durée :** 30 minutes</span><span class="sxs-lookup"><span data-stu-id="0bbc8-104">**Time to complete:** 30 minutes</span></span>  
  
 <span data-ttu-id="0bbc8-105">Dans cette étape, vous mettez à jour le **EchoAdapterBindingElement** et **EchoAdapterBindingElementExtensionElement** classes pour assigner une catégorie de propriétés de votre adaptateur et de la connexion.</span><span class="sxs-lookup"><span data-stu-id="0bbc8-105">In this step, you update the **EchoAdapterBindingElement** and **EchoAdapterBindingElementExtensionElement** classes to assign a category to your adapter and connection properties.</span></span> <span data-ttu-id="0bbc8-106">En procédant ainsi, les propriétés sont regroupées logiquement par catégorie dans le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] et [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] outils.</span><span class="sxs-lookup"><span data-stu-id="0bbc8-106">By doing so, properties are logically grouped by category in the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] and [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] tools.</span></span> <span data-ttu-id="0bbc8-107">Par exemple, si vous souhaitez que le **Application**, **EnableAuthentication**, et **nom d’hôte** propriétés apparaissent sous la **connexion** catégorie, comme illustré ci-dessous, vous devez affecter la catégorie de connexion pour chacune des propriétés de l’Application, EnableAuthentication et nom d’hôte.</span><span class="sxs-lookup"><span data-stu-id="0bbc8-107">For example, if you want the **Application**, **EnableAuthentication**, and **Hostname** properties to appear under the **Connection** category as shown below, you need to assign the Connection category to each of the Application, EnableAuthentication, and Hostname properties.</span></span>  
  
 ![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/c7c0c013-6651-4c32-9f8b-b546a68a0267.gif "c7c0c013-6651-4c32-9f8b-b546a68a0267")  
  
 <span data-ttu-id="0bbc8-108">De même, si vous souhaitez que le **InboundFileFilter** et **InboundFleSystemWatcherFolder** propriétés apparaissent sous la **entrant** catégorie, comme illustré ci-dessous, vous devez affecter la catégorie entrante à chacun.</span><span class="sxs-lookup"><span data-stu-id="0bbc8-108">Similarly, if you want the **InboundFileFilter** and **InboundFleSystemWatcherFolder** properties to appear under the **Inbound** category as shown below, you need to assign the Inbound category to each.</span></span> <span data-ttu-id="0bbc8-109">Si vous souhaitez **nombre** et **EnableConnectionPooling** sous le **divers** catégorie, vous devez affecter la catégorie divers à chacun.</span><span class="sxs-lookup"><span data-stu-id="0bbc8-109">If you want **Count** and **EnableConnectionPooling** to appear under the **Misc** category, you need to assign the Misc category to each.</span></span>  
  
 ![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/2acb7677-8b50-4e45-96a3-42d0e2011f19.gif "2acb7677-8b50-4e45-96a3-42d0e2011f19")  
  
 <span data-ttu-id="0bbc8-110">Gardez à l’esprit que vous pouvez affecter une propriété avec n’importe quel nom de catégorie que vous choisissez.</span><span class="sxs-lookup"><span data-stu-id="0bbc8-110">Keep in mind that you can assign a property with any category name you choose.</span></span> <span data-ttu-id="0bbc8-111">Dans cet exemple, étant donné que la propriété EnableConnnectionPooling n’appartient pas à toutes les autres catégories, nous considérer comme divers (divers).</span><span class="sxs-lookup"><span data-stu-id="0bbc8-111">In this example, since the EnableConnnectionPooling property does not belong to any other categories, we categorize it as Misc (Miscellaneous).</span></span> <span data-ttu-id="0bbc8-112">À la propriété InboundFileFilter, car il est utilisé lors du traitement entrant dans l’exemple, il est plus approprié d’affecter entrant à la propriété, plutôt que de divers.</span><span class="sxs-lookup"><span data-stu-id="0bbc8-112">As to the InboundFileFilter property, since it is used during the inbound handling within the example, it is more appropriate to assign Inbound to the property, rather than Miscellaneous.</span></span> <span data-ttu-id="0bbc8-113">Voici la catégorisation complète de la propriété personnalisée pour l’adaptateur de l’écho.</span><span class="sxs-lookup"><span data-stu-id="0bbc8-113">Here is the complete custom property categorization for the echo adapter.</span></span>  
  
|<span data-ttu-id="0bbc8-114">**Propriété**</span><span class="sxs-lookup"><span data-stu-id="0bbc8-114">**Property**</span></span>|<span data-ttu-id="0bbc8-115">**Catégorie**</span><span class="sxs-lookup"><span data-stu-id="0bbc8-115">**Category**</span></span>|  
|------------------|------------------|  
|<span data-ttu-id="0bbc8-116">InboundFileFilter</span><span class="sxs-lookup"><span data-stu-id="0bbc8-116">InboundFileFilter</span></span>|<span data-ttu-id="0bbc8-117">Trafic entrant</span><span class="sxs-lookup"><span data-stu-id="0bbc8-117">Inbound</span></span>|  
|<span data-ttu-id="0bbc8-118">InboundFileSystemWatcherFolder</span><span class="sxs-lookup"><span data-stu-id="0bbc8-118">InboundFileSystemWatcherFolder</span></span>|<span data-ttu-id="0bbc8-119">Trafic entrant</span><span class="sxs-lookup"><span data-stu-id="0bbc8-119">Inbound</span></span>|  
|<span data-ttu-id="0bbc8-120">Compter</span><span class="sxs-lookup"><span data-stu-id="0bbc8-120">Count</span></span>|<span data-ttu-id="0bbc8-121">Divers</span><span class="sxs-lookup"><span data-stu-id="0bbc8-121">Misc</span></span>|  
|<span data-ttu-id="0bbc8-122">EnableConnectionPooling</span><span class="sxs-lookup"><span data-stu-id="0bbc8-122">EnableConnectionPooling</span></span>|<span data-ttu-id="0bbc8-123">Divers</span><span class="sxs-lookup"><span data-stu-id="0bbc8-123">Misc</span></span>|  
|<span data-ttu-id="0bbc8-124">Application</span><span class="sxs-lookup"><span data-stu-id="0bbc8-124">Application</span></span>|<span data-ttu-id="0bbc8-125">Connexion</span><span class="sxs-lookup"><span data-stu-id="0bbc8-125">Connection</span></span>|  
|<span data-ttu-id="0bbc8-126">EnableAuthentication</span><span class="sxs-lookup"><span data-stu-id="0bbc8-126">EnableAuthentication</span></span>|<span data-ttu-id="0bbc8-127">Connexion</span><span class="sxs-lookup"><span data-stu-id="0bbc8-127">Connection</span></span>|  
|<span data-ttu-id="0bbc8-128">HostName</span><span class="sxs-lookup"><span data-stu-id="0bbc8-128">Hostname</span></span>|<span data-ttu-id="0bbc8-129">Connexion</span><span class="sxs-lookup"><span data-stu-id="0bbc8-129">Connection</span></span>|  
|<span data-ttu-id="0bbc8-130">EchoInUpperCase</span><span class="sxs-lookup"><span data-stu-id="0bbc8-130">EchoInUpperCase</span></span>|<span data-ttu-id="0bbc8-131">Format</span><span class="sxs-lookup"><span data-stu-id="0bbc8-131">Format</span></span>|  
  
 <span data-ttu-id="0bbc8-132">En plus de ces modifications, vous modifiez également la méthode Dispose du **EchoAdapterHandlerBase**.</span><span class="sxs-lookup"><span data-stu-id="0bbc8-132">In addition to those changes, you also modify the Dispose method of **EchoAdapterHandlerBase**.</span></span>  
  
 <span data-ttu-id="0bbc8-133">Pour les propriétés de l’adaptateur exposées par l’adaptateur echo, consultez la section Propriétés de l’adaptateur de le [didacticiel 1 : développer l’adaptateur Echo](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="0bbc8-133">For the adapter properties exposed by the echo adapter, see the adapter properties section of the [Tutorial 1: Develop the Echo Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="0bbc8-134">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="0bbc8-134">Prerequisites</span></span>  
 <span data-ttu-id="0bbc8-135">Avant de commencer cette étape, vous devez effectuer [étape 1 : utiliser l’Assistant de développement d’adaptateur LOB WCF pour créer le projet d’adaptateur Echo](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-1-use-the-wcf-lob-adapter-development-wizard-to-create-the-echo-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="0bbc8-135">Before you begin this step, you must complete [Step 1: Use the WCF LOB Adapter Development Wizard to Create the Echo Adapter Project](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-1-use-the-wcf-lob-adapter-development-wizard-to-create-the-echo-adapter.md).</span></span> <span data-ttu-id="0bbc8-136">Vous devez également être familiarisé avec les `System.ServiceModel.Configuration.BindingElementExtensionElement` et `System.ServiceModel.Configuration.StandardBindingElement` classes.</span><span class="sxs-lookup"><span data-stu-id="0bbc8-136">You should also be familiar with the `System.ServiceModel.Configuration.BindingElementExtensionElement` and `System.ServiceModel.Configuration.StandardBindingElement` classes.</span></span>  
  
## <a name="update-the-echoadapterhandlerbase-dispose-method"></a><span data-ttu-id="0bbc8-137">Mise à jour de la méthode Dispose de EchoAdapterHandlerBase</span><span class="sxs-lookup"><span data-stu-id="0bbc8-137">Update the EchoAdapterHandlerBase Dispose method</span></span>  
  
1.  <span data-ttu-id="0bbc8-138">Dans **l’Explorateur de solutions**, double-cliquez sur le **EchoAdapterHandlerBase.cs** fichier.</span><span class="sxs-lookup"><span data-stu-id="0bbc8-138">In **Solution Explorer**, double-click the **EchoAdapterHandlerBase.cs** file.</span></span>  
  
2.  <span data-ttu-id="0bbc8-139">Supprimez l’instruction suivante à partir de la **Dispose** méthode :</span><span class="sxs-lookup"><span data-stu-id="0bbc8-139">Remove the following statement from the **Dispose** method:</span></span>  
  
    ```csharp  
    throw new NotImplementedException("The method or operation is not implemented.");  
    ```  
  
     <span data-ttu-id="0bbc8-140">La méthode modifiée doit ressembler à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="0bbc8-140">The revised method should look similar to the following:</span></span>  
  
    ```csharp  
    protected virtual void Dispose(bool disposing)  
    {  
       //  
       //TODO: Implement Dispose. Override this method in respective Handler classes  
       //  
    }  
    ```  
  
## <a name="update-the-adapter-properties-class"></a><span data-ttu-id="0bbc8-141">Mise à jour de la classe d’adaptateur de propriétés</span><span class="sxs-lookup"><span data-stu-id="0bbc8-141">Update the Adapter properties class</span></span>  
  
1.  <span data-ttu-id="0bbc8-142">Dans **l’Explorateur de solutions**, double-cliquez sur le **EchoAdapterBindingElement.cs** fichier.</span><span class="sxs-lookup"><span data-stu-id="0bbc8-142">In **Solution Explorer**, double-click the **EchoAdapterBindingElement.cs** file.</span></span>  
  
2.  <span data-ttu-id="0bbc8-143">Dans l’éditeur Visual Studio, développez le **des propriétés personnalisées générées** région.</span><span class="sxs-lookup"><span data-stu-id="0bbc8-143">In the Visual Studio editor, expand the **Custom Generated Properties** region.</span></span>  
  
3.  <span data-ttu-id="0bbc8-144">Pour affecter le **divers** catégorie à la **nombre** propriété, ajoutez l’instruction suivante au début de la **nombre** implémentation.</span><span class="sxs-lookup"><span data-stu-id="0bbc8-144">To assign the **Misc** category to the **Count** property, add the following single statement to the beginning of the **Count** implementation.</span></span>  
  
    ```csharp  
    [System.ComponentModel.Category("")]  
    ```  
  
     <span data-ttu-id="0bbc8-145">Le **nombre** implémentation doit correspondre désormais les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="0bbc8-145">The **Count** implementation should now match the following:</span></span>  
  
    ```csharp  
    [System.ComponentModel.Category("")]  
    [System.Configuration.ConfigurationProperty("count", DefaultValue = 5)]  
    public int Count  
    {  
        get  
        {  
            return ((int)(base["Count"]));  
        }  
        set  
        {  
            base["Count"] = value;  
        }  
    }  
    ```  
  
4.  <span data-ttu-id="0bbc8-146">Pour affecter le **divers** catégorie à la **EnableConnectionPooling** propriété, ajoutez l’instruction suivante au début de la **EnableConnectionPooling** mise en œuvre.</span><span class="sxs-lookup"><span data-stu-id="0bbc8-146">To assign the **Misc** category to the **EnableConnectionPooling** property, add the following single statement to the beginning of the **EnableConnectionPooling** implementation.</span></span>  
  
    ```csharp  
    [System.ComponentModel.Category("")]  
    ```  
  
5.  <span data-ttu-id="0bbc8-147">Pour affecter le **entrant** catégorie à la **InboundFileFilter** propriété, ajoutez l’instruction suivante au début de la **InboundFileFilter** mise en œuvre.</span><span class="sxs-lookup"><span data-stu-id="0bbc8-147">To assign the **Inbound** category to the **InboundFileFilter** property, add the following single statement to the beginning of the **InboundFileFilter** implementation.</span></span>  
  
    ```csharp  
    [System.ComponentModel.Category("Inbound")]  
    ```  
  
6.  <span data-ttu-id="0bbc8-148">Pour affecter le **entrant** categoryto **inboundFleSystemWatcherFolder** propriété, ajoutez l’instruction suivante au début de la **inboundFleSystemWatcherFolder**mise en œuvre.</span><span class="sxs-lookup"><span data-stu-id="0bbc8-148">To assign the **Inbound** categoryto **inboundFleSystemWatcherFolder** property, add the following single statement to the beginning of the **inboundFleSystemWatcherFolder** implementation.</span></span>  
  
    ```csharp  
    [System.ComponentModel.Category("Inbound")]  
    ```  
  
7.  <span data-ttu-id="0bbc8-149">Vérification pour vous assurer que le code dans le **des propriétés personnalisées générées** région correspond à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="0bbc8-149">Check to ensure that the code in the **Custom Generated Properties** region matches the following:</span></span>  
  
    ```csharp  
    [System.ComponentModel.Category("")]  
    [System.Configuration.ConfigurationProperty("count", DefaultValue = 5)]  
    public int Count  
    {  
        get  
        {  
            return ((int)(base["Count"]));  
        }  
        set  
        {  
            base["Count"] = value;  
        }  
    }  
  
    [System.ComponentModel.Category("")]  
    [System.Configuration.ConfigurationProperty("enableConnectionPooling", DefaultValue = true)]  
    public bool EnableConnectionPooling  
    {  
        get  
        {  
            return ((bool)(base["EnableConnectionPooling"]));  
        }  
        set  
        {  
            base["EnableConnectionPooling"] = value;  
        }  
    }  
  
    [System.ComponentModel.Category("Inbound")]  
    [System.Configuration.ConfigurationProperty("inboundFileFilter", DefaultValue = "*.txt")]  
    public string InboundFileFilter  
    {  
        get  
        {  
            return ((string)(base["InboundFileFilter"]));  
        }  
        set  
        {  
            base["InboundFileFilter"] = value;  
        }  
    }  
  
    [System.ComponentModel.Category("Inbound")]  
    [System.Configuration.ConfigurationProperty("inboundFileSystemWatcherFolder", DefaultValue = "{InboundFileSystemWatcherFolder}")]  
    public string InboundFileSystemWatcherFolder  
    {  
        get  
        {  
            return ((string)(base["InboundFileSystemWatcherFolder"]));  
        }  
        set  
        {  
            base["InboundFileSystemWatcherFolder"] = value;  
        }  
    }  
  
    #endregion Custom Generated Properties  
    ```  
  
## <a name="update-the-connection-properties"></a><span data-ttu-id="0bbc8-150">Mettre à jour les propriétés de connexion</span><span class="sxs-lookup"><span data-stu-id="0bbc8-150">Update the Connection Properties</span></span>  
  
1.  <span data-ttu-id="0bbc8-151">Dans **l’Explorateur de solutions**, double-cliquez sur le **EchoAdapterConnectionUri.cs** fichier.</span><span class="sxs-lookup"><span data-stu-id="0bbc8-151">In **Solution Explorer**, double-click the **EchoAdapterConnectionUri.cs** file.</span></span>  
  
2.  <span data-ttu-id="0bbc8-152">Dans l’éditeur Visual Studio, développez le **des propriétés personnalisées générées** région.</span><span class="sxs-lookup"><span data-stu-id="0bbc8-152">In the Visual Studio editor, expand the **Custom Generated Properties** region.</span></span>  
  
3.  <span data-ttu-id="0bbc8-153">Pour affecter le **Format** catégorie à la **EchoInUpperCase** propriété, ajoutez l’instruction suivante au début de la **EchoInUpperCase** mise en œuvre.</span><span class="sxs-lookup"><span data-stu-id="0bbc8-153">To assign the **Format** category to the **EchoInUpperCase** property, add the following single statement to the beginning of the **EchoInUpperCase** implementation.</span></span>  
  
    ```csharp  
    [System.ComponentModel.Category("Format")]  
    ```  
  
4.  <span data-ttu-id="0bbc8-154">Pour affecter le **connexion** catégorie à la **nom d’hôte** propriété, ajoutez l’instruction suivante au début de la **nom d’hôte** implémentation.</span><span class="sxs-lookup"><span data-stu-id="0bbc8-154">To assign the **Connection** category to the **Hostname** property, add the following single statement to the beginning of the **Hostname** implementation.</span></span>  
  
    ```csharp  
    [System.ComponentModel.Category("Connection")]  
    ```  
  
5.  <span data-ttu-id="0bbc8-155">Pour affecter le **connexion** catégorie à la **Application** propriété, ajoutez l’instruction suivante au début de la **Application** implémentation.</span><span class="sxs-lookup"><span data-stu-id="0bbc8-155">To assign the **Connection** category to the **Application** property, add the following single statement to the beginning of the **Application** implementation.</span></span>  
  
    ```csharp  
    [System.ComponentModel.Category("Connection")]  
    ```  
  
6.  <span data-ttu-id="0bbc8-156">Pour affecter le **connexion** categoryto **EnableAuthentication** propriété, ajoutez l’instruction suivante au début de la **EnableAuthentication** mise en œuvre.</span><span class="sxs-lookup"><span data-stu-id="0bbc8-156">To assign the **Connection** categoryto **EnableAuthentication** property, add the following single statement to the beginning of the **EnableAuthentication** implementation.</span></span>  
  
    ```csharp  
    [System.ComponentModel.Category("Connection")]  
    ```  
  
7.  <span data-ttu-id="0bbc8-157">Vérification pour vous assurer que le code dans le **des propriétés personnalisées générées** région correspond à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="0bbc8-157">Check to ensure that the code in the **Custom Generated Properties** region matches the following:</span></span>  
  
    ```csharp  
    #region Custom Generated Properties  
            [System.ComponentModel.Category("Format")]  
            public bool EchoInUpperCase  
            {  
                get  
                {  
                    return this.echoInUpperCase;  
                }  
                set  
                {  
                    this.echoInUpperCase = value;  
                }  
            }  
  
            [System.ComponentModel.Category("Connection")]  
            public string Hostname  
            {  
                get  
                {  
                    return this.hostname;  
                }  
                set  
                {  
                    this.hostname = value;  
                }  
            }  
  
            [System.ComponentModel.Category("Connection")]  
            public string Application  
            {  
                get  
                {  
                    return this.application;  
                }  
                set  
                {  
                    this.application = value;  
                }  
            }  
  
            [System.ComponentModel.Category("Connection")]  
            public bool EnableAuthentication  
            {  
                get  
                {  
                    return this.enableAuthentication;  
                }  
                set  
                {  
                    this.enableAuthentication = value;  
                }  
            }  
            #endregion Custom Generated Properties  
    ```  
  
8.  <span data-ttu-id="0bbc8-158">Dans Visual Studio, à partir de la **fichier** menu, cliquez sur **Enregistrer tout**.</span><span class="sxs-lookup"><span data-stu-id="0bbc8-158">In Visual Studio, from the **File** menu, click **Save All**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0bbc8-159">Vous avez enregistré votre travail.</span><span class="sxs-lookup"><span data-stu-id="0bbc8-159">You saved your work.</span></span> <span data-ttu-id="0bbc8-160">Vous pouvez en toute sécurité fermer Visual Studio pour l’instant ou accédez à l’étape suivante, [étape 3 : implémenter la connexion de l’adaptateur Echo](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-3-implement-the-connection-for-the-echo-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="0bbc8-160">You can safely close Visual Studio at this time or go to the next step, [Step 3: Implement the Connection for the Echo Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-3-implement-the-connection-for-the-echo-adapter.md).</span></span>  
  
## <a name="what-did-i-just-do"></a><span data-ttu-id="0bbc8-161">Quoi simplement ?</span><span class="sxs-lookup"><span data-stu-id="0bbc8-161">What Did I Just Do?</span></span>  
 <span data-ttu-id="0bbc8-162">Vous mis à jour les classes pour attribuer une catégorie à chaque propriété de l’adaptateur et la connexion exposée par l’adaptateur de l’écho.</span><span class="sxs-lookup"><span data-stu-id="0bbc8-162">You just updated classes to assign a category to each adapter and connection property exposed by the echo adapter.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="0bbc8-163">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="0bbc8-163">Next Steps</span></span>  
 <span data-ttu-id="0bbc8-164">Vous implémentez la connexion, la navigation des métadonnées, recherche et résolution des fonctionnalités et l’échange de messages sortants.</span><span class="sxs-lookup"><span data-stu-id="0bbc8-164">You implement connection, metadata browsing, searching, and resolving capabilities, and the outbound message exchange.</span></span> <span data-ttu-id="0bbc8-165">Enfin, vous générez et déployez l’adaptateur de l’écho.</span><span class="sxs-lookup"><span data-stu-id="0bbc8-165">Lastly, you build and deploy the echo adapter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bbc8-166">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0bbc8-166">See Also</span></span>  
 <span data-ttu-id="0bbc8-167">[Étape 3 : Implémenter la connexion de l’adaptateur d’écho](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-3-implement-the-connection-for-the-echo-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="0bbc8-167">[Step 3: Implement the Connection for the Echo Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-3-implement-the-connection-for-the-echo-adapter.md) </span></span>  
 [<span data-ttu-id="0bbc8-168">Didacticiel 1 : Développer l’adaptateur d’écho</span><span class="sxs-lookup"><span data-stu-id="0bbc8-168">Tutorial 1: Develop the Echo Adapter</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md)