---
title: "Single Sign-On : Événement 10855 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ba244f8e-bc61-475f-913c-475ebf1c69ee
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 89bbdb3c004dc7533be9b7f6371ec69b67bde532
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10855"></a><span data-ttu-id="24661-102">Single Sign-On : Événement 10855</span><span class="sxs-lookup"><span data-stu-id="24661-102">Single Sign-On: Event 10855</span></span>
|||  
|-|-|  
|<span data-ttu-id="24661-103">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="24661-103">Product Name</span></span>|<span data-ttu-id="24661-104">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="24661-104">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="24661-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="24661-105">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="24661-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="24661-106">Event ID</span></span>|<span data-ttu-id="24661-107">10855</span><span class="sxs-lookup"><span data-stu-id="24661-107">10855</span></span>|  
|<span data-ttu-id="24661-108">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="24661-108">Event Source</span></span>|<span data-ttu-id="24661-109">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="24661-109">ENTSSO</span></span>|  
|<span data-ttu-id="24661-110">Composant</span><span class="sxs-lookup"><span data-stu-id="24661-110">Component</span></span>|<span data-ttu-id="24661-111">Néant</span><span class="sxs-lookup"><span data-stu-id="24661-111">N/A</span></span>|  
|<span data-ttu-id="24661-112">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="24661-112">Symbolic Name</span></span>|<span data-ttu-id="24661-113">ENTSSO_E_PASSWORD_FILTER_FAILED</span><span class="sxs-lookup"><span data-stu-id="24661-113">ENTSSO_E_PASSWORD_FILTER_FAILED</span></span>|  
|<span data-ttu-id="24661-114">Texte du message</span><span class="sxs-lookup"><span data-stu-id="24661-114">Message Text</span></span>|<span data-ttu-id="24661-115">Les informations d'identification ne peuvent pas être renvoyées car le filtre de mots de passe a échoué.</span><span class="sxs-lookup"><span data-stu-id="24661-115">The credentials cannot be returned because the password filter failed.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="24661-116">Explication</span><span class="sxs-lookup"><span data-stu-id="24661-116">Explanation</span></span>  
 <span data-ttu-id="24661-117">Le filtre de mots de passe n'est pas valide.</span><span class="sxs-lookup"><span data-stu-id="24661-117">The password filter is not valid.</span></span> <span data-ttu-id="24661-118">La cause la plus probable est que le filtre a été créé manuellement, ce qui n'est pas recommandé.</span><span class="sxs-lookup"><span data-stu-id="24661-118">The most likely cause of this is that the filter was created manually, which is not recommended.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="24661-119">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="24661-119">User Action</span></span>  
 <span data-ttu-id="24661-120">Recréez le filtre de mots de passe par l'intermédiaire de l'Assistant Créer un filtre.</span><span class="sxs-lookup"><span data-stu-id="24661-120">Create the password filter again using the Create Filter wizard.</span></span>