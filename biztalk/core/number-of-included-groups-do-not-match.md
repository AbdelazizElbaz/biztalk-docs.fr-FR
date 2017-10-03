---
title: Nombre de groupes inclus ne correspond pas | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1d61ac17-92cd-4a5e-81e6-e2c6fc4085bb
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2f02262012a5d02cebaf86fae5a4d19d9b5486d1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="number-of-included-groups-do-not-match"></a>Le nombre de groupes inclus ne correspond pas
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur EDI|  
|Nom symbolique|X12Ta1InvalidNumberOfIncludedGroupsDescription|  
|Texte du message|Nombre d’inclus groupes ne correspondent pas|  
  
## <a name="explanation"></a>Explication  
 Cet événement de type erreur/avertissement/information indique que le nombre de groupes dans l'échange n'est pas égal au nombre figurant dans le code de fin de l'échange (champ IEA01). Cette situation se produit lorsque l'échange est conservé et que celui-ci est interrompu en cas d'erreur. (Le message d'erreur n'est pas publié dans deux cas : lorsque l'échange est conservé et que les documents informatisés sont interrompus en cas d'erreur et lorsque l'échange est fractionné).  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, assurez-vous que le nombre figurant dans le champ IEA01 du code fin de l'échange est identique au nombre de groupes dans l'échange, puis procédez à un nouvel envoi de l'échange.