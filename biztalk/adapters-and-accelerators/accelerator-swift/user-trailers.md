---
title: Codes de fin utilisateur | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- trailers [SWIFT]
- SWIFT, trailers
ms.assetid: 340d9fc8-467b-4cba-b69f-eb761767deaa
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4dc2d7f2a3dd21d35bb33fa625f59aa27c04e656
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="user-trailers"></a><span data-ttu-id="97841-102">Codes de l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="97841-102">User Trailers</span></span>
<span data-ttu-id="97841-103">Codes de fin utilisateur, à l’exception du code de fin CHK, sont facultatifs et lorsqu’il est présent, se produisent dans l’ordre suivant :</span><span class="sxs-lookup"><span data-stu-id="97841-103">User trailers, except for the CHK trailer, are optional and when present, occur in the following order:</span></span>  
  
|<span data-ttu-id="97841-104">Code de fin du code</span><span class="sxs-lookup"><span data-stu-id="97841-104">Trailer code</span></span>|<span data-ttu-id="97841-105">Nom</span><span class="sxs-lookup"><span data-stu-id="97841-105">Name</span></span>|  
|------------------|----------|  
|<span data-ttu-id="97841-106">MAC</span><span class="sxs-lookup"><span data-stu-id="97841-106">MAC</span></span>|<span data-ttu-id="97841-107">Code d’authentification de message</span><span class="sxs-lookup"><span data-stu-id="97841-107">Message Authentication Code</span></span>|  
|<span data-ttu-id="97841-108">PAC</span><span class="sxs-lookup"><span data-stu-id="97841-108">PAC</span></span>|<span data-ttu-id="97841-109">Code d’authentification propriétaire</span><span class="sxs-lookup"><span data-stu-id="97841-109">Proprietary Authentication Code</span></span>|  
|<span data-ttu-id="97841-110">CHK</span><span class="sxs-lookup"><span data-stu-id="97841-110">CHK</span></span>|<span data-ttu-id="97841-111">Somme de contrôle</span><span class="sxs-lookup"><span data-stu-id="97841-111">Checksum</span></span>|  
|<span data-ttu-id="97841-112">TNG</span><span class="sxs-lookup"><span data-stu-id="97841-112">TNG</span></span>|<span data-ttu-id="97841-113">Formation</span><span class="sxs-lookup"><span data-stu-id="97841-113">Training</span></span>|  
|<span data-ttu-id="97841-114">PDE</span><span class="sxs-lookup"><span data-stu-id="97841-114">PDE</span></span>|<span data-ttu-id="97841-115">Émission de double possible</span><span class="sxs-lookup"><span data-stu-id="97841-115">Possible Duplicate Emission</span></span>|  
  
-   <span data-ttu-id="97841-116">**Code de fin Message Authentication Code (MAC).**</span><span class="sxs-lookup"><span data-stu-id="97841-116">**Message Authentication Code (MAC) Trailer.**</span></span> <span data-ttu-id="97841-117">Autorise l’authentification par l’utilisateur destinataire.</span><span class="sxs-lookup"><span data-stu-id="97841-117">Allows authentication by the receiving user.</span></span> <span data-ttu-id="97841-118">Le code de fin MAC est suivie d’un résultat de l’authentification.</span><span class="sxs-lookup"><span data-stu-id="97841-118">The MAC trailer is followed by an authentication result.</span></span> <span data-ttu-id="97841-119">Ce code de fin est obligatoire pour la plupart des catégories de message de l’utilisateur à l’application de la FIN.</span><span class="sxs-lookup"><span data-stu-id="97841-119">This trailer is mandatory for most user-to-user message categories within the FIN application.</span></span>  
  
     <span data-ttu-id="97841-120">Lorsque le Service de FIN est utilisé, un code de fin PAC (le cas échéant) suit le code de fin MAC.</span><span class="sxs-lookup"><span data-stu-id="97841-120">When the FIN Copy Service is used, a PAC trailer (if present) follows the MAC trailer.</span></span> <span data-ttu-id="97841-121">Le code suivant est un exemple d’un code de fin MAC :</span><span class="sxs-lookup"><span data-stu-id="97841-121">The following code is an example of a MAC trailer:</span></span>  
  
    ```  
    {MAC:<authentication-result>}  
    where <authentication-result> = 8!h  
    ```  
  
-   <span data-ttu-id="97841-122">**Code de fin du Code (PAC) d’authentification propriétaire.**</span><span class="sxs-lookup"><span data-stu-id="97841-122">**Proprietary Authentication Code (PAC) Trailer.**</span></span> <span data-ttu-id="97841-123">Le code de fin PAC est utilisé dans le service de FIN uniquement lorsque vous utilisez l’option d’authentification double.</span><span class="sxs-lookup"><span data-stu-id="97841-123">The PAC trailer is used within the FIN Copy service only when using the double authentication option.</span></span> <span data-ttu-id="97841-124">Messages d’utilisateur à 5 de bloc de FIN incluent le code de fin PAC immédiatement après le code de fin MAC, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="97841-124">Block 5 of FIN user-to-user messages include the PAC trailer immediately after the MAC trailer, if present.</span></span> <span data-ttu-id="97841-125">Ce résultat est calculé sur les champs extraits du bloc 4 du message, la valeur du champ 115, le cas échéant et le \<résultat de l’authentification > du code de fin MAC pour les Services de la copie avec l’authentification double.</span><span class="sxs-lookup"><span data-stu-id="97841-125">This result is calculated on the extracted fields of Block 4 of the message, the value of field 115, if present, and the \<authentication-result> of the MAC trailer for Copy Services with double authentication.</span></span>  
  
     <span data-ttu-id="97841-126">Par conséquent, l’indicateur de fin de bloc (CrLf-) est inclus dans le calcul PAC et les champs sont définis comme suit :</span><span class="sxs-lookup"><span data-stu-id="97841-126">As a result, the end-of-block indicator (CrLf-) is included in the PAC calculation and the fields are defined as follows:</span></span>  
  
    -   <span data-ttu-id="97841-127">Les quatre premiers caractères sont CrLf :</span><span class="sxs-lookup"><span data-stu-id="97841-127">The first four characters are CrLf:</span></span>  
  
    -   <span data-ttu-id="97841-128">Le champ et le délimiteur sont présents, autrement dit, les 32 a :, 20 :, et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="97841-128">The field and the delimiter are present, that is, 32A:, 20:, and so on.</span></span>  
  
    -   <span data-ttu-id="97841-129">Tous les sous-champs et leurs délimiteurs sont présents.</span><span class="sxs-lookup"><span data-stu-id="97841-129">All subfields and their delimiters are present.</span></span>  
  
     <span data-ttu-id="97841-130">Le code suivant est un exemple du format de code de fin PAC :</span><span class="sxs-lookup"><span data-stu-id="97841-130">The following code is an example of the PAC trailer format:</span></span>  
  
    ```  
    {PAC:[<authentication-result>]}  
    where <authentication-result> is mandatory on input messages only and  
    <authentication-result> = 8!h  
    ```  
  
-   <span data-ttu-id="97841-131">**CHK (somme de contrôle), code de fin (obligatoire pour tous les messages FIN)**</span><span class="sxs-lookup"><span data-stu-id="97841-131">**CHK (Checksum) Trailer (mandatory for all FIN messages)**</span></span>  
  
     <span data-ttu-id="97841-132">Le code de fin CHK est obligatoire pour tous les messages FIN et est calculé en fonction des adresse du destinataire (12 caractères avec la neuvième remplacé par *X* ainsi que le bloc de texte).</span><span class="sxs-lookup"><span data-stu-id="97841-132">The CHK trailer is mandatory for all FIN messages and is computed based upon the receiver's address (12 characters with the ninth character replaced by *X* plus the text block).</span></span> <span data-ttu-id="97841-133">Ce code de fin permet au système et du CBT pour vérifier que les messages ne sont pas endommagées en raison d’un dysfonctionnement du système ou une erreur de transmission non détecté.</span><span class="sxs-lookup"><span data-stu-id="97841-133">This trailer allows the system and the CBT to check that messages are not corrupted due to a system malfunction or an undetected transmission error.</span></span>  
  
     <span data-ttu-id="97841-134">Le code suivant est un exemple du format de code de fin CHK :</span><span class="sxs-lookup"><span data-stu-id="97841-134">The following code is an example of the CHK trailer format:</span></span>  
  
    ```  
    {CHK:<checksum-result>}  
    where <checksum-result> = 12!h  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="97841-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="97841-135">See Also</span></span>  
 [<span data-ttu-id="97841-136">Utilisation de schémas</span><span class="sxs-lookup"><span data-stu-id="97841-136">Working with Schemas</span></span>](../../adapters-and-accelerators/accelerator-swift/working-with-schemas.md)