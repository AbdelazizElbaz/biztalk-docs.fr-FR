---
title: "L’analyse des caractères d’échappement | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipeline components [custom], code samples
- pipeline components [custom], escape characters
- pipeline components [custom], parsing
ms.assetid: 2b33f436-3c29-4ff5-8dfa-26d6591713bc
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 50e65ccbe1a1197a3b85ec86a8ae9e11f25eaf61
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="parsing-escape-characters"></a><span data-ttu-id="c0b66-102">L’analyse des caractères d’échappement</span><span class="sxs-lookup"><span data-stu-id="c0b66-102">Parsing Escape Characters</span></span>
<span data-ttu-id="c0b66-103">Lorsque l'analyseur rencontre un caractère d'échappement qui sert de préfixe à un caractère normal (c'est-à-dire un délimiteur sans séquence d'échappement, sans retour à la ligne, non effectif, ou tout autre caractère spécial), le caractère d'échappement est ignoré.</span><span class="sxs-lookup"><span data-stu-id="c0b66-103">When the parser encounters an escape character that prefixes a regular character (that is, one that is not a delimiter or other special character), the escape character is ignored.</span></span> <span data-ttu-id="c0b66-104">Par exemple, prenons une chaîne « abc\d » où «\\» est le caractère d’échappement, la sortie est « abcd ».</span><span class="sxs-lookup"><span data-stu-id="c0b66-104">For example, given a string "abc\d" where "\\" is the escape character, the output is "abcd".</span></span>  
  
 <span data-ttu-id="c0b66-105">Si l’analyseur rencontre un double caractère d’échappement (par exemple, « abc\\\d »), la sortie inclut un seul caractère d’échappement (« abc\d »).</span><span class="sxs-lookup"><span data-stu-id="c0b66-105">If the parser encounters a double escape character (for example, "abc\\\d"), the output includes a single escape character ("abc\d").</span></span>  
  
 <span data-ttu-id="c0b66-106">Si l’analyseur rencontre trois caractères d’échappement (par exemple, abc\\\\\d), la sortie est « abc\d », car les premiers caractères de deux échappement sont analysés comme «\\» et le troisième caractère d’échappement est ignoré.</span><span class="sxs-lookup"><span data-stu-id="c0b66-106">If the parser encounters three escape characters (for example, abc\\\\\d), the output is "abc\d" because the first two escape characters are parsed to "\\" and the third escape character is ignored.</span></span>  
  
 <span data-ttu-id="c0b66-107">L'analyseur traite les délimiteurs mal placés comme des caractères normaux.</span><span class="sxs-lookup"><span data-stu-id="c0b66-107">The parser treats misplaced delimiters as regular characters.</span></span> <span data-ttu-id="c0b66-108">Par exemple, si « Record, Field1, Field, 2 » est reçu, la sortie XML est \<Field1 > \<Field, 2 >.</span><span class="sxs-lookup"><span data-stu-id="c0b66-108">For example, if "Record, Field1, Field,2" is received, the output XML is \<Field1> \<Field,2>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0b66-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c0b66-109">See Also</span></span>  
 [<span data-ttu-id="c0b66-110">Utilisation du moteur d’analyse de fichier plat</span><span class="sxs-lookup"><span data-stu-id="c0b66-110">Using the Flat File Parsing Engine</span></span>](../core/using-the-flat-file-parsing-engine.md)