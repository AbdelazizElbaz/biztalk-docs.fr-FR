---
title: "Single Sign-On : Événement 10661 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c3418f37-770d-4021-9341-5dbe99689da6
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6fdc655a87975a89387d84e2aefdd07a603c0ed3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10661"></a><span data-ttu-id="c1dee-102">Single Sign-On : Événement 10661</span><span class="sxs-lookup"><span data-stu-id="c1dee-102">Single Sign-On: Event 10661</span></span>
## <a name="details"></a><span data-ttu-id="c1dee-103">Détails</span><span class="sxs-lookup"><span data-stu-id="c1dee-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c1dee-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="c1dee-104">Product Name</span></span>|<span data-ttu-id="c1dee-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="c1dee-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="c1dee-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="c1dee-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="c1dee-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="c1dee-107">Event ID</span></span>|<span data-ttu-id="c1dee-108">10661</span><span class="sxs-lookup"><span data-stu-id="c1dee-108">10661</span></span>|  
|<span data-ttu-id="c1dee-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="c1dee-109">Event Source</span></span>|<span data-ttu-id="c1dee-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="c1dee-110">ENTSSO</span></span>|  
|<span data-ttu-id="c1dee-111">Composant</span><span class="sxs-lookup"><span data-stu-id="c1dee-111">Component</span></span>|<span data-ttu-id="c1dee-112">N\A</span><span class="sxs-lookup"><span data-stu-id="c1dee-112">N\A</span></span>|  
|<span data-ttu-id="c1dee-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="c1dee-113">Symbolic Name</span></span>|<span data-ttu-id="c1dee-114">SSO_ERROR_PASSWORD_SYNC_WINDOWS_START_FAILED</span><span class="sxs-lookup"><span data-stu-id="c1dee-114">SSO_ERROR_PASSWORD_SYNC_WINDOWS_START_FAILED</span></span>|  
|<span data-ttu-id="c1dee-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="c1dee-115">Message Text</span></span>|<span data-ttu-id="c1dee-116">Impossible de démarrer la synchronisation de mot de passe pour Windows (depuis PCNS).%r</span><span class="sxs-lookup"><span data-stu-id="c1dee-116">Password sync for Windows (from PCNS) failed to start.%r</span></span><br /><br /> <span data-ttu-id="c1dee-117">Code d’erreur : %1</span><span class="sxs-lookup"><span data-stu-id="c1dee-117">Error Code: %1</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="c1dee-118">Explication</span><span class="sxs-lookup"><span data-stu-id="c1dee-118">Explanation</span></span>  
 <span data-ttu-id="c1dee-119">Cette erreur indique que la synchronisation de mot de passe pour Windows n'a pas démarré.</span><span class="sxs-lookup"><span data-stu-id="c1dee-119">This Error event indicates that password sync for Windows failed to start.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="c1dee-120">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="c1dee-120">User Action</span></span>  
 <span data-ttu-id="c1dee-121">Pour résoudre cette erreur, procédez de l'une des manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="c1dee-121">To resolve this error, do one or more of the following:</span></span>  
  
-   <span data-ttu-id="c1dee-122">Consultez les journaux des événements de l'application et du système pour connaître les événements associés.</span><span class="sxs-lookup"><span data-stu-id="c1dee-122">Check the application and system event logs for associated events.</span></span>  
  
-   <span data-ttu-id="c1dee-123">Vérifiez les propriétés de la configuration de la carte.</span><span class="sxs-lookup"><span data-stu-id="c1dee-123">Verify adapter configuration properties.</span></span>  
  
## <a name="more-info"></a><span data-ttu-id="c1dee-124">En savoir plus</span><span class="sxs-lookup"><span data-stu-id="c1dee-124">More info</span></span>
  
-   [<span data-ttu-id="c1dee-125">Comment administrer la synchronisation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="c1dee-125">How to Administer Password Synchronization</span></span>](../core/how-to-administer-password-synchronization.md)  
  
-   <span data-ttu-id="c1dee-126">**Aide de l’interface utilisateur de l’authentification unique entreprise**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="c1dee-126">**Enterprise Single Sign-On UI Help** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>