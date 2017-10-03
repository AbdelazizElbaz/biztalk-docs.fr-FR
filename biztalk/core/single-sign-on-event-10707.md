---
title: "Single Sign-On : Événement 10707 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 59629786-4f98-4861-aba3-153670bafc12
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 81f4d484aa7a69f23cb66a921f1c630db9fcf790
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10707"></a><span data-ttu-id="ed57b-102">Single Sign-On : Événement 10707</span><span class="sxs-lookup"><span data-stu-id="ed57b-102">Single Sign-On: Event 10707</span></span>
## <a name="details"></a><span data-ttu-id="ed57b-103">Détails</span><span class="sxs-lookup"><span data-stu-id="ed57b-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ed57b-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="ed57b-104">Product Name</span></span>|<span data-ttu-id="ed57b-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="ed57b-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="ed57b-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="ed57b-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="ed57b-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="ed57b-107">Event ID</span></span>|<span data-ttu-id="ed57b-108">10707</span><span class="sxs-lookup"><span data-stu-id="ed57b-108">10707</span></span>|  
|<span data-ttu-id="ed57b-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="ed57b-109">Event Source</span></span>|<span data-ttu-id="ed57b-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="ed57b-110">ENTSSO</span></span>|  
|<span data-ttu-id="ed57b-111">Composant</span><span class="sxs-lookup"><span data-stu-id="ed57b-111">Component</span></span>|<span data-ttu-id="ed57b-112">N\A</span><span class="sxs-lookup"><span data-stu-id="ed57b-112">N\A</span></span>|  
|<span data-ttu-id="ed57b-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="ed57b-113">Symbolic Name</span></span>|<span data-ttu-id="ed57b-114">SSO_WARN_PS_NO_APP_SYNC</span><span class="sxs-lookup"><span data-stu-id="ed57b-114">SSO_WARN_PS_NO_APP_SYNC</span></span>|  
|<span data-ttu-id="ed57b-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="ed57b-115">Message Text</span></span>|<span data-ttu-id="ed57b-116">Les indicateurs de synchronisation de mot de passe pour cet adaptateur doivent autoriser la synchronisation des mots de passe et correspondre aux indicateurs globaux.</span><span class="sxs-lookup"><span data-stu-id="ed57b-116">Password sync flags for this adapter must allow password sync and must match the global flags.</span></span> <span data-ttu-id="ed57b-117">Vérifiez les indicateurs de l'adaptateur et les indicateurs globaux.%r</span><span class="sxs-lookup"><span data-stu-id="ed57b-117">Check the adapter flags and the global flags.%r</span></span><br /><br /> <span data-ttu-id="ed57b-118">Adaptateur : %1</span><span class="sxs-lookup"><span data-stu-id="ed57b-118">Adapter: %1</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="ed57b-119">Explication</span><span class="sxs-lookup"><span data-stu-id="ed57b-119">Explanation</span></span>  
 <span data-ttu-id="ed57b-120">Cet événement d'avertissement indique que les indicateurs de synchronisation de mot de passe pour cet adaptateur doivent autoriser la synchronisation de mot de passe et correspondre aux indicateurs globaux.</span><span class="sxs-lookup"><span data-stu-id="ed57b-120">This Warning event indicates that password sync flags for this adapter must allow password sync and must match the global flags.</span></span>  
  
 <span data-ttu-id="ed57b-121">La synchronisation de mot de passe pour un adaptateur de synchronisation de mot de passe est contrôlée par deux indicateurs. L'un deux autorise l'envoi des mots de passe aux systèmes externes (SSO_FLAG_FULL_SYNC_FROM_WINDOWS_TO_EXTERNAL), tandis que l'autre autorise la réception des mots de passe à partir de systèmes externes (SSO_FLAG_PARTIAL_SYNC_FROM_EXTERNAL_TO_DB).</span><span class="sxs-lookup"><span data-stu-id="ed57b-121">Password sync for a password sync adapter is controlled by two flags, one allows sending of password to external systems (SSO_FLAG_FULL_SYNC_FROM_WINDOWS_TO_EXTERNAL) and another which allows receiving of passwords from external systems (SSO_FLAG_PARTIAL_SYNC_FROM_EXTERNAL_TO_DB).</span></span> <span data-ttu-id="ed57b-122">Pour une synchronisation de mot de passe correcte, ils doivent être définis pour les « indicateurs globaux » et les indicateurs de l'adaptateur spécifique.</span><span class="sxs-lookup"><span data-stu-id="ed57b-122">For successfull password sync these must be set for both the “global flags” and also for the specific adapter flags.</span></span> <span data-ttu-id="ed57b-123">Cet événement d'avertissement est généré lorsque la synchronisation de mot de passe est demandée par un adaptateur de synchronisation de mot de passe externe et qu'aucun de ces indicateurs n'est défini pour les « indicateurs globaux » et les indicateurs de l'adaptateur.</span><span class="sxs-lookup"><span data-stu-id="ed57b-123">This warning event is issued when password sync is requested by an external password sync adapter and neither of these flags is set for both the “global flags” and the adapter flags.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="ed57b-124">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="ed57b-124">User Action</span></span>  
 <span data-ttu-id="ed57b-125">Pour résoudre cet avertissement, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="ed57b-125">To resolve this warning, do the following:</span></span>  
  
-   <span data-ttu-id="ed57b-126">Utilisez le composant logiciel enfichable MMC d’administration de l’authentification unique (système &#124; Propriétés &#124; Options) ou l’outil de ligne de commande `ssomanage –enable winsync/extsync` pour activer les indicateurs globaux.</span><span class="sxs-lookup"><span data-stu-id="ed57b-126">Use the SSO Admin MMC Snap-In (System &#124; Properties &#124; Options) or command line tool  `ssomanage –enable winsync/extsync` to enable the global flags.</span></span>  
  
## <a name="more-info"></a><span data-ttu-id="ed57b-127">En savoir plus</span><span class="sxs-lookup"><span data-stu-id="ed57b-127">More info</span></span>
  
-   <span data-ttu-id="ed57b-128">**Indicateurs l’authentification unique de l’entreprise**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="ed57b-128">**Enterprise Single Sign-On Flags** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>  
  
-   [<span data-ttu-id="ed57b-129">Comment administrer la synchronisation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="ed57b-129">How to Administer Password Synchronization</span></span>](../core/how-to-administer-password-synchronization.md)