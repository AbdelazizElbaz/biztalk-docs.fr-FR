---
title: "Délimiteurs ne sont pas uniques, les séparateurs de segments et de composants sont les mêmes | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 13c41899-02af-4678-a4ad-f3dc48c1fdfb
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 69475949b404474ff4dc9fe53d553c24e125939c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="delimiters-are-not-unique-segment-and-component-separators-are-the-same"></a>Les délimiteurs ne sont pas uniques, les séparateurs de segments et de composants sont identiques
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur EDI|  
|Nom symbolique|-|  
|Texte du message|Les délimiteurs ne sont pas uniques, les séparateurs de segments et de composants sont identiques|  
  
## <a name="explanation"></a>Explication  
 Cet événement de type erreur/avertissement/information indique que le pipeline d'envoi EDI n'a pas pu traiter un échange sortant, car le terminateur de segment ou le séparateur de composants avaient la même valeur. Dans un échange X12, le terminateur de segment correspond au caractère situé en dernière position du segment ISA, alors que le séparateur de composants est le caractère situé dans le champ ISA16. Dans un échange EDIFACT, le terminateur de segment correspond au caractère du champ UNA6, alors que le séparateur de composants est le caractère situé dans le champ UNA1. Une situation où deux séparateurs possèdent la même valeur peut se produire dans un scénario de lot conservé (mais provoquera une condition d'erreur) ou lorsqu'un échange est reçu via une transmission PassThrough, puis récupéré en tant que fichier XML dans MessageBox par le port d'envoi.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, modifiez la valeur du terminateur de segment ou du séparateur de composants dans l'échange, puis soumettez à nouveau ce dernier.