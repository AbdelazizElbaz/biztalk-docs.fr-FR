---
title: "Single Sign-On : Événement 10655 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1bb6a8dd-35e4-40a6-8900-450a9b6de249
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 185a8315cc49de3bfc807636ce78755e8421d802
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10655"></a><span data-ttu-id="ab1fe-102">Single Sign-On : Événement 10655</span><span class="sxs-lookup"><span data-stu-id="ab1fe-102">Single Sign-On: Event 10655</span></span>
## <a name="details"></a><span data-ttu-id="ab1fe-103">Détails</span><span class="sxs-lookup"><span data-stu-id="ab1fe-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ab1fe-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="ab1fe-104">Product Name</span></span>|<span data-ttu-id="ab1fe-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="ab1fe-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="ab1fe-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="ab1fe-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="ab1fe-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="ab1fe-107">Event ID</span></span>|<span data-ttu-id="ab1fe-108">10655</span><span class="sxs-lookup"><span data-stu-id="ab1fe-108">10655</span></span>|  
|<span data-ttu-id="ab1fe-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="ab1fe-109">Event Source</span></span>|<span data-ttu-id="ab1fe-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="ab1fe-110">ENTSSO</span></span>|  
|<span data-ttu-id="ab1fe-111">Composant</span><span class="sxs-lookup"><span data-stu-id="ab1fe-111">Component</span></span>|<span data-ttu-id="ab1fe-112">N\A</span><span class="sxs-lookup"><span data-stu-id="ab1fe-112">N\A</span></span>|  
|<span data-ttu-id="ab1fe-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="ab1fe-113">Symbolic Name</span></span>|<span data-ttu-id="ab1fe-114">SSO_ERROR_PS_PING_CALLBACK_ACCESS_DENIED</span><span class="sxs-lookup"><span data-stu-id="ab1fe-114">SSO_ERROR_PS_PING_CALLBACK_ACCESS_DENIED</span></span>|  
|<span data-ttu-id="ab1fe-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="ab1fe-115">Message Text</span></span>|<span data-ttu-id="ab1fe-116">Accès refusé au serveur de synchronisation de mot de passe (pour ping).%r</span><span class="sxs-lookup"><span data-stu-id="ab1fe-116">Password sync server (for ping) access denied.%r</span></span><br /><br /> <span data-ttu-id="ab1fe-117">Utilisateur client : %1</span><span class="sxs-lookup"><span data-stu-id="ab1fe-117">Client User: %1</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="ab1fe-118">Explication</span><span class="sxs-lookup"><span data-stu-id="ab1fe-118">Explanation</span></span>  
 <span data-ttu-id="ab1fe-119">Cet événement d'erreur indique qu'un message a été envoyé au serveur [nom] mais que la réponse a été bloquée.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-119">This Error event indicates that a message was sent to the [name] server but the reply was blocked.</span></span> <span data-ttu-id="ab1fe-120">Différentes causes peuvent être à l'origine de ce problème (protocole incorrect, autorisations de sécurité insuffisantes sur le serveur, etc.).</span><span class="sxs-lookup"><span data-stu-id="ab1fe-120">This can be caused by a number of different reasons, such as incorrect protocol or insufficient security permissions on the server.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="ab1fe-121">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="ab1fe-121">User Action</span></span>  
 <span data-ttu-id="ab1fe-122">Pour résoudre cette erreur, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="ab1fe-122">To resolve this error, do the following:</span></span>  
  
-   <span data-ttu-id="ab1fe-123">Notez les informations contenues dans ce message et les informations appropriées dans le journal des événements, puis contactez les Services de Support technique Microsoft.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-123">Note the information in this message, and any relevant information in the event log, and contact Microsoft Product Support Services.</span></span>  
  
 <span data-ttu-id="ab1fe-124">Pour plus d'informations, consultez les ressources suivantes dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="ab1fe-124">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="ab1fe-125">Synchronisation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="ab1fe-125">Password Synchronization</span></span>](../core/password-synchronization2.md)