---
title: "Single Sign-On : Événement 10561 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 770e6fc1-0854-4555-8f2a-5f199e3aaca7
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b5148633c7fffabe0ef4bb4789fe4ded58336c10
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10561"></a><span data-ttu-id="35f63-102">Single Sign-On : Événement 10561</span><span class="sxs-lookup"><span data-stu-id="35f63-102">Single Sign-On: Event 10561</span></span>
## <a name="details"></a><span data-ttu-id="35f63-103">Détails</span><span class="sxs-lookup"><span data-stu-id="35f63-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="35f63-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="35f63-104">Product Name</span></span>|<span data-ttu-id="35f63-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="35f63-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="35f63-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="35f63-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="35f63-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="35f63-107">Event ID</span></span>|<span data-ttu-id="35f63-108">10561</span><span class="sxs-lookup"><span data-stu-id="35f63-108">10561</span></span>|  
|<span data-ttu-id="35f63-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="35f63-109">Event Source</span></span>|<span data-ttu-id="35f63-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="35f63-110">ENTSSO</span></span>|  
|<span data-ttu-id="35f63-111">Composant</span><span class="sxs-lookup"><span data-stu-id="35f63-111">Component</span></span>|<span data-ttu-id="35f63-112">Néant</span><span class="sxs-lookup"><span data-stu-id="35f63-112">N/A</span></span>|  
|<span data-ttu-id="35f63-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="35f63-113">Symbolic Name</span></span>|<span data-ttu-id="35f63-114">SSO_ERROR_BACKUP_FAILED_MEDIA</span><span class="sxs-lookup"><span data-stu-id="35f63-114">SSO_ERROR_BACKUP_FAILED_MEDIA</span></span>|  
|<span data-ttu-id="35f63-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="35f63-115">Message Text</span></span>|<span data-ttu-id="35f63-116">Le fichier spécifié pour la sauvegarde des secrets principaux doit figurer dans un système de fichiers NTFS ou sur un média amovible.%r</span><span class="sxs-lookup"><span data-stu-id="35f63-116">The file specified for backup of the master secrets must be on an NTFS file system or removable media.%r</span></span><br /><br /> <span data-ttu-id="35f63-117">Nom du fichier : %1 %r</span><span class="sxs-lookup"><span data-stu-id="35f63-117">File Name: %1%r</span></span><br /><br /> <span data-ttu-id="35f63-118">L’utilisateur client : %2 %r</span><span class="sxs-lookup"><span data-stu-id="35f63-118">Client User: %2%r</span></span><br /><br /> <span data-ttu-id="35f63-119">Ordinateur client : %3 %r</span><span class="sxs-lookup"><span data-stu-id="35f63-119">Client Computer: %3%r</span></span><br /><br /> <span data-ttu-id="35f63-120">Code d’erreur : %4</span><span class="sxs-lookup"><span data-stu-id="35f63-120">Error Code: %4</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="35f63-121">Explication</span><span class="sxs-lookup"><span data-stu-id="35f63-121">Explanation</span></span>  
 <span data-ttu-id="35f63-122">Une tentative de sauvegarde a été effectuée à l'aide d'un média non valide, tel qu'un fichier FAT.</span><span class="sxs-lookup"><span data-stu-id="35f63-122">A backup was attempted using an invalid media, such as a FAT file.</span></span> <span data-ttu-id="35f63-123">Le fichier spécifié pour la sauvegarde des secrets principaux doit figurer dans un système de fichiers NTFS ou sur un média amovible.</span><span class="sxs-lookup"><span data-stu-id="35f63-123">The file specified for backup of the master secrets must be on an NTFS file system or removable media.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="35f63-124">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="35f63-124">User Action</span></span>  
 <span data-ttu-id="35f63-125">Vérifiez le format du média et assurez-vous qu'il s'agit d'un système de fichiers NTFS ou d'un média amovible.</span><span class="sxs-lookup"><span data-stu-id="35f63-125">Check the media format and make sure it is NTFS or removable.</span></span>