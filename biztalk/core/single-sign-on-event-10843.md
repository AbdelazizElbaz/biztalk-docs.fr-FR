---
title: "Single Sign-On : Événement 10843 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 847e464e-5733-4703-905f-d44a4c4f5cc3
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bd86a39d515858e1cda09317ba6139bc67c95ed4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10843"></a><span data-ttu-id="cc3cc-102">Single Sign-On : Événement 10843</span><span class="sxs-lookup"><span data-stu-id="cc3cc-102">Single Sign-On: Event 10843</span></span>
## <a name="details"></a><span data-ttu-id="cc3cc-103">Détails</span><span class="sxs-lookup"><span data-stu-id="cc3cc-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="cc3cc-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="cc3cc-104">Product Name</span></span>|<span data-ttu-id="cc3cc-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="cc3cc-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="cc3cc-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="cc3cc-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="cc3cc-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="cc3cc-107">Event ID</span></span>|<span data-ttu-id="cc3cc-108">10843</span><span class="sxs-lookup"><span data-stu-id="cc3cc-108">10843</span></span>|  
|<span data-ttu-id="cc3cc-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="cc3cc-109">Event Source</span></span>|<span data-ttu-id="cc3cc-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="cc3cc-110">ENTSSO</span></span>|  
|<span data-ttu-id="cc3cc-111">Composant</span><span class="sxs-lookup"><span data-stu-id="cc3cc-111">Component</span></span>|<span data-ttu-id="cc3cc-112">Néant</span><span class="sxs-lookup"><span data-stu-id="cc3cc-112">N/A</span></span>|  
|<span data-ttu-id="cc3cc-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="cc3cc-113">Symbolic Name</span></span>|<span data-ttu-id="cc3cc-114">ENTSSO_E_NO_SECRET2</span><span class="sxs-lookup"><span data-stu-id="cc3cc-114">ENTSSO_E_NO_SECRET2</span></span>|  
|<span data-ttu-id="cc3cc-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="cc3cc-115">Message Text</span></span>|<span data-ttu-id="cc3cc-116">Impossible d'effectuer le chiffrement ou le déchiffrement car le secret n'est pas disponible depuis le serveur de secret principal.</span><span class="sxs-lookup"><span data-stu-id="cc3cc-116">Cannot perform encryption or decryption because the secret is not available from the master secret server.</span></span> <span data-ttu-id="cc3cc-117">Recherchez les erreurs associées dans le journal des événements (sur l'ordinateur « %1 »).</span><span class="sxs-lookup"><span data-stu-id="cc3cc-117">See the event log (on computer ‘%1’) for related errors.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="cc3cc-118">Explication</span><span class="sxs-lookup"><span data-stu-id="cc3cc-118">Explanation</span></span>  
 <span data-ttu-id="cc3cc-119">Accès refusé.</span><span class="sxs-lookup"><span data-stu-id="cc3cc-119">Access is denied.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="cc3cc-120">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="cc3cc-120">User Action</span></span>  
 <span data-ttu-id="cc3cc-121">Le serveur de secret principal est hors ligne ou n'inclut pas le secret principal requis.</span><span class="sxs-lookup"><span data-stu-id="cc3cc-121">Either the master secret server is off-line, or the master secret server is missing the required master secret.</span></span> <span data-ttu-id="cc3cc-122">Recherchez les erreurs associées dans le journal des événements sur l'ordinateur spécifié.</span><span class="sxs-lookup"><span data-stu-id="cc3cc-122">See the event log on the specified computer for related errors.</span></span>