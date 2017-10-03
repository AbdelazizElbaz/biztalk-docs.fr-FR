---
title: "Nombre de documents informatisés inclus ne correspond pas | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: db958803-4667-4558-81a6-70c62d6fe8bf
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 16a28544757c3e9ae75dd7230673c4526fc2c8f2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="number-of-included-transaction-sets-do-not-match"></a>Le nombre de documents informatisés inclus ne correspond pas
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur EDI|  
|Nom symbolique|X12FaNumberOfTsMismatchDescription|  
|Texte du message|Le nombre de documents informatisés inclus ne correspond pas|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'erreur/d'avertissement/d'informations indique que le nombre de documents informatisés dans le groupe de l'échange X12 n'est pas égal au nombre dans le code de fin du groupe (champ GE01). Cette situation se produit lorsque l'échange est conservé et que celui-ci est interrompu en cas d'erreur. (Le message d'erreur n'est pas publié dans deux cas : lorsque l'échange est conservé et que les documents informatisés sont interrompus en cas d'erreur et lorsque l'échange est fractionné).  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, assurez-vous que le nombre dans le champ GE01 du code de fin du groupe est identique au nombre de documents informatisés dans le groupe de l'échange, puis renvoyez l'échange.