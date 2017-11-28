---
title: "Single Sign-On : Événement 10611 est alors généré | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4549ac01-b828-478f-aea0-862e14fac149
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3582ee070b960b7eb17facc8d48e0b3e11dc5b9e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10611"></a><span data-ttu-id="9c18c-102">Single Sign-On : Événement 10611 est alors généré</span><span class="sxs-lookup"><span data-stu-id="9c18c-102">Single Sign-On: Event 10611</span></span>
## <a name="details"></a><span data-ttu-id="9c18c-103">Détails</span><span class="sxs-lookup"><span data-stu-id="9c18c-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9c18c-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="9c18c-104">Product Name</span></span>|<span data-ttu-id="9c18c-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="9c18c-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="9c18c-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="9c18c-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="9c18c-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="9c18c-107">Event ID</span></span>|<span data-ttu-id="9c18c-108">10611</span><span class="sxs-lookup"><span data-stu-id="9c18c-108">10611</span></span>|  
|<span data-ttu-id="9c18c-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="9c18c-109">Event Source</span></span>|<span data-ttu-id="9c18c-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="9c18c-110">ENTSSO</span></span>|  
|<span data-ttu-id="9c18c-111">Composant</span><span class="sxs-lookup"><span data-stu-id="9c18c-111">Component</span></span>|<span data-ttu-id="9c18c-112">Néant</span><span class="sxs-lookup"><span data-stu-id="9c18c-112">N/A</span></span>|  
|<span data-ttu-id="9c18c-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="9c18c-113">Symbolic Name</span></span>|<span data-ttu-id="9c18c-114">SSO_INFO_SERVICE_STARTING_NO_SSL</span><span class="sxs-lookup"><span data-stu-id="9c18c-114">SSO_INFO_SERVICE_STARTING_NO_SSL</span></span>|  
|<span data-ttu-id="9c18c-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="9c18c-115">Message Text</span></span>|<span data-ttu-id="9c18c-116">Le service d'authentification unique est en cours de démarrage.%r</span><span class="sxs-lookup"><span data-stu-id="9c18c-116">The SSO service is starting.%r</span></span><br /><br /> <span data-ttu-id="9c18c-117">Nom de l’ordinateur : %1 %r</span><span class="sxs-lookup"><span data-stu-id="9c18c-117">Computer Name: %1%r</span></span><br /><br /> <span data-ttu-id="9c18c-118">Nom du serveur SQL : %2 %r</span><span class="sxs-lookup"><span data-stu-id="9c18c-118">SQL Server Name: %2%r</span></span><br /><br /> <span data-ttu-id="9c18c-119">Nom de base de données SSO : %3 %r</span><span class="sxs-lookup"><span data-stu-id="9c18c-119">SSO Database Name: %3%r</span></span><br /><br /> <span data-ttu-id="9c18c-120">N'utilise pas SSL.</span><span class="sxs-lookup"><span data-stu-id="9c18c-120">Not using SSL.</span></span> <span data-ttu-id="9c18c-121">Pour plus d'informations sur la sécurisation de la connexion SQL Server, consultez la documentation.</span><span class="sxs-lookup"><span data-stu-id="9c18c-121">See documentation for details on how to secure the SQL Server connection.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="9c18c-122">Explication</span><span class="sxs-lookup"><span data-stu-id="9c18c-122">Explanation</span></span>  
 <span data-ttu-id="9c18c-123">Le service d'authentification unique de l'entreprise, en cours de démarrage, n'utilise pas le protocole SSL (Secure Sockets Layer).</span><span class="sxs-lookup"><span data-stu-id="9c18c-123">The ENTSSO Service is starting without using Secure Sockets Layer (SSL).</span></span> <span data-ttu-id="9c18c-124">Il est recommandé de sécuriser votre connexion entre le service d'authentification unique et SQL.</span><span class="sxs-lookup"><span data-stu-id="9c18c-124">It is recommended that you secure your connection from the SSO Service to SQL.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="9c18c-125">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="9c18c-125">User Action</span></span>  
 <span data-ttu-id="9c18c-126">Consultez la documentation relative à [comment activer SSL pour l’authentification unique](../core/how-to-enable-ssl-for-sso.md)</span><span class="sxs-lookup"><span data-stu-id="9c18c-126">See the documentation at [How to Enable SSL for SSO](../core/how-to-enable-ssl-for-sso.md)</span></span>  
  
 <span data-ttu-id="9c18c-127">.</span><span class="sxs-lookup"><span data-stu-id="9c18c-127">.</span></span>