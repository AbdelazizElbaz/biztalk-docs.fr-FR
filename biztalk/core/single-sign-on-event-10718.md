---
title: "Single Sign-On : Événement 10718 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: de075c59-8396-48d1-be55-79303f83f984
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5b4bf86f4db59033b1ee4202c739ffeda43a587e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10718"></a><span data-ttu-id="1fba8-102">Single Sign-On : Événement 10718</span><span class="sxs-lookup"><span data-stu-id="1fba8-102">Single Sign-On: Event 10718</span></span>
## <a name="details"></a><span data-ttu-id="1fba8-103">Détails</span><span class="sxs-lookup"><span data-stu-id="1fba8-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1fba8-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="1fba8-104">Product Name</span></span>|<span data-ttu-id="1fba8-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="1fba8-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="1fba8-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="1fba8-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="1fba8-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="1fba8-107">Event ID</span></span>|<span data-ttu-id="1fba8-108">10718</span><span class="sxs-lookup"><span data-stu-id="1fba8-108">10718</span></span>|  
|<span data-ttu-id="1fba8-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="1fba8-109">Event Source</span></span>|<span data-ttu-id="1fba8-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="1fba8-110">ENTSSO</span></span>|  
|<span data-ttu-id="1fba8-111">Composant</span><span class="sxs-lookup"><span data-stu-id="1fba8-111">Component</span></span>|<span data-ttu-id="1fba8-112">N\A</span><span class="sxs-lookup"><span data-stu-id="1fba8-112">N\A</span></span>|  
|<span data-ttu-id="1fba8-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="1fba8-113">Symbolic Name</span></span>|<span data-ttu-id="1fba8-114">SSO_ERROR_REPLAY_INCORRECT_ADAPTER</span><span class="sxs-lookup"><span data-stu-id="1fba8-114">SSO_ERROR_REPLAY_INCORRECT_ADAPTER</span></span>|  
|<span data-ttu-id="1fba8-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="1fba8-115">Message Text</span></span>|<span data-ttu-id="1fba8-116">Des données endommagées ont été détectées dans le fichier de reprise ou de progression.%r</span><span class="sxs-lookup"><span data-stu-id="1fba8-116">Corruption was detected in the replay or progress file.%r</span></span><br /><br /> <span data-ttu-id="1fba8-117">Nom du fichier : %1 %r</span><span class="sxs-lookup"><span data-stu-id="1fba8-117">File Name: %1%r</span></span><br /><br /> <span data-ttu-id="1fba8-118">Nom de l’adaptateur supprimé : %2 %r</span><span class="sxs-lookup"><span data-stu-id="1fba8-118">Clear Adapter Name: %2%r</span></span><br /><br /> <span data-ttu-id="1fba8-119">Déchiffrer le nom de l’adaptateur : %3</span><span class="sxs-lookup"><span data-stu-id="1fba8-119">Decrypted Adapter Name: %3</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="1fba8-120">Explication</span><span class="sxs-lookup"><span data-stu-id="1fba8-120">Explanation</span></span>  
 <span data-ttu-id="1fba8-121">Cette erreur indique que des données endommagées ont été détectées dans le fichier de reprise ou de progression.</span><span class="sxs-lookup"><span data-stu-id="1fba8-121">This Error event indicates that corruption was detected in the replay or progress file.</span></span>  
  
 <span data-ttu-id="1fba8-122">Les fichiers de reprise sont stockés pour un adaptateur de synchronisation de mot de passe spécifique, de sorte qu'ils puissent être lus comme s'il s'agissait de cet adaptateur.</span><span class="sxs-lookup"><span data-stu-id="1fba8-122">A replay file is stored for a particular password sync adapter so it can be played back as that particular adapter.</span></span> <span data-ttu-id="1fba8-123">Le nom de l'adaptateur est à la fois stocké en texte clair et sous une forme chiffrée.</span><span class="sxs-lookup"><span data-stu-id="1fba8-123">The adapter name is stored in both clear and encrypted forms.</span></span> <span data-ttu-id="1fba8-124">Ce message indique que lorsque le fichier de reprise a été déchiffré en vue d'être lu, le nom de l'adaptateur déchiffré ne correspondait pas au nom de l'adaptateur.</span><span class="sxs-lookup"><span data-stu-id="1fba8-124">This message indicates that when the replay file was decrypted for playback the decrypted adapter name did not match the adapter name.</span></span> <span data-ttu-id="1fba8-125">Cela peut indiquer que le fichier de reprise possède des données endommagées ou qu'il a été falsifié.</span><span class="sxs-lookup"><span data-stu-id="1fba8-125">This can suggest that there has been some corruption or possible tampering with the replay file.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="1fba8-126">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="1fba8-126">User Action</span></span>  
 <span data-ttu-id="1fba8-127">Pour résoudre cette erreur, procédez de l'une des manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="1fba8-127">To resolve this error, do one or more of the following:</span></span>  
  
-   <span data-ttu-id="1fba8-128">Déterminez la raison pour laquelle le contenu du fichier de reprise est susceptible d'avoir été modifié et vérifiez s'il existe un fichier de sauvegarde.</span><span class="sxs-lookup"><span data-stu-id="1fba8-128">Determine why the contents of the replay file might have been modified, see if a backup exists.</span></span>  
  
-   <span data-ttu-id="1fba8-129">Vérifiez si le secret principal du système SSO a été modifié si le compte de service SSO a été modifié. Cela peut en effet avoir une incidence sur le comportement de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="1fba8-129">Check if the SSO master secret was changed or the SSO service account was changed, this could affect encryption behavior.</span></span>  
  
-   <span data-ttu-id="1fba8-130">Supprimez le fichier de reprise.</span><span class="sxs-lookup"><span data-stu-id="1fba8-130">Delete the replay file.</span></span>  
  
 <span data-ttu-id="1fba8-131">Pour plus d'informations, consultez les ressources ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="1fba8-131">For more information, see the following resources:</span></span>  
  
-   [<span data-ttu-id="1fba8-132">Comment configurer la synchronisation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="1fba8-132">How to Configure Password Synchronization</span></span>](../core/how-to-configure-password-synchronization.md)  
  
-   [<span data-ttu-id="1fba8-133">Synchronisation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="1fba8-133">Password Synchronization</span></span>](../core/password-synchronization2.md)