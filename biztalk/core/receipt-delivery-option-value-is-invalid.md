---
title: "Valeur de Receipt-Delivery-Option n’est pas valide | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0eed306b-0912-4694-a55c-976128117c02
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6f14541cd9c296e6a4527e7c2958123e072be8c6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="receipt-delivery-option-value-is-invalid"></a>Valeur Receipt-Delivery-Option non valide
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur AS2|  
|Nom symbolique|InvalidReceiptDeliveryOptionError|  
|Texte du message|Valeur de Receipt-Delivery-Option : « {0} » n’est pas valide.  {1}|  
  
## <a name="explanation"></a>Explication  
 Cet événement de type erreur/avertissement/information indique que la valeur Receipt-Delivery-Option dans le message AS2 reçu n'est pas une URL valide et n'est pas conforme aux spécifications de la RFC 4130 AS2.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, modifiez Receipt-Delivery-Option dans le message AS2 de sorte à y inclure une URL valide et à ce qu'elle soit conforme aux spécifications de la section 7.3 de la RFC 4130 AS2, puis renvoyez le message AS2.