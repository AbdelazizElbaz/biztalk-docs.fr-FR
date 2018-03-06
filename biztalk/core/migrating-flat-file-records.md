---
title: Migrer des enregistrements de fichier plat | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 75cd5fbc-66c1-4c8b-b81a-1d028e9647b4
caps.latest.revision: 
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ddd43c231077f4e23efca374edbda5bf152f1415
ms.sourcegitcommit: 32f380810b90b70e5df7be72a6a14988a747868e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2018
---
# <a name="migrate-flat-file-records"></a><span data-ttu-id="f4732-102">Migrer des enregistrements de fichier plat</span><span class="sxs-lookup"><span data-stu-id="f4732-102">Migrate Flat File Records</span></span>

## <a name="overview"></a><span data-ttu-id="f4732-103">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="f4732-103">Overview</span></span>
<span data-ttu-id="f4732-104">Microsoft BizTalk Server prend en charge les délimiteurs, bien qu’il prend en charge qu’un seul type de délimiteur : délimiteur enfant.</span><span class="sxs-lookup"><span data-stu-id="f4732-104">Microsoft BizTalk Server supports multi-character delimiters, although it supports only one type of delimiter—child delimiter.</span></span> 
  
 <span data-ttu-id="f4732-105">Trois annotations de schéma contrôlent délimiteur de traitement dans BizTalk Server : deux pour l’analyse (**skip_CR**, **skip_LF**) et une pour la sérialisation (**append_newline**).</span><span class="sxs-lookup"><span data-stu-id="f4732-105">Three schema annotations control delimiter handling in BizTalk Server: two for parsing (**skip_CR**, **skip_LF**), and one for serializing (**append_newline**).</span></span> <span data-ttu-id="f4732-106">BizTalk Server interprète ces annotations comme suit lors de la migration enregistrements :</span><span class="sxs-lookup"><span data-stu-id="f4732-106">BizTalk Server interprets these annotations as follows when migrating records:</span></span>  
  
-   <span data-ttu-id="f4732-107">Si le **skip_CR** annotation a la valeur **true** et le délimiteur actuel n’est pas retour chariot (0x0D), BizTalk Server ajoute un retour chariot au délimiteur actuel.</span><span class="sxs-lookup"><span data-stu-id="f4732-107">If the **skip_CR** annotation has a value of **true** and the current delimiter is not carriage return (0x0D), BizTalk Server adds a carriage return to the current delimiter.</span></span> <span data-ttu-id="f4732-108">Par exemple, si le délimiteur actuel était la barre verticale (0x7C), le délimiteur résultant serait une barre verticale suivie d'un retour chariot (0x7C 0x0D).</span><span class="sxs-lookup"><span data-stu-id="f4732-108">For example, if the current delimiter were the pipe symbol (0x7C), the resulting delimiter is a pipe symbol followed by a carriage return (0x7C 0x0D).</span></span> <span data-ttu-id="f4732-109">Si le délimiteur actuel est un retour chariot, il reste comme seul retour, quelle que soit la valeur de **skip_CR**.</span><span class="sxs-lookup"><span data-stu-id="f4732-109">If the current delimiter is carriage return, it remains as a single carriage return regardless of the value of **skip_CR**.</span></span>  
  
-   <span data-ttu-id="f4732-110">Si le **skip_LF** annotation a la valeur **true**, BizTalk Server ajoute un saut de ligne de caractères (0x0A) au délimiteur actuel.</span><span class="sxs-lookup"><span data-stu-id="f4732-110">If the **skip_LF** annotation has a value of **true**, BizTalk Server adds a linefeed character (0x0A) to the current delimiter.</span></span> <span data-ttu-id="f4732-111">Notez que dans le cas précédent, où le délimiteur actuel est la barre verticale (0x7C), un délimiteur à trois caractères résulte (0x7C 0x0D 0x0A) si les deux **skip_CR** et **skip_LF** sont **lavaleurtrue**.</span><span class="sxs-lookup"><span data-stu-id="f4732-111">Notice that in the preceding case where the current delimiter is the pipe symbol (0x7C), a three character delimiter results (0x7C 0x0D 0x0A) if both **skip_CR** and **skip_LF** are **true**.</span></span>  
  
-   <span data-ttu-id="f4732-112">BizTalk Server ignore le paramètre de la **append_newline** annotation.</span><span class="sxs-lookup"><span data-stu-id="f4732-112">BizTalk Server ignores the setting of the **append_newline** annotation.</span></span>  
  
 <span data-ttu-id="f4732-113">Ces interprétations des annotations garantissent une migration sans difficulté la plupart du temps.</span><span class="sxs-lookup"><span data-stu-id="f4732-113">While these interpretations of the annotations ensure the majority of cases migrate without difficulty, there are some cases where migration fails.</span></span> <span data-ttu-id="f4732-114">Par exemple, si **skip_CR** et **skip_LF** sont tous deux **true** et le délimiteur actuel est la barre verticale (0x7C), BizTalk Server accepte tous les éléments suivants comme valide délimiteurs dans un seul jeu d’enregistrements : 0x7C 0x0D 0x0A, 0x7C 0x0D, 0x7C 0x0A et 0x7C.</span><span class="sxs-lookup"><span data-stu-id="f4732-114">For example, if **skip_CR** and **skip_LF** are both **true** and the current delimiter is the pipe symbol (0x7C), BizTalk Server accepts all of the following as valid delimiters within a single set of records: 0x7C 0x0D 0x0A, 0x7C 0x0D, 0x7C 0x0A, and 0x7C.</span></span> <span data-ttu-id="f4732-115">Enregistrements à l’aide de ces ensembles de délimiteurs ne peuvent pas être migrés et requièrent un code d’analyseur personnalisé dans BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="f4732-115">Records using such sets of delimiters cannot be migrated and require custom parser code in BizTalk Server.</span></span>  
  
 <span data-ttu-id="f4732-116">Bien que BizTalk Server n'ait qu’un seul type de délimiteur, il interprète les anciennes annotations afin que les enregistrements migrent facilement.</span><span class="sxs-lookup"><span data-stu-id="f4732-116">Although BizTalk Server has only one type of delimiter, it interprets the old annotations so that records migrate easily.</span></span> <span data-ttu-id="f4732-117">Si un schéma BizTalk Server comporte des valeurs pour **def_record_delimdef_field_delim**, **def_subfield_delim**, et ils sont référencés dans **delimiter_type** en tant que **inherit_record**, et ainsi de suite, BizTalk Server récupère la valeur correspondante et la stocke localement.</span><span class="sxs-lookup"><span data-stu-id="f4732-117">If a BizTalk Server schema has values for **def_record_delimdef_field_delim**, **def_subfield_delim**, and these are referenced in **delimiter_type** as **inherit_record**, and so on, BizTalk Server retrieves the corresponding value and stores it locally.</span></span>  
  
 <span data-ttu-id="f4732-118">En outre, BizTalk Server ajoute des champs aux enregistrements positionnels marqués sans enfants.</span><span class="sxs-lookup"><span data-stu-id="f4732-118">In addition, BizTalk Server adds fields for tagged positional records without children.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4732-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f4732-119">See Also</span></span>  
 [<span data-ttu-id="f4732-120">Problèmes connus de génération et de validation de schéma</span><span class="sxs-lookup"><span data-stu-id="f4732-120">Known Issues with Schema Generation and Validation</span></span>](../core/known-issues-with-schema-generation-and-validation.md)