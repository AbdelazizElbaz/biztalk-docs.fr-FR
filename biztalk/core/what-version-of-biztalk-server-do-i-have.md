---
title: "Quelle version de BizTalk Server possédez-vous ? | Microsoft Docs"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cb651202-f682-4e5f-8a79-221877af20a7
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ce5508a3b7c78e52fe5fcbef40e351dce58f2816
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="what-version-of-biztalk-server-do-i-have"></a><span data-ttu-id="54ac4-103">Quelle version de BizTalk Server possédez-vous ?</span><span class="sxs-lookup"><span data-stu-id="54ac4-103">What Version of BizTalk Server Do I Have?</span></span>
<span data-ttu-id="54ac4-104">Vous pouvez exécuter différentes versions et éditions de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="54ac4-104">You may be running different versions and different editions of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="54ac4-105">Cette rubrique vous montre comment déterminer [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] informations sur l’installation, y compris le chemin d’installation, Édition et numéro de version.</span><span class="sxs-lookup"><span data-stu-id="54ac4-105">This topic shows you how to determine [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation information, including the version number, edition, and installation path.</span></span>  
  
## <a name="use-the-registry"></a><span data-ttu-id="54ac4-106">Utiliser le Registre</span><span class="sxs-lookup"><span data-stu-id="54ac4-106">Use the registry</span></span>
  
1.  <span data-ttu-id="54ac4-107">Sélectionnez **Démarrer**, type `regedt32`, puis ouvrez-le.</span><span class="sxs-lookup"><span data-stu-id="54ac4-107">Select **Start**, type `regedt32`, and then open it.</span></span>  
  
2.  <span data-ttu-id="54ac4-108">Développez **HKEY_LOCAL_MACHINE**, développez **logiciel**, développez **Microsoft**, développez **BizTalk Server**, puis sélectionnez **3.0**.</span><span class="sxs-lookup"><span data-stu-id="54ac4-108">Expand **HKEY_LOCAL_MACHINE**, expand **SOFTWARE**, expand **Microsoft**, expand **BizTalk Server**, and then select **3.0**.</span></span>  
  
3.  <span data-ttu-id="54ac4-109">Le volet droit affiche les informations d’installation, à savoir :</span><span class="sxs-lookup"><span data-stu-id="54ac4-109">The right pane displays installation information, including:</span></span>  
  
    |<span data-ttu-id="54ac4-110">Sous-clé</span><span class="sxs-lookup"><span data-stu-id="54ac4-110">Sub-key</span></span>|<span data-ttu-id="54ac4-111"> Description</span><span class="sxs-lookup"><span data-stu-id="54ac4-111">Description</span></span>|  
    |--------------|-----------------|  
    |<span data-ttu-id="54ac4-112">**Chemin d’installation**</span><span class="sxs-lookup"><span data-stu-id="54ac4-112">**InstallPath**</span></span>|<span data-ttu-id="54ac4-113">Répertorie le chemin d’installation sous lequel vous avez installé [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="54ac4-113">Lists the installation path where you installed [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>|  
    |<span data-ttu-id="54ac4-114">**ProductEdition**</span><span class="sxs-lookup"><span data-stu-id="54ac4-114">**ProductEdition**</span></span>|<span data-ttu-id="54ac4-115">Répertorie l’édition, ainsi que les informations suivantes :</span><span class="sxs-lookup"><span data-stu-id="54ac4-115">Lists the edition, including:</span></span><br /><br /> <span data-ttu-id="54ac4-116">-Développeur</span><span class="sxs-lookup"><span data-stu-id="54ac4-116">-   Developer</span></span><br /><span data-ttu-id="54ac4-117">-Branche</span><span class="sxs-lookup"><span data-stu-id="54ac4-117">-   Branch</span></span><br /><span data-ttu-id="54ac4-118">-Standard</span><span class="sxs-lookup"><span data-stu-id="54ac4-118">-   Standard</span></span><br /><span data-ttu-id="54ac4-119">-Entreprise</span><span class="sxs-lookup"><span data-stu-id="54ac4-119">-   Enterprise</span></span>|  
    |<span data-ttu-id="54ac4-120">**Version de produit**</span><span class="sxs-lookup"><span data-stu-id="54ac4-120">**ProductVersion**</span></span>|<span data-ttu-id="54ac4-121">Répertorie la version de base.</span><span class="sxs-lookup"><span data-stu-id="54ac4-121">Lists the base product version.</span></span> <span data-ttu-id="54ac4-122">Pour la version de produit spécifique, y compris les service packs et mises à jour cumulatives, consultez [Versions BizTalk](http://social.technet.microsoft.com/wiki/contents/articles/7915.biztalk-versions.aspx).</span><span class="sxs-lookup"><span data-stu-id="54ac4-122">For specific product version, including service packs and cumulative updates, see [BizTalk Versions](http://social.technet.microsoft.com/wiki/contents/articles/7915.biztalk-versions.aspx).</span></span>|  

## <a name="use-the-control-panel"></a><span data-ttu-id="54ac4-123">Utilisez le panneau de configuration</span><span class="sxs-lookup"><span data-stu-id="54ac4-123">Use the control panel</span></span>

1.  <span data-ttu-id="54ac4-124">Sélectionnez **Démarrer**, type `Programs and Features`, puis ouvrez-le.</span><span class="sxs-lookup"><span data-stu-id="54ac4-124">Select **Start**, type `Programs and Features`, and then open it.</span></span>  

2. <span data-ttu-id="54ac4-125">Dans la liste, sélectionnez **Microsoft BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="54ac4-125">In the list, select **Microsoft BizTalk Server**.</span></span> <span data-ttu-id="54ac4-126">La version et l’édition sont répertoriées.</span><span class="sxs-lookup"><span data-stu-id="54ac4-126">The version and edition are listed.</span></span>

<span data-ttu-id="54ac4-127">Consultez [Versions BizTalk](http://social.technet.microsoft.com/wiki/contents/articles/7915.biztalk-versions.aspx).</span><span class="sxs-lookup"><span data-stu-id="54ac4-127">See [BizTalk Versions](http://social.technet.microsoft.com/wiki/contents/articles/7915.biztalk-versions.aspx).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="54ac4-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="54ac4-128">See Also</span></span>  
 [<span data-ttu-id="54ac4-129">Prise en main</span><span class="sxs-lookup"><span data-stu-id="54ac4-129">Get started</span></span>](../core/getting-started-with-biztalk-server.md)