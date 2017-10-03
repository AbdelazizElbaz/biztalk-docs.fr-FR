---
title: "Single Sign-On : Événement 10564 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e523c97a-608e-4bf4-8747-cfa0cce10acf
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7268b877a59fcd4e993a2c9009d48d73e5db9ac8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10564"></a><span data-ttu-id="f14a9-102">Single Sign-On : Événement 10564</span><span class="sxs-lookup"><span data-stu-id="f14a9-102">Single Sign-On: Event 10564</span></span>
## <a name="details"></a><span data-ttu-id="f14a9-103">Détails</span><span class="sxs-lookup"><span data-stu-id="f14a9-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f14a9-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="f14a9-104">Product Name</span></span>|<span data-ttu-id="f14a9-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="f14a9-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="f14a9-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="f14a9-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="f14a9-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="f14a9-107">Event ID</span></span>|<span data-ttu-id="f14a9-108">10564</span><span class="sxs-lookup"><span data-stu-id="f14a9-108">10564</span></span>|  
|<span data-ttu-id="f14a9-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="f14a9-109">Event Source</span></span>|<span data-ttu-id="f14a9-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="f14a9-110">ENTSSO</span></span>|  
|<span data-ttu-id="f14a9-111">Composant</span><span class="sxs-lookup"><span data-stu-id="f14a9-111">Component</span></span>|<span data-ttu-id="f14a9-112">Néant</span><span class="sxs-lookup"><span data-stu-id="f14a9-112">N/A</span></span>|  
|<span data-ttu-id="f14a9-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="f14a9-113">Symbolic Name</span></span>|<span data-ttu-id="f14a9-114">SSO_ERROR_BACKUP_FILE_INCORRECT_FORMAT</span><span class="sxs-lookup"><span data-stu-id="f14a9-114">SSO_ERROR_BACKUP_FILE_INCORRECT_FORMAT</span></span>|  
|<span data-ttu-id="f14a9-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="f14a9-115">Message Text</span></span>|<span data-ttu-id="f14a9-116">Le format du fichier de sauvegarde est incorrect.</span><span class="sxs-lookup"><span data-stu-id="f14a9-116">The backup file does not have the correct format.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="f14a9-117">Explication</span><span class="sxs-lookup"><span data-stu-id="f14a9-117">Explanation</span></span>  
 <span data-ttu-id="f14a9-118">Le format du fichier de sauvegarde est incorrect.</span><span class="sxs-lookup"><span data-stu-id="f14a9-118">The backup file does not have the correct format.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="f14a9-119">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="f14a9-119">User Action</span></span>  
 <span data-ttu-id="f14a9-120">Vérifiez qu'il s'agit du bon fichier et qu'il figure au bon emplacement.</span><span class="sxs-lookup"><span data-stu-id="f14a9-120">Check that you have the correct file and location.</span></span> <span data-ttu-id="f14a9-121">Vous devez également confirmer qu'aucun autre fichier de ce dossier ne comporte l'extension .BAK, car le système ENTSSO risquerait de les confondre avec le fichier de sauvegarde actuel.</span><span class="sxs-lookup"><span data-stu-id="f14a9-121">You should also confirm that there are no other files in that folder with the .BAK extension, as the ENTSSO system may confuse them with the actual backup file.</span></span>