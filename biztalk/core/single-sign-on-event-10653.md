---
title: "Single Sign-On : Événement 10653 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a0d85aca-20d9-4d65-8834-b31eacf143c8
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 91ec21a7883c3c1d3e97519f9239050ea18035fd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10653"></a><span data-ttu-id="8b382-102">Single Sign-On : Événement 10653</span><span class="sxs-lookup"><span data-stu-id="8b382-102">Single Sign-On: Event 10653</span></span>
## <a name="details"></a><span data-ttu-id="8b382-103">Détails</span><span class="sxs-lookup"><span data-stu-id="8b382-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8b382-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="8b382-104">Product Name</span></span>|<span data-ttu-id="8b382-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="8b382-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="8b382-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="8b382-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="8b382-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="8b382-107">Event ID</span></span>|<span data-ttu-id="8b382-108">10653</span><span class="sxs-lookup"><span data-stu-id="8b382-108">10653</span></span>|  
|<span data-ttu-id="8b382-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="8b382-109">Event Source</span></span>|<span data-ttu-id="8b382-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="8b382-110">ENTSSO</span></span>|  
|<span data-ttu-id="8b382-111">Composant</span><span class="sxs-lookup"><span data-stu-id="8b382-111">Component</span></span>|<span data-ttu-id="8b382-112">N\A</span><span class="sxs-lookup"><span data-stu-id="8b382-112">N\A</span></span>|  
|<span data-ttu-id="8b382-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="8b382-113">Symbolic Name</span></span>|<span data-ttu-id="8b382-114">SSO_ERROR_PS_ADAPTER_CALLBACK_ACCESS_DENIED</span><span class="sxs-lookup"><span data-stu-id="8b382-114">SSO_ERROR_PS_ADAPTER_CALLBACK_ACCESS_DENIED</span></span>|  
|<span data-ttu-id="8b382-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="8b382-115">Message Text</span></span>|<span data-ttu-id="8b382-116">Accès refusé au serveur de synchronisation de mot de passe (pour les adaptateurs).%r</span><span class="sxs-lookup"><span data-stu-id="8b382-116">Password sync server (for adapters) access denied.%r</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="8b382-117">Explication</span><span class="sxs-lookup"><span data-stu-id="8b382-117">Explanation</span></span>  
 <span data-ttu-id="8b382-118">Cet événement d'erreur indique qu'un client a tenté de contacter le serveur mais que l'appel a été refusé.</span><span class="sxs-lookup"><span data-stu-id="8b382-118">This Error event indicates that a client attempted to contact the server but the call was refused.</span></span> <span data-ttu-id="8b382-119">Différentes causes peuvent être à l'origine de ce problème (protocole incorrect, autorisations de sécurité insuffisantes, etc.).</span><span class="sxs-lookup"><span data-stu-id="8b382-119">This can be caused by a number of different reasons, such as incorrect protocol or insufficient security permissions.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="8b382-120">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="8b382-120">User Action</span></span>  
 <span data-ttu-id="8b382-121">Pour résoudre cette erreur, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="8b382-121">To resolve this error, do the following:</span></span>  
  
-   <span data-ttu-id="8b382-122">Notez les informations contenues dans ce message et les informations appropriées dans le journal des événements, puis contactez les Services de Support technique Microsoft.</span><span class="sxs-lookup"><span data-stu-id="8b382-122">Note the information in this message, and any relevant information in the event log, and contact Microsoft Product Support Services.</span></span>  
  
 <span data-ttu-id="8b382-123">Pour plus d'informations, consultez les ressources suivantes dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="8b382-123">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="8b382-124">Synchronisation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="8b382-124">Password Synchronization</span></span>](../core/password-synchronization2.md)