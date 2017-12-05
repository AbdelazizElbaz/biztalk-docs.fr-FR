---
title: "Élément racine inattendu | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ecccf57e-9295-4a6d-95b6-efec662478cf
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ec4ed8e39a05f81984dca21794eca3d829ba8f42
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="unexpected-root-element"></a>Élément racine inattendu
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|ID d'événement|0|  
|Source de l'événement|0|  
|Composant|0|  
|Nom symbolique|0|  
|Texte du message|Élément racine inattendu|  
  
## <a name="explanation"></a>Explication  
 Propriété d’en-tête ne figure pas dans \<en-têtes\>...\</headers\> format. Cette situation s'applique généralement à InboundHeaders et OutboundCustomHeaders.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Assurez-vous que la propriété d’en-tête est au format \<en-têtes\>... \</headers\>.