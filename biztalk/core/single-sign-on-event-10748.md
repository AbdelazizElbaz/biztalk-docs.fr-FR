---
title: "Single Sign-On : Événement 10748 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6b4b18ea-6565-4c0b-89f8-30a8c67601ba
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7d83f0bfec0137e0788b55ca6aa5857f3dcfcc50
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10748"></a><span data-ttu-id="62a2c-102">Single Sign-On : Événement 10748</span><span class="sxs-lookup"><span data-stu-id="62a2c-102">Single Sign-On: Event 10748</span></span>
## <a name="details"></a><span data-ttu-id="62a2c-103">Détails</span><span class="sxs-lookup"><span data-stu-id="62a2c-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="62a2c-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="62a2c-104">Product Name</span></span>|<span data-ttu-id="62a2c-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="62a2c-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="62a2c-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="62a2c-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="62a2c-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="62a2c-107">Event ID</span></span>|<span data-ttu-id="62a2c-108">10748</span><span class="sxs-lookup"><span data-stu-id="62a2c-108">10748</span></span>|  
|<span data-ttu-id="62a2c-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="62a2c-109">Event Source</span></span>|<span data-ttu-id="62a2c-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="62a2c-110">ENTSSO</span></span>|  
|<span data-ttu-id="62a2c-111">Composant</span><span class="sxs-lookup"><span data-stu-id="62a2c-111">Component</span></span>|<span data-ttu-id="62a2c-112">N\A</span><span class="sxs-lookup"><span data-stu-id="62a2c-112">N\A</span></span>|  
|<span data-ttu-id="62a2c-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="62a2c-113">Symbolic Name</span></span>|<span data-ttu-id="62a2c-114">SSO_WARN_PS_ADAPTER_NOT_RUNNING</span><span class="sxs-lookup"><span data-stu-id="62a2c-114">SSO_WARN_PS_ADAPTER_NOT_RUNNING</span></span>|  
|<span data-ttu-id="62a2c-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="62a2c-115">Message Text</span></span>|<span data-ttu-id="62a2c-116">Impossible de contacter l'adaptateur de destination.</span><span class="sxs-lookup"><span data-stu-id="62a2c-116">Could not contact the destination adapter.</span></span><br /><br /> <span data-ttu-id="62a2c-117">Il se peut qu'il ne soit pas en cours d'exécution ou initialisé.%r</span><span class="sxs-lookup"><span data-stu-id="62a2c-117">It may not be running or initialized.%r</span></span><br /><br /> <span data-ttu-id="62a2c-118">ID de suivi : %1 %r</span><span class="sxs-lookup"><span data-stu-id="62a2c-118">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="62a2c-119">Carte : %2 %r</span><span class="sxs-lookup"><span data-stu-id="62a2c-119">Adapter: %2%r</span></span><br /><br /> <span data-ttu-id="62a2c-120">Nom du serveur SSO : %3 %r</span><span class="sxs-lookup"><span data-stu-id="62a2c-120">SSO Server Name: %3%r</span></span><br /><br /> <span data-ttu-id="62a2c-121">Code d’erreur : %4</span><span class="sxs-lookup"><span data-stu-id="62a2c-121">Error Code: %4</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="62a2c-122">Explication</span><span class="sxs-lookup"><span data-stu-id="62a2c-122">Explanation</span></span>  
 <span data-ttu-id="62a2c-123">Cet événement d'avertissement indique que la synchronisation des mots de passe n'a pas pu contacter l'adaptateur de synchronisation de mot de passe spécifié.</span><span class="sxs-lookup"><span data-stu-id="62a2c-123">This Warning event indicates that Password Synchronization could not contact the specified password sync adapter.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="62a2c-124">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="62a2c-124">User Action</span></span>  
 <span data-ttu-id="62a2c-125">Pour résoudre cet avertissement, effectuez l'une ou plusieurs des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="62a2c-125">To resolve this warning, do one or more of the following:</span></span>  
  
-   <span data-ttu-id="62a2c-126">Vérifiez l'adaptateur externe.</span><span class="sxs-lookup"><span data-stu-id="62a2c-126">Check the external adapter.</span></span>  
  
-   <span data-ttu-id="62a2c-127">Utilisez le composant logiciel enfichable MMC ou les outils de ligne de commande pour activer l'adaptateur.</span><span class="sxs-lookup"><span data-stu-id="62a2c-127">Use the MMC Snap-In or command line tools to enable the adapter.</span></span>  
  
-   <span data-ttu-id="62a2c-128">Consultez les journaux des événements de l'application et du système relatifs aux erreurs associées.</span><span class="sxs-lookup"><span data-stu-id="62a2c-128">Check the system and application event logs for associated errors.</span></span>  
  
 <span data-ttu-id="62a2c-129">Pour plus d'informations, consultez les ressources ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="62a2c-129">For more information, see the following resources:</span></span>  
  
-   [<span data-ttu-id="62a2c-130">Comment administrer la synchronisation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="62a2c-130">How to Administer Password Synchronization</span></span>](../core/how-to-administer-password-synchronization.md)