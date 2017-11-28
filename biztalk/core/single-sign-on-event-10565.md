---
title: "Single Sign-On : Événement 10565 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6d279491-dc0d-44c4-a77e-a67498a3481d
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9567421210689d8615cf88e7fbd6493ef5749d02
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10565"></a><span data-ttu-id="a3587-102">Single Sign-On : Événement 10565</span><span class="sxs-lookup"><span data-stu-id="a3587-102">Single Sign-On: Event 10565</span></span>
## <a name="details"></a><span data-ttu-id="a3587-103">Détails</span><span class="sxs-lookup"><span data-stu-id="a3587-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a3587-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="a3587-104">Product Name</span></span>|<span data-ttu-id="a3587-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="a3587-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="a3587-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="a3587-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="a3587-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="a3587-107">Event ID</span></span>|<span data-ttu-id="a3587-108">10565</span><span class="sxs-lookup"><span data-stu-id="a3587-108">10565</span></span>|  
|<span data-ttu-id="a3587-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="a3587-109">Event Source</span></span>|<span data-ttu-id="a3587-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="a3587-110">ENTSSO</span></span>|  
|<span data-ttu-id="a3587-111">Composant</span><span class="sxs-lookup"><span data-stu-id="a3587-111">Component</span></span>|<span data-ttu-id="a3587-112">Néant</span><span class="sxs-lookup"><span data-stu-id="a3587-112">N/A</span></span>|  
|<span data-ttu-id="a3587-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="a3587-113">Symbolic Name</span></span>|<span data-ttu-id="a3587-114">SSO_ERROR_SECRET_VALIDATE_FAILED</span><span class="sxs-lookup"><span data-stu-id="a3587-114">SSO_ERROR_SECRET_VALIDATE_FAILED</span></span>|  
|<span data-ttu-id="a3587-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="a3587-115">Message Text</span></span>|<span data-ttu-id="a3587-116">Le secret n'a pas pu être chargé à partir du Registre.</span><span class="sxs-lookup"><span data-stu-id="a3587-116">The secret could not be loaded from the registry.</span></span> <span data-ttu-id="a3587-117">Il se peut que le compte du service d'authentification unique ait été modifié ou que le secret soit endommagé.</span><span class="sxs-lookup"><span data-stu-id="a3587-117">The service account for the SSO service may have been changed or the secret may be corrupted.</span></span> <span data-ttu-id="a3587-118">Restaurez le secret à partir d'un fichier de sauvegarde.%r</span><span class="sxs-lookup"><span data-stu-id="a3587-118">Restore the secret from a backup file.%r</span></span><br /><br /> <span data-ttu-id="a3587-119">MSID : %1</span><span class="sxs-lookup"><span data-stu-id="a3587-119">MSID: %1</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="a3587-120">Explication</span><span class="sxs-lookup"><span data-stu-id="a3587-120">Explanation</span></span>  
 <span data-ttu-id="a3587-121">Un administrateur du système a probablement modifié le compte du service d'authentification unique, ce qui rend le déchiffrement impossible.</span><span class="sxs-lookup"><span data-stu-id="a3587-121">It is likely that an administrator in the system has changed the SSO Service account, making decryption impossible.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="a3587-122">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="a3587-122">User Action</span></span>  
 <span data-ttu-id="a3587-123">Recherchez la personne qui a modifié le compte du service d'authentification unique, puis restaurez le secret à partir d'un fichier de sauvegarde.</span><span class="sxs-lookup"><span data-stu-id="a3587-123">Find the person who changed the SSO Service account, and then restore the secret from a backup file.</span></span> <span data-ttu-id="a3587-124">Pour plus d’informations sur la restauration de la clé secrète, consultez [gestion du Secret](../core/managing-the-master-secret.md).</span><span class="sxs-lookup"><span data-stu-id="a3587-124">For more information on restoring the secret, see [Managing the Master Secret](../core/managing-the-master-secret.md).</span></span>