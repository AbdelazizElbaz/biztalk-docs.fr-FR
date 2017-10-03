---
title: "Single Sign-On : Événement 10542 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e8e12444-b47c-4919-85b6-85c8e33b8342
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3ebcf97a9de014d0651c9f239c1ae6e846925f3b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10542"></a>Single Sign-On : Événement 10542
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10542|  
|Source de l'événement|ENTSSO|  
|Composant|CO|  
|Nom symbolique|SSO_WARN_APP_TICKETS_VALIDATED|  
|Texte du message|Les tickets ne peuvent pas être échangés pour cette application s'ils n'ont pas été validés.%r<br /><br /> Nom de l’application : %1|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'avertissement indique que les tickets de l'application ne peuvent pas être échangés sans être validés. Une fois les tickets de l'application échangés, ils peuvent être validés ou non. L'étape de validation permet d'accroître la sécurité en comparant le nom de l'utilisateur ayant émis le ticket avec le nom de l'utilisateur indiqué dans le message BizTalk. Si les noms diffèrent, la validation échoue. Lorsqu'un message BizTalk transite par un hôte non approuvé, le nom de l'utilisateur indiqué dans le message BizTalk est remplacé par celui de l'hôte non approuvé. L'étape de validation permet de s'assurer que le message BizTalk a uniquement transité par les hôtes approuvés. Ce message signifie précisément que la validation est requise au niveau du système d'applications (en raison d'une option du système SSO définie), mais aucune information de validation n'a été fournie par l'appelant.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cet avertissement, effectuez l'une ou plusieurs des opérations suivantes :  
  
-   Si vous utilisez BizTalk Server, assurez-vous que votre message transite uniquement par les hôtes approuvés. Cela permet de réduire le risque de falsification des données du message.  
  
-   Si votre scénario le permet, désactivez l'étape de validation pour cette application. La validation correspond à une option d'administration pouvant être désactivée au niveau du système ou d'une application spécifique.  
  
 Pour plus d'informations, consultez les ressources suivantes dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :  
  
-   [Tickets SSO](../core/sso-tickets.md)  
  
-   [Comment afficher les propriétés d’une Application associée](../core/how-to-list-the-properties-of-an-affiliate-application.md)  
  
-   [Comment mettre à jour les propriétés d’une Application associée](../core/how-to-update-the-properties-of-an-affiliate-application.md)