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
ms.openlocfilehash: f200e7c68a43360dc9edbae42ebea196b884f577
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="parsing-escape-characters"></a><span data-ttu-id="87dc8-102">L’analyse des caractères d’échappement</span><span class="sxs-lookup"><span data-stu-id="87dc8-102">Parsing Escape Characters</span></span>
<span data-ttu-id="87dc8-103">Lorsque l'analyseur rencontre un caractère d'échappement qui sert de préfixe à un caractère normal (c'est-à-dire un délimiteur sans séquence d'échappement, sans retour à la ligne, non effectif, ou tout autre caractère spécial), le caractère d'échappement est ignoré.</span><span class="sxs-lookup"><span data-stu-id="87dc8-103">When the parser encounters an escape character that prefixes a regular character (that is, one that is not a delimiter or other special character), the escape character is ignored.</span></span> <span data-ttu-id="87dc8-104">Par exemple, prenons une chaîne « abc\d » où «\\» est le caractère d’échappement, la sortie est « abcd ».</span><span class="sxs-lookup"><span data-stu-id="87dc8-104">For example, given a string "abc\d" where "\\" is the escape character, the output is "abcd".</span></span>  
  
 <span data-ttu-id="87dc8-105">Si l’analyseur rencontre un double caractère d’échappement (par exemple, « abc\\\d »), la sortie inclut un seul caractère d’échappement (« abc\d »).</span><span class="sxs-lookup"><span data-stu-id="87dc8-105">If the parser encounters a double escape character (for example, "abc\\\d"), the output includes a single escape character ("abc\d").</span></span>  
  
 <span data-ttu-id="87dc8-106">Si l’analyseur rencontre trois caractères d’échappement (par exemple, abc\\\\\d), la sortie est « abc\d », car les premiers caractères de deux échappement sont analysés comme «\\» et le troisième caractère d’échappement est ignoré.</span><span class="sxs-lookup"><span data-stu-id="87dc8-106">If the parser encounters three escape characters (for example, abc\\\\\d), the output is "abc\d" because the first two escape characters are parsed to "\\" and the third escape character is ignored.</span></span>  
  
 <span data-ttu-id="87dc8-107">L'analyseur traite les délimiteurs mal placés comme des caractères normaux.</span><span class="sxs-lookup"><span data-stu-id="87dc8-107">The parser treats misplaced delimiters as regular characters.</span></span> <span data-ttu-id="87dc8-108">Par exemple, si « Record, Field1, Field, 2 » est reçu, la sortie XML est \<Field1\> \<Field, 2\>.</span><span class="sxs-lookup"><span data-stu-id="87dc8-108">For example, if "Record, Field1, Field,2" is received, the output XML is \<Field1\> \<Field,2\>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87dc8-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="87dc8-109">See Also</span></span>  
 [<span data-ttu-id="87dc8-110">Utilisation du moteur d’analyse de fichier plat</span><span class="sxs-lookup"><span data-stu-id="87dc8-110">Using the Flat File Parsing Engine</span></span>](../core/using-the-flat-file-parsing-engine.md)