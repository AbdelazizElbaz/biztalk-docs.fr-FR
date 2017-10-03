---
title: "Service de gestion de réseau | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 21469dad-6c64-470a-bd58-8309d789ce6c
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 741abaaa3042cb40f7043b25ce041bb84740f26a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="service-network-management"></a><span data-ttu-id="36643-102">Gestion des services réseau</span><span class="sxs-lookup"><span data-stu-id="36643-102">Service Network Management</span></span>
<span data-ttu-id="36643-103">Gouvernance exécution efficace requiert une connaissance des services déployés dans l’environnement d’exécution.</span><span class="sxs-lookup"><span data-stu-id="36643-103">Effective run-time governance requires knowledge of the services deployed into the run-time environment.</span></span> <span data-ttu-id="36643-104">AmberPoint SMS peut découvrir les emplacements de réception et déployés au sein d’un groupe d’administration de BizTalk, des ports d’envoi comme indiqué dans la Figure 1.</span><span class="sxs-lookup"><span data-stu-id="36643-104">AmberPoint SMS can discover the actual receive locations and send ports deployed within a BizTalk Management Group, as shown in Figure 1.</span></span>  
  
 <span data-ttu-id="36643-105">![Découverte du conteneur AmberPoint](../esb-toolkit/media/ch9-amberpointcontainerdiscovery.gif "Ch9-AmberPointContainerDiscovery")</span><span class="sxs-lookup"><span data-stu-id="36643-105">![AmberPoint Container Discovery](../esb-toolkit/media/ch9-amberpointcontainerdiscovery.gif "Ch9-AmberPointContainerDiscovery")</span></span>  
  
 <span data-ttu-id="36643-106">**Figure 1**</span><span class="sxs-lookup"><span data-stu-id="36643-106">**Figure 1**</span></span>  
  
 <span data-ttu-id="36643-107">**Les écrans de découverte du conteneur AmberPoint SMS**</span><span class="sxs-lookup"><span data-stu-id="36643-107">**The AmberPoint SMS Container Discovery screens**</span></span>  
  
 <span data-ttu-id="36643-108">À l’aide des informations sur les services déployés, AmberPoint SMS présente différentes perspectives des services qui permettent aux utilisateurs de comprendre la configuration de l’exécution et vous remercions de leurs dépendances sur d’autres services au sein de l’exécution du service réseau.</span><span class="sxs-lookup"><span data-stu-id="36643-108">Using information on the deployed services, AmberPoint SMS presents various perspectives of the services that help users to understand the run-time configuration and appreciate their dependencies on other services within the running service network.</span></span> <span data-ttu-id="36643-109">La figure 2 illustre les écrans de profil et les dépendances du service.</span><span class="sxs-lookup"><span data-stu-id="36643-109">Figure 2 shows the service profile and dependencies screens.</span></span>  
  
 <span data-ttu-id="36643-110">![Profil de Service AmberPoint](../esb-toolkit/media/ch9-amberpointserviceprofile.gif "Ch9-AmberPointServiceProfile")</span><span class="sxs-lookup"><span data-stu-id="36643-110">![AmberPoint Service Profile](../esb-toolkit/media/ch9-amberpointserviceprofile.gif "Ch9-AmberPointServiceProfile")</span></span>  
  
 <span data-ttu-id="36643-111">**Figure 2**</span><span class="sxs-lookup"><span data-stu-id="36643-111">**Figure 2**</span></span>  
  
 <span data-ttu-id="36643-112">**Les écrans de profil et les dépendances de service AmberPoint SMS**</span><span class="sxs-lookup"><span data-stu-id="36643-112">**The AmberPoint SMS service profile and dependencies screens**</span></span>  
  
 <span data-ttu-id="36643-113">AmberPoint SMS peut publier et transférer des découvertes de service et les métadonnées de l’exécution à existant Universal Description, Discovery, Integration (UDDI) registres, référentiels de gestion de configuration personnalisée et des consoles de gestion de système principal, tel que Microsoft Operations Manager 2004 (MOM) et System Center Operations Manager 2007 (SCOM).</span><span class="sxs-lookup"><span data-stu-id="36643-113">AmberPoint SMS can publish and forward service discoveries and run-time metadata to existing Universal Description, Discovery, and Integration (UDDI) registries, custom configuration management repositories, and master system management consoles, such as Microsoft Operations Manager 2004 (MOM) and System Center Operations Manager 2007 (SCOM).</span></span>