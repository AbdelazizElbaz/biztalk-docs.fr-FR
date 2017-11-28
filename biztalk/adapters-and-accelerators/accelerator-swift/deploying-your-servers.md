---
title: "Déploiement de vos serveurs | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deploying, servers
- servers, deploying
ms.assetid: 6036e42b-59b8-4092-addd-288e9c4b91d6
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f0c158e3c14a5a695e7c1e042cd3dfb0277260b7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="deploying-your-servers"></a><span data-ttu-id="7b9c1-102">Déploiement de vos serveurs</span><span class="sxs-lookup"><span data-stu-id="7b9c1-102">Deploying Your Servers</span></span>
<span data-ttu-id="7b9c1-103">Cette section fournit des instructions de configuration de chacun des serveurs dans votre [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] déploiement.</span><span class="sxs-lookup"><span data-stu-id="7b9c1-103">This section provides instructions for configuring each of the servers in your [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] deployment.</span></span> <span data-ttu-id="7b9c1-104">Après avoir configuré le réseau que vous déployez le logiciel sur chaque serveur à l’aide de la procédure suivante.</span><span class="sxs-lookup"><span data-stu-id="7b9c1-104">After you configure the network you deploy the software on each server by using the following steps.</span></span>  
  
 <span data-ttu-id="7b9c1-105">Avant de commencer le déploiement de serveurs, assurez-vous que lire et effectuer les étapes décrites dans la préparation au déploiement [préparation au déploiement](../../adapters-and-accelerators/accelerator-swift/preparing-for-deployment.md).</span><span class="sxs-lookup"><span data-stu-id="7b9c1-105">Before starting server deployment, make sure that you read and perform the deployment preparation steps described in [Preparing for Deployment](../../adapters-and-accelerators/accelerator-swift/preparing-for-deployment.md).</span></span> <span data-ttu-id="7b9c1-106">Ne parvient pas à respecter les recommandations de la section précédente peuvent entraîner une configuration non pris en charge et inconnue du déploiement (et les étapes suivantes peuvent échouer).</span><span class="sxs-lookup"><span data-stu-id="7b9c1-106">Failing to adhere to the prescriptive guidance in the previous section might result in an unknown and unsupported configuration of the deployment (and subsequent steps might fail).</span></span>  
  
 <span data-ttu-id="7b9c1-107">Pour plus d’informations, consultez le [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] Guide de déploiement.</span><span class="sxs-lookup"><span data-stu-id="7b9c1-107">For more information, see the [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] Deployment Guide.</span></span>  
  
 <span data-ttu-id="7b9c1-108">Contenu de cette section :</span><span class="sxs-lookup"><span data-stu-id="7b9c1-108">This section contains:</span></span>  
  
-   [<span data-ttu-id="7b9c1-109">Étape 1 : Installation de la plate-forme de Base</span><span class="sxs-lookup"><span data-stu-id="7b9c1-109">Step 1: Installing the Base Platform</span></span>](../../adapters-and-accelerators/accelerator-swift/step-1-installing-the-base-platform.md)  
  
-   [<span data-ttu-id="7b9c1-110">Étape 2 : Configuration d’équilibrage de charge réseau sur les serveurs</span><span class="sxs-lookup"><span data-stu-id="7b9c1-110">Step 2: Configuring NLB on the Servers</span></span>](../../adapters-and-accelerators/accelerator-swift/step-2-configuring-nlb-on-the-servers.md)  
  
-   [<span data-ttu-id="7b9c1-111">Étape 3 : Configurer le contrôleur de domaine</span><span class="sxs-lookup"><span data-stu-id="7b9c1-111">Step 3: Configuring the Domain Controller</span></span>](../../adapters-and-accelerators/accelerator-swift/step-3-configuring-the-domain-controller.md)  
  
-   [<span data-ttu-id="7b9c1-112">Étape 4 : Configuration des serveurs de base de données</span><span class="sxs-lookup"><span data-stu-id="7b9c1-112">Step 4: Configuring the Database Servers</span></span>](../../adapters-and-accelerators/accelerator-swift/step-4-configuring-the-database-servers.md)  
  
-   [<span data-ttu-id="7b9c1-113">Étape 5 : Configuration des serveurs de messagerie BizTalk</span><span class="sxs-lookup"><span data-stu-id="7b9c1-113">Step 5: Configuring the BizTalk Messaging Servers</span></span>](../../adapters-and-accelerators/accelerator-swift/step-5-configuring-the-biztalk-messaging-servers.md)  
  
-   [<span data-ttu-id="7b9c1-114">Étape 6 : Configurer les serveurs d’Orchestration de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="7b9c1-114">Step 6: Configuring the BizTalk Orchestration Servers</span></span>](../../adapters-and-accelerators/accelerator-swift/step-6-configuring-the-biztalk-orchestration-servers.md)  
  
-   [<span data-ttu-id="7b9c1-115">Étape 7 : Configuration des serveurs frontaux HTTP BizTalk</span><span class="sxs-lookup"><span data-stu-id="7b9c1-115">Step 7: Configuring the BizTalk HTTP Front-End Servers</span></span>](../../adapters-and-accelerators/accelerator-swift/step-7-configuring-the-biztalk-http-front-end-servers.md)  
  
-   [<span data-ttu-id="7b9c1-116">Étape 8 : Modifications apportées à la Configuration</span><span class="sxs-lookup"><span data-stu-id="7b9c1-116">Step 8: Post-Configuration Changes</span></span>](../../adapters-and-accelerators/accelerator-swift/step-8-post-configuration-changes.md)