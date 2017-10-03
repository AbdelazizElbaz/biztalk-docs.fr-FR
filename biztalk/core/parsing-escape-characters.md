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
# <a name="parsing-escape-characters"></a>L’analyse des caractères d’échappement
Lorsque l'analyseur rencontre un caractère d'échappement qui sert de préfixe à un caractère normal (c'est-à-dire un délimiteur sans séquence d'échappement, sans retour à la ligne, non effectif, ou tout autre caractère spécial), le caractère d'échappement est ignoré. Par exemple, prenons une chaîne « abc\d » où «\\» est le caractère d’échappement, la sortie est « abcd ».  
  
 Si l’analyseur rencontre un double caractère d’échappement (par exemple, « abc\\\d »), la sortie inclut un seul caractère d’échappement (« abc\d »).  
  
 Si l’analyseur rencontre trois caractères d’échappement (par exemple, abc\\\\\d), la sortie est « abc\d », car les premiers caractères de deux échappement sont analysés comme «\\» et le troisième caractère d’échappement est ignoré.  
  
 L'analyseur traite les délimiteurs mal placés comme des caractères normaux. Par exemple, si « Record, Field1, Field, 2 » est reçu, la sortie XML est \<Field1 > \<Field, 2 >.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation du moteur d’analyse de fichier plat](../core/using-the-flat-file-parsing-engine.md)