---
title: Interface du moteur de messagerie | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 14241db3-edcf-4449-9ec8-2171a14496c0
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a135505240e94fb42e5810a3e7ac71d4c99c34a8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="messaging-engine-interfaces"></a><span data-ttu-id="c48ae-102">Interface du moteur de messagerie</span><span class="sxs-lookup"><span data-stu-id="c48ae-102">Messaging Engine Interfaces</span></span>
<span data-ttu-id="c48ae-103">Il existe trois interfaces publiques que les adaptateurs peuvent utiliser pour autoriser les interactions avec le moteur de messagerie.</span><span class="sxs-lookup"><span data-stu-id="c48ae-103">There are three public interfaces that adapters can use to allow interaction with the Messaging Engine.</span></span> <span data-ttu-id="c48ae-104">Elles sont définies dans les sections suivantes :</span><span class="sxs-lookup"><span data-stu-id="c48ae-104">These are outlined in the following sections.</span></span>  
  
## <a name="ibttransportproxy"></a><span data-ttu-id="c48ae-105">IBTTransportProxy</span><span class="sxs-lookup"><span data-stu-id="c48ae-105">IBTTransportProxy</span></span>  
 <span data-ttu-id="c48ae-106">Les adaptateurs interagissent toujours avec le moteur de messagerie en utilisant leur propre proxy de transport.</span><span class="sxs-lookup"><span data-stu-id="c48ae-106">Adapters always interact with the Messaging Engine by using their own transport proxy.</span></span> <span data-ttu-id="c48ae-107">Le proxy de transport est utilisé dans les opérations du type création de lots, obtention de la fabrique de messages et inscription des récepteurs isolés auprès du moteur.</span><span class="sxs-lookup"><span data-stu-id="c48ae-107">The transport proxy is used for operations such as creating batches, getting the message factory, and registering isolated receivers with the engine.</span></span>  
  
## <a name="ibttransportbatch"></a><span data-ttu-id="c48ae-108">IBTTransportBatch</span><span class="sxs-lookup"><span data-stu-id="c48ae-108">IBTTransportBatch</span></span>  
 <span data-ttu-id="c48ae-109">Cette interface est fournie par le moteur de messagerie et définit les méthodes qui sont utilisées par les adaptateurs pour exécuter des opérations sur les lots de messages.</span><span class="sxs-lookup"><span data-stu-id="c48ae-109">This interface is provided by the Messaging Engine, and defines methods that adapters can use to operate on batches of messages.</span></span> <span data-ttu-id="c48ae-110">Le moteur de messagerie traite les lots de façon asynchrone.</span><span class="sxs-lookup"><span data-stu-id="c48ae-110">The Messaging Engine processes batches asynchronously.</span></span>  
  
## <a name="ibtdtccommitconfirm"></a><span data-ttu-id="c48ae-111">IBTDTCCommitConfirm</span><span class="sxs-lookup"><span data-stu-id="c48ae-111">IBTDTCCommitConfirm</span></span>  
 <span data-ttu-id="c48ae-112">Les adaptateurs utilisant des transactions MSDTC (Microsoft Distributed Transaction Coordinator) explicites sur des lots doivent utiliser cette interface pour informer le moteur de l'issue de la transaction utilisant cette interface.</span><span class="sxs-lookup"><span data-stu-id="c48ae-112">Adapters using explicit Microsoft Distributed Transaction Coordinator (MSDTC) transactions on batches must use this interface to notify the engine of the outcome of the transaction using this interface.</span></span>