---
title: "Utiliser l’authentification unique pour sécuriser TIBCO EMS | Documents Microsoft"
description: "Présentation de la sécurité lors de l’utilisation de l’adaptateur Microsoft BizTalk pour TIBCO Enterprise Message Service dans BizTalk Server"
ms.custom: 
ms.date: 10/19/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0eccb44b-e9d8-42c2-a575-47f1d1cfe93c
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1d0974595a13e583928bca1cab394fce0d1d154f
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="security-in-biztalk-adapter-for-tibco-ems"></a><span data-ttu-id="34b94-103">Sécurité dans l'adaptateur BizTalk pour TIBCO EMS</span><span class="sxs-lookup"><span data-stu-id="34b94-103">Security in BizTalk Adapter for TIBCO EMS</span></span>

## <a name="overview"></a><span data-ttu-id="34b94-104">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="34b94-104">Overview</span></span>
<span data-ttu-id="34b94-105">L'adaptateur Microsoft BizTalk pour TIBCO Enterprise Message Service prend en charge l'authentification unique (SSO).</span><span class="sxs-lookup"><span data-stu-id="34b94-105">Microsoft BizTalk Adapter for TIBCO Enterprise Message Service provides Single Sign-On (SSO) support.</span></span> <span data-ttu-id="34b94-106">Une application associée qui a été créée par des outils de l'authentification unique de l'entreprise représente un système serveur tel que TIBCO Enterprise Message Service.</span><span class="sxs-lookup"><span data-stu-id="34b94-106">An affiliate application created by Enterprise Single Sign-On tools represents a server system such as TIBCO Enterprise Message Service.</span></span>  

<span data-ttu-id="34b94-107">Cette section fournit des instructions relatives au déploiement d'un adaptateur BizTalk pour TIBCO Enterprise Message Service dans un environnement sécurisé.</span><span class="sxs-lookup"><span data-stu-id="34b94-107">This section provides guidelines on how to deploy BizTalk Adapter for TIBCO Enterprise Message Service in a secure environment.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="34b94-108">Il est hautement recommandé de limiter l’utilisation de l’adaptateur BizTalk pour Enterprise Message Service aux utilisateurs autorisés, comme les fichiers du client sont directement connectés aux applications line-of-business.</span><span class="sxs-lookup"><span data-stu-id="34b94-108">It is highly recommended that you restrict the use of BizTalk Adapter for Enterprise Message Service to authorized users only, as the client files directly connect to the line-of-business applications.</span></span>    

  
## <a name="next-steps"></a><span data-ttu-id="34b94-109">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="34b94-109">Next steps</span></span>
  
-   [<span data-ttu-id="34b94-110">Configuration requise pour l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="34b94-110">Requirements for Single Sign-On</span></span>](../core/requirements-for-single-sign-on4.md)  
  
-   [<span data-ttu-id="34b94-111">Authentification unique et adaptateur BizTalk pour TIBCO Enterprise Message Service</span><span class="sxs-lookup"><span data-stu-id="34b94-111">Single Sign-On and BizTalk Adapter for TIBCO Enterprise Message Service</span></span>](../core/single-sign-on-and-biztalk-adapter-for-tibco-enterprise-message-service.md)  
  
-   [<span data-ttu-id="34b94-112">Création d’applications associées</span><span class="sxs-lookup"><span data-stu-id="34b94-112">Creating Affiliate Applications</span></span>](../core/creating-affiliate-applications5.md)  
  
-   [<span data-ttu-id="34b94-113">Création de ports d’envoi</span><span class="sxs-lookup"><span data-stu-id="34b94-113">Creating Send Ports</span></span>](../core/creating-send-ports1.md)  
  
-   [<span data-ttu-id="34b94-114">Exécution de projets d’authentification unique</span><span class="sxs-lookup"><span data-stu-id="34b94-114">Running SSO Projects</span></span>](../core/running-sso-projects2.md)