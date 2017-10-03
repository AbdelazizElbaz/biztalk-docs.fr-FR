---
title: "Single Sign-On : Événement 10658 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c5bee12d-502b-4fee-bc84-25807eb0e48e
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c9594f2462422190c243d98c165ead37898e33f2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10658"></a><span data-ttu-id="5b096-102">Single Sign-On : Événement 10658</span><span class="sxs-lookup"><span data-stu-id="5b096-102">Single Sign-On: Event 10658</span></span>
## <a name="details"></a><span data-ttu-id="5b096-103">Détails</span><span class="sxs-lookup"><span data-stu-id="5b096-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5b096-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="5b096-104">Product Name</span></span>|<span data-ttu-id="5b096-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="5b096-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="5b096-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="5b096-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="5b096-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="5b096-107">Event ID</span></span>|<span data-ttu-id="5b096-108">10658</span><span class="sxs-lookup"><span data-stu-id="5b096-108">10658</span></span>|  
|<span data-ttu-id="5b096-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="5b096-109">Event Source</span></span>|<span data-ttu-id="5b096-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="5b096-110">ENTSSO</span></span>|  
|<span data-ttu-id="5b096-111">Composant</span><span class="sxs-lookup"><span data-stu-id="5b096-111">Component</span></span>|<span data-ttu-id="5b096-112">N\A</span><span class="sxs-lookup"><span data-stu-id="5b096-112">N\A</span></span>|  
|<span data-ttu-id="5b096-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="5b096-113">Symbolic Name</span></span>|<span data-ttu-id="5b096-114">SSO_ERROR_PASSWORD_SYNC_ADAPTERS_START_FAILED</span><span class="sxs-lookup"><span data-stu-id="5b096-114">SSO_ERROR_PASSWORD_SYNC_ADAPTERS_START_FAILED</span></span>|  
|<span data-ttu-id="5b096-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="5b096-115">Message Text</span></span>|<span data-ttu-id="5b096-116">Échec du démarrage de la synchronisation des mots de passe pour les cartes réseau.%r</span><span class="sxs-lookup"><span data-stu-id="5b096-116">Password sync for external adapters failed to start.%r</span></span><br /><br /> <span data-ttu-id="5b096-117">Code d’erreur : %1</span><span class="sxs-lookup"><span data-stu-id="5b096-117">Error Code: %1</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="5b096-118">Explication</span><span class="sxs-lookup"><span data-stu-id="5b096-118">Explanation</span></span>  
 <span data-ttu-id="5b096-119">Cet événement de type erreur indique que la synchronisation des mots de passe pour les cartes réseau n'a pas démarré.</span><span class="sxs-lookup"><span data-stu-id="5b096-119">This Error event indicates that password sync for external adapters failed to start.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="5b096-120">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="5b096-120">User Action</span></span>  
 <span data-ttu-id="5b096-121">Pour résoudre cette erreur, procédez de l'une des manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="5b096-121">To resolve this error, do one or more of the following:</span></span>  
  
-   <span data-ttu-id="5b096-122">Consultez les journaux des événements de l'application et du système pour connaître les événements associés.</span><span class="sxs-lookup"><span data-stu-id="5b096-122">Check the application and system event logs for associated events.</span></span>  
  
-   <span data-ttu-id="5b096-123">Vérifiez les propriétés de la configuration de la carte.</span><span class="sxs-lookup"><span data-stu-id="5b096-123">Verify adapter configuration properties.</span></span>  

## <a name="more-info"></a><span data-ttu-id="5b096-124">En savoir plus</span><span class="sxs-lookup"><span data-stu-id="5b096-124">More info</span></span>  
  
-   [<span data-ttu-id="5b096-125">Comment administrer la synchronisation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="5b096-125">How to Administer Password Synchronization</span></span>](../core/how-to-administer-password-synchronization.md)  
  
-   <span data-ttu-id="5b096-126">**Aide de l’interface utilisateur de l’authentification unique entreprise**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="5b096-126">**Enterprise Single Sign-On UI Help** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>