---
title: "Encapsuler les caractères | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d7268f46-9bf6-4c76-9b3a-b4ee0e8db997
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f95ed10811232b15762c31bfc435ac7772a53b3d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="wrap-characters"></a><span data-ttu-id="7a2bf-102">Encapsuler des caractères</span><span class="sxs-lookup"><span data-stu-id="7a2bf-102">Wrap Characters</span></span>

## <a name="overview"></a><span data-ttu-id="7a2bf-103">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="7a2bf-103">Overview</span></span>
<span data-ttu-id="7a2bf-104">Un caractère de retour à la ligne est un caractère unique utilisé pour renvoyer les caractères de données à la ligne dans un champ afin de supprimer toute signification spéciale que ces caractères de données auraient sinon.</span><span class="sxs-lookup"><span data-stu-id="7a2bf-104">A wrap character is a single character that is used to wrap the data characters in a field for the purpose of suppressing any special meaning that any of those data characters would otherwise have.</span></span> <span data-ttu-id="7a2bf-105">Pour exemple, si vous définissez un enregistrement de fichier plat comme présentant les caractéristiques suivantes :</span><span class="sxs-lookup"><span data-stu-id="7a2bf-105">For example, if you define a flat file record as having the following characteristics:</span></span>  
  
-   <span data-ttu-id="7a2bf-106">Nom = Record1</span><span class="sxs-lookup"><span data-stu-id="7a2bf-106">Name = Record1</span></span>  
  
-   <span data-ttu-id="7a2bf-107">Délimité</span><span class="sxs-lookup"><span data-stu-id="7a2bf-107">Delimited</span></span>  
  
-   <span data-ttu-id="7a2bf-108">Délimiteur enfant = virgule (,)</span><span class="sxs-lookup"><span data-stu-id="7a2bf-108">Child delimiter = comma character (,)</span></span>  
  
-   <span data-ttu-id="7a2bf-109">Classement enfant = infix</span><span class="sxs-lookup"><span data-stu-id="7a2bf-109">Child order = infix</span></span>  
  
-   <span data-ttu-id="7a2bf-110">Caractère d’échappement = barre oblique inverse (\\)</span><span class="sxs-lookup"><span data-stu-id="7a2bf-110">Escape character = backslash character (\\)</span></span>  
  
-   <span data-ttu-id="7a2bf-111">Balise = RECORD1</span><span class="sxs-lookup"><span data-stu-id="7a2bf-111">Tag = RECORD1</span></span>  
  
-   <span data-ttu-id="7a2bf-112">Trois champs nommés Field1, Field2 et Field3, chacun défini de manière à utiliser le signe dièse (#) comme leur caractère de retour à la ligne.</span><span class="sxs-lookup"><span data-stu-id="7a2bf-112">Three fields named Field1, Field2, and Field3, each defined to use the number sign character (#) as their wrap character.</span></span>  
  
 <span data-ttu-id="7a2bf-113">Ensuite, les données de fichier plat suivantes s'appliquent à l'enregistrement.</span><span class="sxs-lookup"><span data-stu-id="7a2bf-113">Then the following flat file data applies for the record.</span></span>  
  
```  
RECORD1#field1#,#field2#,#field3#  
  
```  
  
 <span data-ttu-id="7a2bf-114">Les données sont désassemblées dans le fragment suivant de XML.</span><span class="sxs-lookup"><span data-stu-id="7a2bf-114">The data is disassembled into the following fragment of XML.</span></span>  
  
```  
<Record1>  
    <Field1></Field1>  
    <Field2></Field2>  
    <Field3></Field3>  
</Record1>  
  
```  
  
 <span data-ttu-id="7a2bf-115">Notez que les caractères de retour à la ligne (#) entourant les caractères de données en gras field1, field2 et field3 ont été supprimés.</span><span class="sxs-lookup"><span data-stu-id="7a2bf-115">Note that the wrap characters (#) surrounding the bolded data characters field1, field2, and field3 have been removed.</span></span>  
  
 <span data-ttu-id="7a2bf-116">Lorsque l’assembleur de fichier plat effectue l’opération inverse, de convertir la version XML de l’enregistrement de son enregistrement de fichier plat équivalent, les caractères de retour à la ligne sont insérés avant et après les caractères de données de chacun des champs, on obtient la séquence d’origine de caractères de fichier plat.</span><span class="sxs-lookup"><span data-stu-id="7a2bf-116">When the flat file assembler performs the reverse operation, converting the XML version of the record to its equivalent flat file record, the wrap characters are inserted before and after the data characters of each of the fields, yielding the original sequence of flat file characters.</span></span>  
  
 <span data-ttu-id="7a2bf-117">Le caractère d'échappement défini peut être utilisé conjointement avec le caractère de retour à la ligne défini.</span><span class="sxs-lookup"><span data-stu-id="7a2bf-117">The defined escape character can be used in conjunction with the defined wrap character.</span></span> <span data-ttu-id="7a2bf-118">Supposez par exemple que la valeur de Field1 soit modifiée comme suit (texte en gras).</span><span class="sxs-lookup"><span data-stu-id="7a2bf-118">For example, suppose the value of Field1 is changed as follows (shown in bold type).</span></span>  
  
```  
<Record1>  
    <Field1></Field1>  
    <Field2>field2</Field2>  
    <Field3>field3</Field3>  
</Record1>  
  
```  
  
 <span data-ttu-id="7a2bf-119">Lorsque ce fragment XML sera assemblé, à l'aide des définitions d'enregistrement et de champ fournies, la séquence suivante de caractères de fichier plat sera produite (la séquence de caractères d'échappement et de dièses est en gras).</span><span class="sxs-lookup"><span data-stu-id="7a2bf-119">When this XML fragment is assembled, using the record and field definitions provided, the following sequence of flat file characters is produced (the escaped number sign character sequence is shown in bold type).</span></span>  
  
```  
RECORD1#field1#,#field2#,#field3#  
  
```  
  
 <span data-ttu-id="7a2bf-120">Lorsque vous créez un schéma de fichier plat à l’aide de l’Éditeur BizTalk, vous pouvez définir un caractère de retour à la ligne par défaut pour l’ensemble du schéma à l’aide de la **Default Wrap Character** et **par défaut caractère de retour** propriétés de la **Schéma** nœud.</span><span class="sxs-lookup"><span data-stu-id="7a2bf-120">When creating a flat file schema using BizTalk Editor, you can define a default wrap character for the entire schema using the **Default Wrap Character** and **Default Wrap Character Type** properties of the **Schema** node.</span></span> <span data-ttu-id="7a2bf-121">Vous pouvez ensuite configurer chaque champ dans le schéma à utiliser ce caractère de retour à la ligne par défaut ou un caractère personnalisé, spécifiques aux champs de type wrap à l’aide de la **Wrap Character** et **caractère de retour** propriétés de la **Fieldelement** ou **attribut de champ** nœuds dans les schémas de fichier plat.</span><span class="sxs-lookup"><span data-stu-id="7a2bf-121">Then, you can configure each individual field in the schema to either use this default wrap character or a custom, field-specific wrap character using the **Wrap Character** and **Wrap Character Type** properties of the **Field Element** or **Field Attribute** nodes in flat file schemas.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="7a2bf-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7a2bf-122">See Also</span></span>  
- [<span data-ttu-id="7a2bf-123">Comment interpréter les caractères spéciaux dans le cadre d’une valeur de champ</span><span class="sxs-lookup"><span data-stu-id="7a2bf-123">Ways to Interpret Special Characters as Part of a Field Value</span></span>](../core/ways-to-interpret-special-characters-as-part-of-a-field-value.md)  
- <span data-ttu-id="7a2bf-124">Encapsuler les propriétés de caractères [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]:</span><span class="sxs-lookup"><span data-stu-id="7a2bf-124">Wrap character properties [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]:</span></span>  
    -  <span data-ttu-id="7a2bf-125">Caractère de retour par défaut (propriété de nœud des schémas de fichier plat</span><span class="sxs-lookup"><span data-stu-id="7a2bf-125">Default Wrap Character (Node Property of Flat File Schemas</span></span>
    -  <span data-ttu-id="7a2bf-126">Type de caractère de retour à la ligne par défaut (propriété de nœud des schémas de fichier plat</span><span class="sxs-lookup"><span data-stu-id="7a2bf-126">Default Wrap Character Type (Node Property of Flat File Schemas</span></span>
    -  <span data-ttu-id="7a2bf-127">Encapsuler des caractères (propriété de nœud des schémas de fichier plat</span><span class="sxs-lookup"><span data-stu-id="7a2bf-127">Wrap Character (Node Property of Flat File Schemas</span></span>  
    -  <span data-ttu-id="7a2bf-128">Encapsuler le Type de caractère (propriété de nœud des schémas de fichier plat</span><span class="sxs-lookup"><span data-stu-id="7a2bf-128">Wrap Character Type (Node Property of Flat File Schemas</span></span>