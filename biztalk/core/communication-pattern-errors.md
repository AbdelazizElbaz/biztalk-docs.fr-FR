---
title: "Erreurs de modèle de communication | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 06656073-9bae-4d6f-98ae-2714a72ee79c
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 36677694b8f2d0973c04d942a196d055b696bd5c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="communication-pattern-errors"></a>Erreurs en relation avec les modèles de communication
Informations sur le diagnostic et résolution des erreurs de modèle de Communication WCF.  

## <a name="fault-messages-are-not-supported-on-one-way-ports"></a>Les messages d'erreur ne sont pas pris en charge sur les ports unidirectionnels
  
||Détails de l’erreur|  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|ID d'événement|0|  
|Source de l'événement|0|  
|Composant|0|  
|Nom symbolique|0|  
|Texte du message|Les messages d'erreur ne sont pas pris en charge sur les ports unidirectionnels. Corrigez le type de port de description « {0} » de service « {{1} », puis réexécutez l’Assistant|  
  
## <a name="explanation"></a>Explication  
 Cette erreur indique que le service que vous tentez d'utiliser est unidirectionnel et qu'une erreur a été spécifiée.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour corriger le service, passez du modèle de communication unidirectionnel au modèle de communication de requête-réponse. Vous pouvez également supprimer l'erreur dans le code.
 
 