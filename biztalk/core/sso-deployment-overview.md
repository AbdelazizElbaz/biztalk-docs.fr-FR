---
title: "Vue d’ensemble du déploiement de l’authentification unique | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SSO, deploying example
- SSO, deploying
- deploying, SSO
- SSO, multiple computers
- examples, deploying
ms.assetid: 6eccee26-c392-41fe-97fb-3afe1685540f
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f88afb52f1db1263112732e70befb2ab95e6b135
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="sso-deployment-overview"></a><span data-ttu-id="85239-102">Vue d’ensemble du déploiement de l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="85239-102">SSO Deployment Overview</span></span>
<span data-ttu-id="85239-103">Dans cet exemple, le système est déployé sur trois domaines, lesquels contiennent les ordinateurs suivants :</span><span class="sxs-lookup"><span data-stu-id="85239-103">The system in this example is deployed over three domains, containing the following computers:</span></span>  
  
 <span data-ttu-id="85239-104">**Domaine ORCH.com**</span><span class="sxs-lookup"><span data-stu-id="85239-104">**Domain ORCH.com**</span></span>  
  
-   <span data-ttu-id="85239-105">Contrôleur de domaine ORCH</span><span class="sxs-lookup"><span data-stu-id="85239-105">ORCH domain controller</span></span>  
  
-   <span data-ttu-id="85239-106">HIS1, le serveur HISSO</span><span class="sxs-lookup"><span data-stu-id="85239-106">HIS1, the HISSO server</span></span>  
  
-   <span data-ttu-id="85239-107">HIS2, le serveur de secret principal</span><span class="sxs-lookup"><span data-stu-id="85239-107">HIS2, the Master Secret Server</span></span>  
  
-   <span data-ttu-id="85239-108">HIS3, la base de données d'administration</span><span class="sxs-lookup"><span data-stu-id="85239-108">HIS3, the Admin database</span></span>  
  
 <span data-ttu-id="85239-109">**Domaine SQL.com**</span><span class="sxs-lookup"><span data-stu-id="85239-109">**Domain SQL.com**</span></span>  
  
-   <span data-ttu-id="85239-110">Contrôleur de domaine SQL</span><span class="sxs-lookup"><span data-stu-id="85239-110">SQL domain controller</span></span>  
  
-   <span data-ttu-id="85239-111">SQL2, la base de données SSO</span><span class="sxs-lookup"><span data-stu-id="85239-111">SQL2, the SSO database</span></span>  
  
 <span data-ttu-id="85239-112">**Domaine HIS.com**</span><span class="sxs-lookup"><span data-stu-id="85239-112">**Domain HIS.com**</span></span>  
  
-   <span data-ttu-id="85239-113">Contrôleur de domaine HIS</span><span class="sxs-lookup"><span data-stu-id="85239-113">HIS domain controller</span></span>  
  
-   <span data-ttu-id="85239-114">Base de données HIS4</span><span class="sxs-lookup"><span data-stu-id="85239-114">HIS4 database</span></span>  
  
 <span data-ttu-id="85239-115">Les points clés qui définissent ce déploiement sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="85239-115">The key points defining this deployment are as follows:</span></span>  
  
-   <span data-ttu-id="85239-116">Les domaines ORCH.com et SQL.com entretiennent une relation d'approbation sélective bidirectionnelle.</span><span class="sxs-lookup"><span data-stu-id="85239-116">Domain ORCH.com and domain SQL.com have a two-way selective trust relationship.</span></span>  
  
-   <span data-ttu-id="85239-117">Le domaine ORCH.com est configuré en tant que niveau fonctionnel [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] ou [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] natif.</span><span class="sxs-lookup"><span data-stu-id="85239-117">Domain ORCH.com is configured as native [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] or [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] functional level.</span></span>  
  
-   <span data-ttu-id="85239-118">Tous les services SSO sont exécutés sous un compte d'utilisateur du domaine ORCH.com (Orch\SSOSvcUser).</span><span class="sxs-lookup"><span data-stu-id="85239-118">All SSO services are running on an ORCH.com domain user account (Orch\SSOSvcUser).</span></span> <span data-ttu-id="85239-119">L'utilisateur dispose des autorisations d'accès à l'ordinateur SQL2 du domaine SQL.com.</span><span class="sxs-lookup"><span data-stu-id="85239-119">The user is configured to have access permission on the SQL2 machine in the SQL.com domain.</span></span> <span data-ttu-id="85239-120">La transition de protocole et la délégation contrainte sont également configurées pour l'utilisateur au sein du domaine ORCH.com.</span><span class="sxs-lookup"><span data-stu-id="85239-120">The user is configured for protocol transition and constrain delegation within the ORCH.com domain.</span></span>  
  
-   <span data-ttu-id="85239-121">Un autre utilisateur du domaine ORCH.com (Orch\TestAppUser) est configuré pour exécuter des programmes de test.</span><span class="sxs-lookup"><span data-stu-id="85239-121">Another ORCH.com domain user (Orch\TestAppUser) is set for running test programs.</span></span> <span data-ttu-id="85239-122">La transition de protocole et la délégation contrainte sont également configurées pour cet utilisateur.</span><span class="sxs-lookup"><span data-stu-id="85239-122">This user is also configured for protocol transition and constrain delegation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85239-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="85239-123">See Also</span></span>  
 [<span data-ttu-id="85239-124">Processus de déploiement</span><span class="sxs-lookup"><span data-stu-id="85239-124">Deployment Process</span></span>](../core/deployment-process.md)