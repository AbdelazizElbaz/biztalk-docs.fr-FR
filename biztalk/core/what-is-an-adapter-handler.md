---
title: "Qu'est-ce qu'un gestionnaire d'adaptateur ? | Microsoft Docs"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- handlers [adapters]
- adapters, handlers
- handlers [adapters], about handlers
ms.assetid: 4d1afa39-6320-467f-a7e8-f5f18236648e
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7c8a1b60661427776dd4e35ffce27bf120bf94a7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="what-is-an-adapter-handler"></a><span data-ttu-id="8c936-103">Qu'est-ce qu'un gestionnaire d'adaptateur ?</span><span class="sxs-lookup"><span data-stu-id="8c936-103">What Is an Adapter Handler?</span></span>
<span data-ttu-id="8c936-104">Un gestionnaire d'adaptateur est une instance d'un hôte BizTalk dans lequel le code d'adaptateur est exécuté.</span><span class="sxs-lookup"><span data-stu-id="8c936-104">An adapter handler is an instance of a BizTalk host in which the adapter code runs.</span></span> <span data-ttu-id="8c936-105">Lorsque vous spécifiez un gestionnaire d'envoi ou de réception pour un adaptateur, vous indiquez l'instance d'hôte dans le contexte de laquelle le code d'adaptateur sera exécuté.</span><span class="sxs-lookup"><span data-stu-id="8c936-105">When you specify a send or receive handler for an adapter you are specifying which host instance the adapter code will run in the context of.</span></span> <span data-ttu-id="8c936-106">Un gestionnaire d'adaptateur est chargé d'exécuter l'adaptateur et contient les propriétés d'une instance spécifique d'un adaptateur.</span><span class="sxs-lookup"><span data-stu-id="8c936-106">An adapter handler is responsible for executing the adapter and contains properties for a specific instance of an adapter.</span></span> <span data-ttu-id="8c936-107">Une configuration BizTalk Server par défaut créera les gestionnaires d'adaptateur pour les adaptateurs installés, mais vous pouvez créer d'autres gestionnaires d'adaptateur à des fins d'équilibrage de la charge ou pour isoler le processus d'un gestionnaire d'adaptateur particulier.</span><span class="sxs-lookup"><span data-stu-id="8c936-107">A default BizTalk Server configuration will create adapter handlers for all of the installed adapters, but you may want to create additional adapter handlers for purposes of load balancing or to provide process isolation for a particular adapter handler.</span></span>  
  
 <span data-ttu-id="8c936-108">Les gestionnaires d'adaptateur sont liés à une instance d'hôte BizTalk. Les instances d'hôte BizTalk sont liées à un serveur BizTalk.</span><span class="sxs-lookup"><span data-stu-id="8c936-108">Adapter handlers are bound to a BizTalk Host instance, and BizTalk Host instances are bound to a BizTalk server.</span></span> <span data-ttu-id="8c936-109">Par conséquent, vous devez ajouter des serveurs BizTalk supplémentaires à votre groupe BizTalk si vous souhaitez équilibrer la charge liée aux processus des adaptateurs entre les serveurs BizTalk.</span><span class="sxs-lookup"><span data-stu-id="8c936-109">Therefore, you must add additional BizTalk servers to your BizTalk group if you want to load balance adapter processing across BizTalk servers.</span></span> <span data-ttu-id="8c936-110">Il n'est pas nécessaire d'ajouter d'autres serveurs BizTalk à votre groupe BizTalk si vous créez des gestionnaires d'adaptateur supplémentaires afin d'isoler les processus.</span><span class="sxs-lookup"><span data-stu-id="8c936-110">You do not need to add additional BizTalk servers to your BizTalk group if you are creating additional adapter handlers for the purpose of process isolation.</span></span>  
  
 <span data-ttu-id="8c936-111">Si vous devez créer une instance d'hôte dans laquelle exécuter un gestionnaire d'adaptateur, vous devez d'abord créer un hôte, puis créer une instance de cet hôte à exécuter sur un de vos serveurs BizTalk.</span><span class="sxs-lookup"><span data-stu-id="8c936-111">If you need to create a new host instance to run an adapter handler in, you must first create a host and then create an instance of that host to run on one of your BizTalk servers.</span></span> <span data-ttu-id="8c936-112">Pour plus d’informations, consultez [la création d’un nouvel hôte](../core/how-to-create-a-new-host.md) et [l’ajout d’une Instance d’hôte](../core/how-to-add-a-host-instance.md).</span><span class="sxs-lookup"><span data-stu-id="8c936-112">For more information, see [How to Create a New Host](../core/how-to-create-a-new-host.md) and [How to Add a Host Instance](../core/how-to-add-a-host-instance.md).</span></span>  
  
 <span data-ttu-id="8c936-113">Tous les gestionnaires d'adaptateur, à l'exception des gestionnaires de réception des adaptateurs HTTP et SOAP, doivent être configurés pour être exécutés sur un hôte In-process.</span><span class="sxs-lookup"><span data-stu-id="8c936-113">All adapter handlers except for HTTP and SOAP adapter receive handlers must be configured to run in an in-process host.</span></span> <span data-ttu-id="8c936-114">Les gestionnaires de réception des adaptateurs HTTP et SOAP peuvent uniquement être exécutés sur un hôte isolé.</span><span class="sxs-lookup"><span data-stu-id="8c936-114">HTTP and SOAP adapter receive handlers can only be run in an isolated host.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c936-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8c936-115">See Also</span></span>  
 [<span data-ttu-id="8c936-116">Création et suppression de gestionnaires d’adaptateur</span><span class="sxs-lookup"><span data-stu-id="8c936-116">Creating and Deleting Adapter Handlers</span></span>](../core/creating-and-deleting-adapter-handlers.md)