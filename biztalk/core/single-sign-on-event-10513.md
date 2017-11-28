---
title: "Single Sign-On : Événement 10513 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b3306223-111f-4abf-ae65-be839b355216
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7f1be7ae463dbb1ee9651f69f231614cc11db5f1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10513"></a><span data-ttu-id="ad293-102">Single Sign-On : Événement 10513</span><span class="sxs-lookup"><span data-stu-id="ad293-102">Single Sign-On: Event 10513</span></span>
## <a name="details"></a><span data-ttu-id="ad293-103">Détails</span><span class="sxs-lookup"><span data-stu-id="ad293-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ad293-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="ad293-104">Product Name</span></span>|<span data-ttu-id="ad293-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="ad293-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="ad293-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="ad293-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="ad293-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="ad293-107">Event ID</span></span>|<span data-ttu-id="ad293-108">10513</span><span class="sxs-lookup"><span data-stu-id="ad293-108">10513</span></span>|  
|<span data-ttu-id="ad293-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="ad293-109">Event Source</span></span>|<span data-ttu-id="ad293-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="ad293-110">ENTSSO</span></span>|  
|<span data-ttu-id="ad293-111">Composant</span><span class="sxs-lookup"><span data-stu-id="ad293-111">Component</span></span>|<span data-ttu-id="ad293-112">N\A</span><span class="sxs-lookup"><span data-stu-id="ad293-112">N\A</span></span>|  
|<span data-ttu-id="ad293-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="ad293-113">Symbolic Name</span></span>|<span data-ttu-id="ad293-114">SSO_ERROR_DB_FIRST_ACCESS</span><span class="sxs-lookup"><span data-stu-id="ad293-114">SSO_ERROR_DB_FIRST_ACCESS</span></span>|  
|<span data-ttu-id="ad293-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="ad293-115">Message Text</span></span>|<span data-ttu-id="ad293-116">Impossible de contacter la base de données SSO : %1 %r</span><span class="sxs-lookup"><span data-stu-id="ad293-116">Failed to contact the SSO database: %1%r</span></span><br /><br /> <span data-ttu-id="ad293-117">%2 %r</span><span class="sxs-lookup"><span data-stu-id="ad293-117">%2%r</span></span><br /><br /> <span data-ttu-id="ad293-118">Code d’erreur : %3</span><span class="sxs-lookup"><span data-stu-id="ad293-118">Error code: %3</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="ad293-119">Explication</span><span class="sxs-lookup"><span data-stu-id="ad293-119">Explanation</span></span>  
 <span data-ttu-id="ad293-120">Cet événement de type erreur indique que le service SSO ne peut pas se connecter à la base de données SSO à son démarrage.</span><span class="sxs-lookup"><span data-stu-id="ad293-120">This Error event indicates that the SSO Service cannot connect to the SSO database when it starts.</span></span> <span data-ttu-id="ad293-121">Le message d'événement contient la chaîne DSN (Data Source Name - nom de source de données) indiquant les noms du SQL Server et de la base de données, ainsi qu'un message d'erreur émanant des bibliothèques de connexions SQL.</span><span class="sxs-lookup"><span data-stu-id="ad293-121">The event message contains the Data Source Name (DSN) string indicating the specified SQL Server and database names as well as the error message that was returned from the SQL connection libraries.</span></span>  
  
 <span data-ttu-id="ad293-122">Quand le service SSO démarre, il tente de se connecter à la base de données SSO via les noms de SQL Server et de base de données SSO spécifiés dans le registre.</span><span class="sxs-lookup"><span data-stu-id="ad293-122">When the SSO Service starts, it will attempt to connect to the SSO database using the SQL Server and SSO database names specified in the registry.</span></span> <span data-ttu-id="ad293-123">Il tente de se connecter 12 fois, en attendant 5 secondes entre chaque tentative ayant échoué. Cela lui prend en tout 1 minute.</span><span class="sxs-lookup"><span data-stu-id="ad293-123">The SSO Service will attempt to connect 12 times, waiting 5 seconds between each failed attempt, for a total of 1 minute.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="ad293-124">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="ad293-124">User Action</span></span>  
 <span data-ttu-id="ad293-125">Pour résoudre cette erreur, procédez de l'une des manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="ad293-125">To resolve this error, do one or more of the following:</span></span>  
  
-   <span data-ttu-id="ad293-126">Vérifiez que le service SQL Server (MSSQLSERVER) est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="ad293-126">Verify the SQL Server (MSSQLSERVER) service is running.</span></span>  
  
-   <span data-ttu-id="ad293-127">Vérifiez que la chaîne DSN indiquée dans le message d'erreur est correcte et contient les noms de SQL Server et de base de données adéquats.</span><span class="sxs-lookup"><span data-stu-id="ad293-127">Verify the Data Source Name (DSN) string indicated in the error message is correct and contains the correct SQL Server and database names.</span></span>  
  
 <span data-ttu-id="ad293-128">Pour plus d'informations, consultez les ressources suivantes dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="ad293-128">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="ad293-129">Mise en œuvre Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="ad293-129">Implementing Enterprise Single Sign-On</span></span>](../core/implementing-enterprise-single-sign-on.md)  
  
-   [<span data-ttu-id="ad293-130">Comment afficher les informations de base de données SSO</span><span class="sxs-lookup"><span data-stu-id="ad293-130">How to Display the SSO Database Information</span></span>](../core/how-to-display-the-sso-database-information.md)  
  
-   [<span data-ttu-id="ad293-131">Configuration de l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="ad293-131">Configuring SSO</span></span>](../core/configuring-sso.md)  
  
-   <span data-ttu-id="ad293-132">documentation en ligne de SQL Server</span><span class="sxs-lookup"><span data-stu-id="ad293-132">SQL Server Books Online</span></span>