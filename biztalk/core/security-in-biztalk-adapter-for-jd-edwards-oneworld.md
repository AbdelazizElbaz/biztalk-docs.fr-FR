---
title: "Utiliser l’authentification unique pour sécuriser JD Edwards OneWorld | Documents Microsoft"
description: "Présentation de la sécurité lors de l’utilisation de l’adaptateur Microsoft BizTalk JD Edwards OneWorld dans BizTalk Server"
ms.custom: 
ms.date: 10/18/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: beb736a8-d95f-4d44-a882-2d437c4892f4
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 97e72ffbc38cad2f5bbd622ed497663cf8ac5f3c
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="security-in-jd-edwards-oneworld"></a><span data-ttu-id="afcc5-103">Sécurité dans JD Edwards OneWorld</span><span class="sxs-lookup"><span data-stu-id="afcc5-103">Security in JD Edwards OneWorld</span></span>

## <a name="overview"></a><span data-ttu-id="afcc5-104">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="afcc5-104">Overview</span></span>
<span data-ttu-id="afcc5-105">L'adaptateur Microsoft BizTalk pour JD Edwards OneWorld prend en charge l'authentification unique (SSO).</span><span class="sxs-lookup"><span data-stu-id="afcc5-105">Microsoft BizTalk Adapter for JD Edwards OneWorld provides Single Sign-On (SSO) support.</span></span> <span data-ttu-id="afcc5-106">Une application associée qui a été créée par des outils de l'authentification unique de l'entreprise représente un système serveur tel que JD Edwards OneWorld.</span><span class="sxs-lookup"><span data-stu-id="afcc5-106">An affiliate application created by Enterprise Single Sign-On tools represents a server system such as JD Edwards OneWorld.</span></span>  

<span data-ttu-id="afcc5-107">Cette section fournit des instructions relatives au déploiement d'un adaptateur Microsoft BizTalk pour JD Edwards OneWorld dans un environnement sécurisé.</span><span class="sxs-lookup"><span data-stu-id="afcc5-107">This section provides guidelines about how to deploy Microsoft BizTalk Adapter for JD Edwards OneWorld in a secure environment.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="afcc5-108">Nous avons recommandé de limiter l’utilisation de l’adaptateur BizTalk pour JD Edwards OneWorld aux utilisateurs autorisés, comme les fichiers du client sont directement connectés aux applications line-of-business.</span><span class="sxs-lookup"><span data-stu-id="afcc5-108">We recommended that you restrict the use of BizTalk Adapter for JD Edwards OneWorld to authorized users only, as the client files directly connect to the line-of-business applications.</span></span>  

## <a name="next-steps"></a><span data-ttu-id="afcc5-109">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="afcc5-109">Next steps</span></span>
  
-   [<span data-ttu-id="afcc5-110">Configuration requise pour l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="afcc5-110">Requirements for Single Sign-On</span></span>](../core/requirements-for-single-sign-on5.md)  
  
-   [<span data-ttu-id="afcc5-111">Authentification unique et adaptateur BizTalk pour JD Edwards OneWorld</span><span class="sxs-lookup"><span data-stu-id="afcc5-111">Single Sign-On and BizTalk Adapter for JD Enterprise OneWorld</span></span>](../core/single-sign-on-and-biztalk-adapter-for-jd-enterprise-oneworld.md)  
  
-   [<span data-ttu-id="afcc5-112">Création d’applications associées</span><span class="sxs-lookup"><span data-stu-id="afcc5-112">Creating Affiliate Applications</span></span>](../core/creating-affiliate-applications3.md)  
  
-   [<span data-ttu-id="afcc5-113">Configuration du répertoire virtuel</span><span class="sxs-lookup"><span data-stu-id="afcc5-113">Configuring the Virtual Directory</span></span>](../core/configuring-the-virtual-directory.md)  
  
-   [<span data-ttu-id="afcc5-114">Comment faire pour configurer l’adaptateur de réception HTTP</span><span class="sxs-lookup"><span data-stu-id="afcc5-114">How to Configure the HTTP Receive Adapter</span></span>](../core/how-to-configure-the-http-receive-adapter2.md)  
  
-   [<span data-ttu-id="afcc5-115">Création de ports d’envoi et de réception</span><span class="sxs-lookup"><span data-stu-id="afcc5-115">Creating Send and Receive Ports</span></span>](../core/creating-send-and-receive-ports.md)  
  
-   [<span data-ttu-id="afcc5-116">Importation de schémas dans des projets BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="afcc5-116">Importing Schemas into BizTalk Server Projects</span></span>](../core/importing-schemas-into-biztalk-server-projects1.md)  
  
-   [<span data-ttu-id="afcc5-117">Exécution d’orchestrations</span><span class="sxs-lookup"><span data-stu-id="afcc5-117">Running Orchestrations</span></span>](../core/running-orchestrations1.md)  
  
-   [<span data-ttu-id="afcc5-118">Exécution de projets d’authentification unique</span><span class="sxs-lookup"><span data-stu-id="afcc5-118">Running SSO Projects</span></span>](../core/running-sso-projects3.md)