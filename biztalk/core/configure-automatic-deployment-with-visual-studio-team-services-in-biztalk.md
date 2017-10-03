---
title: "Configurer le déploiement automatique avec Visual Studio Team Services dans BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 57f769bb-5105-43e2-9096-ed54cdf82b90
caps.latest.revision: "8"
author: tordgladnordahl
ms.author: tonordah
manager: anneta
ms.openlocfilehash: 23d79eae3bd89a572a919cfeff800178f9163796
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configure-automatic-deployment-with-visual-studio-team-services-in-biztalk-server"></a><span data-ttu-id="3306c-102">Configurer le déploiement automatique avec Visual Studio Team Services dans BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="3306c-102">Configure automatic deployment with Visual Studio Team Services in BizTalk Server</span></span>
<span data-ttu-id="3306c-103">Déployer automatiquement [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] applications à l’aide de Visual Studio Team Services.</span><span class="sxs-lookup"><span data-stu-id="3306c-103">Automatically deploy [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] applications using Visual Studio Team Services.</span></span> 

<span data-ttu-id="3306c-104">**En commençant par [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [!INCLUDE[featurepack1](../includes/featurepack1.md)]** , [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] fournit une expérience d’application lifecycle management (ALM) et un déploiement automatique amélioré.</span><span class="sxs-lookup"><span data-stu-id="3306c-104">**Starting with [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [!INCLUDE[featurepack1](../includes/featurepack1.md)]**, [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] provides an improved automatic deployment and application lifecycle management (ALM) experience.</span></span> 

<span data-ttu-id="3306c-105">Cette section vous montre comment le programme d’installation de VSTS avec [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]et ajoutez votre première application à déployer.</span><span class="sxs-lookup"><span data-stu-id="3306c-105">This section shows you how to setup VSTS with [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)], and add your first application to deploy.</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="3306c-106">Avant de commencer</span><span class="sxs-lookup"><span data-stu-id="3306c-106">Before you begin</span></span>

* <span data-ttu-id="3306c-107">Vous devez Visual Studio Team Services (VSTS) prêt.</span><span class="sxs-lookup"><span data-stu-id="3306c-107">Have your Visual Studio Team Services (VSTS) account ready.</span></span> <span data-ttu-id="3306c-108">N’en avez pas ?</span><span class="sxs-lookup"><span data-stu-id="3306c-108">Don't have one?</span></span> <span data-ttu-id="3306c-109">[S’inscrire pour Visual Studio Team Services](https://www.visualstudio.com/docs/setup-admin/team-services/sign-up-for-visual-studio-team-services).</span><span class="sxs-lookup"><span data-stu-id="3306c-109">[Sign up for Visual Studio Team Services](https://www.visualstudio.com/docs/setup-admin/team-services/sign-up-for-visual-studio-team-services).</span></span>
* <span data-ttu-id="3306c-110">Si vous avez déjà un Agent VSTS est installé sur votre ordinateur BizTalk, l’agent existant est remplacé par le dernier Agent VSTS.</span><span class="sxs-lookup"><span data-stu-id="3306c-110">If you already have a VSTS Agent installed on your BizTalk computer, then the existing agent is overwritten with the latest VSTS Agent.</span></span> <span data-ttu-id="3306c-111">Vous devrez peut-être mettre à jour votre [service VSTS pour les aligner avec le nouvel agent](https://www.visualstudio.com/docs/build/actions/agents/v2-windows#replace-an-agent).</span><span class="sxs-lookup"><span data-stu-id="3306c-111">You may have to update your [VSTS service to align with the new agent](https://www.visualstudio.com/docs/build/actions/agents/v2-windows#replace-an-agent).</span></span>
* <span data-ttu-id="3306c-112">Déploiement automatique avec VSTS est effectué sur une [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] dans le groupe.</span><span class="sxs-lookup"><span data-stu-id="3306c-112">Automatic deployment with VSTS is done on one [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] in the group.</span></span> <span data-ttu-id="3306c-113">Assurez-vous que l’ordinateur dispose de Visual Studio et le [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] outils de développement et Kit de développement SDK.</span><span class="sxs-lookup"><span data-stu-id="3306c-113">Be sure the computer has Visual Studio and the [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] Developer Tools and SDK installed.</span></span> <span data-ttu-id="3306c-114">Consultez le [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] [matérielle et logicielle requise](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2016.md).</span><span class="sxs-lookup"><span data-stu-id="3306c-114">See the [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] [hardware and software requirements](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2016.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="3306c-115">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="3306c-115">Next steps</span></span>
[<span data-ttu-id="3306c-116">Configurer VSTS pour le déploiement automatique</span><span class="sxs-lookup"><span data-stu-id="3306c-116">Configure VSTS for automatic deployment</span></span>](../core/configure-visual-studio-team-services-to-deploy-biztalk-solutions-or-projects.md)

[<span data-ttu-id="3306c-117">Configurer le modèle JSON</span><span class="sxs-lookup"><span data-stu-id="3306c-117">Configure the JSON template</span></span>](../core/configure-the-json-template-for-automatic-deployment.md)

[<span data-ttu-id="3306c-118">Configurer les variables et les jetons de l’environnement</span><span class="sxs-lookup"><span data-stu-id="3306c-118">Configure environmental tokens and variables</span></span>](../core/configure-environmental-tokens-and-variables-for-automatic-deployment.md)

[<span data-ttu-id="3306c-119">Ajouter une application BizTalk dans VSTS</span><span class="sxs-lookup"><span data-stu-id="3306c-119">Add a BizTalk application to VSTS</span></span>](../core/add-a-biztalk-server-application-to-visual-studio-team-services.md)