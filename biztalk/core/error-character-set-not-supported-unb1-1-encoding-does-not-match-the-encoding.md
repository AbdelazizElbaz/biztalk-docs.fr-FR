---
title: "Set non pris en charge, car les informations de codage en UNB1.1 ne correspondent pas au codage réel de caractères | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 085ea8e3-e0d8-45bd-9985-6787b00e4d5a
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 41a6eafbb0e71de5f13e792361cdc0d1fc338088
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="character-set-not-supported-because-the-encoding-information-in-unb11-does-not-match-the-actual-encoding"></a>Jeu de caractères non pris en charge car les informations de codage en UNB1.1 ne correspondent pas au codage réel.
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur EDI|  
|Nom symbolique|-|  
|Texte du message|Jeu de caractères non pris en charge. Ceci peut être dû au fait que les informations de codage en UNB1.1 ne correspondent pas au codage réel de l'échange.|  
  
## <a name="explanation"></a>Explication  
 Cet événement de type erreur/avertissement/information indique que le pipeline de réception EDI n'a pas pu traiter l'échange EDIFACT entrant, car les caractères utilisés dans l'échange n'étaient pas conformes au jeu de caractères identifié dans le champ UNB1.1 de l'échange.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, effectuez l’une des opérations suivantes :  
  
-   Modifiez les caractères utilisés dans l'échange afin qu'ils soient conformes au jeu de caractères défini dans le champ UNB1.1 de l'échange.  
  
-   Modifiez le jeu de caractères défini dans le champ UNB1.1 de l'échange, afin que tous les caractères de l'échange fassent partie du jeu de caractères.