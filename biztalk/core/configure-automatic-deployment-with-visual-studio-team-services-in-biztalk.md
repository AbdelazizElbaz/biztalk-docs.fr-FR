---
title: "Configurer le déploiement automatique avec Visual Studio Team Services | Documents Microsoft"
description: "Installer BizTalk Feature Pack pour utiliser la gestion du cycle de vie des applications avec VSTS à déployer vos applications dans différents environnements de BizTalk"
ms.custom: 
ms.date: 11/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 57f769bb-5105-43e2-9096-ed54cdf82b90
caps.latest.revision: "8"
author: tordgladnordahl
ms.author: mandia
manager: anneta
ms.openlocfilehash: 04a7d2b2430a5dc57403fc179fa1c1859d3a82b3
ms.sourcegitcommit: a0165ec2f1e8b58545638666b7bfa2bf440036fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="configure-automatic-deployment-with-visual-studio-team-services-in-biztalk-server"></a><span data-ttu-id="3f792-103">Configurer le déploiement automatique avec Visual Studio Team Services dans BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="3f792-103">Configure automatic deployment with Visual Studio Team Services in BizTalk Server</span></span>

## <a name="overview"></a><span data-ttu-id="3f792-104">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="3f792-104">Overview</span></span>

<span data-ttu-id="3f792-105">**En commençant par [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [!INCLUDE[featurepack1](../includes/featurepack1.md)]** , [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] fournit une expérience d’application lifecycle management (ALM) et un déploiement automatique amélioré.</span><span class="sxs-lookup"><span data-stu-id="3f792-105">**Starting with [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [!INCLUDE[featurepack1](../includes/featurepack1.md)]**, [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] provides an improved automatic deployment and application lifecycle management (ALM) experience.</span></span> 

<span data-ttu-id="3f792-106">À l’aide de Visual Studio Team Services, vous pouvez déployer automatiquement [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] applications pour différents environnements de BizTalk.</span><span class="sxs-lookup"><span data-stu-id="3f792-106">Using Visual Studio Team Services, you can automatically deploy [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] applications to different BizTalk environments.</span></span> 

<span data-ttu-id="3f792-107">En règle générale, il existe deux rôles impliqués :</span><span class="sxs-lookup"><span data-stu-id="3f792-107">Typically, there are two roles involved:</span></span>

- <span data-ttu-id="3f792-108">Développeur BizTalk crée l’application et il génère localement.</span><span class="sxs-lookup"><span data-stu-id="3f792-108">BizTalk developer creates the application, and builds it locally.</span></span> <span data-ttu-id="3f792-109">Vérifie ensuite l’application dans Git ou Team Foundation Version Control.</span><span class="sxs-lookup"><span data-stu-id="3f792-109">Then, checks the application into Git or Team Foundation Version Control.</span></span>
- <span data-ttu-id="3f792-110">VSTS admin crée les définitions de build et de mise en production et déploie l’application BizTalk vers d’autres environnements (développement, UAT, Production).</span><span class="sxs-lookup"><span data-stu-id="3f792-110">VSTS admin creates the build and release definitions, and deploys to the BizTalk application to different environments (Dev, UAT, Production).</span></span>

<span data-ttu-id="3f792-111">Si vous n’avez jamais utilisé VSTS, cette procédure pas à pas peut être difficile.</span><span class="sxs-lookup"><span data-stu-id="3f792-111">If you’ve never used VSTS, this walkthrough may be challenging.</span></span> <span data-ttu-id="3f792-112">Elle nécessite une compréhension des git, y compris le clonage et l’envoi des modifications.</span><span class="sxs-lookup"><span data-stu-id="3f792-112">It does require some understanding of git, including cloning, and pushing changes.</span></span> 

<span data-ttu-id="3f792-113">Nous vous montrons comment le programme d’installation de VSTS avec [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]et ajoutez votre première application à déployer.</span><span class="sxs-lookup"><span data-stu-id="3f792-113">We show you how to setup VSTS with [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)], and add your first application to deploy.</span></span> <span data-ttu-id="3f792-114">Nous vous recommandons de vous reporter à la [des conseils de VSTS](https://docs.microsoft.com/vsts/user-guide/), comme l’UI VSTS change.</span><span class="sxs-lookup"><span data-stu-id="3f792-114">We recommend you refer to the [VSTS guidance](https://docs.microsoft.com/vsts/user-guide/), as the VSTS UI changes.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="3f792-115">Avant de commencer</span><span class="sxs-lookup"><span data-stu-id="3f792-115">Before you begin</span></span>

* <span data-ttu-id="3f792-116">Vous devez Visual Studio Team Services (VSTS) prêt.</span><span class="sxs-lookup"><span data-stu-id="3f792-116">Have your Visual Studio Team Services (VSTS) account ready.</span></span> <span data-ttu-id="3f792-117">N’en avez pas ?</span><span class="sxs-lookup"><span data-stu-id="3f792-117">Don't have one?</span></span> <span data-ttu-id="3f792-118">[S’inscrire pour Visual Studio Team Services](https://www.visualstudio.com/docs/setup-admin/team-services/sign-up-for-visual-studio-team-services).</span><span class="sxs-lookup"><span data-stu-id="3f792-118">[Sign up for Visual Studio Team Services](https://www.visualstudio.com/docs/setup-admin/team-services/sign-up-for-visual-studio-team-services).</span></span>
* <span data-ttu-id="3f792-119">Si vous avez déjà un Agent VSTS est installé sur votre ordinateur BizTalk, l’agent existant est remplacé par le dernier Agent VSTS.</span><span class="sxs-lookup"><span data-stu-id="3f792-119">If you already have a VSTS Agent installed on your BizTalk computer, then the existing agent is overwritten with the latest VSTS Agent.</span></span> <span data-ttu-id="3f792-120">Vous devrez peut-être mettre à jour votre [service VSTS pour les aligner avec le nouvel agent](https://www.visualstudio.com/docs/build/actions/agents/v2-windows#replace-an-agent).</span><span class="sxs-lookup"><span data-stu-id="3f792-120">You may have to update your [VSTS service to align with the new agent](https://www.visualstudio.com/docs/build/actions/agents/v2-windows#replace-an-agent).</span></span>
* <span data-ttu-id="3f792-121">Déploiement automatique avec VSTS est effectué sur une [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] dans le groupe.</span><span class="sxs-lookup"><span data-stu-id="3f792-121">Automatic deployment with VSTS is done on one [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] in the group.</span></span> <span data-ttu-id="3f792-122">Assurez-vous que l’ordinateur dispose de Visual Studio et le [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] outils de développement et Kit de développement SDK.</span><span class="sxs-lookup"><span data-stu-id="3f792-122">Be sure the computer has Visual Studio and the [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] Developer Tools and SDK installed.</span></span> <span data-ttu-id="3f792-123">Consultez le [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] [matérielle et logicielle requise](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2016.md).</span><span class="sxs-lookup"><span data-stu-id="3f792-123">See the [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] [hardware and software requirements](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2016.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3f792-124">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="3f792-124">Prerequisites</span></span>

* <span data-ttu-id="3f792-125">Installer [Feature Pack 1](https://www.microsoft.com/download/details.aspx?id=55100) sur votre[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f792-125">Install [Feature Pack 1](https://www.microsoft.com/download/details.aspx?id=55100) on your [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]</span></span>
* <span data-ttu-id="3f792-126">Certains expérience et la base de connaissances avec la création et l’utilisation avec les définitions de VSTS.</span><span class="sxs-lookup"><span data-stu-id="3f792-126">Some experience and knowledge with creating and working with definitions in VSTS.</span></span> <span data-ttu-id="3f792-127">Si vous êtes débutant VSTS, il peut s’agir de bonnes ressources :</span><span class="sxs-lookup"><span data-stu-id="3f792-127">If you're brand new to VSTS, these may be good resources:</span></span> 

  [<span data-ttu-id="3f792-128">Vue d’ensemble de Visual Studio Team Services</span><span class="sxs-lookup"><span data-stu-id="3f792-128">Visual Studio Team Services overview</span></span>](https://www.visualstudio.com/docs/overview)  
  [<span data-ttu-id="3f792-129">L’élément de configuration/CD pour les internautes novices</span><span class="sxs-lookup"><span data-stu-id="3f792-129">CI/CD for newbies</span></span>](https://www.visualstudio.com/docs/build/get-started/ci-cd-part-1)

## <a name="get-started"></a><span data-ttu-id="3f792-130">Prise en main</span><span class="sxs-lookup"><span data-stu-id="3f792-130">Get started</span></span>
[<span data-ttu-id="3f792-131">Étape 1 : Ajouter un projet d’Application et mettre à jour le modèle de .json</span><span class="sxs-lookup"><span data-stu-id="3f792-131">Step 1: Add Application project & update .json template</span></span>](feature-pack-add-application-project.md)  

[<span data-ttu-id="3f792-132">Étape 2 : Créer le jeton VSTS & installer l’agent de build</span><span class="sxs-lookup"><span data-stu-id="3f792-132">Step 2: Create the VSTS token & install the build agent</span></span>](feature-pack-create-vsts-token.md)

[<span data-ttu-id="3f792-133">Étape 3 : Création de la build et définitions de version</span><span class="sxs-lookup"><span data-stu-id="3f792-133">Step 3: Create the build and release definitions</span></span>](feature-pack-add-build-release-definitions.md)

[<span data-ttu-id="3f792-134">Configurer les variables et les jetons de l’environnement</span><span class="sxs-lookup"><span data-stu-id="3f792-134">Configure environmental tokens and variables</span></span>](configure-environmental-tokens-and-variables-for-automatic-deployment.md)