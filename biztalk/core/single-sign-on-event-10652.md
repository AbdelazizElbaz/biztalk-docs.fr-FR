---
title: "Single Sign-On : Événement 10652 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ae7fe452-bcec-4722-8ec6-78d4fe462a0a
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 62066b2fbbc47d07fa57f047313ed5ed8cda47d5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10652"></a><span data-ttu-id="d8c66-102">Single Sign-On : Événement 10652</span><span class="sxs-lookup"><span data-stu-id="d8c66-102">Single Sign-On: Event 10652</span></span>
## <a name="details"></a><span data-ttu-id="d8c66-103">Détails</span><span class="sxs-lookup"><span data-stu-id="d8c66-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d8c66-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="d8c66-104">Product Name</span></span>|<span data-ttu-id="d8c66-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="d8c66-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="d8c66-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="d8c66-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="d8c66-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="d8c66-107">Event ID</span></span>|<span data-ttu-id="d8c66-108">10652</span><span class="sxs-lookup"><span data-stu-id="d8c66-108">10652</span></span>|  
|<span data-ttu-id="d8c66-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="d8c66-109">Event Source</span></span>|<span data-ttu-id="d8c66-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="d8c66-110">ENTSSO</span></span>|  
|<span data-ttu-id="d8c66-111">Composant</span><span class="sxs-lookup"><span data-stu-id="d8c66-111">Component</span></span>|<span data-ttu-id="d8c66-112">N\A</span><span class="sxs-lookup"><span data-stu-id="d8c66-112">N\A</span></span>|  
|<span data-ttu-id="d8c66-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="d8c66-113">Symbolic Name</span></span>|<span data-ttu-id="d8c66-114">SSO_ERROR_PASSWORD_SYNC_START_FAILED</span><span class="sxs-lookup"><span data-stu-id="d8c66-114">SSO_ERROR_PASSWORD_SYNC_START_FAILED</span></span>|  
|<span data-ttu-id="d8c66-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="d8c66-115">Message Text</span></span>|<span data-ttu-id="d8c66-116">Impossible d'initialiser les services de synchronisation des mots de passe.%r</span><span class="sxs-lookup"><span data-stu-id="d8c66-116">Password sync services failed to initialize.%r</span></span><br /><br /> <span data-ttu-id="d8c66-117">Code d’erreur : %1</span><span class="sxs-lookup"><span data-stu-id="d8c66-117">Error Code: %1</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="d8c66-118">Explication</span><span class="sxs-lookup"><span data-stu-id="d8c66-118">Explanation</span></span>  
 <span data-ttu-id="d8c66-119">Cet événement d'erreur indique que le service de synchronisation des mots de passe n'a pas pu démarrer en raison d'une exception.</span><span class="sxs-lookup"><span data-stu-id="d8c66-119">This Error event indicates that the Password Sync Service could not start due to an exception.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="d8c66-120">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="d8c66-120">User Action</span></span>  
 <span data-ttu-id="d8c66-121">Pour résoudre cette erreur, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="d8c66-121">To resolve this error, do the following:</span></span>  
  
-   <span data-ttu-id="d8c66-122">Consultez les journaux des événements de l'application et du système relatifs aux erreurs associées à ENTSSO ou à d'autres services.</span><span class="sxs-lookup"><span data-stu-id="d8c66-122">Check both the Application and System event logs for related errors from ENTSSO or other services.</span></span>  
  
 <span data-ttu-id="d8c66-123">Pour plus d'informations, consultez les ressources suivantes dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="d8c66-123">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="d8c66-124">Synchronisation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="d8c66-124">Password Synchronization</span></span>](../core/password-synchronization2.md)