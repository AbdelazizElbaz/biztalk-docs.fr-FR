---
title: "Développement d’un adaptateur de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cd2623c4-dc92-435f-83d4-1b6213f3cf59
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c8be86000a154da7b3087d34e92f61da964065ed
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="developing-a-receive-adapter"></a><span data-ttu-id="1d415-102">Développement d'un adaptateur de réception</span><span class="sxs-lookup"><span data-stu-id="1d415-102">Developing a Receive Adapter</span></span>
<span data-ttu-id="1d415-103">Cette section décrit les interactions d'objets qui se produisent dans les adaptateurs de réception.</span><span class="sxs-lookup"><span data-stu-id="1d415-103">This section describes the object interactions that occur within receive adapters.</span></span> <span data-ttu-id="1d415-104">Ces informations vous serviront à développer des adaptateurs de réception personnalisés ou à comprendre le fonctionnement des adaptateurs natifs.</span><span class="sxs-lookup"><span data-stu-id="1d415-104">You can use this information to guide custom adapter development when creating receive adapters, or to learn about how the native adapters work.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1d415-105">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="1d415-105">In This Section</span></span>  
  
-   [<span data-ttu-id="1d415-106">Modèles d’échange pour les adaptateurs de réception</span><span class="sxs-lookup"><span data-stu-id="1d415-106">Exchange Patterns for Receive Adapters</span></span>](../core/exchange-patterns-for-receive-adapters.md)  
  
-   [<span data-ttu-id="1d415-107">Instanciation et initialisation un adaptateur de réception</span><span class="sxs-lookup"><span data-stu-id="1d415-107">Instantiating and Initializing a Receive Adapter</span></span>](../core/instantiating-and-initializing-a-receive-adapter.md)  
  
-   [<span data-ttu-id="1d415-108">Opérations de l’adaptateur de réception</span><span class="sxs-lookup"><span data-stu-id="1d415-108">Receive Adapter Operations</span></span>](../core/receive-adapter-operations.md)  
  
-   [<span data-ttu-id="1d415-109">Traitement par lot des Messages pour le traitement de réception</span><span class="sxs-lookup"><span data-stu-id="1d415-109">Batching Messages for Receive Processing</span></span>](../core/batching-messages-for-receive-processing.md)  
  
-   [<span data-ttu-id="1d415-110">Interfaces pour adaptateurs de réception</span><span class="sxs-lookup"><span data-stu-id="1d415-110">Interfaces for Receive Adapters</span></span>](../core/interfaces-for-receive-adapters.md)  
  
-   [<span data-ttu-id="1d415-111">Prise en charge de l’authentification unique pour les adaptateurs de réception</span><span class="sxs-lookup"><span data-stu-id="1d415-111">SSO Support for Receive Adapters</span></span>](../core/sso-support-for-receive-adapters.md)