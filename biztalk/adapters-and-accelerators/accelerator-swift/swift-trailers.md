---
title: SWIFT remorques | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SWIFT Trailer schema
- schemas, SWIFT
- trailers [SWIFT]
- SWIFT, trailers
ms.assetid: b6d64584-0514-4c87-98c0-33755efc4695
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bc3155ac21f55e7c61483b9287429f9b722f6a84
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="swift-trailers"></a><span data-ttu-id="3c2e0-102">Codes de fin SWIFT</span><span class="sxs-lookup"><span data-stu-id="3c2e0-102">SWIFT Trailers</span></span>
<span data-ttu-id="3c2e0-103">Chaque message SWIFT possède un ou plusieurs codes de fin comme requis par les exigences d’exchange et la sécurité de message.</span><span class="sxs-lookup"><span data-stu-id="3c2e0-103">Each SWIFT message has one or more trailers as required by the message exchange and security requirements.</span></span> <span data-ttu-id="3c2e0-104">Codes de fin système, le cas échéant, suivent les codes de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="3c2e0-104">System trailers, if applicable, follow user trailers.</span></span> <span data-ttu-id="3c2e0-105">Chaque code de fin dans le bloc de code de fin s’affiche dans un sous-bloc délimité par les autres paires d’accolades.</span><span class="sxs-lookup"><span data-stu-id="3c2e0-105">Each trailer within the Trailer Block appears within a subblock delimited by further pairs of curly brackets.</span></span> <span data-ttu-id="3c2e0-106">Chaque sous-bloc commence par trois lettres indiquant le type de code de fin, suivi du signe deux-points.</span><span class="sxs-lookup"><span data-stu-id="3c2e0-106">Each subblock begins with three letters denoting the trailer type, followed by a colon.</span></span>  
  
 <span data-ttu-id="3c2e0-107">Le schéma de code de fin SWIFT (SWIFT Trailer.xsd) contient le format pour les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="3c2e0-107">The SWIFT Trailer schema (SWIFT Trailer.xsd) contains the format for the following:</span></span>  
  
-   <span data-ttu-id="3c2e0-108">Le délimiteur de fin du bloc de texte</span><span class="sxs-lookup"><span data-stu-id="3c2e0-108">The ending delimiter of the text block</span></span>  
  
-   <span data-ttu-id="3c2e0-109">Codes de l’utilisateur (utilisateur et des informations système)</span><span class="sxs-lookup"><span data-stu-id="3c2e0-109">User trailers (user and system information)</span></span>  
  
-   <span data-ttu-id="3c2e0-110">Codes de fin système</span><span class="sxs-lookup"><span data-stu-id="3c2e0-110">System trailers</span></span>  
  
 <span data-ttu-id="3c2e0-111">Le délimiteur de fin du bloc de texte est «- »}.</span><span class="sxs-lookup"><span data-stu-id="3c2e0-111">The ending delimiter of the Text Block is "-}".</span></span> <span data-ttu-id="3c2e0-112">Le bloc de code de fin commence par « {5 : ».</span><span class="sxs-lookup"><span data-stu-id="3c2e0-112">The trailer block begins with "{5:".</span></span> <span data-ttu-id="3c2e0-113">Le contenu du bloc de code de fin inclut à la fois les informations utilisateur (somme de contrôle, l’authentification des messages, d’authentification propriétaire et ainsi de suite) et les informations système (messages retardés, référence du message, possible de messages en double et ainsi de suite).</span><span class="sxs-lookup"><span data-stu-id="3c2e0-113">The contents of the trailer block include both user information (checksum, message authentication, proprietary authentication, and so on), and system information (delayed message, message reference, possible duplicate message, and so on).</span></span> <span data-ttu-id="3c2e0-114">Codes de fin ajoutées par SWIFT fournissent également un bloc de tiers, délimité par « {S: ».</span><span class="sxs-lookup"><span data-stu-id="3c2e0-114">Trailers added by SWIFT also provide a third block, delimited by "{S:".</span></span> <span data-ttu-id="3c2e0-115">Le *SWIFT utilisateur manuel*, « Description du Service de FIN », décrit en détail le contenu du bloc 5.</span><span class="sxs-lookup"><span data-stu-id="3c2e0-115">The *SWIFT User Handbook*, "FIN Service Description" topic, describes in detail the contents of block 5.</span></span> [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]<span data-ttu-id="3c2e0-116">ne valide pas le contenu du bloc S.</span><span class="sxs-lookup"><span data-stu-id="3c2e0-116"> does not validate the contents of block S.</span></span>  
  
 <span data-ttu-id="3c2e0-117">L’interface FIN réelle ou le réseau SWIFT ajoute les codes de fin.</span><span class="sxs-lookup"><span data-stu-id="3c2e0-117">The actual FIN interface or the SWIFT network appends the trailers.</span></span> <span data-ttu-id="3c2e0-118">Si un message contient un code de fin lorsque [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] reçoit le message, [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] exécute le code de fin avec le message.</span><span class="sxs-lookup"><span data-stu-id="3c2e0-118">If a message contains a trailer when [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] receives the message, [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] carries the trailer with the message.</span></span> [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]<span data-ttu-id="3c2e0-119">ne génère pas d’erreur si un message ne contient pas un code de fin lorsque [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] reçoit le message.</span><span class="sxs-lookup"><span data-stu-id="3c2e0-119"> does not raise an error if a message does not contain a trailer when [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] receives the message.</span></span> <span data-ttu-id="3c2e0-120">Comme avec les en-têtes, toutes les entrées de code de fin, y compris les blocs eux-mêmes, sont facultatives dans [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3c2e0-120">As with headers, all of the trailer entries, including the blocks themselves, are optional in [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)].</span></span>  
  
 <span data-ttu-id="3c2e0-121">Contenu de cette section :</span><span class="sxs-lookup"><span data-stu-id="3c2e0-121">This section contains:</span></span>  
  
-   [<span data-ttu-id="3c2e0-122">Codes de l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="3c2e0-122">User Trailers</span></span>](../../adapters-and-accelerators/accelerator-swift/user-trailers.md)  
  
-   [<span data-ttu-id="3c2e0-123">Système de codes de fin</span><span class="sxs-lookup"><span data-stu-id="3c2e0-123">System Trailers</span></span>](../../adapters-and-accelerators/accelerator-swift/system-trailers.md)  
  
## <a name="see-also"></a><span data-ttu-id="3c2e0-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3c2e0-124">See Also</span></span>  
 [<span data-ttu-id="3c2e0-125">Utilisation de schémas</span><span class="sxs-lookup"><span data-stu-id="3c2e0-125">Working with Schemas</span></span>](../../adapters-and-accelerators/accelerator-swift/working-with-schemas.md)