---
title: "Scénario : Déploiement de deux Versions d’une Application | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- receive locations, multiple assemblies
- assemblies, multiple assemblies
- receive locations, examples
- assemblies, deploying
- assemblies, examples
ms.assetid: 3e79a7df-bf77-4a0b-86ec-359fcf3489b3
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f1bb4f04e8b00dd171de89bbed6f01d2a2d1e2e2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="scenario-deploying-two-versions-of-an-application"></a><span data-ttu-id="3fcdc-102">Scénario : Déploiement de deux Versions d’une Application</span><span class="sxs-lookup"><span data-stu-id="3fcdc-102">Scenario: Deploying Two Versions of an Application</span></span>
<span data-ttu-id="3fcdc-103">Cette rubrique décrit le déploiement de deux versions d'une application au sein d'un groupe BizTalk, de sorte qu'elles puissent s'exécuter simultanément.</span><span class="sxs-lookup"><span data-stu-id="3fcdc-103">This topic describes the scenario of deploying two versions of an application within a BizTalk group, so that they can both run simultaneously.</span></span> <span data-ttu-id="3fcdc-104">Dans ce scénario, vous devez déployer une nouvelle version principale de l'application.</span><span class="sxs-lookup"><span data-stu-id="3fcdc-104">In this scenario, you need to deploy a major new version of the application.</span></span> <span data-ttu-id="3fcdc-105">Les partenaires doivent modifier leur interaction avec le système du fait des modifications apportées au schéma ou au protocole, ce qui revient globalement à utiliser une nouvelle version de l'application.</span><span class="sxs-lookup"><span data-stu-id="3fcdc-105">It requires partners to change their interaction with the system due to either schema or protocol change - essentially a new application.</span></span> <span data-ttu-id="3fcdc-106">Le changement de ce système a été testé, mais pas à l'échelle d'un système de production entier.</span><span class="sxs-lookup"><span data-stu-id="3fcdc-106">The changeover to this system has been tested but not under the scale of a full production system.</span></span> <span data-ttu-id="3fcdc-107">Vous souhaitez gérer le nouveau système avec 20 % des partenaires, avant d'augmenter progressivement ce pourcentage jusqu'à 100 % des partenaires.</span><span class="sxs-lookup"><span data-stu-id="3fcdc-107">You want to pilot the new system with 20 percent of the partners, and gradually increase that percentage until all the partners are using it.</span></span>  
  
 <span data-ttu-id="3fcdc-108">Les deux applications recevant les messages sur deux emplacements de réception différents, vous devez demander aux partenaires qui doivent utiliser la nouvelle version de l'application d'envoyer des messages vers la nouvelle URL, de sorte qu'ils puissent être traités par la nouvelle version.</span><span class="sxs-lookup"><span data-stu-id="3fcdc-108">Because the two applications receive messages on two different receive locations, you must ask those partners that should use the new version of the application to send messages to the new URL, so that they will be processed by the new version.</span></span>  
  
 <span data-ttu-id="3fcdc-109">Le schéma suivant montre un déploiement d'application côte à côte type.</span><span class="sxs-lookup"><span data-stu-id="3fcdc-109">The following diagram shows a typical side-by-side application deployment.</span></span>  
  
 <span data-ttu-id="3fcdc-110">![Deux Versions d’assemblys déployées ensemble](../core/media/sidebysideassemblyversions.gif "SideBySideAssemblyVersions")</span><span class="sxs-lookup"><span data-stu-id="3fcdc-110">![Two Assembly Versions Deployed Together](../core/media/sidebysideassemblyversions.gif "SideBySideAssemblyVersions")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fcdc-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3fcdc-111">See Also</span></span>  
 [<span data-ttu-id="3fcdc-112">Déploiement d’applications et scénarios de gestion</span><span class="sxs-lookup"><span data-stu-id="3fcdc-112">Application Deployment and Management Scenarios</span></span>](../core/application-deployment-and-management-scenarios.md)