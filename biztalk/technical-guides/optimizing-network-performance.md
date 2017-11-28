---
title: "Optimisation des performances réseau | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b6c3985a-48b3-489b-8fe3-3b7bfd0515f9
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8225bd082140ac1347bc99a91ea209f9d79a8bab
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="optimizing-network-performance"></a><span data-ttu-id="75d74-102">Optimisation des performances réseau</span><span class="sxs-lookup"><span data-stu-id="75d74-102">Optimizing Network Performance</span></span>
<span data-ttu-id="75d74-103">Dans un environnement BizTalk Server sur lequel l’ordinateur BizTalk Server est distinct de l’ordinateur SQL Server, chaque message traité par BizTalk Server requiert la communication sur le réseau.</span><span class="sxs-lookup"><span data-stu-id="75d74-103">In a BizTalk Server environment where the BizTalk Server computer is separate from the SQL Server computer, each and every message processed by BizTalk Server requires communication over the network.</span></span> <span data-ttu-id="75d74-104">Cette communication comprend un trafic considérable entre l’ordinateur BizTalk Server et la base de données BizTalk MessageBox, la base de données de gestion BizTalk, les bases de données BAM et autres bases de données.</span><span class="sxs-lookup"><span data-stu-id="75d74-104">This communication includes considerable traffic between the BizTalk Server computer and the BizTalk MessageBox database, the BizTalk Management database, the BAM databases, and other databases.</span></span> <span data-ttu-id="75d74-105">Dans les scénarios de charge élevée, cette communication peut entraîner un trafic réseau considérable et peut devenir un goulot d’étranglement, en particulier lorsque les paramètres réseau n’ont pas été optimisées, n’est pas suffisant cartes d’interface réseau sont installés ou de bande passante réseau insuffisantes disponible.</span><span class="sxs-lookup"><span data-stu-id="75d74-105">In high-load scenarios, this communication can result in considerable network traffic and can become a bottleneck, especially when network settings have not been optimized, not enough network interface cards are installed, or insufficient network bandwidth is available.</span></span>  
  
 <span data-ttu-id="75d74-106">Cette section fournit des recommandations générales pour l’amélioration des performances réseau et décrit plusieurs entrées de Registre qui peuvent être modifiées pour optimiser la pile réseau pour atténuer l’occurrence des goulots d’étranglement sur le réseau.</span><span class="sxs-lookup"><span data-stu-id="75d74-106">This section provides some general recommendations for improving network performance and describes several registry entries that can be modified to optimize the network stack to mitigate the occurrence of bottlenecks on the network.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="75d74-107">Certaines recommandations de cette section nécessitent des modifications au Registre Windows.</span><span class="sxs-lookup"><span data-stu-id="75d74-107">Some of the recommendations in this section require modifications to the Windows registry.</span></span> <span data-ttu-id="75d74-108">Une utilisation incorrecte de l'Éditeur du Registre peut causer des problèmes vous obligeant à réinstaller votre système d'exploitation.</span><span class="sxs-lookup"><span data-stu-id="75d74-108">Incorrect use of Registry Editor may cause problems requiring you to reinstall your operating system.</span></span> <span data-ttu-id="75d74-109">Son utilisation est sous votre entière responsabilité.</span><span class="sxs-lookup"><span data-stu-id="75d74-109">Use Registry Editor at your own risk.</span></span> <span data-ttu-id="75d74-110">Pour plus d’informations sur la façon de sauvegarder, restaurer et modifier le Registre, consultez l’article de la Base de connaissances Microsoft [256896, « informations du Registre Windows pour les utilisateurs expérimentés »](http://go.microsoft.com/fwlink/?LinkId=62729) (http://go.microsoft.com/fwlink/?LinkId=62729).</span><span class="sxs-lookup"><span data-stu-id="75d74-110">For more information about how to back up, restore, and modify the registry, see the Microsoft Knowledge Base article [256896, "Windows registry information for advanced users"](http://go.microsoft.com/fwlink/?LinkId=62729) (http://go.microsoft.com/fwlink/?LinkId=62729).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="75d74-111">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="75d74-111">In This Section</span></span>  
  
-   [<span data-ttu-id="75d74-112">Instructions générales pour améliorer les performances du réseau</span><span class="sxs-lookup"><span data-stu-id="75d74-112">General Guidelines for Improving Network Performance</span></span>](../technical-guides/general-guidelines-for-improving-network-performance.md)  
  
-   [<span data-ttu-id="75d74-113">Paramètres qui peuvent être modifiées pour améliorer les performances réseau</span><span class="sxs-lookup"><span data-stu-id="75d74-113">Settings that can be Modified to Improve Network Performance</span></span>](../technical-guides/settings-that-can-be-modified-to-improve-network-performance.md)  
  
## <a name="see-also"></a><span data-ttu-id="75d74-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="75d74-114">See Also</span></span>  
 [<span data-ttu-id="75d74-115">Optimisation des performances</span><span class="sxs-lookup"><span data-stu-id="75d74-115">Optimizing Performance</span></span>](../technical-guides/optimizing-performance.md)