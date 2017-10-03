---
title: "Single Sign-On : Événement 10765 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e28fe42e-aa2b-4be4-b757-bc9c5c37526b
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6c0fbc04f4c8fc98a87de87a4cd48529a3ca7e2e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10765"></a><span data-ttu-id="b6e5d-102">Single Sign-On : Événement 10765</span><span class="sxs-lookup"><span data-stu-id="b6e5d-102">Single Sign-On: Event 10765</span></span>
## <a name="details"></a><span data-ttu-id="b6e5d-103">Détails</span><span class="sxs-lookup"><span data-stu-id="b6e5d-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b6e5d-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="b6e5d-104">Product Name</span></span>|<span data-ttu-id="b6e5d-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="b6e5d-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="b6e5d-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="b6e5d-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="b6e5d-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="b6e5d-107">Event ID</span></span>|<span data-ttu-id="b6e5d-108">10765</span><span class="sxs-lookup"><span data-stu-id="b6e5d-108">10765</span></span>|  
|<span data-ttu-id="b6e5d-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="b6e5d-109">Event Source</span></span>|<span data-ttu-id="b6e5d-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="b6e5d-110">ENTSSO</span></span>|  
|<span data-ttu-id="b6e5d-111">Composant</span><span class="sxs-lookup"><span data-stu-id="b6e5d-111">Component</span></span>|<span data-ttu-id="b6e5d-112">Néant</span><span class="sxs-lookup"><span data-stu-id="b6e5d-112">N/A</span></span>|  
|<span data-ttu-id="b6e5d-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="b6e5d-113">Symbolic Name</span></span>|<span data-ttu-id="b6e5d-114">ENTSSO_E_NO_CREDENTIALS</span><span class="sxs-lookup"><span data-stu-id="b6e5d-114">ENTSSO_E_NO_CREDENTIALS</span></span>|  
|<span data-ttu-id="b6e5d-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="b6e5d-115">Message Text</span></span>|<span data-ttu-id="b6e5d-116">Aucune information d'identification n'a été définie pour le mappage.</span><span class="sxs-lookup"><span data-stu-id="b6e5d-116">No credentials have been set for the mapping.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="b6e5d-117">Explication</span><span class="sxs-lookup"><span data-stu-id="b6e5d-117">Explanation</span></span>  
 <span data-ttu-id="b6e5d-118">Vous avez effectué une demande d'obtention des informations d'identification concernant un mappage et le mappage spécifié ne possède aucune information d'identification.</span><span class="sxs-lookup"><span data-stu-id="b6e5d-118">You have requested a GetCredentials on a mapping, and the mapping specified has no credentials.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="b6e5d-119">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="b6e5d-119">User Action</span></span>  
 <span data-ttu-id="b6e5d-120">Utilisez la ligne de commande ou le logiciel enfichable MMC pour définir les informations d'identification relatives au mappage.</span><span class="sxs-lookup"><span data-stu-id="b6e5d-120">Use the command line or the MMC Snap-in to set credentials for the mapping.</span></span>