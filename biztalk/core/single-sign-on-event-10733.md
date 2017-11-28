---
title: "Single Sign-On : Événement 10733 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 01520ae4-f692-4697-82ce-53a8a63b5bd9
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1387d7c853bba91bea429470d9a615e065a6e8dd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10733"></a><span data-ttu-id="02ef3-102">Single Sign-On : Événement 10733</span><span class="sxs-lookup"><span data-stu-id="02ef3-102">Single Sign-On: Event 10733</span></span>
## <a name="details"></a><span data-ttu-id="02ef3-103">Détails</span><span class="sxs-lookup"><span data-stu-id="02ef3-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="02ef3-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="02ef3-104">Product Name</span></span>|<span data-ttu-id="02ef3-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="02ef3-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="02ef3-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="02ef3-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="02ef3-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="02ef3-107">Event ID</span></span>|<span data-ttu-id="02ef3-108">10733</span><span class="sxs-lookup"><span data-stu-id="02ef3-108">10733</span></span>|  
|<span data-ttu-id="02ef3-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="02ef3-109">Event Source</span></span>|<span data-ttu-id="02ef3-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="02ef3-110">ENTSSO</span></span>|  
|<span data-ttu-id="02ef3-111">Composant</span><span class="sxs-lookup"><span data-stu-id="02ef3-111">Component</span></span>|<span data-ttu-id="02ef3-112">N\A</span><span class="sxs-lookup"><span data-stu-id="02ef3-112">N\A</span></span>|  
|<span data-ttu-id="02ef3-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="02ef3-113">Symbolic Name</span></span>|<span data-ttu-id="02ef3-114">SSO_WARN_PS_SET_WINDOWS_PASSWORD</span><span class="sxs-lookup"><span data-stu-id="02ef3-114">SSO_WARN_PS_SET_WINDOWS_PASSWORD</span></span>|  
|<span data-ttu-id="02ef3-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="02ef3-115">Message Text</span></span>|<span data-ttu-id="02ef3-116">Échec de la mise à jour du mot de passe Windows dans la base de données SSO.%r</span><span class="sxs-lookup"><span data-stu-id="02ef3-116">Failed to update the Windows password in the SSO database.%r</span></span><br /><br /> <span data-ttu-id="02ef3-117">ID de suivi : %1 %r</span><span class="sxs-lookup"><span data-stu-id="02ef3-117">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="02ef3-118">Le compte Windows : %2\\%3 %r</span><span class="sxs-lookup"><span data-stu-id="02ef3-118">Windows Account: %2\\%3%r</span></span><br /><br /> <span data-ttu-id="02ef3-119">Code d’erreur : %4</span><span class="sxs-lookup"><span data-stu-id="02ef3-119">Error Code: %4</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="02ef3-120">Explication</span><span class="sxs-lookup"><span data-stu-id="02ef3-120">Explanation</span></span>  
 <span data-ttu-id="02ef3-121">Cet événement d'avertissement indique que la synchronisation des mots de passe n'a pas pu mettre à jour le mot de passe du compte Windows spécifié dans la base de données SSO.</span><span class="sxs-lookup"><span data-stu-id="02ef3-121">This Warning event indicates that Password Sync failed to update the specified Windows account password in the SSO database.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="02ef3-122">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="02ef3-122">User Action</span></span>  
 <span data-ttu-id="02ef3-123">Pour résoudre cet avertissement, effectuez l'une ou plusieurs des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="02ef3-123">To resolve this warning, do one or more of the following:</span></span>  
  
-   <span data-ttu-id="02ef3-124">Consultez les journaux des événements de l'application et du système relatifs aux erreurs associées.</span><span class="sxs-lookup"><span data-stu-id="02ef3-124">Check the system and application event logs for associated errors.</span></span>  
  
-   <span data-ttu-id="02ef3-125">Vérifiez que le mot de passe du compte spécifié est un mot de passe Windows valide.</span><span class="sxs-lookup"><span data-stu-id="02ef3-125">Verify the password for the specified account is a valid Windows password.</span></span>  
  
 <span data-ttu-id="02ef3-126">Pour plus d'informations, consultez les ressources ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="02ef3-126">For more information, see the following resources:</span></span>  
  
-   [<span data-ttu-id="02ef3-127">Synchronisation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="02ef3-127">Password Synchronization</span></span>](../core/password-synchronization2.md)