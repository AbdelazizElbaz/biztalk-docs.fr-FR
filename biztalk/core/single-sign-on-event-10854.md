---
title: "Single Sign-On : Événement 10854 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d8faed9d-5c7e-4b99-bcd9-ea5f670d5e72
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 42f9e9e761689b2ed21ec37acdbb8a63f1f88070
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10854"></a><span data-ttu-id="c5427-102">Single Sign-On : Événement 10854</span><span class="sxs-lookup"><span data-stu-id="c5427-102">Single Sign-On: Event 10854</span></span>
## <a name="details"></a><span data-ttu-id="c5427-103">Détails</span><span class="sxs-lookup"><span data-stu-id="c5427-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c5427-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="c5427-104">Product Name</span></span>|<span data-ttu-id="c5427-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="c5427-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="c5427-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="c5427-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="c5427-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="c5427-107">Event ID</span></span>|<span data-ttu-id="c5427-108">10854</span><span class="sxs-lookup"><span data-stu-id="c5427-108">10854</span></span>|  
|<span data-ttu-id="c5427-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="c5427-109">Event Source</span></span>|<span data-ttu-id="c5427-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="c5427-110">ENTSSO</span></span>|  
|<span data-ttu-id="c5427-111">Composant</span><span class="sxs-lookup"><span data-stu-id="c5427-111">Component</span></span>|<span data-ttu-id="c5427-112">Néant</span><span class="sxs-lookup"><span data-stu-id="c5427-112">N/A</span></span>|  
|<span data-ttu-id="c5427-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="c5427-113">Symbolic Name</span></span>|<span data-ttu-id="c5427-114">ENTSSO_E_INVALID_STRING_FORMAT</span><span class="sxs-lookup"><span data-stu-id="c5427-114">ENTSSO_E_INVALID_STRING_FORMAT</span></span>|  
|<span data-ttu-id="c5427-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="c5427-115">Message Text</span></span>|<span data-ttu-id="c5427-116">Le format de chaîne est incorrect pour cette fonction.</span><span class="sxs-lookup"><span data-stu-id="c5427-116">The string format is incorrect for this function.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="c5427-117">Explication</span><span class="sxs-lookup"><span data-stu-id="c5427-117">Explanation</span></span>  
 <span data-ttu-id="c5427-118">Le format de chaîne est incorrect pour cette fonction.</span><span class="sxs-lookup"><span data-stu-id="c5427-118">The string format is incorrect for this function.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="c5427-119">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="c5427-119">User Action</span></span>  
 <span data-ttu-id="c5427-120">La mise en forme correcte des chaînes de mot de passe est décrite ci-après :</span><span class="sxs-lookup"><span data-stu-id="c5427-120">Proper formatting for password strings is described below:</span></span>  
  
 <span data-ttu-id="c5427-121">Propriété de type VT_BSTR</span><span class="sxs-lookup"><span data-stu-id="c5427-121">VT_BSTR type property</span></span>  
  
 <span data-ttu-id="c5427-122">Le délimiteur est / (barre oblique)</span><span class="sxs-lookup"><span data-stu-id="c5427-122">The delimiter is / (slash)</span></span>  
  
 <span data-ttu-id="c5427-123">sd = situation par défaut (pas d'opération - ne rien faire)</span><span class="sxs-lookup"><span data-stu-id="c5427-123">dc = default case (no operation - do nothing)</span></span>  
  
 <span data-ttu-id="c5427-124">Exemple : le contrôleur de domaine /</span><span class="sxs-lookup"><span data-stu-id="c5427-124">Example: dc/</span></span>  
  
 <span data-ttu-id="c5427-125">(aucune modification - « Cat » par « Cat »)</span><span class="sxs-lookup"><span data-stu-id="c5427-125">(no change - 'Cat' to 'Cat')</span></span>  
  
 <span data-ttu-id="c5427-126">cm = caractère majuscule</span><span class="sxs-lookup"><span data-stu-id="c5427-126">uc = upper case</span></span>  
  
 <span data-ttu-id="c5427-127">Exemple : CU /</span><span class="sxs-lookup"><span data-stu-id="c5427-127">Example: uc/</span></span>  
  
 <span data-ttu-id="c5427-128">(indiquer le mot de passe en majuscules - « Cat » par « CAT »)</span><span class="sxs-lookup"><span data-stu-id="c5427-128">(change password to upper case - 'Cat' to 'CAT')</span></span>  
  
 <span data-ttu-id="c5427-129">lm = lettres minuscules</span><span class="sxs-lookup"><span data-stu-id="c5427-129">lc = lower case</span></span>  
  
 <span data-ttu-id="c5427-130">Exemple : lc /</span><span class="sxs-lookup"><span data-stu-id="c5427-130">Example: lc/</span></span>  
  
 <span data-ttu-id="c5427-131">(indiquer le mot de passe en minuscules - « Cat » par « cat »)</span><span class="sxs-lookup"><span data-stu-id="c5427-131">(change password to lower case - 'Cat' to 'cat')</span></span>  
  
 <span data-ttu-id="c5427-132">sc = supprimer des caractères - suivi du nombre, puis des caractères</span><span class="sxs-lookup"><span data-stu-id="c5427-132">rc = remove chars - followed by count followed by chars</span></span>  
  
 <span data-ttu-id="c5427-133">Exemple : rc/2 / #@/</span><span class="sxs-lookup"><span data-stu-id="c5427-133">Example: rc/2/#@/</span></span>  
  
 <span data-ttu-id="c5427-134">(supprimez les caractères « # » et « @ » du mot de passe - «C@t# » « CT »)</span><span class="sxs-lookup"><span data-stu-id="c5427-134">(remove the characters '#' and '@' from the password - 'C@t#' to 'Ct')</span></span>  
  
 <span data-ttu-id="c5427-135">cr = caractères de remplacement - suivi du nombre, des caractères à remplacer, ainsi que des caractères de remplacement</span><span class="sxs-lookup"><span data-stu-id="c5427-135">sc = substitute chars - followed by count followed by chars to replace followed by substitute chars</span></span>  
  
 <span data-ttu-id="c5427-136">Exemple : sc/3/abc/def /</span><span class="sxs-lookup"><span data-stu-id="c5427-136">Example: sc/3/abc/def/</span></span>  
  
 <span data-ttu-id="c5427-137">(supprimer les caractères « a », « b » et « c » du mot de passe et les remplacer par « d », « e » et « f » respectivement)</span><span class="sxs-lookup"><span data-stu-id="c5427-137">(remove the characters 'a', 'b' and 'c' from the password and replace with 'd', 'e' and 'f' respectively)</span></span>  
  
 <span data-ttu-id="c5427-138">(« Cat » par « Cdt »)</span><span class="sxs-lookup"><span data-stu-id="c5427-138">('Cat' to 'Cdt')</span></span>  
  
 <span data-ttu-id="c5427-139">rd = remplir à partir du début - suivi du nombre (longueur minimum du mot de passe) et d'un seul caractère de remplissage</span><span class="sxs-lookup"><span data-stu-id="c5427-139">ps = pad from start - followed by count (min password length) followed by single pad char</span></span>  
  
 <span data-ttu-id="c5427-140">Exemple : ps/8/Nb /</span><span class="sxs-lookup"><span data-stu-id="c5427-140">Example: ps/8/#/</span></span>  
  
 <span data-ttu-id="c5427-141">(si le mot de passe comprend moins de 8 caractères, remplir à partir du début avec le caractère « # » jusqu'à obtenir un total de 8 caractères)</span><span class="sxs-lookup"><span data-stu-id="c5427-141">(if the password is not at least 8 chars in length then pad from the start with the character '#' until there are 8 chars total)</span></span>  
  
 <span data-ttu-id="c5427-142">(« Cat » par « #####Cat »)</span><span class="sxs-lookup"><span data-stu-id="c5427-142">('Cat' to '#####Cat')</span></span>  
  
 <span data-ttu-id="c5427-143">rf = remplir à partir de la fin - suivi du nombre (longueur minimum du mot de passe) et d'un seul caractère de remplissage</span><span class="sxs-lookup"><span data-stu-id="c5427-143">pe = pad from end - followed by count (min password length) followed by single pad char</span></span>  
  
 <span data-ttu-id="c5427-144">Exemple : pe/10 / $/</span><span class="sxs-lookup"><span data-stu-id="c5427-144">Example: pe/10/$/</span></span>  
  
 <span data-ttu-id="c5427-145">(si le mot de passe comprend moins de 10 caractères, remplir à partir de la fin avec le caractère « $ » jusqu'à obtenir un total de 10 caractères)</span><span class="sxs-lookup"><span data-stu-id="c5427-145">(if the password is not at least 10 chars in length then pad to the end with the character '$' until there are 10 chars total)</span></span>  
  
 <span data-ttu-id="c5427-146">(« Cat » par « Cat$$$$$$$ »)</span><span class="sxs-lookup"><span data-stu-id="c5427-146">('Cat' to 'Cat$$$$$$$')</span></span>  
  
 <span data-ttu-id="c5427-147">tr = tronquer - longueur limite de la chaîne, suivie du nombre</span><span class="sxs-lookup"><span data-stu-id="c5427-147">tr = truncate - limit length of string - followed by count</span></span>  
  
 <span data-ttu-id="c5427-148">Exemple : tr/11 /</span><span class="sxs-lookup"><span data-stu-id="c5427-148">Example: tr/11/</span></span>  
  
 <span data-ttu-id="c5427-149">(« Cat123456789 » par « Cat12345678 ») ;</span><span class="sxs-lookup"><span data-stu-id="c5427-149">('Cat123456789' to 'Cat12345678');</span></span>  
  
 <span data-ttu-id="c5427-150">Les jetons sont traités dans l'ordre dans lequel ils apparaissent dans la chaîne.</span><span class="sxs-lookup"><span data-stu-id="c5427-150">The tokens are processed in their order in the string.</span></span>  
  
 <span data-ttu-id="c5427-151">Exemple :</span><span class="sxs-lookup"><span data-stu-id="c5427-151">Example:</span></span>  
  
 <span data-ttu-id="c5427-152">cm/sc/1/&/ce/2/#$/--/rd/8/&/tr/32/</span><span class="sxs-lookup"><span data-stu-id="c5427-152">uc/rc/1/&/sc/2/#$/--/ps/8/&/tr/32/</span></span>