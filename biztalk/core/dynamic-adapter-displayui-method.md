---
title: "Méthode DisplayUI de l’adaptateur dynamique | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9183d2ee-4265-4fee-9d1d-7e2462d8ff37
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fd26bc5e5e344f53537e16135bf0a30b8b1443c8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="dynamic-adapter-displayui-method"></a><span data-ttu-id="73655-102">Méthode DisplayUI de l'adaptateur dynamique</span><span class="sxs-lookup"><span data-stu-id="73655-102">Dynamic Adapter DisplayUI Method</span></span>
<span data-ttu-id="73655-103">Cette méthode sur le **IDynamicAdapterConfig** interface affiche l’interface utilisateur personnalisée pour l’adaptateur personnalisé.</span><span class="sxs-lookup"><span data-stu-id="73655-103">This method on the **IDynamicAdapterConfig** interface displays the custom user interface for the custom adapter.</span></span> <span data-ttu-id="73655-104">Elle permet d'afficher, de sélectionner et d'importer les fichiers de prise en charge associés en fonction des services sélectionnés dans le projet BizTalk.</span><span class="sxs-lookup"><span data-stu-id="73655-104">This enables the user to view, select, and import the related supporting files based upon the selected services into their BizTalk project.</span></span>  
  
 <span data-ttu-id="73655-105">Dans l’adaptateur file, modifiez le code dans le **displayUI** méthode du fichier AdapterManagement.cs afin de créer une interface utilisateur personnalisée (interface utilisateur) pour sélectionner le type de schéma à accepter.</span><span class="sxs-lookup"><span data-stu-id="73655-105">In the file adapter, modify the code within the **displayUI** method of the AdapterManagement.cs file to create a custom user interface (UI) for selecting the type of schema to accept.</span></span> <span data-ttu-id="73655-106">Ceci fait, sélectionnez le fichier WSDL approprié.</span><span class="sxs-lookup"><span data-stu-id="73655-106">After a schema is selected, choose the appropriate WSDL file.</span></span>  
  
 <span data-ttu-id="73655-107">Le code suivant est issu le **displayUI** méthode du fichier AdapterManagement.cs.</span><span class="sxs-lookup"><span data-stu-id="73655-107">The following code is from the **displayUI** method of the AdapterManagement.cs file.</span></span>  
  
```  
/// <summary>  
        /// Acquire wsdl(s) from which to build the user interface  
        /// </summary>  
        /// <param name="endPointConfiguration"></param>  
        /// <param name="owner"></param>  
        /// <param name="WSDLList">Array of custom UI's WSDL (returned)</param>  
        /// <returns></returns>  
        public Result DisplayUI(IPropertyBag endPointConfiguration,   
            IWin32Window owner,  
            out string [] WSDLList)   
      {  
            WSDLList = new string[1];  
            WSDLList[0] = GetResource("AdapterManagement.service1.wsdl");  
            return Result.Continue;  
        }  
```