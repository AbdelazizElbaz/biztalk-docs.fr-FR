---
title: "La gestion des chaînes Values1 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- jdearglist.txt, configuring strings
- strings, left-justified
- strings, configuring
- strings, right-justified
ms.assetid: a180b818-1009-45f5-a503-d10ed7dd27fc
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6f32b29b9a8688fe8402730c1db8f12e42a67bab
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="handling-string-values"></a><span data-ttu-id="d6418-102">Gestion des valeurs de chaîne</span><span class="sxs-lookup"><span data-stu-id="d6418-102">Handling String Values</span></span>
<span data-ttu-id="d6418-103">Cette rubrique décrit la configuration de certains arguments de chaîne comme alignés à droite (et remplis à gauche).</span><span class="sxs-lookup"><span data-stu-id="d6418-103">This topic describes how to configure certain string arguments as right-justified (and left padded).</span></span>  
  
## <a name="types-of-string-values"></a><span data-ttu-id="d6418-104">Types de valeurs de chaîne</span><span class="sxs-lookup"><span data-stu-id="d6418-104">Types of String Values</span></span>  
 <span data-ttu-id="d6418-105">JD Edwards OneWorld expose deux types de valeurs de chaîne à l'aide de sa couche d'interopérabilité :</span><span class="sxs-lookup"><span data-stu-id="d6418-105">JD Edwards OneWorld exposes two kinds of string values through its interoperability layer:</span></span>  
  
-   <span data-ttu-id="d6418-106">Char : un caractère unique</span><span class="sxs-lookup"><span data-stu-id="d6418-106">Char: a single character</span></span>  
  
-   <span data-ttu-id="d6418-107">chaîne de longueur maximale</span><span class="sxs-lookup"><span data-stu-id="d6418-107">maximum length string</span></span>  
  
 <span data-ttu-id="d6418-108">JD Edwards OneWorld utilise une notation hongroise pour nommer les arguments de ces types dans les fonctions commerciales.</span><span class="sxs-lookup"><span data-stu-id="d6418-108">JD Edwards OneWorld uses Hungarian notation to name the arguments of these types in the business functions.</span></span> <span data-ttu-id="d6418-109">Par exemple, les arguments de ces types commencent par :</span><span class="sxs-lookup"><span data-stu-id="d6418-109">For example, arguments of these types begin with:</span></span>  
  
-   <span data-ttu-id="d6418-110">c</span><span class="sxs-lookup"><span data-stu-id="d6418-110">c</span></span>  
  
-   <span data-ttu-id="d6418-111">sz</span><span class="sxs-lookup"><span data-stu-id="d6418-111">sz</span></span>  
  
### <a name="left-justified-values"></a><span data-ttu-id="d6418-112">Valeurs alignées à gauche</span><span class="sxs-lookup"><span data-stu-id="d6418-112">Left-Justified Values</span></span>  
 <span data-ttu-id="d6418-113">Pour une majorité d'arguments de type sz, la chaîne de longueur maximale ou tableau de caractères, JD Edwards OneWorld attend une valeur alignée à gauche.</span><span class="sxs-lookup"><span data-stu-id="d6418-113">For a majority of sz-type arguments, maximum length string or char array, JD Edwards OneWorld expects a left-justified value.</span></span> <span data-ttu-id="d6418-114">Pour une ligne d'adresse, dont la longueur maximale est de 40 caractères, JD Edwards OneWorld attend (par exemple) :</span><span class="sxs-lookup"><span data-stu-id="d6418-114">For a street address line, which is of maximum length 40, JD Edwards OneWorld expects (for example):</span></span>  
  
 <span data-ttu-id="d6418-115">"4567 Main St.       "</span><span class="sxs-lookup"><span data-stu-id="d6418-115">"4567 Main St.       "</span></span>  
  
 <span data-ttu-id="d6418-116">chaîne complétée d'espaces pour atteindre la longueur de 40 caractères.</span><span class="sxs-lookup"><span data-stu-id="d6418-116">padded to length 40 with blanks.</span></span> <span data-ttu-id="d6418-117">Il n'est pas nécessaire d'entrer les caractères de remplissage, car l'adaptateur Microsoft BizTalk pour JD Edwards OneWorld le fait automatiquement.</span><span class="sxs-lookup"><span data-stu-id="d6418-117">It is not necessary for you to enter the padding because Microsoft BizTalk Adapter for JD Edwards OneWorld provides this for you.</span></span> <span data-ttu-id="d6418-118">Vous devez uniquement entrer « 4567 Main St.» , dans votre code client.</span><span class="sxs-lookup"><span data-stu-id="d6418-118">You only need to enter "4567 Main St.", in your client code.</span></span>  
  
### <a name="right-justified-values"></a><span data-ttu-id="d6418-119">Valeurs alignées à droite</span><span class="sxs-lookup"><span data-stu-id="d6418-119">Right-Justified Values</span></span>  
 <span data-ttu-id="d6418-120">Pour certains sous-ensembles de valeurs en relation avec ce type, JD Edwards OneWorld attend des valeurs alignées à droites avec un remplissage à gauche.</span><span class="sxs-lookup"><span data-stu-id="d6418-120">For some subset of values for this type, JD Edwards OneWorld expects values that are right justified with padding on the left.</span></span> <span data-ttu-id="d6418-121">Par exemple, pour les fonctions du module source B4200310, l’argument szBusinessUnit est de longueur 12.</span><span class="sxs-lookup"><span data-stu-id="d6418-121">For example, for business functions in the B4200310 source module, the argument szBusinessUnit is of length 12.</span></span> <span data-ttu-id="d6418-122">Cet argument représente une usine, par exemple une installation de production.</span><span class="sxs-lookup"><span data-stu-id="d6418-122">This argument represents a plant, such as a production facility.</span></span> <span data-ttu-id="d6418-123">Pour un numéro d’unité 30, J.D.</span><span class="sxs-lookup"><span data-stu-id="d6418-123">For a plant number of 30, J.D.</span></span> <span data-ttu-id="d6418-124">Edwards OneWorld XE attend une valeur de :</span><span class="sxs-lookup"><span data-stu-id="d6418-124">Edwards OneWorld XE expects a value of:</span></span>  
  
 <span data-ttu-id="d6418-125">"          30"</span><span class="sxs-lookup"><span data-stu-id="d6418-125">"          30"</span></span>  
  
 <span data-ttu-id="d6418-126">Pour entrer une valeur qui sera aligné à droite, vous devez entrer le paramètre dans un fichier nommé jdearglist.txt.</span><span class="sxs-lookup"><span data-stu-id="d6418-126">To enter a value that will be right-justified, you must enter the parameter in a file called jdearglist.txt.</span></span> <span data-ttu-id="d6418-127">Ce dernier est lu lorsque vous générez le schéma.</span><span class="sxs-lookup"><span data-stu-id="d6418-127">The jdearglist.txt is read when you generate the schema.</span></span> <span data-ttu-id="d6418-128">Toute valeur répertoriée dans ce fichier texte est automatiquement convertie en une valeur alignée à droite et complétée d'espaces à gauche.</span><span class="sxs-lookup"><span data-stu-id="d6418-128">Any value that is listed in this text file is automatically converted to a right-justified value and padded on the left with blanks.</span></span>  
  
 <span data-ttu-id="d6418-129">Vous devez créer jdearglist.txt à l’aide d’un texte de l’éditeur, avec des entrées décrivant ces paramètres et enregistrez-le dans le dossier suivant : %BizTalk_Install_Adapter%\config\JDE\\</span><span class="sxs-lookup"><span data-stu-id="d6418-129">You must create jdearglist.txt using a text editor, with entries describing these parameters, and save it in the following folder: %BizTalk_Install_Adapter%\config\JDE\\</span></span>  
  
 <span data-ttu-id="d6418-130">Où **BizTalk_Install_Adapter %** est le répertoire dans lequel vous avez installé l’adaptateur BizTalk pour JD Edwards OneWorld.</span><span class="sxs-lookup"><span data-stu-id="d6418-130">Where **%BizTalk_Install_Adapter%** is the directory in which you installed BizTalk Adapter for JD Edwards OneWorld.</span></span>  
  
 <span data-ttu-id="d6418-131">Si ce fichier est inexistant ou vide, un message d'information s'affiche dans l'adaptateur BizTalk pour le journal JD Edwards OneWorld lors de la première ouverture de l'adaptateur.</span><span class="sxs-lookup"><span data-stu-id="d6418-131">If this file does not exist or is empty, an informational message appears in the BizTalk Adapter for JD Edwards OneWorld log when the adapter first opens.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d6418-132">Si vous modifiez ce fichier après avoir généré votre schéma, vous devez régénérer le schéma pour actualiser les données qu'il contient.</span><span class="sxs-lookup"><span data-stu-id="d6418-132">If you change this file after generating your schema, you must regenerate the schema to refresh the data it contains.</span></span>  
  
 <span data-ttu-id="d6418-133">Pour vérifier que vous utilisez les dernières informations de ce fichier, vous pouvez utiliser le Gestionnaire des tâches pour arrêter le processus browsingagent.exe avant de générer de nouveau votre schéma. Toutefois, cela ne devrait pas être nécessaire.</span><span class="sxs-lookup"><span data-stu-id="d6418-133">To verify that you are using the latest information in this file, you can use the Task Manager to stop the browsingagent.exe process before regenerating your schema; however, this should not be necessary.</span></span>  
  
 <span data-ttu-id="d6418-134">Voici un exemple du format des entrées dans le fichier jdearglist.txt :</span><span class="sxs-lookup"><span data-stu-id="d6418-134">The following is an example of the format for entries in the jdearglist.txt file:</span></span>  
  
```  
<SourceModule>.<BusinessFunction>.<Argument>  
```  
  
 <span data-ttu-id="d6418-135">Exemple :</span><span class="sxs-lookup"><span data-stu-id="d6418-135">For example:</span></span>  
  
```  
B4200310.F4211FSBeginDoc.szBusinessUnit  
```  
  
 <span data-ttu-id="d6418-136">Pour un ensemble de fonctions commerciales appartenant au même module commercial, des arguments de nom similaire (du même type) sont partagés entre plusieurs ou toutes les fonctions commerciales.</span><span class="sxs-lookup"><span data-stu-id="d6418-136">For a set of business functions belonging to the same business module, like-named arguments (of the same type) are shared across some or all of the business functions.</span></span> <span data-ttu-id="d6418-137">Vous pouvez utiliser le caractère générique astérisque (*) au lieu du nom de fonction commerciale.</span><span class="sxs-lookup"><span data-stu-id="d6418-137">You can use the wildcard character (*) instead of the business function name.</span></span> <span data-ttu-id="d6418-138">Exemple :</span><span class="sxs-lookup"><span data-stu-id="d6418-138">For example:</span></span>  
  
```  
B4200310.*.szBusinessUnit  
```  
  
> [!NOTE]
>  <span data-ttu-id="d6418-139">Lors de l'importation d'un processus d'entreprise JD Edwards OneWorld sur un autre ordinateur, vous devez copier jdearglist.txt manuellement.</span><span class="sxs-lookup"><span data-stu-id="d6418-139">When importing a JD Edwards OneWorld business process to another computer, you must copy jdearglist.txt manually.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6418-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d6418-140">See Also</span></span>  
 <span data-ttu-id="d6418-141">[Paramètre Justification des chaînes dans Jdearglist](../core/setting-string-justification-in-jdearglist.md) </span><span class="sxs-lookup"><span data-stu-id="d6418-141">[Setting String Justification in Jdearglist](../core/setting-string-justification-in-jdearglist.md) </span></span>  
 [<span data-ttu-id="d6418-142">Annexe a : les Types de données</span><span class="sxs-lookup"><span data-stu-id="d6418-142">Appendix A: Data Types</span></span>](../core/appendix-a-data-types.md)