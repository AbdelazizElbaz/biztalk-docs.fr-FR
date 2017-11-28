---
title: Installer les correctifs COM + | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 587ae3da-db65-4da8-9d3b-89effb91b197
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 40610c649e00993323adedf0ea29330dd289a0e3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="installing-com-hotfix-rollup-packages"></a><span data-ttu-id="3afd7-102">Installer les correctifs COM +</span><span class="sxs-lookup"><span data-stu-id="3afd7-102">Installing COM+ Hotfix Rollup Packages</span></span>
> [!NOTE]  
>  <span data-ttu-id="3afd7-103">Cette rubrique s’applique uniquement pour Windows Server 2003.</span><span class="sxs-lookup"><span data-stu-id="3afd7-103">This topic is applicable only for Windows Server 2003.</span></span>  
  
 <span data-ttu-id="3afd7-104">Vous devez installer la dernière version du package de correctifs cumulatifs COM + Windows Server 2003 et la version la plus récente du correctif cumulatif Distributed Transaction Coordinator (DTC).</span><span class="sxs-lookup"><span data-stu-id="3afd7-104">You should install the last version of the Windows Server 2003 COM+ hotfix rollup package and latest version of the Distributed Transaction Coordinator (DTC) rollup package.</span></span> <span data-ttu-id="3afd7-105">Il s’agit, car les packages incluent plusieurs correctifs de stabilité et de performances.</span><span class="sxs-lookup"><span data-stu-id="3afd7-105">This is because the packages include many performance and stability fixes.</span></span>  
  
 <span data-ttu-id="3afd7-106">Vous devez installer ces correctifs cumulatifs sur tous les ordinateurs exécutant [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et sur tous les ordinateurs exécutant SQL Server.</span><span class="sxs-lookup"><span data-stu-id="3afd7-106">You should install these rollups on all computers running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and on all computers running SQL Server.</span></span> <span data-ttu-id="3afd7-107">Les sélections multiples sont particulièrement importants pour votre solution BizTalk s’exécuter correctement dans les scénarios à débit élevé.</span><span class="sxs-lookup"><span data-stu-id="3afd7-107">The rollups are especially important for your BizTalk solution to perform well in high-throughput scenarios.</span></span>  
  
 <span data-ttu-id="3afd7-108">Les problèmes DTC qui ont été résolus sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="3afd7-108">The DTC issues that have been fixed are as follows:</span></span>  
  
-   <span data-ttu-id="3afd7-109">Arrêt inattendu de DTC</span><span class="sxs-lookup"><span data-stu-id="3afd7-109">Unexpected DTC shutdown</span></span>  
  
-   <span data-ttu-id="3afd7-110">Problèmes de fragmentation de mémoire</span><span class="sxs-lookup"><span data-stu-id="3afd7-110">Memory fragmentation issues</span></span>  
  
-   <span data-ttu-id="3afd7-111">DTC peut cesser de répondre en charge</span><span class="sxs-lookup"><span data-stu-id="3afd7-111">DTC may stop responding under load</span></span>  
  
-   <span data-ttu-id="3afd7-112">DTC peut entraîner une fuite de mémoire ou cesser de répondre lorsqu’il est utilisé avec[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3afd7-112">DTC may leak memory or stop responding when used with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]</span></span>  
  
-   <span data-ttu-id="3afd7-113">Performances de DTC sous charge ont été améliorées</span><span class="sxs-lookup"><span data-stu-id="3afd7-113">Performance of DTC under load has been improved</span></span>  
  
## <a name="installing-the-com-rollup-package"></a><span data-ttu-id="3afd7-114">L’installation du Package du correctif cumulatif de COM +</span><span class="sxs-lookup"><span data-stu-id="3afd7-114">Installing the COM+ Rollup Package</span></span>  
 <span data-ttu-id="3afd7-115">COM + n’est plus en publiant cumulatifs.</span><span class="sxs-lookup"><span data-stu-id="3afd7-115">COM+ is no longer releasing rollup packages.</span></span> <span data-ttu-id="3afd7-116">Suivez ces informations pour installer le dernier package COM + :</span><span class="sxs-lookup"><span data-stu-id="3afd7-116">Follow this information to install the last COM+ package:</span></span>  
  
-   <span data-ttu-id="3afd7-117">La version finale du cumul COM + est le « Windows Server 2003 post-Service Pack 2 COM + 1.5 correctif cumulatif Package 12 ».</span><span class="sxs-lookup"><span data-stu-id="3afd7-117">The final version of the COM+ rollup is the “Windows Server 2003 Post-Service Pack 2 COM+ 1.5 Hotfix Rollup Package 12”.</span></span> <span data-ttu-id="3afd7-118">Ce correctif logiciel va installer sur n’importe quelle version de Windows Server 2003, y compris celles sans service pack installé.</span><span class="sxs-lookup"><span data-stu-id="3afd7-118">This hotfix will install on any version of Windows Server 2003, even those without a service pack installed.</span></span> <span data-ttu-id="3afd7-119">Vous trouverez plus d’informations sur ce correctif logiciel dans l’article de la Base de connaissances Microsoft 934016, [« disponibilité de Windows Server 2003 post-Service Pack 2 COM + 1.5 correctif cumulatif Package 12 «](http://go.microsoft.com/fwlink/?LinkId=158756) (http://go.microsoft.com/fwlink/?LinkId=158756).</span><span class="sxs-lookup"><span data-stu-id="3afd7-119">More information about this hotfix can be found in Microsoft Knowledge Base article 934016, ["Availability of Windows Server 2003 Post-Service Pack 2 COM+ 1.5 Hotfix Rollup Package 12"](http://go.microsoft.com/fwlink/?LinkId=158756) (http://go.microsoft.com/fwlink/?LinkId=158756).</span></span>  
  
## <a name="installing-the-dtc-rollup-package"></a><span data-ttu-id="3afd7-120">Installation du Package de correctif cumulatif DTC</span><span class="sxs-lookup"><span data-stu-id="3afd7-120">Installing the DTC Rollup Package</span></span>  
 <span data-ttu-id="3afd7-121">DTC publiera cumulatifs indépendantes de COM +.</span><span class="sxs-lookup"><span data-stu-id="3afd7-121">DTC will be releasing rollup packages independent of COM+.</span></span> <span data-ttu-id="3afd7-122">Suivez ces informations pour installer le dernier package DTC :</span><span class="sxs-lookup"><span data-stu-id="3afd7-122">Follow this information to install the latest DTC package:</span></span>  
  
-   <span data-ttu-id="3afd7-123">À ce jour, le dernier correctif cumulatif DTC est « Package 16 ».</span><span class="sxs-lookup"><span data-stu-id="3afd7-123">As of this writing, the latest DTC hotfix rollup is “Package 16”.</span></span> <span data-ttu-id="3afd7-124">Vous trouverez plus d’informations sur ce correctif logiciel dans l’article de la Base de connaissances Microsoft 958013, [« Liste des problèmes MS DTC qui sont résolus dans Windows Server 2003 MS DTC Package de correctifs cumulatifs 16 »](http://support.microsoft.com/kb/979919) (http://support.microsoft.com/kb/979919) .</span><span class="sxs-lookup"><span data-stu-id="3afd7-124">More information about this hotfix can be found in Microsoft Knowledge Base article 958013, ["List of the MS DTC issues that are fixed in Windows Server 2003 MS DTC Hotfix Rollup Package 16"](http://support.microsoft.com/kb/979919) (http://support.microsoft.com/kb/979919).</span></span>  
  
     <span data-ttu-id="3afd7-125">L’article sur le dernier package de correctif cumulatif de correctif logiciel DTC peut être recherché en [http://support.microsoft.com](http://support.microsoft.com/) pour l’expression (y compris les guillemets) :</span><span class="sxs-lookup"><span data-stu-id="3afd7-125">The KB article about the latest DTC hotfix rollup package can be found by searching [http://support.microsoft.com](http://support.microsoft.com/) for the phrase (including the quotes):</span></span>  
  
    ```  
    "MS DTC Hotfix Rollup Package"  
    ```  
  
     <span data-ttu-id="3afd7-126">La requête suivante effectue cette recherche pour vous.</span><span class="sxs-lookup"><span data-stu-id="3afd7-126">The following query does this search for you.</span></span> <span data-ttu-id="3afd7-127">Choisir la plus récente :</span><span class="sxs-lookup"><span data-stu-id="3afd7-127">Choose the latest one:</span></span>  
  
     [<span data-ttu-id="3afd7-128">http://support.Microsoft.com/search/default.aspx?Query= « MS + DTC + + Package correctif cumulatif + »</span><span class="sxs-lookup"><span data-stu-id="3afd7-128">http://support.microsoft.com/search/default.aspx?query="MS+DTC+Hotfix+Rollup+Package"</span></span>](http://support.microsoft.com/search/default.aspx?query=%22MS+DTC+Hotfix+Rollup+Package%22)