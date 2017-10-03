---
title: "Single Sign-On : Événement 10705 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 81456bdd-dfd8-4483-aa76-5ec72350cc70
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 41db0b3aeba4e3c71da3193af807f881bb4ae586
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10705"></a><span data-ttu-id="193c5-102">Single Sign-On : Événement 10705</span><span class="sxs-lookup"><span data-stu-id="193c5-102">Single Sign-On: Event 10705</span></span>
## <a name="details"></a><span data-ttu-id="193c5-103">Détails</span><span class="sxs-lookup"><span data-stu-id="193c5-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="193c5-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="193c5-104">Product Name</span></span>|<span data-ttu-id="193c5-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="193c5-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="193c5-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="193c5-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="193c5-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="193c5-107">Event ID</span></span>|<span data-ttu-id="193c5-108">10705</span><span class="sxs-lookup"><span data-stu-id="193c5-108">10705</span></span>|  
|<span data-ttu-id="193c5-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="193c5-109">Event Source</span></span>|<span data-ttu-id="193c5-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="193c5-110">ENTSSO</span></span>|  
|<span data-ttu-id="193c5-111">Composant</span><span class="sxs-lookup"><span data-stu-id="193c5-111">Component</span></span>|<span data-ttu-id="193c5-112">N\A</span><span class="sxs-lookup"><span data-stu-id="193c5-112">N\A</span></span>|  
|<span data-ttu-id="193c5-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="193c5-113">Symbolic Name</span></span>|<span data-ttu-id="193c5-114">SSO_WARN_PS_NOT_ADAPTER</span><span class="sxs-lookup"><span data-stu-id="193c5-114">SSO_WARN_PS_NOT_ADAPTER</span></span>|  
|<span data-ttu-id="193c5-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="193c5-115">Message Text</span></span>|<span data-ttu-id="193c5-116">L'adaptateur spécifié n'est pas une application d'adaptateur.</span><span class="sxs-lookup"><span data-stu-id="193c5-116">The specified adapter is not an adapter application.</span></span> <span data-ttu-id="193c5-117">Vérifiez le type de l'application.%r</span><span class="sxs-lookup"><span data-stu-id="193c5-117">Check the application type.%r</span></span><br /><br /> <span data-ttu-id="193c5-118">Adaptateur : %1</span><span class="sxs-lookup"><span data-stu-id="193c5-118">Adapter: %1</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="193c5-119">Explication</span><span class="sxs-lookup"><span data-stu-id="193c5-119">Explanation</span></span>  
 <span data-ttu-id="193c5-120">Cet événement d'informations indique que l'adaptateur spécifié n'est pas une application d'adaptateur.</span><span class="sxs-lookup"><span data-stu-id="193c5-120">This Warning event indicates that the specified adapter is not an adapter application.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="193c5-121">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="193c5-121">User Action</span></span>  
 <span data-ttu-id="193c5-122">Pour résoudre cet avertissement, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="193c5-122">To resolve this warning, do the following:</span></span>  
  
-   <span data-ttu-id="193c5-123">Utilisez le composant logiciel enfichable MMC d'administration de l'authentification unique, cliquez avec le bouton droit sur l'adaptateur spécifié, puis cliquez sur Propriétés pour déterminer le type d'application ou utilisez les outils de ligne de commande ssops -list et ssops -display pour déterminer le type de l'application.</span><span class="sxs-lookup"><span data-stu-id="193c5-123">Use the SSO Admin MMC Snap-In, right click the specified adapter, and then click Properties to determine the application type or use the command line tool  ssops -list and ssops -display to determine the application type.</span></span>  
  
-   <span data-ttu-id="193c5-124">Utilisez le composant logiciel enfichable MMC d'administration de l'authentification unique ou ssops -addapp pour définir l'application de l'adaptateur.</span><span class="sxs-lookup"><span data-stu-id="193c5-124">Use the SSO Admin MMC Snap-In or ssops -addapp to set the adapter application.</span></span>  
  
 <span data-ttu-id="193c5-125">Pour plus d'informations, consultez les ressources ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="193c5-125">For more information, see the following resources:</span></span>  
  
-   [<span data-ttu-id="193c5-126">Comment administrer la synchronisation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="193c5-126">How to Administer Password Synchronization</span></span>](../core/how-to-administer-password-synchronization.md)