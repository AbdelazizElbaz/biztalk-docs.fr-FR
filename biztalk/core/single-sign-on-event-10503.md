---
title: "Single Sign-On : Événement 10503 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 04292ae8-8daf-4f5a-837e-fe5dfcd02b10
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 53c02388304fa9fab0b518517ba51b2db94412f2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10503"></a><span data-ttu-id="0bb83-102">Single Sign-On : Événement 10503</span><span class="sxs-lookup"><span data-stu-id="0bb83-102">Single Sign-On: Event 10503</span></span>
## <a name="details"></a><span data-ttu-id="0bb83-103">Détails</span><span class="sxs-lookup"><span data-stu-id="0bb83-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0bb83-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="0bb83-104">Product Name</span></span>|<span data-ttu-id="0bb83-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="0bb83-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="0bb83-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="0bb83-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="0bb83-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="0bb83-107">Event ID</span></span>|<span data-ttu-id="0bb83-108">10503</span><span class="sxs-lookup"><span data-stu-id="0bb83-108">10503</span></span>|  
|<span data-ttu-id="0bb83-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="0bb83-109">Event Source</span></span>|<span data-ttu-id="0bb83-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="0bb83-110">ENTSSO</span></span>|  
|<span data-ttu-id="0bb83-111">Composant</span><span class="sxs-lookup"><span data-stu-id="0bb83-111">Component</span></span>|<span data-ttu-id="0bb83-112">N\A</span><span class="sxs-lookup"><span data-stu-id="0bb83-112">N\A</span></span>|  
|<span data-ttu-id="0bb83-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="0bb83-113">Symbolic Name</span></span>|<span data-ttu-id="0bb83-114">SSO_ERROR_SERVICE_START_FAILED</span><span class="sxs-lookup"><span data-stu-id="0bb83-114">SSO_ERROR_SERVICE_START_FAILED</span></span>|  
|<span data-ttu-id="0bb83-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="0bb83-115">Message Text</span></span>|<span data-ttu-id="0bb83-116">Échec du démarrage du service d'authentification unique.%r</span><span class="sxs-lookup"><span data-stu-id="0bb83-116">The SSO service failed to start.%r</span></span><br /><br /> <span data-ttu-id="0bb83-117">Code d’erreur : %1</span><span class="sxs-lookup"><span data-stu-id="0bb83-117">Error Code: %1</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="0bb83-118">Explication</span><span class="sxs-lookup"><span data-stu-id="0bb83-118">Explanation</span></span>  
 <span data-ttu-id="0bb83-119">Cet événement d'erreur indique que le service d'authentification unique de l'entreprise n'a pas pu démarrer en raison d'une exception.</span><span class="sxs-lookup"><span data-stu-id="0bb83-119">This Error event indicates that the ENTSSO Service could not start due to an exception.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="0bb83-120">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="0bb83-120">User Action</span></span>  
 <span data-ttu-id="0bb83-121">Pour résoudre cette erreur, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="0bb83-121">To resolve this error, do the following:</span></span>  
  
-   <span data-ttu-id="0bb83-122">Consultez les journaux des événements de l'application et du système relatifs aux erreurs associées à ENTSSO ou à d'autres services.</span><span class="sxs-lookup"><span data-stu-id="0bb83-122">Check both the Application and System event logs for related errors from ENTSSO or other services.</span></span>  
  
 <span data-ttu-id="0bb83-123">Pour plus d'informations, consultez les ressources suivantes dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="0bb83-123">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="0bb83-124">À l’aide de l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="0bb83-124">Using SSO</span></span>](../core/using-sso.md)