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
ms.openlocfilehash: a1111322d59f8ff5c6ba6209aa48eb515a23c72f
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="http-adapter-samples"></a><span data-ttu-id="bec14-102">Exemples d'adaptateur HTTP</span><span class="sxs-lookup"><span data-stu-id="bec14-102">HTTP Adapter Samples</span></span>
<span data-ttu-id="bec14-103">Cette section contient des exemples qui illustrent des fonctionnalités avancées lors de l'utilisation de l'adaptateur HTTP BizTalk.</span><span class="sxs-lookup"><span data-stu-id="bec14-103">This section contains samples that illustrate advanced functionality when using the BizTalk HTTP Adapter.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bec14-104">Avant d'exécuter cet exemple, effectuez les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="bec14-104">Before running this sample, you need to do the following steps:</span></span>  
>   
>  1.  <span data-ttu-id="bec14-105">Ouvrez IIS, ajoutez les restrictions ISAPI et CGI :</span><span class="sxs-lookup"><span data-stu-id="bec14-105">Open IIS, add ISAPI and CGI restrictions:</span></span>  
>   
>      <span data-ttu-id="bec14-106">Cliquez sur Nom de l'ordinateur dans le volet gauche, puis sur Restrictions ISAPI et CGI dans le volet droit, puis ajoutez le chemin ISAPI ou CGI :</span><span class="sxs-lookup"><span data-stu-id="bec14-106">Click Machine Name on left panel, then click "ISAPI and CGI restrictions" on the right panel, then Add the ISAPI or CGI path:</span></span>  
>   
>      <span data-ttu-id="bec14-107">Sur un ordinateur 64 bits, ajoutez : C:\Program Files (x86) \Microsoft BizTalk Server \<version\>\HttpReceive64\BTSHTTPReceive.dll</span><span class="sxs-lookup"><span data-stu-id="bec14-107">On a 64 bit machine add:   C:\Program Files (x86)\Microsoft BizTalk Server \<version\>\HttpReceive64\BTSHTTPReceive.dll</span></span>  
>   
>      <span data-ttu-id="bec14-108">Sur un ordinateur 32 bits, ajoutez : C:\Program Files (x86) \Microsoft BizTalk Server \<version\>\HttpReceive\BTSHTTPReceive.dll</span><span class="sxs-lookup"><span data-stu-id="bec14-108">On a 32 bit machine add:   C:\Program Files (x86)\Microsoft BizTalk Server \<version\>\HttpReceive\BTSHTTPReceive.dll</span></span>  
>   
>      <span data-ttu-id="bec14-109">Cochez le chemin de l'extension autorisé ou exécutez-le.</span><span class="sxs-lookup"><span data-stu-id="bec14-109">Check allowed extension path or execute.</span></span>  
> 2.  <span data-ttu-id="bec14-110">Cliquez sur HTTPRequestResponseSample dans le volet gauche, puis sur Mappage de gestionnaires dans le volet central, puis cliquez sur Ajouter un mappage de scripts avec les paramètres suivants :</span><span class="sxs-lookup"><span data-stu-id="bec14-110">Click "HTTPRequestResponseSample" on left panel, then click "Handler Mapping" on middle panel, then click "Add script mapping” with the following setting:</span></span>  
>   
>      <span data-ttu-id="bec14-111">Chemin des demandes : BTSHTTPReceive.dll</span><span class="sxs-lookup"><span data-stu-id="bec14-111">Request path:BTSHTTPReceive.dll</span></span>  
>   
>      <span data-ttu-id="bec14-112">Exécutable :</span><span class="sxs-lookup"><span data-stu-id="bec14-112">Executable:</span></span>  
>   
>      <span data-ttu-id="bec14-113">Sur un ordinateur 64 bits, ajoutez : C:\Program Files (x86) \Microsoft BizTalk Server \<version\>\HttpReceive64\\</span><span class="sxs-lookup"><span data-stu-id="bec14-113">On 64 bit machine add:   C:\Program Files (x86)\Microsoft BizTalk Server \<version\>\HttpReceive64\\</span></span>  
>   
>      <span data-ttu-id="bec14-114">Sur un ordinateur 32 bits, ajoutez : C:\Program Files (x86) \Microsoft BizTalk Server \<version\>\HttpReceive\\</span><span class="sxs-lookup"><span data-stu-id="bec14-114">On 32 bit machine add:   C:\Program Files (x86)\Microsoft BizTalk Server \<version\>\HttpReceive\\</span></span>  
>   
>      <span data-ttu-id="bec14-115">Restrictions des demandes :</span><span class="sxs-lookup"><span data-stu-id="bec14-115">Request restrictions:</span></span>  
>   
>      <span data-ttu-id="bec14-116">Verbes : POST</span><span class="sxs-lookup"><span data-stu-id="bec14-116">Verbs: POST</span></span>  
>   
>      <span data-ttu-id="bec14-117">Accès : Script</span><span class="sxs-lookup"><span data-stu-id="bec14-117">Access: Script</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bec14-118">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="bec14-118">In This Section</span></span>  
  
-   [<span data-ttu-id="bec14-119">HTTPSolicitResponse</span><span class="sxs-lookup"><span data-stu-id="bec14-119">HTTPSolicitResponse</span></span>](../core/httpsolicitresponse.md)  
  
-   [<span data-ttu-id="bec14-120">HTTPRequestResponse</span><span class="sxs-lookup"><span data-stu-id="bec14-120">HTTPRequestResponse</span></span>](../core/httprequestresponse.md)