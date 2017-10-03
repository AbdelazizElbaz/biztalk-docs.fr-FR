---
title: "Single Sign-On : Événement 10753 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6b538083-180b-4a15-bedf-aac4fc351c30
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6fc43f8ffba195b7a0156a9004d140f1e3c585db
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10753"></a>Single Sign-On : Événement 10753
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10753|  
|Source de l'événement|ENTSSO|  
|Composant|Néant|  
|Nom symbolique|ENTSSO_E_MAPPING_EXISTS|  
|Texte du message|Le mappage existe déjà.|  
  
## <a name="explanation"></a>Explication  
 Ce mappage existe déjà sur le compte Windows utilisé ou le compte externe.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Vérifiez les mappages existants et le mappage que vous tentez de créer. Si le mappage souhaité existe déjà, utilisez-le et supprimez votre nouveau mappage. Sinon, supprimez votre nouveau mappage et recréez-le.