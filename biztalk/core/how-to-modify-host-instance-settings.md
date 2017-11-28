---
title: "Mettre à jour les paramètres de l’Instance hôte | Documents Microsoft"
description: "Modifier les paramètres de l’instance d’hôte dans l’administrateur BizTalk Server"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2338255b-cc13-4f6a-86c3-9ecc666c43e5
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d85635f7f7a3b2cfe05abaf041cac07913b36f96
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="update-biztalk-host-instance-settings"></a><span data-ttu-id="3ed0a-103">Mettre à jour les paramètres de l’instance hôte BizTalk</span><span class="sxs-lookup"><span data-stu-id="3ed0a-103">Update BizTalk host instance settings</span></span>

## <a name="overview"></a><span data-ttu-id="3ed0a-104">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="3ed0a-104">Overview</span></span>
<span data-ttu-id="3ed0a-105">Le [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)] permet de modifier les informations de configuration d'un hôte donné à l'intérieur d'un groupe BizTalk.</span><span class="sxs-lookup"><span data-stu-id="3ed0a-105">Using the [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)], you can modify the configuration information of a given host instance, across a BizTalk group.</span></span> <span data-ttu-id="3ed0a-106">Cette rubrique contient une procédure pas à pas permettant de modifier les paramètres de performance au niveau de l'instance de l'hôte dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3ed0a-106">This topic provides the step-by-step procedure to modify the host instance level performance settings in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
 <span data-ttu-id="3ed0a-107">Les paramètres BizTalk (provenant d'un environnement source) sont souvent enregistrés au format XML.</span><span class="sxs-lookup"><span data-stu-id="3ed0a-107">Often you have the BizTalk settings (from a source environment) saved as an XML file.</span></span> <span data-ttu-id="3ed0a-108">Un fichier XML contient des informations permettant de répliquer les paramètres sur l'ordinateur cible.</span><span class="sxs-lookup"><span data-stu-id="3ed0a-108">The XML file contains information that allows you to replicate the settings on the target machine.</span></span> <span data-ttu-id="3ed0a-109">Vous pouvez importer ces paramètres dans le Panneau de configuration, plutôt que de configurer de nouvelles valeurs.</span><span class="sxs-lookup"><span data-stu-id="3ed0a-109">You can import those settings to Settings Dashboard, instead of setting up new values.</span></span> <span data-ttu-id="3ed0a-110">De même, après avoir configuré des nouvelles valeurs pour [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], vous pouvez les exporter dans un fichier XML pour les utiliser sur un autre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="3ed0a-110">On the other hand, after setting up new values for [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], you can export them to an XML file to be used in another machine.</span></span>  
  
 <span data-ttu-id="3ed0a-111">Pour plus d’informations sur l’importation de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] paramètres, voir [importer ou exporter le panneau de configuration à l’aide de paramètres de BizTalk](how-to-import-biztalk-settings-using-settings-dashboard.md) et [importation ou exportation BizTalk paramètres à l’aide de BTSTask](how-to-import-biztalk-settings-using-btstask.md).</span><span class="sxs-lookup"><span data-stu-id="3ed0a-111">For information on importing the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] settings, see [Import or export BizTalk Settings Using Settings Dashboard](how-to-import-biztalk-settings-using-settings-dashboard.md) and [Import or export BizTalk Settings Using BTSTask](how-to-import-biztalk-settings-using-btstask.md).</span></span> 
  
## <a name="prerequisites"></a><span data-ttu-id="3ed0a-112">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="3ed0a-112">Prerequisites</span></span>  
 <span data-ttu-id="3ed0a-113">Pour effectuer cette opération, vous devez être connecté en tant que membre du groupe Administrateurs de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="3ed0a-113">To perform this operation, you must be signed in as a member of the BizTalk Server Administrators group.</span></span>  
  
## <a name="update-the-host-instance-level-settings"></a><span data-ttu-id="3ed0a-114">Mettre à jour les paramètres de niveau d’instance hôte</span><span class="sxs-lookup"><span data-stu-id="3ed0a-114">Update the host instance level settings</span></span>  
  
1.  <span data-ttu-id="3ed0a-115">Dans le **Console d’Administration de BizTalk Server**, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], avec le bouton droit **groupe BizTalk**, puis cliquez sur **paramètres**.</span><span class="sxs-lookup"><span data-stu-id="3ed0a-115">In the **BizTalk Server Administration Console**, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], right-click **BizTalk Group**, and then click **Settings**.</span></span>  
  
2.  <span data-ttu-id="3ed0a-116">Dans le **Panneau de configuration BizTalk** boîte de dialogue le **Instances d’hôte** onglet, effectuez l’une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="3ed0a-116">In the **BizTalk Settings Dashboard** dialog box, on the **Host Instances** tab, do any of the following:</span></span>  
  
    -   <span data-ttu-id="3ed0a-117">Modifiez les paramètres .NET CLR d'une instance d'hôte.</span><span class="sxs-lookup"><span data-stu-id="3ed0a-117">Modify the .NET CLR settings for a host instance.</span></span> <span data-ttu-id="3ed0a-118">Consultez [modifier les paramètres de CLR .NET](../core/how-to-modify-net-clr-settings.md).</span><span class="sxs-lookup"><span data-stu-id="3ed0a-118">See [Change the .NET CLR Settings](../core/how-to-modify-net-clr-settings.md).</span></span>  
  
    -   <span data-ttu-id="3ed0a-119">Modifiez les paramètres de limitation de mémoire de l'orchestration.</span><span class="sxs-lookup"><span data-stu-id="3ed0a-119">Modify the orchestration memory throttling settings.</span></span> <span data-ttu-id="3ed0a-120">Consultez [modifier la paramètres de limitation de mémoire d’Orchestration](../core/how-to-modify-orchestration-memory-throttling-settings.md).</span><span class="sxs-lookup"><span data-stu-id="3ed0a-120">See [Change the Orchestration Memory Throttling Settings](../core/how-to-modify-orchestration-memory-throttling-settings.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ed0a-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3ed0a-121">See Also</span></span>  
 [<span data-ttu-id="3ed0a-122">Utilisez le panneau de configuration de BizTalk Server réglage des performances</span><span class="sxs-lookup"><span data-stu-id="3ed0a-122">Use Settings Dashboard for BizTalk Server Performance Tuning</span></span>](../core/using-settings-dashboard-for-biztalk-server-performance-tuning.md)