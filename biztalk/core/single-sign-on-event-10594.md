---
title: "Single Sign-On : Événement 10594 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1f4c6041-39a8-49bc-b39e-66cb6eb2efae
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 804b2616080ceee0b6a31f7623e19e05c11481f5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10594"></a>Single Sign-On : Événement 10594
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10594|  
|Source de l'événement|ENTSSO|  
|Composant|Néant|  
|Nom symbolique|SSO_WARN_TICKET_VALIDATE_FAILED|  
|Texte du message|Échec de la validation du ticket. Le nom de l'expéditeur doit correspondre à celui de l'émetteur du ticket.%r<br /><br /> Nom de l’application : %1 %r<br /><br /> Ticket émis par : %2 %r<br /><br /> Nom de l’expéditeur : %3|  
  
## <a name="explanation"></a>Explication  
 Pour qu'un ticket soit validé, les champs Ticket émis par et Nom de l'expéditeur (dans le message d'avertissement) doivent correspondre. En revanche, si le message est transmis via un hôte BizTalk non approuvé, le champ Nom de l'expéditeur prend la valeur de l'hôte BizTalk non approuvé et le ticket n'est pas validé.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Si vous utilisez l'authentification unique de l'entreprise, vérifiez que votre message est transmis via des hôtes BizTalk approuvés uniquement. Cela permet de réduire le risque de falsification des données du message.  
  
 Si vous ne maîtrisez pas entièrement les implications de sécurité pour votre cas, vous pouvez désactiver la validation pour cette application. Notez que la validation est une option d'administration qui peut être désactivée pour le système ou pour cette application particulière.