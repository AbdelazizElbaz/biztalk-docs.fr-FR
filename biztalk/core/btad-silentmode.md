---
title: BTAD_SilentMode | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BTAD_SilentMode [environment variable], about BTAS_SilentMode
- BTAD_SilentMode [environment variable]
- BTAD_SilentMode [environment variable], warnings
ms.assetid: 271835cf-1587-44c5-b5af-b4df4e981ab4
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 31715835c98d2f60a3b5f1c18251571ea57641d7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="btadsilentmode"></a><span data-ttu-id="e9583-102">BTAD_SilentMode</span><span class="sxs-lookup"><span data-stu-id="e9583-102">BTAD_SilentMode</span></span>
<span data-ttu-id="e9583-103">BTAD_SilentMode spécifie des options d'exécution du script en mode silencieux.</span><span class="sxs-lookup"><span data-stu-id="e9583-103">BTAD_SilentMode specifies options for running the script in silent mode.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e9583-104">Notes</span><span class="sxs-lookup"><span data-stu-id="e9583-104">Remarks</span></span>  
 <span data-ttu-id="e9583-105">Lorsque vous sélectionnez une option de mode silencieux, BTS Installer insère sa valeur dans la variable BTAD_SilentMode.</span><span class="sxs-lookup"><span data-stu-id="e9583-105">When you specify an option for silent mode, BTS Installer places its value into the BTAD_SilentMode variable.</span></span>  
  
 <span data-ttu-id="e9583-106">La valeur par défaut de BTAD_SilentMode est 2, ce qui indique que le script s'exécute en mode silencieux.</span><span class="sxs-lookup"><span data-stu-id="e9583-106">The default value of BTAD_SilentMode is 2, which specifies that the script runs in silent mode.</span></span> <span data-ttu-id="e9583-107">Le tableau suivant répertorie les valeurs possibles de BTAD_SilentMode.</span><span class="sxs-lookup"><span data-stu-id="e9583-107">The following table describes the possible values for BTAD_SilentMode.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="e9583-108">Si vous démarrez l'interface utilisateur BizTalk Server à partir de scripts, les boîtes de dialogue modales risquent de ne pas être visibles ou actives, ce qui ne facilite pas leur affichage et leur fermeture.</span><span class="sxs-lookup"><span data-stu-id="e9583-108">If you start the BizTalk Server user interface from scripts, modal dialog boxes may not be visible or have focus, making them difficult to view and dismiss.</span></span> <span data-ttu-id="e9583-109">Les bases de données BizTalk risquent de ne plus être accessibles et de se verrouiller lorsque des boîtes de dialogue modales sont ouvertes.</span><span class="sxs-lookup"><span data-stu-id="e9583-109">The BizTalk databases can become locked and inaccessible while modal dialog boxes are open.</span></span> <span data-ttu-id="e9583-110">C'est pourquoi les scripts destinés à des systèmes de production doivent s'exécuter en mode silencieux.</span><span class="sxs-lookup"><span data-stu-id="e9583-110">For this reason, on production systems, all scripts should run in silent mode.</span></span>  
  
|<span data-ttu-id="e9583-111">Valeur</span><span class="sxs-lookup"><span data-stu-id="e9583-111">Value</span></span>|<span data-ttu-id="e9583-112">Description</span><span class="sxs-lookup"><span data-stu-id="e9583-112">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e9583-113">0</span><span class="sxs-lookup"><span data-stu-id="e9583-113">0</span></span>|<span data-ttu-id="e9583-114">Ne modifie pas le niveau de l'interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="e9583-114">Does not change the user interface (UI) level.</span></span>|  
|<span data-ttu-id="e9583-115"> 1</span><span class="sxs-lookup"><span data-stu-id="e9583-115">1</span></span>|<span data-ttu-id="e9583-116">Utilise le niveau d'interface utilisateur par défaut.</span><span class="sxs-lookup"><span data-stu-id="e9583-116">Uses the default UI level.</span></span>|  
|<span data-ttu-id="e9583-117">2</span><span class="sxs-lookup"><span data-stu-id="e9583-117">2</span></span>|<span data-ttu-id="e9583-118">Effectue une installation silencieuse (valeur par défaut).</span><span class="sxs-lookup"><span data-stu-id="e9583-118">Performs a silent installation (the default).</span></span>|  
|<span data-ttu-id="e9583-119">3</span><span class="sxs-lookup"><span data-stu-id="e9583-119">3</span></span>|<span data-ttu-id="e9583-120">Permet la gestion simple de l'avancement et des erreurs.</span><span class="sxs-lookup"><span data-stu-id="e9583-120">Provides simple progress and error handling.</span></span>|  
|<span data-ttu-id="e9583-121">4</span><span class="sxs-lookup"><span data-stu-id="e9583-121">4</span></span>|<span data-ttu-id="e9583-122">Fournit une interface utilisateur créée ; supprime les assistants.</span><span class="sxs-lookup"><span data-stu-id="e9583-122">Provides authored UI; suppresses wizards.</span></span>|  
|<span data-ttu-id="e9583-123">0x80</span><span class="sxs-lookup"><span data-stu-id="e9583-123">0x80</span></span>|<span data-ttu-id="e9583-124">En cas de combinaison avec l'une des valeurs ci-dessus, Windows Installer affiche une boîte de dialogue modale indiquant si le script s'est exécuté correctement ou si une erreur s'est produite.</span><span class="sxs-lookup"><span data-stu-id="e9583-124">If combined with any above value, Windows Installer displays a modal dialog box if the script has executed successfully or if there has been an error.</span></span> <span data-ttu-id="e9583-125">Aucune boîte de dialogue ne s'affiche si l'utilisateur annule l'opération.</span><span class="sxs-lookup"><span data-stu-id="e9583-125">No dialog box is displayed if the user cancels the operation.</span></span>|  
|<span data-ttu-id="e9583-126">0x40</span><span class="sxs-lookup"><span data-stu-id="e9583-126">0x40</span></span>|<span data-ttu-id="e9583-127">En cas de combinaison avec la valeur 3, Windows Installer affiche des boîtes de dialogue de progression mais aucune boîte de dialogue modale ni aucune boîte de dialogue d'erreur.</span><span class="sxs-lookup"><span data-stu-id="e9583-127">If combined with the 3 value, Windows Installer displays progress dialog boxes but does not display any modal dialog boxes or error dialog boxes.</span></span>|  
|<span data-ttu-id="e9583-128">0x20</span><span class="sxs-lookup"><span data-stu-id="e9583-128">0x20</span></span>|<span data-ttu-id="e9583-129">En cas de combinaison avec la valeur 3, Windows Installer affiche des boîtes de dialogue de progression mais aucune boîte de dialogue modale ni aucune boîte de dialogue d'erreur.</span><span class="sxs-lookup"><span data-stu-id="e9583-129">If combined with the 3 value, Windows Installer displays progress dialog boxes but does not display any modal dialog boxes or error dialog boxes.</span></span>|  
|<span data-ttu-id="e9583-130">0x100</span><span class="sxs-lookup"><span data-stu-id="e9583-130">0x100</span></span>|<span data-ttu-id="e9583-131">En cas de combinaison avec la valeur 3, Windows Installer affiche des boîtes de dialogue de progression mais aucune boîte de dialogue modale ni aucune boîte de dialogue d'erreur.</span><span class="sxs-lookup"><span data-stu-id="e9583-131">If combined with the 3 value, Windows Installer displays progress dialog boxes but does not display any modal dialog boxes or error dialog boxes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e9583-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e9583-132">See Also</span></span>  
 <span data-ttu-id="e9583-133">[Variables d’environnement de Script de pré-traitement et de post-traitement](../core/pre-and-post-processing-script-environment-variables.md) </span><span class="sxs-lookup"><span data-stu-id="e9583-133">[Pre- and Post-processing Script Environment Variables](../core/pre-and-post-processing-script-environment-variables.md) </span></span>  
 [<span data-ttu-id="e9583-134">Comment les Variables d’environnement indiquent état du déploiement</span><span class="sxs-lookup"><span data-stu-id="e9583-134">How Environment Variables Indicate Deployment State</span></span>](../core/how-environment-variables-indicate-deployment-state.md)