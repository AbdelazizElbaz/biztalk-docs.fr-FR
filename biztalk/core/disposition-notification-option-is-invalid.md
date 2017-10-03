---
title: "Disposition-Notification-Option n’est pas valide | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a1b807a8-eec9-45a5-83cc-075c91b4bc9e
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 72221c98dfcac42f735f63a1ce01a7c26bc45387
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="disposition-notification-option-is-invalid"></a>Disposition-Notification-Option non valide
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur AS2|  
|Nom symbolique|-|  
|Texte du message|Valeur de disposition-Notification-Option : « {0} » n’est pas valide. {1}|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline de réception AS2 n'a pas pu générer le MDN car l'en-tête Disposition-Notification-Option est non valide.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, assurez-vous que l'en-tête Disposition-Notification-Option du message AS2 est conforme à la syntaxe décrite dans la norme RFC 4130, « Échange de données d'entreprise MIME pair à pair sécurisé via HTTP, AS2 (Applicability Statement 2) ». Vérifiez que l'en-tête Signed-Receipt-Protocol est défini sur « facultatif » ou « pcks7-signature », et que l'en-tête Signed-Receipt-MICAlg est défini sur « facultatif »,  « MD5 » ou « SHA1 ». (Ces deux en-têtes sont inclus dans l'en-tête Disposition-Notification-Option.)