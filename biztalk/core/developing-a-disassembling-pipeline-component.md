---
title: "Composant de Pipeline du développement d’un désassemblage | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDisassemblerComponent interface, disassembling
- pipeline components [custom], IDisassemblerComponent
- pipeline components [custom], IBaseComponent
- IBaseComponent interface, disassembling
- pipeline components [custom], disassembling
ms.assetid: 77c0aa7d-4d1b-4a8f-bef8-d38e7e4045c6
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fc4e831561f9940ad7e8ee91479a2fada1fcd910
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="developing-a-disassembling-pipeline-component"></a><span data-ttu-id="a31fa-102">Développement d’un composant de Pipeline de désassemblage</span><span class="sxs-lookup"><span data-stu-id="a31fa-102">Developing a Disassembling Pipeline Component</span></span>
<span data-ttu-id="a31fa-103">Un composant de pipeline de désassemblage reçoit un message en entrée et produit zéro ou plusieurs messages en sortie.</span><span class="sxs-lookup"><span data-stu-id="a31fa-103">A disassembling pipeline component receives one message on input and produces zero or more messages on output.</span></span> <span data-ttu-id="a31fa-104">Les composants de désassemblage sont utilisés pour fractionner des échanges de messages en documents individuels.</span><span class="sxs-lookup"><span data-stu-id="a31fa-104">Disassembling components are used to split interchanges of messages into individual documents.</span></span> <span data-ttu-id="a31fa-105">Les composants du désassembleur doivent implémenter les interfaces suivantes :</span><span class="sxs-lookup"><span data-stu-id="a31fa-105">Disassembler components must implement the following interfaces:</span></span>  
  
-   `IBaseComponent`
  
-   `IDisassemblerComponent`
  
-   `IComponentUI`
  
-   <span data-ttu-id="a31fa-106">**IPersistPropertyBag.**</span><span class="sxs-lookup"><span data-stu-id="a31fa-106">**IPersistPropertyBag .**</span></span> <span data-ttu-id="a31fa-107">Pour cette interface, consultez la documentation .NET Framework SDK.</span><span class="sxs-lookup"><span data-stu-id="a31fa-107">Refer to the .NET Framework SDK documentation for this interface.</span></span>  
  
 <span data-ttu-id="a31fa-108">Vous pouvez créer votre propre désassemblage composant en étendant le **FFDasmComp** ou **XMLDasmComp** classe.</span><span class="sxs-lookup"><span data-stu-id="a31fa-108">You can create your own disassembling component by extending the **FFDasmComp** or **XMLDasmComp** class.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="a31fa-109">Si votre désassembleur personnalisé définit la propriété de contexte MessageDestination sur SuspendQueue, le flux renvoyé par le désassembleur doit prendre en charge Seek(0) pour que la suspension opère.</span><span class="sxs-lookup"><span data-stu-id="a31fa-109">If your custom disassembler will be setting the MessageDestination context property to SuspendQueue, the stream returned by the disassembler must to support Seek(0) for the suspension to work.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a31fa-110">Les composants de pipeline personnalisés doivent copier les parties supplémentaires du message d'entrée vers le ou les messages de sortie.</span><span class="sxs-lookup"><span data-stu-id="a31fa-110">Custom pipeline components should copy any additional parts from the input message to the output message(s).</span></span> <span data-ttu-id="a31fa-111">Ceci les empêche d'effectuer un autre traitement dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="a31fa-111">This preserves them for further processing in the pipeline.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a31fa-112">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="a31fa-112">In This Section</span></span>  
  
-   [<span data-ttu-id="a31fa-113">La gestion des flux de données entrantes dans les composants de Pipeline</span><span class="sxs-lookup"><span data-stu-id="a31fa-113">Handling Incoming Data Streams in Pipeline Components</span></span>](../core/handling-incoming-data-streams-in-pipeline-components.md)  
  
-   [<span data-ttu-id="a31fa-114">Gestion du codage dans un composant de Pipeline désassembleur</span><span class="sxs-lookup"><span data-stu-id="a31fa-114">Handling Encoding in a Disassembler Pipeline Component</span></span>](../core/handling-encoding-in-a-disassembler-pipeline-component.md)  
  
-   [<span data-ttu-id="a31fa-115">Étendre le composant de Pipeline de désassembleur de fichier plat</span><span class="sxs-lookup"><span data-stu-id="a31fa-115">Extending the Flat File Disassembler Pipeline Component</span></span>](../core/extending-the-flat-file-disassembler-pipeline-component.md)