---
title: Configuration du réseau | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- deploying, network configuration
ms.assetid: fb6265b8-2e6d-4344-bb44-4f4fd995382d
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 83a9e8ffe6b278c91429835c3ae32c96d45ef22e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="network-configuration"></a><span data-ttu-id="9005b-102">Configuration réseau</span><span class="sxs-lookup"><span data-stu-id="9005b-102">Network Configuration</span></span>
<span data-ttu-id="9005b-103">Cette section fournit des indications pour la configuration du réseau dans votre déploiement.</span><span class="sxs-lookup"><span data-stu-id="9005b-103">This section provides prescriptive guidance for configuring the network in your deployment.</span></span> <span data-ttu-id="9005b-104">Pour plus d’informations, consultez [préparation au déploiement](../../adapters-and-accelerators/accelerator-swift/preparing-for-deployment.md).</span><span class="sxs-lookup"><span data-stu-id="9005b-104">For more information, see [Preparing for Deployment](../../adapters-and-accelerators/accelerator-swift/preparing-for-deployment.md).</span></span>  
  
 <span data-ttu-id="9005b-105">Définir des réseaux locaux virtuels (VLAN) dans le commutateur et puis connectez les câbles appropriés.</span><span class="sxs-lookup"><span data-stu-id="9005b-105">You define virtual local area networks (VLANs) in the switch and then connect the appropriate cables.</span></span> <span data-ttu-id="9005b-106">En définissant les réseaux locaux virtuels, vous désignez les ports sur le commutateur pour chaque segment de réseau ou de la couche.</span><span class="sxs-lookup"><span data-stu-id="9005b-106">By defining the VLANs, you are designating ports on the switch for each network segment or tier.</span></span> <span data-ttu-id="9005b-107">Vous devez créer un réseau local virtuel pour chacun des environnements suivants :</span><span class="sxs-lookup"><span data-stu-id="9005b-107">You must create a VLAN for each of the following environments:</span></span>  
  
-   [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="9005b-108">réception et envoi de couche</span><span class="sxs-lookup"><span data-stu-id="9005b-108"> receive and send tier</span></span>  
  
-   [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="9005b-109">couche d’orchestration et de la base de données</span><span class="sxs-lookup"><span data-stu-id="9005b-109"> orchestration and database tier</span></span>  
  
-   <span data-ttu-id="9005b-110">Réseau d’entreprise</span><span class="sxs-lookup"><span data-stu-id="9005b-110">Corporate network</span></span>  
  
 <span data-ttu-id="9005b-111">Après avoir défini les réseaux locaux virtuels, vous pouvez connecter les câbles réseau à partir des serveurs pour les ports appropriés sur le commutateur.</span><span class="sxs-lookup"><span data-stu-id="9005b-111">After you have defined the VLANs, you can connect the network cables from the servers to the appropriate ports on the switch.</span></span>  
  
 <span data-ttu-id="9005b-112">Contenu de cette section :</span><span class="sxs-lookup"><span data-stu-id="9005b-112">This section contains:</span></span>  
  
-   [<span data-ttu-id="9005b-113">Diagramme physique</span><span class="sxs-lookup"><span data-stu-id="9005b-113">Physical Diagram</span></span>](../../adapters-and-accelerators/accelerator-swift/physical-diagram.md)  
  
-   [<span data-ttu-id="9005b-114">Équilibrage de charge réseau</span><span class="sxs-lookup"><span data-stu-id="9005b-114">Network Load Balancing</span></span>](../../adapters-and-accelerators/accelerator-swift/network-load-balancing.md)