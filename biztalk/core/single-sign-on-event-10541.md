---
title: "Single Sign-On : Événement 10541 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7e206158-5652-453c-91ac-9a75ab02809a
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 201a43682898f312687f3d5d453f3b050bc75d48
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10541"></a>Single Sign-On : Événement 10541
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10541|  
|Source de l'événement|ENTSSO|  
|Composant|CO|  
|Nom symbolique|SSO_WARN_SSO_TICKETS_VALIDATED|  
|Texte du message|Les tickets ne peuvent pas être échangés sans être validés.|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'avertissement indique que les tickets SSO ne peuvent pas être échangés sans être validés. Dans le cadre de leur échange, les tickets SSO peuvent être validés ou non. L'étape de validation permet d'accroître la sécurité en comparant le nom de l'utilisateur ayant émis le ticket avec le nom de l'utilisateur indiqué dans le message BizTalk. Si les noms diffèrent, la validation échoue. Lorsqu'un message BizTalk transite par un hôte non approuvé, le nom de l'utilisateur indiqué dans le message BizTalk est remplacé par celui de l'hôte non approuvé. L'étape de validation permet de s'assurer que le message BizTalk a uniquement transité par les hôtes approuvés. En particulier, ce message indique que la validation est requise au niveau du système SSO (en raison d'une option du système SSO) mais qu'aucune information de validation n'a été fournie par l'appelant.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cet avertissement, effectuez l'une ou plusieurs des opérations suivantes :  
  
-   Si vous utilisez BizTalk Server, assurez-vous que votre message transite uniquement par les hôtes approuvés. Cela permet de réduire le risque de falsification des données du message.  
  
-   Si votre scénario le permet, désactivez l'étape de validation pour cette application. La validation correspond à une option d'administration pouvant être désactivée au niveau du système ou d'une application spécifique.  
  
 Pour plus d'informations, consultez les ressources suivantes dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :  
  
-   [Tickets SSO](../core/sso-tickets.md)  
  
-   [Comment afficher les propriétés d’une Application associée](../core/how-to-list-the-properties-of-an-affiliate-application.md)  
  
-   [Comment mettre à jour les propriétés d’une Application associée](../core/how-to-update-the-properties-of-an-affiliate-application.md)