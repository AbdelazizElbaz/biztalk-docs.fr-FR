---
title: "Délimiteurs ne sont pas uniques | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1c37cc55-8923-4124-9004-91ee5093df9c
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8cc4f9c8eeb3a16fdd45222313bfb013dbf32ae5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="delimiters-are-not-unique"></a>Les délimiteurs ne sont pas uniques.
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur EDI|  
|Nom symbolique|-|  
|Texte du message|Les délimiteurs ne sont pas uniques.|  
  
## <a name="explanation"></a>Explication  
 Cet événement de type erreur/avertissement/information indique que le pipeline d'envoi EDI n'a pas pu traiter un échange sortant, car au moins deux des séparateurs identifiés dans l'échange, et utilisés pour séparer les facets de l'échange, étaient identiques. Les séparateurs sont identifiés dans le segment ISA d'un échange X12 et dans le segment UNA d'un échange EDIFACT. Deux séparateurs ou plus peuvent présenter la même valeur dans un scénario de lot conservé ou si un échange est reçu via une transmission de transfert et récupéré par le port d'envoi sous la forme d'un fichier XML dans MessageBox. Cette erreur provoque l'échec du traitement de l'échange.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, identifiez les séparateurs de l'échange qui présentent la même valeur, puis modifiez la valeur de l'un d'eux.