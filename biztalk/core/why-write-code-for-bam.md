---
title: "Pourquoi écrire du code pour l'analyse BAM ? | Microsoft Docs"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4434f50a-e0a9-45e0-8c68-a059011e1296
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 10b8ccb29d95daf8ccdf80d67faef3e50495af04
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="why-write-code-for-bam"></a><span data-ttu-id="b4eec-103">Pourquoi écrire du code pour l'analyse BAM ?</span><span class="sxs-lookup"><span data-stu-id="b4eec-103">Why Write Code For BAM?</span></span>
<span data-ttu-id="b4eec-104">Dans la plupart des cas, vous pouvez utiliser les outils BAM suivants sans qu'il soit nécessaire d'écrire votre propre code pour réaliser les fonctions de suivi :</span><span class="sxs-lookup"><span data-stu-id="b4eec-104">In most circumstances you can use the BAM tools without writing your own code to perform your tracking functions.</span></span> <span data-ttu-id="b4eec-105">complément BAM pour Excel, utilitaire de gestion de l'analyse BAM et l'Éditeur de modèle de suivi (TPE).</span><span class="sxs-lookup"><span data-stu-id="b4eec-105">These tools are the BAM Add-in for Excel, the BAM Management utility, and the Tracking Profile Editor (TPE).</span></span> <span data-ttu-id="b4eec-106">L'analyse BAM de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] fournit les intercepteurs pour les orchestrations BizTalk et les composants de messagerie (pipelines et ports).</span><span class="sxs-lookup"><span data-stu-id="b4eec-106">BAM in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] provides interceptors for BizTalk orchestrations and messaging components (pipelines and ports).</span></span> <span data-ttu-id="b4eec-107">Un intercepteur est un logiciel qui instrumente une application de sorte qu'elle puisse collecter les données de façon générique en fonction d'un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="b4eec-107">An interceptor is software that instruments an application so that it can collect data in a generic way based on a configuration file.</span></span> <span data-ttu-id="b4eec-108">Pour que votre application utilise ces intercepteurs, vous pouvez vous servir de l'Éditeur de modèle de suivi.</span><span class="sxs-lookup"><span data-stu-id="b4eec-108">You can instrument your application to use these interceptors by using the Tracking Profile Editor.</span></span> <span data-ttu-id="b4eec-109">Pour plus d’informations sur l’éditeur de modèle de suivi, consultez [éditeur](../core/tracking-profile-editor.md).</span><span class="sxs-lookup"><span data-stu-id="b4eec-109">For more information about the Tracking Profile Editor, see [Tracking Profile Editor](../core/tracking-profile-editor.md).</span></span>  
  
 <span data-ttu-id="b4eec-110">Il existe toutefois deux principales situations pour lesquelles vous trouverez plus pratique d'instrumenter votre application à l'aide des API de l'analyse BAM :</span><span class="sxs-lookup"><span data-stu-id="b4eec-110">There are two primary scenarios, however, in which you will find it advantageous to instrument your application using the BAM APIs:</span></span>  
  
-   <span data-ttu-id="b4eec-111">lorsqu'il n'existe aucun intercepteur BAM pour l'hôte à analyser ;</span><span class="sxs-lookup"><span data-stu-id="b4eec-111">There is no BAM interceptor for the host you intend to monitor.</span></span>  
  
-   <span data-ttu-id="b4eec-112">lorsque l'intercepteur intégré n'est pas compatible avec la complexité de votre application.</span><span class="sxs-lookup"><span data-stu-id="b4eec-112">The built-in interceptor does not allow for the complexity of your application.</span></span>  
  
 <span data-ttu-id="b4eec-113">Lorsqu’il n’existe aucun intercepteur intégré, vous pouvez utiliser l’analyse BAM **EventStream** API pour capturer les événements d’intérêt.</span><span class="sxs-lookup"><span data-stu-id="b4eec-113">When there is no built-in interceptor, you can use the BAM **EventStream** APIs to capture the events of interest.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b4eec-114">Vous pouvez combiner **EventStream** classes avec la **BAMInterceptor** classe pour créer votre propre intercepteur.</span><span class="sxs-lookup"><span data-stu-id="b4eec-114">You can combine **EventStream** classes with the **BAMInterceptor** class to create your own interceptor.</span></span> <span data-ttu-id="b4eec-115">L'exemple du kit de développement logiciel (SDK) API BAM illustre un intercepteur générique qu'il est possible d'étendre.</span><span class="sxs-lookup"><span data-stu-id="b4eec-115">The BAM API SDK sample illustrates a simple generic interceptor that you can extend.</span></span> <span data-ttu-id="b4eec-116">La création de votre propre intercepteur vous permet d'instrumenter un certain nombre de processus similaires sans avoir à écrire un nouveau code pour chaque application.</span><span class="sxs-lookup"><span data-stu-id="b4eec-116">By constructing your own interceptor you can instrument a number of similar processes without writing new code for each application.</span></span> <span data-ttu-id="b4eec-117">Pour afficher l’exemple du SDK API BAM, consultez [l’API BAM (exemple BizTalk Server)](../core/bam-api-biztalk-server-sample.md).</span><span class="sxs-lookup"><span data-stu-id="b4eec-117">To view the BAM API SDK sample, see [BAM API (BizTalk Server Sample)](../core/bam-api-biztalk-server-sample.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4eec-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b4eec-118">See Also</span></span>  
 [<span data-ttu-id="b4eec-119">Implémentation de Solutions BAM</span><span class="sxs-lookup"><span data-stu-id="b4eec-119">Implementing BAM Solutions</span></span>](../core/implementing-bam-solutions.md)