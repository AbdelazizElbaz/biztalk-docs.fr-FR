---
title: "Single Sign-On : Événement 10514 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0b527841-a2e2-44c7-a9cb-6e9a8eea2fba
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 40077ead4157b4cc6c91a2c44b4a19569d76ebc1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10514"></a><span data-ttu-id="39d79-102">Single Sign-On : Événement 10514</span><span class="sxs-lookup"><span data-stu-id="39d79-102">Single Sign-On: Event 10514</span></span>
## <a name="details"></a><span data-ttu-id="39d79-103">Détails</span><span class="sxs-lookup"><span data-stu-id="39d79-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="39d79-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="39d79-104">Product Name</span></span>|<span data-ttu-id="39d79-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="39d79-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="39d79-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="39d79-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="39d79-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="39d79-107">Event ID</span></span>|<span data-ttu-id="39d79-108">10514</span><span class="sxs-lookup"><span data-stu-id="39d79-108">10514</span></span>|  
|<span data-ttu-id="39d79-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="39d79-109">Event Source</span></span>|<span data-ttu-id="39d79-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="39d79-110">ENTSSO</span></span>|  
|<span data-ttu-id="39d79-111">Composant</span><span class="sxs-lookup"><span data-stu-id="39d79-111">Component</span></span>|<span data-ttu-id="39d79-112">N\A</span><span class="sxs-lookup"><span data-stu-id="39d79-112">N\A</span></span>|  
|<span data-ttu-id="39d79-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="39d79-113">Symbolic Name</span></span>|<span data-ttu-id="39d79-114">SSO_ERROR_DB_ACCESS</span><span class="sxs-lookup"><span data-stu-id="39d79-114">SSO_ERROR_DB_ACCESS</span></span>|  
|<span data-ttu-id="39d79-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="39d79-115">Message Text</span></span>|<span data-ttu-id="39d79-116">Une erreur s'est produite lors de la tentative d'accès à la base de données SSO.%r</span><span class="sxs-lookup"><span data-stu-id="39d79-116">An error occurred while attempting to access the SSO database.%r</span></span><br /><br /> <span data-ttu-id="39d79-117">Fonction : %1 %r</span><span class="sxs-lookup"><span data-stu-id="39d79-117">Function: %1%r</span></span><br /><br /> <span data-ttu-id="39d79-118">Fichier : %2 %r</span><span class="sxs-lookup"><span data-stu-id="39d79-118">File: %2%r</span></span><br /><br /> <span data-ttu-id="39d79-119">%3.%r</span><span class="sxs-lookup"><span data-stu-id="39d79-119">%3.%r</span></span><br /><br /> <span data-ttu-id="39d79-120">Code d’erreur SQL : %4 %r</span><span class="sxs-lookup"><span data-stu-id="39d79-120">SQL Error code: %4%r</span></span><br /><br /> <span data-ttu-id="39d79-121">Code d’erreur : %5</span><span class="sxs-lookup"><span data-stu-id="39d79-121">Error code: %5</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="39d79-122">Explication</span><span class="sxs-lookup"><span data-stu-id="39d79-122">Explanation</span></span>  
 <span data-ttu-id="39d79-123">Cet événement d'erreur indique qu'une erreur a été reçue de SQL Server lors de la tentative d'accès à la base de données SSO.</span><span class="sxs-lookup"><span data-stu-id="39d79-123">This Error event indicates that an error was received from SQL Server when attempting to access the SSO database.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="39d79-124">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="39d79-124">User Action</span></span>  
 <span data-ttu-id="39d79-125">Pour résoudre cette erreur, procédez de l'une des manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="39d79-125">To resolve this error, do one or more of the following:</span></span>  
  
-   <span data-ttu-id="39d79-126">Vérifiez que le service SQL Server (MSSQLSERVER) est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="39d79-126">Verify that the SQL Server (MSSQLSERVER) service is running.</span></span>  
  
-   <span data-ttu-id="39d79-127">Vérifiez le code d’erreur SQL Server à l’aide du centre d’événements et erreurs à [http://go.microsoft.com/fwlink/?LinkID=20869](http://go.microsoft.com/fwlink/?LinkID=20869).</span><span class="sxs-lookup"><span data-stu-id="39d79-127">Check the SQL Server error code using the Events and Errors Message Center at [http://go.microsoft.com/fwlink/?LinkID=20869](http://go.microsoft.com/fwlink/?LinkID=20869).</span></span>  
  
 <span data-ttu-id="39d79-128">Pour plus d'informations, consultez les ressources suivantes dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="39d79-128">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="39d79-129">Mise en œuvre Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="39d79-129">Implementing Enterprise Single Sign-On</span></span>](../core/implementing-enterprise-single-sign-on.md)  
  
-   [<span data-ttu-id="39d79-130">Comment afficher les informations de base de données SSO</span><span class="sxs-lookup"><span data-stu-id="39d79-130">How to Display the SSO Database Information</span></span>](../core/how-to-display-the-sso-database-information.md)  
  
 <span data-ttu-id="39d79-131">Consultez également la documentation en ligne de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="39d79-131">See also SQL Server Books Online.</span></span>