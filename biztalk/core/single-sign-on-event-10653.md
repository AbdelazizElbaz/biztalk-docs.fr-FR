---
title: "Single Sign-On : Événement 10653 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a0d85aca-20d9-4d65-8834-b31eacf143c8
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 91ec21a7883c3c1d3e97519f9239050ea18035fd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10653"></a>Single Sign-On : Événement 10653
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10653|  
|Source de l'événement|ENTSSO|  
|Composant|N\A|  
|Nom symbolique|SSO_ERROR_PS_ADAPTER_CALLBACK_ACCESS_DENIED|  
|Texte du message|Accès refusé au serveur de synchronisation de mot de passe (pour les adaptateurs).%r|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'erreur indique qu'un client a tenté de contacter le serveur mais que l'appel a été refusé. Différentes causes peuvent être à l'origine de ce problème (protocole incorrect, autorisations de sécurité insuffisantes, etc.).  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, procédez comme suit :  
  
-   Notez les informations contenues dans ce message et les informations appropriées dans le journal des événements, puis contactez les Services de Support technique Microsoft.  
  
 Pour plus d'informations, consultez les ressources suivantes dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :  
  
-   [Synchronisation de mot de passe](../core/password-synchronization2.md)