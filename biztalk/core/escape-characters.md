---
title: "Caractères d’échappement | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3af800b9-d31b-487a-9a06-6eda47d1574e
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7e961a205b77a9944a497d6e6cbed0df71f63e03
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="escape-characters"></a><span data-ttu-id="83b2c-102">Caractères d’échappement</span><span class="sxs-lookup"><span data-stu-id="83b2c-102">Escape Characters</span></span>

## <a name="overview"></a><span data-ttu-id="83b2c-103">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="83b2c-103">Overview</span></span>
<span data-ttu-id="83b2c-104">Un caractère d'échappement est un caractère unique qui supprime toute signification du caractère qui le suit.</span><span class="sxs-lookup"><span data-stu-id="83b2c-104">An escape character is a single character that suppresses any special meaning of the character that follows it.</span></span> <span data-ttu-id="83b2c-105">Pour exemple, si vous définissez un enregistrement de fichier plat comme présentant les caractéristiques suivantes :</span><span class="sxs-lookup"><span data-stu-id="83b2c-105">For example, if you define a flat file record as having the following characteristics:</span></span>  
  
-   <span data-ttu-id="83b2c-106">Nom = Record1</span><span class="sxs-lookup"><span data-stu-id="83b2c-106">Name = Record1</span></span>  
  
-   <span data-ttu-id="83b2c-107">Délimité</span><span class="sxs-lookup"><span data-stu-id="83b2c-107">Delimited</span></span>  
  
-   <span data-ttu-id="83b2c-108">Délimiteur enfant = virgule (,)</span><span class="sxs-lookup"><span data-stu-id="83b2c-108">Child delimiter = comma character (,)</span></span>  
  
-   <span data-ttu-id="83b2c-109">Classement enfant = préfixe</span><span class="sxs-lookup"><span data-stu-id="83b2c-109">Child order = prefix</span></span>  
  
-   <span data-ttu-id="83b2c-110">Caractère d’échappement = barre oblique inverse (\\)</span><span class="sxs-lookup"><span data-stu-id="83b2c-110">Escape character = backslash character (\\)</span></span>  
  
-   <span data-ttu-id="83b2c-111">Balise = RECORD1</span><span class="sxs-lookup"><span data-stu-id="83b2c-111">Tag = RECORD1</span></span>  
  
-   <span data-ttu-id="83b2c-112">Deux champs nommés Field1 et Field2</span><span class="sxs-lookup"><span data-stu-id="83b2c-112">Two fields named Field1 and Field2</span></span>  
  
 <span data-ttu-id="83b2c-113">Ensuite, les données de fichier plat suivantes s'appliquent à l'enregistrement.</span><span class="sxs-lookup"><span data-stu-id="83b2c-113">Then the following flat file data applies for the record.</span></span>  
  
```  
RECORD1,testfield1\,testfield1,testfield2  
                  ^^  
  
```  
  
 <span data-ttu-id="83b2c-114">Les données seront désassemblées dans le fragment suivant de XML.</span><span class="sxs-lookup"><span data-stu-id="83b2c-114">The data will be disassembled into the following fragment of XML.</span></span>  
  
```  
<Record1>  
    <Field1>testfield1,testfield1</Field1>  
    <Field2>testfield2</Field2>  
</Record1>  
  
```  
  
 <span data-ttu-id="83b2c-115">Notez que la séquence de caractère d’échappement `\,` figurant sur la ligne suivant l'enregistrement de fichier plat a été convertie en une virgule seule sans caractère d'échappement dans les données du champ Field1 dans l'enregistrement XML équivalent.</span><span class="sxs-lookup"><span data-stu-id="83b2c-115">Note that the escape character sequence `\,` indicated on the line following the flat file record, has been converted to a single comma character without the escape character in the data for Field1 in the equivalent XML record.</span></span> <span data-ttu-id="83b2c-116">De plus, cette virgule n'a pas été interprétée comme un séparateur de champs comme l’étaient les deux autres virgules.</span><span class="sxs-lookup"><span data-stu-id="83b2c-116">Furthermore, that comma character was not interpreted as a field delimiter like the other two commas are.</span></span>  
  
 <span data-ttu-id="83b2c-117">Lorsque l'assembleur de fichier plat effectue l'opération inverse, convertissant la version XML de l'enregistrement en son équivalent en fichier plat, le caractère d'échappement est inséré avant la virgule, au milieu de Field1, indiquant ainsi qu’il doit être interprété comme une donnée et non comme un délimiteur de champ.</span><span class="sxs-lookup"><span data-stu-id="83b2c-117">When the flat file assembler performs the reverse operation, converting the XML version of the record to its equivalent flat file record, the escape character will be inserted before the comma in the middle of Field1, thereby indicating that it should be interpreted as data rather than as a field delimiter.</span></span>  
  
 <span data-ttu-id="83b2c-118">Lorsque vous créez un schéma de fichier plat à l’aide de l’Éditeur BizTalk, vous pouvez définir un caractère d’échappement par défaut pour l’ensemble du schéma à l’aide de la **de caractères d’échappement par défaut** et **Type de caractère d’échappement par défaut** propriétés de la **schéma** nœud.</span><span class="sxs-lookup"><span data-stu-id="83b2c-118">When creating a flat file schema using BizTalk Editor, you can define a default escape character for the entire schema using the **Default Escape Character** and **Default Escape Character Type** properties of the **Schema** node.</span></span> <span data-ttu-id="83b2c-119">Vous pouvez ensuite configurer chaque enregistrement individuel dans le schéma à utiliser ce caractère d’échappement par défaut ou un caractère d’échappement personnalisée, spécifiques à l’enregistrement à l’aide de la **caractère d’échappement]** et **le Type de caractère d’échappement**propriétés de la **enregistrement** nœud.</span><span class="sxs-lookup"><span data-stu-id="83b2c-119">Then, you can configure each individual record in the schema to either use this default escape character or a custom, record-specific escape character using the **Escape Character]** and **Escape Character Type** properties of the **Record** node.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83b2c-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="83b2c-120">See Also</span></span>  
- [<span data-ttu-id="83b2c-121">Comment interpréter les caractères spéciaux dans le cadre d’une valeur de champ</span><span class="sxs-lookup"><span data-stu-id="83b2c-121">Ways to Interpret Special Characters as Part of a Field Value</span></span>](../core/ways-to-interpret-special-characters-as-part-of-a-field-value.md)  
- <span data-ttu-id="83b2c-122">Séquence d’échappement de caractères, propriétés [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]:</span><span class="sxs-lookup"><span data-stu-id="83b2c-122">Escape character properties  [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]:</span></span>  
    - <span data-ttu-id="83b2c-123">Caractère d’échappement par défaut (propriété de nœud des schémas de fichier plat)</span><span class="sxs-lookup"><span data-stu-id="83b2c-123">Default Escape Character (Node Property of Flat File Schemas)</span></span>
    - <span data-ttu-id="83b2c-124">Type de caractère d’échappement par défaut (propriété de nœud des schémas de fichier plat)</span><span class="sxs-lookup"><span data-stu-id="83b2c-124">Default Escape Character Type (Node Property of Flat File Schemas)</span></span>
    - <span data-ttu-id="83b2c-125">Caractère d’échappement (propriété de nœud des schémas de fichier plat)</span><span class="sxs-lookup"><span data-stu-id="83b2c-125">Escape Character (Node Property of Flat File Schemas)</span></span>  
    - <span data-ttu-id="83b2c-126">Type de caractère (propriété de nœud des schémas de fichier plat) d’échappement</span><span class="sxs-lookup"><span data-stu-id="83b2c-126">Escape Character Type (Node Property of Flat File Schemas)</span></span>