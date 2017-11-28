---
title: Diagramme physique | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: deploying, network configuration
ms.assetid: 4291727b-8687-496a-8f03-0da4b3201967
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0fcd0558d8fe3d45063a53800b1f3c082a2ba056
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="physical-diagram"></a><span data-ttu-id="5a4fc-102">Diagramme physique</span><span class="sxs-lookup"><span data-stu-id="5a4fc-102">Physical Diagram</span></span>
<span data-ttu-id="5a4fc-103">Un déploiement classique a mis en cluster des ordinateurs BizTalk Server pour la messagerie (envoi et réception), les ordinateurs pour exécuter le processus d’entreprise (orchestration), les ordinateurs BizTalk Server pour les modèles InfoPath (site MRSR), de l’accès à BizTalk Server et ordinateurs SQL Server en cluster.</span><span class="sxs-lookup"><span data-stu-id="5a4fc-103">A typical deployment has clustered BizTalk Server computers for messaging (sending and receiving), BizTalk Server computers for executing the business process (orchestration), BizTalk Server computers for accessing the InfoPath templates (MRSR site), and clustered SQL Server computers.</span></span> <span data-ttu-id="5a4fc-104">Le déploiement suivant permet de garantir un environnement sécurisé à partir de l’intranet et les utilisateurs sur Internet.</span><span class="sxs-lookup"><span data-stu-id="5a4fc-104">The following deployment ensures a secure environment from both the intranet and Internet users.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5a4fc-105">Ce déploiement typique est la configuration recommandée.</span><span class="sxs-lookup"><span data-stu-id="5a4fc-105">This typical deployment is the recommended configuration.</span></span> <span data-ttu-id="5a4fc-106">Vous devez vérifier vos propres besoins et les configurations de serveur pour vous assurer que votre déploiement fonctionne correctement.</span><span class="sxs-lookup"><span data-stu-id="5a4fc-106">You will need to verify your own business needs and server configurations to make certain your deployment works correctly.</span></span>  
  
 <span data-ttu-id="5a4fc-107">Vous pouvez faire évoluer ce déploiement vers le haut ou vers le bas, out ou, selon le profil d’utilisation et des besoins commerciaux croissants.</span><span class="sxs-lookup"><span data-stu-id="5a4fc-107">You can scale this deployment up or down, out or back, depending on the usage profile and your growing business needs.</span></span> <span data-ttu-id="5a4fc-108">Les scénarios d’évolutivité classiques comprennent l’ajout d’un ou plusieurs serveurs dans chaque cluster afin de garantir une disponibilité élevée ou un meilleur débit.</span><span class="sxs-lookup"><span data-stu-id="5a4fc-108">Typical scalability scenarios include adding one or more servers in each cluster to ensure higher availability or better throughput.</span></span> <span data-ttu-id="5a4fc-109">Petites entreprises préférerez peut-être opter pour réduire la puissance leur déploiement pour que les mêmes serveurs exécuter plusieurs fonctions, telles qu’avoir une [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] ordinateur gérer l’orchestration et messagerie.</span><span class="sxs-lookup"><span data-stu-id="5a4fc-109">Smaller enterprises might prefer scaling back their deployment to have the same servers perform multiple functions, such as having one [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] computer handle both orchestration and messaging.</span></span> [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]<span data-ttu-id="5a4fc-110">[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]prend en charge le déploiement sur un seul serveur.</span><span class="sxs-lookup"><span data-stu-id="5a4fc-110">[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] supports deployment on a single server.</span></span> <span data-ttu-id="5a4fc-111">L’illustration suivante montre un exemple de l’environnement de déploiement distribué recommandée pour un déploiement complet de A4SWIFT.</span><span class="sxs-lookup"><span data-stu-id="5a4fc-111">The following figure shows an example of the recommended distributed deployment environment for a full A4SWIFT deployment.</span></span>  
  
 ![](../../adapters-and-accelerators/accelerator-swift/media/fsa-deploy-full.gif "FSA_Deploy_Full")  
<span data-ttu-id="5a4fc-112">Exemple de déploiement complet A4SWIFT</span><span class="sxs-lookup"><span data-stu-id="5a4fc-112">Example of a full A4SWIFT deployment</span></span>