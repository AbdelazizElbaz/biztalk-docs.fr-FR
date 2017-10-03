---
title: "Un élément de fin est introuvable à la profondeur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a1edb60a-122a-4fe9-8d73-96521fe7326b
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4a90265b4348e4d35b66099f426b6f6177851ccc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="an-end-element-could-not-be-found-at-depth"></a>Un élément de fin à la profondeur n'a pas pu être trouvé
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur EDI|  
|Nom symbolique|EndElementNotFoundAtDepth|  
|Texte du message|Un élément de fin à la profondeur {0} n'a pas pu être trouvé|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'erreur/d'avertissement/d'informations indique que BizTalk Server n'a pas pu traiter l'échange sortant car la validation du message XML a échoué. Le message XML ne contenait pas de balise de fin pour un en-tête ou élément de données.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, ajoutez la balise ou le code de fin approprié au message XML, puis renvoyez-le.