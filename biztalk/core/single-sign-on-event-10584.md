---
title: "Single Sign-On : Événement 10584 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8af9377d-b4fd-48a6-961a-3629b3db644a
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d08be0100d53f081eb7d8f4faa27d1e7f46f6f46
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10584"></a><span data-ttu-id="26855-102">Single Sign-On : Événement 10584</span><span class="sxs-lookup"><span data-stu-id="26855-102">Single Sign-On: Event 10584</span></span>
## <a name="details"></a><span data-ttu-id="26855-103">Détails</span><span class="sxs-lookup"><span data-stu-id="26855-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="26855-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="26855-104">Product Name</span></span>|<span data-ttu-id="26855-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="26855-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="26855-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="26855-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="26855-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="26855-107">Event ID</span></span>|<span data-ttu-id="26855-108">10584</span><span class="sxs-lookup"><span data-stu-id="26855-108">10584</span></span>|  
|<span data-ttu-id="26855-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="26855-109">Event Source</span></span>|<span data-ttu-id="26855-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="26855-110">ENTSSO</span></span>|  
|<span data-ttu-id="26855-111">Composant</span><span class="sxs-lookup"><span data-stu-id="26855-111">Component</span></span>|<span data-ttu-id="26855-112">Néant</span><span class="sxs-lookup"><span data-stu-id="26855-112">N/A</span></span>|  
|<span data-ttu-id="26855-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="26855-113">Symbolic Name</span></span>|<span data-ttu-id="26855-114">SSO_WARN_NO_IMPERSONATION</span><span class="sxs-lookup"><span data-stu-id="26855-114">SSO_WARN_NO_IMPERSONATION</span></span>|  
|<span data-ttu-id="26855-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="26855-115">Message Text</span></span>|<span data-ttu-id="26855-116">Impossible d'emprunter l'identité du client.%r</span><span class="sxs-lookup"><span data-stu-id="26855-116">Could not impersonate the client.%r</span></span><br /><br /> <span data-ttu-id="26855-117">Code d’erreur : %1</span><span class="sxs-lookup"><span data-stu-id="26855-117">Error Code: %1</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="26855-118">Explication</span><span class="sxs-lookup"><span data-stu-id="26855-118">Explanation</span></span>  
 <span data-ttu-id="26855-119">Le système d'authentification unique de l'entreprise emprunte l'identité du client pour la vérifier.</span><span class="sxs-lookup"><span data-stu-id="26855-119">Impersonating the client is something the ENTSSO System does to verify the client’s identity.</span></span> <span data-ttu-id="26855-120">Diverses causes peuvent expliquer le fait que le système ne parvienne pas à effectuer cette opération.</span><span class="sxs-lookup"><span data-stu-id="26855-120">When the system is unable to impersonate a client, one of three things may have occurred.</span></span> <span data-ttu-id="26855-121">Il se peut que le client tente d'effectuer une activité inhabituelle ou d'infiltrer la sécurité du système, ou que l'application cliente ait été conçue pour bloquer l'emprunt d'identité.</span><span class="sxs-lookup"><span data-stu-id="26855-121">The client may be attempting to perform an usual activity, the client may be attempting to infiltrate system security, or the client application may have been designed to block impersonation.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="26855-122">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="26855-122">User Action</span></span>  
 <span data-ttu-id="26855-123">Localisez l'application cliente, puis déterminez ce qu'elle tente de faire et si elle bloque ou non l'emprunt d'identité.</span><span class="sxs-lookup"><span data-stu-id="26855-123">Locate the client application and determine what it is attempting to do, and whether or not it is blocking impersonation.</span></span>