---
title: "Délimiteurs ne sont pas uniques, le séparateur de champs et de segments sont les mêmes | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1441434a-e969-4803-8e44-c7738d9b23ed
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 440ffb1213936fba4b08a8ee478f6c141eba38fc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="delimiters-are-not-unique-field-and-segment-separator-are-the-same"></a>Les délimiteurs ne sont pas uniques. Les séparateurs de champs et de segments sont identiques
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur EDI|  
|Nom symbolique|-|  
|Texte du message|Les délimiteurs ne sont pas uniques. Les séparateurs de champs et de segments sont identiques|  
  
## <a name="explanation"></a>Explication  
 Cet événement de type erreur/avertissement/information indique que le pipeline d'envoi EDI n'a pas pu traiter un échange sortant, car l'élément de données et les séparateurs de segments avaient la même valeur. Dans un échange X12, le séparateur d'éléments de données est le caractère se trouvant à la quatrième position du segment ISA et le terminateur de segment est le caractère figurant en dernière position du segment ISA. Dans un échange EDIFACT, le séparateur d'éléments de données est le caractère figurant dans le champ UNA2 et le terminateur de segment est le caractère figurant dans le champ UNA6. Une situation où deux séparateurs possèdent la même valeur peut se produire dans un scénario de lot conservé (mais provoquera une condition d'erreur) ou lorsqu'un échange est reçu via une transmission PassThrough, puis récupéré en tant que fichier XML dans MessageBox par le port d'envoi.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, modifiez la valeur de l'élément de données ou du séparateur de segments dans l'échange, puis soumettez à nouveau ce dernier.