---
title: "Emplacements de réception et événements Rendezvous TIBCO | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: receive locations, life cycle
ms.assetid: 3576af82-4723-4efc-961e-40b1150cf13d
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e9278687ff212fc2368eca138780417d7c052824
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="tibco-rendezvous-events-and-receive-locations"></a><span data-ttu-id="6837e-102">Emplacements de réception et événements Rendezvous TIBCO</span><span class="sxs-lookup"><span data-stu-id="6837e-102">TIBCO Rendezvous Events and Receive Locations</span></span>
<span data-ttu-id="6837e-103">Un système TIBCO Rendezvous peut envoyer des messages vers le nom d'objet de son choix.</span><span class="sxs-lookup"><span data-stu-id="6837e-103">Any TIBCO Rendezvous system can send messages to their subject name of choice.</span></span> <span data-ttu-id="6837e-104">Le concept de *événement* est la génération de messages par d’autres programmes TIBCO Rendezvous.</span><span class="sxs-lookup"><span data-stu-id="6837e-104">The concept of *event* is the generation of messages by other TIBCO Rendezvous programs.</span></span>  
  
 <span data-ttu-id="6837e-105">Les étapes suivantes décrivent le cycle de vie d'un emplacement de réception :</span><span class="sxs-lookup"><span data-stu-id="6837e-105">The following steps describe the life cycle of a receive location:</span></span>  
  
1.  <span data-ttu-id="6837e-106">création d'un emplacement de réception ;</span><span class="sxs-lookup"><span data-stu-id="6837e-106">Receive location is created.</span></span>  
  
2.  <span data-ttu-id="6837e-107">association de l'emplacement de réception à un hôte ;</span><span class="sxs-lookup"><span data-stu-id="6837e-107">Receive location is associated with a host.</span></span>  
  
3.  <span data-ttu-id="6837e-108">liaison de l'emplacement de réception à une orchestration ;</span><span class="sxs-lookup"><span data-stu-id="6837e-108">Receive location is bound to an orchestration.</span></span>  
  
4.  <span data-ttu-id="6837e-109">activation de l'emplacement de réception ;</span><span class="sxs-lookup"><span data-stu-id="6837e-109">Receive location is enabled.</span></span>  
  
5.  <span data-ttu-id="6837e-110">réception de messages sur l'emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="6837e-110">Receive location receives messages.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6837e-111">Le nom de chaque emplacement de réception doit être unique.</span><span class="sxs-lookup"><span data-stu-id="6837e-111">Each receive location must have a unique name.</span></span> <span data-ttu-id="6837e-112">Deux emplacements de réception ne peuvent pas avoir le même nom au sein d'un même déploiement [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6837e-112">Two receive locations cannot have the same name in the same [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] deployment.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6837e-113">Il est recommandé de définir des listes de contrôle d'accès renforcées dans l'emplacement de dépôt des emplacements de réception.</span><span class="sxs-lookup"><span data-stu-id="6837e-113">It is recommended that you set strong access control lists (ACL) in the receive locations drop locations.</span></span> <span data-ttu-id="6837e-114">Par exemple, vous devez définir des listes de contrôle d'accès renforcées pour le répertoire dans lequel l'emplacement de réception des fichiers sélectionne des messages, afin que seuls les utilisateurs autorisés puissent déposer des messages dans cet emplacement.</span><span class="sxs-lookup"><span data-stu-id="6837e-114">For example, you must set strong ACLs for the directory where the file receive location picks up messages, so that only authorized users can drop messages in this location.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6837e-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6837e-115">See Also</span></span>  
 [<span data-ttu-id="6837e-116">Gestionnaires de réception création TIBCO Rendezvous</span><span class="sxs-lookup"><span data-stu-id="6837e-116">Creating TIBCO Rendezvous Receive Handlers</span></span>](../core/creating-tibco-rendezvous-receive-handlers.md)