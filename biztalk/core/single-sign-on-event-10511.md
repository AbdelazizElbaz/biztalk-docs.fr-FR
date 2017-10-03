---
title: "Single Sign-On : Événement 10511 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 98371982-0db5-4ae0-9f92-f05a58e23b83
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c080812d70dc78a0fe2a9b217833f961da951401
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10511"></a><span data-ttu-id="14dd1-102">Single Sign-On : Événement 10511</span><span class="sxs-lookup"><span data-stu-id="14dd1-102">Single Sign-On: Event 10511</span></span>
## <a name="details"></a><span data-ttu-id="14dd1-103">Détails</span><span class="sxs-lookup"><span data-stu-id="14dd1-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="14dd1-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="14dd1-104">Product Name</span></span>|<span data-ttu-id="14dd1-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="14dd1-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="14dd1-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="14dd1-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="14dd1-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="14dd1-107">Event ID</span></span>|<span data-ttu-id="14dd1-108">10511</span><span class="sxs-lookup"><span data-stu-id="14dd1-108">10511</span></span>|  
|<span data-ttu-id="14dd1-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="14dd1-109">Event Source</span></span>|<span data-ttu-id="14dd1-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="14dd1-110">ENTSSO</span></span>|  
|<span data-ttu-id="14dd1-111">Composant</span><span class="sxs-lookup"><span data-stu-id="14dd1-111">Component</span></span>|<span data-ttu-id="14dd1-112">N\A</span><span class="sxs-lookup"><span data-stu-id="14dd1-112">N\A</span></span>|  
|<span data-ttu-id="14dd1-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="14dd1-113">Symbolic Name</span></span>|<span data-ttu-id="14dd1-114">SSO_ERROR_NO_DSN</span><span class="sxs-lookup"><span data-stu-id="14dd1-114">SSO_ERROR_NO_DSN</span></span>|  
|<span data-ttu-id="14dd1-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="14dd1-115">Message Text</span></span>|<span data-ttu-id="14dd1-116">Les noms du serveur SQL Server et de la base de données SSO sont introuvables dans le Registre.</span><span class="sxs-lookup"><span data-stu-id="14dd1-116">The SQL Server and SSO database names were not found in the registry.</span></span> <span data-ttu-id="14dd1-117">Utilisez les outils d'administration SSO pour configurer ces valeurs.</span><span class="sxs-lookup"><span data-stu-id="14dd1-117">Use the SSO administration tools to configure these values.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="14dd1-118">Explication</span><span class="sxs-lookup"><span data-stu-id="14dd1-118">Explanation</span></span>  
 <span data-ttu-id="14dd1-119">Cet événement d'erreur indique que les noms du serveur SQL Server et de la base de données SSO sont introuvables dans le Registre.</span><span class="sxs-lookup"><span data-stu-id="14dd1-119">This Error event indicates that the SQL Server and SSO database names were not found in the registry.</span></span> <span data-ttu-id="14dd1-120">Le service SSO requiert ces informations pour se connecter à la base de données SSO.</span><span class="sxs-lookup"><span data-stu-id="14dd1-120">The SSO service requires this information so it can connect to the SSO database.</span></span> <span data-ttu-id="14dd1-121">Celles-ci sont définies dans le Registre lors de la configuration.</span><span class="sxs-lookup"><span data-stu-id="14dd1-121">This information is set in the registry during configuration.</span></span> <span data-ttu-id="14dd1-122">Ceci peut indiquer que la configuration n'a pas été correctement exécutée ou que les entrées de Registre ont été supprimées après l'exécution de la configuration.</span><span class="sxs-lookup"><span data-stu-id="14dd1-122">This may indicate that configuration did not complete correctly or that the registry entries have been deleted after configuration was completed.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="14dd1-123">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="14dd1-123">User Action</span></span>  
 <span data-ttu-id="14dd1-124">Pour résoudre cette erreur, procédez de l'une des manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="14dd1-124">To resolve this error, do one or more of the following:</span></span>  
  
-   <span data-ttu-id="14dd1-125">Si vous suspectez une défaillance de la configuration, annulez la configuration du produit, puis reconfigurez-la à l'aide du programme de configuration.</span><span class="sxs-lookup"><span data-stu-id="14dd1-125">If you suspect a wider configuration failure, unconfigure the product and then reconfigure using the configuration program.</span></span>  
  
-   <span data-ttu-id="14dd1-126">Ces entrées de Registre manquantes spécifiques peuvent également être définies à l'aide de l'outil de ligne de commande de l'authentification unique (ssoconfig.exe) accessible dans le répertoire d'installation de l'authentification unique (généralement, C:\Program Files\Common Files\Enterprise Single Sign-On).</span><span class="sxs-lookup"><span data-stu-id="14dd1-126">Alternatively these specific missing registry entries can be set using the SSO command line tool, ssoconfig.exe located in the SSO installation directory, typically C:\Program Files\Common Files\Enterprise Single Sign-On.</span></span> <span data-ttu-id="14dd1-127">Il se peut que votre répertoire d'installation de l'authentification unique soit différent.</span><span class="sxs-lookup"><span data-stu-id="14dd1-127">Your SSO installation directory may be different.</span></span> <span data-ttu-id="14dd1-128">Utilisez le **- setDB** option pour définir les noms de base de données SQL Server et SSO requis.</span><span class="sxs-lookup"><span data-stu-id="14dd1-128">Use the **-setDB** option to set the required SQL Server and SSO database names.</span></span>  
  
 <span data-ttu-id="14dd1-129">Pour plus d'informations, consultez les ressources suivantes dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="14dd1-129">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="14dd1-130">Mise en œuvre Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="14dd1-130">Implementing Enterprise Single Sign-On</span></span>](../core/implementing-enterprise-single-sign-on.md)