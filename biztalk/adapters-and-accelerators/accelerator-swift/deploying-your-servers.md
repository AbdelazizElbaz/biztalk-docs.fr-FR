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
ms.openlocfilehash: 8fc3da3798e78e9b5fcf1ce09180c43e10417997
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="deploying-your-servers"></a><span data-ttu-id="37de6-102">Déploiement de vos serveurs</span><span class="sxs-lookup"><span data-stu-id="37de6-102">Deploying Your Servers</span></span>
<span data-ttu-id="37de6-103">Cette section fournit des instructions de configuration de chacun des serveurs dans votre [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] déploiement.</span><span class="sxs-lookup"><span data-stu-id="37de6-103">This section provides instructions for configuring each of the servers in your [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] deployment.</span></span> <span data-ttu-id="37de6-104">Après avoir configuré le réseau que vous déployez le logiciel sur chaque serveur à l’aide de la procédure suivante.</span><span class="sxs-lookup"><span data-stu-id="37de6-104">After you configure the network you deploy the software on each server by using the following steps.</span></span>  
  
 <span data-ttu-id="37de6-105">Avant de commencer le déploiement de serveurs, assurez-vous que lire et effectuer les étapes décrites dans la préparation au déploiement [préparation au déploiement](../../adapters-and-accelerators/accelerator-swift/preparing-for-deployment.md).</span><span class="sxs-lookup"><span data-stu-id="37de6-105">Before starting server deployment, make sure that you read and perform the deployment preparation steps described in [Preparing for Deployment](../../adapters-and-accelerators/accelerator-swift/preparing-for-deployment.md).</span></span> <span data-ttu-id="37de6-106">Ne parvient pas à respecter les recommandations de la section précédente peuvent entraîner une configuration non pris en charge et inconnue du déploiement (et les étapes suivantes peuvent échouer).</span><span class="sxs-lookup"><span data-stu-id="37de6-106">Failing to adhere to the prescriptive guidance in the previous section might result in an unknown and unsupported configuration of the deployment (and subsequent steps might fail).</span></span>  
  
 <span data-ttu-id="37de6-107">Pour plus d’informations, consultez le Guide de déploiement de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="37de6-107">For more information, see the BizTalk Server Deployment Guide.</span></span>  
  
 <span data-ttu-id="37de6-108">Contenu de cette section :</span><span class="sxs-lookup"><span data-stu-id="37de6-108">This section contains:</span></span>  
  
-   [<span data-ttu-id="37de6-109">Étape 1 : Installation de la plateforme de base</span><span class="sxs-lookup"><span data-stu-id="37de6-109">Step 1: Installing the Base Platform</span></span>](../../adapters-and-accelerators/accelerator-swift/step-1-installing-the-base-platform.md)  
  
-   [<span data-ttu-id="37de6-110">Étape 2 : Configuration de l’équilibrage de la charge réseau sur les serveurs</span><span class="sxs-lookup"><span data-stu-id="37de6-110">Step 2: Configuring NLB on the Servers</span></span>](../../adapters-and-accelerators/accelerator-swift/step-2-configuring-nlb-on-the-servers.md)  
  
-   [<span data-ttu-id="37de6-111">Étape 3 : Configuration du contrôleur de domaine</span><span class="sxs-lookup"><span data-stu-id="37de6-111">Step 3: Configuring the Domain Controller</span></span>](../../adapters-and-accelerators/accelerator-swift/step-3-configuring-the-domain-controller.md)  
  
-   [<span data-ttu-id="37de6-112">Étape 4 : Configuration des serveurs de base de données</span><span class="sxs-lookup"><span data-stu-id="37de6-112">Step 4: Configuring the Database Servers</span></span>](../../adapters-and-accelerators/accelerator-swift/step-4-configuring-the-database-servers.md)  
  
-   [<span data-ttu-id="37de6-113">Étape 5 : Configuration des serveurs de messagerie BizTalk</span><span class="sxs-lookup"><span data-stu-id="37de6-113">Step 5: Configuring the BizTalk Messaging Servers</span></span>](../../adapters-and-accelerators/accelerator-swift/step-5-configuring-the-biztalk-messaging-servers.md)  
  
-   [<span data-ttu-id="37de6-114">Étape 6 : Configuration des serveurs d’orchestration BizTalk</span><span class="sxs-lookup"><span data-stu-id="37de6-114">Step 6: Configuring the BizTalk Orchestration Servers</span></span>](../../adapters-and-accelerators/accelerator-swift/step-6-configuring-the-biztalk-orchestration-servers.md)  
  
-   [<span data-ttu-id="37de6-115">Étape 7 : Configuration des serveurs frontend HTTP BizTalk</span><span class="sxs-lookup"><span data-stu-id="37de6-115">Step 7: Configuring the BizTalk HTTP Front-End Servers</span></span>](../../adapters-and-accelerators/accelerator-swift/step-7-configuring-the-biztalk-http-front-end-servers.md)  
  
-   [<span data-ttu-id="37de6-116">Étape 8 : Modifications post-configuration</span><span class="sxs-lookup"><span data-stu-id="37de6-116">Step 8: Post-Configuration Changes</span></span>](../../adapters-and-accelerators/accelerator-swift/step-8-post-configuration-changes.md)