---
title: TIBCO Rendezvous Limitations | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: TIBCO Rendezvous, limitations
ms.assetid: 8e210457-2887-43f9-a249-be1daa6ee4eb
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 717188e42450d13dee92364cd9c673aaaf48eaf6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="tibco-rendezvous-limitations"></a><span data-ttu-id="1ae13-102">Restrictions en relation avec TIBCO Rendezvous</span><span class="sxs-lookup"><span data-stu-id="1ae13-102">TIBCO Rendezvous Limitations</span></span>
<span data-ttu-id="1ae13-103">Dans TIBCO Rendezvous, l'unicité des noms de champ n'est pas garantie.</span><span class="sxs-lookup"><span data-stu-id="1ae13-103">In TIBCO Rendezvous, field name uniqueness is not guaranteed.</span></span> <span data-ttu-id="1ae13-104">Si un message TIBCO Rendezvous contient deux noms de champ identiques, le fichier XML qui en résulte n'est pas valide.</span><span class="sxs-lookup"><span data-stu-id="1ae13-104">If a TIBCO Rendezvous message contains two field names that are the same, the resulting XML is not valid.</span></span>  
  
 <span data-ttu-id="1ae13-105">Les autres limitations suivantes s'appliquent :</span><span class="sxs-lookup"><span data-stu-id="1ae13-105">Other limitations include the following:</span></span>  
  
-   <span data-ttu-id="1ae13-106">Il n'est pas possible de classer/trier les champs.</span><span class="sxs-lookup"><span data-stu-id="1ae13-106">Field ordering/sorting is not provided.</span></span>  
  
-   <span data-ttu-id="1ae13-107">Selon la documentation de TIBCO Rendezvous, les caractères non imprimables ne sont pas utilisés dans les noms d'objet. Il reste toutefois possible que de tels caractères soient utilisés.</span><span class="sxs-lookup"><span data-stu-id="1ae13-107">According to TIBCO Rendezvous documentation, non-printable characters are not used in subject names; however, it is still possible that such characters are used.</span></span> <span data-ttu-id="1ae13-108">L'adaptateur BizTalk pour TIBCO Rendezvous ne prend pas en charge les noms d'objet contenant ces caractères.</span><span class="sxs-lookup"><span data-stu-id="1ae13-108">BizTalk Adapter for TIBCO Rendezvous does not support subject names containing those characters.</span></span>  
  
-   <span data-ttu-id="1ae13-109">La connexion sécurisée aux démons n'est pas prise en charge.</span><span class="sxs-lookup"><span data-stu-id="1ae13-109">Secure connection to daemons is not supported.</span></span>  
  
-   <span data-ttu-id="1ae13-110">Les types de données personnalisés ne sont pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="1ae13-110">Custom data types are not supported.</span></span>  
  
-   <span data-ttu-id="1ae13-111">La messagerie certifiée n'est pas prise en charge du côté transmetteur.</span><span class="sxs-lookup"><span data-stu-id="1ae13-111">Certified Messaging is not supported on the transmit side.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ae13-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1ae13-112">See Also</span></span>  
 <span data-ttu-id="1ae13-113">[Concepts de TIBCO Rendezvous](../core/tibco-rendezvous-concepts.md) </span><span class="sxs-lookup"><span data-stu-id="1ae13-113">[TIBCO Rendezvous Concepts](../core/tibco-rendezvous-concepts.md) </span></span>  
 [<span data-ttu-id="1ae13-114">Bien démarrer</span><span class="sxs-lookup"><span data-stu-id="1ae13-114">Getting Started</span></span>](../core/getting-started-with-biztalk-adapter-for-tibco-rendezvous.md)