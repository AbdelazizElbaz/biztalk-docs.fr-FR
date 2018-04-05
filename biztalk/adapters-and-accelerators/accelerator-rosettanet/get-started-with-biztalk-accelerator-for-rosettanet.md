---
title: Prise en main de BizTalk Accelerator pour RosettaNet | Documents Microsoft
description: Consultez les didacticiels disponibles pour aider à en savoir plus et prise en main l’accélérateur RosettaNet (BTARN) dans BizTalk Server
caps.latest.revision: 7
author: MandiOhlinger
manager: anneta
ms.custom: ''
ms.date: 08/09/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- btarn.configuration.introduction
ms.assetid: 28a8942c-b461-4b2f-bc1f-1fc22cd08882
ms.author: mandia
ms.openlocfilehash: 156153010a4ee9caa5cb02535d516e05e49a21fa
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="get-started-with-biztalk-accelerator-for-rosettanet"></a><span data-ttu-id="19482-103">Prise en main de BizTalk Accelerator pour RosettaNet</span><span class="sxs-lookup"><span data-stu-id="19482-103">Get started with BizTalk Accelerator for RosettaNet</span></span>
<span data-ttu-id="19482-104">Microsoft BizTalk Accelerator pour RosettaNet (BTARN) simplifie le développement et le déploiement de solutions d’intégration basée sur les normes RosettaNet.</span><span class="sxs-lookup"><span data-stu-id="19482-104">The Microsoft BizTalk Accelerator for RosettaNet (BTARN) streamlines the development and deployment of RosettaNet standards-based integration solutions.</span></span> [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]<span data-ttu-id="19482-105">prend en charge les versions 1.1 et 2.0.01 du Framework RNIF (RosettaNet Implementation).</span><span class="sxs-lookup"><span data-stu-id="19482-105"> supports the RosettaNet Implementation Framework (RNIF) versions 1.1 and 2.0.01.</span></span> <span data-ttu-id="19482-106">RNIF est une infrastructure d’application réseau ouverte qui permet à des partenaires commerciaux exécuter de façon collaborative RosettaNet PIP (PIP).</span><span class="sxs-lookup"><span data-stu-id="19482-106">RNIF is an open network application framework that enables business partners to collaboratively run RosettaNet Partner Interface Processes (PIPs).</span></span> <span data-ttu-id="19482-107">Consultez [GS1 nous](http://go.microsoft.com/fwlink/?LinkID=33859) pour plus d’informations sur standard RosettaNet.</span><span class="sxs-lookup"><span data-stu-id="19482-107">See [GS1 US](http://go.microsoft.com/fwlink/?LinkID=33859) for more information about RosettaNet standard.</span></span>
  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]<span data-ttu-id="19482-108">prend également en charge l’échange de l’échange de données chimiques (CHEMICAL) normes Chem.</span><span class="sxs-lookup"><span data-stu-id="19482-108"> also supports the exchange of Chemical Data Exchange (CIDX) Chem eStandards.</span></span>  
  
<span data-ttu-id="19482-109">Cette section fournit des informations spécifiques au rôle sur la façon dont vous pouvez utiliser BizTalk Server et l’accélérateur RosettaNet dans votre entreprise pour l’intégration d’application d’entreprise (IAE) et entre les partenaires commerciaux pour automatiser l’approvisionnement de l’entreprise-entreprise solutions.</span><span class="sxs-lookup"><span data-stu-id="19482-109">This section provides role-specific information about how you can use BizTalk Server and the RosettaNet accelerator in your company for enterprise application integration (EAI), and among business partners to automate business-to-business procurement solutions.</span></span>  

## <a name="loopback-tutorial"></a><span data-ttu-id="19482-110">Didacticiel de bouclage</span><span class="sxs-lookup"><span data-stu-id="19482-110">Loopback tutorial</span></span>

<span data-ttu-id="19482-111">Inclut les étapes détaillées qui expliquent comment utiliser l’accélérateur RosettaNet pour simuler une implémentation de processus entre l’organisation d’accueil et partenaire sur un seul ordinateur.</span><span class="sxs-lookup"><span data-stu-id="19482-111">Includes detailed steps that describe how to use the RosettaNet accelerator to simulate a process implementation between the home and partner organization on a single computer.</span></span>

<span data-ttu-id="19482-112">Dans ce didacticiel, vous créez une organisation d’origine, une organisation partenaire, un accord commercial, utilisez l’utilitaire de bouclage pour créer un accord de mise en miroir, puis exécutez un exemple de processus pour vérifier que le scénario de bouclage.</span><span class="sxs-lookup"><span data-stu-id="19482-112">In this tutorial, you create a home organization, a partner organization, a trade agreement, use the Loopback utility to create a mirror agreement, and then run a sample process to verify the loop-back scenario.</span></span>

<span data-ttu-id="19482-113">Accédez à [didacticiel bouclage](loopback-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="19482-113">Go to [Loopback tutorial](loopback-tutorial.md).</span></span> 

## <a name="double-action-tutorial"></a><span data-ttu-id="19482-114">Didacticiel double action</span><span class="sxs-lookup"><span data-stu-id="19482-114">Double action tutorial</span></span>

<span data-ttu-id="19482-115">Une solution de bout en bout à l’aide de l’accélérateur RosettaNet.</span><span class="sxs-lookup"><span data-stu-id="19482-115">An end-to-end solution using the RosettaNet accelerator.</span></span> <span data-ttu-id="19482-116">Ce didacticiel décrit les étapes pour implémenter une solution compatible avec RosettaNet en créant un scénario de partenaire commercial entre deux entreprises fictives : Contoso, l’organisation du fournisseur et Fabrikam, l’organisation de l’acheteur.</span><span class="sxs-lookup"><span data-stu-id="19482-116">The tutorial details the steps to implement a RosettaNet-compliant solution by creating a trading partner scenario between two fictitious companies: Contoso, the supplier organization, and Fabrikam, the buyer organization.</span></span>

<span data-ttu-id="19482-117">Il inclut l’utilisation de la Console de gestion BTARN, créer des applications line-of-business (LOB) et créer des orchestrations personnalisées.</span><span class="sxs-lookup"><span data-stu-id="19482-117">It includes working with the BTARN Management Console, creating line-of-business (LOB) applications, and creating custom orchestrations.</span></span>

<span data-ttu-id="19482-118">Accédez à [didacticiel Double action](double-action-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="19482-118">Go to [Double action tutorial](double-action-tutorial.md).</span></span> 


## <a name="private-process-tutorial"></a><span data-ttu-id="19482-119">Didacticiel de processus privé</span><span class="sxs-lookup"><span data-stu-id="19482-119">Private process tutorial</span></span>
<span data-ttu-id="19482-120">Une solution de bout en bout à l’aide de l’accélérateur RosettaNet.</span><span class="sxs-lookup"><span data-stu-id="19482-120">An end-to-end solution using the RosettaNet accelerator.</span></span> <span data-ttu-id="19482-121">Ce didacticiel décrit les étapes pour implémenter une solution compatible avec RosettaNet en créant un scénario commercial entre deux entreprises fictives : Contoso, l’organisation du fournisseur et Fabrikam, l’organisation de l’acheteur.</span><span class="sxs-lookup"><span data-stu-id="19482-121">The tutorial details the steps to implement a RosettaNet-compliant solution by creating a trading scenario between two fictitious companies: Contoso, the supplier organization, and Fabrikam, the buyer organization.</span></span>

<span data-ttu-id="19482-122">Il décrit divers aspects de la création d’une solution RosettaNet, notamment l’intégration ERP, application de la stratégie, personnalisation de processus privé et promouvoir une communication sécurisée.</span><span class="sxs-lookup"><span data-stu-id="19482-122">It outlines various aspects of creating a RosettaNet-based solution, including ERP integration, business policy enforcement, private process customization, and promoting secure communication.</span></span>

<span data-ttu-id="19482-123">Accédez à [didacticiel de processus privé](private-process-tutorial.md)</span><span class="sxs-lookup"><span data-stu-id="19482-123">Go to [Private process tutorial](private-process-tutorial.md)</span></span>


## <a name="tutorial-links"></a><span data-ttu-id="19482-124">Liens de didacticiels</span><span class="sxs-lookup"><span data-stu-id="19482-124">Tutorial Links</span></span>
[<span data-ttu-id="19482-125">Didacticiel de bouclage</span><span class="sxs-lookup"><span data-stu-id="19482-125">Loopback tutorial</span></span>](loopback-tutorial.md)  
[<span data-ttu-id="19482-126">Didacticiel double action</span><span class="sxs-lookup"><span data-stu-id="19482-126">Double action tutorial</span></span>](double-action-tutorial.md)  
[<span data-ttu-id="19482-127">Didacticiel de processus privé</span><span class="sxs-lookup"><span data-stu-id="19482-127">Private process tutorial</span></span>](private-process-tutorial.md)

## <a name="see-also"></a><span data-ttu-id="19482-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="19482-128">See also</span></span>
[<span data-ttu-id="19482-129">Accessibilité des personnes handicapées</span><span class="sxs-lookup"><span data-stu-id="19482-129">Accessibility for People with Disabilities</span></span>](accessibility-for-people-with-disabilities3.md)