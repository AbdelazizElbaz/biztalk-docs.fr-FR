---
title: La gestion des chaînes Values2 | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- string values, configuring
- formatting strings
- strings, formatting
- left-justified string values
- jdearglist.txt
- strings, left-justified
- right-justified string values
- strings, right-justified
ms.assetid: 23d54731-b2b9-4610-a533-e041237e0bb3
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 024663faa56d92361d861a61a0d64a4608839aa6
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="handling-string-values"></a><span data-ttu-id="30a52-102">Gestion des valeurs de chaîne</span><span class="sxs-lookup"><span data-stu-id="30a52-102">Handling String Values</span></span>
<span data-ttu-id="30a52-103">Cette rubrique décrit la configuration de certains arguments de chaîne comme alignés à droite (et remplis à gauche).</span><span class="sxs-lookup"><span data-stu-id="30a52-103">This topic describes how to configure certain string arguments as right-justified (and left padded).</span></span>  
  
## <a name="types-of-string-values"></a><span data-ttu-id="30a52-104">Types de valeurs de chaîne</span><span class="sxs-lookup"><span data-stu-id="30a52-104">Types of String Values</span></span>  
 <span data-ttu-id="30a52-105">JD Edwards EnterpriseOne expose deux types de valeurs de chaîne via sa couche d'interopérabilité :</span><span class="sxs-lookup"><span data-stu-id="30a52-105">JD Edwards EnterpriseOne exposes two kinds of string values through its interoperability layer:</span></span>  
  
-   <span data-ttu-id="30a52-106">Char : un caractère unique</span><span class="sxs-lookup"><span data-stu-id="30a52-106">char: a single character</span></span>  
  
-   <span data-ttu-id="30a52-107">chaîne de longueur maximale</span><span class="sxs-lookup"><span data-stu-id="30a52-107">maximum length string</span></span>  
  
 <span data-ttu-id="30a52-108">JD Edwards EnterpriseOne utilise la notation hongroise pour nommer les arguments de ces types dans les fonctions d'entreprise.</span><span class="sxs-lookup"><span data-stu-id="30a52-108">JD Edwards EnterpriseOne uses Hungarian notation to name the arguments of these types in the business functions.</span></span> <span data-ttu-id="30a52-109">Par exemple, les arguments de ces types commencent par :</span><span class="sxs-lookup"><span data-stu-id="30a52-109">For example, arguments of these types begin with:</span></span>  
  
-   <span data-ttu-id="30a52-110">c</span><span class="sxs-lookup"><span data-stu-id="30a52-110">c</span></span>  
  
-   <span data-ttu-id="30a52-111">sz</span><span class="sxs-lookup"><span data-stu-id="30a52-111">sz</span></span>  
  
### <a name="left-justified-values"></a><span data-ttu-id="30a52-112">Valeurs alignées à gauche</span><span class="sxs-lookup"><span data-stu-id="30a52-112">Left-Justified Values</span></span>  
 <span data-ttu-id="30a52-113">JD Edwards EnterpriseOne attend une valeur alignée à gauche pour une majorité d'arguments de type sz, la chaîne de longueur maximale ou le tableau de caractères.</span><span class="sxs-lookup"><span data-stu-id="30a52-113">For a majority of sz-type arguments, maximum length string or char array, JD Edwards EnterpriseOne expects a left-justified value.</span></span> <span data-ttu-id="30a52-114">Par exemple, pour une ligne « Adresse de domicile » d'une longueur maximale de 40, JD Edwards EnterpriseOne attend ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="30a52-114">For examples, for a street address line, which is of maximum length 40, JD Edwards EnterpriseOne expects (for example):</span></span>  
  
 <span data-ttu-id="30a52-115">« 4567 rue. »</span><span class="sxs-lookup"><span data-stu-id="30a52-115">"4567 Main St.    "</span></span>  
  
 <span data-ttu-id="30a52-116">chaîne complétée d'espaces pour atteindre la longueur de 40 caractères.</span><span class="sxs-lookup"><span data-stu-id="30a52-116">padded to length 40 with blanks.</span></span> <span data-ttu-id="30a52-117">Il n'est pas nécessaire d'entrer le remplissage car l'adaptateur Microsoft BizTalk pour JD Edwards EnterpriseOne le fait automatiquement.</span><span class="sxs-lookup"><span data-stu-id="30a52-117">It is not necessary for you to enter the padding because Microsoft BizTalk Adapter for JD Edwards EnterpriseOne provides this for you.</span></span> <span data-ttu-id="30a52-118">Vous devez juste saisir « 4567 Rue Pr » dans le code client.</span><span class="sxs-lookup"><span data-stu-id="30a52-118">You only need to enter "4567 Main St ", in your client code.</span></span>  
  
### <a name="right-justified-values"></a><span data-ttu-id="30a52-119">Valeurs alignées à droite</span><span class="sxs-lookup"><span data-stu-id="30a52-119">Right-Justified Values</span></span>  
 <span data-ttu-id="30a52-120">Pour certains sous-ensembles de valeurs de ce type, JD Edwards EnterpriseOne attend des valeurs alignées à droite, avec un remplissage à gauche.</span><span class="sxs-lookup"><span data-stu-id="30a52-120">For some subset of values for this type, JD Edwards EnterpriseOne expects values that are right justified with padding on the left.</span></span> <span data-ttu-id="30a52-121">Par exemple, pour les fonctions du module source B4200310, l’argument szBusinessUnit est de longueur 12.</span><span class="sxs-lookup"><span data-stu-id="30a52-121">For example, for business functions in the B4200310 source module, the argument szBusinessUnit is of length 12.</span></span> <span data-ttu-id="30a52-122">Cet argument représente une usine, par exemple une installation de production.</span><span class="sxs-lookup"><span data-stu-id="30a52-122">This argument represents a plant, such as a production facility.</span></span> <span data-ttu-id="30a52-123">Pour un numéro d'usine de 30, JD Edwards EnterpriseOne attend la valeur suivante :</span><span class="sxs-lookup"><span data-stu-id="30a52-123">For a plant number of 30, JD Edwards EnterpriseOne expects a value of:</span></span>  
  
 <span data-ttu-id="30a52-124">"           30"</span><span class="sxs-lookup"><span data-stu-id="30a52-124">"           30"</span></span>  
  
 <span data-ttu-id="30a52-125">Pour entrer une valeur qui sera aligné à droite, vous devez entrer le paramètre dans un fichier nommé jdearglist.txt.</span><span class="sxs-lookup"><span data-stu-id="30a52-125">To enter a value that will be right-justified, you must enter the parameter in a file called jdearglist.txt.</span></span> <span data-ttu-id="30a52-126">Ce dernier est lu lorsque vous générez le schéma.</span><span class="sxs-lookup"><span data-stu-id="30a52-126">The jdearglist.txt is read when you generate the schema.</span></span> <span data-ttu-id="30a52-127">Chaque valeur de ce fichier texte est automatiquement convertie en une valeur alignée à droite et remplie à gauche avec des espaces vides.</span><span class="sxs-lookup"><span data-stu-id="30a52-127">Any value in this text file is automatically converted to a right-justified value and padded on the left with blanks.</span></span>  
  
 <span data-ttu-id="30a52-128">Vous devez créer le fichier jdearglist.txt à l'aide d'un éditeur de texte, avec des entrées décrivant ces paramètres, puis l'enregistrer dans le dossier suivant :</span><span class="sxs-lookup"><span data-stu-id="30a52-128">You must create jdearglist.txt using a text editor, with entries describing these parameters, and save it in the following folder:</span></span>  
  
 <span data-ttu-id="30a52-129">C:\Program Files\Microsoft BizTalk Adapters\JDEEnterpriseOne\config</span><span class="sxs-lookup"><span data-stu-id="30a52-129">C:\Program Files\Microsoft BizTalk Adapters\JDEEnterpriseOne\config</span></span>  
  
 <span data-ttu-id="30a52-130">Si ce fichier n'existe pas ou est vide, un message est affiché dans le journal de l'adaptateur BizTalk pour JD Edwards EnterpriseOne lors de la première ouverture de l'adaptateur.</span><span class="sxs-lookup"><span data-stu-id="30a52-130">If this file does not exist or is empty, an informational message appears in BizTalk Adapter for JD Edwards EnterpriseOne log when the adapter first opens.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="30a52-131">Si vous modifiez ce fichier après avoir généré votre schéma, vous devez régénérer le schéma pour actualiser les données qu'il contient.</span><span class="sxs-lookup"><span data-stu-id="30a52-131">If you change this file after generating your schema, you must regenerate the schema to refresh the data it contains.</span></span> <span data-ttu-id="30a52-132">Pour vérifier que vous utilisez les dernières informations de ce fichier, vous pouvez utiliser le Gestionnaire des tâches pour arrêter le processus browsingagent.exe avant de générer de nouveau votre schéma. Toutefois, cela ne devrait pas être nécessaire.</span><span class="sxs-lookup"><span data-stu-id="30a52-132">To verify that you are using the latest information in this file, you can use the Task Manager to stop the browsingagent.exe process before regenerating your schema; however, this should not be necessary.</span></span>  
  
 <span data-ttu-id="30a52-133">Voici un exemple du format des entrées dans le fichier jdearglist.txt :</span><span class="sxs-lookup"><span data-stu-id="30a52-133">The following is an example of the format for entries in the jdearglist.txt file:</span></span>  
  
```  
<SourceModule>.<BusinessFunction>.<Argument>  
  
```  
  
 <span data-ttu-id="30a52-134">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="30a52-134">For example:</span></span>  
  
```  
B4200310.F4211FSBeginDoc.szBusinessUnit  
```  
  
 <span data-ttu-id="30a52-135">Pour un ensemble de fonctions commerciales appartenant au même module commercial, des arguments de nom similaire (du même type) sont partagés entre plusieurs ou toutes les fonctions commerciales.</span><span class="sxs-lookup"><span data-stu-id="30a52-135">For a set of business functions belonging to the same business module, like-named arguments (of the same type) are shared across some or all of the business functions.</span></span> <span data-ttu-id="30a52-136">Vous pouvez utiliser le caractère générique astérisque (\*) au lieu du nom de fonction commerciale.</span><span class="sxs-lookup"><span data-stu-id="30a52-136">You can use the wildcard character (\*) instead of the business function name.</span></span> <span data-ttu-id="30a52-137">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="30a52-137">For example:</span></span>  
  
```  
B4200310.*.szBusinessUnit  
  
```  
  
> [!NOTE]
>  <span data-ttu-id="30a52-138">Lors de l'importation d'un processus d'entreprise JD Edwards EnterpriseOne sur un autre ordinateur, vous devez copier jdearglist.txt manuellement.</span><span class="sxs-lookup"><span data-stu-id="30a52-138">When importing a JD Edwards EnterpriseOne business process to another computer, you must copy jdearglist.txt manually.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30a52-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="30a52-139">See Also</span></span>  
 [<span data-ttu-id="30a52-140">Annexe B : Types de données</span><span class="sxs-lookup"><span data-stu-id="30a52-140">Appendix B: Data Types</span></span>](../core/appendix-b-data-types.md)