---
title: "Déploiement de la Solution de gestion des processus métier | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deploying, process management solution tutorial
- process management solution tutorial, deploying
ms.assetid: e033e0cd-0333-4f16-a4a0-eaae9ce98fcc
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a0a61048ecb90876b251657f00361c35587a7ec1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="deploying-the-business-process-management-solution"></a><span data-ttu-id="f06f9-102">Déploiement de la solution de gestion des processus d'entreprise</span><span class="sxs-lookup"><span data-stu-id="f06f9-102">Deploying the Business Process Management Solution</span></span>
<span data-ttu-id="f06f9-103">La solution de gestion des processus d'entreprise présente une manière de construire un gestionnaire de processus dans une application BizTalk.</span><span class="sxs-lookup"><span data-stu-id="f06f9-103">The Business Process Management (BPM) solution shows one way to construct a process manager in a BizTalk application.</span></span> <span data-ttu-id="f06f9-104">Elle utilise un composant pour sélectionner et contrôler la séquence d'étapes du traitement de commande.</span><span class="sxs-lookup"><span data-stu-id="f06f9-104">The solution uses a component to select and control the sequence of stages in order processing.</span></span> <span data-ttu-id="f06f9-105">La solution prend une commande (par exemple, pour un nouveau service, une mise à niveau ou une annulation de service), la consigne et en accuse réception avant de la transmettre pour traitement.</span><span class="sxs-lookup"><span data-stu-id="f06f9-105">The solution takes an order—which may be for a new service, an upgrade, or termination of service—logs it, and acknowledges the order before passing it on for processing.</span></span> <span data-ttu-id="f06f9-106">Le traitement de la commande consiste en une ou plusieurs étapes.</span><span class="sxs-lookup"><span data-stu-id="f06f9-106">The processing consists of one or more stages that handle the order.</span></span> <span data-ttu-id="f06f9-107">Enfin, la solution renvoie une réponse à la demande d'origine.</span><span class="sxs-lookup"><span data-stu-id="f06f9-107">Finally, the solution returns a response to the original order request.</span></span>  
  
 <span data-ttu-id="f06f9-108">Ce guide de déploiement décrit l'installation et l'exécution de la solution de gestion des processus d'entreprise sur un ordinateur de développement et plusieurs serveurs de production.</span><span class="sxs-lookup"><span data-stu-id="f06f9-108">This deployment guide describes how to install and run the business process management solution on a development computer and multiple production servers.</span></span>  
  
 <span data-ttu-id="f06f9-109">Pour plus d’informations sur la solution gestion des processus d’entreprise, consultez [présentation de la Solution de gestion des processus métier](../core/understanding-the-business-process-management-solution.md).</span><span class="sxs-lookup"><span data-stu-id="f06f9-109">For more information about the business process management solution, see [Understanding the Business Process Management Solution](../core/understanding-the-business-process-management-solution.md).</span></span>  
  
 <span data-ttu-id="f06f9-110">**Guide de lecteur**</span><span class="sxs-lookup"><span data-stu-id="f06f9-110">**Reader Guidance**</span></span>  
  
 <span data-ttu-id="f06f9-111">Ce document suppose que vous connaissez BizTalk Server, Windows Server et Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f06f9-111">This document assumes that you are familiar with BizTalk Server, Windows Server, and Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span></span> <span data-ttu-id="f06f9-112">Il suppose également que vous comprenez les concepts de base sur l’intégration d’applications d’entreprise et les services Web.</span><span class="sxs-lookup"><span data-stu-id="f06f9-112">It also assumes that you understand basic concepts about enterprise application integration and Web services.</span></span> <span data-ttu-id="f06f9-113">En outre, il est recommandé d'être familiarisé avec la création d'applications sous [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], la création de projets, la définition de références et l'utilisation du mode de débogage pour déboguer et tester votre solution.</span><span class="sxs-lookup"><span data-stu-id="f06f9-113">Additionally, we recommend that you are familiar with how to build applications by using [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] and that you are familiar with creating projects, setting references, and using the debug mode to debug and test your solution.</span></span> <span data-ttu-id="f06f9-114">Pour plus d’informations sur les compétences et connaissances préalables pour les professionnels de l’informatique et aux développeurs, consultez [condition préalable compétences et connaissances](../core/prerequisite-skills-and-knowledge5.md).</span><span class="sxs-lookup"><span data-stu-id="f06f9-114">For more information about the prerequisite skills and knowledge for IT professionals and developers, see [Prerequisite Skills and Knowledge](../core/prerequisite-skills-and-knowledge5.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f06f9-115">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="f06f9-115">In This Section</span></span>  
  
-   [<span data-ttu-id="f06f9-116">Programme d’installation de développeur Machine pour la Solution gestion des processus d’entreprise</span><span class="sxs-lookup"><span data-stu-id="f06f9-116">Developer Machine Setup for the Business Process Management Solution</span></span>](../core/developer-machine-setup-for-the-business-process-management-solution.md)