---
title: "Le programme d’installation de développeur Machine pour la Solution gestion des processus d’entreprise | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- developer servers
- process management solution tutorial, developer servers
- process management solution tutorial, deploying
ms.assetid: cf975323-53ec-45a8-9f68-80ad423f298b
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1e2491d755062828a3204d895fa7be7552ef06d5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="developer-machine-setup-for-the-business-process-management-solution"></a><span data-ttu-id="c0f6d-102">Configuration de l'ordinateur du développeur pour démarrer la solution de gestion des processus d'entreprise</span><span class="sxs-lookup"><span data-stu-id="c0f6d-102">Developer Machine Setup for the Business Process Management Solution</span></span>
<span data-ttu-id="c0f6d-103">La solution de gestion des processus d'entreprise présente une manière de construire un gestionnaire de processus dans une application BizTalk.</span><span class="sxs-lookup"><span data-stu-id="c0f6d-103">The Business Process Management (BPM) solution shows one way to construct a process manager in a BizTalk application.</span></span> <span data-ttu-id="c0f6d-104">Elle utilise un composant pour sélectionner et contrôler la séquence d'étapes du traitement de commande.</span><span class="sxs-lookup"><span data-stu-id="c0f6d-104">The solution uses a component to select and control the sequence of stages in order processing.</span></span> <span data-ttu-id="c0f6d-105">La solution prend une commande (par exemple, pour un nouveau service, une mise à niveau ou un arrêt de service), la consigne et en accuse réception avant de la transmettre pour traitement.</span><span class="sxs-lookup"><span data-stu-id="c0f6d-105">The solution takes an order—which may be for new service, an upgrade, or termination of service—logs it, and acknowledges the order before passing it on for processing.</span></span> <span data-ttu-id="c0f6d-106">Le traitement de la commande consiste en une ou plusieurs étapes.</span><span class="sxs-lookup"><span data-stu-id="c0f6d-106">The processing consists of one or more stages that handle the order.</span></span> <span data-ttu-id="c0f6d-107">Enfin, la solution renvoie une réponse à la demande d'origine.</span><span class="sxs-lookup"><span data-stu-id="c0f6d-107">Finally, the solution returns a response to the original order request.</span></span>  
  
 <span data-ttu-id="c0f6d-108">En tant que développeur, vous commencez par vous familiariser avec le fonctionnement d'un seul ordinateur.</span><span class="sxs-lookup"><span data-stu-id="c0f6d-108">As a developer, you first get the scenario running on a single computer.</span></span> <span data-ttu-id="c0f6d-109">Une fois les fonctionnalités testées sur celui-ci, vous allez discuter, avec les informaticiens, du déploiement de la solution sur des serveurs de production.</span><span class="sxs-lookup"><span data-stu-id="c0f6d-109">After testing functionalities on the single computer, you will discuss how to deploy the solution on production servers with IT professionals.</span></span> <span data-ttu-id="c0f6d-110">Vous devez les aider à concevoir l'architecture du système pour qu'elle réponde aux besoins du service (haute disponibilité, performances accrues, maintenance facilitée).</span><span class="sxs-lookup"><span data-stu-id="c0f6d-110">You need to help them to design the system architecture to satisfy service requirements such as high availability, better performance, and easier maintenance.</span></span> <span data-ttu-id="c0f6d-111">Ensuite, vous préparez les ressources pour un déploiement de production basé sur la conception.</span><span class="sxs-lookup"><span data-stu-id="c0f6d-111">You will then prepare resources for production deployment based on the design.</span></span>  
  
 <span data-ttu-id="c0f6d-112">Ce guide de déploiement décrit l'installation et le test de la solution de gestion des processus d'entreprise sur un seul ordinateur.</span><span class="sxs-lookup"><span data-stu-id="c0f6d-112">This deployment guide describes how to install and test the business process management solution on a single computer.</span></span>  
  
 <span data-ttu-id="c0f6d-113">Pour plus d’informations sur la solution gestion des processus d’entreprise, consultez [présentation de la Solution de gestion des processus métier](../core/understanding-the-business-process-management-solution.md).</span><span class="sxs-lookup"><span data-stu-id="c0f6d-113">For more information about the business process management solution, see [Understanding the Business Process Management Solution](../core/understanding-the-business-process-management-solution.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c0f6d-114">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="c0f6d-114">In This Section</span></span>  
  
-   [<span data-ttu-id="c0f6d-115">Avant d’installer la Solution gestion des processus d’entreprise</span><span class="sxs-lookup"><span data-stu-id="c0f6d-115">Before Installing the Business Process Management Solution</span></span>](../core/before-installing-the-business-process-management-solution.md)  
  
-   [<span data-ttu-id="c0f6d-116">Comment installer la Solution gestion des processus d’entreprise</span><span class="sxs-lookup"><span data-stu-id="c0f6d-116">How to Install the Business Process Management Solution</span></span>](../core/how-to-install-the-business-process-management-solution.md)  
  
-   [<span data-ttu-id="c0f6d-117">Comment exécuter la Solution gestion des processus d’entreprise</span><span class="sxs-lookup"><span data-stu-id="c0f6d-117">How to Run the Business Process Management Solution</span></span>](../core/how-to-run-the-business-process-management-solution.md)