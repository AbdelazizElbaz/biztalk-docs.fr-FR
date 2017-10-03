---
title: "Single Sign-On : Événement 10654 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 49372d5a-8136-4bdd-8004-b5736ddbe058
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 06d7de49ec1606c7c0a33f802af11af4e8ad2848
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10654"></a><span data-ttu-id="ddd6c-102">Single Sign-On : Événement 10654</span><span class="sxs-lookup"><span data-stu-id="ddd6c-102">Single Sign-On: Event 10654</span></span>
## <a name="details"></a><span data-ttu-id="ddd6c-103">Détails</span><span class="sxs-lookup"><span data-stu-id="ddd6c-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ddd6c-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="ddd6c-104">Product Name</span></span>|<span data-ttu-id="ddd6c-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="ddd6c-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="ddd6c-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="ddd6c-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="ddd6c-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="ddd6c-107">Event ID</span></span>|<span data-ttu-id="ddd6c-108">10654</span><span class="sxs-lookup"><span data-stu-id="ddd6c-108">10654</span></span>|  
|<span data-ttu-id="ddd6c-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="ddd6c-109">Event Source</span></span>|<span data-ttu-id="ddd6c-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="ddd6c-110">ENTSSO</span></span>|  
|<span data-ttu-id="ddd6c-111">Composant</span><span class="sxs-lookup"><span data-stu-id="ddd6c-111">Component</span></span>|<span data-ttu-id="ddd6c-112">N\A</span><span class="sxs-lookup"><span data-stu-id="ddd6c-112">N\A</span></span>|  
|<span data-ttu-id="ddd6c-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="ddd6c-113">Symbolic Name</span></span>|<span data-ttu-id="ddd6c-114">SSO_ERROR_PS_WINDOWS_CALLBACK_ACCESS_DENIED</span><span class="sxs-lookup"><span data-stu-id="ddd6c-114">SSO_ERROR_PS_WINDOWS_CALLBACK_ACCESS_DENIED</span></span>|  
|<span data-ttu-id="ddd6c-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="ddd6c-115">Message Text</span></span>|<span data-ttu-id="ddd6c-116">Accès refusé au serveur de synchronisation de mot de passe (pour Windows).%r</span><span class="sxs-lookup"><span data-stu-id="ddd6c-116">Password sync server (for Windows) access denied.%r</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="ddd6c-117">Explication</span><span class="sxs-lookup"><span data-stu-id="ddd6c-117">Explanation</span></span>  
 <span data-ttu-id="ddd6c-118">Cet événement d'erreur indique qu'un message a été envoyé au serveur [nom] mais que la réponse a été bloquée.</span><span class="sxs-lookup"><span data-stu-id="ddd6c-118">This Error event indicates that a message was sent to the [name] server but the reply was blocked.</span></span> <span data-ttu-id="ddd6c-119">Différentes causes peuvent être à l'origine de ce problème (protocole incorrect, autorisations de sécurité insuffisantes sur le serveur, etc.).</span><span class="sxs-lookup"><span data-stu-id="ddd6c-119">This can be caused by a number of different reasons, such as incorrect protocol or insufficient security permissions on the server.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="ddd6c-120">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="ddd6c-120">User Action</span></span>  
 <span data-ttu-id="ddd6c-121">Pour résoudre cette erreur, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="ddd6c-121">To resolve this error, do the following:</span></span>  
  
-   <span data-ttu-id="ddd6c-122">Notez les informations contenues dans ce message et les informations appropriées dans le journal des événements, puis contactez les Services de Support technique Microsoft.</span><span class="sxs-lookup"><span data-stu-id="ddd6c-122">Note the information in this message, and any relevant information in the event log, and contact Microsoft Product Support Services.</span></span>  
  
 <span data-ttu-id="ddd6c-123">Pour plus d'informations, consultez les ressources suivantes dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="ddd6c-123">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="ddd6c-124">Synchronisation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="ddd6c-124">Password Synchronization</span></span>](../core/password-synchronization2.md)