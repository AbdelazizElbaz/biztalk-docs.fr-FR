---
title: "Single Sign-On : Événement 10708 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 63675191-41cb-43fc-9355-e4ddc3f354c5
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d600c39b2e79e619e5adfbda2ffc152169ccd5d4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10708"></a><span data-ttu-id="11041-102">Single Sign-On : Événement 10708</span><span class="sxs-lookup"><span data-stu-id="11041-102">Single Sign-On: Event 10708</span></span>
## <a name="details"></a><span data-ttu-id="11041-103">Détails</span><span class="sxs-lookup"><span data-stu-id="11041-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="11041-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="11041-104">Product Name</span></span>|<span data-ttu-id="11041-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="11041-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="11041-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="11041-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="11041-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="11041-107">Event ID</span></span>|<span data-ttu-id="11041-108">10708</span><span class="sxs-lookup"><span data-stu-id="11041-108">10708</span></span>|  
|<span data-ttu-id="11041-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="11041-109">Event Source</span></span>|<span data-ttu-id="11041-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="11041-110">ENTSSO</span></span>|  
|<span data-ttu-id="11041-111">Composant</span><span class="sxs-lookup"><span data-stu-id="11041-111">Component</span></span>|<span data-ttu-id="11041-112">N\A</span><span class="sxs-lookup"><span data-stu-id="11041-112">N\A</span></span>|  
|<span data-ttu-id="11041-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="11041-113">Symbolic Name</span></span>|<span data-ttu-id="11041-114">SSO_WARN_PS_NO_WIN_SYNC</span><span class="sxs-lookup"><span data-stu-id="11041-114">SSO_WARN_PS_NO_WIN_SYNC</span></span>|  
|<span data-ttu-id="11041-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="11041-115">Message Text</span></span>|<span data-ttu-id="11041-116">La synchronisation des mots de passe à partir de Windows n'est pas autorisée.</span><span class="sxs-lookup"><span data-stu-id="11041-116">Password sync from Windows is not allowed.</span></span> <span data-ttu-id="11041-117">Vérifiez les indicateurs globaux.%r</span><span class="sxs-lookup"><span data-stu-id="11041-117">Check the global flags.%r</span></span><br /><br /> <span data-ttu-id="11041-118">ID de suivi : %1 %r</span><span class="sxs-lookup"><span data-stu-id="11041-118">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="11041-119">Utilisateur client : %2</span><span class="sxs-lookup"><span data-stu-id="11041-119">Client User: %2</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="11041-120">Explication</span><span class="sxs-lookup"><span data-stu-id="11041-120">Explanation</span></span>  
 <span data-ttu-id="11041-121">Cet événement d'avertissement indique que la synchronisation des mots de passe est demandée par Windows et qu'aucun des indicateurs globaux n'est défini.</span><span class="sxs-lookup"><span data-stu-id="11041-121">This Warning event indicates that password sync is requested by Windows and neither of the global flags is set.</span></span> <span data-ttu-id="11041-122">Il y a deux indicateurs. L'un deux autorise l'envoi des mots de passe aux systèmes externes (SSO_FLAG_FULL_SYNC_FROM_WINDOWS_TO_EXTERNAL), tandis que l'autre autorise la réception des mots de passe à partir de systèmes externes (SSO_FLAG_PARTIAL_SYNC_FROM_EXTERNAL_TO_DB).</span><span class="sxs-lookup"><span data-stu-id="11041-122">There are two flags, one that allows sending of password to external system: SSO_FLAG_FULL_SYNC_FROM_WINDOWS_TO_EXTERNAL and another that allows receiving of passwords from external systems SSO_FLAG_PARTIAL_SYNC_FROM_EXTERNAL_TO_DB.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="11041-123">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="11041-123">User Action</span></span>  
 <span data-ttu-id="11041-124">Pour résoudre cet avertissement, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="11041-124">To resolve this warning, do the following:</span></span>  
  
-   <span data-ttu-id="11041-125">Utilisez le composant logiciel enfichable de la console MMC d’administration SSO, (système &#124; Propriétés &#124; Options) ou l’outil de ligne de commande `ssomanage –enable winsync/extsync` pour activer les indicateurs globaux.</span><span class="sxs-lookup"><span data-stu-id="11041-125">Use the SSO Admin MMC Snap-In, (System &#124; Properties &#124; Options) or command line tool  `ssomanage –enable winsync/extsync` to enable the global flags.</span></span>  
  
## <a name="more-info"></a><span data-ttu-id="11041-126">En savoir plus</span><span class="sxs-lookup"><span data-stu-id="11041-126">More info</span></span>
  
-   <span data-ttu-id="11041-127">**Indicateurs l’authentification unique de l’entreprise**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="11041-127">**Enterprise Single Sign-On Flags** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>
  
-   [<span data-ttu-id="11041-128">Comment administrer la synchronisation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="11041-128">How to Administer Password Synchronization</span></span>](../core/how-to-administer-password-synchronization.md)