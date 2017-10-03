---
title: "Single Sign-On : Événement 10509 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f906823f-db3f-45fc-bf61-cbe6a9566bd7
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b4d61cbb7af195aa88c36b64149366334c835b80
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10509"></a><span data-ttu-id="b71dd-102">Single Sign-On : Événement 10509</span><span class="sxs-lookup"><span data-stu-id="b71dd-102">Single Sign-On: Event 10509</span></span>
## <a name="details"></a><span data-ttu-id="b71dd-103">Détails</span><span class="sxs-lookup"><span data-stu-id="b71dd-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b71dd-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="b71dd-104">Product Name</span></span>|<span data-ttu-id="b71dd-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="b71dd-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="b71dd-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="b71dd-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="b71dd-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="b71dd-107">Event ID</span></span>|<span data-ttu-id="b71dd-108">10509</span><span class="sxs-lookup"><span data-stu-id="b71dd-108">10509</span></span>|  
|<span data-ttu-id="b71dd-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="b71dd-109">Event Source</span></span>|<span data-ttu-id="b71dd-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="b71dd-110">ENTSSO</span></span>|  
|<span data-ttu-id="b71dd-111">Composant</span><span class="sxs-lookup"><span data-stu-id="b71dd-111">Component</span></span>|<span data-ttu-id="b71dd-112">N\A</span><span class="sxs-lookup"><span data-stu-id="b71dd-112">N\A</span></span>|  
|<span data-ttu-id="b71dd-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="b71dd-113">Symbolic Name</span></span>|<span data-ttu-id="b71dd-114">SSO_INFO_SERVICE_REMOVE_FAILED</span><span class="sxs-lookup"><span data-stu-id="b71dd-114">SSO_INFO_SERVICE_REMOVE_FAILED</span></span>|  
|<span data-ttu-id="b71dd-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="b71dd-115">Message Text</span></span>|<span data-ttu-id="b71dd-116">Impossible de supprimer le service SSO.%r</span><span class="sxs-lookup"><span data-stu-id="b71dd-116">Failed to remove the SSO service.%r</span></span><br /><br /> <span data-ttu-id="b71dd-117">Code d’erreur : %1</span><span class="sxs-lookup"><span data-stu-id="b71dd-117">Error Code: %1</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="b71dd-118">Explication</span><span class="sxs-lookup"><span data-stu-id="b71dd-118">Explanation</span></span>  
 <span data-ttu-id="b71dd-119">Cet événement indique que la désinstallation du service ENTSSO a échoué.</span><span class="sxs-lookup"><span data-stu-id="b71dd-119">This event indicates that the ENTSSO Service failed to uninstall.</span></span> <span data-ttu-id="b71dd-120">Cet événement peut uniquement survenir lors d'une installation manuelle de l'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="b71dd-120">This event can only occur during a manual uninstallation of Enterprise Single Sign-On.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="b71dd-121">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="b71dd-121">User Action</span></span>  
 <span data-ttu-id="b71dd-122">Pour résoudre cet événement, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="b71dd-122">To resolve this event, do the following:</span></span>  
  
-   <span data-ttu-id="b71dd-123">Consultez les journaux des événements de l'application et du système relatifs aux erreurs associées à ENTSSO ou à d'autres services.</span><span class="sxs-lookup"><span data-stu-id="b71dd-123">Check both the Application and System event logs for related errors from ENTSSO or other services.</span></span>  
  
 <span data-ttu-id="b71dd-124">Pour plus d'informations, consultez les ressources suivantes dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="b71dd-124">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="b71dd-125">L’installation de l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="b71dd-125">Installing SSO</span></span>](../core/installing-sso.md)  
  
-   [<span data-ttu-id="b71dd-126">Mise en œuvre Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="b71dd-126">Implementing Enterprise Single Sign-On</span></span>](../core/implementing-enterprise-single-sign-on.md)