---
title: "Single Sign-On : Événement 10706 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d73db77e-5bb6-431c-a8ca-5682d7ab3d6a
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5703c81d87376349561f644da558b8594cd51b79
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10706"></a><span data-ttu-id="c52e4-102">Single Sign-On : Événement 10706</span><span class="sxs-lookup"><span data-stu-id="c52e4-102">Single Sign-On: Event 10706</span></span>
## <a name="details"></a><span data-ttu-id="c52e4-103">Détails</span><span class="sxs-lookup"><span data-stu-id="c52e4-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c52e4-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="c52e4-104">Product Name</span></span>|<span data-ttu-id="c52e4-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="c52e4-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="c52e4-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="c52e4-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="c52e4-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="c52e4-107">Event ID</span></span>|<span data-ttu-id="c52e4-108">10706</span><span class="sxs-lookup"><span data-stu-id="c52e4-108">10706</span></span>|  
|<span data-ttu-id="c52e4-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="c52e4-109">Event Source</span></span>|<span data-ttu-id="c52e4-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="c52e4-110">ENTSSO</span></span>|  
|<span data-ttu-id="c52e4-111">Composant</span><span class="sxs-lookup"><span data-stu-id="c52e4-111">Component</span></span>|<span data-ttu-id="c52e4-112">N\A</span><span class="sxs-lookup"><span data-stu-id="c52e4-112">N\A</span></span>|  
|<span data-ttu-id="c52e4-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="c52e4-113">Symbolic Name</span></span>|<span data-ttu-id="c52e4-114">SSO_WARN_PS_NO_GLOBAL_SYNC</span><span class="sxs-lookup"><span data-stu-id="c52e4-114">SSO_WARN_PS_NO_GLOBAL_SYNC</span></span>|  
|<span data-ttu-id="c52e4-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="c52e4-115">Message Text</span></span>|<span data-ttu-id="c52e4-116">Les adaptateurs requièrent une synchronisation de mot de passe pour être autorisés par les indicateurs globaux.</span><span class="sxs-lookup"><span data-stu-id="c52e4-116">Group adapters require password sync to be allowed by the global flags.</span></span> <span data-ttu-id="c52e4-117">Vérifiez les indicateurs globaux.%r</span><span class="sxs-lookup"><span data-stu-id="c52e4-117">Check the global flags.%r</span></span><br /><br /> <span data-ttu-id="c52e4-118">Adaptateur : %1</span><span class="sxs-lookup"><span data-stu-id="c52e4-118">Adapter: %1</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="c52e4-119">Explication</span><span class="sxs-lookup"><span data-stu-id="c52e4-119">Explanation</span></span>  
 <span data-ttu-id="c52e4-120">Cet avertissement indique que la synchronisation de mot de passe est demandée par un adaptateur de synchronisation de mot de passe externe et qu'aucun indicateur global n'est défini.</span><span class="sxs-lookup"><span data-stu-id="c52e4-120">This Warning event indicates that password sync is requested by an external password sync adapter and neither of the global flags is set.</span></span> <span data-ttu-id="c52e4-121">Il y a deux indicateurs. L'un deux autorise l'envoi des mots de passe aux systèmes externes (SSO_FLAG_FULL_SYNC_FROM_WINDOWS_TO_EXTERNAL), tandis que l'autre autorise la réception des mots de passe à partir de systèmes externes (SSO_FLAG_PARTIAL_SYNC_FROM_EXTERNAL_TO_DB).</span><span class="sxs-lookup"><span data-stu-id="c52e4-121">There are two flags, one that allows sending of password to external system: SSO_FLAG_FULL_SYNC_FROM_WINDOWS_TO_EXTERNAL and another that allows receiving of passwords from external systems SSO_FLAG_PARTIAL_SYNC_FROM_EXTERNAL_TO_DB.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="c52e4-122">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="c52e4-122">User Action</span></span>  
 <span data-ttu-id="c52e4-123">Pour résoudre cet avertissement, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="c52e4-123">To resolve this warning, do the following:</span></span>  
  
-   <span data-ttu-id="c52e4-124">Utilisez le composant logiciel enfichable de la console MMC d’administration SSO, (système &#124; Propriétés &#124; Options) ou l’outil de ligne de commande `ssomanage –enable winsync/extsync` pour activer les indicateurs globaux.</span><span class="sxs-lookup"><span data-stu-id="c52e4-124">Use the SSO Admin MMC Snap-In, (System &#124; Properties &#124; Options) or command line tool  `ssomanage –enable winsync/extsync` to enable the global flags.</span></span>  
  
## <a name="more-info"></a><span data-ttu-id="c52e4-125">En savoir plus</span><span class="sxs-lookup"><span data-stu-id="c52e4-125">More info</span></span>
  
-   <span data-ttu-id="c52e4-126">**Indicateurs l’authentification unique de l’entreprise**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="c52e4-126">**Enterprise Single Sign-On Flags** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>
  
-   [<span data-ttu-id="c52e4-127">Comment administrer la synchronisation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="c52e4-127">How to Administer Password Synchronization</span></span>](../core/how-to-administer-password-synchronization.md)