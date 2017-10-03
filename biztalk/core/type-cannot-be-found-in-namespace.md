---
title: "Type est introuvable dans l’espace de noms | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 66387fa6-3ba3-499f-99d6-bb0033c68adc
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 515dd9b6b73b43bee22ffc7b67745bb45adcaf6c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="type-cannot-be-found-in-namespace"></a>Type introuvable dans l'espace de noms
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|ID d'événement|0|  
|Source de l'événement|0|  
|Composant|0|  
|Nom symbolique|0|  
|Texte du message|Erreur : Le Type « {0} » ne peut pas être trouvé dans l’espace de noms « {{1} »|  
  
## <a name="explanation"></a>Explication  
 Cette erreur indique que des artefacts créés font référence à des types introuvables dans l'espace de noms spécifié.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Ajoutez une référence contenant le type introuvable, puis réexécutez l'Assistant (si vous êtes le propriétaire du service WCF que vous tentez d'utiliser). Sinon, contactez le fournisseur de services.