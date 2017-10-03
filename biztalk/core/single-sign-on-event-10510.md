---
title: "Single Sign-On : Événement 10510 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4553ad4c-9553-4b8b-b3a3-72aed2a61202
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 053f75541597e3b2e721c53714aaaf8517c3c49f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10510"></a><span data-ttu-id="304b5-102">Single Sign-On : Événement 10510</span><span class="sxs-lookup"><span data-stu-id="304b5-102">Single Sign-On: Event 10510</span></span>
## <a name="details"></a><span data-ttu-id="304b5-103">Détails</span><span class="sxs-lookup"><span data-stu-id="304b5-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="304b5-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="304b5-104">Product Name</span></span>|<span data-ttu-id="304b5-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="304b5-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="304b5-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="304b5-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="304b5-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="304b5-107">Event ID</span></span>|<span data-ttu-id="304b5-108">10510</span><span class="sxs-lookup"><span data-stu-id="304b5-108">10510</span></span>|  
|<span data-ttu-id="304b5-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="304b5-109">Event Source</span></span>|<span data-ttu-id="304b5-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="304b5-110">ENTSSO</span></span>|  
|<span data-ttu-id="304b5-111">Composant</span><span class="sxs-lookup"><span data-stu-id="304b5-111">Component</span></span>|<span data-ttu-id="304b5-112">N\A</span><span class="sxs-lookup"><span data-stu-id="304b5-112">N\A</span></span>|  
|<span data-ttu-id="304b5-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="304b5-113">Symbolic Name</span></span>|<span data-ttu-id="304b5-114">SSO_INFO_DLL_LOAD_FAILED</span><span class="sxs-lookup"><span data-stu-id="304b5-114">SSO_INFO_DLL_LOAD_FAILED</span></span>|  
|<span data-ttu-id="304b5-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="304b5-115">Message Text</span></span>|<span data-ttu-id="304b5-116">Échec du chargement de %1.</span><span class="sxs-lookup"><span data-stu-id="304b5-116">Failed to load %1.</span></span> <span data-ttu-id="304b5-117">Vérifiez que ce fichier est disponible.</span><span class="sxs-lookup"><span data-stu-id="304b5-117">Check that this file is available.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="304b5-118">Explication</span><span class="sxs-lookup"><span data-stu-id="304b5-118">Explanation</span></span>  
 <span data-ttu-id="304b5-119">Cet événement d'informations indique que le service d'authentification unique n'a pas pu charger le fichier DLL.</span><span class="sxs-lookup"><span data-stu-id="304b5-119">This Information event indicates that the SSO service has failed to load the DLL.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="304b5-120">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="304b5-120">User Action</span></span>  
 <span data-ttu-id="304b5-121">Pour résoudre cet événement, effectuez une ou plusieurs des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="304b5-121">To resolve this event, do one or more of the following:</span></span>  
  
-   <span data-ttu-id="304b5-122">Vérifiez le fichier DLL situé dans le répertoire d'installation de l'authentification unique (généralement, C:\Program Files\Common Files\Enterprise Single Sign-On).</span><span class="sxs-lookup"><span data-stu-id="304b5-122">Verify the DLL is located in the SSO installation directory, typically C:\Program Files\Common Files\Enterprise Single Sign-On.</span></span> <span data-ttu-id="304b5-123">Il se peut que votre répertoire d'installation de l'authentification unique soit différent.</span><span class="sxs-lookup"><span data-stu-id="304b5-123">Your SSO installation directory may be different.</span></span>  
  
-   <span data-ttu-id="304b5-124">Si le fichier DLL est manquant ou endommagé, remplacez-le, puis redémarrez le service.</span><span class="sxs-lookup"><span data-stu-id="304b5-124">If the single DLL is missing or corrupted, attempt to replace it and then restart the service.</span></span>  
  
 <span data-ttu-id="304b5-125">Pour plus d'informations, consultez les ressources suivantes dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="304b5-125">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="304b5-126">Mise en œuvre Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="304b5-126">Implementing Enterprise Single Sign-On</span></span>](../core/implementing-enterprise-single-sign-on.md)