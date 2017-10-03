---
title: Didacticiel de bouclage | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- loopbacks, tutorial
- loopback tutorial, about the loopback tutorial
- loopback tutorial
- tutorials, loopback tutorial
ms.assetid: 0f69c1f1-4039-4949-8eed-127ceabbc3cc
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b3b013eb65320dc36dd1319d7332e45ed54b2444
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="loopback-tutorial"></a><span data-ttu-id="1c117-102">Didacticiel de bouclage</span><span class="sxs-lookup"><span data-stu-id="1c117-102">Loopback Tutorial</span></span>
<span data-ttu-id="1c117-103">Ce didacticiel contient des procédures détaillées qui décrivent comment vous pouvez utiliser [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] pour simuler une implémentation de processus entre l’organisation d’accueil et partenaire sur un seul ordinateur.</span><span class="sxs-lookup"><span data-stu-id="1c117-103">This tutorial contains detailed steps that describe how you can use [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] to simulate a process implementation between the home and partner organization on a single computer.</span></span>  
  
 <span data-ttu-id="1c117-104">Dans un environnement de production réel, l’implémentation de votre organisation partenaire réside sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="1c117-104">In a real production environment, your partner organization implementation resides on a remote computer.</span></span> <span data-ttu-id="1c117-105">Ce didacticiel utilise l’utilitaire de bouclage pour créer un miroir commerciaux d’accord pour simuler le partenaire commercial sur le même ordinateur.</span><span class="sxs-lookup"><span data-stu-id="1c117-105">This tutorial uses the Loopback utility to create a mirror trading agreement to simulate the trading partner on the same computer.</span></span> <span data-ttu-id="1c117-106">À l’aide d’un scénario de bouclage seul ordinateur fonctionne pour à des fins de développement et de test.</span><span class="sxs-lookup"><span data-stu-id="1c117-106">Using a single computer loop-back scenario works for development and test purposes.</span></span> <span data-ttu-id="1c117-107">Il est recommandé que vous n’utilisez ne pas l’utilitaire de bouclage dans un environnement de production.</span><span class="sxs-lookup"><span data-stu-id="1c117-107">It is recommended that you do not to use the Loopback utility in a production environment.</span></span>  
  
 <span data-ttu-id="1c117-108">Ce scénario de bouclage ne prend pas en charge la signature des messages et donc ne prend pas en charge non répudiation.</span><span class="sxs-lookup"><span data-stu-id="1c117-108">This loopback scenario does not support signing messages, and thus does not support non-repudiation.</span></span>  
  
 <span data-ttu-id="1c117-109">Ce scénario prend en charge le chiffrement des messages si vous avez configurée une autorité de certification, et que vous avez une clé privée pour le chiffrement disponible à des fins de test.</span><span class="sxs-lookup"><span data-stu-id="1c117-109">This scenario supports encryption of messages if you have a certification authority configured, and you have a private key for encryption available for test purposes.</span></span>  
  
 <span data-ttu-id="1c117-110">Dans ce didacticiel, vous créez une organisation d’origine, une organisation partenaire, un accord commercial, utilisez l’utilitaire de bouclage pour créer un accord de mise en miroir, puis exécutez un exemple de processus pour vérifier que le scénario de bouclage.</span><span class="sxs-lookup"><span data-stu-id="1c117-110">In this tutorial, you create a home organization, a partner organization, a trade agreement, use the Loopback utility to create a mirror agreement, and then run a sample process to verify the loop-back scenario.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1c117-111">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="1c117-111">In This Section</span></span>  
  
-   [<span data-ttu-id="1c117-112">Préparation pour le didacticiel</span><span class="sxs-lookup"><span data-stu-id="1c117-112">Preparing for the Tutorial</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/preparing-for-the-tutorial.md)  
  
-   [<span data-ttu-id="1c117-113">Étape 1 : Créer l’organisation d’origine</span><span class="sxs-lookup"><span data-stu-id="1c117-113">Step 1: Create the Home Organization</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-1-create-the-home-organization.md)  
  
-   [<span data-ttu-id="1c117-114">Étape 2 : Créer l’organisation du partenaire</span><span class="sxs-lookup"><span data-stu-id="1c117-114">Step 2: Create the Partner Organization</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-2-create-the-partner-organization.md)  
  
-   [<span data-ttu-id="1c117-115">Étape 3 : Modifier le Partner Interface Process</span><span class="sxs-lookup"><span data-stu-id="1c117-115">Step 3: Edit the Partner Interface Process</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-3-edit-the-partner-interface-process.md)  
  
-   [<span data-ttu-id="1c117-116">Étape 4 : Créer un accord commercial</span><span class="sxs-lookup"><span data-stu-id="1c117-116">Step 4: Create a Trade Agreement</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-4-create-a-trade-agreement.md)  
  
-   [<span data-ttu-id="1c117-117">Étape 5 : Créer un accord de mise en miroir</span><span class="sxs-lookup"><span data-stu-id="1c117-117">Step 5: Create a Mirror Agreement</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-5-create-a-mirror-agreement.md)  
  
-   [<span data-ttu-id="1c117-118">Étape 6 : Démarrer des Orchestrations</span><span class="sxs-lookup"><span data-stu-id="1c117-118">Step 6: Start Orchestrations</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-6-start-orchestrations.md)  
  
-   [<span data-ttu-id="1c117-119">Étape 7 : Créer un exemple de Message LOB</span><span class="sxs-lookup"><span data-stu-id="1c117-119">Step 7: Create a Sample LOB Message</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-7-create-a-sample-lob-message.md)  
  
-   [<span data-ttu-id="1c117-120">Étape 8 : Afficher les Messages dans les bases de données BTARN</span><span class="sxs-lookup"><span data-stu-id="1c117-120">Step 8: View Messages in the BTARN Databases</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-8-view-messages-in-the-btarn-databases.md)