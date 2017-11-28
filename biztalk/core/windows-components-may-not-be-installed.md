---
title: "Les composants de Windows ne peuvent pas être installés | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fc78ac0a-ee21-4633-afb3-1357efd29903
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 506f9c310a75c9f65564e4feb047157731bafa66
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="windows-components-may-not-be-installed"></a><span data-ttu-id="57eae-102">Les composants Windows ne sont peut-être pas installés</span><span class="sxs-lookup"><span data-stu-id="57eae-102">Windows components may not be installed</span></span>
## <a name="details"></a><span data-ttu-id="57eae-103">Détails</span><span class="sxs-lookup"><span data-stu-id="57eae-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="57eae-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="57eae-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="57eae-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="57eae-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="57eae-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="57eae-106">Event ID</span></span>|<span data-ttu-id="57eae-107">0</span><span class="sxs-lookup"><span data-stu-id="57eae-107">0</span></span>|  
|<span data-ttu-id="57eae-108">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="57eae-108">Event Source</span></span>|<span data-ttu-id="57eae-109">0</span><span class="sxs-lookup"><span data-stu-id="57eae-109">0</span></span>|  
|<span data-ttu-id="57eae-110">Composant</span><span class="sxs-lookup"><span data-stu-id="57eae-110">Component</span></span>|<span data-ttu-id="57eae-111">0</span><span class="sxs-lookup"><span data-stu-id="57eae-111">0</span></span>|  
|<span data-ttu-id="57eae-112">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="57eae-112">Symbolic Name</span></span>|<span data-ttu-id="57eae-113">0</span><span class="sxs-lookup"><span data-stu-id="57eae-113">0</span></span>|  
|<span data-ttu-id="57eae-114">Texte du message</span><span class="sxs-lookup"><span data-stu-id="57eae-114">Message Text</span></span>|<span data-ttu-id="57eae-115">Le composant Windows suivant n’est peut-être pas être installé : serveur d’applications -&gt; Internet Information Services (IIS) -&gt; fichiers communs.</span><span class="sxs-lookup"><span data-stu-id="57eae-115">The following Windows component may not be installed: Application Server -&gt; Internet Information Services (IIS) -&gt; Common Files.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="57eae-116">Explication</span><span class="sxs-lookup"><span data-stu-id="57eae-116">Explanation</span></span>  
 <span data-ttu-id="57eae-117">Cette erreur se produit lors d'une tentative de publication si Internet Information Services n'est pas installé sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="57eae-117">This error will occur when publishing is attempted without Internet Information Services (IIS) installed on the local computer.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="57eae-118">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="57eae-118">User Action</span></span>  
 <span data-ttu-id="57eae-119">Pour Windows 7 et Windows Vista SP2, installez IIS sur l'ordinateur local et configurez IIS comme suit :</span><span class="sxs-lookup"><span data-stu-id="57eae-119">For Windows 7 and Windows Vista SP2, Install IIS on the local machine and configure IIS as follows:</span></span>  
  
1.  <span data-ttu-id="57eae-120">Cliquez sur **Démarrer**, cliquez sur **le panneau de configuration**, puis cliquez sur **programmes**.</span><span class="sxs-lookup"><span data-stu-id="57eae-120">Click **Start**, click **Control Panel**, and click **Programs**.</span></span>  
  
2.  <span data-ttu-id="57eae-121">Cliquez sur **activer des fonctionnalités Windows et**.</span><span class="sxs-lookup"><span data-stu-id="57eae-121">Click **Turn Windows features on and off**.</span></span> <span data-ttu-id="57eae-122">L'Assistant Fonctionnalités Windows s'affiche.</span><span class="sxs-lookup"><span data-stu-id="57eae-122">The Windows Features Wizard appears.</span></span>  
  
3.  <span data-ttu-id="57eae-123">Pour ajouter le composant IIS, activez-le.</span><span class="sxs-lookup"><span data-stu-id="57eae-123">To add, check the IIS component.</span></span>  
  
 <span data-ttu-id="57eae-124">Pour [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] et [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)], installez IIS sur l'ordinateur local et configurez IIS comme suit :</span><span class="sxs-lookup"><span data-stu-id="57eae-124">For [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] and [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)], Install IIS on the local machine and configure IIS as follows:</span></span>  
  
1.  <span data-ttu-id="57eae-125">Cliquez sur **Démarrer**, cliquez sur **le panneau de configuration**, puis cliquez sur **outils d’administration**.</span><span class="sxs-lookup"><span data-stu-id="57eae-125">Click **Start**, click **Control Panel**, and click **Administrative Tools**.</span></span>  
  
2.  <span data-ttu-id="57eae-126">Cliquez sur **le Gestionnaire de serveur**.</span><span class="sxs-lookup"><span data-stu-id="57eae-126">Click **Server Manager**.</span></span> <span data-ttu-id="57eae-127">La fenêtre Gestionnaire de serveur s'affiche.</span><span class="sxs-lookup"><span data-stu-id="57eae-127">The Server Manger window appears.</span></span>  
  
3.  <span data-ttu-id="57eae-128">Cliquez sur **ajouter des rôles**, Assistant Ajout de rôles s’affiche.</span><span class="sxs-lookup"><span data-stu-id="57eae-128">Click **Add Roles**, Add Roles Wizard appears.</span></span>  
  
4.  <span data-ttu-id="57eae-129">Pour ajouter, sélectionnez le composant IIS.</span><span class="sxs-lookup"><span data-stu-id="57eae-129">To add, Select IIS component.</span></span>