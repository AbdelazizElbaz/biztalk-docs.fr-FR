---
title: "X12 jeu de caractères EDI | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 76e7b327-b0bd-4f16-8bfe-6c0184059f2b
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 46bcf25317d38846c6376b1fa25572b926c92992
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="x12-edi-character-set"></a>Jeu de caractères X12 EDI
Lorsque vous utilisez le caractère Ñ ou un accent grave ('), spécifiez les éléments suivants :  
  
||Jeu de caractères|  
|-|-------------------|  
|Seul le caractère Ñ dans le document EDI|Utiliser le jeu de caractères étendu|  
|Seul un accent grave (`) dans le document EDI|Utiliser le jeu de caractères  UTF-8|  
|Le caractère Ñ **et** un accent grave (') dans le même document :|-Le document entrant doit avoir l’encodage UTF-8<br />-Utiliser le jeu de caractères UTF-8|  
  
 Les liens suivants fournissent davantage d’informations sur les jeux de caractères EDI :  
  
 [Jeux de caractères EDI](http://go.microsoft.com/fwlink/p/?LinkId=271249)  
  
 [Prise en charge du jeu de caractères EDI](http://go.microsoft.com/fwlink/p/?LinkId=271250)