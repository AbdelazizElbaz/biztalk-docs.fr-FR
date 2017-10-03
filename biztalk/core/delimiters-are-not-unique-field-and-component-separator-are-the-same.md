---
title: "Délimiteurs ne sont pas uniques, de champ et le séparateur de composants sont les mêmes | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cba15b30-b07d-4caa-8c43-6b4d8c4ca81c
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5f803612a905f0be196afcfc0b43af23501ccdf0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="delimiters-are-not-unique-field-and-component-separator-are-the-same"></a>Les délimiteurs ne sont pas uniques. Les séparateurs de champs et de composants sont identiques
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur EDI|  
|Nom symbolique|-|  
|Texte du message|Les délimiteurs ne sont pas uniques. Les séparateurs de champs et de composants sont identiques|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline d'envoi EDI n'a pas pu traiter un échange sortant, car l'élément de données et les séparateurs de composants ont la même valeur. Dans un échange X12, le séparateur d'éléments de données correspond au caractère situé en quatrième position du segment ISA et le séparateur de composants correspond au caractère dans le champ ISA16. Dans un échange EDIFACT, le séparateur d'éléments de données correspond au caractère dans le champ UNA2 et le séparateur de composants correspond au caractère dans le champ UNA1. Une situation où deux séparateurs possèdent la même valeur peut se produire dans un scénario de lot conservé (mais provoquera une condition d'erreur) ou lorsqu'un échange est reçu via une transmission PassThrough, puis récupéré en tant que fichier XML dans MessageBox par le port d'envoi.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, modifiez la valeur de l'élément de données ou celle des séparateurs de composants, puis renvoyez l'échange.