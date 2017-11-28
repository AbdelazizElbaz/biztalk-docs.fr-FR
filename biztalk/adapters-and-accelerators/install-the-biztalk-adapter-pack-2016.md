---
title: Installer BizTalk Adapter Pack 2016 | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 23c74470-6336-49be-95c3-32b5c279e0ab
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fec17ce2da0183b9029839d3054261c5db3952a2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="install-the-biztalk-adapter-pack-2016"></a><span data-ttu-id="db275-102">Installer BizTalk Adapter Pack 2016</span><span class="sxs-lookup"><span data-stu-id="db275-102">Install the BizTalk Adapter Pack 2016</span></span>
## <a name="overview"></a><span data-ttu-id="db275-103">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="db275-103">Overview</span></span>

<span data-ttu-id="db275-104">Le [!INCLUDE[adapterpacknoversion_md](../includes/adapterpacknoversion-md.md)] (LOB) est inclus avec [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="db275-104">The [!INCLUDE[adapterpacknoversion_md](../includes/adapterpacknoversion-md.md)] (BAP) is included with [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="db275-105">Par conséquent, lorsque vous téléchargez [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)], vous téléchargez également les adaptateurs dans le [!INCLUDE[adapterpacknoversion_md](../includes/adapterpacknoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="db275-105">So when you download [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)], you are also downloading the adapters in the [!INCLUDE[adapterpacknoversion_md](../includes/adapterpacknoversion-md.md)].</span></span> 

<span data-ttu-id="db275-106">Le [!INCLUDE[adapterpacknoversion_md](../includes/adapterpacknoversion-md.md)] utilise le [!INCLUDE[firstref_btsWinCommFoundation_md](../includes/firstref-btswincommfoundation-md.md)] pour communiquer avec les différents systèmes de line-of-business (LOB).</span><span class="sxs-lookup"><span data-stu-id="db275-106">The [!INCLUDE[adapterpacknoversion_md](../includes/adapterpacknoversion-md.md)] uses the [!INCLUDE[firstref_btsWinCommFoundation_md](../includes/firstref-btswincommfoundation-md.md)] to communicate with different enterprise line-of-business (LOB) systems.</span></span> <span data-ttu-id="db275-107">Le [!INCLUDE[adapterpacknoversion_md](../includes/adapterpacknoversion-md.md)] a son propre ensemble d’exigences, de sa propre expérience d’installation et de ses propres étapes d’installation.</span><span class="sxs-lookup"><span data-stu-id="db275-107">The [!INCLUDE[adapterpacknoversion_md](../includes/adapterpacknoversion-md.md)] has its own set of requirements, its own setup experience, and its own installation steps.</span></span> 

<span data-ttu-id="db275-108">Le [!INCLUDE[adapterpacknoversion_md](../includes/adapterpacknoversion-md.md)] est facultatif et est uniquement nécessaire si vous souhaitez [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] pour envoyer ou recevoir des messages à un des systèmes métier de l’entreprise suivantes :</span><span class="sxs-lookup"><span data-stu-id="db275-108">The [!INCLUDE[adapterpacknoversion_md](../includes/adapterpacknoversion-md.md)] is optional, and is only needed if you want [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] to send or receive messages to any of the following enterprise LOB systems:</span></span> 

* <span data-ttu-id="db275-109">Base de données Oracle</span><span class="sxs-lookup"><span data-stu-id="db275-109">Oracle Database</span></span>
* <span data-ttu-id="db275-110">Oracle E-Business Suite (EBS)</span><span class="sxs-lookup"><span data-stu-id="db275-110">Oracle E-Business Suite (EBS)</span></span>
* <span data-ttu-id="db275-111">SAP</span><span class="sxs-lookup"><span data-stu-id="db275-111">SAP</span></span>
* <span data-ttu-id="db275-112">SQL Server</span><span class="sxs-lookup"><span data-stu-id="db275-112">SQL Server</span></span>
* <span data-ttu-id="db275-113">Siebel</span><span class="sxs-lookup"><span data-stu-id="db275-113">Siebel</span></span>

<span data-ttu-id="db275-114">Chaque version de [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] inclut ses propres [!INCLUDE[adapterpacknoversion_md](../includes/adapterpacknoversion-md.md)] version.</span><span class="sxs-lookup"><span data-stu-id="db275-114">Every version of [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] includes its own [!INCLUDE[adapterpacknoversion_md](../includes/adapterpacknoversion-md.md)] version.</span></span> <span data-ttu-id="db275-115">Seule la version fournie avec votre [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] est prise en charge.</span><span class="sxs-lookup"><span data-stu-id="db275-115">Only the version included with your [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] version is supported.</span></span> <span data-ttu-id="db275-116">Ils ne sont pas compatibles.</span><span class="sxs-lookup"><span data-stu-id="db275-116">They are not backward-compatible.</span></span>

<span data-ttu-id="db275-117">Ce document répertorie la configuration logicielle requise et les étapes pour installer le Microsoft BizTalk adaptateur Pack (LOB) inclus avec [!INCLUDE[bts2016_md](../includes/bts2016-md.md)].</span><span class="sxs-lookup"><span data-stu-id="db275-117">This document lists the software requirements, and the steps to install the Microsoft BizTalk Adapter Pack (BAP) included with [!INCLUDE[bts2016_md](../includes/bts2016-md.md)].</span></span> 

## <a name="get-started-here"></a><span data-ttu-id="db275-118">Commencez ici</span><span class="sxs-lookup"><span data-stu-id="db275-118">Get started here</span></span>
[<span data-ttu-id="db275-119">Configuration logicielle requise</span><span class="sxs-lookup"><span data-stu-id="db275-119">Software prerequisites</span></span>](../adapters-and-accelerators/software-prerequisites-for-biztalk-adapter-pack-2016.md)  
[<span data-ttu-id="db275-120">Étapes d’installation</span><span class="sxs-lookup"><span data-stu-id="db275-120">Install steps</span></span>](../adapters-and-accelerators/installing-the-biztalk-adapter-pack-2016.md)  
[<span data-ttu-id="db275-121">Valider les étapes d’installation</span><span class="sxs-lookup"><span data-stu-id="db275-121">Post installation steps</span></span>](../adapters-and-accelerators/post-installation-steps-for-biztalk-adapter-pack-2016.md)  
[<span data-ttu-id="db275-122">Mettre à jour ou désinstaller</span><span class="sxs-lookup"><span data-stu-id="db275-122">Update or uninstall</span></span>](../adapters-and-accelerators/update-or-uninstall-the-biztalk-adapter-pack-2016.md)