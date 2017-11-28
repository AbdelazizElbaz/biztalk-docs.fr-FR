---
title: "Exemples d’adaptateur HTTP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- HTTP adapters, examples
- examples, HTTP adapters
ms.assetid: 6796ea39-2947-45df-b228-1ecdb23a7ab8
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c4eb20ba2a9dc91f9b8bd17442f8bd3e7986fcfa
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="http-adapter-samples"></a><span data-ttu-id="d3207-102">Exemples d'adaptateur HTTP</span><span class="sxs-lookup"><span data-stu-id="d3207-102">HTTP Adapter Samples</span></span>
<span data-ttu-id="d3207-103">Cette section contient des exemples qui illustrent des fonctionnalités avancées lors de l'utilisation de l'adaptateur HTTP BizTalk.</span><span class="sxs-lookup"><span data-stu-id="d3207-103">This section contains samples that illustrate advanced functionality when using the BizTalk HTTP Adapter.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d3207-104">Avant d'exécuter cet exemple, effectuez les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="d3207-104">Before running this sample, you need to do the following steps:</span></span>  
>   
>  1.  <span data-ttu-id="d3207-105">Ouvrez IIS, ajoutez les restrictions ISAPI et CGI :</span><span class="sxs-lookup"><span data-stu-id="d3207-105">Open IIS, add ISAPI and CGI restrictions:</span></span>  
>   
>      <span data-ttu-id="d3207-106">Cliquez sur Nom de l'ordinateur dans le volet gauche, puis sur Restrictions ISAPI et CGI dans le volet droit, puis ajoutez le chemin ISAPI ou CGI :</span><span class="sxs-lookup"><span data-stu-id="d3207-106">Click Machine Name on left panel, then click "ISAPI and CGI restrictions" on the right panel, then Add the ISAPI or CGI path:</span></span>  
>   
>      <span data-ttu-id="d3207-107">Sur un ordinateur 64 bits, ajoutez : C:\Program Files (x86) \Microsoft BizTalk Server \<version > \HttpReceive64\BTSHTTPReceive.dll</span><span class="sxs-lookup"><span data-stu-id="d3207-107">On a 64 bit machine add:   C:\Program Files (x86)\Microsoft BizTalk Server \<version>\HttpReceive64\BTSHTTPReceive.dll</span></span>  
>   
>      <span data-ttu-id="d3207-108">Sur un ordinateur 32 bits, ajoutez : C:\Program Files (x86) \Microsoft BizTalk Server \<version > \HttpReceive\BTSHTTPReceive.dll</span><span class="sxs-lookup"><span data-stu-id="d3207-108">On a 32 bit machine add:   C:\Program Files (x86)\Microsoft BizTalk Server \<version>\HttpReceive\BTSHTTPReceive.dll</span></span>  
>   
>      <span data-ttu-id="d3207-109">Cochez le chemin de l'extension autorisé ou exécutez-le.</span><span class="sxs-lookup"><span data-stu-id="d3207-109">Check allowed extension path or execute.</span></span>  
> 2.  <span data-ttu-id="d3207-110">Cliquez sur HTTPRequestResponseSample dans le volet gauche, puis sur Mappage de gestionnaires dans le volet central, puis cliquez sur Ajouter un mappage de scripts avec les paramètres suivants :</span><span class="sxs-lookup"><span data-stu-id="d3207-110">Click "HTTPRequestResponseSample" on left panel, then click "Handler Mapping" on middle panel, then click "Add script mapping” with the following setting:</span></span>  
>   
>      <span data-ttu-id="d3207-111">Chemin des demandes : BTSHTTPReceive.dll</span><span class="sxs-lookup"><span data-stu-id="d3207-111">Request path:BTSHTTPReceive.dll</span></span>  
>   
>      <span data-ttu-id="d3207-112">Exécutable :</span><span class="sxs-lookup"><span data-stu-id="d3207-112">Executable:</span></span>  
>   
>      <span data-ttu-id="d3207-113">Sur un ordinateur 64 bits, ajoutez : C:\Program Files (x86) \Microsoft BizTalk Server \<version > \HttpReceive64\\</span><span class="sxs-lookup"><span data-stu-id="d3207-113">On 64 bit machine add:   C:\Program Files (x86)\Microsoft BizTalk Server \<version>\HttpReceive64\\</span></span>  
>   
>      <span data-ttu-id="d3207-114">Sur un ordinateur 32 bits, ajoutez : C:\Program Files (x86) \Microsoft BizTalk Server \<version > \HttpReceive\\</span><span class="sxs-lookup"><span data-stu-id="d3207-114">On 32 bit machine add:   C:\Program Files (x86)\Microsoft BizTalk Server \<version>\HttpReceive\\</span></span>  
>   
>      <span data-ttu-id="d3207-115">Restrictions des demandes :</span><span class="sxs-lookup"><span data-stu-id="d3207-115">Request restrictions:</span></span>  
>   
>      <span data-ttu-id="d3207-116">Verbes : POST</span><span class="sxs-lookup"><span data-stu-id="d3207-116">Verbs: POST</span></span>  
>   
>      <span data-ttu-id="d3207-117">Accès : Script</span><span class="sxs-lookup"><span data-stu-id="d3207-117">Access: Script</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d3207-118">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="d3207-118">In This Section</span></span>  
  
-   [<span data-ttu-id="d3207-119">HTTPSolicitResponse</span><span class="sxs-lookup"><span data-stu-id="d3207-119">HTTPSolicitResponse</span></span>](../core/httpsolicitresponse.md)  
  
-   [<span data-ttu-id="d3207-120">HTTPRequestResponse</span><span class="sxs-lookup"><span data-stu-id="d3207-120">HTTPRequestResponse</span></span>](../core/httprequestresponse.md)