---
title: "Comment modifier les paramètres de l’hôte | Documents Microsoft"
description: "Modifier les paramètres de l’hôte BizTalk dans l’Administration de BizTalk Server pour améliorer les performances et limitation"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0759b3a0-560e-4a11-92e6-9de0e15f463b
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 998c668bf787c9db260597c3a350e0e571492212
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="update-biztalk-host-settings"></a><span data-ttu-id="5f313-103">Mettre à jour les paramètres de l’hôte BizTalk</span><span class="sxs-lookup"><span data-stu-id="5f313-103">Update BizTalk host settings</span></span>

## <a name="overview"></a><span data-ttu-id="5f313-104">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="5f313-104">Overview</span></span>
<span data-ttu-id="5f313-105">Le panneau de configuration permet de modifier les informations de configuration d'un hôte donné à l'intérieur d'un groupe BizTalk.</span><span class="sxs-lookup"><span data-stu-id="5f313-105">Using the Settings Dashboard, you can modify the configuration information of a given host, across a BizTalk group.</span></span> <span data-ttu-id="5f313-106">Cette rubrique contient une procédure pas à pas permettant de modifier les paramètres de performance au niveau de l'hôte dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5f313-106">This topic provides the step-by-step procedure to modify the host-level performance settings in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5f313-107">Vous pouvez également modifier les paramètres d'instance du groupe et de l'hôte.</span><span class="sxs-lookup"><span data-stu-id="5f313-107">You can also modify the group and host instance settings.</span></span> <span data-ttu-id="5f313-108">Pour plus d’informations sur la façon de modifier les paramètres, consultez [à l’aide de paramètres de tableau de bord pour BizTalk Server Performance Tuning](../core/using-settings-dashboard-for-biztalk-server-performance-tuning.md).</span><span class="sxs-lookup"><span data-stu-id="5f313-108">For information about how to modify the settings, see [Using Settings Dashboard for BizTalk Server Performance Tuning](../core/using-settings-dashboard-for-biztalk-server-performance-tuning.md).</span></span>  
  
 <span data-ttu-id="5f313-109">Vous pouvez exporter les paramètres actuels de BizTalk Server dans un fichier XML.</span><span class="sxs-lookup"><span data-stu-id="5f313-109">The current BizTalk Server settings can be exported to an XML file.</span></span> <span data-ttu-id="5f313-110">Plus tard, vous pourrez les importer dans le panneau de configuration au lieu de configurer de nouvelles valeurs.</span><span class="sxs-lookup"><span data-stu-id="5f313-110">Later, you can import those settings to the Settings Dashboard instead of setting up new values.</span></span> <span data-ttu-id="5f313-111">Pour plus d’informations sur l’importation de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] paramètres, voir [importer ou exporter le panneau de configuration à l’aide de paramètres de BizTalk](how-to-import-biztalk-settings-using-settings-dashboard.md) et [importation ou exportation BizTalk paramètres à l’aide de BTSTask](how-to-import-biztalk-settings-using-btstask.md).</span><span class="sxs-lookup"><span data-stu-id="5f313-111">For information on importing the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] settings, see [Import or export BizTalk Settings Using Settings Dashboard](how-to-import-biztalk-settings-using-settings-dashboard.md) and [Import or export BizTalk Settings Using BTSTask](how-to-import-biztalk-settings-using-btstask.md).</span></span> 
  
## <a name="prerequisites"></a><span data-ttu-id="5f313-112">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="5f313-112">Prerequisites</span></span>  
 <span data-ttu-id="5f313-113">Pour effectuer cette opération, vous devez être connecté en tant que membre du groupe Administrateurs de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="5f313-113">To perform this operation, you must be signed in as a member of the BizTalk Server Administrators group.</span></span>  
  
## <a name="update-the-host-level-settings"></a><span data-ttu-id="5f313-114">Mettre à jour les paramètres au niveau de l’hôte</span><span class="sxs-lookup"><span data-stu-id="5f313-114">Update the host-level settings</span></span>  
  
1.  <span data-ttu-id="5f313-115">Dans le **Console d’Administration de BizTalk Server**, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], avec le bouton droit **groupe BizTalk**, puis cliquez sur **paramètres**.</span><span class="sxs-lookup"><span data-stu-id="5f313-115">In the **BizTalk Server Administration Console**, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], right-click **BizTalk Group**, and then click **Settings**.</span></span>  
  
2.  <span data-ttu-id="5f313-116">Dans le **Panneau de configuration BizTalk** boîte de dialogue le **hôtes** , effectuez une ou plusieurs des opérations suivantes.</span><span class="sxs-lookup"><span data-stu-id="5f313-116">In the **BizTalk Settings Dashboard** dialog box, on the **Hosts** page, do one or more of the following.</span></span>  
  
    -   <span data-ttu-id="5f313-117">Modifiez les paramètres de performances généraux de l'hôte BizTalk.</span><span class="sxs-lookup"><span data-stu-id="5f313-117">Modify the general performance settings of the BizTalk host.</span></span> <span data-ttu-id="5f313-118">Consultez [comment modifier les paramètres généraux](../core/how-to-modify-general-settings.md).</span><span class="sxs-lookup"><span data-stu-id="5f313-118">See [How to Modify General Settings](../core/how-to-modify-general-settings.md).</span></span>  
  
    -   <span data-ttu-id="5f313-119">Modifiez les paramètres de limitation basée sur la ressource de l'hôte BizTalk.</span><span class="sxs-lookup"><span data-stu-id="5f313-119">Modify the resource-based throttling settings of the BizTalk host.</span></span> <span data-ttu-id="5f313-120">Consultez [comment modifier la ressource en fonction de paramètres de limitation](../core/how-to-modify-resource-based-throttling-settings.md).</span><span class="sxs-lookup"><span data-stu-id="5f313-120">See [How to Modify Resource Based Throttling Settings](../core/how-to-modify-resource-based-throttling-settings.md).</span></span>  
  
    -   <span data-ttu-id="5f313-121">Modifier les paramètres de limitation basée sur la fréquence de l’hôte BizTalk.</span><span class="sxs-lookup"><span data-stu-id="5f313-121">Modify the rate-based throttling settings of the BizTalk host.</span></span> <span data-ttu-id="5f313-122">Consultez [comment modifier la fréquence en fonction de paramètres de limitation](../core/how-to-modify-rate-based-throttling-settings.md).</span><span class="sxs-lookup"><span data-stu-id="5f313-122">See [How to Modify Rate Based Throttling Settings](../core/how-to-modify-rate-based-throttling-settings.md).</span></span>  
  
    -   <span data-ttu-id="5f313-123">Modifiez les paramètres de limitation de l'orchestration de l'hôte BizTalk.</span><span class="sxs-lookup"><span data-stu-id="5f313-123">Modify the orchestration throttling settings of the BizTalk host.</span></span> <span data-ttu-id="5f313-124">Consultez [comment modifier les paramètres de limitation d’Orchestration](../core/how-to-modify-orchestration-throttling-settings.md).</span><span class="sxs-lookup"><span data-stu-id="5f313-124">See [How to Modify Orchestration Throttling Settings](../core/how-to-modify-orchestration-throttling-settings.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f313-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5f313-125">See Also</span></span>  
 [<span data-ttu-id="5f313-126">Utilisez le panneau de configuration de BizTalk Server réglage des performances</span><span class="sxs-lookup"><span data-stu-id="5f313-126">Use Settings Dashboard for BizTalk Server Performance Tuning</span></span>](../core/using-settings-dashboard-for-biztalk-server-performance-tuning.md)